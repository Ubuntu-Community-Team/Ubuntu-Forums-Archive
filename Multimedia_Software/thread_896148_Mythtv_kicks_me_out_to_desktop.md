---
title: "Mythtv kicks me out to desktop"
date: 2008-08-20
forum: Multimedia Software
---

### Post by kristersaurus on 2008-08-20
Hey guys,

Ive got an old dell latitude c610 laptop i've installed the mythtv frontend on. It can talk to the database just fine, but when i try to watch tv, the screen goes blank and kicks me out to the desktop. There are no errors in the frontend logfile.

The frontend works fine when i boot from the mythbuntu live cd. Obviously, this isn't something that is possible to do all the time.

Any ideas?

Thanks.

---

### Post by NT4usB on 2008-08-21
Run mythfrontend from a terminal:```
mythfrontend -v all
``` and look at the errors.
Usually, it's either the directory to hold recordings doesn't exist or, if it does, myth doesn't have permissions to write to it.
Live TV writes to the recording directory... so it's not really 'live' but cached so you can pause, ffw, & rewind.

---

### Post by kristersaurus on 2008-08-21
Thanks for the tip. Don't know why i didn't think of that. I'll give that a shot and let you know how it goes.

---

### Post by kristersaurus on 2008-08-21
Looks like its seg faulting:

2008-08-21 22:42:41.787 write -> 22 49      QUERY_FILETRANSFER 24[]:[]REQUEST_BLOCK[]:[]65536
2008-08-21 22:42:41.786 AO: no change exiting
2008-08-21 22:42:41.787 AO: Pause 1
2008-08-21 22:42:41.787 AO: OutputAudioLoop: audio paused
2008-08-21 22:42:41.788 AO: 65536 bytes free on soundcard
2008-08-21 22:42:41.790 AO: 61824 bytes free on soundcard
2008-08-21 22:42:41.792 AO: 58144 bytes free on soundcard
2008-08-21 22:42:41.795 AO: 58544 bytes free on soundcard
2008-08-21 22:42:41.797 AO: 58944 bytes free on soundcard
Segmentation fault

Also, sometimes i get Unable to open mixer ALSA:default followed by a seg fault.

Im a noob when it comes to linux sound drivers...but maybe using alsa is the issue...any clues?

I've also tried setting sound device to NULL with no luck. same seg fault.

---

### Post by NoVista on 2008-08-22
It's a known bug if you have xserver-xgl installed.

Came back to edit and now not sure .. ..

---

### Post by kristersaurus on 2008-08-23
good thinking, but I do not have xserver-xgl installed.

---

