---
title: "No sound in Ubuntu 6.06"
date: 2006-06-20
forum: Multimedia &amp; Video
---

### Post by jphekman on 2006-06-20
Hi all. I recently install Ubuntu 6.06. Note that I installed server, then upgraded to desktop, so it is possible that I may have failed to install an important package. Hardware is a Dell desktop (which I bought used, but I can dig up more specific specs if important).

Sound is not working. Specifically:

* lspci -v does detect my card:
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
        Subsystem: Dell: Unknown device 0151
        Flags: bus master, medium devsel, latency 0, IRQ 201
        I/O ports at ee00 [size=256]
        I/O ports at edc0 [size=64]
        Memory at febffa00 (32-bit, non-prefetchable) [size=512]
        Memory at febff900 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

* alsamixer sees my card and says: Card: Intel ICH5  

* System -> Preferences -> Sound has no cards listed in the "default sound card" dropdown

* gstreamer-properties, when I hit test, says (whether I specify autodetect, ALSA, or OSS) "could not open resource for writing"

* xmms says it couldn't open audio

Any help would be very much appreciated. Thanks!

---

### Post by glotz on 2006-06-20
Try adding **snd-intel8x0** to **/etc/modules** and restart.

---

### Post by jphekman on 2006-06-20
Turns out I needed to add myself to the audio group in /etc/group.

Note that the sound module was in fact loading so no editing of /etc/modules was necessary -- but thanks!

I submit that adduser ought to add the new user to the audio group automatically (I tested and it does not do so). (Could this have anything to do with the fact that I installed server and subsequently added the desktop packages on top?)

---

### Post by timholley on 2006-06-20
how did you add yourself to the group folder,and theres no group folder in my etc folder.

---

### Post by jphekman on 2006-06-21
[QUOTE=timholley]how did you add yourself to the group folder,and theres no group folder in my etc folder.[/QUOTE]

First, become root (su -). Then use your favorite text editor to edit the file /etc/group. 
Find the line that looks like this:

audio:x:29:

Add your username to it:

audio:x:29:jphekman

except I assume your username isn't jphekman, it's something else :)

---

### Post by timholley on 2006-06-21
oh ok,ty,i went and checked that line and my name is there.i checked in the users and groups thing in system-adminstration-users and groups and im in the audio group,its just not working:confused:

---

### Post by gosh on 2006-06-22
[quote=jphekman]First, become root (su -). Then use your favorite text editor to edit the file /etc/group. 
Find the line that looks like this:

audio:x:29:

Add your username to it:

audio:x:29:jphekman

except I assume your username isn't jphekman, it's something else :)[/quote] 
The strangest thing happened to me when trying this.
This is what my terminal came up with:

```
root@ubuntu:/home/jos# gedit /etc/group

(gedit:19686): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
- using device default
- using device default
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
root@ubuntu:/home/jos#

``` 
BTW, the file had this line audio:x:29:jos

---

### Post by timholley on 2006-06-22
ne other ideas of how to fix this/

---

