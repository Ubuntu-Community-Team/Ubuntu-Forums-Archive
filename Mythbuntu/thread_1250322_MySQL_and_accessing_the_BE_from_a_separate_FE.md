---
title: "MySQL and accessing the BE from a separate FE"
date: 2009-08-26
forum: Mythbuntu
---

### Post by BigEdgar on 2009-08-26
Hi,

I've been to the MythTV list and the MySQL list and have not had any luck there, so I'm hoping the Mythbuntu community can help with this...

I've traditionally just run a combined backend/frontend machine, but have recently decided to add a frontend machine. I can't for the life of me figure out why I can't access MySQL from the frontend (or any other machine) on my network. 

I followed the docs to grant permissions in the DB ([http://www.mythtv.org/docs/mythtv-HOWTO-6.html#ss6.2](http://www.mythtv.org/docs/mythtv-HOWTO-6.html#ss6.2)), and made the correct changes in the backend mythtv-setup fields, but still get an "access denied" message when trying to connect. So now I'm simply trying to access MySQL from the command line, and have no problems doing this from the backend machine, but can't access it from any other machines. 

Anyways, I've granted permissions correctly as far as I can tell, but whenever I login a) from a remote machine, or b) when specifying a host on the local machine, I get an access denied error message at the terminal: ERROR 1045 (28000): Access denied for user 'mythtv'@'mythtv3.local' (using password: YES)

Here's a run down of all of the things I have tried (thanks to folks on the MythTV list who helped with some suggestions, the MySQL list has not proven to be of any help yet...):


1. This works fine (accessing MySQL on the server machine from the server machine):

$ mysql -u mythtv -p

2. But doing this from the server or client machine does *not* work:

$ mysql -u mythtv -h 192.168.5.19 -p
Enter password:
ERROR 1045 (28000): Access denied for user 'mythtv'@'mythtv3.local' (using password: YES)

3. I've granted permissions from very specific all the way up to them wide open (followed instructions at [http://www.mythtv.org/docs/mythtv-HOWTO-6.html#ss6.2):](http://www.mythtv.org/docs/mythtv-HOWTO-6.html#ss6.2):)

mysql> select User, Host from user where user='mythtv';
+--------+----------------------+
| User | Host |
+--------+----------------------+
| mythtv | % |
| mythtv | 192.168.5.% |
| mythtv | ubuntu-desktop.local |
| mythtv | localhost |
+--------+----------------------+
4 rows in set (0.00 sec)

4. I'm not running a firewall.

5. I've got skip-networking and bind-address disabled in my.cnf file (and I've restarted MySQL many times since I made these changes):

# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
# bind-address = 127.0.0.1

6. Now, I *can* get access from a remote machine if I start mysqld with the --skip-grant-tables option, so that tells me that the problem lies in my grant table. But I can't see anything wrong with it.

7. I can telnet in on 3306 just fine from a remote machine, so I'm confident that this is not a networking issue:

$ telnet 192.168.5.19 3306
Trying 192.168.5.19...
Connected to 192.168.5.19.
Escape character is '^]'.
@
5.0.75-0ubuntu10.2.7k7mCCh,`,UHIt12GO5]

8. I've enabled logging and warnings, but I'm not seeing any warnings get popped anywhere. Errors appear to be showing up in syslog, which is great. But I can't get warnings to show up. According to the MySQL docs, if the value for log-warning is >1, then connection related info is written to the error log:

"The --log-warnings option or log_warnings system variable can be used to control warning logging to the error log. The default value is enabled (1). Warning logging can be disabled using a value of 0. If the value is greater than 1, aborted connections are written to the error log."

So I've set the log level in the DB:

mysql> show global variables like 'log_warn%';
+---------------+-------+
| Variable_name | Value |
+---------------+-------+
| log_warnings | 1 |
+---------------+-------+
1 row in set (0.00 sec)

mysql> set global log_warnings=2;
Query OK, 0 rows affected (0.00 sec)

mysql> show global variables like 'log_warn%';
+---------------+-------+
| Variable_name | Value |
+---------------+-------+
| log_warnings | 2 |
+---------------+-------+
1 row in set (0.00 sec)

Logging in with the u/p and host that result in the "access denied" error message doesn't cause anything to show up in the syslog.

In addition, I've also just started mysqld from the command line with logging and log-warnings enabled:

$ sudo /usr/sbin/mysqld --log-warnings=2 --log-error

... and still, the access attempt doesn't show up in any of the logs. (And I don't see any other warnings logged anywhere).
********************

As I said, I'm stumped. Anyone have any ideas on what I'm missing here?

---

### Post by tgm4883 on 2009-08-26
Usually you just have to enable the MythTV service (or is it the MySQL service) in MCC. I would try that, although it may no longer work with all the stuff you have done.

---

### Post by BigEdgar on 2009-08-26
Do you mean enable this via the MCC on the FE or the BE?

---

### Post by tgm4883 on 2009-08-26
> **bigedgar said:**
> do you mean enable this via the mcc on the fe or the be?

be

---

### Post by BigEdgar on 2009-08-26
Thanks. I did initially adjust a few settings via the MCC that were related to enabling access from a FE (can't recall what they were off hand), but I do recall that they didn't cause access from the FE to work, which is why I did all the other stuff. I'll check the MCC on the BE again tonight so I can detail what I did.

---

### Post by roundhay on 2009-08-26
I recently set up a a frontend on a laptop (eeepc) and my office PC to access my main FE/BE machine.

I could not find any great how-to's but if I remember correctly you have to set the PIN number in the backend settings to 0000 and I had to run:

sudo dpkg-reconfigure mythtv database

There is an option during the reconfiguration to allow remote connections.

After doing this when I opened up one of the frontends on the network and it automatically found the backend and I could watch TV

The backend PIN is mentioned here
[http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend](http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend)

---

### Post by joho500 on 2009-08-27
It may be obvious, but did you change the IP-addresses in the Backend setup from 127.0.0.1 to your LAN IP-address?

Joost

---

