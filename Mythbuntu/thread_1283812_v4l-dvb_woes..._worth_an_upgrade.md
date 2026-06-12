---
title: "v4l-dvb woes... worth an upgrade?"
date: 2009-10-05
forum: Mythbuntu
---

### Post by micah161 on 2009-10-05
Although I am newly registered, I have been a very satisfied 8.10 server user for 10 months.  Recently decided to get rid of my TV and replace it with a MythTV frontend/backend.  Here's what I started with:

Pentium 4 Northwood 2.4GHz
Asus P4P800 Deluxe MB (AGP only)
1 Gb Memory
ATI Radeon AIW 9600 PRO 128 MB AGP Video Card/Tuner - (since I was just running the server, this card was pulled out most of the time)

I wanted to tune OTA HD content so I bought a Hauppauge 1600 PCI card (picked this because I also wanted the FM tuner to use with Squeezecenter).

THE PROBLEM:
The ATI video card isn't supported in Jaunty (Xwin 1.6) but I can't get the v4l-dvb module to compile under Intrepid (2.6.24-24 Kernel).  I could either wait until they figure out the bug or upgrade the video card.

I could pick up a Nvidia 256MB 6200 card for $40, but I'd like to get one of the new 1920x1080 e-IPS displays (currently using a 19"CRT) and use it to watch HD content and 1080i AVCHD files from my video cam.

I suspect the Nvidia 6200 will be incapable of these tasks and don't really want to waste the ATI card.  As you can see, I'm not really on the bleeding edge of high tech.  Is the 6200 better/worse than the ATI performance wise?  It is worth upgrading to an "unsupported" kernel to get v4l-dvb to compile?  Is HD viewing realistic for this hardware?  

Thanks, micah

---

### Post by micah161 on 2009-10-06
UPDATE:  I can get a PCI (not express) 8400 GS card for $40 so I can take advantage of the VDPAU drivers.  However, the AGP 8X is 2.1Gb/s which seems a lot faster than the 133MB/s on the PCI --plus my tuner card is on the PCI bus too.  Any suggestions or should I give up and start building a new system?

---

### Post by silverdulcet on 2009-10-06
> **micah161 said:**
> Although I am newly registered, I have been a very satisfied 8.10 server user for 10 months.  Recently decided to get rid of my TV and replace it with a MythTV frontend/backend.  Here's what I started with:

Pentium 4 Northwood 2.4GHz
Asus P4P800 Deluxe MB (AGP only)
1 Gb Memory
ATI Radeon AIW 9600 PRO 128 MB AGP Video Card/Tuner - (since I was just running the server, this card was pulled out most of the time)

I wanted to tune OTA HD content so I bought a Hauppauge 1600 PCI card (picked this because I also wanted the FM tuner to use with Squeezecenter).

THE PROBLEM:
The ATI video card isn't supported in Jaunty (Xwin 1.6) but I can't get the v4l-dvb module to compile under Intrepid (2.6.24-24 Kernel).  I could either wait until they figure out the bug or upgrade the video card.


I'm curious what sort of problems you ran into compiling the module for Mythbuntu Intrepid 8.10? I've been compiling the v4l-dvb driver for every kernel update since I installed 8.10 and the HVR-1600 has never had a problem. Did you follow these instructions? 

