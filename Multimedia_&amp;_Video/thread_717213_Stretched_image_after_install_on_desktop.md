---
title: "Stretched image after install on desktop"
date: 2008-03-06
forum: Multimedia &amp; Video
---

### Post by bharkins on 2008-03-06
I installed Gusty on my desktop today. The first problem was the wrong aspect ratio of the screen image - it is stretched horizontally. The Video is Nvdia GeForce 8800 GTS on an HP f2304 23 inch LCD screen. I am dual booting with Vista where the screen resolution is 1280x768 which is perfect for images. I ran xorg.conf update - no change. The various aspect ratios shown do not include 1280x768 - the nearest is 1280x960. Is there a way to force the correct resolution to 1280x768?

---

### Post by pondochris on 2008-03-08
Did you install the latest driver for your 8800 gts? If not, that is the problem. The best thing to do in that case would be to install envy(just google "envy" and it will be the first one). This will install the latest nvidia driver for you and you will get the proper resolution.

You may run into the problem of "no sound" though. Try to uninstall and reinstall the alsa drivers through synaptic, that should fix it. You may have to compile alsa from source though if synaptic doesn't work. I had to compile alsa from source but I had just installed a custom kernel.

---

### Post by bharkins on 2008-03-09
> **pondochris said:**
> Did you install the latest driver for your 8800 gts? If not, that is the problem. The best thing to do in that case would be to install envy(just google "envy" and it will be the first one). This will install the latest nvidia driver for you and you will get the proper resolution.

You may run into the problem of "no sound" though. Try to uninstall and reinstall the alsa drivers through synaptic, that should fix it. You may have to compile alsa from source though if synaptic doesn't work. I had to compile alsa from source but I had just installed a custom kernel.

That solved the problem. I can now get 1280x768 resolution which gives a correct aspect ratio - no stretch.

(This may have been posted twice - sorry)

Thanks

---

### Post by bharkins on 2008-03-11
> **pondochris said:**
> Did you install the latest driver for your 8800 gts? If not, that is the problem. The best thing to do in that case would be to install envy(just google "envy" and it will be the first one). This will install the latest nvidia driver for you and you will get the proper resolution.

You may run into the problem of "no sound" though. Try to uninstall and reinstall the alsa drivers through synaptic, that should fix it. You may have to compile alsa from source though if synaptic doesn't work. I had to compile alsa from source but I had just installed a custom kernel.

Yes, I have no sound, but that was before the "image stretch" problem. My sound card is Soundblaster X-Fi working fine in Vista and XP. On the volume control icon in the panel, there is a red X - if that is clicked it talks about getting updated gstreamer packages. I did that - no go. I went to the Creative site and downloaded a Linux driver for the card, "XFiDrv_Linux_US-1.04". I have not been able to install it, and Creative is not too much help. I also found an extensive guideline on the Forum for sound driver problems. Looks real complicated. I'll keep working in it, and it seems as though sound with Linux is even more difficult than it was in the Vista beta days. Interestingly, on my old Dell laptop and my new HP notebook, Ubuntu detected the sound cards immediately on install. These both were Conextant cards.

---

### Post by pondochris on 2008-03-13
When I had sound problems I fixed it by doing the following:

