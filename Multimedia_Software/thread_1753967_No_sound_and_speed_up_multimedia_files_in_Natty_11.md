---
title: "No sound and speed up multimedia files in Natty 11.04..."
date: 2011-05-09
forum: Multimedia Software
---

### Post by NewReformist on 2011-05-09
So I don't know what happened, but all multimedia files are suddenly  speed up/and-or with no sound (Ubuntu 11.04 with all recent updates, firefox 4,  adobe flash-instick etc.)

If I try to play a flash movie on for instance Youtube it's sped-up with  no sound, if I play an MP3 song (I use Exaile) the bar is sped up and there's no sound  either, if I start an avi movie (VLC) it's not sped up but there's no sound  though.

When I log in to the system the logging in jingle is not playing, so basically the sound just got turned off for some reason but according to the soundbar it should be on.

This problem started just recently. I don't know if it has to do with  recent updates or that my log in re-started a couple of times after  using a KDE program (Kmess).

---

### Post by verymadpip on 2011-05-14
I suspect I have the same problem.
I've not reinstated my music files yet after a reinstall so I can't comment on that, internet video & startup jingle I can confirm.

As I've little to lose at this point I'll probably try a fresh install & see what happens, although a solution would be good.

---

### Post by lidex on 2011-05-14
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

No joy? Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by verymadpip on 2011-05-15
Thanks lidex, I'll give that a go when I get back home tonight.

Thinking ahead a little, rather than just whining about it, I could always file a bug report if it goes wrong.

---

### Post by verymadpip on 2011-05-15
I chickened out & reinstalled.

---

