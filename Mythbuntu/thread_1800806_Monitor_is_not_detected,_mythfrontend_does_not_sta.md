---
title: "Monitor is not detected, mythfrontend does not start"
date: 2011-07-09
forum: Mythbuntu
---

### Post by samihs72 on 2011-07-09
Hi! I have LG 42LD750N TV and I faced problem when TV is in "standby" state: It's not sending any signal to ATI Radeon HD 3200 graphic card. When my mythtv PC starts to record TV program and TV is off/standby, mythfrontend cannot start because xorg is not started without monitor detection. I am using open radeon driver.

Is there any way to force to load and connect e.g. HDMI setup without monitor detection? Or is there some way to load some "dummy" Xorg configuration for starting x?

I am using Mythbuntu 10.04+enabled repositories (mythtv 0.24). I am attaching my current xorg.conf

---

### Post by stratoscape on 2011-08-17
Hi,
I wish I was posting good news but I saw this and just wanted to say I too have the same issue with my Vizio (heck this is not even related to the equipment) Something a few years changed with an update to X10 or VNC or something cause my mythbackend which was headleass forever but after a update now requires a monitor to be detected or the system halts. 

I do not specialize on Linux so I have been trolling this forum for 2 years waiting for a answer but my work around is to make sure the monitor/LCD is on and ready on the input your Mythtv is on and it will boot every time.

frustrating thing is training the family to do this (I just wish some one could explain this and wow to resolve it

good luck

Strato

---

### Post by BicyclerBoy on 2011-08-17
IF you were using a nVidia graphics you would insert this into your /etc/X11/xorg.conf
Option "ConnectedMonitor" "string"
where "string" could be "CRT" "DFP" etc..

I suspect there would be a similar X server option for ATI/AMD

---

### Post by nickrout on 2011-08-18
look in the logs.
/var/log/Xorg.0.log

---

### Post by samihs72 on 2011-08-22
> **nickrout said:**
> look in the logs.
/var/log/Xorg.0.log
Hello! Yes, that's the case that these HDMI-0 and DVI-0 both seems to be "disconnected" /var/log/Xorg.0.log, even cable has been connected to LG TV. :confused:

When LG tv is on, HDMI-0 or DVI-0 shows "connected" as it should.

---

### Post by BicyclerBoy on 2011-08-23
The frontend does not need to be running for recordings to be made.

Does the backend have any requirement for X server to be started ? I'm not sure.

You do not have to be logged in for a recording to be made.
My system starts up & records (if turned off), then shuts down again (not logged in).

You could try something like this
aticonfig --enable-monitor=tmds1 --effective=now

in some x server init script..

---

### Post by samihs72 on 2011-08-24
> **BicyclerBoy said:**
> The frontend does not need to be running for recordings to be made.

Does the backend have any requirement for X server to be started ? I'm not sure.

You do not have to be logged in for a recording to be made.
My system starts up & records (if turned off), then shuts down again (not logged in).

You could try something like this
aticonfig --enable-monitor=tmds1 --effective=now

in some x server init script..
Hi! The problem is not recording, they work just fine without monitor detection, backend works without starting xorg.

The problem is, when backend has started recording and LG TV has been off, I cannot get mythfrontend started, because xorg has not been started. I have to restart mythtv box with LG TV on for getting Mythfrontend open. That's not good option during TV show recording.

---

### Post by mathog on 2011-08-25
[http://www.nvnews.net/vbulletin/showpost.php?p=1957437&postcount=6](http://www.nvnews.net/vbulletin/showpost.php?p=1957437&postcount=6)

---

### Post by BicyclerBoy on 2011-08-26
That's what I posted in #3
I have been using that for > 3yrs.

But the OP is using AMD/ATI not nVidia...
So I posted #6.

We have not found out if it works yet..

---

### Post by samihs72 on 2011-09-11
Hi Fellows! Thanks for your replies... The problem is, that I am using open radeon driver, which has very good quality of video. So I am not anxious to change to Catalyst driver, because I used to have problems with tearing video quality...

I made bug report about this problem, maybe some day we will have option to ConnectedMonitor and UseDisplayDevice options for open radeon driver.

 [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/808622](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/808622)

---

### Post by nickrout on 2011-09-11
> **samihs72 said:**
> Hi! The problem is not recording, they work just fine without monitor detection, backend works without starting xorg.

The problem is, when backend has started recording and LG TV has been off, I cannot get mythfrontend started, because xorg has not been started. I have to restart mythtv box with LG TV on for getting Mythfrontend open. That's not good option during TV show recording.

well for a start why restart the whole machine? ```
sudo restart gdm
``` will start xorg.

---

### Post by samihs72 on 2011-09-16
> **nickrout said:**
> well for a start why restart the whole machine? ```
sudo restart gdm
``` will start xorg.
Hi nickrout! I have tried this and it caused problem, that new x session will be started but it come to login page and my username and password are not acceptable and I never got X session and mythfrontend open anymore... :confused:

Have anyone tried start Mythbuntu combined frontend-backend machine without monitor (xorg does not start) and got frontend restarted successfully somehow without confusing frontend startup setup?

---

### Post by BicyclerBoy on 2011-09-16
No idea if it will make any difference but the right syntax now is:

sudo service gdm restart

---

### Post by samihs72 on 2011-11-25
> **BicyclerBoy said:**
> No idea if it will make any difference but the right syntax now is:

sudo service gdm restart
Could someone, who is expert with mythtv and can test, following scenario:

1. Plug off monitor cable from mythtv fe/be machine.
2.  Start mythtv machine. Xorg and mythfrontend should not be started...
3. Plug in monitor cable and give command in Terminal:
sudo service gdm restart

What will happen? Do Xorg and mythfrontend starts properly?

I have situation, that mythtv is primary DVB system now, it has to be stable.

BR
Sami

---

