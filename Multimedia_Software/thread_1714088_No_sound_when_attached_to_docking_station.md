---
title: "No sound when attached to docking station"
date: 2011-03-24
forum: Multimedia Software
---

### Post by FloydPink on 2011-03-24
Hello guys,

I have been using Linux and Ubuntu only since the last two months on my (2006) Sony Vaio VGN A617S laptop which is going pretty well on Ubuntu 10.10. When installing Ubuntu audio did get installed alright, and the speakers on the laptop itself are working well even now with the right drivers (snd-hda-intel) for the Realtek ALC260 soundcard.

My problem is when laptop is docked to the A/V docking  station (I have seen it referred as a port replicator as well - the  model number is VGP-PRAV2), with its two external speakers. And these were not on when Ubuntu was being installed. What is interesting is the headphones jack on the laptop does work when the docking station does not.

I have been trying hard and have already tried quite a few things I saw to be related issues, like:
a) adjustments to some IEC958 in alsamixer
b) using a custom mod for the ALC260 card

All this is to no avail.

If someone could help me with this, that would be really appreciated.

Thank you.

---

### Post by Script Warlock on 2011-03-25
check this thread it might help [http://ubuntuforums.org/showthread.php?t=1598229](http://ubuntuforums.org/showthread.php?t=1598229)

---

### Post by FloydPink on 2011-03-25
> **Script Warlock said:**
> check this thread it might help [http://ubuntuforums.org/showthread.php?t=1598229](http://ubuntuforums.org/showthread.php?t=1598229)Thanks for that, SW.
I followed the alsa-info script mentioned there and have uploaded its analysis at [http://www.alsa-project.org/db/?f=85fcef10c898915d64ebe47b5ab2d6d842241150](http://www.alsa-project.org/db/?f=85fcef10c898915d64ebe47b5ab2d6d842241150)

If someone could guide me after looking into that report, that would be awesome...

---

### Post by FloydPink on 2011-03-27
The docking station works really well on Win XP and after a few more hours worth of analysis through my untrained eyes, these are things I thought could help:

These are how the sound controls look in XP vs Ubuntu 10.10:

[IMG]http://i.imgur.com/EnoGF.png[/IMG]

[IMG]http://i.imgur.com/87cW9.png[/IMG]

Also, found these from the Windows Program files directory for Realtek:

AzMixerSel.ini - [http://paste.ubuntu.com/586244/](http://paste.ubuntu.com/586244/)
RtlUpd.ini - [http://paste.ubuntu.com/586246/](http://paste.ubuntu.com/586246/)
HDA.inf - [http://paste.ubuntu.com/586247/](http://paste.ubuntu.com/586247/)
HDA104D.inf - [http://paste.ubuntu.com/586250/](http://paste.ubuntu.com/586250/)
HDAHP882.inf - [http://paste.ubuntu.com/586252/](http://paste.ubuntu.com/586252/)
HDAHPBPC.inf - [http://paste.ubuntu.com/586253/](http://paste.ubuntu.com/586253/)
HDARt.inf - [http://paste.ubuntu.com/586257/](http://paste.ubuntu.com/586257/)

It would be great if someone can help me in making the A/V docking station working on Ubuntu

Thanks

---

### Post by FloydPink on 2011-03-27
Upgraded to the latest version of ALSA driver (1.0.24), but still no love!
The updated alsa-info.sh dump is at [http://www.alsa-project.org/db/?f=d8cb1118a5da1c6388f4d169c2b454e7f1a011da](http://www.alsa-project.org/db/?f=d8cb1118a5da1c6388f4d169c2b454e7f1a011da)

---

### Post by FloydPink on 2011-03-27
Is there a good place to learn how one can tweak the driver settings using the [HDA Analyser]("http://www.alsa-project.org/main/index.php/HDA_Analyzer")? Or is there some place where I can learn about what is shown in the /proc/asound/card0/code#0 virtual file...

I think my problem could be that EAPD is not being enabled and/or used when the laptop is docked on to the port replicator...

These nodes which are being shown as 'PIN's in HDA Analyzer that have EAPD disabled in it...

```
Node 0x0f [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001003f: IN OUT HP EAPD Detect Trigger ImpSense
  EAPD 0x0:
  Pin Default 0x21043010: [Jack] Line Out at Sep Rear
    Conn = RCA, Color = Blue
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x08
Node 0x10 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001003f: IN OUT HP EAPD Detect Trigger ImpSense
  EAPD 0x0:
  Pin Default 0x0321411f: [Jack] HP Out at Ext Left
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0xf
    Misc = NO_PRESENCE
  Pin-ctls: 0xc0: OUT HP
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x09
```

Any help is really appreciated...

---

### Post by FloydPink on 2011-03-31
Would someone please point me in the right direction? I am totally lost trying to get the audio working through the external speakers...

Thank you in advance...

---

