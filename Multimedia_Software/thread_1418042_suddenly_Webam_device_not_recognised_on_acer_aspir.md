---
title: "suddenly Webam device not recognised on acer aspire one"
date: 2010-02-28
forum: Multimedia Software
---

### Post by cello_911 on 2010-02-28
I have been using netbpok remix for some time .. and all of the sudden the internal webcam is not recognised ,, no device appears neither on test or cheese, or amsn or skype ..I get the colours bars and thats it,,

any ideas on how to get the device recognised again? ..

thanks

cello

---

### Post by needledreams on 2010-04-28
This is happening to me too.  I'm getting frustated!

I have an Acer Aspire One AOA150.  The 1st time I installed UNR it worked.  Then I had to uninstall and install it again because the wireless wasn't detecting. No I tried again the camera and is not working.  

I read a thread about a generic driver but I'm new in this and what I was reading was complicate and I'm afraid of screwing up.

Also the card readers (for SD) are not working.

---

### Post by no2498 on 2010-04-29
in cheese try making the pic size smaller
cheese has all the webcam settings nowdays

hope this helps

---

### Post by no2498 on 2010-04-29
ops just reread it
open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

should reset the dev's

---

### Post by joao.taborda on 2010-05-24
same problem...

i run gstreamer-properties and got this answer:

Video for Linux (v4l): Device "/dev/video0" does not exist. 

lsusb didn't return the camera (nor the SD card readers...altought i don't know if it should)

---

### Post by joao.taborda on 2010-05-24
my out put for lsusb is

```
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

everytime i see others posting their lsusb listing there are many more devices... my camera is not appearing there and any ather device.... except the usb port (i assume that's what is listed :-/)

---

### Post by no2498 on 2010-05-25
look in the  addremove programs see if you have gstreamer good, bad, ugly installed

---

### Post by no2498 on 2010-05-26
and have you did this yet

sudo apt-get install ubuntu-restricted-extras

---

### Post by joao.taborda on 2010-05-27
> **no2498 said:**
> look in the  addremove programs see if you have gstreamer good, bad, ugly installed

in synaptic?...or in the software center?... i can find different gstreamer packages already installed in synaptic...

what do you mean with good bad or ugly installed?

and i already have the ubuntu-restricted-extras installed...

any other clues?

---

### Post by no2498 on 2010-05-27
just type gstreamer in the add remove
or synaptic


add remove tells you, good, bad, or, ugly
you need all 3

synaptic dont

---

### Post by joao.taborda on 2010-05-28
i have all the gstreamer good bad and ugly.... and reallly think it's not the gstreamer software that's not working....

i found it very strange the output of *lsusb* I posted above... can someone with an aspire one check it? shouldn't it appear the webcam on the list?

---

### Post by no2498 on 2010-05-28
cheese has a good help file in it look in its faq's

it tells you how to change the plugin in gstreamer-properties

hope this helps

---

### Post by no2498 on 2010-05-28
btw did you try v4l1 and v4l2  gstreamer-properties
click the bottom test button for each 1

---

