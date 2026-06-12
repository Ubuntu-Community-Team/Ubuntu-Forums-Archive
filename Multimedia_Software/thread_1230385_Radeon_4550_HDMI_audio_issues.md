---
title: "Radeon 4550 HDMI audio issues"
date: 2009-08-03
forum: Multimedia Software
---

### Post by kryptyksol on 2009-08-03
Good Morning Everyone,

I am having a bit of trouble getting audio through the HDMI cable on my current setup, it is a radeon HD4550,  and I am running the latest version of ubuntu, everything is updated. (version 9.04)

The issue is that no audio comes through, I have everything un-muted, and the sound settings seem to recognize that there is a sound card (they have an option for ATI HD audio) I am stumped, and was wondering if anyone here had any insight into this? I am farily proficient with the linux command line, the issue is I dont really know where to look :) I've never set anything like this up.

Thank you for your time.

Patrick

---

### Post by kryptyksol on 2009-08-03
update: I have now tried everything in the sound problems sticky, my sound card is being detected by ALSA, as: 

**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Also verified that it is not muted.

---

### Post by markbuntu on 2009-08-03
First go here

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

come back if that did not help

---

### Post by andrewbrown22 on 2010-02-07
I know this is a fairly old post, but it hasn't been marked as solved. 

I'm currently looking to upgrade my HP DC7700 with Ubuntu 9.10 to an ATI Radeon 4550 card by MSI and I was wondering if digital audio through the HDMI port had been fixed in this latest version of Ubuntu.

---

### Post by Yellow Pasque on 2010-02-07
You'll need to run a very recent version of the radeonhd driver, built from git. This page explains building radeonhd from source: [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)
You may need to upgrade ALSA as well: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

In terms of seeing native support in Ubuntu, the HDMI audio patches are expected to be pulled into the 2.6.34 kernel, so you won't see working HDMI audio in Lucid/10.04 unless you run a backported 2.6.34 kernel with it (Ubuntu plans to offer backported kernels for Lucid).

---

### Post by andrewbrown22 on 2010-02-11
So basically, after some work I should be able to have it functioning correctly?
I can't really find any more information on the internet, at least regarding this specific card I'm looking to buy and Ubuntu as far as compatibility.

---

### Post by jamesdew on 2010-02-11
Wow someone else trying to get HDMI audio with a 4550, I thought I was alone.

I had so much trouble with this, the only way I ever got it to work under jaunty was to specify the hwplug: in XBMC. Sound didn't work in any other applications though.

finally I upgraded to karmic and it worked out of the box. Except now I can only get stereo, no-one else seems to be investigating this anymore so I just gave up and accepted stereo, I also tried the new 10.1 catalysts recently, sound also worked just fine but still stereo.

---

### Post by andrewbrown22 on 2010-02-11
So you can confirm that it works within Ubuntu 9.10?

That's good news, honestly. 

As for the audio thing, you mean that you only get stereo audio and not some sort of surround configuration?

---

### Post by jamesdew on 2010-02-11
Yup works fine for me in 9.10

Yes only stereo works. As I said I did get it working in XBMC using the plughw: method addressing the device directly and was able to output DTS and 5.1. However this was annoying as the device kept changing locations and besides the video crashed all the time.

Upgrading to 9.10 solved all that but now I have

HDMI DIGITAL STEREO listed as the device profile where are under the devices. This maybe because passthrough audio doesn't work anymore im not actually sure. Perhaps you could let me know if you have the same issue when you upgrade.

But the short version of this story is yes (aside from possible issue with stereo only hdmi output) this works perfectly on 9.10.

---

### Post by andrewbrown22 on 2010-02-11
Ok, thanks for the info, that's great news. I wouldn't have a real need for 5.1 anyway, at least currently.

---

