---
title: "No mic on Skype with Logitech Webcam"
date: 2009-10-19
forum: Multimedia Software
---

### Post by garnold on 2009-10-19
I know that info about this is all over these forums but some of the info is dated and some requires really tinkering with stuff I'm not ready for yet (noob here). 

I'm running 9.04 an would like to use the mic in my logitech webcam with Skype. The only option I have in skype for sound/mic is plusaudio. I'm not sure what to do to ge the mic to work.

This seems to be the only area of Ubuntu that has really been hard to understand. The sound and recording part of the OS is rather complicated since there are some many different servers that can talk to that sound card.

Sorry for, yet another, Slype and Mic thread but I could really use some help please.

---

### Post by taryneast on 2009-11-08
I'm also having the same problem, and not sure how to fix it.
I'll explain the problems I'm having and perhaps we'll jointly find a solution that'll help you too. :)

I'm running Skype version 2.1.0.47 on 64-bit ubuntu 8.10 on an AMD TurionX2 laptop.

The webcam+mic is the Logitech Webcam C250

The video works fine, but I'm having continual problems getting the mic to work. 

There is a built-in mic in the laptop, and I'm guessing there's some kind of competition between the two, but I don't know how to fix it.

Either I get video and can talk (but hear nothing) or I can hear (but I'm told they can't hear me talking). With the latter, I'm told that I'm *VERY QUIET*, and that I should turn up the volume on Skype... but I don't seemt o have a volume-control in Skype. My friends have sent me screenshots of the volume controls that *they* have available (under Audio-controls) but this doesn't appear on my version of Skype.


I looked in System > Sound to see if I could get it working - and perhaps chose the onboard mic instead of the webcam one - but I have no idea how to tell which is which and how to select them or test them (test just does nothing but op up the 'testing' box... unlike sound where you can actually hear a tone).

Any ideas as to how I can a) figure out what is going wrong and b) fix it?

Cheers and thanks,
Taryn

---

### Post by Rumpty on 2009-11-08
For what it is worth, here is what I did, assembled from various comments on the forum, and thanks to those people.

Running a Logitech webcam on Ubuntu 9.04, or 9.10. Skype 2.1.0.47

Install padevchooser (and related stuff which it will bring in) if it isn't installed already. In Skype options - audio devices, I have "allow Skype to adjust audio levels" unticked. Otherwise options are at default, using pulse audio.

Open Pulse Audio Volume control. Select the Input Devices tab. Your Logitech webcam USB mic should be there. Click on the speaker symbol at the right of the mic section to unmute the mic. You should now see activity on the volume level bar when you make noises.

Leave pavolume control open, just slide it out of the way. Open Skype, start a call.  As soon as the call is going, select the recording tab in pavolume control. Skype should have appeared here, to show that it is using the mic. You may have to click in this Recording window to actually get the mic working in Skype. 

That's about it. Ubuntu seems to open with the mic muted, hence having to select the Input Devices tab as above, and unmute it.

---

