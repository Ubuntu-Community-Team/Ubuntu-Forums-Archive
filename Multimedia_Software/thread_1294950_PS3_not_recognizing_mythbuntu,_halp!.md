---
title: "PS3 not recognizing mythbuntu, halp!"
date: 2009-10-18
forum: Multimedia Software
---

### Post by S0VERE1GN on 2009-10-18
HEy all. 

recently installed mythbuntu and got it up and running. File sharing works for my LG blue ray in my bedroom, but my PS3 does not see the mythbuntu box. any help? 

ALSO: i had file sharing going on media tomb for the ps3 and the LG, but it was very sluggish...mythbuntu runs nice and fast, but won't work for ps3...

---

### Post by S0VERE1GN on 2009-10-19
bump!!! anyone know?

---

### Post by csrbrendan on 2009-10-19
Please does somebody know the answer? I got the same problem, Thanks!

---

### Post by S0VERE1GN on 2009-10-19
breakfast bump. 

i just updated today (kinda forgot to do that...) going to see if that changes anything.

---

### Post by S0VERE1GN on 2009-10-19
updates still didnt help. 

going to just try and install mediatomb again.

---

### Post by owenlinx on 2009-11-17
Mine is working well. If you go into the backend setup>General change the 127.0.0.1 to the computers ip address (mine is 192.168.1.10) it will show up over upnp. 
1 more tip go to [http://ip](http://ip) address/mythweb/settings/video then look for VideoStartupDir: add your files like this  
```
/home/justin/Videos/:/home/justin/Music/:
``` 
They will be scanned every 20 min. 

Oh and one more thing To watch a HD recording try 
```
ffmpeg -i INPUT -vcodec mpeg4  -b 3500k -acodec libfaac -ar 32000 -ab 128k -f mp4 OUTPUT.mp4
or if you have time
ffmpeg -i INPUT -an -pass 1 -vcodec libx264 -vpre fastfirstpass -b 4000k OUTPUT.mp4 && ffmpeg -i INPUT -acodec libfaac -ab 128k -pass 2 -vcodec libx264 -vpre hq -b 4000k OUTPUT.mp4
```
For sd stuff try this
[http://ubuntuforums.org/showthread.php?t=346778](http://ubuntuforums.org/showthread.php?t=346778)

Good Luck

---

