---
title: "Setting all application to output to IEC195"
date: 2007-01-05
forum: Multimedia &amp; Video
---

### Post by moeFinley on 2007-01-05
I want all my applications to use IEC958 (optical out) and in the Gnome Sound Preferences this is how I have it setup.  Now Banshee will output sound through IEC958 and I guess some other apps that I'm yet to find.

How do I get all of my applications to play through IEC958? (Totem, Gxine, Opera, Firefox, Gxmame)

```
**** List of PLAYBACK Hardware Devices ****
card 0: nForce2 [NVidia nForce2], device 0: Intel ICH [NVidia nForce2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: nForce2 [NVidia nForce2], device 2: Intel ICH - IEC958 [NVidia nForce2 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Thanks for any help

PS.  I found an [interesting article]("http://wiki.freespire.org/index.php/What's_Wrong_With_Linux_Audio") in the Linspire Wiki about Linux sound.  Seems the Linux community just needs to make it's mind up and for once standardise something!

---

### Post by pseudonym on 2007-01-05
Hi, I don't use Gnome but you'll often find that you need to tell individual apps how to output sound. Some good tips for xine can be found [here]("http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound") and [here]("http://www.flaterco.com/kb/audio.html").

XMMS is easily configured for digital output in it's settings menu. Firefox should just use your default sound device, I thought?? , like many other apps.

Judging by your hardware, one other thing you may be interested in is [this howto]("http://www.ubuntuforums.org/showthread.php?t=253725"), especially if you have the 'Soundstorm' dolby digital encoder chip. I used this OSS driver when I had an nforce2 motherboard, and found the quality better than ALSA overall, even on AC97.

As far as standardisation goes, what has been one of linux's greatest strengths - choice - can also be its biggest downfall eg. there are so many distributions that it's hard to speak of one 'Linux' like you can with windows or mac. That can pose problems for hardware support and software development.

But for audio, these days every distribution uses ALSA, and all modern software is written for this sound API, too. OSS still exists as an alternative (see opensound.com) but ALSA is really the 'norm' now.

HTH :)

---

### Post by moeFinley on 2007-01-05
Wow, great links thanks! =D> 

I sorted it out by changing /etc/asound.conf so that I specified a default device.

```
pcm.card0 {
  type hw
  card 0
}

pcm.!default { 
  type hw 
  card 0 
  device 2
}
```

Device 2 is my optical out.

Thanks for the help.

---

### Post by pseudonym on 2007-01-05
You're welcome :)

Something else you may be interested in - looks like the [ALSA wiki]("http://alsa.opensrc.org/Main_Page") has just been re-organised, if you hadn't found it already. Probably should have pointed you there earlier, come to think of it :-k 

I'm just getting back into ALSA with this new system of mine. I had an ASUS A7N8X-Deluxe system before this, which had the Soundstorm chip, and I'd been using that nvidia OSS driver mentioned above for a long time.

ALSA is working well with the new onboard HD audio (I only use SPDIF, too), but I still miss that Dolby Digital Live on the last board. Never had better sound out of a PC than that :(

---

