---
title: "looking for webcam driver"
date: 2010-01-20
forum: Multimedia Software
---

### Post by bloodytiger on 2010-01-20
hi

 i have encountered many problems opening my webcam. it is an integrated webcam. its model is    ID 05ca:1810 Ricoh Co., Ltd Pavilion Webcam [R5U870]. i have recently installed the r5u870 driver but still cant open it. i also tried many softwares such as cheez and camorama webcam viewer. but nothing happen. plz ubunto experts help out

ps : my laptop is hp dv 6426us with ubunto 9.10 as operating system

---

### Post by lyall on 2010-01-20
> **bloodytiger said:**
> hi

 i have encountered many problems opening my webcam. it is an integrated webcam. its model is    ID 05ca:1810 Ricoh Co., Ltd Pavilion Webcam [R5U870]. i have recently installed the r5u870 driver but still cant open it. i also tried many softwares such as cheez and camorama webcam viewer. but nothing happen. plz ubunto experts help out

ps : my laptop is hp dv 6426us with ubunto 9.10 as operating system

see the following links
[https://help.ubuntu.com/community/Webcam]("https://help.ubuntu.com/community/Webcam")
and
[https://help.ubuntu.com/community/]("https://help.ubuntu.com/community/")
and scroll down to **4.16 WebCams**

hope this helps
it is a place to start looking

good luck and have fun learning

---

### Post by bloodytiger on 2010-01-21
i tried to install easycam but cant be installed it repquires dependency python2.4-glade2
i googled it but couldnt find it

so i tried to install gspca it was installed but couldnt be launched

---

### Post by janthonywj on 2010-01-22
Hi, 

I'm getting frustrated trying to look for an answer to what I think is a simple solution. I can't get my built in webcam or mic to work. I have a Sony Vaio VGN-FZ140E (upgraded to 4GB Ram). 

Every search I do comes up with solutions to older versions of Ubuntu that don't apply anymore. (I think) I'm running 9.10 64-bit. 

I assume that if lsusb shows the correct device the driver would be installed correctly? Attached is the screenshot. 

Bus 001 Device 002: ID 05ca:1837 Ricoh Co., Ltd Visual Communication Camera VGP-VCC4 [R5U870]

I don't know why it wouldn't be working. Any help would greatly be appreciated.

---

### Post by hifimusic on 2010-02-03
I have ubuntu 9.10 installed on a Vaio FZ140E and everything works beautifully.

For microphone: you just need to fiddle with the audio settings a bit. the default audio device selected is wrong. change that to the other available option.

For webcam: go to 

[http://linux.softpedia.com/progDownload/ricoh-webcam-r5u870-Download-30296.html](http://linux.softpedia.com/progDownload/ricoh-webcam-r5u870-Download-30296.html)

and download 

Ubuntu DEB i386 (firmware)
[ubuntu_deb] [97.50 KB]

or 	

Ubuntu DEB amd64 (firmware)
[ubuntu_deb] [97.50 KB]

and install the package

and it should start working.

---

### Post by fishtoprecords on 2010-02-04
> **hifimusic said:**
> For microphone: you just need to fiddle with the audio settings a bit. the default audio device selected is wrong. change that to the other available option.

Thank you @hifimusic. I was having trouble with skype, and changing the audio input device fixed it. I think my laptop was defaulting to the mic-input jack, not my Logitech webcam/mic setup.

---

### Post by no2498 on 2010-02-05
janthonywj

open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 or v4l2
click the bottom test button for each

get programs cheese and wxcam 1 of the 2 will see your cam

if gstreamer is not installed install it

---

