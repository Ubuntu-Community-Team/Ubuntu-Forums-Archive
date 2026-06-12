---
title: "telnet service hw?"
date: 2009-05-05
forum: Networking &amp; Wireless
---

### Post by ottosykora on 2009-05-05
I need to run one PC with Ubuntu (8.10) and connect to it via telnet within the same subnet. No firewall, same segment, not public connection.

What do I have to install to start common telnet service on the ubuntu so I can contact it from other machine?

(no need for remote desktop etc, must be common telnet only)

---

### Post by slakkie on 2009-05-05
I wouldn't advise to use telnet, I would go for ssh (which is basicly the secure version of telnet). But by installing the telnetd package you will install the telnetd server. 

But only do this if telnet is really required, I would first check if you can do the same thing with ssh.

After you installed telnetd, restart inetd and then you will be able to connect via telnet to your box, you could put some deny entries in your hosts.(allow|deny) files to limit access from other networks.

But again, please check if you can use ssh instead.

---

### Post by ottosykora on 2009-05-05
>wouldn't advise to use telnet, I would go for ssh (which is basicly the secure version of telnet).<


yes, but this will not work on the other machine I need to call from. This we tested many times, it is a 386 embeded and has simply not enough computing power to do that.


> But by installing the telnetd package you will install the telnetd server.<





Tried to make sudo apt-get install telnetd

OK, it did download the file, started install, but then lot of error messages came up, telling me I have to run update and more.
Update, well it is a fresh installation, first 8.10 then all updates then update to 9.
Since the machine refused to boot properly with the lates kernell, I am starting it with previous one ...11?? or someting.

No special other software installed. 
I also checked if the entries in the inetd.conf for the telnet are there , all seems to me as relative newbie ok.

Telneting from the other machine fails, while I can telnet with it to some other units in the net.

---

### Post by slakkie on 2009-05-05
> **ottosykora said:**
> >wouldn't advise to use telnet, I would go for ssh (which is basicly the secure version of telnet).<


yes, but this will not work on the other machine I need to call from. This we tested many times, it is a 386 embeded and has simply not enough computing power to do that.


> But by installing the telnetd package you will install the telnetd server.<





Tried to make sudo apt-get install telnetd

OK, it did download the file, started install, but then lot of error messages came up, telling me I have to run update and more.
Update, well it is a fresh installation, first 8.10 then all updates then update to 9.
Since the machine refused to boot properly with the lates kernell, I am starting it with previous one ...11?? or someting.

No special other software installed. 
I also checked if the entries in the inetd.conf for the telnet are there , all seems to me as relative newbie ok.

Telneting from the other machine fails, while I can telnet with it to some other units in the net.

If it is warning you to update, you should do it (unless you have reasons not to update):

sudo aptitude update
sudo aptitude -s safe-upgrade # this will run the upgrade path, but without doing anything

If you are ok with this run:
sudo aptitude safe-upgrade

If it updates your kernel, you will need to reboot your machine, otherwise:

inetd
telnet localhost 

and you should be connected to your own box. Then try connecting from a different box inside the same network.

---

### Post by ottosykora on 2009-05-05
>If it is warning you to update, you should do it (unless you have reasons not to update):

sudo aptitude update
sudo aptitude -s safe-upgrade # this will run the upgrade path, but without doing anything<

well done that all



>inetd
telnet localhost<

OK, I made first
sudo apt-get install telnetd

ok, it was installed.
I was not able to start it manually, or better I did not figure out how.
But on next rebbot, 
netstat -a¦grep telnetd

gives answer that tcp6 0 0 telent listening

I tried then the local connect, but this asks me to install openbsd-inetd , probably instead the one I installed.

Connection from local net failed, 'connection refused' it did say on my embeded machine and also a windows in same subnet was not able to get connection.

Is the telnet now on? (netstat says so, but???)
Or is it off since only the openbsd-inetd will run on ubuntu?



