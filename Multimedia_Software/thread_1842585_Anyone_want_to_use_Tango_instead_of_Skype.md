---
title: "Anyone want to use Tango instead of Skype?"
date: 2011-09-11
forum: Multimedia Software
---

### Post by WayOutThere on 2011-09-11
Hi - we just bought one of the new Android tablets with a front facing camera and a program called Tango was installed. Tango appears to be another Voice/Video over IP alternative to Skype et al.

anyway, I found it strange that Tango has an Android and MAC version but no Linux version. You can go here to see what they are planning to create and Linux only has four votes.  That would certainly explain why they don't think Linux is worth the effort.

([http://support.tango.me/forums/327482-feature-requests](http://support.tango.me/forums/327482-feature-requests)) [sorry, if you want to see what they are planning you have to join their forum - I have absolutely no affiliation with Tango at all]

The reason I'm interested is that we haven't had much luck getting Skype to work between my Ubuntu 10.04 LTS 64 bit system and my wife's Android phone (Droix X) and we're hoping that there is a Ubuntu-Android solution that will allow us to video each other when I'm on the road. :D

---

### Post by no2498 on 2011-09-12
skype is a 32 bit program
you need to install the lib's for 32 bit

after that
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
and if that works
put this in the right place
#!/bin/bash
          LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
          /usr/bin/skype

---

### Post by VanillaMozilla on 2011-09-12
Tango would have plenty of competition on Linux.  So you want a Linux VOIP program?  The Ubuntu default is Empathy.  I would start with that.  Others to try:  Twinkle, Jitsi, Linphone.  There are many others.  These all use the SIP protocol (plus maybe others?).

---

### Post by petesilverstein on 2011-09-12
> **no2498 said:**
> skype is a 32 bit program
you need to install the lib's for 32 bit

after that
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
and if that works
put this in the right place
#!/bin/bash
          LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
          /usr/bin/skype

Love Ubuntu, but I'm still getting the hang of the terminal.  I think your approach would solve my problem with no video Skype.  Can you fill in the blanks and post step-by-step instructions that direct me to the "right place"?

Many thanks for your efforts to date.

--Pete

---

### Post by WayOutThere on 2011-09-12
Apparently I wasn't very clear in my previous message. I have Skype installed on my Ubuntu system. My wife has it installed on her tablet. They don't work together - we don't get VIDEO.

I don't want VoIP - I want Video over IP.

I'm looking for a program that works on an Android tablet and that works on Ubuntu 64 bit. While Skype is installed on both and Voice over IP works, the VIDEO in Skype doesn't work. She can see me, but I can't see her, so it appears that the video side of Skype on Ubuntu doesn't work for me.

So, can anyone tell me what does work on both systems - VIDEO+voice over IP, that actually works.

Tango looked like an alternative until I found out that they don't support Linux.

---

### Post by VanillaMozilla on 2011-09-19
Apparently I wasn't very clear either.  At least some of those I mentioned (or all of them?) will also do video, but they use open protocols instead of Skype.  So assuming Tango supports standard, open protocols, you should be able to find a program for Linux.  It doesn't have to be the same program, you know.

Sorry, though, I don't have any experience with video over IP.  Just VOIP.

---

### Post by stevo__h on 2011-11-27
Skype works well on Kubuntu from 9.10 to 11.10 there is a tick box in skype options to start web cam automatically But First install cheese (sudo apt-get install cheese) and run to check your webcam is working with no problems if its working then it will work in skype play with video setting within skype

---

### Post by tambe on 2012-12-07
> **WayOutThere said:**
> Apparently I wasn't very clear in my previous message. I have Skype installed on my Ubuntu system. My wife has it installed on her tablet. They don't work together - we don't get VIDEO.

I don't want VoIP - I want Video over IP.

I'm looking for a program that works on an Android tablet and that works on Ubuntu 64 bit. While Skype is installed on both and Voice over IP works, the VIDEO in Skype doesn't work. She can see me, but I can't see her, so it appears that the video side of Skype on Ubuntu doesn't work for me.

So, can anyone tell me what does work on both systems - VIDEO+voice over IP, that actually works.


Tango looked like an alternative until I found out that they don't support Linux.

Voice over Internet Protocol, also called VoIP, VoIP, VoIP (VoIP for short in English, Voice over IP) is a group of resources that enable the voice signal to travel through the Internet using a IP (Internet Protocol). This means that the signal is sent digitally voice in data packets, instead of sending in analog circuits through usable only by conventional telephone networks (PSTN stands for Public Switched Telephone Network, Public Switched Telephone Network ).
more information on the wikiedia.

---

### Post by cybrsaylr on 2012-12-07
I've been using Skype on my desktop running 64 bit 12.04 with no issues since moving to 12.04 but I don't use or need the video portion.

---

### Post by monkeybrain2012 on 2012-12-07
I have never had problems with Skype, I also use google-chat, video audio quality are just as good if not better. For open source check out jitsi, it is under intense development and have many attractive features (desktop sharing and conference video talk (which may be still in beta, but this is a paid feature in Skype) and good privacy and security, no worries of back doors and Ads)

[https://jitsi.org/](https://jitsi.org/)

Here is a presentation
[http://vimeo.com/36396972](http://vimeo.com/36396972)

---

### Post by oldos2er on 2012-12-07
Old thread closed.

---

