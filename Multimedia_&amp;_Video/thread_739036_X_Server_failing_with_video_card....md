---
title: "X Server failing with video card..."
date: 2008-03-29
forum: Multimedia &amp; Video
---

### Post by Hailey Stargazer on 2008-03-29
Hello All,
This is my inaugural post, I've been reading this forum for several months now, but this is the first time that I need some help...
I have been busy trying to upgrade my nephew's 8 year old  computer. It was originally running windows millennium when I first received it and he wanted me to upgrade the system to xp...Well, considering the age and resources of this computer (and the new found love I have for this os) I decided to install Ubuntu. I was not able to boot from disk with his computer.....insert ridiculously long story here....so I wound up switching the hard drive from computer A into computer B (an already existing ubuntu machine) and loaded the OS onto computer A's hard drive this way. I rebooted computer A's hard drive while still in computer B and everything works perfectly....
However, when I switch the hard drive back to the original (and 8 year old) computer I get these errors:

starting anac(h)ronistic cron anacron       [ok]
starting deferred execution scheduler atd     [ok]
starting periodic command scheduler crond   [ok]
checking battery state....     [ok]
running local boot scriptsc/etc/rc.local      [ok]
 
/etc/gdm/fail safe x server: line 47 [too many arguments]

From reading these forums I have seen a few instances of similar errors with 'x server' and they all seem to have something to do with video cards....with which I know little about. 
The card in the system (i think) is a nvidia g-force 2xm...at least that is what the chip says...can anyone help with this one?

Oh yeah, I also installed: nvidia-glx-legacy, with no avail then uninstalled the package, then installed nvidia-glx....with no change...

---

### Post by bobbydale on 2008-03-29
Try this:

[http://ubuntuforums.org/showthread.php?p=2323861](http://ubuntuforums.org/showthread.php?p=2323861)

---

### Post by Hailey Stargazer on 2008-03-30
Thank you for the link...I had tried the ' dpkg-reconfigure xserver-xorg ' but not in an actual terminal.. Why would I make such a silly mistake you might ask? Well, I forgot to mention what a Linux novice I am. We are talking only a few months old.
I will try these suggestions, thanks again for responding

---

### Post by Hailey Stargazer on 2008-04-03
Well I am able to run through all of the manual settings for the 'dpkg-reconfigure xserver-xorg'  with no incident. But when I reach the last option for setting the desired default color depth in bits....I enter in the number, press OK and then a small terminal opens from the bottom of the screen (shrinking the above window) awaiting a command....but what do I tell it?
I found somewhere that a way to kill and restart the 'xserver' is <Ctrl><Alt><Backspace>...but this doesn't seem to help. And when I reboot its the same original error message, so its almost like I am exiting without saving the settings....
Any help would be great...
Thanks, 
Hailey

---

### Post by Hailey Stargazer on 2008-04-06
Ok, after successfully editing the dpkg-reconfigure xserver-xorg...

Upon restart I get the ubuntu loading screen now and a light brown background with the capacity to use the mouse but then I get an error message dialog box:
"the greeter application appears to be crashing. Attempting to use a default one"....the system tries and then comes back to the brown screen and displays the error message again..

I open into a terminal and try to manually start server x by typing 'start x'....and I get this error message...

'start x:
   home/username/.serverauth.5033
   home/ username/.x authority
   home/ username/.x authority

x: warning; process set to priority -1 instead of requested priority 0

fatal server error:
Server is already active for display 0 if this server is no longer running,remove /tmp/.xo-lock and start again.

xlib:connection to ":0.0" refused by server
xlib: invalid MTI-MAGIC-COOKIE-1 key giving up
xinit: unable to connect to x server
xinit: no such process (errno 3): server error
-desktop:~$

Anyone know what this error could mean, or any thoughts on how to load the x server.....

---

### Post by Hailey Stargazer on 2008-04-10
Wound up wiping the drive and starting over...used the command 'dpkg-reconfigure xserver-xorg' and manually updated the video card info. Then 'sudo startx', which logged me in as root, to where there were drivers (nvidia accelerated graphics driver) available for install. Once installed and restarted I was able to log in normally....hope this helps someone else!

---

