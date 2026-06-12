---
title: "Somebody pl. help me with my sound"
date: 2011-06-03
forum: Multimedia Software
---

### Post by jlroar on 2011-06-03
hi guys i have tried everyway to fix my sound using different posts from this forum and also have read the entire sound fixing guide here: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

but i still cant get my sound to work.. PL.Pl. pl. i need your urgent help .. I have ubuntu 10.04 installed, I can give you other info as u need it..

Cheers
Raj

---

### Post by jlroar on 2011-06-03
dont worry guys sound is working now, thx to "[atreides8081]("http://ubuntuforums.org/member.php?u=1078054")"

Try:

 	Code:
 	sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r) 
and reboot.

(it worked for me on a sony vaio.)

THX ubuntuforums for finally ending my frustration :d

---

