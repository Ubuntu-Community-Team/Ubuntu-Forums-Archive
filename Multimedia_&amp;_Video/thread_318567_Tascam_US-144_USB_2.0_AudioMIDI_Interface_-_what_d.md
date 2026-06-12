---
title: "Tascam US-144 USB 2.0 Audio/MIDI Interface - what do I need to do to get it working?"
date: 2006-12-14
forum: Multimedia &amp; Video
---

### Post by CapnWhizBang on 2006-12-14
Not sure if I've made another hardware blunder. (I returned the M-Audio Audiophile USB after a month of frustration) I haven't found any posts in the Ubuntu Forums regarding this device. Does anyone have any ideas what it will take for me to get this thing working in Ubuntu? I have been following the instructions found here for the US-122 (its predecessor) to no avail. Thanks....

---

### Post by ronlybonly on 2006-12-18
Sorry I can't help you on this one, but please let me know if you do get this device working because I am looking into purchasing it myself.

---

### Post by CapnWhizBang on 2006-12-19
It works very nicely. In Windows`XP. I haven't gotten any responses to my posts regarding Linux. I'm guessing that I'll have to wait until the necessary drivers/config files for Linux are written. For now I'm stuck using the Cubase LE software that came with the interface in Windows XP. For what I need it has been sufficient so far.

---

### Post by gnomeza on 2006-12-27
The Tascam 144 is not currently supported by the Tascam driver (snd-usb-usx2y).

That said, I don't think the Tascam 144 is too different from the 122.
At best, it's a case of adding the usb ID to the tascam driver (0x800f according to this post: [http://permalink.gmane.org/gmane.linux.alsa.devel/43192](http://permalink.gmane.org/gmane.linux.alsa.devel/43192)), and getting and loading the 144 firmware.

I've ordered one.

---

### Post by CapnWhizBang on 2006-12-27
I thought that it should not be a stretch to get the 144 working since it is supposedly nearly identical to the 122. I think the 144 has a digital in/out the 122 lacks.
I don't know what to do with the usb ID mentioned above, or how to acquire and load the firmware. 
When you get your unit and get it working, please share the process so I can get back to linux.

Thanks

---

### Post by gnomeza on 2007-01-11
Received one Tascam US-144 yesterday. Will get to play around with it tonight.

---

### Post by rems on 2007-01-20
I plan to buy the us144

Did anyone manage to get it working?

---

### Post by jonobo on 2007-02-12
Try this US-122 Howto:
[https://help.ubuntu.com/community/TASCAM_US-122#head-9b186d172cf30d97e983bfbe0e609c8863cd63f0](https://help.ubuntu.com/community/TASCAM_US-122#head-9b186d172cf30d97e983bfbe0e609c8863cd63f0)
Simply take the Firmware for the US-144 or try what happens with the US-122-Firmware (no warranties ;) ).

---

### Post by rems on 2007-02-15
Thanks for the link :)
I finally purchased a us 122L (which is cheaper than the us122), I tried to load us122's firmware on it, following your guide, but it didn't work: i'm stuck at step 8
I ran
```
sudo fxload -s ./usx2y-fw-0.1b/ld2-ezusb.hex -I /usr/share/alsa/firmware/usx2yloader/us122fw.ihx -D /proc/bus/usb/005/002
```
And I got
```
can't modify CPUCS: Broken pipe
```

Is it because the us122l is not compatible with the us122?
Besides I don't think there are much differences between those two, but I have no idea about what I have to change

---

### Post by sebbouckaert on 2007-02-18
Yep, I've got exactly the same situation with the US-122L interface. I use it in a professional recording setup in Windows XP. But since I have a dual boot system I'd like to get  this device working in Kubuntu just for more daily use. 

Any suggestions or help would be appreciated. Thanks.

---

### Post by rems on 2007-02-20
I think we should send an e-mail to the us122 firmware's author to ask him if he could adapt his code to the us122l
Since english is not my native language i suggest that some one else writes the letter :)

---

### Post by ssavelan on 2007-03-10
I got it working.. unfortunately I can't remember how... it was for a friend and it took a few hours to figure out.....

You will have to compile the ALSA drivers and firmware loaders and lib and such from source....
[URL="http://www.alsa-project.org/"]
http://www.alsa-project.org/[/URL]

Have fun boys and girls...

---

### Post by rems on 2007-03-11
Wow! I wonder how did you do that!
I guess you had to change some stuff in the driver.
Do you remember having the can't modify CPUCS: Broken pipe error while trying yo update the us122l's driver? And are you sure it was the us122l or us144 and not the us122?

---

### Post by gnomeza on 2007-05-08
Current status on Linux support can probably be followed here:
  [http://www.pps.jussieu.fr/~smimram/tascam/](http://www.pps.jussieu.fr/~smimram/tascam/)

---

### Post by edgar83 on 2008-06-15
Any news about us144 support?

---

### Post by sebbouckaert on 2008-06-15
mmmm...

me also waiting on news for US122L driver too...
but it still says that "This is just a matter of time now..."

so guess need to be a little more patient...

---

### Post by mcheccyb on 2008-06-26
so far this is the only thing that really has irritated me in linux.

every other bit of computer hardware i have got working with ubuntu, just not the tascam us-122l.

i'm really hoping someone develops a linux driver for it.

---

