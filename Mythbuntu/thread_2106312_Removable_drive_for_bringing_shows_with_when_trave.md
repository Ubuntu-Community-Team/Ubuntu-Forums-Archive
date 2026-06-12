---
title: "Removable drive for bringing shows with when traveling"
date: 2013-01-18
forum: Mythbuntu
---

### Post by itlarson on 2013-01-18
Does anyone know if the Seagate GoFlex Satellite 500GB will mount properly when plugged into a linux computer?  On one hand it's just a NTFS external hard drive.  On the other hand seagate has a cryptic comment on their website about linux not being able to prevent it from sleeping. Also, is it a problem if the computer only has usb 2.0?

---

### Post by helpee on 2013-01-18
I've never met a usb storage drive that wouldn't mount with a good 'ole " mount -o ". As far as keeping it from sleeping, as long as you're actively using it ( ie, copying files over ), it should stay awake. These things generally don't fall asleep in the middle of an action.

From their website
[http://www.seagate.com/external-hard-drives/portable-hard-drives/wireless/seagate-satellite/](http://www.seagate.com/external-hard-drives/portable-hard-drives/wireless/seagate-satellite/)
the drive is USB 2.0 backwards compatible.

---

### Post by itlarson on 2013-01-19
Thanks for the advice.  It soundslike the worst case is I'd have to unplug and re-plug it after it's been idle for a while.  Could it be woken by a script which unmounted and remounted it?

---

### Post by helpee on 2013-01-19
You could make a cron job for every 5 minutes that runs a script that adds and then removes an empty file.

Make your script something like this, for the purposes of this post, lets call it script.sh

;#!/bin/bash

;lsusb | grep YourDevice > /dev/null 2>&1
;CHECK=$?
;if [ $CHECK = 0 ]
;	then
;		echo > /path/to/your/empty/file
;		sleep 3
;		rm /path/to/your/empty/file
;fi

Save it and make it an executable file

Make a crontab for it

sudo gedit /etc/crontab

Add the following line

*/5 * * * * /path/to/script.sh &

Save and exit. 

Restart cron

sudo /etc/init.d/cron restart

Hope this helps!

Cheers

---

### Post by SeijiSensei on 2013-01-19
It would probably wake up just by unplugging and replugging the USB cable.  

I have a Maxtor external that goes to sleep but reawakens whenever Linux tries to write to the device.  I've never had to intervene manually at all.

---

### Post by itlarson on 2013-01-20
Thanks for the advice. This is for my parents, who I built a mythbox for.  They got an iPad (against my advice), and I am now looking for a way for them to watch their TV shows on it when they travel.  This drive seems about the best in terms of reviews, capacity, and brand name.

---

### Post by greg_ory on 2013-01-20
Found that in the Seagte Forum:

Can I play files from my GoFlex Satellite to my Linux computer?
***************************************************************
Linux is not supported by Seagate Support, however as long as your version of Linux has appropriate browser support, media player capability, and wireless connectivity, it should be able to connect and play files. When connecting via USB, the drive may go to sleep and cause errors if Linux doesn't wait for it to wake up. There is no tool available to disable the sleep feature under Linux.

Even I believe that any external hard drive that is windows compatible is Linux compatible it would still worry me that the manufacturer says that the drive is not supported on Linux. I changed entirly the way I buy my hardware what means if the hardware is not linux supported I don't buy.

That of course is everyone's own decision.

-Greg

---

### Post by nickrout on 2013-01-21
Those drives have problems in linux, as demonstrated by the above posts. Simply don't give your money to them. There are a million cheap USB hard drives out there, even 1TB ones are relatively cheap. Just get a standard black box one off the shelf at your local electronics shop.

---

