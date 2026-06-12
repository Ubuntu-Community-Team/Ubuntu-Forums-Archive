---
title: "Random hangs on mythbuntu 8.04"
date: 2008-07-03
forum: Mythbuntu
---

### Post by TonyGould on 2008-07-03
I'm having random hangs on my mythbuntu 8.04 server. I need to hard reset, because I can't use Ctr-Alt-F1 to see what's happening, or ssh in. However the machine sounds like it's still whirring away at the same time. At 10:44pm today it seems like the server crashed (this was the time on the welcome screen when I switched the TV on), but I was still able to ping the machine successfully until 10:54pm when I switched it off&on.

There don't seem to be any patterns to it unfortunately :(. And I can't see anything at all helpful in /var/log. For example with the 10:44pm crash there were messages in kern.log, messages, syslog until 10:34 or even 10:40 or so and then nothing until the hard reboot. This has been the same pattern all along.

I'm at my wits end on this one, although I'm fairly new to linux so hope I can get some help here! I've had this machine running for months on ubuntu 7.10, very stable although the mythtv-backend crashed out every so often (but without hanging the kernel). I did an install of 8.04 to a new disk otherwise on the same hardware, but with a 64 bit o/s hoping to squeeze a bit more performance out of the box. Ever since I've been using 8.04 in anger I've had these random hangs. I've ran a memtest just in case, but no issues there.

Recently I've removed powernowd (made the machine faster but didn't fix hangs), switched from wireless networking to wired, and have removed various non-essential services using sysvconfig.

The only remaining things I can think of are to remove more services with sysvconfig (hoping I don't break anything), disconnect non-essential hardware (e.g. the wireless card, the old hard disk which is still connected, an RF keyboard). Maybe revert to 2.6.24-16 kernel.

Anyone any better ideas?

Hope someone can help. This is a real fly in the ointment. I have now moved my laptop away from Windows altogether, and today was watching children's TV out in the garden with my daughter -- she's 3 and will see watching TV this way as completely natural :). Could be v enjoyable all round, but I'm losing days on this!

Tony.

PS the machine is an Asus Pundit-P1 AH2, with Athlonx2 5000 (w/ Nova-T 500 dual tuner).

---

### Post by db260179 on 2008-07-04
First you could try my test kernel

