---
title: "VLC freezes"
date: 2010-05-18
forum: Multimedia Software
---

### Post by Criminel on 2010-05-18
Hi,
When playing video files with VLC under 10.04 ubuntu the video freezes (7 times in a 1 hour video) while the audio keeps playing.
I'm guessing cache or other memory issues,  or even too many processes going at once (even if VLC is the only software running whne I'm watching a movie) but I'm unabe to detect the problem.
This happens while playing files from burned discs or from the CPU itself. Any ideas?

Thanks  a  lot.

---

### Post by MMoudry on 2010-06-11
I have the same problem... do you have nVidia card?
Only way to fix this without restarting is to do a 'service gdm restart'

---

### Post by MMoudry on 2010-06-14
Right, I found out that simply killing the VLC process is enough. The XServer in itself doesn't freeze.

---

### Post by 666hunter666 on 2010-07-13
I dunno about x server freezing or not, but I'm having the same problem as above. every once in a while my VLC will freeze up for about 10 seconds or so then continue on.  it only occurs like every half hour-45 minutes or so (just a guess) and Audacious is doing the same thing although not to as great an extent.  And rebooting and restarting gdm doesn't seem to help. it always occurs.  I'm running Ubuntu 10.04 LTS on a p4 3.0ghz prescott in an MSI V class board with 2GB system ram and an nVidia 7300 GT AGP 512MB and the proprietary display drivers.  any help would be appreciated.

---

