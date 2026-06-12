---
title: "No sound/choppy sound"
date: 2010-10-24
forum: Multimedia Software
---

### Post by clickwir on 2010-10-24
Since upgrading to 10.10 from 10.04, I've had a lot of sound problems. So, I completely wiped and realoaded Kubuntu 10.10 64bit today. COMPLETELY reloaded from nothing. 

Still have the problem. 

```

lspci
00:00.0 Host bridge: Intel Corporation 82Q35 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82Q35 Express PCI Express Root Port (rev 02)
00:03.0 Communication controller: Intel Corporation 82Q35 Express MEI Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DM-2 Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IO (ICH9DO) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV770 LE [Radeon HD 4800 Series]
01:00.1 Audio device: ATI Technologies Inc HD48x0 audio
04:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface (rev b2)
07:00.0 Multimedia audio controller: Creative Labs SB X-Fi

```

Flash, for example, has no sound. Amarok does have sound, but it's very choppy. Like it's trying to decode as fast as possible and trying to play it at the same time. It's not an even sound at all. I don't have startup and shutdown sounds, ie. KDE events.

I did check KMIX and the default sound is the X-FI. I'm not using any special ATI drivers, just whatever Kubuntu decided to choose for me at install/boot. 

Help!

---

### Post by clickwir on 2010-10-24
OH yea.... I also get a lot of these in /var/log/messages when sound is trying to play but very choppy.

Oct 24 19:40:38 ruger10-22 pulseaudio[1686]: ratelimit.c: 2 events suppressed
Oct 24 19:42:59 ruger10-22 pulseaudio[1686]: ratelimit.c: 19 events suppressed
Oct 24 19:43:10 ruger10-22 pulseaudio[1686]: ratelimit.c: 24 events suppressed
Oct 24 19:43:30 ruger10-22 pulseaudio[1686]: ratelimit.c: 3 events suppressed

---

### Post by checho4 on 2010-10-26
I too am having a similar problem.  I've been running Kubuntu 10.10 from a clean install for about 2 weeks now and have been very happy with it.  However, this same problem started for me about an hour ago.  My /var/log/messages looks similar as well:

Oct 26 13:33:41 kxps pulseaudio[2027]: ratelimit.c: 1 events suppressed
Oct 26 13:33:52 kxps pulseaudio[2027]: ratelimit.c: 12 events suppressed
Oct 26 13:34:02 kxps pulseaudio[2027]: ratelimit.c: 2 events suppressed
Oct 26 13:34:08 kxps pulseaudio[2027]: ratelimit.c: 3 events suppressed

Any help would be greatly appreciated!

---

### Post by clickwir on 2010-10-26
Do you have multiple sound cards? HDMI? Wondering if pulseaudio is getting confused with everything?

I have an ATI card that does HDMI, an addon X-FI board and also onboard with my motherboard. ONboard is disabled in BIOS though. And I think I have the ATI HDMI blacklisted. But I still have trouble.

---

### Post by clickwir on 2010-10-31
Didn't fix the problem, but I'm not having the problem. I saw lots of other people are having trouble with X-Fi cards. Took out mine and replaced it with an old Diamond Monster Sound (ES1968) and sound is great now.

---

### Post by clickwir on 2010-10-31
I take that back. I get sound, but it's still choppy. Still getting a lot of pulseaudio ratelimit in /var/log/messages. 

```
Oct 31 23:22:49 ruger10-22 pulseaudio[1641]: ratelimit.c: 6233 events suppressed
Oct 31 23:23:30 ruger10-22 pulseaudio[1641]: ratelimit.c: 6250 events suppressed
Oct 31 23:23:35 ruger10-22 pulseaudio[1641]: ratelimit.c: 22715 events suppressed
Oct 31 23:23:40 ruger10-22 pulseaudio[1641]: ratelimit.c: 14886 events suppressed

```

I don't know. I guess I better wait till pulseaudio gets fixed again. I don't know what else could be going on.

---

### Post by Zorael on 2010-11-02
I get this in some select programs (notably VLC), which I fixed by setting PulseAudio to default to using 48khz sound. I have a netbook with an integrated Intel HDA chipset.

Open up **/etc/pulse/daemon.conf** and look for the following line;
```
;default-sample-rate = 44100
```
...and change it to the following (note missing semicolon);
```
default-sample-rate = 48000
```
Then restart PulseAudio and try again.
```
$ pulseaudio -k
$ pulseaudio -D
```
(or just reboot)

---