[http://ubuntuforums.org/showthread.php?t=848176](http://ubuntuforums.org/showthread.php?t=848176)

, If no difference, go into the bios, and manually set the IRQ's i.e Reserve IRQ 7,3,4 Force IRQ's to you PCI cards.

Then in the grub boot menu.lst, add in def options, pci=routeirq (dont uncomment the #), then in the terminal run sudo update-grub

The latest ubuntu kernel seems very flakey!, thats why i recompiled a new kernel with the more established SLAB scheduler.

SLUB was introduced at the end of 2007, i've noticed issues cropping up around this problem.

Ideally, send you log files (messages.log,syslog.log, mythtv/mythtv-backend.log, mythtv-frontend.log etc) here, gzip them, then attach to this post.

Thanks

---

### Post by TonyGould on 2008-07-04
Thanks for that I'll give it a go. However I'm rather green at this -- I know next to nothing about the kernel. I've figured I run dpkg i as root, but which packages? There are rather a lot.

```
avm-fritz-firmware-2.6.24-19_3.11+2.6.24.13-19.42_amd64.deb
avm-fritz-kernel-source_3.11+2.6.24.13-19.42_amd64.deb
fglrx-amdcccle_2.6.24.13-19.42_amd64.deb
fglrx-control_8-3+2.6.24.13-19.42_amd64.deb
fglrx-kernel-source_8-3+2.6.24.13-19.42_amd64.deb
linux-headers-2.6.24-19-mythamd64_2.6.24-19.34_amd64.deb
linux-headers-lum-2.6.24-19-mythamd64_2.6.24-19.28_amd64.deb
linux-image-2.6.24-19-mythamd64_2.6.24-19.34_amd64.deb
linux-image-debug-2.6.24-19-mythamd64_2.6.24-19.34_amd64.deb
linux-restricted-modules-2.6.24-19-myth64_2.6.24.13-19.42_amd64.deb
linux-restricted-modules-2.6.24-19-mythamd64_2.6.24.13-19.42_amd64.deb
linux-restricted-modules-2.6.24-19-openvz_2.6.24.13-19.42_amd64.deb
linux-restricted-modules-2.6.24-19-rt_2.6.24.13-19.42_amd64.deb
linux-restricted-modules-2.6.24-19-xen_2.6.24.13-19.42_amd64.deb
linux-ubuntu-modules-2.6.24-19-mythamd64_2.6.24-19.28_amd64.deb
nic-restricted-firmware-2.6.24-19-generic-di_2.6.24.13-19.42_amd64.udeb
nic-restricted-modules-2.6.24-19-generic-di_2.6.24.13-19.42_amd64.udeb
nvidia-glx_96.43.05+2.6.24.13-19.42_amd64.deb
nvidia-glx-dev_96.43.05+2.6.24.13-19.42_amd64.deb
nvidia-glx-legacy_71.86.04+2.6.24.13-19.42_amd64.deb
nvidia-glx-legacy-dev_71.86.04+2.6.24.13-19.42_amd64.deb
nvidia-glx-new_169.12+2.6.24.13-19.42_amd64.deb
nvidia-glx-new-dev_169.12+2.6.24.13-19.42_amd64.deb
nvidia-kernel-source_96.43.05+2.6.24.13-19.42_amd64.deb
nvidia-legacy-kernel-source_71.86.04+2.6.24.13-19.42_amd64.deb
nvidia-new-kernel-source_169.12+2.6.24.13-19.42_amd64.deb
xorg-driver-fglrx_7.1.0-8-3+2.6.24.13-19.42_amd64.deb
xorg-driver-fglrx-dev_7.1.0-8-3+2.6.24.13-19.42_amd64.deb

```

Then once installed presumably I need to edit menu.lst to point to the newly installed kernel, or will installation do that for me?

---

### Post by db260179 on 2008-07-04
I assume your machine is 64bit? - these packages are for 64bit kernel only, the link i supplyed is for i386 kernel.

I did another link, which you have downloaded as well - 64bit version (as shown by you post)

Anyway, you need to just install the following:-

If I386 - not 64bit -
[http://gallery.mulberry.towerhamlets.sch.uk/kerneltest.zip](http://gallery.mulberry.towerhamlets.sch.uk/kerneltest.zip)

In terminal shell, type as follows
sudo dpkg -i
linux-headers-2.6.24-19-mythtv_2.6.24-19.34_i386.deb
linux-image-2.6.24-19-mythtv_2.6.24-19.34_i386.deb
linux-restricted-modules-2.6.24-19-mythtv_2.6.24.13-19.42_i386.deb
linux-ubuntu-modules-2.6.24-19-mythtv_2.6.24-19.28_i386.deb


If you pc is 64bit - generic 64bit kernel
[http://gallery.mulberry.towerhamlets.sch.uk/kernelgeneric.rar](http://gallery.mulberry.towerhamlets.sch.uk/kernelgeneric.rar)

In terminal shell, type as follows

sudo dpkg -i 
linux-headers-2.6.24-19-myth64_2.6.24-19.34_amd64.deb
linux-image-2.6.24-19-myth64_2.6.24-19.34_amd64.deb
linux-restricted-modules-2.6.24-19-myth64_2.6.24.13-19.42_amd64.deb
linux-ubuntu-modules-2.6.24-19-myth64_2.6.24-19.28_amd64.deb

Then still in the terminal, type
sudo gedit /boot/grub/menu.lst
Find the line # def_options=
add pci=routeirq
save,exit
Type, sudo update-grub
Reboot machine, select new kernel

For the log files, copy them like this

goto /var/, using a file manager

then create an archive of the log directory
send it here

Hope this helps?

---

### Post by TonyGould on 2008-07-04
Thanks, my machine has a 64 bit mythbuntu install (and has an nvidia card in it as well). With mythbuntu 7.10 I was running a 32 bit kernel though. I switched to 64 bit to get better transcoding performance and as I hoped it is 20-30% better (once I got rid of powernowd).

Anyway, I couldn't quite get your commands to work as the "mythtv" variants weren't present for all 4 and it complained about bad dependencies if I mixed them up. So I tried the "mythamd64" set as below.

```
sudo dpkg -i sudo dpkg -i linux-headers-2.6.24-19-mythamd64_2.6.24-19.34_amd64.deb linux-image-2.6.24-19-mythamd64_2.6.24-19.34_amd64.deb linux-restricted-modules-2.6.24-19-mythamd64_2.6.24.13-19.42_amd64.deb linux-ubuntu-modules-2.6.24-19-mythamd64_2.6.24-19.28_amd64.deb
```

It boots up with the new kernel, and plays back ok. No crashes in the 1st 5 minutes. From what you're saying it sounds like
(a) there's a chance that reverting to the previous scheduler will stop the hangs
(b) if they don't only then is it necessary to make the bios changes you suggested? - I'm a little leary about messing with the system at that level. (although pci=routeirq is in grub already).

Cheers,

Tony.

---

### Post by db260179 on 2008-07-04
Keep the machine running over the weekend. If no issues, then this defiantly solves this random crashing issue. 

It boots up with the new kernel, and plays back ok. No crashes in the 1st 5 minutes. From what you're saying it sounds like
(a) there's a chance that reverting to the previous scheduler will stop the hangs
(b) if they don't only then is it necessary to make the bios changes you suggested? - I'm a little leary about messing with the system at that level. (although pci=routeirq is in grub already).

Cheers,

Tony.[/QUOTE]

---

### Post by ethernut on 2008-07-04
I tried i386 8.04 and amd64 8.04 and get random hangs in both, infact I cant get it to stay stable long enough to do all the updates..  5-10 Mins max and a hard lock.


I tred the amd64 kernel update.. here's my results..

root@mythtv:/tmp/kernelgeneric# dpkg -i linux-headers-2.6.24-19-myth64_2.6.24-19.34_amd64.deb linux-image-2.6.24-19-myth64_2.6.24-19.34_amd64.deb linux-restricted-modules-2.6.24-19-myth64_2.6.24.13-19.42_amd64.deb linux-ubuntu-modules-2.6.24-19-myth64_2.6.24-19.28_amd64.deb
(Reading database ... 72534 files and directories currently installed.)
Preparing to replace linux-headers-2.6.24-19-myth64 2.6.24-19.34 (using linux-headers-2.6.24-19-myth64_2.6.24-19.34_amd64.deb) ...
Unpacking replacement linux-headers-2.6.24-19-myth64 ...
Preparing to replace linux-image-2.6.24-19-myth64 2.6.24-19.34 (using linux-image-2.6.24-19-myth64_2.6.24-19.34_amd64.deb) ...
Done.
Unpacking replacement linux-image-2.6.24-19-myth64 ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-19-myth64
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Preparing to replace linux-restricted-modules-2.6.24-19-myth64 2.6.24.13-19.42 (using linux-restricted-modules-2.6.24-19-myth64_2.6.24.13-19.42_amd64.deb) ...
Unpacking replacement linux-restricted-modules-2.6.24-19-myth64 ...
Preparing to replace linux-ubuntu-modules-2.6.24-19-myth64 2.6.24-19.28 (using linux-ubuntu-modules-2.6.24-19-myth64_2.6.24-19.28_amd64.deb) ...
Unpacking replacement linux-ubuntu-modules-2.6.24-19-myth64 ...
dpkg: error processing linux-ubuntu-modules-2.6.24-19-myth64_2.6.24-19.28_amd64.deb (--install):
 corrupted filesystem tarfile - corrupted package archive
Read from remote host 192.168.2.101: Connection reset by peer


Something wrong with the package?

Thanks

Ether..

---

### Post by db260179 on 2008-07-05
Looks like you download is corrupt! - try to download the file again, use a download manager

Download [http://gallery.mulberry.towerhamlets.sch.uk/kernelgeneric.rar.md5sum](http://gallery.mulberry.towerhamlets.sch.uk/kernelgeneric.rar.md5sum)
[http://gallery.mulberry.towerhamlets.sch.uk/kernelamd64.rar.md5sum](http://gallery.mulberry.towerhamlets.sch.uk/kernelamd64.rar.md5sum)

To make sure your download is the same

In terminal, type md5sum -c kernelamd64.rar.md5sum


Unpacking replacement linux-ubuntu-modules-2.6.24-19-myth64 ...
dpkg: error processing linux-ubuntu-modules-2.6.24-19-myth64_2.6.24-19.28_amd64.deb (--install):
 corrupted filesystem tarfile - corrupted package archive
Read from remote host 192.168.2.101: Connection reset by peer


Something wrong with the package?

Thanks

Ether..[/QUOTE]

---

### Post by TonyGould on 2008-07-05
> 
Keep the machine running over the weekend. If no issues, then this defiantly solves this random crashing issue.


Good news: no random hangs.
Bad news: repeatedly crashed on playing a DVD (Sound of Music/Doe a Deer: pretty innocuous!)

This problem is similar to what I saw before in that there is nothing I can see in the logs, but different in that it is repeatable. In case you can see anything, I've attached the logs. I had crashes at approx 11:50
12:00, and 12:15.

I've now gone back to the -18 kernel, where I noticed I never had a crash (see next message). I'll post back if I have any problems there. I've just ran through the Sound of Music DVD tracks many times and the -18 kernel has no objection to Julie Andrews!

If I get time, I'll try running your kernel without "pci=routeirq" on the DVD and see if it still hangs. I'm running the -18 kernel with exactly the same settings I had before in the hope that I can do something else with my time for the next few weeks. I really need to get on with non-mythtv stuff: have fallen very far behind with some deadlines.

Tony

---

### Post by TonyGould on 2008-07-05
This post shows that my problems really started with -19 and that -18 was completely stable. My impression is that the kernel releases have been fixing things but -19 has introduced a big problem, at least for me. Your scheduler seemed to make -19 reliable for me, but not bullet-proof.

From 2008-06-09  23:28:58 to 2008-06-21  23:04:12 I used the -18 kernel without a single crash. Things started to go badly wrong within minutes of updating to -19.

Here's the update log for kernel images
```

2:Log started: 2008-04-23  21:36:24
21:Setting up linux-image-2.6.24-16-generic (2.6.24-16.30) ...
29:Setting up linux-image-generic (2.6.24.16.18) ...
44:Log ended: 2008-04-23  21:36:51
3011:Log started: 2008-05-31  21:05:45
3189:Setting up linux-image-2.6.24-17-generic (2.6.24-17.31) ...
3338:Setting up linux-image-generic (2.6.24.17.19) ...
3365:Log ended: 2008-05-31  21:07:57
3485:Log started: 2008-06-09  23:28:02
3523:Setting up linux-image-2.6.24-18-generic (2.6.24-18.32) ...
3562:Setting up linux-image-generic (2.6.24.18.20) ...
3572:Log ended: 2008-06-09  23:28:58
3574:Log started: 2008-06-21  23:04:12
3755:Setting up linux-image-2.6.24-19-generic (2.6.24-19.33) ...
3891:Setting up linux-image-generic (2.6.24.19.21) ...
3934:Log ended: 2008-06-21  23:06:37
4064:Log started: 2008-06-25  01:23:52
4097:Setting up linux-image-2.6.24-19-generic (2.6.24-19.34) ...
4131:Log ended: 2008-06-25  01:24:45

```

and here's the log of crashes using "last | grep crash" not including your test kernel
```

tv       tty7         :0               Fri Jul  4 15:13 - crash  (00:30)    
tv       tty7         :0               Thu Jul  3 22:34 - crash  (00:33)    
tv       tty7         :0               Thu Jul  3 16:47 - crash  (01:32)    
tv       pts/0        :0.0             Wed Jul  2 20:14 - crash  (00:17)    
tv       tty1                          Wed Jul  2 20:08 - crash  (00:23)    
tv       tty7         :0               Wed Jul  2 20:06 - crash  (00:25)    
tv       tty7         :0               Wed Jul  2 08:51 - crash  (11:14)    
tv       pts/1        192.168.1.2      Sun Jun 29 01:51 - crash  (00:17)    
tv       tty1                          Sun Jun 29 01:32 - crash  (00:35)    
tv       pts/0        192.168.1.2      Sun Jun 29 01:32 - crash  (00:36)    
tv       tty7         :0               Sun Jun 29 01:32 - crash  (00:36)    
tv       tty7         :0               Sat Jun 28 20:20 - crash  (00:27)    
tv       pts/0        192.168.1.2      Sat Jun 28 01:37 - crash  (00:07)    
tv       tty7         :0               Sat Jun 28 00:36 - crash  (01:08)    
tv       pts/1        192.168.1.2      Fri Jun 27 23:37 - crash  (00:58)    
tv       pts/0        :0.0             Fri Jun 27 21:34 - crash  (03:01)    
tv       tty7         :0               Fri Jun 27 21:33 - crash  (03:02)    
tv       tty7         :0               Thu Jun 26 11:56 - crash  (00:15)    
tv       pts/0        :0.0             Wed Jun 25 00:08 - crash  (01:11)    
tv       tty7         :0               Wed Jun 25 00:08 - crash  (01:11)    
tv       tty7         :0               Tue Jun 24 19:03 - crash  (02:17)    
tv       tty7         :0               Tue Jun 24 18:14 - crash  (00:48)    
tv       tty7         :0               Tue Jun 24 14:34 - crash  (03:39)    
tv       tty7         :0               Sun Jun 22 11:39 - crash  (00:12)    
tv       pts/1        :0.0             Sat Jun 21 23:32 - crash  (00:33)    
tv       pts/0        :0.0             Sat Jun 21 23:30 - crash  (00:35)    
tv       tty7         :0               Sat Jun 21 23:28 - crash  (00:37)    
tv       pts/0        :0.0             Mon Jun  9 23:05 - crash  (00:14)    
tv       tty7         :0               Mon Jun  9 23:04 - crash  (00:14)    

```

I only had 1 crash prior to -19, and had *no* crashes on -18. Maybe that was because I wasn't using it so heavily, but fingers crossed it will be stable for me.

Thanks again for your help,

Tony.

---

### Post by db260179 on 2008-07-05
Interesting. In your xorg.conf, remove the Option "AddARGBGLXVisuals" "True"

This can cause issues. Also remove the noapic from the grub menu.lst

Looking at you mythbackend.log, you have some database issues going on.

(Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = 8517   AND       networkid        = 9018   AND       transportid      = 8197 AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = 1
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away)

Have you enable proposed updates in you apt sources.list? - i recommend those updates.

Also clearing you bios settings can help, clr cmos jumper on the motherboard. Also reserving IRQ's for serial,parallel ports can help alot - force the IRQ's for the tv tuner card and other pci devices.

Does your machine hard lock, when not using mythtv?

It looks like you mythtv install is borked?
You can try reconfiguring mythtv-database, dpkg-reconfigure mythtv-backend
dpkg-reconfigure mythtv-database

DONT set a root password, leave it blank!

> **TonyGould said:**
> Good news: no random hangs.
Bad news: repeatedly crashed on playing a DVD (Sound of Music/Doe a Deer: pretty innocuous!)

This problem is similar to what I saw before in that there is nothing I can see in the logs, but different in that it is repeatable. In case you can see anything, I've attached the logs. I had crashes at approx 11:50
12:00, and 12:15.

I've now gone back to the -18 kernel, where I noticed I never had a crash (see next message). I'll post back if I have any problems there. I've just ran through the Sound of Music DVD tracks many times and the -18 kernel has no objection to Julie Andrews!

If I get time, I'll try running your kernel without "pci=routeirq" on the DVD and see if it still hangs. I'm running the -18 kernel with exactly the same settings I had before in the hope that I can do something else with my time for the next few weeks. I really need to get on with non-mythtv stuff: have fallen very far behind with some deadlines.

Tony

---

### Post by TonyGould on 2008-07-05
Thanks!

> **db260179 said:**
> 
Interesting. In your xorg.conf, remove the Option "AddARGBGLXVisuals" "True"
This can cause issues.


Will do. This option isn't going to have caused the hard kernel panics I saw though is it? (Note I run xfce so no compiz or anything sophisticated)

> **db260179 said:**
> 
Also remove the noapic from the grub menu.lst


I put this in to resolve the "MP-BIOS BUG 8254 timer not connected" message. Searching on the net noapic seems to be the solution to this one -- did I do something wrong?

> **db260179 said:**
> 
Looking at you mythbackend.log, you have some database issues going on.

(Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = 8517   AND       networkid        = 9018   AND       transportid      = 8197 AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = 1
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away)


This is only after mythwelcome issues the shut down command: I guess MySQL shuts down before mythtv-backend. For example:

```

2008-07-05 11:19:32.546 I'm idle now... shutdown will occur in 150 seconds.
2008-07-05 11:19:33.540 AFD: Opened codec 0x8c1a50, id(MPEG2VIDEO) type(Video)
2008-07-05 11:19:33.542 AFD: codec MP3 has 2 channels
2008-07-05 11:19:33.543 AFD: Opened codec 0x8e5630, id(MP3) type(Audio)
2008-07-05 11:19:33.543 AFD: codec MP3 has 1 channels
2008-07-05 11:19:33.544 AFD: Opened codec 0x8e5c70, id(MP3) type(Audio)
2008-07-05 11:19:33.545 AFD: Opened codec 0x8e62b0, id(DVB_SUBTITLE) type(Subtitle)
2008-07-05 11:19:33.620 Preview: Grabbed preview '/var/lib/mythtv/recordings/1071_20080705105900.mpg' 720x576@154s
2008-07-05 11:22:01.717 MainServer::HandleAnnounce Monitor
2008-07-05 11:22:01.718 adding: tv as a client (events: 0)
2008-07-05 11:22:01.719 MainServer::HandleAnnounce Monitor
2008-07-05 11:22:01.720 adding: tv as a client (events: 1)
2008-07-05 11:22:01.740 CheckShutdownServer returned - OK to shutdown
2008-07-05 11:22:01.747 Running the command to set the next scheduled wakeup time :-
						mythshutdown --setwakeup 2008-07-05T15:33:30
2008-07-05 11:22:01.887 Running the command to shutdown this computer :-
						sudo -H mythshutdown --shutdown
2008-07-05 11:22:02.781 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = 16000   AND       networkid        = 9018   AND       transportid      = 12290 AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid = 1
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

```

> **db260179 said:**
> 
Have you enable proposed updates in you apt sources.list? - i recommend those updates.


No -- I'll try that and see what comes in. But to be honest I'm wary of updates after (it seems) the -19 kernel broke my system so spectacularly.

> **db260179 said:**
> 
Also clearing you bios settings can help, clr cmos jumper on the motherboard. Also reserving IRQ's for serial,parallel ports can help alot - force the IRQ's for the tv tuner card and other pci devices.


The first part means taking the machine apart doesn't it? The second part is BIOS settings, right?


> **db260179 said:**
> 
Does your machine hard lock, when not using mythtv?


It's always running mythbackend, so hard to say. I've had it hang when it's not doing very much at all, so the answer to that is a qualified yes.

> **db260179 said:**
> 
It looks like you mythtv install is borked?
You can try reconfiguring mythtv-database, dpkg-reconfigure mythtv-backend
dpkg-reconfigure mythtv-database


Is this because of the SQL errors at the top? If so, false alarm on that one, so not to worry.

> **db260179 said:**
> 
DONT set a root password, leave it blank!


This will leave the previous password intact I take it?

Best wishes,

Tony.

---

### Post by db260179 on 2008-07-07
Will do. This option isn't going to have caused the hard kernel panics I saw though is it? (Note I run xfce so no compiz or anything sophisticated)

It can cause issues!



I put this in to resolve the "MP-BIOS BUG 8254 timer not connected" message. Searching on the net noapic seems to be the solution to this one -- did I do something wrong?

Just leave it out for the time being.



This is only after mythwelcome issues the shut down command: I guess MySQL shuts down before mythtv-backend. For example:

Have a look at this thread - [http://ubuntuforums.org/showthread.php?p=5147324](http://ubuntuforums.org/showthread.php?p=5147324)

Also, have you enabled the weekly mythtv0.21 fixes? - this can fix loads of issues, found after the inital release of mythtv0.21

[http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)



No -- I'll try that and see what comes in. But to be honest I'm wary of updates after (it seems) the -19 kernel broke my system so spectacularly.

It's worth a try, and my systems are running fine with the proposed updates.



The first part means taking the machine apart doesn't it? The second part is BIOS settings, right?

Correct! - Make a note of you bios settings, also check if you have the latest bios code.


It's always running mythbackend, so hard to say. I've had it hang when it's not doing very much at all, so the answer to that is a qualified yes.

Do a test, turn off the mythtvbackend (sudo /etc/init.d/mythtv-backend stop)

See if the pc, still crashes.


Is this because of the SQL errors at the top? If so, false alarm on that one, so not to worry.

Errors are mysql related. Because of the constant crashing, it may of damaged the mysql database.

Easily fixed, goto /usr/share/doc/mythtv-backend/contrib, extract myth.find_orphans.gz and myth.rebuilddatabase.pl.gz
Make them executable.

then run in terminal,

sudo apt-get install libtime-format-perl, then ./myth.rebuilddatabase.pl --user=mythtv --pass=*your password of mythtv* --database=mythconverg --try_default

./myth.find_orphans.pl --user=mythtv --pass=*your password of mythtv* --database=mythconverg --dodbdelete --dodelete

First commmand rebuilds the database, the second finds any orphaned entry's and removes them.




This will leave the previous password intact I take it?

Correct, you only really need to know the mythtv password within the database. (located in /etc/mysql/my.cnf)


It might be worth doing a dual boot, with a normal copy of ubuntu, and see if the machine still crashes? it might be unrelated to mythbuntu, and apply to all the version of ubuntu!

---

### Post by TonyGould on 2008-07-07
Hi,

Sorry, but I'm getting seriously pushed to spend time on my job, my studying and my family, so if I don't reply in depth for a while it's because I've run out of time for mythtv for a while. Current status is that this morning before you replied I had a couple of crashes with the -18 kernel, which puts paid to the idea that there is an issue specific to the -19 kernel.I guess that unless something else changed in the updates, I just wasn't using -18 heavily before (it was probably when I was still on gutsy on the other disc).

I switched this morning after the crashes to the realtime kernel (linux-image-rt package). Looking at the wiki, [http://rt.wiki.kernel.org/index.php/Frequently_Asked_Questions](http://rt.wiki.kernel.org/index.php/Frequently_Asked_Questions), I wouldn't be surprised if this helps, as it seems like there is a load of code where the kernel would wait that is now interruptible. However, I know now that I need to leave it at least half a week of normal use before judging whether anything has improved or not. I'll post back then.

best wishes,

Tony.

PS some good ideas in your post, but don't I get the latest mythtv already from having it in synaptic? I pulled down some (v minor) updates just a few days ago.
PPS I can see where you're coming from now with the pci=routeirq and bios changes to allocate the pic up-front. It's all about making the machine more deterministic so that things don't get allocated randomly. Given how often my machine auto shuts down and starts up that sounds like a good thing to do.

---

### Post by TonyGould on 2008-07-22
Quick update: I've been 2 weeks now on the realtime kernel, and no lockups. I've twice had to kill the backend -- in both cases I was able to use Crtl-Alt-F1 to get a terminal going. Given I was having hangs 2-3 times per day prior to that, this is a big improvement.

I'm still going to try out some of those things you mentioned, e.g. enabling the weekly mythtv updates, but for the moment it's really nice to be able to use the machine to enjoy watching TV shows rather than spening 90% of the time swearing and losing sleep trying to fix it.

Tony

---

