---
title: "No Audio on mono bluetooth headsets Karmic"
date: 2009-11-05
forum: Multimedia Software
---

### Post by remarkosmoc on 2009-11-05
Hello,

I am a skype user and as such like to use a bluetooth headset for skype audio.  I'm using Karmic with the latest updates.  I can pair my devices fine.  I have two devices and if I can get either working I'd be quite happy.

I have an insignia BT-BTHDST.  This device can be used as either an A2DP stero headphones, or like an analog headset.  Using pulse audio volume control I can switch just fine and listen to any appliction A2DP with good sound quality.  However if I go to the configuration tab of volume control and choose Telephony Duplex instead of A2DP, I get no audio.  The Mic works fine but I get no output.

Similarity, I have a motorola H375 that behaves the same, everything connects fine and the mic works fine but I have no audio.  

Presently I can use skype by putting the headset in my ear as a placeholder for the mic, but I'm listening to the PC speakers for the output.

Thanks

---

### Post by jobrahms on 2009-11-09
I'm having the same problem with a plantronics 220. My headset does not have an A2DP setting. Anyone know what's going on?

---

### Post by ronnie666 on 2009-11-15
i have the same plantronics 220 [Bluetooth headset]("http://www.wirelessphonegallery.com/bluetooth.aspx") which i use with my Samsung F210 and i have no probem with it. it just works great.

---

### Post by remarkosmoc on 2009-12-03
did you do anything special to get it to work?

---

### Post by curlybap on 2009-12-10
I'm having the same problem, anyone found a solution?

---

### Post by angyii on 2009-12-22
I have a Motorola H375 and it works by default in Karmic.  Maybe there are some residual problems from Jaunty if you upgraded as opposed to a fresh install.  I fiddled around with my bluetooth settings in Jaunty, which rendered bluetooth unusable in Karmic.  A fresh install fixed it for me.

---

### Post by accumulator on 2010-02-13
If having problems with mono headsets, try

```
HFP=false
```

in /etc/bluetooth/audio.conf

---

### Post by WaroDaBeast on 2010-06-01
First off, let me apologize if digging up this old thread is deemed  inappropriate.

I'm posting to say that I've got the very same problem under Ubuntu  10.04 with a Plantronics 220 headset and a Belkin F8T012xx1 bluetooth  dongle : I can record fine, but I got no playback.

Updating Bluez to version 4.64 via launchpad didn't help. Oh, and the "HFP=false" trick didn't work either.

---

### Post by curlybap on 2010-06-01
Just dropping in to say that I'm still having the same problem under 10.04; headset works fine with my phone.

---

### Post by ulrichard on 2010-06-02
My bluetooth devices that only have either mono duplex or stereo simplex work without any problems out of the box in both Karmic and Lucid.
But now I bought a Jabra Halo which supports both profiles. It works fine in Lucid. In the Pulse Mixer, I can select the profile I want to use. 
But on Karmic I get no sound. It seems to be confused with the two profiles. The headset doesnt appear in the hardware section of the pulse mixer. Playing around with ~/.asoundrc doesn't change a thing.
If I execute the temporary commands suggested in [https://help.ubuntu.com/community/BluetoothHeadset](https://help.ubuntu.com/community/BluetoothHeadset) it will work temporarily. That tells me that the hardware is ok, and that it's a software problem. But I don't want to execute shell scripts everytime prior to use my headset.
Also installing BlueMan didn't help.
Is there anything I can do in Karmic? The F### Poulsbo driver prevents me from updating my netbook to Lucid.

---

### Post by curlybap on 2010-06-02
My headset supports HSP/HFP telephony duplex and this option appears in the hardware tab of the Sound Preferences in both Lucid and Karmic, and only works for output, not input.

---

### Post by WaroDaBeast on 2010-06-02
> **ulrichard said:**
> If I execute the temporary commands suggested in [https://help.ubuntu.com/community/BluetoothHeadset](https://help.ubuntu.com/community/BluetoothHeadset) it will work temporarily. That tells me that the hardware is ok, and that it's a software problem. But I don't want to execute shell scripts everytime prior to use my headset.

The thing is, running an "hcitool scan" command line doesn't yield anything as far as my bluetooth headset is concerned. My cell phone &#8211; a Sony-Ericsson W300i &#8211; is detected fine though.

---

### Post by farbird on 2010-06-02
add the ppa for blueman repo, install blueman and all its bluez upgrades..

apt-get install pavucontrol

use it to select the hardware u'd like to output [ a2dp/hsp ]

that works for me...

---

### Post by WaroDaBeast on 2010-06-03
> **farbird said:**
> add the ppa for blueman repo, install blueman and all its bluez upgrades..

apt-get install pavucontrol

use it to select the hardware u'd like to output [ a2dp/hsp ]

that works for me...

Thanks for the advice... Even though this didn't solve my problem, I know now what's going on – applications accept mono sound from the headset, but always try to output stereo sound to it. I need a way to force mono sound in the output options...

---

### Post by curlybap on 2010-06-04
> **WaroDaBeast said:**
> Thanks for the advice... Even though this didn't solve my problem, I know now what's going on – applications accept mono sound from the headset, but always try to output stereo sound to it. I need a way to force mono sound in the output options...

That was the impression I got, too. I found this on forcing mono, but I'm not sure how to feed that through to the Bluetooth output.

[http://www.mail-archive.com/pulseaudio-discuss@mail.0pointer.de/msg03592.html]("http://www.mail-archive.com/pulseaudio-discuss@mail.0pointer.de/msg03592.html")

---

