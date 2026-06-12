---
title: "Pinnacle Remote Kit w blaster anyone have it working"
date: 2008-06-14
forum: Mythbuntu
---

### Post by mark467 on 2008-06-14
This is the remote:

[http://www.pinnaclesys.com/PublicSite/us/Products/Consumer+Products/PCTV+Tuners/PCTV+Vista+Companion/Pinnacle+Remote+Kit+for+Windows+Media+Center.htm](http://www.pinnaclesys.com/PublicSite/us/Products/Consumer+Products/PCTV+Tuners/PCTV+Vista+Companion/Pinnacle+Remote+Kit+for+Windows+Media+Center.htm)

Does anyone have one and have it working?
Can anyone point me in the right direction?

---

### Post by mark467 on 2008-06-19
Does anyone have this remote? Any luck at all getting it to work?

---

### Post by Nikitas350 on 2008-06-19
I don't know much about remote kits but I found this (using google):
[http://wiki.epfl.ch/cfavi/mythtv](http://wiki.epfl.ch/cfavi/mythtv)
and this
[http://wiki.epfl.ch/cfavi/documents/lircrc](http://wiki.epfl.ch/cfavi/documents/lircrc)
Good luck

---

### Post by jjuzwik on 2008-06-19
> **mark467 said:**
> This is the remote:

[http://www.pinnaclesys.com/PublicSite/us/Products/Consumer+Products/PCTV+Tuners/PCTV+Vista+Companion/Pinnacle+Remote+Kit+for+Windows+Media+Center.htm](http://www.pinnaclesys.com/PublicSite/us/Products/Consumer+Products/PCTV+Tuners/PCTV+Vista+Companion/Pinnacle+Remote+Kit+for+Windows+Media+Center.htm)

Does anyone have one and have it working?
Can anyone point me in the right direction?

I have this remote, and was able to get it working by closely reading 'the_crowbar's post in this thread:

[LINK]("http://ubuntuforums.org/showthread.php?t=388728&highlight=lirc&page=4")

---

### Post by mark467 on 2008-06-22
I tried that but the make portion did not work. I will try again and post the errors.  
Thanks

---

### Post by mark467 on 2008-06-22
Ok now its working. I had to add 
sudo apt-get install build-essential
before the configure and make would work

then I did  this

Mythbuntu seems to look at the lirc_mceusb2.ko file in the "/lib/modules/2.6.22-14-generic/ubuntu/media/lirc/lirc_mceusb2" directory. So we just copied the new driver file from "/lib/modules/2.6.22-14-generic/misc" to the other directory and it worked right away.

Still not working. I wonder if my lirc is working right at all.

---

### Post by ThisOneIsFree on 2008-08-06
I was able to get the remote working, following the instructions of the thread above.

Now i m working on the blaster part... but at the moment i can't change any channel from the usb tranceiver. Is there someone that was able to use the tranceiver part of the pinnacle remote kit ?

---

