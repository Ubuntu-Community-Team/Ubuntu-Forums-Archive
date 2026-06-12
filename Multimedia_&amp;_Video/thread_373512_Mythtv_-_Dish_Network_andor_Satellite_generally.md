---
title: "Mythtv - Dish Network and/or Satellite generally"
date: 2007-03-01
forum: Multimedia &amp; Video
---

### Post by juanhunglow on 2007-03-01
This thread is a spawn from another thread **[COLOR="Blue"][here re: IVTV in Feisty]("http://www.ubuntuforums.org/showthread.php?t=331802").[/COLOR]**  So as not to hi-jack that threat this was started.

Users of mythtv that have either dish network or some other form of satellite service might have unique issues related to myth that standard cable users don't, or problems different that those with HD or other enhanced services.

Some of the question that have already been presented is whether there is any better video quality in myth when using s-video connection vs. coax.  If your using sat and myth looks good let us know.  Also, because of the vast hardware differences let us know what PVR card/devise you are using.
Also, how do you use the system with IR, or without IR/blaster, and do you have any unique ideas on controlling your sat box.

I have a PVR-350 from Hauppauge and my mythtv setup is front/back desktop combo at the moment.  This was my first attempt at myth and if was fairly painless.  I would like to get to a backend separate from a front setup but with the sat box issues I don't know if that will come.  I used the Edgy install guide on my install of Feisty found here **[COLOR="Blue"][https://help.ubuntu.com/community/MythTV]("https://help.ubuntu.com/community/MythTV") [/COLOR]**Great documentation and thanks to superm1.

I split the signal that goes to my 2nd tv (I have a 2 tuner dish network box) and ran the split back to my PVR with coax.  The picture and sound are good, but not great.  The house was already wired with coax so hooking that up was easy, I would like to try s-video connection to the PVR but I'm going to have to move the PC or get a 50' cable to make that work.

If you have any insight, comments or questions please post them.

---

### Post by karlec on 2007-10-25
What type of dish receiver do you have? 
My receiver is currently a 2 tuner HD-DVR  but I only have one TV attached.  I believe that I have tried the coax connection from the receiver TV2 'port' but that did not work (meaning my PVR500 is not tuning at all).  does anything else need to be done between the receiver and my mythbox and/or between the receiver and my TV?  :confused:

---

### Post by davetay1021 on 2007-11-11
I have the Dish Netwok 322 ( I believe ) dual tuner receiver.  My capture card is a PVR-250 and I have an ATI Radeon 9000 video card.  I'm running coax to mythbuntu (7.1) and the picture is, as you said, good but not great.  I'm using the mce remote with the ir blaster, although I haven't yet got the blaster working in order to control my satellite box.

My question is how do I configure the myth box to change the channels on the sat box (through the blaster)  but leave my tuner tuned to channel 3, which is required by the sat box.  This is something I've never got working properly.  Currently I can change the channels on the tuner, but that doesn't do me any good, since the tuner has to stay on channel 3.  If I change channels on the sat box using the sat remote, I'm very limited in recording since I can't schedule recordings without leaving my sat box on the right channel.  Am I missing something easy here?

---

### Post by newlinux on 2007-11-11
In mythtv-setup, under input connections you would set "Preset tuner to channel" to 3 for your card to always tune 3, and  you would need to set the appropriate "External Channel Change Command"  to handle tuning the box.  This should be probably be a script that uses LIRC to change the channel, after LIRC has been configured for the blaster.

---

