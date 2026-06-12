---
title: "Cannot Connect to Port UPnP or 3306"
date: 2011-05-31
forum: Mythbuntu
---

### Post by nhtrader on 2011-05-31
I performed an upgrade this morning and had trouble. So much so that I had to change servers. Eventually, I completed an upgrade from 20110528 v0.24.1-4  to  20010531 v0.24.1-9

Unfortunately I now have a problem. Everything worked fine until this morning.

Now I cannot use Mythtv using hostname 10.10.10.12. I can only use it with hostname localhost.

If I use hostname 10.10.10.12, I get the following error...

Method 1 using terminal mode command:
==================================
mythtv-setup<E>
"Mythbackend must be closed before continuing. Is it OK to close any currentyly running mythbackend processes? YES
Enter User Password
Country and Language layout screen appears. I select SAVE
Database configuration page 1 appears with hostname containing local home network IP address.

Now I press ESC to exit.



Method 2 using GUI menus:
========================
Applications|Multimedia|MythtvFrontend

Country and Language layout screen appears. I select SAVE
Database configuration page 1 appears with hostname containing local home network IP address.

"Cannot connect to port 3306"

However, if I change the hostname from 10.10.10.12 to localhost Myth Frontend works normally. But when I attempt to change hostname from localhost to any IP address on my home network, Mythtv produces the errors cited above.



1. I've checked all config files: config.xml and mysql.txt and made sure that they are all synchronized:
/etc/mythtv/mysql.txt
/home/mythtv/.mythtv/mysql.txt
/home/dad/.mythtv/mysql.txt
/etc/mythtv/config.xml
/usr/share/doc/mythtv-backend/contrib/config_files/config.xml
/usr/share/mythtv/config.xml
/home/mythtv/.mythtv/config.xml
/home/dad/.mythtv/config.xml
/root/.mythtv/config.xml

2. I've checked /etc/hosts, /etc/hosts.allow, /etc/hosts.deny. /etc/resolv.conf  - all OK.

3. In terminal mode I used command:
ifconfig => 10.10.10.12

this confirms correct IP address for MythBox

4. Didn't attempt to manually reset MYSQL b/c database access works fine using localhost.

5. Noticed that router's DHCP client list didn't include Mythbox IP address. Don't know why Mythbox's  ipaddress and computer name isn't in list?

---

### Post by ian dobson on 2011-05-31
Hi,

Has anything changed on your mysql configuration? There is an option to only bind to a specific address. Have a look in your my.cnf file.

Can you actually ping your ip address 10.10.10.12.

What happens if you stop the frontend and then try starting it? Does it actually attach to the backend?

Regards
Ian Dobson

---

### Post by nhtrader on 2011-05-31
> **ian dobson said:**
> Hi,

Has anything changed on your mysql configuration? There is an option to only bind to a specific address. Have a look in your my.cnf file.

Can you actually ping your ip address 10.10.10.12.

What happens if you stop the frontend and then try starting it? Does it actually attach to the backend?

Regards
Ian Dobson



I have not changed anything, and I'm the only user. 

I found this file:
/etc/mysql/my.cnf
this entry exists:   bind address = 127.0.0.1

I now commented it out  with leading #
Then entered terminal mode:
sudo su
service mysql stop
service mysql start

Used GUI menus to start FE - now OK with IP address.


Just to answer your questions for future readers:

Can you actually ping your ip address 10.10.10.12.  Yes, in terminal mode I entered ping 10.10.10.12<E>


As for last part, upon restart of FE after commenting out bind address = 127.0.0.1, it now attaches to BE.
However, prior to changing the /etc/mysql/my.cnf file it did not attach.

I don't know why the mysql configuration file changed, but I'm guessing that the overnight upgrade changed it.

Thanks. Your suggestion worked.

---

### Post by ian dobson on 2011-05-31
Hi,

Glad to see the problem is solved. An update to mysql maybe a week ago or so may have changed the my.cnf file. But if mysql isn't restarted it'll work with the old configuration.

Maybe mark the thread as solved.

Regards
Ian Dobson

---

