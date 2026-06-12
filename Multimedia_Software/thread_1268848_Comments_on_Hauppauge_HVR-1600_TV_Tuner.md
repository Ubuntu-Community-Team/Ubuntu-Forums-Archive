---
title: "Comments on Hauppauge HVR-1600 TV Tuner"
date: 2009-09-17
forum: Multimedia Software
---

### Post by bsntech on 2009-09-17
Hello all,

I am considering purchasing the Hauppauage HVR-1600 TV tuner to upgrade from my analog PVR-150 card.

The HVR-1600 has both an analog and digital tuner so I will be able to record the analog cable but also pick up the HD channels.

My question is this - I've read some buzz online about how the HVR-1600 has horrible analog tuner quality.  Others indicate (even with a posted e-mail response from Hauppauage Tech Support) that the PVR-150 is much more superior than the HVR-1600 for the analog tuner.

Does anyone have any kind of reference or experience between these two cards and just how "bad" the difference is between the two?

I am using MythBuntu with the PVR-150 currently and although the PVR-150 is supposed to record in stereo, it does not.  So I was hoping by doing the upgrade to the HVR-1600, I would get stereo recording through analog and I would also have the added bonus of having a digital tuner.

Thank you for any responses!

---

### Post by HappyFeet on 2009-09-17
My friend bought the 1600 and has had no luck getting it going in ubuntu. I, like you, have the pvr150, and can record in stereo. I don't know what the issue is in your case. I would do more research in picking a tv tuner card. Perhaps you should start a thread asking which digital card people are using with ubuntu.

---

### Post by bsntech on 2009-09-18
Hi HappyFeet,

When was the last time your friend had tried to get the HVR-1600 going?  There is a page on MythTV's site now that details some small instructions on it.  It does appear that the cx18 drivers are now installed by default in the new kernel.

However, there is a note that there is a some compatibility problems between the nVidia cards the HVR-1600 - where you have to put an extra variable in your menu.lst when starting up to set the virtual memory to something like 256 MB.

---

### Post by bsmith1051 on 2009-09-18
I can't say anything about the relative tuner strengths but the older PVR-150 has a hardware-based MPEG2 encoder, right?  So, assuming the drivers support it, you should have lower-CPU more-reliable analog recordings with that.

The HVR-1600 (which I have) is primarily a digital OTA tuner -- and OTA recordings are already encoded, hence no CPU demands.

---

### Post by bumanie on 2009-09-18
Look [here]("http://www.mythtv.org/wiki/Tuner_Card") for heaps of information about tuner cards.

---

### Post by BanjoBear on 2009-09-18
I was looking for this all day. [http://ubuntuforums.org/showthread.php?t=1044766&highlight=wintv-hvr+1600](http://ubuntuforums.org/showthread.php?t=1044766&highlight=wintv-hvr+1600). Post 5 worked for me.

---

### Post by bsntech on 2009-09-18
Hi BanjoBear -

Go into your /boot/grub/menu.lst file and add the following onto the end of the command that starts the kernel (the command that starts the kernel will start with "kernel" in the line):

vmalloc=512m

There is a known problem with nVidia cards using the nVidia driver and the HVR-1600.  By passing this in with the start of the kernel, it will get you going.

---

### Post by BanjoBear on 2009-09-19
Hi Bsntech, 
 Thanks for the help. I was getting help with it when I changed my 'cry for help' post. I'm new to Ubuntu and the people on this forum are super helpful. Very glad to be becoming part of this. So, any suggestions on what works best for simply watching tv? Mythtv seems a bit complicated. Thanks again...

---

### Post by bsntech on 2009-09-19
I can't really comment on any other ways to watch TV in Linux except MythTV.  It is a little complicated to get it all setup, but once it is, it is your one-stop shop for all of your movies, tv recordings, and regular TV watching that allows you to pause live TV and pick up where you left off (to go make popcorn or something).

Windows is much easier for just playing regular TV with the built-in Hauppauge WinTV program.

But, after changing to MythTV and getting everything just right, I won't go back to Windows.  I love the fact that the remote with the capture card works great and will even work for other programs in Linux as well (if programmed for that program's use).  The fact that MythTV does an OK job at automatically skipping commercials is a nice feature as well.

Hands down - MythTV is the best bet.  The easiest way to setup MythTV would be if you download MythBuntu and go from there - play with it a little bit and just find some regular documentation online for HOWTOs to get you going.

I have one at my site although I have many things going in with it - digital out (SPDIF) to my receiver, specific VIA Xabre driver settings for Xorg, IR settings for the remote, and various other things.

[http://www.bsntech.com/content/view/591/281/]("http://www.bsntech.com/content/view/591/281/")

---

### Post by oregonbob on 2009-09-19
For what it is worth, I have 9.04 and added Hauppauge 1600. It works fine under Windows, but I cannot get MythTV to work. I get as far as it successfully scanning all my digi channels and it finds them all. But when I load up the frontend and click "Watch TV", the screen goes black as if it will start, then pauses 2 seconds and quits back to the menu. I've spent hours trying to figure out the settings. I found the MythTV guide for that exact tuner, did the steps, but it still don't work.

I'll try some of the suggestions I see above.

---

### Post by bsntech on 2009-09-20
Oregonbob -

Two things that I have seen in my experience to cause the problem you have with the TV not working.

1) Make sure the location where TV is recorded to has read/write access to both the mythtv user and your user account.  Really, just make read/write for all users for that folder.  Live TV is still recorded to that same folder.

2) Ensure that you have properly scanned for channels in the MythTV Backend.  I have seen where there are not any channels in the system and it will do exactly as you mentioned.

---

### Post by oregonbob on 2009-09-20
Yes, That fixed it for me! All I did was move the "default" tv folder to home, made it writable by all and it works!

Thanks!

Now everyone looks like blue Martians, I'll have to explore what is causing that or get used to it.

---

### Post by angelina104 on 2011-01-17
WinTV-HVR-1600 brings over-the-air high definition ATSC digital TV, clear QAM  digital cable TV and analog cable TV to your PC. Watch and record TV in a window  or full screen using high quality MPEG-2.
 Clear QAM TV channels are unencrypted digital TV channels broadcast by your  local cable operator. Many cable operators in North America are transmitting the  high definition ATSC channels on their cable networks. They also broadcast the  basic cable channels in using clear QAM. You can use the WinTV v6 application to  watch and record these channels.
Got some information about this iPad case, but what is the difference between these kind of USB TV tuners, see the links below:
[http://www.espow.com/wholesale-entertainment-home-video-accessories-digital-tv-tuners.html](http://www.espow.com/wholesale-entertainment-home-video-accessories-digital-tv-tuners.html)  
 can any one tell me?

---

### Post by chuckrp on 2012-03-03
The card is working for me. I found that there is only one selection in the list of video cards in the set up that that worked for me. I am still have low volume problems when I record or watch TV using the card. Any suggestions?

---