and you should be connected to your own box. Then try connecting from a different box inside the same network.

---

### Post by slakkie on 2009-05-05
The openbsd-inetd got installed automatically when I installed telnetd, what happens when you install it manually?

This is what happens when I install telnetd:

```

13:58 pts/3 0 wesleys@eniac:/home/wesleys$ sudo aptitude install telnetd
[sudo] password for wesleys:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been automatically kept back:
  amarok-xine apport firefox-3.0 k3b libfreetype6 libwmf0.2-7 linux-libc-dev linux-restricted-modules-common python-apport python-problem-report xulrunner-1.9
The following NEW packages will be automatically installed:
  openbsd-inetd
The following packages have been kept back:
  acpid amarok apport-qt firefox
The following NEW packages will be installed:
  openbsd-inetd telnetd
0 packages upgraded, 2 newly installed, 0 to remove and 25 not upgraded.
Need to get 0B/76.9kB of archives. After unpacking 283kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Selecting previously deselected package openbsd-inetd.
(Reading database ... 126271 files and directories currently installed.)
Unpacking openbsd-inetd (from .../openbsd-inetd_0.20050402-6_i386.deb) ...
Selecting previously deselected package telnetd.
Unpacking telnetd (from .../telnetd_0.17-35ubuntu1_i386.deb) ...
Setting up openbsd-inetd (0.20050402-6) ...
 * Stopping internet superserver inetd                                                                                                                                     [ OK ]
 * Not starting internet superserver: no services enabled.

Setting up telnetd (0.17-35ubuntu1) ...
Adding user telnetd to group utmp

Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
13:59 pts/3 0 wesleys@eniac:/home/wesleys$ inetd
zsh: correct 'inetd' to 'net' [nyae]? n
inetd: non-root must specify a config file
13:59 pts/3 1 wesleys@eniac:/home/wesleys$ sudo !!
sudo inetd
13:59 pts/3 0 wesleys@eniac:/home/wesleys$ telnet localhost
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
Ubuntu 8.04.2
eniac login: wesleys
Password:
Last login: Tue May  5 13:28:06 CEST 2009 on :0
Linux eniac 2.6.24-23-generic #1 SMP Wed Apr 1 21:47:28 UTC 2009 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/
You have new mail.

# Users logged in (max 13)
 13:59:20 up  4:33,  2 users,  load average: 0.76, 0.35, 0.18
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
wesleys  :0       -                13:28   ?xdm?   2:36m  0.02s /bin/sh /usr/bi
wesleys  pts/5    localhost        13:59    0.00s  0.06s  0.06s -zsh

# Fortune of the shell
For the fashion of Minas Tirith was such that it was built on seven levels,
each delved into a hill, and about each was set a wall, and in each wall
was a gate.
                -- J.R.R. Tolkien, "The Return of the King"

        [Quoted in "VMS Internals and Data Structures", V4.4, when
         referring to system overview.]

Linux eniac 2.6.24-23-generic #1 SMP Wed Apr 1 21:47:28 UTC 2009 i686 GNU/Linux

13:59 pts/5 0 wesleys@eniac:/home/wesleys$

```

---

### Post by ottosykora on 2009-05-05
On my side, different version of the telnet was installed.
It did install some inetutils-telnetd  as I remember it.

The telnet was listening, but I could not reach it by any client.

I installed then the openbsd one. This time it said it is removing the inetutils one and installing the openbsd one. It did also start the server so finally I managed to log in not only to localhost, but also from my remote embeded machine. Somehow it takes long time to contcat the telnet server, some 20-30 sec (???) but then I get the prompt and can login.

Can it be that the inetutils one is somehow not compatible? Strange, with netstat, the inetutils one had tcp6 0 0 ... at the begining of the line instead of simple tcp like the openbsd one.
???

Huuh, this was an exercise! Now I have to get a break first.

---

