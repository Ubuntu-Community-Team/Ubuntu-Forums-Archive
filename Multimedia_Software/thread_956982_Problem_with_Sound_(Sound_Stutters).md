---
title: "Problem with Sound (Sound Stutters)"
date: 2008-10-23
forum: Multimedia Software
---

### Post by mshamsuddeen2 on 2008-10-23
Ok my sound card is a snd_hda_intel type. Whenever i play mp3 files or video files in totem player, i get a blank pop up, and it just hangs. So i installed vlc, and now the mp3 works fine. But when i play video files esp avi the sound keeps on stuttering and the vid keeps on playing and so its all out of sync and gets really ugly. It does the same with WMV, DAT, MPG, and MKV files too, but flv files work fine. This also happens when i boot into Ubuntu at the login screen, the drums keep on stuttering for like 10 seconds before they subside, and sometimes after like 10 - 20 mins after ive logged into my Ubuntu desktop i get the other boot sound with stutters of course.

Ive read the tutorial at the top of the page on how to fix the sound problem, the thing is my sound card is detected so thats no prob, its just functioning very wierd.

Can someon pls help me. My specs are:-

Compaq Presario CQ40
Intel Core2Duo P750
2GB RAM
160GB Hard Disk SATA Western Digital
Intel HDA Sound Card
Ubuntu 8.10 (just upgraded, yes i know its still in BETA)

P.S Same thing was happening when i had 8.04, so i upgraded hoping the better hardware support in 8.10 might solve the problem.

---

### Post by damien_d on 2008-11-25
I too am having the same problems.

It manifests itself at the login screen and when playing audio, such as Amarok.

This is my hardware:
```

damien@damien-desktop:~$ lspci

<snip>
00:07.0 Audio device: nVidia Corporation Unknown device 0774 (rev a1)
<snip>

damien@damien-desktop:~$ sudo lspci -v

<snip>

00:07.0 Audio device: nVidia Corporation Unknown device 0774 (rev a1)
	Subsystem: Giga-byte Technology Unknown device a002
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at fb100000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Capabilities: [6c] HyperTransport: MSI Mapping

<snip>


```

I am running 8.04 (Hardy Heron) AMD64.   I have tried both with the standard kernel and also tried:

```

sudo apt-get install linux-backports-hardy

```

Interestingly, the backports makes it worse.  Whereas with the standard kernel modules, the logins sreen sound is jittery, but (most of the time) music from Amarok is good.   However, with backports, it only makes the problem worse.

```

damien@damien-desktop:~$ uname -r
2.6.24-21-generic

```

If it can be helpful, I can record the login screen sound and post as an attachment.

Cheers
Damien

---

