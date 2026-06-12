---
title: "Installation with tvout and old crt TV set"
date: 2007-10-25
forum: Mythbuntu
---

### Post by axelsvag on 2007-10-25
I hate to find problem with this excellent software but..... When I try to make a fresh install with the final release and use my tv set set as monitor I just come to the first step press enter to make an install. After about 30 seconds the screen gets a lot of coloured lines and it is impossible to see anything useful. So it seems like there is some with the xorg during install that change so my tv set can´t interpret the signal. 

I will now try my lcdpanel instead and hope that will solve my problem.

---

### Post by OffAxis on 2007-10-25
tv out isn't supported with the default drivers; you must load the proprietary ones for your card to enable it. There's an option in the mythbuntu control center for this.

So you'll want to do the install with your lcd monitor attached, and then swap it out for your tv afterwards.

---

### Post by axelsvag on 2007-10-25
Yes I realise that and nowadays almost everyone have an lcd laying. But as some sort of driver is a default driver and that one work with the crt it does not seems an impossible task to make some tweak so you can use a crttv monitor as installation interface or?

---

### Post by mungewell on 2007-10-25
> **axelsvag said:**
> Yes I realise that and nowadays almost everyone have an lcd laying. But as some sort of driver is a default driver and that one work with the crt it does not seems an impossible task to make some tweak so you can use a crttv monitor as installation interface or?

You seem to be mixing up CRT Monitors (VGA) with CRT TV (Composite video), there a huge number of GFX cards with composite outputs - controlled in different ways....

By the sound of your description your GFX card is booting in some mode where it is capable of creating the composite output and the screen is getting scrambled the moment that X starts messing with GFX card.

Somethings things that could be tried without installing a specific driver:

1) 'Safe mode' - set X to a really low resolution.

2) 'Hacked mode line' - you can hard configure X to output exactly the same line/frame rate as PAL or NTSC. Enough so that you can make a little circuit to create the sync and drive an RGB input on a TV directly.
[http://www.sput.nl/hardware/tv-x.html](http://www.sput.nl/hardware/tv-x.html)

This might make the GFX card maintain the ability to continue a composite output.

3) 'SSH install'. I don't know whether this is possible of Ubuntu, but I recall a comment of Novell Open Audio that they can spec IP/SSH Username/Password as boot options and do the whole (clean) install over SSH.
[http://en.opensuse.org/SDB:Remote_Installation_of_SUSE_LINUX](http://en.opensuse.org/SDB:Remote_Installation_of_SUSE_LINUX)

4) 'VNC install' as above, but X session shared via VNC.

Hope you find a solution.
Mungewell.

---

### Post by axelsvag on 2007-10-26
Yes I mix the expressions. And thank you for your help. What I meant was that the tvout option maybe could be detected autmatically so I don´t have to install the mythbuntu with a crt monitor or lcd monitor. I was to lazy to make some tweaking so I used my old lcd to be able to control the installation. And the mythbuntu final release works much much better than the RC so I am glad that I made a fresh install.

---

### Post by neilneil2000 on 2007-10-28
I have been having similar problems...

I have a Radeon 7000/VE graphics card and I want ot run Mythbuntu on my CRT TV in the lounge.

The card has both S-video and component TV-out.

When the TV is connected, and I put the Mythbuntu CD in for a liveboot I can see everything until the X server starts running and then it becomes a mess.

I have tried installing Mythbuntu with a VGA monitor attached as well, and have installed the fglrx driver, however I cannot seem to enable the  composite tv out, it isn't recognised by fglrx_info.

The S-video is but I can't get any picture out of that either, and the TV scart port is not wired properly for S-Video so the image output during boot is striped with RGB.

Essentially what I want to be able to do is enable the component output on my graphics card so I can use the TV.

Thanks in advance.

---

### Post by toggles on 2009-11-09
I know this is an old thread, but I am still using a Radeon 7000 (RV100) as reported by lspci and I just installed mythbuntu 9.10 and need to get tv out (svideo) working for my old analog set.
My solution was to setup a user to auto login and auto run mythfrontend, then all you need to do was to wait for frontend to start and turn the tv out on..

I added the following line to /etc/rc.local

/root/bin/enable.tvout &

I created the following script as /root/bin/enable.tvout

#!/bin/bash
mb=`/bin/ps aux | /bin/grep mythfrontend  | grep -v grep`
while [ -z "${mb}" ]; do
    sleep 1
    mb=`/bin/ps aux | /bin/grep mythfrontend  | grep -v grep`
done

xrandr --output S-video --set load_detection 1
xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600
xvattr -a XV_CRTC -v 1

You need to configure the the frontend to be 800x600 and set the panel to autohide due to a reported bug, but it seems to work.

Cheers.

---

