---
title: "No sound"
date: 2007-09-25
forum: Multimedia &amp; Video
---

### Post by mpgarate on 2007-09-25
I'm not sure my sound card model, but ubuntu has had no problems with it, until today. I re-installed, and sound worked, but as soon as I tried to get mp3 support going, (via 2x clicking on an mp3 file, and following the dialogs from movie player) I got no more sound. red X on sound icon in corner, and some generic errors

> The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

and
> 
No volume control GStreamer plugins and/or devices found.


help please?


edit: just a thought.. it may be the kernel I'm using. I have a 64bit dual core, but am running the standard ubuntu release (32 bit). The kernel up now is named i386 (or something similar) and the one I ran before, when I'm sure sound was working, was 'generic.' i will test and edit this post again.

---

### Post by soltanis on 2007-09-25
I have almost the exact same problem. Did it happen to you after you installed kernel updates or linux headers or something?

---

### Post by mpgarate on 2007-09-25
okay yeah i was right. first off ill list a few key specs

ubuntu gutsy, dual core amd 64, dell integrated (nvidia?) sound card

broken when I upgraded my kernel to 'Ubuntu gutsy (development branch), kernel 2.6.22-12-386' I lost sound

I load 'Ubuntu gutsy (development branch), kernel 2.6.22-12-generic' and I get sound!!

I changed my grub menu to make the the default via

> sudo gedit /boot/grub/menu.lst

---

### Post by fede82 on 2007-09-25
Same happened to me. Using an onboard realtek from an nforce2 motherboard.
Stopped working (almost surely) after upgrading the kernel yesterday.

( post: [http://ubuntuforums.org/showthread.php?t=559881&highlight=sound+card+stopped+working]("http://ubuntuforums.org/showthread.php?t=559881&highlight=sound+card+stopped+working")) 

maybe it is some bug with this kernel?

---

### Post by ~LoKe on 2007-09-25
-386 is way outdated.  -generic supports more. ;)

---

### Post by fede82 on 2007-09-25
fixed it!
installed realtek drivers [http://www.realtek.com.tw/downloads/]("http://www.realtek.com.tw/downloads/") again (don`t know why the first time didn`t work)

hope it stays that way!

---

### Post by frenchcr on 2007-09-26
> **mpgarate said:**
> I'm not sure my sound card model, but ubuntu has had no problems with it, until today. I re-installed, and sound worked, but as soon as I tried to get mp3 support going, (via 2x clicking on an mp3 file, and following the dialogs from movie player) I got no more sound. red X on sound icon in corner, and some generic errors
...
and
....
help please?

edit: just a thought.. it may be the kernel I'm using. I have a 64bit dual core, but am running the standard ubuntu release (32 bit). The kernel up now is named i386 (or something similar) and the one I ran before, when I'm sure sound was working, was 'generic.' i will test and edit this post again.


I have exactly the same problem and no idea how to fix it.

upgraded kernel from **2.6.22-11-generic** to **2.6.22-12-386**

Compiz fusion just crashes too.

---

### Post by mpgarate on 2007-09-26
im not sure about compiz... but when booting, at the grub menu, choose the one that says 'generic'

if you then boot up and everything works, just do that every time

---

### Post by master_kernel on 2007-09-29
Same here after upgrade to 2.6.22.9 vanilla.

---

### Post by bonusiso on 2007-09-29
i had the same problem... i have tried lots of things but finally i recognised that it was easy one...

type gnome-volume-control on terminal, then open the PCM, then your sound is back...

i hope it will work :)

---

