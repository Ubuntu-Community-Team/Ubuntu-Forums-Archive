---
title: "Xrdp works for RDP w/o prelaunched vncserver!!"
date: 2010-04-14
forum: Networking &amp; Wireless
---

### Post by celem on 2010-04-14
Solution – XRDP works multiple RDP sessions without vncserver involvement!

The Need:
I am helping a local genealogy society set up their research center. They want three workstations and a single data server. The genealogy program of choice was GRAMPS, which I have used for years – a Wonderful program! No data is going to be input on the workstations – the users are simply researching existing data on the server.

Since several RDP-based Wyse thin client units were available for free as were monitors and keyboards, the decision was quickly made to use an RDP based client/server system. Using VNC was unacceptable due to its speed and latency issues, plus, it isn't supported by the  Wyse thin client units – ONLY RDP and Cytrix.

Using Microsoft's server OS and Terminal Server package was far, far beyond the society's budget. We briefly considered equipping a Windows XP box with a copy ThinSoft's RDP server package, WinConnect Server XP, but its $300 price tag was still too much for the society.

The decision was to use Linux for the server. At first we considered LTSP but it is oriented towards PXE net boots and, while this may have worked, its complexity scared us off and we opted for what, we initially thought, was a much simpler solution – XRDP.

We were right and wrong at the same time. It is simple to set up – very simple, but the lack of documentation places many pitfalls in front of you, PLUS the solution is distribution dependent. 

I spent many hours on this issue. There are numerous sources on the web citing solutions to running XRDP. Unfortunately, they all involve running vncserver against the destination logins. This is NOT what we desired. We wanted to be able to boot up the host system but not login at all, yet still be able to connect to a session via RDP. I tried numerous distributions and eventually spending a lot of time going through the xrdp source code and planting out my own debug messages in /etc/xrdp/startsm.sh to output to a file in /tmp. Putting in “ps -eS >> /tmp/xrdp.txt” was particularly useful because it showed that xrdp/sesman DID launch an Xvnc, meaning that it was unnecessary to pre-launch vncserver, as most pundits recommend. The solution was figuring out how to connect to the Xvnc session created by sesman.

I discovered the solution somewhat by accident. It seems that the files created in the destination user's .vnc folder by vncserver were interfering with xrdp/sesman. Here is what worked.

[LIST=1]
[*]1.Starting with a nearly virgin install of Ubuntu 10.04 beta 1, installed two users intended to be accessed for remote login via RDP. That is ALL that I did – I never even logged into them.
[*]2.My first entry xrdp.ini was unmodified except that “ask” was deleted from “username=”. _Everything was unmodified_.
[*]3.Using tsclient on another machine, with the desired username, that was NOT logged in, and password pre-filled, I connected and received a nice Gnome desktop.
[*]4.The session was on 5910.
[*]5.While keeping this session active, I logged into the next login created for remote access and received my second nice Gnome sesktop on port 5911 – automatically. Xrdp-sesman DOES automatically launch Xvnc in a useful way!
[/LIST]

Ok, everything isn't roses. I can **ONLY** get this to work on Ubuntu version 10.04 e/w Gnome. It fails on CentOS 5.2, Xubuntu 9.10, SuperOS 9.10 and Lubuntu 10.04. In all cases xrdp was version 4.1.1, so the issue is not with xrdp/sesman – it lies within the OS – what, I do not know. I did not test KDE at all.
---------------
```

The system is running Ubuntu 10.04 LTS beta - the Lucid Lynx, amd64:
uname -a
Linux ubu910 2.6.32-16-generic #25-Ubuntu SMP Tue Mar 9 16:33:12 UTC 2010 x86_64 GNU/Linux
---------------------------------
Contents of /etc/xrdp/sesman.ini:
---------------------------------
[Globals]
ListenAddress=127.0.0.1
ListenPort=3350
EnableUserWindowManager=1
UserWindowManager=/etc/xrdp/startwm.sh
DefaultWindowManager=/etc/xrdp/startwm.sh

[Security]
AllowRootLogin=1
MaxLoginRetry=4
TerminalServerUsers=tsusers
TerminalServerAdmins=tsadmins

[Sessions]
MaxSessions=10
KillDisconnected=0
IdleTimeLimit=0
DisconnectedTimeLimit=0

[Logging]
LogFile=/var/log/sesman.log
LogLevel=DEBUG
EnableSyslog=0
SyslogLevel=DEBUG

[X11rdp]
param1=-bs
param2=-ac

[Xvnc]
param1=-bs
param2=-ac

----------------------------
Contents of /etc/xrdp/startwm.sh:
----------------------------
#!/bin/sh

if [ -r /etc/default/locale ]; then
  . /etc/default/locale
  export LANG LANGUAGE
fi

. /etc/X11/Xsession
----------------------------
Contents of /etc/xrdp/xrdp.ini:
----------------------------

[globals]
bitmap_cache=yes
bitmap_compression=yes
port=3389
crypt_level=low
channel_code=1

[xrdp1]
name=remote
lib=libvnc.so
username=
password=ask
ip=127.0.0.1
port=-1

---------------------------------
The user "remoc1" contains a .vnc folder that was created by sesman NOT vncserver. It only contains one file "sesman_passwd".



```

---

### Post by celem on 2010-04-14
Just tested via VirtualBox images - PCLinuxOS 2009.2 fails but Ylmf v1.0 works. Ylmf is based on Ubuntu 10.04

---

