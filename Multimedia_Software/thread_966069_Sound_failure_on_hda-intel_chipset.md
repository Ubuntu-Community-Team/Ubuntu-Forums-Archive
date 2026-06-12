---
title: "Sound failure on hda-intel chipset"
date: 2008-11-01
forum: Multimedia Software
---

### Post by andrewtherenaldo on 2008-11-01
I'm using an acer aspire with an hda-intel chipset, and I just upgraded to Ibex. The sound had worked fine before, but now it just makes high-pitched squeals.

I upgraded alsa-lib and utils and driver, but the sound control now says, "No volume control GStreamer plugins and/or devices found."

I'm sure there is an easy way to fix this.

Thanks for your help!

---

### Post by andrewtherenaldo on 2008-11-01
Also:

1) lspci -v

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 0133
	Flags: fast devsel, IRQ 22
	Memory at fc200000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

2) cat /proc/asound/cards
--- no soundcards ---

---

### Post by eagleapex on 2008-11-01
I'm having a similar problem. No sound at all.

eagleapex@skippy:~$ lspci -v

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
	Subsystem: Dell Device 0301
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at d800 [size=256]
	I/O ports at dc40 [size=64]
	Memory at ffa00400 (32-bit, non-prefetchable) [size=512]
	Memory at ffa00000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

???
What now?

---

### Post by jsh-hk on 2008-11-01
Same problem here.  I have a Dell Inspiron 1420n, one of the Dell laptops shipped with Ubuntu pre-installed.  My soundcard is detected:
```

 cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfe9fc000 irq 21
```
```

lspci -v
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: Dell Device 01f3
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at fe9fc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
```

... but no sound.  Help!

---

### Post by beauman on 2008-11-02
Funny. On my MacBook I have the same chipset with revision 3

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

Sound works. I have an up-to-date ibex installed.

strange...

---

### Post by jsh-hk on 2008-11-02
This turned out to be an easy fix in my case.  During the upgrade, my custom alsa-base file was replaced with a new version.  I switched it back and rebooted, and now everything works fine.

Oops!

---

### Post by tennisisgood on 2008-11-02
exactly where is the alsa-base file located..and how can it be switched back (i didnt back up any files while upgrading :(

---

### Post by jsh-hk on 2008-11-02
/etc/modprobe.d/alsa-base

The upgrade tool renamed the old one as alsa-base.dpkg-old... or something like that, can't exactly remember :)

For future reference, I ran:

```
sudo updatedb
locate alsa-base
vimdiff /etc/modprobe.d/alsa-base /etc/modprobe.d/alsa-base.dpkg.old

```
to figure this out.

---

### Post by jsh-hk on 2008-11-02
And, of course, to make the change

```
sudo mv /etc/modprobe.d/alsa-base /etc/modprobe.d/alsa-base.backup
sudo mv /etc/modprobe.d/alsa-base.dpkg-old /etc/modprobe.d/alsa-base
```

---

### Post by andrewtherenaldo on 2008-11-02
andrew@Nebuchadnezzar:~$ vimdiff /etc/modprobe.d/alsa-base /etc/modprobe.d/alsa-base.dpkg.old
This Vim was not compiled with the diff feature.

andrew@Nebuchadnezzar:~$ sudo mv /etc/modprobe.d/alsa-base.dpkg-old /etc/modprobe.d/alsa-base
mv: cannot stat `/etc/modprobe.d/alsa-base.dpkg-old': No such file or directory

I just need to spend some time and find it...

---

### Post by andrewtherenaldo on 2008-11-02
I'm not exactly sure where the old version would be.

andrew@Nebuchadnezzar:~$ locate alsa-base
/etc/modprobe.d/alsa-base
/usr/share/alsa-base
/usr/share/alsa-base/alsa.default
/usr/share/bug/alsa-base
/usr/share/bug/alsa-base/control
/usr/share/bug/alsa-base/presubj
/usr/share/bug/alsa-base/script
/usr/share/doc/alsa-base
/usr/share/doc/alsa-base/FAQ
/usr/share/doc/alsa-base/NEWS.Debian.gz
/usr/share/doc/alsa-base/README
/usr/share/doc/alsa-base/README.Debian.gz
/usr/share/doc/alsa-base/SOUNDCARDS.gz
/usr/share/doc/alsa-base/changelog-old.Debian.gz
/usr/share/doc/alsa-base/changelog.Debian.gz
/usr/share/doc/alsa-base/changelog.gz
/usr/share/doc/alsa-base/copyright
/usr/share/doc/alsa-base/driver
/usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz
/usr/share/doc/alsa-base/driver/Audigy-mixer.txt.gz
/usr/share/doc/alsa-base/driver/Audiophile-Usb.txt.gz
/usr/share/doc/alsa-base/driver/Bt87x.txt
/usr/share/doc/alsa-base/driver/CMIPCI.txt.gz
/usr/share/doc/alsa-base/driver/ControlNames.txt
/usr/share/doc/alsa-base/driver/Joystick.txt
/usr/share/doc/alsa-base/driver/MIXART.txt
/usr/share/doc/alsa-base/driver/OSS-Emulation.txt.gz
/usr/share/doc/alsa-base/driver/Procfile.txt.gz
/usr/share/doc/alsa-base/driver/SB-Live-mixer.txt.gz
/usr/share/doc/alsa-base/driver/VIA82xx-mixer.txt
/usr/share/doc/alsa-base/driver/emu10k1-jack.txt
/usr/share/doc/alsa-base/driver/hda_codec.txt.gz
/usr/share/doc/alsa-base/driver/hdspm.txt.gz
/usr/share/doc/alsa-base/driver/powersave.txt
/usr/share/doc/alsa-base/driver/seq_oss.html
/usr/share/doc/alsa-base/driver/serial-u16550.txt
/usr/share/lintian/overrides/alsa-base
/var/cache/apt/archives/alsa-base_1.0.17.dfsg-2ubuntu1_all.deb
/var/lib/dpkg/info/alsa-base.conffiles
/var/lib/dpkg/info/alsa-base.list
/var/lib/dpkg/info/alsa-base.md5sums
/var/lib/dpkg/info/alsa-base.postinst
/var/lib/dpkg/info/alsa-base.postrm
/var/lib/dpkg/info/alsa-base.preinst

---

