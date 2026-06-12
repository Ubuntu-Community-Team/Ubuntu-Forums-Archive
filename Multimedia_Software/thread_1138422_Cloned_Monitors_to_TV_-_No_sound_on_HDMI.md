---
title: "Cloned Monitors to TV - No sound on HDMI"
date: 2009-04-26
forum: Multimedia Software
---

### Post by RARCA on 2009-04-26
I have cloned my monitor with the TV and am trying to get the sound from mplayer and VLC to play down the HDMI cable to the TV.  All the settings changes that I read about in forum just keep keep the sound coming onto the desktop speakers that are plugged in with an ordinary jack.

I am running Ubuntu Desktop 9.04.  Any help or requests for more information would be appreciated.

---

### Post by solitaire on 2009-04-26
Quick check: 

Is it "HDMI to HDMI" or "DVI to HDMI"?
DVI does not do Audio so you need a separate audio cable to the TV.

What's the Graphics card (or Motherboard if embeded) might give a hint to the solution..

---

### Post by RARCA on 2009-04-26
It is HDMI to HDMI on and Nvidia 9500S that I have updated software installed for (at least I really really really think I do)

---

### Post by bedhead75 on 2009-04-26
Does your video card actually have digital audio pass-through?  If so, you have to make sure you've connected the digital audio output on the motherboard to the input jack on the video card itself in order to get sound through HDMI.  Depending on the brand, not all nvidia cards have this feature...which is counter-intuitive if they offer HDMI video output.  If you do have digital audio pass through, I think you also have to select the proper options the in the System > Sound > Playback preferences pull-down menu.  If there is no digital audio pass through, you'll have to connect a separate analog sound cord from the computer to TV.  And if this latter case is true, the TV might not recognize analog sound from this separate source if it is receiving video through HDMI.  In order to fix this, you'll have to fool the TV by setting the "UseEdid" option to "false" in your Xorg.conf file, and manually set up the modelines and proper timings for the TV.  Getting this proper information can be a pain and I spent a few days figuring it all out.

---

### Post by solitaire on 2009-04-26
The latest BETA drivers:

[http://news.softpedia.com/news/Nvidia-Linux-Display-Driver-173-08-Beta-Released-83238.shtml](http://news.softpedia.com/news/Nvidia-Linux-Display-Driver-173-08-Beta-Released-83238.shtml)

They should work a bit better than the standard ones.

I hope this is not a huge problem with linux+HDMI... I'm picking up a Acer AspireREVO Net-top in a couple of weeks!!

---

### Post by RARCA on 2009-04-27
Thanks for advising to udpate to the new beta.  I just can not get x server stopped to update it with all the advice on the web.  Suggestions welcome.

@bedhead75 I have been able to watch my avi files with VLC on my Vista OS, so I know the hardware is good for it.  It is just a matter of settings that seem to be the issue.  Arg.

---

### Post by RARCA on 2009-05-05
> **solitaire said:**
> The latest BETA drivers:

[http://news.softpedia.com/news/Nvidia-Linux-Display-Driver-173-08-Beta-Released-83238.shtml](http://news.softpedia.com/news/Nvidia-Linux-Display-Driver-173-08-Beta-Released-83238.shtml)

They should work a bit better than the standard ones.

I hope this is not a huge problem with linux+HDMI... I'm picking up a Acer AspireREVO Net-top in a couple of weeks!!
Tried to update this after pressing ctrl alt F1 and run the file.  Problem is that it says something about my Kernel 2.6 (which I have) because I am running Ubuntu 9.04.  Very confused.  Anyone help?

---

