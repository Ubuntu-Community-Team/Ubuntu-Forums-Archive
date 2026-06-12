---
title: "error: get-edid is not installed"
date: 2007-12-27
forum: Multimedia &amp; Video
---

### Post by greeninoregon on 2007-12-27
I installed all of my updates today. I was prompted to restart. When I did, it started normally until it came to a screen that said this:


[INDENT]    *Starting anac(h)ronistic cron anacron [ok]
    *Starting deferred execution scheduler atd [ok]
    *Starting periodic command scheduler crond [ok]
    *Checking battery state [ok]
    *Running local boot scripts (/etc/rc.local) [ok][/INDENT]


Where it freezes.


Then it finally goes to a screen that says:

[INDENT]    "Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"
    <Y/N>[/INDENT]

If you choose yes, it takes you to another screen:

[INDENT]    /etc/gdm/failsafexserver: line 47: [: too many arguments
    Warning: Could not retrieve EDID because get-edid is not installed (1)
    <OK>[/INDENT]

Which takes you to:


[INDENT]    The X server is now disabled. Restart GDM when it is configured correctly.
    <OK>[/INDENT]

Then it goes back to:

[INDENT]
    *Starting anac(h)ronistic cron anacron [ok]
    *Starting deferred execution scheduler atd [ok]
    *Starting periodic command scheduler crond [ok]
    *Checking battery state [ok]
    *Running local boot scripts (/etc/rc.local) [ok][/INDENT]

(And doesn't do anything else... just sits there.)

I tried everything on this post: [http://ubuntuforums.org/archive/index.php/t-585420.html](http://ubuntuforums.org/archive/index.php/t-585420.html) and nothing worked. Going through the setup, and trying to install edid didn't work. Edid wouldn't install.


I tried to find an error report for this, but I couldn't. I read somewhere about customizing an edid file, but that's my last resort.

Any suggestions?

(Also, I cross-posted this to absolute-beginner. Not sure if there are rules against cross posting. If there are, let me know and I'll take the other down. I'll probably have better luck here.)

---

### Post by tgilber1 on 2007-12-27
Your Xserver cannot startup probably due to a driver issue with your video adapter.  After a failed attempt, the Xserver warning message appears.  When you finish diagnosing the Xserver problem, your system will continue to boot up showing you the service messages as you startup.

The edid message means one of two things, 

1.  You have a Intel or PPC (Mac) platform and you have not installed the read-edid and parse-edid packages
2.  You have a amd platform where a read-edid package does not exist.  Hence, the /etc/failsafeXServer script tries to run the get-edid command without checking what type of platform.

What type of video adapter do you have?  Please can you provide your xorg.conf and /var/gdm/:0.log* files?

---

### Post by rubbersoul.josh on 2008-01-08
i don't mean to hijack this thread, but i am using an amd and having the same problem.  is there something i can do to bypass the get-edid?

i've tried a number of things including reconfiguring with no luck.  i have ubuntu 7.1 installed using the alternative disc because i was having problems with the live cd. 

thanks for the help

---

### Post by anonymoususer on 2008-01-14
Hello, Having a similar problem.

I was running Feisty with no problems until I installed ubuntu audio studio.  It prompted for reboot and now my story is the same as above.

AMD + nVidia.

-calvin

---

### Post by DrHenley on 2008-01-14
Same here.  AMD Athlon & ATI Radeon 7000.  Installed Ubuntu Satuday and was was working fine when I went to bed last night.  I have dual monitors, and today one of the screens was blank so I rebooted and started getting the error.

I booted from the live CD to see if I could figure out which line in /etc/gdm/failsafeXserver had too many arguments, and possibly fix it, but no such luck.

Do I need an Intel box for Ubuntu to work right?  :confused:

Bummer....:(

---

### Post by DrHenley on 2008-01-14
Duplicate

---

### Post by Yellow Pasque on 2008-01-14
Do you have read-edid installed?
```
sudo apt-get install read-edid
```
If it still asks for 'get-edid', try making a symbolic link.

---

### Post by shields on 2008-01-17
I was getting this error after installing a new graphic card.  I logged in and typed this:
```
sudo dpkg-reconfigure xserver-xorg
```
Then I followed the "wizard" leaving most items at default.

After a reboot, the error was gone and the graphics worked fine.

Good luck.

---

### Post by Astronomerob on 2008-02-02
Hi,

I'm having this same problem too.

Sheild, would you mind going over exactly what you did, because I followed basically what you said and it doesn't seem to have done anything.

Anyone else have other ideas?

Is this a bug and are the Ubuntu developers aware of it?

Thank you.

---

