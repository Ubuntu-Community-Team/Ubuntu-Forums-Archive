---
title: "ASUS 1015E-DS03 Netbook  Sound does not work"
date: 2014-04-24
forum: Multimedia Software
---

### Post by izquierdista on 2014-04-24
Hello,
I purchased a refurbished laptop that came with Ubuntu pre-installed thinking that it would run great out of the box. Well everything works BUT NO SOUND!!!


I go to the "Sound Settings" and nothing is shown in the "Play sound through" section, I have even tried plugging in my headphones but no sound is heard either.

Is there a driver or something that I can install to make this work??

here are the specs:

Netbook: ASUS 1015E-DS03
Soundcard: Intel pantherpoint HDMI
OS: Ubuntu 12.04LTS

I dont know if the following information is of any help:

talticpac@talticpac-1015E:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
Subdevices: 1/1
Subdevice #0: subdevice #0
talticpac@talticpac-1015E:~$


I would greatly appreciate any help you can provide me with.

---

### Post by trag on 2014-04-25
download ' restricted drivers ' and ' Gstreamer ' either through the software center or via synaptic package manager. Once installed your sound should work
good luck
trag

---

### Post by izquierdista on 2014-04-25
I went ahead and installed Gstreamer and when I went to the "additional drivers" and activated the ones listed. 

I rebooted the computer but the sound still doesnt work

see the printscreens I have attached to this reply to see what I am talking about.

---

### Post by trag on 2014-04-25
when you say you went to the "additional drivers" are you referring to the "restricted extras"?or something else, they are separate and distinct entities. Additional drivers are found in system settings and restricted extra's are in the software center.

---

### Post by izquierdista on 2014-04-25
thanks for the clarification. I went to synaptic package manager just now and found the package called "restricted extras" and installed it but I still dont hear anything :(

---

### Post by Yellow Pasque on 2014-04-25
Test out a LiveCD/USB of Ubuntu 14.04. If sound works there, then you probably need to upgrade your kernel (or just run Ubuntu 14.04...).

---

### Post by trag on 2014-04-25
I checked out the user manual for the 1015 series,there is a special function key on the keyboard to mute/unmute the audio. hit the blue 'fn' +  f10 key which should have a crossed speaker icon.Hope this works.
Just as a side note to all this there is a linux distro available that has been built specifically for EEE netbook users called Leeenx. check it out here   [http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Leeenux-51809.shtml](http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Leeenux-51809.shtml) it might be worth taking a look at,then again maybe not.

good luck
trag

---

### Post by izquierdista on 2014-04-27
I did a fresh install of Ubuntu 14.04 64 bit thinking that might fix the problem but I still have the exact problem, I still have no sound :( I am so confused

---

