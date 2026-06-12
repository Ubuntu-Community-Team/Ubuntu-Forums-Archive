---
title: "Sound problems after upgrading to 6.06"
date: 2006-06-18
forum: Multimedia &amp; Video
---

### Post by mich_r on 2006-06-18
Hi
I have Sound Blaster 16 PCI sound card and the Logitech Quickcam Messenger webcam (with microphone). All was working perfectly in breezy, but now it is making me crazy - there is a random behavior between reboots sometimes sound is working, sometimes not.
With arecord -l I discovered that the sound devices are "swapping", that means sometimes I have:
```

**** Lista CAPTURE urz&#261;dze&#324; ****
karta 0: Camera [Camera], urz&#261;dzenie 0: USB Audio [USB Audio]
  Urz&#261;dzenia podrz&#281;dne: 1/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0
karta 1: AudioPCI [Ensoniq AudioPCI], urz&#261;dzenie 0: ES1371/1 [ES1371 DAC2/ADC]
  Urz&#261;dzenia podrz&#281;dne: 1/1
  Urz&#261;dzenie podrz&#281;dne #0: subdevice #0

```
And sometimes AudioPCI is listed as first, and the Camera as second.
For example in VLC media player I have to adjust manually an ALSA output device every time the cards swap their positions. But in Audicity for example there is no such option and it just don't work when Camera is the first device.

Plesase, help me , how to "tie" AudioPCI as first device? Or maybe the problem is something else, so how to spot it?


```

~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
0000:00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
0000:00:09.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 08)0000:00:0a.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0000:00:0b.0 USB Controller: Silicon Image, Inc. USB0673 (rev 05)
0000:00:0c.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)

~$ lsusb
Bus 002 Device 002: ID 046d:08f6 Logitech, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse
Bus 001 Device 002: ID 03f0:7104 Hewlett-Packard DeskJet 3420c
Bus 001 Device 001: ID 0000:0000

~$ cat /proc/asound/cards
0 [Camera         ]: USB-Audio - Camera
                     Camera at usb-0000:00:07.2-2, full speed
1 [AudioPCI       ]: ENS1371 - Ensoniq AudioPCI
                     Ensoniq AudioPCI ENS1371 at 0xdc00, irq 12

```

---

### Post by kombipom on 2006-06-18
My dad is having the same problem as he also has the same webcam.  

asoundconf may be the answer.  It's man page says that you can use asoundconf set-default-card CARD.  However I'm not sure what you should put in for CARD, probably ENS1371.

I'm not sure if this is any different from selecting the Default card in System->Preferences->Sound but it's worth a go.

Let me know how you get on.

---

### Post by ariel on 2006-06-18
Similar problem here. My sound-enabled camera shows up as the default sound device, instead of my ICH5 based sound card.

If I try changing System > Preferences > Sound, my change doesn't stick.

I tried:

  asoundconf set-default-card ICH5

but this is not making a difference. 

Really, Totem sound is working fine; the only problem I have is with realplayer 10  (I have video but no sound), and i suspect this might be related to this default card problem. Any suggestion?

Thanks

---

### Post by mich_r on 2006-06-21
So the problem is more common than I thought before.

I also tried asoundconf, default sound card in Preferences>Sound, none of that make a difference.

Please, linux gurus, some noobs desperately need help :(

---

### Post by mich_r on 2006-06-24
Ok, people, I think I have the solution. I followed FarEast's advice at [http://ubuntuforums.org/showthread.php?t=114551](http://ubuntuforums.org/showthread.php?t=114551) and it seems to work.

Because of random nature of the problem I am not 100% sure of success but I have done three reboots and so far it works as expected.

I think I should add that there were no /etc/modprobe.d/sound file in my system, so I've created a new one.

---

### Post by trorion on 2006-06-24
Try opening your volume control (on gnome just double-click the speaker on the control bar) and un-muting PCM.  The update appears to have muted this.

---

### Post by Krister Hallergard on 2006-06-25
Believe I found a solution to disable my TV Tuner card, which was blocking the sound card: added the line "blacklist saa7134_alsa" to /etc/modprobe.d/blacklist

---

### Post by ariel on 2006-06-25
In case it helps someone, i could fix my realplayer no-audio problem with a similar solution as the one in the thread below.

The problem was that realplayer uses OSS/dsp0; if your audio card/chipset shows up in a different dsp device, then you will have no audio (unless you know more about realplayer config than myself :)). ALSA OSS-emulation needs to be reconfigured with the proper mapping.

My solution was:

   - To use aoss wrapper to temporarily map the dsp0 to the ICH5 card: edit ~/.asoundrc and add
        pcm.dsp0 {      type plug      slave.pcm "hw:1,0" }
        Then, "aoss firefox", or "aoss realplay" can be used and audio works with realplayer.
        (Note: apparently this also produces permanent changes, after a reboot)
   - To permanently change the mapping of dsp0: sudo gedit /etc/modprobe.d/alsa-base and add the line:
    options snd-pcm-oss dsp_map=1



[quote=mich_r]Ok, people, I think I have the solution. I followed FarEast's advice at [http://ubuntuforums.org/showthread.php?t=114551]("http://ubuntuforums.org/showthread.php?t=114551") and it seems to work.

Because of random nature of the problem I am not 100% sure of success but I have done three reboots and so far it works as expected.

I think I should add that there were no /etc/modprobe.d/sound file in my system, so I've created a new one.[/quote]

---

### Post by junior aspirin on 2006-06-26
Krister Hallergard can you still use you tv card after blacklisting it. my problem is the same. for some reason it thinks the tv card is a sound card and is overiding my real sound card.

---

### Post by Krister Hallergard on 2006-06-26
junior aspirin!  I had long ago given up all hope to use my TV card (Yuan TUN900) with Linux.  But then I saw this post which has given me some hope, and it even suggests to blacklist the card first!
[http://www.ubuntuforums.org/showthread.php?t=187203](http://www.ubuntuforums.org/showthread.php?t=187203)

---

### Post by Krister Hallergard on 2006-06-27
Followed the commands of Brainkilla in the above link and can now watch B/W television without sound.  The channel shown is the one set in XP.  Did not expect to get this far with Yuan TUN900 card

---

### Post by woedend on 2006-07-09
theres no need to blacklist.
do a search on these forums for
webcam kills sound
find my post, i give details on how to fix it, just making the usb audio device not grab default.

---