1. Download alsa source here [http://www.icewalkers.com/Linux/Software/56600/ALSA-driver.html](http://www.icewalkers.com/Linux/Software/56600/ALSA-driver.html) and untar to Desktop (or wherever you like).

2. cd into directory you chose to untar to in terminal

3. ./configure

4. make

5. make install

I cant remember if I had to run as root though.  this fixed my sound and one other guy's too.  wasn't too complicated.

---

### Post by bharkins on 2008-03-14
> **pondochris said:**
> When I had sound problems I fixed it by doing the following:

1. Download alsa source here [http://www.icewalkers.com/Linux/Software/56600/ALSA-driver.html](http://www.icewalkers.com/Linux/Software/56600/ALSA-driver.html) and untar to Desktop (or wherever you like).

2. cd into directory you chose to untar to in terminal

3. ./configure

4. make

5. make install

I cant remember if I had to run as root though.  this fixed my sound and one other guy's too.  wasn't too complicated.

Did this work with the Creative X-Fi card on a 32 bit Ubuntu OS? My understanding is that the X-Fi driver is only for 64 bit machines and Linux OS.

---

### Post by bharkins on 2008-03-14
> **pondochris said:**
> When I had sound problems I fixed it by doing the following:

1. Download alsa source here [http://www.icewalkers.com/Linux/Software/56600/ALSA-driver.html](http://www.icewalkers.com/Linux/Software/56600/ALSA-driver.html) and untar to Desktop (or wherever you like).

2. cd into directory you chose to untar to in terminal

3. ./configure

4. make

5. make install

I cant remember if I had to run as root though.  this fixed my sound and one other guy's too.  wasn't too complicated.

./configure gives "no command found". The file I downloaded is "alsa-driver-1.0.16" with 53 folders plus many sub-folders. I don't see how it "wasn't too complicate"! Looks to me like a highly knowledgeable Linux user is needed to install the sound driver. When I installed the updated driver for Vista, the sound worked immediately. I'm still interested in getting sound in Ubuntu, but I'm finding it much more difficult than the Nvidia 3D graphics driver installed.

---

### Post by pondochris on 2008-03-15
> **bharkins said:**
> ./configure gives "no command found". The file I downloaded is "alsa-driver-1.0.16" with 53 folders plus many sub-folders. I don't see how it "wasn't too complicate"! Looks to me like a highly knowledgeable Linux user is needed to install the sound driver. When I installed the updated driver for Vista, the sound worked immediately. I'm still interested in getting sound in Ubuntu, but I'm finding it much more difficult than the Nvidia 3D graphics driver installed.

I have the day off tomorrow so I'll double check the steps I took and let you know for sure...I do a bit of posting from my blackberry while at work and don't have access to a PC while there but I would be more than happy to check it out as I have the next 3 days off.  I am just a normal guy who loves ubuntu and I enjoy helping people out.  feel free to PM me and I will see if I can get my IM up and running and will go step by step via IM if you want.

---

### Post by bharkins on 2008-03-15
> **pondochris said:**
> I have the day off tomorrow so I'll double check the steps I took and let you know for sure...I do a bit of posting from my blackberry while at work and don't have access to a PC while there but I would be more than happy to check it out as I have the next 3 days off.  I am just a normal guy who loves ubuntu and I enjoy helping people out.  feel free to PM me and I will see if I can get my IM up and running and will go step by step via IM if you want.

OK, how do I send you a PM - to what address, name, etc?

---

### Post by pondochris on 2008-03-16
ok I checked the steps I took and they work.  the only thing I can think that may be wrong is you aren't in the correct directory.  you have to cd into the alsa driver folder for the "./configure" to work.

I extracted it to my desktop so for step 2  I had to type into terminal 


 cd /home/chris/Desktop/alsa-driver-1.0.16


then for step 5 I had to use sudo so it looked like this

sudo make install

hopefully this clears things up for you

p.s. if you click my name it will give you the option to send a private message.

---

### Post by bharkins on 2008-03-18
> **pondochris said:**
> ok I checked the steps I took and they work.  the only thing I can think that may be wrong is you aren't in the correct directory.  you have to cd into the alsa driver folder for the "./configure" to work.

I extracted it to my desktop so for step 2  I had to type into terminal 


 cd /home/chris/Desktop/alsa-driver-1.0.16


then for step 5 I had to use sudo so it looked like this

sudo make install

hopefully this clears things up for you

p.s. if you click my name it will give you the option to send a private message.

I sent a PM to you, but you may not have seen it yet. Anyway, I did get a lot of text running after doing the configure, make, make install. However, nothing caused the X next to the volume control to go off. I found a Linux driver for my ASUS MB on the vendor CD, but I wanted to make sure it would work in Vista as well. The onboard sound is RealTek AC97. It downloaded OK, but Windows Security wouldn't let it install - not a digital signature, blah,  blah. I can see why people hate M$! I may try the Linux driver alone, just to see if I can get any sound at all in Ubuntu on the desktop.

---

