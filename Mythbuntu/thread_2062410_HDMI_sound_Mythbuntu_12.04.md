---
title: "HDMI sound Mythbuntu 12.04"
date: 2012-09-24
forum: Mythbuntu
---

### Post by tdcarlo on 2012-09-24
Hi,

After over a year and a half of running mythbuntu my hard drive crashed and I had to do another install.  I decided to try 12.04.  After the install, I can not get sound out of HDMI.  In the past, I went to alsamixer unmuted everything and then set my device to ALSA:hdmi and got sound out of the backend/frontend combo and two stand alone front ends.  It did not work this time.  I honestly tried searching for "HDMI no sound mythbuntu 12.04" and couldn't  find anything.  I have little experience trouble shooting and am not sure what to include in this post

aplay -l says card 0 device 3
chip is nvidia mcp79/7a

any help would be appreciated

Thanks,
Troy

---

### Post by nickrout on 2012-09-25
Use the setup wizard.

---

### Post by tdcarlo on 2012-09-25
Thanks for the reply.  I did use both setup wizard and the audio submenu.  I turned the speaker test on and tried every combination.  It is interesting that it chooses ALSA:hdmi:CARD=NVidia,DEV=0 when aplay says device 3....it doesn't accept it when I try to change it to ALSA:hdmi:CARD=NVidia,DEV=3

---

### Post by PhilWig on 2012-09-25
I had a similar problem with Nvidia, fixed with:

Control centre > Graphics driver > Restricted drivers manager> select Nvidia accelerated graphics driver [recommended]

Then chose the setting which worked (white noise) in
Frontend > setup > Setup wizard second page.

That got sound working in myth but not for browsers or mythnetvision.  That needed /etc/asound.conf creating to match setup parameters eg:

> pcm.!default {
      type plug
      slave.pcm {
              type hw
              card 0
              device 3
      }
 }

Your system may vary.  Best wishes.
Phil

---

### Post by nickrout on 2012-09-25
> **tdcarlo said:**
> Thanks for the reply.  I did use both setup wizard and the audio submenu.  I turned the speaker test on and tried every combination.  It is interesting that it chooses ALSA:hdmi:CARD=NVidia,DEV=0 when aplay says device 3....it doesn't accept it when I try to change it to ALSA:hdmi:CARD=NVidia,DEV=3Have you tried all the devices the mythtv scan finds? There is no point in changing it to something you think is right, the system finds all available devices.

---

### Post by BicyclerBoy on 2012-09-25
Isn't this because mythtv enumerates the devices from 0 to 3 where the codecs are logically numbered [3] for some MCP & [3, 7, 8, 9] in later inc. MCP89 HDA.
According to the nVidia HDMI audio doc..
MCP77, MCP78, MCP79, MCP7A, and ION are odd-ball in that they have 4 stereo codecs but alsa only exposes them as one (2 or 6 or 8 ch). No hot-plug events. No ELD.

As prev posted..You do need the nVidia proprietary driver.

speaker-test -l 1 -c 2 -r 48000 -D hw:0,3
speaker-test -l 1 -c 6 -r 48000 -D hw:0,3
speaker-test -l 1 -c 8 -r 48000 -D hw:0,3

---

### Post by tdcarlo on 2012-09-25
Thank you, this got sound out of my system.  It is only white noise but its a start.  I think I have to fiddle with it more, but its a start!





> **PhilWig said:**
> I had a similar problem with Nvidia, fixed with:

Control centre > Graphics driver > Restricted drivers manager> select Nvidia accelerated graphics driver [recommended]

Then chose the setting which worked (white noise) in
Frontend > setup > Setup wizard second page.

That got sound working in myth but not for browsers or mythnetvision.  That needed /etc/asound.conf creating to match setup parameters eg:


Your system may vary.  Best wishes.
Phil

---

### Post by tdcarlo on 2012-09-25
I got it.  I after activating the driver I had to check the "Force audio device output to 48kHz.

Thank you all for helping!

---

### Post by tdcarlo on 2012-09-25
How do I mark the post solved?

---

### Post by anonymousdog on 2012-09-26
Thread Tools

---