[http://www.mythtv.org/wiki/Hauppauge_HVR-1600]("http://www.mythtv.org/wiki/Hauppauge_HVR-1600")

If so, what sort of errors did you get? Post them here, and most likely we can figure out what went wrong.

> UPDATE: I can get a PCI (not express) 8400 GS card for $40 so I can take advantage of the VDPAU drivers. However, the AGP 8X is 2.1Gb/s which seems a lot faster than the 133MB/s on the PCI --plus my tuner card is on the PCI bus too. Any suggestions or should I give up and start building a new system?

The PCI version of the 8400 GS card works fine from all the reports I've read. Its important to make sure you get the 512MB version to ensure smooth playback. It won't support the Advanced De-interlacing, but otherwise works very well.

---

### Post by micah161 on 2009-10-06
I was following these instructions:

[http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

But the Mercurial instructions seem to be the same (hg clone, make, etc).

I get the same errors they have been getting on the Daily Build Tests for the 2.6.24-7-i686 kernel:

[http://www.xs4all.nl/~hverkuil/logs/Monday.log]("http://www.xs4all.nl/%7Ehverkuil/logs/Monday.log")

I figured if the compile error showed up on the log, then it was a "known" bug.

EDIT:  The 512MB version of the 8400 gs is $55 and has a fan.  Still debating how much $$ to invest in old tech.

---

### Post by silverdulcet on 2009-10-06
> I get the same errors they have been getting on the Daily Build Tests for the 2.6.24-7-i686 kernel:


I just recently switched to Mythbuntu 9.04, but when I was running 8.10 I believe the kernel version I was compiling v4l-dvb for was 2.6.27-11 or so. Granted this was for an amd64 version. From the logs in the link you posted, it compiled fine in both the amd64 and i686 versions of 2.6.27-11. Is there a reason that your installation doesn't have the latest kernel for Intrepid? I am no expert, perhaps I'm missing something here.

My system was:
AMD64 3200+ 
Sapphire ATI 9600 AGP 128MB
HVR-1600

It was able to play live and recorded ATSC with normal playback settings using the fglrx-9.3 drivers and XVideo acceleration.

---

### Post by micah161 on 2009-10-06
As far as I could tell, I had the latest "supported" kernel for Intrepid (actually 8.04 Desktop LTS).  Maybe I should explore the "unsupported" kernel options. 

Good to know the 9600 will work for ATSC.  If I get that far I can get rid of my TV.  I assume you upgraded your video card when you moved to Jaunty or did you find another solution?

---

### Post by JMcFly on 2009-10-06
Try the xserver-xorg-video-radeon open source driver, it gets the older ATI cards working in Jaunty but at slightly reduced power.
 
I'm running P4 2.4ghz, 2gb ram, 512meg ATI X1650 Pro and my ATSC playback will drop frames occasionally in Jaunty. The 9600 will really put you at a disadvantage.

---

### Post by silverdulcet on 2009-10-06
> **micah161 said:**
> As far as I could tell, I had the latest "supported" kernel for Intrepid (actually 8.04 Desktop LTS).  Maybe I should explore the "unsupported" kernel options. 

Good to know the 9600 will work for ATSC.  If I get that far I can get rid of my TV.  I assume you upgraded your video card when you moved to Jaunty or did you find another solution?

Thats where the confusion is. If you are running 8.04 that is Hardy Heron. In your first post you said Intrepid. See the ubuntu releases with names and version numbers here:
[http://releases.ubuntu.com/]("http://releases.ubuntu.com/") 

According to most the Intrepid 8.10 version of Mythbuntu has support for the HVR-1600 in the kernel with perhaps just a firmware download. It wasn't my experience. Which is why I was building the v4l-dvb source myself. So if you upgrade to 8.10 you should be able to get your tv tuner to work with just adding the firmware or even building from source.

Before I upgraded to Jaunty, I upgraded the hardware as well.
Athlon II X2 240
GIGABYTE GA-MA785GM-US2H

So atm, I'm using the onboard HD4200 graphics. 

To get back on topic, I didn't experience any frame dropping with the previous hardware. I was using the last fglrx version (9.3) to support the 9600 (rv350) graphics card. I used fglrx instead of the open source drivers since I wasn't able to adjust the overscan on my HDTV with the open source drivers and the fglrx drivers allowed me to adjust the screen perfectly.

Not sure how an Athlon 64 3200+ compares in performance to your Pentium 4 Northwood 2.4GHz, but I'd give it a try and see how well it performs for you.

---

### Post by micah161 on 2009-10-06
thanks.  for some reason I had it stuck in my head that the animal names didn't change when you go from an .04 to a .1 release.  then i saw that 9.1 will be a koala.

i am in the middle of the 8.10 desktop install now - i'll post an update when I know the answer.

---

