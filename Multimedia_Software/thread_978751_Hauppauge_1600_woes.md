---
title: "Hauppauge 1600 woes?"
date: 2008-11-11
forum: Multimedia Software
---

### Post by CaptainPatent on 2008-11-11
[edit - Hauppauge card now showing picture / sound but persistent crackling sound exists (not due to PCM being turned down in alsamixer) - go to post #4 for details]

I have a brand new Mythbuntu install (8.10) and a Hauppauge 1600 TV tuner card. The tuner card was recognized as it should have been, but it seems that no matter how I set up the tuner input all I get is a jumpy gray screen instead of any actual TV when I go to live TV on the frontend.

I've tried multiple settings and input methods (the card has 3 inputs) to no avail. I've also tried combinations of running past my digital TV converter box and going through it. (the Hauppauge card has a digital tuner so I'm hoping to bypass the box.)

The original settings I chose were the ones featured in the WIKI here: [http://www.mythtv.org/wiki/index.php/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/index.php/Hauppauge_HVR-1600) specifically steps 3a and 3b.

I'm pretty sure I want the digital tuner bypassing the box, but with the settings from the WIKI I don't even get the grey screen... myth frontend just jumps out of live TV like I don't have a card configured (and I'm fairly certain I do.)

Is there anyone with a similar setup who knows what settings to use? Are there any tricks I need to know that can tell me what's wrong? Any help is much appreciated.

[B][edit - Solved... Mostly.

As for the tuner issues, Without realizing it I downloaded the ALT version which shouldn't, but does cause problems in setting up the system.

The bad news is the hauppage 1600 driver for linux still has some sound / picture issues. The sound will apparently always crackle to some degree and seems to vary by channel and the card does not initilize properly until after the first time you use it. Again this is an unknown driver issue.][/B]

---

### Post by CaptainPatent on 2008-11-11
Also I wanted to know if I will need to run through my cable box... I don't think I need to, but I heard something about cards no longer being able to decode digital.

---

### Post by CaptainPatent on 2008-11-11
Still no luck on this one. If anyone has ideas it would be much appreciated. If you need any additional information I'd be glad to provide it.

---

### Post by CaptainPatent on 2008-11-13
Here's an update since I last left you. I was still continuously getting a gray screen (not static... just gray) and I had tried literally every potential input combination.

I decided to see if the card works at all so I plugged it into my Windows box and everything went just fine. I plugged it back into my Myth box and **_without changing any settings_** it showed picture / sound just fine. (note audio still has some problems but I'll get to that)

I thought I was finished with my problems - I was able to reboot just fine without the gray screen returning (I thought it may not have been initializing properly), but my power went out this morning and after restarting from the improper shutdown the gray screen returned with no settings able to get me back to where I was.

I did the windows box "trick" again and got picture but no sound. I re-install the latest cx18 drivers (which may or may not have actually been newer) and I started getting picture and sound.

I'm back to where I was with picture working and sound "working" (there is still a crackling noise which may be my sound card, but I think it's the tuner card producing the sound when recording) I know about the PCM issue and have checked alsamixer constantly to make sure the volumes are right - this is NOT the case here.

I think I've narrowed this down to a few very likely causes - 

**Most likely** - The driver does not yet initialize the device properly. I'm assuming the card stores some settings about the computer before it starts (note this is speculation as I have no idea how the card actually initializes) and the Linux driver doesn't know how to dump that information. This would make some sense as to why I had to start TV under a Windows box first and then move it to my MythTV box.

**Less likely** - my own sound card is not initializing properly. While I have had this same Myth setup under 7.04 and with a ATI TV Wonder in place of the Hauppauge 1600 with fully working sound, it may be the drivers conflict somewhere. This may also explain why the crackling exists with the Hauppauge and not with the TV Wonder.

**Least likely** - my hardware seriously just wants to drive me crazy. I know the motherboard itself is having some smaller issues, but they don't seem to be stopping the proper function of the Hauppauge card.

For now I'm going to try and see if I can pinpoint why the sound is crackling. The reason I say it's the tuner is there are some stations that produce much more crackle than others and it isn't a signal problem - once again the setup worked find under windows without crackle.

---

### Post by dazer26 on 2009-01-09
I know it's been a couple of months, but if you have made any progress on the bad sound i'd love to know.  I'm Using the Hauppauge 1600 tuner with MythTV under Kubuntu 8.10 (with kde4.2 beta 2).  I am using whatever driver came with the latest ubuntu kernel update.  I personally didn't have the grey screen programs as you did, but I already had used the tuner under windows.  I do have the same Crackling sound problem, I have played with all the volume controls with no luck.  At first I thought it might be a problem with the sample rate, but mythtv only gives me one option (44 or 48 khz  I think) which I beleive is correct for the card.  

Another problem I have is that when I change channels sometimes the video becomes jumpy and the sound is not synced with the video,  Increasing the buffer has helped a bit, but still hasn't fixed it.

---

### Post by gohanssjn on 2009-01-18
Same problem here.  Sound is unusable.

---

### Post by CaptainPatent on 2009-02-22
Note to everyone - I accidentally downloaded the ALT instead of the standard version. While theoretically that shouldn't cause a problem it still does. After reinstalling from a base version I have no problems except the driver issues with the Hauppauge card.

***REMAINING PROBLEM:***
*I know the bash-script workaround for the hauppauge 1600 initilization, but if anyone has found a driver that overcomes that issue and the issue of the crackling sound please let me know. I have a hunch the driver used doesn't properly initilize a noise filter chip in the card itself but that's just a hunch.*

---

### Post by dazer26 on 2009-07-21
Ok Update.

I was having wireless card issues with linux, so I took a break from it for a while in frustration.  I recently installed linux Mint (Gloria) and gave the TV card another shot.

At first after I got mythtv setup I had the same crackling sound issue as before.  so I went to [http://linuxtv.org/hg/v4l-dvb/](http://linuxtv.org/hg/v4l-dvb/) and got the latest driver.  There must have been a recent update as after installing that the sound is almost perfect.  The problem with initial captures seems to be fixed as well, the tv works even on the first try.

Edit: I had jumpy video, but I found the de-interlace options and fixed this

---

### Post by dazer26 on 2009-11-05
the 1600 works out of the box with 9.10, didn't have to update the driver this time :)

Follow these instructions to set up mythtv for the 1600.

[http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600)

---

### Post by earnoth on 2010-02-28
> **dazer26 said:**
> the 1600 works out of the box with 9.10, didn't have to update the driver this time :)

Follow these instructions to set up mythtv for the 1600.

[http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600)

I've ordered a HVR 1600 to install on mythbuntu - based on your experience, your post seems to indicate that with 9.10 I should be able to I can skip over the driver steps in the mythtv.org link you posted and go right to the "Backend Setup" section?


Thanks in advance, and thanks for updating the thread with your latest experience!  :D

---

