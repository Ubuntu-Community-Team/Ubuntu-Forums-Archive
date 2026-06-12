---
title: "Problem playing videos"
date: 2011-04-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by artjermyn on 2011-04-13
I seem to be having a weird problem when playing video files (using movie player & vlc).  I can play the video fine, but when i attempt to move the player window, x seems to crash and pops me back into the login screen.

Anyone else with this problem?  I've searched the forums and found nothing.

I'm using ubuntu classic with the latest (4/13) daily build.

video card:
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01) (prog-if 00 [VGA controller])
	Subsystem: Giga-byte Technology Device d000
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 11
	Memory at d8000000 (32-bit, prefetchable) [size=64M]
	Memory at dd000000 (32-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at de000000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel modules: viafb

---

### Post by KegHead on 2011-04-13
Hi!

I have problem also.

I can stream videos, but I can't play them when download is complete.

VLC & movie player.

Running 11.04b2/classic/2.6.39-999

KegHead

---

### Post by Harry33 on 2011-04-14
Try playing without Compiz, for example in Ubuntu Classic DE.

---

### Post by mc4man on 2011-04-14
> **artjermyn said:**
> I seem to be having a weird problem when playing video files (using movie player & vlc).  I can play the video fine, but when i attempt to move the player window, x seems to crash and pops me back into the login screen.

Anyone else with this problem?  I've searched the forums and found nothing.

I'm using ubuntu classic with the latest (4/13) daily build.

if you want to see if compiz is involved do a logout and then log in w/ Classic (no effects) -
( metacity

---

### Post by KegHead on 2011-04-14
Hi!

I'm using 11.04b2/classic/2.6.39-999.

KegHead

---

### Post by dino99 on 2011-04-14
> **KegHead said:**
> Hi!

I'm using 11.04b2/classic/2.6.39-999.

KegHead

i have had problem too and have to uninstall mozilla-plugin-vlc (dont work with FF4.0)

---

### Post by KegHead on 2011-04-14
Hi!

I can play video's I already have.

When I download from (as an example) from Extratorent the video streams, but I can't play once it's downloaded.

I've also tried UMPlayer w/no success.

Any ideas?

KegHead

---

### Post by artjermyn on 2011-04-14
I've tried it on a fresh install without any vlc plugins.  It seems to be a xorg problem.  There is a bug report in launchpad.  

Maybe you can use the ubuntu-bug program to report the error.  I've tried and even though it crashes, I can't seem to get it to create a crash report.

[https://bugs.launchpad.net/bugs/752405]("https://bugs.launchpad.net/bugs/752405")

---

### Post by KegHead on 2011-04-14
Thanks!

I guess it will be fixed.

KegHead

---

### Post by artjermyn on 2011-04-14
This:[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/760743]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/760743")

This bug has been added to launchpad.  If you're affected by this, you may want to go over and mark that it affects you and/or post some details (ubuntu-bug app).

---

