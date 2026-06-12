---
title: "Digital sound problem"
date: 2008-12-21
forum: Multimedia Software
---

### Post by beerguzzler on 2008-12-21
I have both analogue and digital sound coming from my motherboard

My issue is that although I can get sound via digital link in MythTv and VLC when playing DVD'S and other media types, (pc is connected to my amp and speakers) I cannot get any sound from Firefox and system (ie sounds that play for email notification and system boot up/log off).

However if i have pc speakers plugged into the analogue port on the card I get sound. 

Bizarre thing is that it all used to work perfectly, just recently it has stopped. I have checked the sound device and have nothing set to mute.

Result from aplay -l

"**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Any advice on where to start is much appreciated.

---

### Post by beerguzzler on 2008-12-22
^

---

### Post by beerguzzler on 2008-12-30
anyone?

This is seriously doing my box in now. I've made sure that there is nothing in Alsamixer set to mute.

My amp lights up with Linear PCM which is expected. If i mute master it blanks out as expected and comes back when i un-mute.

Like I said, VLC, Mythtv works fine, just the system, firefox and Thunderbird I need to get working.

---

### Post by beerguzzler on 2009-01-03
I have 2 choices now.

Re-install Ubuntu for about the 6th time in as many months or go back to Windows.

People say Windows is unstable, yet I've never had to re-install XP because of a sound driver issue!!!

---

### Post by linux_tech on 2009-01-03
If have Intrepid you may want to install these, to help improve your sound.
```

sudo apt-get install gnome-alsamixer
sudo apt-get install alsa-oss
sudo apt-get install libasound2
sudo apt-get install libasound2-plugins

```
To open volume control type:
```

gnome-volume-control

```
To open gnome-alsamixer type
```

gnome-alsamixer

```

---

### Post by doug1212 on 2009-01-04
@OP,
This is may be a pulse audio issue, I think PA has problems when using digital pass through.
I would suggest trying plain ALSA and ensure that it using iec958.
I use digital out on my set up but I use a cheap Trust PCI card and not on board sound and is ok.
Doug.

---

### Post by beerguzzler on 2009-01-04
> **linux_tech said:**
> If have Intrepid you may want to install these, to help improve your sound.
```

sudo apt-get install gnome-alsamixer
sudo apt-get install alsa-oss
sudo apt-get install libasound2
sudo apt-get install libasound2-plugins

```
To open volume control type:
```

gnome-volume-control

```
To open gnome-alsamixer type
```

gnome-alsamixer

```

Thanks but using Hardy, have already got the above installed. When using gnome-alsamixer IEC958 is ticked. Nothing is set to mute. I have noticed that if you select mute on master then the amp display changes to show no speaker, but if you then unmute it comes back, but still no system sound. Still works in Mythtv and VLC.

> **doug1212 said:**
> @OP,
This is may be a pulse audio issue, I think PA has problems when using digital pass through.
I would suggest trying plain ALSA and ensure that it using iec958.
I use digital out on my set up but I use a cheap Trust PCI card and not on board sound and is ok.
Doug.

How do I switch from pulse to ALSA?

---

### Post by IQRules on 2009-01-04
Here is the link, [http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/](http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/)

---

### Post by beerguzzler on 2009-01-04
> **IQRules said:**
> Here is the link, [http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/](http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/)

Thanks but didn't cure it.

---

### Post by beerguzzler on 2009-01-24
I've noticed that although aplay -l shows the audio as HDA ATI SB 882 
alsamixer picks it up as HDA ATI SB 885

I've also discovered that if i mute iec958 and then play something in Mythtv, mythtv unmutes the card and plays correctly.

Mythtv sound options are set to :
Audio output device - ALSA:SPDIF
Passthrough output device - ALSA:1E958

I'm really at a loss as to why it works for Mythtv and not for system sounds.

I don't really want to re-install Ubuntu because trying to get the LIRC and the MCE remote control working correctly is a complete pain.

---

### Post by allene222 on 2009-02-13
I had that problem until I set up an alsa.conf file that fixed it.  I documented what I did here:
[http://www.mythtv.org/wiki?title=AllensDigitalAudioHowto](http://www.mythtv.org/wiki?title=AllensDigitalAudioHowto)

Basically, the breakthrough is this:
 
pcm.!default {
     type plug
     slave {
        pcm "hw:0,1"
        format S32_LE
     }
}

Allen

---

### Post by beerguzzler on 2009-02-14
> **allene222 said:**
> I had that problem until I set up an alsa.conf file that fixed it.  I documented what I did here:
[http://www.mythtv.org/wiki?title=AllensDigitalAudioHowto](http://www.mythtv.org/wiki?title=AllensDigitalAudioHowto)

Basically, the breakthrough is this:
 
pcm.!default {
     type plug
     slave {
        pcm "hw:0,1"
        format S32_LE
     }
}

Allen

Thanks Allen,

Since doing a fresh Intrepid install and following the disable PA tutorial it seems to be working (3 days now :lolflag: ), but if it fails again I'll certainly give your tip a go.

---

### Post by beerguzzler on 2009-02-16
no suprise to find out that system wide sound failed again today.

But thanks to Allen's guide got it fixed, hopefully permantely.

added the following to asound.conf

pcm.!default {
     type plug
     slave.pcm "iec958"
  }

rebooted and all working fine.

---

### Post by dsabatino on 2009-03-22
Thanks linux_tech, your terminal commands helped solve my problem. Digital audio output is working now.

---

### Post by oldsoundguy on 2009-03-24
I have my digital out WORKING, that is not the issue. (It feeds a digital surround amp.)
The issue for me is that the ONLY volume controls I have are those within a launched program such as Amarok .. I can turn it DOWN using it ... or I have to haul out the remote and turn down the pre-amp itself!
The master volume remains at 80% even if SHUT OFF!
This has been this way since 7.10! 
(creative 5.1 live drive card)

IF I switch to ANALOG out, the panel volume control WORKS. (works on the headphone feed, too)

---

