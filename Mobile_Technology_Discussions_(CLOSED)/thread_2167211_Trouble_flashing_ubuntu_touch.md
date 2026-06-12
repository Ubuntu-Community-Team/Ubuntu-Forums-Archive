---
title: "Trouble flashing ubuntu touch"
date: 2013-08-12
forum: Mobile Technology Discussions (CLOSED)
---

### Post by frankennetbook on 2013-08-12
So I recently bought an android phone for the purpose of trying out ubuntu os on a phone. 

I bought a M-Horse 9500 mini which runs Android version 4.1.2, says kernel 2.6.35.7

I downloaded ubuntu successfully but when I went to deploy the image to the phone with:

phablet-flash cdimage-touch

and I got this error:
error: device not found
ERROR:phablet-flash:Command 'adb shell getprop ro.cm.device ' returned non-zero exit status 255

i then tried:

 adb devices

and got no list of connected devices, I also enabled USB debugging as required.  

Just wonder if anyone has any thoughts

---

### Post by Cheesemill on 2013-08-13
> **frankennetbook said:**
> So I recently bought an android phone for the purpose of trying out ubuntu os on a phone.

You should have researched what devices you can install Ubuntu Touch on, your phone isn't currently supported.

[https://wiki.ubuntu.com/Touch/Devices](https://wiki.ubuntu.com/Touch/Devices)

---

### Post by frankennetbook on 2013-08-13
I was under the impression that it was made specifically for Nexus phones / tablets but I thought that it could be made to work on most android phones.  

Also, shouldn't it at the least be visible to the computer?

---

### Post by grahammechanical on 2013-08-14
> I was under the impression that it was made specifically for Nexus phones / tablets

Specifically, Galaxy Nexus, Nexus 4, Nexus 7, Neuxs 10.

> I thought that it could be made to work on most android phones.

No. Only if the device has suitable hardware and someone has ported Ubuntu touch to it.

[https://wiki.ubuntu.com/Touch/Devices](https://wiki.ubuntu.com/Touch/Devices)

Regards.

---

### Post by Ams_Domingos on 2013-08-16
I'M ALSO HAVING THE SAME PROBLEM, TRIED TO INSTALL ON MY NEXUS 4. AND AT THE END OF THE INSTALLATION BEFORE RESET RETURN THIS ERROR: error: device not foundERROR:phablet-flash:Command 'adb shell mount /sdcard/' returned non-zero exit status 255

---

### Post by Ams_Domingos on 2013-08-16
Someone has a solution?

---

### Post by frankennetbook on 2013-08-17
Is there anything that needs to be done to make a phone "visible" to your computer?  I know when I plug my Samsung into the computer it shows up right away, not sure why this phone wouldn't show up as attached / plugged into usb or whatever....

---

### Post by Ams_Domingos on 2013-08-26
message appears at the end of the installation, after all procedures, after downloading and sending all files for the Nexus 4.

---

### Post by sG6QkYr on 2013-10-18
Need reactive USB Developer Mode ;)

Repeat the step 2.1 and 2.2 and try again.

---

### Post by elliotn on 2013-11-01
u need to enable Android debug mode in settings

---

