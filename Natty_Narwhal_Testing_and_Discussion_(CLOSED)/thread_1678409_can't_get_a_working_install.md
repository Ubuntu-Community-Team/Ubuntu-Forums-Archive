---
title: "can't get a working install"
date: 2011-01-30
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by reiki on 2011-01-30
I downloaded the daily from 1/27and installed to an external eSATA. 1st boot got me to a desktop with unity on the left. But clicking on the little menu icon at teh top resulted in a blank area overlaying teh desktop and unity icons disappeared. Then parts of the task bar at the top disappeared. Right clicking brought them back... kinda. Tried to install the proprietary (fglrx) driver, but it apparently fails. Booted to recovery and tried to repair broken packages. Now it starts the 11.04 splash screen and then crashes and reboots itself. I'm guessing it's a video driver issue, but I can't get a working install to even play with.

Dell Zino HD, AMD Neo X2 dual core, 8GB memory, ATI HD4330 512MB graphics (dedicated graphics card), used ubuntu desktop CD amd64 version. 

I can't even get to a point where I can break it 'cause it's broken from teh get-go. :)  I realize it's alpha, but is this kinda where we are right now? If so I guess I'm going to have to hold off further testing until it actually is bootable here.

---

### Post by coffeecat on 2011-01-30
Presumably that's a **Mobility** HD 4330. If so, my first suggestion is to avoid that fglrx driver for now. I'm using a (desktop) HD4350 which is based on  the same RV710 as yours and Unity is working just fine (sorta! :)) at the moment with the default open-source driver.

Your initial problems are familiar to most of us here. We are in the middle of major transition in the xserver and the daily image you used may very well have landed youin the middle of it.

Here's a suggestion. First, re-install. That's probably quicker than trying to repair what you've got. Second, at first boot, after you put in your username and before you put in your password at the login screen, click on one of the icons at the bottom of the screen and choose 'classic desktop' to get you into the standard gnome desktop, rather than 'Ubuntu Desktop' which is Unity. This is just so that you can update in a stable (we hope!) desktop.

Third - do a 'sudo apt-get update' but before you do an upgrade, install aptitude. Now do 'sudo aptitude safe-upgrade' and let it upgrade. Aptitude is probably safer than apt-get for upgrades at this stage. Or I've been using Synaptic recently, but watch what it wants to remove. Resist the temptation to install the proprietary fglrx driver for now! :wink:

Reboot, and at the login screen, choose 'Ubuntu desktop' for Unity. Hopefully, you'll have a (somewhat) usable Unity desktop.

Have fun!

---

### Post by reiki on 2011-01-30
The ZinoHD i a desktop, BUT the graphics card is in an MXM slot (like a laptop would have) rather than a PCI type slot. Zino HD is an ultra small form factor like a mac mini so it may very well be using a mobile HD4330.

This all works great under 10.04 and 10.10 (my primary OS).

I'll give the reinstall a try. I did the sudo apt-get update before doing sudo apt-get upgrade, but maybe that was my mistake as I didn't use aptitude and safe-upgrade. I'll give it a try now and see what happens. :)

---

### Post by reiki on 2011-01-30
Ok, did a complete reinstall. Logged in to classic desktop on first boot. apt-get upgrade, installed aptitude, aptitude safe-upgrade, done... can't boot at all now. Never even gets to a login screen. :)

Screen goes blank with blinking cursor upper left for a second, then eventually no signal to monitor. I did not do anything with the video driver, but I did see that during the safe-upgrade, it installed a new kernel. Can't boot to new kernel nor can I boot to the originally installed kernel. So.... it's dead. hehehe
I've been using Ubuntu as my primary since I think 2005... I don't ever remember not being able to get it working when testing a development release. BUT... I am getting older and things have changed. :)

This does suck though because I wanted to play with 11.04.

---

### Post by coffeecat on 2011-01-30
That's very disappointing. :(

Don't give up just yet. There was an issue with xserver-xorg-input-evdev which was affecting some people but not others. Thread here if you're interested:

[http://ubuntuforums.org/showthread.php?t=1678264](http://ubuntuforums.org/showthread.php?t=1678264)

Despite the mention of nvidia in the first post I think it may affect systems with other graphics, and there's a mention of it only affecting AMD64 systems in a later post. Whether that's right or not I don't know - all I can say is that my desktop and one of my laptops, both with AMD64 processors and ATI graphics are unaffected.

Whatever, the bugfixed xserver-xorg-input-evdev package has only just come through in the last hour or so - at least with the Ubuntu server I'm using. So - can you boot into recovery mode with networking? You'll have to use ethernet I guess. If so, you could run another aptitude update and aptitude safe-upgrade from the root console to see whether there is an updated xserver-xorg-input-evdev that you can install. It *might* be the answer.

---

### Post by reiki on 2011-01-30
ok well I did a bunch of reading and found the threads about xserver-xorg-input-evdev so I installed AGAIN and did the apt-get update, then installed aptitude, then did aptitude hold xserver-xorg-input-evdev and THEN did aptitude safe-upgrade and NOW I'm booted to 11.04. I can actually boot into the Ubuntu Desktop as well as the Classic. I do get a popup about some system error, but at least I'm in.

NOW.... do I dare UNhold xserver-xorg-inut-evdev and let it upgrade? :)

How do I see what version I'd get if I did that?
.... wait... if I run safe-upgrade I think it tells me what's there and asks me if I want to.... guess I'll find out... wish me luck. :)

---edit--- OK ran safe-upgrade after unholding and it has replaced 2.3.2-6 with 2.6.0-1. 
Going to reboot and see what happens....

---

### Post by coffeecat on 2011-01-30
> **reiki said:**
> wish me luck. :)

Good luck! :wink:

Welcome to all the fun of alpha testing. :p

---

### Post by reiki on 2011-01-30
back... I guess it worked :)
I was able to boot with the new xserver-xorg-input-evdev.

Now... I still get a popup a few seconds after logging in that just says, "System program problem detected Do you want to report the problem now?"

If I say I want to report it I get "Sorry, the program "update-apt-xapian-index" closed unexpectedly. and I'm getting errors while reporting the errors. :)

oh yeah.... I remember having this kind of fun. heheheh

off to do a bit of exploring if this will stay running long enough.

---

### Post by cariboo on 2011-01-30
Several of us are getting the same error, I just cancel the error report window and continue on, it doesn't seem to cause any problems.

---

### Post by sonicb00m on 2011-01-31
tried the daily iso yesterday and Unity will stil&#314; not work with my HD5450. Classic desktop mode works but trying to get Unity to play ball just permanently breaks any attempt to access any state of desktop. Disappointing.

---

