---
title: "ENLTV-FM tv tuner card not working in ubuntu edgy"
date: 2006-12-09
forum: Multimedia &amp; Video
---

### Post by survient on 2006-12-09
Trying to install an ENLTV-FM, ubuntu recognizes it as a SAA7134 chipset, specifically Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01). It's an Encore ENLTV-FM tv tuner card. I've been searching through the forums for weeks, cannot get it to work in myth tv or tv time. I've seen some foreign forums talk of an ENLTV-FM-HA, I think it's spanish, but this is not my card, and I can't translate the forums properly to figure out how to do this. I'd just like it to work, I don't have money to get a new card right now, and it's just bugging me to all hell's creation ](*,) . It's not the best card, but, it works well enough. Any help would be appreciated. I'm using ubuntu edgy, any more info needed, I'll list.

---

### Post by brainformat on 2006-12-09
hi,
look, i'm not familiar with your card. but if system recognise it as philips saa, than it probably is philips chip i it.
i had the same situation with my asus tv/fm card it realy has philips chip and it works fine on my comp...

---

### Post by survient on 2006-12-11
so............how do I get it to work?!! I mean, there are a few philips chipsets for tv time. Can I at least get a bone(a link to a site I can get drivers for the card, or an app that deals with the philips chipset) here?

---

### Post by mooseboy on 2006-12-16
I just got this card working in Edgy with the following setup:

Open a sudo'ed text editor, create a new file "/etc/modprobe.d/saa7134", put in the following line:
options saa7134 card=3;tuner=2

save, run "sudo rmmod saa7134_alsa && sudo rmmod saa7134 && sudo modprobe saa7134"

Voila, your TV card should now be working. A side effect of this is you'll more than likely get blasted with static from the TV tuner. Luckily for me, I just need the Composite Video to hook up my Wii. The RCA plugs I'll feed straight into my soundcard.

---

### Post by survient on 2006-12-16
Yep. Thx, worked like a charm, everything's working cept the FM tuner, but radio around here's bad, and I really don't care. Just like being able to use the video on my other monitor without the sound going mute, as it does in windows. No static issues here, all works well. Thx again

---

### Post by chuvisco on 2007-01-27
> **mooseboy said:**
> I just got this card working in Edgy with the following setup:

Open a sudo'ed text editor, create a new file "/etc/modprobe.d/saa7134", put in the following line:
options saa7134 card=3;tuner=2

save, run "sudo rmmod saa7134_alsa && sudo rmmod saa7134 && sudo modprobe saa7134"

Voila, your TV card should now be working. A side effect of this is you'll more than likely get blasted with static from the TV tuner. Luckily for me, I just need the Composite Video to hook up my Wii. The RCA plugs I'll feed straight into my soundcard.

This worked for me.  I got the sound working in MythTV by following [these]("http://www.mythtv.org/docs/mythtv-HOWTO-7.html#ss7.2") instructions.  The card doesn't seem to be working right after hibernation, though.

---

### Post by Pauan on 2008-03-08
> **mooseboy said:**
> I just got this card working in Edgy with the following setup:

Open a sudo'ed text editor, create a new file "/etc/modprobe.d/saa7134", put in the following line:
options saa7134 card=3;tuner=2

save, run "sudo rmmod saa7134_alsa && sudo rmmod saa7134 && sudo modprobe saa7134"

Voila, your TV card should now be working. A side effect of this is you'll more than likely get blasted with static from the TV tuner. Luckily for me, I just need the Composite Video to hook up my Wii. The RCA plugs I'll feed straight into my soundcard.

You have my great many thanks! I am using an ENCORE ENLTV-FM TV Tuner and had almost given up hope of getting it to work. I too am using it to play video games with my Wii on the computer. Oddly enough, running the command didn't work, as saa7134_also does not exist. However, after removing the first part (sudo rmmod saa7134_alsa) it works now!

---

### Post by Vox754 on 2008-04-23
Heh. This card does work with the "saa7134" driver.

ENLTV-FM TV Tuner
```

00:08.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
        Subsystem: Philips Semiconductors Unknown device 2341
        Flags: bus master, medium devsel, latency 32, IRQ 19
        Memory at fa000000 (32-bit, non-prefetchable) [size=1K]

```

In the kernel messages it appears as a different card
```

 saa7130[0]: subsystem: 1131:2341, board: LifeView/Typhoon FlyVIDE
O2000 [card=3,insmod option]

```

However, after more than two years I haven't been able to make it work perfectly with my setup.

The problem, I think, is my motherboard.

I have the Biostar K8M800-M74 board, which is VIA-based with the S3 Unichrome Pro video card and VT8237 AC97 Audio Controller.

As you can see, it is a cheap PC.
For the most part 3D acceleration is broken (Launchpad bug #43154); maybe this affects the TV card also.

I've tried watching TV with vlc, zapping, totem, mplayer, and others, and they don't work quite right. So far the only program that lets me change channels is the hideous "xawtv".

In case anyone has any successful experience with this particular combo of TV card and motherboard let me know.
I'm using NTSC US-cable, so 
```

options saa7134 card=3;tuner=2

```
seem to work okay.

If you are new and want to save the trouble, you may chose not to buy these products. There are better supported cards and motherboards out there.

---

