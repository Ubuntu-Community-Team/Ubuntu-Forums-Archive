---
title: "Pidgin Internet Messenger connect and hang!"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by ubantuwannabe on 2009-01-15
Hi,

I'm using Pidgin Internet Messenger connect and hang!

Protocal used is MSN.

It connects nicely initally. 

Next I type a message and send to my colleague,

next it hangs.

I have to choose either Wait or Force Quit.

Is there any solutions to the above solution?

thanks

---

### Post by kranny on 2009-01-15
Pidgin version and ubuntu version?and also i would suggest typing pidgin in a terminal and paste any error messages you get.

---

### Post by Twitch6000 on 2009-01-15
> **ubantuwannabe said:**
> Hi,

I'm using Pidgin Internet Messenger connect and hang!

Protocal used is MSN.

It connects nicely initally. 

Next I type a message and send to my colleague,

next it hangs.

I have to choose either Wait or Force Quit.

Is there any solutions to the above solution?

thanks

I think the problem is due to a recent update on the msn protocol.

I would use aMSN(latest version) as they already have the problem fixed.

---

### Post by ubantuwannabe on 2009-01-15
Hi this is the log

buffer@buffer-desktop:~$ tail -f /var/log/messages
Jan 15 12:01:11 buffer-desktop -- MARK --
Jan 15 12:21:11 buffer-desktop -- MARK --
Jan 15 12:41:11 buffer-desktop -- MARK --
Jan 15 13:01:11 buffer-desktop -- MARK --
Jan 15 13:21:11 buffer-desktop -- MARK --
Jan 15 13:41:11 buffer-desktop -- MARK --
Jan 15 14:01:11 buffer-desktop -- MARK --
Jan 15 14:09:15 buffer-desktop kernel: [19701.206138] type=1503 audit(1231999755.218:5): operation="inode_permission" requested_mask="::rw" denied_mask="::rw" fsuid=7 name="/dev/tty" pid=16815 profile="/usr/sbin/cupsd"
Jan 15 14:21:11 buffer-desktop -- MARK --
Jan 15 14:41:11 buffer-desktop -- MARK --
^Z
[2]+  Stopped                 tail -f /var/log/messages


thanks

---

### Post by kranny on 2009-01-15
> **ubantuwannabe said:**
> Hi this is the log

buffer@buffer-desktop:~$ tail -f /var/log/messages
Jan 15 12:01:11 buffer-desktop -- MARK --
Jan 15 12:21:11 buffer-desktop -- MARK --
Jan 15 12:41:11 buffer-desktop -- MARK --
Jan 15 13:01:11 buffer-desktop -- MARK --
Jan 15 13:21:11 buffer-desktop -- MARK --
Jan 15 13:41:11 buffer-desktop -- MARK --
Jan 15 14:01:11 buffer-desktop -- MARK --
Jan 15 14:09:15 buffer-desktop kernel: [19701.206138] type=1503 audit(1231999755.218:5): operation="inode_permission" requested_mask="::rw" denied_mask="::rw" fsuid=7 name="/dev/tty" pid=16815 profile="/usr/sbin/cupsd"
Jan 15 14:21:11 buffer-desktop -- MARK --
Jan 15 14:41:11 buffer-desktop -- MARK --
^Z
[2]+  Stopped                 tail -f /var/log/messages


thanks

type pidgin in a terminal and post the messages you get

---

### Post by ubantuwannabe on 2009-01-16
with respect to [http://ubuntuforums.org/archive/index.php/t-75276.html](http://ubuntuforums.org/archive/index.php/t-75276.html)

then you need to have CVS downloader so
=>is this something we have to download?

gedit ~/amsn-installer
=>is this a new file

[: 50: 0: unexpected operator
/home/buffer/amsn-installer: 172: Syntax error: "do" unexpected (expecting "}")

May I know how to I resolve this?

thanks

---

### Post by kevdog on 2009-01-16
Please provide the following

pidgin -v

And then start pidgin at the command line: pidgin

And post the output.

---

### Post by ubantuwannabe on 2009-01-18
ubuntu 8.10
Pidgin 2.5.2

I could not see any error message when typing pidgin.

tail -f /var/log/syslog
Jan 19 11:32:24 buffer-desktop gdm[4929]: WARNING: Couldn't authenticate user 
Jan 19 11:32:36 buffer-desktop pulseaudio[5247]: ltdl-bind-now.c: Failed to find original dlopen loader.
Jan 19 11:32:36 buffer-desktop pulseaudio[5249]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted

---

### Post by kevdog on 2009-01-18
An MSN bug has been fixed (although I don't know if its the same one you are experiencing) with the newest 2.5.4 release.  I would either install this from getdeb (which I rarely recommend) or compile from source (which is my preferred method): [http://ubuntuforums.org/showthread.php?t=975783](http://ubuntuforums.org/showthread.php?t=975783)

---