### Post by celem on 2010-04-15
Just tested via VirtualBox images - antiX-M8.5-68, Linux 2.6.32-mepis-smp using the iceWM. This release uses version 5.0 of xrdp. Results were a partial success. I am presented with a desktop e/w conky but only a partial menu wherein I can change the desktop background and the RUN dialog, but not much else.

---

### Post by celem on 2010-04-18
Final update! All was working well and I could open and close mamny sessions from multiple terminals without problems - then something happened. After I changed screen resolutions AND removed the Quit button - things got bad. From that point on if I quit a session, sesmon died. I don't know what happened but I have run out of time to figure it out and have shifted over to FreeNX as my second choice.

:(

---

### Post by celem on 2010-04-20
Yet another update. 
Some **significant success** with lubuntu 10.04 Beta. 
My xrdp sessions work perfectly connecting, disconnecting, reconnecting, etc. This is looking very promising. To work the /etc/xrdp/startwm.sh file must be edited to correctly start the window manager. I also stuck a ps command in there so that I could capture the Xvnc session just after it invoked and before the RDP session actually started. I have pasted below both the current contents of my lubuntu's startwm.sh and also the relevant portion of the ps -Af output:

startwm.sh:
```
#!/bin/sh

if [ -r /etc/default/locale ]; then
  . /etc/default/locale
  export LANG LANGUAGE
fi

ps -Af >/tmp/xrdp.txt

exec /usr/bin/lxsession -s Lubuntu -e LXDE
#. /etc/X11/Xsession


```

ps -Af output:
```
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 15:45 ?        00:00:00 /sbin/init
...
xrdp       638     1  0 15:45 ?        00:00:17 /usr/bin/xrdp
root       644     1  0 15:45 ?        00:00:03 /usr/bin/sesman
...
root      1575   644  1 16:57 ?        00:00:00 /usr/lib/xrdp/sessvc 1577 1576
remoc1    1576  1575  2 16:57 ?        00:00:00 /bin/sh ///etc/xrdp/startwm.sh
remoc1    1577  1575  4 16:57 ?        00:00:00 Xvnc :10 -geometry 800x600 -depth 16 -rfbauth /home/remoc1/.vnc/sesman_passwd -bs -ac
remoc1    1578  1576  0 16:57 ?        00:00:00 ps -Af

```

---

### Post by MCC on 2010-08-07
THANK YOU! I tried your script in Lubuntu 10.04 and it works perfectly. I'm setting up a machine on some old hardware that needed remote GUI access and this finally did the trick.

Edit: I'm logging in from Windows 7, so I had to get the Windows XP RDP client. I downloaded it from the MS website, let it self-extract to %temp%, extracted a .exe from there with 7zip, and copied/renamed the relevant .exe and .dll from a .cab file. They don't make it easy. :)

---

### Post by amlucent23 on 2010-09-08
Wow, I am curious if you tried suse?  I have previously had the most luck with xrdp on suse using their "nomad" packages.  if so what did you find wrong with it.. did it use vnc?

I swear I have set this up in suse 11.1 using the nomad repo.  [http://opensuse.swerdna.org/suserdp111.html](http://opensuse.swerdna.org/suserdp111.html)

Anyway, thank you for documenting this and doing a lot of the troubleshooting.  I will certainly try this out.

---

### Post by celem on 2010-09-08
I did not try SUSE - I stuck with Lubuntu, since it works. Maybe, if I ever have any spare time, I'll devote some more effort on XRDP. For Linux to not have a viable RDP solution borders on being criminal. The only truly viable solutions are Micro$oft based and that really needs to be remedied. I would really love to better dissect the XRDP source and see if I can determine how to eliminate the distro dependencies - someday!

---

### Post by amlucent23 on 2010-09-08
Ok, I gave suse 11.3 a spin last night and tried to set this up but its horrible.. I tell you the easiest time I ever had was with suse 11.1 using their Nomad repo.  I install 3 packages and it just worked... they even made a admin utility for yast.

I agree, its criminal.  All the linux remote admin/desktop stuff kind of sucks (excluding ssh of course).  VNC just needs to be put out to pasture.  NX is promising but just not there yet.. and probably never will be.  I see no active development on googles Neatx which I was so excited about when I first saw it.

---

### Post by tulcak@gmail.com on 2010-09-28
What is the current status?  I am trying to set this up as well and for the same reason!  GRAMPS.  wow.  I've spent many many hours and have had partial success.  Right now, from the windows vista 64bit box, I can start an rdp connection, but, all I get is a black screen.  I know I am missing something somewhere... session files? config files?... I don't know.  I think I am close.

by the way, I am a noob.  I can post details if you are interested in the bumblings of an amateur, but maybe my mistakes might give you something usefull.  the basic setup is an Ubuntu 10.04 studio box and a windows vista 64bit box.

---

### Post by celem on 2010-09-30
For me, it is a back-burnered issue, since the project that I using it for has taken a different direction. That said, (1) it does work well on Lubuntu; (2) I received an email response from the xrdp lead developer stating that the project remains in active development, despite no recent postings.

RDP remains a personal interest - BUT - there are only so many hours in a day and my pressing need for functional RDP went away.

---

### Post by steveferson on 2012-08-31
Thanks for this! Changing startwm.sh as described helped fix my issue where I was just getting a blank (grey) screen with an X cursor when I logged in.

---

### Post by uRock on 2012-08-31
Thread is two years old.

Thread Closed

---

