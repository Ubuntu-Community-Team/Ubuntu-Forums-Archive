---
title: "Squid3 doesn't run properly on startup"
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by dawbomb on 2008-12-24
Hi!

I have set up and am successfully running a squid3 proxy server at my house, with one slight glitch.  It doesn't start properly when I start up my server.  The services are running, but when I go into a web browser on any computer (even the server itself) I get a squid3 timeout page.  All I have to do is type /etc/init.d/squid3 restart and hey presto, works like a charm.  The "server" is running ubuntu desktop 8.10.

I have tried reinstalling squid3, with no result.  The server can't run around the clock because I get moaned at that its wasting electricity, and its not very conducive to sleep (it sits in my bedroom).  At the same time, it must "just work" when the power button is pressed, otherwise the 'rents get rather irate when they have to phone me because they have no internet.

Many thanks.

---

### Post by joebeasley on 2008-12-25
You have to tell squid to start at boot.  Install rcconf and enable it at boot.

sudo apt-get install rcconf

After install run rcconf and enable squid3.  

sudo rcconf

Use the arrow keys to highlight squid3.  Press the spacebar to "check" it.  Squid will start at reboot.

---

### Post by dawbomb on 2008-12-26
According to rcconf, squid3 was already running at startup.  Which is logical, seeing as when I try to start squid using sudo /etc/init.d/squid3 start, it fails, but when i restart instead of start it it goes perfectly.  I can also stop, then start, which does the same thing.

I did uncheck squid3, exit, restart rcconf, then recheck squid3, and when i restarted my machine I still had to restart squid3 before I could start browsing...

---

### Post by diemos784 on 2009-03-17
> **dawbomb said:**
> According to rcconf, squid3 was already running at startup.  Which is logical, seeing as when I try to start squid using sudo /etc/init.d/squid3 start, it fails, but when i restart instead of start it it goes perfectly.  I can also stop, then start, which does the same thing.

I did uncheck squid3, exit, restart rcconf, then recheck squid3, and when i restarted my machine I still had to restart squid3 before I could start browsing...

I am also experiencing the same issue. I am running Intrepid with squid3. Since I am a noob at Linux, I do my configuration through webmin. Whatever default auto-start script squid3 seem to install, fails to launch the program correctly. squid3 will be listed on the process list, but attempting to use the proxy results in an error page. The work around I use, is to disable squid3 auto-start up, and creating a launcher with the commands "gksu /etc/init.d/squid3 start" and manually clicking on that launcher every time I boot. Seems like a very noobish way but it works ;). Unlike the auto-start script, manually starting squid3 results in everything working correctly. Does anyone know of a solution?

---

### Post by maulbongo on 2009-03-31
Hi there,

I had the same problem and solved it like this:

create autostart for squid3:

1.    create a file named as you need with ending .sh and also mark it as executable
    (for example /home/%username%/squid3-restart.sh)

2.    write down the command you like to execute in this file
    (for example /etc/init.d/squid3 restart)

3.    go to "system", "settings", "session" and add a new startprogramm
    (here for example named "squid-restart" and for command type "sudo /home/%username%/squid3-restart.sh")

4.    if you execute this command now the system still askes for sudo password, so we need to edit the file /etc/sudoers
    (but be really careful!!). open nautilus as sudo ("sudo nautilus"), go to /etc and right click on this file "sudoers" open properties,
    now change the rights of root from read only to read and write
    open the file with texteditor or "vi" and add a new line:
    %username% ALL=NOPASSWD: /home/%username%/squid3-restart.sh

5.    save the changes, and change again the properties of "sudoers" from read and write to read only (it's really important, otherwise your system
    won't start anymore after shutdown or reboot !!!!).

6.    That's it, all done and you have got command script for squid3 running on startup and restarting once and than it works.

---

### Post by dawbomb on 2009-04-04
Thanks, I've fixed it a different way...  I had an old computer lying around, which is now a dedicated server, running Ubuntu Server 8.04.  That runs almost all the way round the clock, as its also acting as a file server which all the computers in the house (including my parents') backup to, and a sort of an email server.  Basically it downloads my gmail so that when I open evolution, my emails are there instantly :P

I didn't see the need to upgrade to Server 8.10, but I'll upgrade it to 9.04 when the "stable" version is released.  I say "stable", because at the moment I'm running 9.04 beta on my desktop and laptop, and there is no problem with stability there!

Thanks for the help!

---

### Post by mikelward on 2009-04-07
Is it bug 97513?
[https://bugs.launchpad.net/ubuntu/+source/squid/+bug/97513/](https://bugs.launchpad.net/ubuntu/+source/squid/+bug/97513/)

Squid starts before NetworkManager, so it doesn't know which DNS servers to use.

---

