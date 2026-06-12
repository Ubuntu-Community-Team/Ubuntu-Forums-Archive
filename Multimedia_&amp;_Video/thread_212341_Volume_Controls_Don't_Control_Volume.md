---
title: "Volume Controls Don't Control Volume?"
date: 2006-07-09
forum: Multimedia &amp; Video
---

### Post by phunkalicious on 2006-07-09
Hi there, I am a new Ubuntu user and so far I like it very much.  I am having problems getting my sound to work correctly.  Actually it does work for the most part (the USB headset support is flakey at best, not always identifying it or switching automatically on detection, etc) but I can't my laptop keys to control any sound.  I can see the little windows pop up and change when I hit volume up and down, or mute, so it must be doing something, but rhythm box will still keep playing and is not affected by the key presses.  I have tried changing the preferences to control PCM from Master, but still nothing.  Please help. :confused:

---

### Post by Rackerz on 2006-07-09
Have you gone to System -> Preferences -> Keyboard Shortcuts and enabled and configured your media keys? I had too, then restart Rhythmbox and they should work.

---

### Post by phunkalicious on 2006-07-09
Yes I tried this, it got the pause and play buttons working but the volume buttons are already correctly mapped, and they still do not work on rhythmbox :(

---

### Post by phunkalicious on 2006-07-09
The buttons, or any volume control for that matter, are also not working for me in totem.  I have to use the builtin controls of the totem application instead of the overall system volume control. :(

---

### Post by phunkalicious on 2006-07-13
Bump, since no one in IRC or here seems to know...

---

### Post by phunkalicious on 2006-07-13
Ok.
This is what I have tried so far.  Sound is proving to be much more difficult in Dapper than it was in Breezy. Also, I am running a Dell XPS M170 laptop, and the sound card shows as an Intel ICH6.

As of now, the play, pause, stop, next track, and previous track multimedia buttons work within Rhythmbox, as well as Banshee.

1. I've hit the prefrences on the volume icon in the task tray, and have tried changing it from Master to PCM and to even headset.  When anything is selected, the mute, volume down, and volume up multimedia buttons do not affect the level of volume.  The Gnome balloon does pop up and show the volume adjusting, but it does not actually adjust.
[LIST=1]
[*]When set to master, if I right click the icon to mute, nothing happens.
[*]When set to headphone, right clicking the icon and choosing mute does indeed mute the volume, as well as raise and lower it.
[*]When set to PCM, right clicking the icon and choosing mute does indeed mute the volume, as well as raise and lower it.
[/LIST]

The multimedia keys for volume control still do nothing.

2.  Within alsamixer, the volume controls for Master, PCM, and Headphone reflect the gnome volume tray icon, as in Master does nothing but PCM and Headphone do affect the level of volume.

3.  I dug way deep into xkb, far deeper than anyone using Ubuntu should have to.  I edited /etc/X11/xkb/symbols/inet to add my key bindings after looking up their even codes, like so:

```
// Laptop/notebook Dell XPS M170
partial alphanumeric_keys
xkb_symbols "xps"      {
    key <I10>	{	[XF86AudioPrev		]	};
    key <I19>	{	[XF86AudioNext		]	};
    key <I20>	{	[XF86AudioMute		]	};
    key <I22>	{	[XF86AudioPlay, XF86AudioPause	] };
    key <I24>	{	[XF86AudioStop		]	};
    key <I2E>	{	[XF86AudioLowerVolume	]	};
    key <I30>	{	[XF86AudioRaiseVolume	]	};
};
```

I also edited all the other relevant files that are needed to have this option show up:

/etc/X11/xkb/rules/xfree86.html
```
    <model>
      <configItem>
        <name>xps</name>
        <description>Laptop/notebook Dell XPS M170</description>
        <description xml:lang="es">Laptop/notebook Dell XPS M170</description>
        <description xml:lang="ru">&#1053;&#1072;&#1089;&#1090;&#1086;&#1083;&#1100;&#1085;&#1072;&#1103;/&#1087;&#1086;&#1088;&#1090;&#1072;&#1090;&#1080;&#1074;&#1085;&#1072;&#1103; &#1076;&#1083;&#1103; Dell XPS M170</description>
        <description xml:lang="sr">&#1058;&#1072;&#1089;&#1090;&#1072;&#1090;&#1091;&#1088;&#1077; &#1087;&#1088;&#1077;&#1085;&#1086;&#1089;&#1085;&#1080;&#1093; &#1088;&#1072;&#1095;&#1091;&#1085;&#1072;&#1088;&#1072; Dell XPS M170</description>
      </configItem>
    </model>
```

/etc/X11/xkb/rules/xfree86.lst

```
  xps		  Laptop/notebook Dell XPS M170
```

and finally /etc/X11/xkb/rules/xfree86

```
! $inetkbds = a4techKB21 a4techKBS8 acer_tm_800 acpi airkey azonaRF2300 \
              brother \
              btc5113rf btc5126t btc9000 btc9000a btc9001ah btc5090\
              cherryblue cherrybluea cherryblueb cherrycyboard \
              chicony chicony9885 \
              compaqeak8 compaqik7 compaqik13 compaqik18 cymotionlinux \
              armada presario ipaq \
              dell xps inspiron dellusbmm dtk2000 \
```

This causes my layout to show up fine within the keyboard preferences in Gnome.

But still, my volume is uncontrollable from the keyboard, and now I am very sad. :cry: :cry: :cry: :cry: :cry:

---

### Post by GNUbieNZ on 2006-07-14
Hi,

Yes I have this problem also, on my Packard Bell laptop.  Turning down the volume with the media keys changes the Master volume and not the Headphone volume.

Is there some way of placing a strategically placed symlink to link the headphone volume to the master volume, and then all will be fine.  A cheap hack will be fine!!!

Thanks
Dave

---

### Post by phunkalicious on 2006-07-15
Well I spoke to a nice person named dek_aik on IRC who pointed me at these links:
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/38546](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/38546)
 [http://linux.derkeiler.com/Mailing-Lists/Debian/2005-07/1147.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2005-07/1147.html)

[http://www.ubuntuforums.org/showpost.php?p=679010&postcount=5](http://www.ubuntuforums.org/showpost.php?p=679010&postcount=5)

So it looks like there is some quirk I need to account for, which... I thought I did, but apparently not.  I added this to my /etc/modprobe.d/alsa-base

```
options snd-intel8x0 ac97_quirk=hp_only
```

From what I could decipher from the documentation, this should switch the master and headphone volume controls.

Then I did sudo modprobe -a snd_intel8x0 and sudo update-modules, but the volume controls on my laptop still do not modify the actual volume setting.

Please help, because maybe I did something wrong?. :(

P.S.  Here is some output that I hope helps people help me. :D

```

phunkalicious@optimus:~/ninan-1.0.3$ cat /proc/asound/cards
0 [ICH6           ]: ICH4 - Intel ICH6
                     Intel ICH6 with STAC9750,51 at 0xdffffe00, irq 169
phunkalicious@optimus:~/ninan-1.0.3$ lsmod | grep snd
snd_usb_audio          78784  0
snd_usb_lib            16640  1 snd_usb_audio
snd_rawmidi            25504  1 snd_usb_lib
snd_seq_device          8716  1 snd_rawmidi
snd_hwdep               9376  1 snd_usb_audio
snd_intel8x0           33692  3
snd_ac97_codec         93088  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  5 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  2 snd_pcm
snd                    55268  14 snd_usb_audio,snd_rawmidi,snd_seq_device,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
usbcore               130692  8 snd_usb_audio,snd_usb_lib,hci_usb,usb_storage,usbhid,ehci_hcd,uhci_hcd 
```

---

### Post by ltmon on 2006-07-15
Wish I could help, but I'm forced to add my own very similar problem.

I have an Asus Z96J laptop using the snd_hda_intel driver for sound.

Whenever I just the sound volume with my laptop keys the "headphone" channel volume is adjusted.  What I really need is for the "PCM" or the "Front" channel to be adjusted, as these are the channels that actually work.

I've tried setting the master channel on kmix to one of these, but the sound up and down keys keep adjusting just the headphone channel.  Incidentally, this makes no difference to the sound volume at all - even through the headphones.

Cheers,

L.

---

### Post by phunkalicious on 2006-07-15
The AC97 quirk worked, I just had to reboot my computer for some reason for it to take it effect.

---

### Post by ltmon on 2006-07-15
Does this work with the snd-intel-hda module, or is it for only for older models?

Is their an equivalent, because I think it's what I need, or at least similar.

L.

---

### Post by lean on 2006-07-15
I have the same problem with a digial USB sound card. AudioTrack Optiplex. The master volume doesn't work, but only the software volume in applications. This is definitly an ALSA issue.

---

