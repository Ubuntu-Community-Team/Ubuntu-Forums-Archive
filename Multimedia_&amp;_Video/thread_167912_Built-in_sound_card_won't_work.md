---
title: "Built-in sound card won't work"
date: 2006-04-29
forum: Multimedia &amp; Video
---

### Post by neoaddict on 2006-04-29
I have a built-in sound card thing on my Pentium I computer and Ubuntu doesn't seem to recognize that there's one there.  It keeps on saying that it couldn't find any sound devices.

Any suggestions?  (By the way, I've downloaded the Gnome Sound Fix via Automatix)

---

### Post by deadgobby on 2006-04-29
You should also check that all your apps use alsa for utput. Such options are usually in every settings menu.
Also, check under multimedia systems selector that alsa is selected both for output and for sink.

Go To system > preferences > multimedia systems selector.

---

### Post by neoaddict on 2006-04-29
I've enabled Alsa, but I've tried creating a test pipeline to it with no luck.

Sound icon in the tray still is greyed out with a x.

---

### Post by deadgobby on 2006-04-29
[QUOTE=neoaddict]I've enabled Alsa, but I've tried creating a test pipeline to it with no luck.

Sound icon in the tray still is greyed out with a x.[/QUOTE]

Go up to the sound icon and right click. See if it's on mute, if not then go to open volume control. Goto edit>preferences, click on all the boxes and then go to play back tabe and see if all the volume controls are up. If so then test. If that does not work. Go back to the speaker icon and right click agian and goto preferences and see what dev it sees. 
if not check this link
[http://ubuntuforums.org/showthread.php?t=165638&highlight=sound](http://ubuntuforums.org/showthread.php?t=165638&highlight=sound)

---

### Post by neoaddict on 2006-04-29
Not on mute.

Can't open volume control - says no devices found.

Can't open alsamixer either in terminal, says functions are missing or something.

I've tried the dmreg (sp?) thing that I found by searching on the forums, but it only detected on PNP card, which was my modem.

---

### Post by deadgobby on 2006-04-30
you are doing to need to do some work here.... Should take about 5 minutes of cut and paste.
[http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)

---

### Post by neoaddict on 2006-04-30
Still doesn't work.  :(

---

### Post by deadgobby on 2006-04-30
[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=sound&titlesearch](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=sound&titlesearch)

---

### Post by neoaddict on 2006-04-30
Nope.  :(

I googled a lot and found that not really anyone got the CS4236b sound card to work on their system.

Dell's site told me to use sndconfig, but Ubuntu doesn't seem to have that.

I then went to Debian's site and found 0.68, but that apparently conflicts with pcuitils, so if anyone could find a version of sndconfig that doesn't conflict with any Ubuntu libraries, that'd be great.

---

### Post by deadgobby on 2006-05-02
Well you can go out and get a Sound Blaster Live card. You can run asla mixer and may work just fine. The cost is not really that much.

---

### Post by deadgobby on 2006-05-04
Hi try this and see if this works
mount --bind /dev /chroot/dev

---

