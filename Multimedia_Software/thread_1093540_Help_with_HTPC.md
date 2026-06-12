---
title: "Help with HTPC"
date: 2009-03-11
forum: Multimedia Software
---

### Post by drewv on 2009-03-11
I'm new to Linux and Ubuntu, but after doing a little research I want to use Ubuntu for my HTPC I'm planning on building.  I wanted to make sure I'm planning everything correctly before I buy any parts and run into issues I could've prevented.

Here's what I'm planning on so far, using MythTV w/a dual tuner HDTV card for my PVR, a wireless network card for internet access, a blu-ray reader/dvd burner, hdmi to a 46" Samsung LCD TV, an AMD Athlon 64 X2 4400+ Brisbane 2.3GHz dual-core CPU, and integrated graphics.  Does everything look like it will work so far?

A couple of questions I had are:

1)Which chipset is a better choice, AMD's 780G or Nvidia's 8200/8300?  I think the 780G has better support for HD audio.  Am I right?  

and 2) Do I need to check all of the components to make sure they are compatible with Ubuntu, or only certain ones?

Oh yeah, I might try to add a RAID system to it in the future. 

Let me know if you have any suggestions on making this go smoothly.

Thanks!

---

### Post by Bloemetjesgordijn on 2009-03-12
Hi

I have also a HTPC setup (not Mythbuntu, just Ubuntu) with a 780 motherboard. It runs fine (Pls notice I added to mine HTPC an add graphical card with crossfireX) 

Regarding the sound, I have no idea how the onboard HD sound is. I am currently using a dedicated soundcard. (Wanted to have good / great audio)

If I were you I would check the linux support on:
- the digital tuner (mine is a Hauppauge PVR 3000) not working with the current kernel. 
- wireless card (I have seen some threads regarding wireless cards (it should be working)

Furthermore if your HTPC casing has a display on it, google the internet for any linux related issues.

Last word of advise, be prepared that this HTPC project, will become a new hobby that will eat up all available time. 

Cheerz

Bloemetjesgordijn

---

### Post by drewv on 2009-03-14
Thanks!

I was hoping to be able to use the on board video to be able to cut down on cost and to leave more PCIe slots open for the tuner(s).  Does anyone know which onboard video supports blu-ray playback and works well MythTV?

---

### Post by steefjeqv on 2009-03-15
Hi,

First of all, bluray on Linux isn't possible (at the moment). A bluray system needs certified components before it will display any commercial bluray content. 
Stupid isn't it ? But dont't blame GNU/Linux, blame the multimedia industrie for trying to sell us something that is locked down. 
Perhaps unencrypted content is possible.

Next, if you want hardware decoding then the only viable solution (for now) is Nvidia with it's VDPAU. This only works with the 8XXX or 9XXX range of their cards (h264, mpeg2, VC-1 etc....).

Greetings,
Steven

---

### Post by drewv on 2009-03-15
I hadn't figured that out about the bluray not working with Linux.  Bummer!  Do you if anything is in the works for getting bluray support?  It might be a couple of months before I can get around to this project anyway.

---

### Post by Bloemetjesgordijn on 2009-03-16
Hmm, I didnt know there were issues with BlueRay in Linux. Good thing I didnt buy a BlueRay player....

However, I can play / view downloaded BlueRay content perfectly

Cheerz

Bloemetjesgordijn

---

### Post by steefjeqv on 2009-03-17
Hi,

Here's a link which should explain things :

[http://www.phoronix.com/scan.php?page=news_item&px=NzE0Ng]("http://www.phoronix.com/scan.php?page=news_item&px=NzE0Ng")

Greetings,
Steven

---

### Post by Bloemetjesgordijn on 2009-03-20
> **steefjeqv said:**
> Hi,

Here's a link which should explain things :

[http://www.phoronix.com/scan.php?page=news_item&px=NzE0Ng]("http://www.phoronix.com/scan.php?page=news_item&px=NzE0Ng")

Greetings,
Steven



Thx

---

### Post by TomB19 on 2009-03-20
> **Bloemetjesgordijn said:**
> However, I can play / view downloaded BlueRay content perfectly

Here too.  I can play blueray derived material on my older nVidia system as well as my 780GX based system.  Both systems use built in video and audio.

Personally, I'm done with nVidia and expect them to be out of business within 3 years.

Both systems output toslink and sound brilliant.  There is no benefit to using a sound card if you're going to connect to your A/V receiver optically.

Next, I wouldn't build up a big HTPC system.  The smaller and lighter the better.  Why would anyone want to have a bunch of dedicated resources or a hot and loud system beside their TV?

My backend system is 64 bit Kubuntu 8.10.  I run a quad core system with 8 GB RAM, software RAID 5 array of 6 x 750 GB drives (soon to be upgraded to 1.5 TB drives), dual tuner cable card, etc., etc.  It's what you want to transcode and store a ton of video.  The problem is, it's neither small, cool, or quiet.

The backend is housed in an Antec P182 case with an 80+ certified PSU.  Don't forget, it will be running all the time so it's worth while to have an efficient PSU and a case that runs relatively cool and quiet.

For a front end, I run a system with integrated graphics.  It's an nVidia chip set and it's a few years old but it runs perfectly.  Remember, it only has to stream video so it doesn't much matter about CPU power.  It has no hard disk, floppy, or cards of any kind.  It's a PSU, DVD drive, motherboard, CPU, IR receiver, 1 GB of RAM, and a single 80mm fan is fine since it doesn't create much heat (Panaflo L80 - so it's pretty much silent).

Also, I can turn the front end off whenever I'm not using it so it makes zero noise... not that I can hear it when it's on.

Best of all, it boots a pre-packaged PXE image over the network.  It boots quickly, like the set top box that it is.  I can try a new image and if it goes sour, I can just point my tftp server back to the old image and my TV is running again.  Do not underestimate the power of this capability.  Nothing is more frustrating than doing an upgrade, have everything go south, and not being able to watch TV until it's all fixed.

Here is the MiniMyth web site.  It's super slick.

[http://www.minimyth.org/](http://www.minimyth.org/)

---

### Post by ghat on 2009-03-20
hi

Other websites I use

[http://www.silentpcreview.com/](http://www.silentpcreview.com/)
[[SIZE=2][COLOR=Black]**[FONT=Arial]Guide to Building a HD HTPC[/FONT] **[/COLOR][/SIZE]]("http://www.avsforum.com/avs-vb/showthread.php?t=940972")
**[COLOR=Black][[B]HTPC - Linux Chat**]("http://www.avsforum.com/avs-vb/forumdisplay.php?f=76")[/COLOR]
[/B]

I was waiting for the NVidia 9XXX mGPU, when I bought the GMAX4500HD which 
is a total misery... dont buy that board.....

Next I am looking at...
[http://www.engadget.com/2009/02/20/nivida-ion-platform-to-support-via-nano-processors-this-year/](http://www.engadget.com/2009/02/20/nivida-ion-platform-to-support-via-nano-processors-this-year/)

my 2c

Ghat

---

