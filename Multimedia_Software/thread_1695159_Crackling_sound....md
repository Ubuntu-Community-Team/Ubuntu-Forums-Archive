---
title: "Crackling sound..."
date: 2011-02-25
forum: Multimedia Software
---

### Post by motermouth15 on 2011-02-25
I have searched around the forums for help but haven't had any luck with finding a solution. Suddenly one day last week, after i restarted my computer, whenever i watch a movie i get more crackles than sound. 

I have a ubuntu server running 10.04 with samba shares set up. Everything I do is streamed to and from my server, however, even once I move the movie to my local harddrive, the problem still exists.

After searching other forums, i tried switching everything to the ALSA, along with unmuting my PCM, however none of this worked.

[edit]I forgot to mention that if i stream music off of pandora, grooveshark, or even music off of my server, i have no problems at all.

Any help would be extremely appreciated!! Thanks!!

---

### Post by motermouth15 on 2011-02-28
any ideas?

---

### Post by lidex on 2011-03-01
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by jbollom on 2011-04-29
Hey,

Im having the same problems
In running ubuntu server 10.04. Its an intel server motherboard that doesent have sound so im using a creative usb sound card
have also tried my creative wireless usb headphones and they are the same
any help would be great

here is my alsa info
[http://www.alsa-project.org/db/?f=bcf324d2f68891df21103d64c52c3d291dba2910](http://www.alsa-project.org/db/?f=bcf324d2f68891df21103d64c52c3d291dba2910)

Josh

---

### Post by jbollom on 2011-04-29
I have found something very unusual
if i open a massive log file with gedit the crackly goes away
once i close gedit it comes back
i have no idea what this could be

---

