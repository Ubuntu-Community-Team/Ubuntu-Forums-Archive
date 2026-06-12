---
title: "DVICO Dual Digital 2 IR remote not working"
date: 2008-06-10
forum: Mythbuntu
---

### Post by lpnb on 2008-06-10
Hi, this is my first post since installing the latest (8.04?) version of mythbuntu  it is now working quite well apart from a strange horizontal split of the video at the top of the screen when there is a lot of motion in the image. you might say it looks "flickery" - very watchable but I am a perfectionist it it is just not good enough. - it does not matter if it is HD/SD/DVD/divx.......some problem. tried with and without XvMC with no change....is it just an Nvidia thing? I have seen it before on 3 other cards but I can't seem to find any reference to it on the web.

Though this post is relating to my frustration with the remote of the DVICO card.

Basically irrecord can't see it at all and dmesg | grep IR-Receiver gets this:

--------------------------------

root@mythbox:/dev/input# dmesg |grep IR-receiver 
[       31.739860] input:  IR-receiver inside and USB DVB receiver as /devices/pci0000:00/0000:00:08.0/0000:01:08.2/usb3/3-1/input/input9
[       32.175195] input:  IR-receiver inside and USB DVB receiver as /devices/pci0000:00/0000:00:08.0/0000:01:08.2/usb3/3-1/input/input10
root@mythbox:/dev/input#

------------------------

root@mythbox:/dev/input# lircd -v
lircd 0.8.3pre1
root@mythbox:/dev/input# 

------------------------

If I cat any of the /dev/input/xxxxx's I dont' get any response from the remote.

But I think any of you experts who see the above dmesg messages will know exactly what the problem is ;-)

can anyone please help me??

BTW, mythbuntu in general is a fantastic experience and the contributors have ended up with a system they can be proud of!

Oh yeah my system has:
Biostar NF560 A2G+ with AMD 5000+, 2GB 
Nvidia 6600 GT PCIe

---

### Post by lpnb on 2008-06-16
Please Please please, anyone??? my partner is getting very annoyed with the keyboard on the coffee table and is starting to get very disenchanted with the whole thing!

---

