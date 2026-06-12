---
title: "Setting Default Soundcard Manually"
date: 2006-06-21
forum: Multimedia &amp; Video
---

### Post by yawnster on 2006-06-21
Howdy guys,

I installed XMMS a few days ago, got all my MP3 files sorted last night, all working perfectly, turned the puter off for the night, switched it on again this morning and no sound at all..

I think I have narrowed down the problem though, When I go to System->Prefs->Sound and look at the Default Soundcard its not connected to the right one.. It should be on NVIDIA nForce2 but its on something different, [AK5370]("http://www.asahi-kasei.co.jp/akm/en/product/ak5370/ak5370.html") which after doing a little searching seems to be some sort of USB Audio Controller..

I was therefore wondering if anyone could supply a manual command to reset the Soundcard as everytime I select nForce2 from the drop-box it will just switch back to AK5370 after closing the window.

Yawnster

PS.. On Kernel 2.6.16.19, this was needed to get my wireless card to work correctly..

---

### Post by yawnster on 2006-06-21
Hmm.. I seem to have fixed this problem by clearing out old kernels.. I did have a few old kernels in place.. (2.6.15.23 and 2.6.15.25) after removing the 2.6.15.23 one my sound now works on the right kernel.. however sound is now buggered on the remaining backup kernel, 2.6.15.25.. hmm interesting..

Oh well.. Got it working now..

Yawnster

---

### Post by degel3030 on 2006-06-22
can you tell me how you cleared out the old kernels? i am having the same problem, except its effecting mplayer, really really annoying

---

### Post by unco on 2006-09-20
Can someone post how to clear out kernals, I've got the same problem and found my ubuntu switches sound device between NVIDIA nForce2 and AK5370 driver on alternate boots/restarts. So sound device not found when starting mplayer every second time I boot.

Result is that my to boot ubuntu takes nearly as long and booting windows, when you consider I need to boot it twice in a row.

---

### Post by dannyboy79 on 2006-09-22
Interesting, after I played xmms on my machine my sound broke and doesn't play out of the right channel, it only works from the left? SO I wonder what xmms does to the alsa config or whatever to screw things up? I stil haven't figured it out. I would also be intersted in figuring out how to clear old kernels? thanks

---

### Post by unco on 2006-09-22
This resolved my problem, great.

[http://www.ubuntuforums.org/showthread.php?t=262012]("http://www.ubuntuforums.org/showthread.php?t=262012")  (kernel cleanup thread)

goto synaptic and then search for 'linux kernel image for version' and remove the sub-versions you don't want.

---

### Post by ermannobonifazi on 2006-09-23
Do you have some other USB sound device on you computer (like USB cam?)
Sometime happen that Ubuntu change the order of Audio device (is a bug) and as default is choosen a different audio device (like USB Cam).
to check the problem try this command (when you have working audio and when you have not working audio)

cat /proc/asound/modules

check default sound card (tagged with 0). Should be your ICH.

To avoid the problem in the future you can try

sudo gedit /etc/modprobe.d/alsa-base

and put the right index for the sound card (0 for you preferred, -2 for the rest). 
This method is not guaranteed. Same time may fail. 

(someone on the forum says this may depend to have installed more than one linux kernel at the same time, so you can try removing the unused kernel image release. I've not tested this).


To definitively avoid the problem you can (as me) blacklist the usb_audio sound module, but this wil prevent to use the Cam or other USB audio device.

---

### Post by dannyboy79 on 2006-09-25
The solution to
--------------------------------------------------------------------------------

This resolved my problem, great.

[http://www.ubuntuforums.org/showthread.php?t=262012](http://www.ubuntuforums.org/showthread.php?t=262012) (kernel cleanup thread)

goto synaptic and then search for 'linux kernel image for version' and remove the sub-versions you don't want.

DIDN'T help me at all. Still only sound from left speaker. Why can't anyone help me troubleshot this?????????

---

