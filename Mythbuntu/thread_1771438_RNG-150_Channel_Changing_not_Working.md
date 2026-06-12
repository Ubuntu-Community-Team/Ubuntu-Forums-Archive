---
title: "RNG-150 Channel Changing not Working"
date: 2011-05-30
forum: Mythbuntu
---

### Post by chrismurf2900 on 2011-05-30
I have an RNG-150 through Comcast cable.  I have had Mythbuntu/MythTV setup and working to record shows, change channels, etc. for over a year now.  Everything was working fine, until last week.  I have my STB connected via firewire for both recording and changing channels.

Last week, Comcast sent out a firmware upgrade to all set-top boxes to change their menu from Comcast branding to Xfinity branding (and make the menu look "better").  Now I can no longer change channels for the STB.  I'm assuming that the way the box handles changing channels is implemented differently (hopefully they haven't disabled changing channels via that).

I've looked at some other forums, and have tried mythchanger and stb-command to no avail (see this link for other people who are having issues: [http://ubuntuforums.org/showthread.php?t=1693057&page=2](http://ubuntuforums.org/showthread.php?t=1693057&page=2)).

I know I could resort to utilizing an IR blaster, but it's frustrating to know that it was working, but not anymore.

I'm willing to dive into **coding up a fix**, considering a lot of other users are experiencing the same frustrations, but don't know where to begin.

If anyone has a fix for this, or can point me into the right direction to code up a fix, it would be greatly appreciated.
I'm willing to spend time to come up with a solution to fix this issue.

Thanks!

---

### Post by chrismurf2900 on 2011-06-01
Okay, so no luck finding any information on changing channels via firewire for Comcast RNG-150 STB.

For now, I'm going to be using an IR Transmitter to change channels.  I've found the following article which discusses how to configure the external channel changer ([http://old.nabble.com/....html]("http://old.nabble.com/Trouble-with-Comcst-Custom-3-device-remote-and-Cisco-RNG-150-Set-Top--Box-td29144842.html"))

I've also been taking a look into stb-command code to see how that works.  From there, its probably going to be trial and error to see what commands I can send to actually get it to work.

If anyone knows whether or not Comcast has disabled firewire channel changing with their new firmware update, please let me know (I have yet to find out, and don't want to waste time if it's not possible).

---

### Post by bavid on 2011-07-08
I'm in the same boat. Channel changing over firewire worked fine until a couple of weeks ago, but now it's broken. I'm not sure if the exact date, since I was on vacation, but I suspect that it was coincident with the Xfinity "upgrade."

I'm willing to help test, but I don't know much about firewire.

---

### Post by lessfield on 2011-11-28
same boat, but with a  RNG110
I have  comcast, in pittsburgh pa
I lost firewire channel change on nov 24 2011. 
I have tried 4 different firewire cards; using  distros  11.10,  10.10, and 10.04.

I was using 6200ch for over a year with this box. 
plugreport now returns
[FONT="Arial"]libiec61883 error: error reading oMPR
libiec61883 error: error reading iMPR
[/FONT]
If I enter the rng110 diag menu(hold ok/select on power up) and navigate to the '18 TASK STATUS' screen I see 
NAME                 PRI    SIZE STATE
1394  CONTROL TASK   179    8192 Pend
1394 KEYPRESS TASK   179    5120 Ready
1394 SINK TASK       179    8192 Pend

---

### Post by tim273 on 2012-03-19
Are there any solutions to this yet?

---

