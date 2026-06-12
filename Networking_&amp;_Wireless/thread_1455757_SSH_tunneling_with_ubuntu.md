---
title: "SSH tunneling with ubuntu"
date: 2010-04-16
forum: Networking &amp; Wireless
---

### Post by donaldvr on 2010-04-16
In my continuing effort to get away from relying on Windows, I've run into a snag.  This is what I am able to do in windows:

From my windows laptop at home, I can use putty to ssh into the ubuntu server at work.  Putty can be configured to forward a local port to another windows computer on the network at work.  Here is a screen shot of the putty configuration:
[IMG]http://173.45.239.75/putty_config.png[/IMG]

In this case, when I am connected to the work ubuntu server, i can use remote desktop and connect to 127.0.0.1:880 and I would be connected via RDP to a desktop in my office.

I've tried to do the same thing from my ubuntu laptop with this command:
sudo ssh [username]@[workip] -L 880:[desktop_at_work_local_ip]:3389

When I connect this way and try to use rdesktop to connect to 127.0.0.1:880, the connection is refused.

I know I'm doing something, wrong, but I can't figure out what.  Please help!

---

### Post by Brandon Williams on 2010-04-17
First, I would avoid using local port numbers that require usind sudo to open the ssh connection. Instead of local port 880, use local port 3389 (or any other port greater than 1000).
```
ssh username@workip -L 3389:desktop_at_work_local_ip:3389
```
I doubt this is the problem; it's just good practice to avoid using sudo when it isn't necessary.

Next, verify that the tunnel is really being established. Run this command, replacing 3389 with whatever local port number you choose:
```
netstat -lnp | grep ssh | grep :3389
```
You can also add the -N switch (don't run a remote command) and the '-o ExitOnForwardFailure=yes' option to the ssh command line so that ssh will exit if the local forwarding cannot be established.

If the ssh session is being established and the local port forwarding is working, then the next thing to check is whether there is a firewall rule of some sort that is blocking your packets on one side or the other.

---

### Post by donaldvr on 2010-04-17
Brandon - Thank you for sharing you brilliance!

Changing the forwarding port to a number > 1000 fixed the problem.  

The other tips you listed for problem-solving will come in handy in the future, I'm sure.

Now I just have to figure out how to change that prefix to solved. ;)

---

### Post by altonbr on 2010-04-22
I have the same problem but I need this ssh tunnel to access my work's mysql db...

I ran
```
ssh -L 3306:localhost:3306 username@domain
```
and then
```
sudo netstat -lnp | grep ssh | grep :3306
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      8776/ssh        
tcp6       0      0 ::1:3306                :::*                    LISTEN      8776/ssh 
```

But now I need to connect to the mysql server through the command-line or mysql administrator and I can't figure out how. Any suggestions?

---

### Post by computer13137 on 2010-04-22
altonbr: If you are tunneling your MySQL port to localhost, then you should be able to access it by using localhost as the MySQL server.  It is as though it's running on 127.0.0.1, as long as the SSH tunnel is open.


I am concerned that someone on Google may find this thread and try to use it as a guide to tunnel a port for themselves, and I want to clear something up.
There is nothing wrong with forwarding ports less than port 1,000. It's just that those are "privileged" ports, and only root can forward them. :)

Cheers,
Kirk

---

### Post by altonbr on 2010-04-22
> **computer13137 said:**
> altonbr: If you are tunneling your MySQL port to localhost, then you should be able to access it by using localhost as the MySQL server.  It is as though it's running on 127.0.0.1, as long as the SSH tunnel is open.


Cheers,
Kirk

Well that's what I thought, but it didn't work... when I used 'localhost' as the domain anyway. It seems to work with '127.0.0.1' when```
ssh -L 3306:localhost:3306 username@domain
```so thank you!

For others:

After running the command above, you can then connect to your MySQL db through the command-line like so:```
mysql -u username -h 127.0.0.1 -p
```or via MySQL Administrator (```
aptitude install mysql-admin
```)
by using your username and 127.0.0.1 for your IP address.

---

### Post by Goldiescorpio on 2012-07-02
Thx Brandon,

this solved my problem!

grtz

---

