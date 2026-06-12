---
title: "Sharing Mobile Broadband to Wifi still unanswered?"
date: 2008-12-31
forum: Networking &amp; Wireless
---

### Post by chadraytay on 2008-12-31
Does anyone know how to force ubuntu/network manager to always assume ppp0 mobile broadband is the source of the internet. :confused:

I keep checking google and forums searches for this but::KS

I see several threads of people wanting to load up their mobile broadband and share it with their wifi connection/other computers.

The default response seems to be a link to a thread about sharing between eth0 and eth1 or eth0 and wlan0 and so on.

This does not work. At all.

The moment ubuntu connects to the wifi network it decides that the internet absolutely must be coming from wifi, and ignores everything else.

The only thing that seems to work for me is making gnome-ppp dial at the exact moment wifi is loading so they flick on simultaneously. This is very difficult to do! And then if wifi flickers a moment... poof, gone.
:confused:

---

### Post by oygle on 2008-12-31
I'm having similar problems, no responses to my thread.  :(

Is [this bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/290639") the problem ?

Oygle

---

### Post by chadraytay on 2009-01-07
Is there actually no way to force ubuntu to use only a certain connection as the internet connection?

---

### Post by chadraytay on 2009-01-16
:confused: Wow, no ways to manually select your internet connection...
Suppose I'm gonna have to prop the old laptop up in the corner with WinXP running on it... takes all of 5 seconds to get that convinced where the internet is coming from and where to send it.:-k

---

### Post by oygle on 2009-01-17
Are you running 8.10 (Intrepid), and are you using Network Manager ?

Try to set the Wifi under NM as 'unmanaged', and then when you have the mobile broadband up, try

```
sudo ifconfig ppp0 up
```

and replace ppp0 with the interface name of your Wifi

If you can't get the internet with mobilebroadband, then

```
sudo ifconfig ppp0 down
```

(replace pppo with the interface name of your Wifi)

and then use NM to 'connect'. If it doesn't connect, try a disconnect, then connect. I use mobile broadband and it auto connects, but at boot, I always need to disconnect, then connect.

After you do have the mobile broadband (I guess the interface is ppp0) up and internet going, then bring the Wifi up with that 'ifconfig' command.

Oygle

---

### Post by chadraytay on 2009-01-17
Actaully, I finally found the bug report specifically related to the issue, and the fix.  The fedorah core project was actually annoyed enough by this to track it down. The option "noipdefault" is required to be passed when dialing the cdma connection. In fedorah (and several other distros) this simply involved adding that option to a config file in /etc/sysconfig that networkmanager is set to read before doing anything.  Ubuntu doesn't have this file/setup. I also couldn't seem to find any equivilant config file to put it in.  

Thus, I swapped down to using wvdial to dial up and added the options in the ppp options file. Dials up fine, sets route fine, works fine. Going to check next if I can just pass the option in gnome-ppp as well, since it seems to ignore the options file...

---

### Post by oygle on 2009-01-17
Good that you have had some progress.

---

### Post by Macchi on 2009-01-18
I am also looking for solutions to share a mobile broadband connection with a small group of computers through wifi. Fedora is supposed to manage that with the NM 0.7 but I did not manage to find a way do it with the GUI in Ubuntu.

Command line solutions (i've done that) cannot be handled by most human users and would force many to adopt other operating systems. I can share the connections with Mac and Win but would definitely prefer to use Ubuntu.



PS: I confess to have love/hate feelings towards NM. It is great to have it around but I often have to disable or uninstall it to be able to use certain hardware or manage to connect under certain situations. The bugs are also boring to cope with and I can't really find my way through the logic of the code and architecture of NM. I would welcome a redesign towards a modular and scalable architecture.

---

### Post by oygle on 2009-01-18
Yes, command line solutions are ok for people who love to do that to fix something, but if Ubuntu networking is going to stop people using it (Ubuntu), then the core developers need to do some serious re-thinking. 

If Ubuntu is going to be a 'successful' Linux desktop, that the average home user can install and use via a GUI, then networking must have to be one of the top priorities, surely.

Networking is so 'easy in XP, why is it so 'hard' in Ubuntu ??

Oygle

PS If I do make any progress with using concurrent connections with NM, will post results at [http://ubuntuforums.org/showthread.php?t=1022569](http://ubuntuforums.org/showthread.php?t=1022569)

PPS I was going to look at [UMTSmon]("http://umtsmon.sourceforge.net/")

---

