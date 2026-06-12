---
title: "fglrxinfo showing mesa for &quot;ati radeon 200&quot;"
date: 2009-04-10
forum: Multimedia Software
---

### Post by rohit2412 on 2009-04-10
this is an old desktop having ati radeon 200 with 32 mb shared memory

fglrxinfo always shows me the mesa driver....(even after enabling from restricted drivers)

as such i followed this [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Verifying]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Verifying") 
including many other things i have tried(ati-installer,envy,restricted drivers,manual install)
this required removal of xgl-server
after i did that i am surprised to see my glxgears go from 150 to 750 but i still see mesa driver from fglrxinfo

earlier(150 fps) i was able to enable compiz but with bad results(but it worked)
but now (750 fps) enabling compiz gives me a white screen(i have composite enabled)

also can somebody tell me what "opengloverlay" in device section of xorg.conf means(i turned it on while experimenting but it gave no visible results)

---

### Post by cariboo on 2009-04-10
Have a look [here]("http://www.phoronix.com/forums/showthread.php?t=7588"), it may answer some of your questions.

Jim

---

### Post by markbuntu on 2009-04-10
fglrx is not installed properly. If it is using mesa then that usually means the kernel modules are missing.

apt-get purge fglrx

If you used envy, use envy to remove the driver. If you used the Hardware Devices use apt-get purge fglrx. If you get any errors please let us know.

Renstall the driver. Do not use ENVY. If you used envy at any point the driver is misinstalled. The best thing for you would be to get a newer driver from the ati site. Make sure it is one that supports the 200. I have a 200 on one of my machines and it works fine with fglrx in hardy and intrepid.

---

