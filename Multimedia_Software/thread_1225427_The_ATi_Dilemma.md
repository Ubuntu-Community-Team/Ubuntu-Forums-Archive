---
title: "The ATi Dilemma"
date: 2009-07-28
forum: Multimedia Software
---

### Post by o2Do on 2009-07-28
Hi there,

I am a newbie to ubuntu, but have found my way around, with lots of help.

But now I am at a tremendous crossroad.  So here is the dilemma.

My wife actually loves Ubuntu, she has a Gateway T-1631 Laptop with an ATi X1270, pre installed Vista. We left it on just so we can watch netflix via the HDMI to the TV.

She hates windows, and prefers Ubuntu, but... We have screen flickering issues. Especially during use of Boxee, XBMC, or other intensive apps.  But sometimes it just happens.

We are currently running Ubuntu 9.04, because 8.04 & 8.10 does not support her wireless card Realtek8187s.

From what I understand I can't install proprietary drivers in this setup, nor can I roll back due to the wireless problem. Is this correct?  

She really wants to use Ubuntu but the screen flicker is driving her nuts.  Please, any advice?

Much appreciated,
Mr. & Mrs. 2D

---

### Post by martinbaselier on 2009-07-28
Check this site:

[http://wiki.cchtml.com/](http://wiki.cchtml.com/)

when it's up again. 

It's the most useful site for installing the ati driver. 

You would have to check the ati website, if you can use their driver on jaunty. If the driver version for your card is 9.3, it won't work. If it's higher, it will.

You could compile the realtek driver for use with ubuntu 8.10, or use the current kernel on it. But then you would need to patch the ati driver. 

For compiling a single kernel module (driver), this tutorial can help.
[http://ubuntuforums.org/showthread.php?t=1012054](http://ubuntuforums.org/showthread.php?t=1012054)

note: if you use the driver from the current kernel and try to compile it on an older kernel, you might need to apply some changes to the source, due to changes in api between kernel versions.

---

### Post by o2Do on 2009-07-28
Thank you very much, first off.

The first link tells me I am screwed as far as the ATi working nicely in 9.04.

The second link seems quite complicated, however I am going to try to understand more clearly the information in the second link as I am sure it may just solve my problem.

---

### Post by ssri on 2009-07-28
> **o2Do said:**
> Thank you very much, first off.

The first link tells me I am screwed as far as the ATi working nicely in 9.04.

The second link seems quite complicated, however I am going to try to understand more clearly the information in the second link as I am sure it may just solve my problem.

From the 2nd link, it says that your realtek driver is supported on 2.6.27-10 and up..

If you enable backports and proposed repositories in intrepid, then you can update your kernel to 2.6.27-14.  Additionally, you can then enjoy full 3d acceleration that comes with Catalyst 9.3.  I recommend installing the catalyst drivers via the manual way.  Good luck!

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by o2Do on 2009-07-29
Hey thanks, I have a fun project tomorrow then :)  My wife and I greatly appreciate it.

---

### Post by ssri on 2009-07-29
also, on my x2300 radeon, I added these to my /etc/X11/xorg.conf after successfully installing fglrx and doing aticonfig --initial -f


Section "Device"
	Option	    "UseFastTLS" "1"
	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "off"
	Option	    "TexturedVideo" "on"
	Option	    "EnableRandR12" "false"


Section "DRI"
	Group        "Video"
	Mode         0666
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection 

and so far, it has worked like a charm...  Also you have to disable xrandr if you want to allow catalyst to control multiple screens...

[http://ubuntuforums.org/showthread.php?p=7170485](http://ubuntuforums.org/showthread.php?p=7170485)

---

### Post by steefjeqv on 2009-07-29
Hi,

Don't install fglrx (closed source ATI driver) on your laptop.
As of the 9.5 (or is it 9.4) version your graphics aren't supported anymore.

You can solve the flicker by upgrading your default ati driver (xserver-xorg-video-ati).

I've written a small how to (post 32 of this thread) :

[http://ubuntuforums.org/showthread.php?t=1174943&page=4]("http://ubuntuforums.org/showthread.php?t=1174943&page=4")

If you've already tried installing fglrx remove it using this command (before you try the how to).:

sudo dpkg --purge fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx

Greetings,
Steven

---

### Post by martinbaselier on 2009-07-29
@ssri. Are you sure the 9.3 driver works on jaunty with an older kernel. As far as I know the 9.3 version doesn't support the xorg version 1.6 as used in jaunty. 

I know there's a patch to make the ati kernel driver work on the new kernel. So if it would only be a kernel problem, it should be possible to fix that. 

I had jaunty on my laptop when the 9.3 version came out and I tried to install it, but due to a change in api between the two xorg versions the driver would not load. The kernel module still loaded fine though at that time.

---

### Post by ssri on 2009-07-29
@martinbaselier

If you read my posts, you will see that I recommended the OP to install intrepid (w/ 2.6.27-14 that supports his realtek) in order to enjoy full 3D from Catalyst 9.3, the version that most definitely is compatible with his card and intrepid (xserver 1.5.2).

---

### Post by martinbaselier on 2009-07-29
I guess I didn't read carefully enough. I overlooked that. Thanks.

---

### Post by o2Do on 2009-07-29
> **ssri said:**
> From the 2nd link, it says that your realtek driver is supported on 2.6.27-10 and up..

If you enable backports and proposed repositories in intrepid, then you can update your kernel to 2.6.27-14.  Additionally, you can then enjoy full 3d acceleration that comes with Catalyst 9.3.  I recommend installing the catalyst drivers via the manual way.  Good luck!

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)


Well I updated to kernel 2.6.27-14.xx but it does not work :(

---

### Post by ssri on 2009-07-29
Did you try to install the restricted modules, the ones that have non-free drivers?  I think they are in there for your kernel, but you have to add in the restricted flag for your repos.

Open up /etc/apt/sources.list in terminal via "gksudo gedit /etc/apt/sources.list" and when you see deb and deb-src followed by ubuntu/ intrepid main (etc...) add in "restricted universe multiverse", so that the lines will be like:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

then go into synaptic, search for restricted and install the ones for your kernel-generic, as well as ubuntu, and restart.

---

### Post by martinbaselier on 2009-07-29
I just found a simple solution in another thread. :)
[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)

---

### Post by o2Do on 2009-07-29
> **steefjeqv said:**
> Hi,

Don't install fglrx (closed source ATI driver) on your laptop.
As of the 9.5 (or is it 9.4) version your graphics aren't supported anymore.

You can solve the flicker by upgrading your default ati driver (xserver-xorg-video-ati).

I've written a small how to (post 32 of this thread) :

[http://ubuntuforums.org/showthread.php?t=1174943&page=4](http://ubuntuforums.org/showthread.php?t=1174943&page=4)

If you've already tried installing fglrx remove it using this command (before you try the how to).:

sudo dpkg --purge fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx

Greetings,
Steven

Ok so here is my update:  I tried to fix the ubuntu 8.10 install, but no go.

So I resorted to Steven's solution I followed his tut, now no more screen flicker in 9.04. But I am having problems enabling compiz.

[quote=martinbaselier]I just found a simple solution in another thread. :smile:
[http://tan-com.com/posts/technology/...i-driver-issue]("http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue")
[/quote]


Thanks! But as I am an uneducated newbie (lol) which do ya'll think is better?

---

