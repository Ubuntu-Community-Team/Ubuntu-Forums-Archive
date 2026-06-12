---
title: "Kino not detecting Camera Sony TRV22E"
date: 2008-04-02
forum: Multimedia &amp; Video
---

### Post by jiteshsamani on 2008-04-02
Hi,

I am running Gutsy Gibbon. Have recently installed a VIA 1394 fireward card. Kino for some reason will not detect my Sony Camcorder though the connection is OK as the camera flashes the "DV IN" message. I've added the libpt-plugins-avc - still no joy. Please help as I am not a Linux expert.

Any ideas would be much appreciated.

Thx
Jitesh

---

### Post by xc3RnbFO8P on 2008-04-02
Is there problem in Kino Preferences>  ieee 1394, do get "subsystem not responding"

---

### Post by granny6989 on 2008-04-03
Try looking at this:

[http://ubuntuforums.org/showthread.php?t=645826](http://ubuntuforums.org/showthread.php?t=645826)

I tried like hell to get my Sony to show up under Kino but nothing worked. Looked into the mentioned post, typed in the code at terminal, and once I exited I had full control and capture using a PCI Firewire card. Good Luck.

S*

---

### Post by xc3RnbFO8P on 2008-04-04
Hardware Compatibility List:
[http://www.linux1394.org/hcl.php?class_id=3]("http://www.linux1394.org/hcl.php?class_id=3")

Be sure you got this installed in Synaptic Package Manager:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=64889&stc=1&d=1207289742[/IMG]
> sudo gedit /etc/modules

Add this four lines in to the bottom of the page:
> raw1394
video1394
ohci1394
dv1394
**Save**

Load the modules:
> sudo modprobe dv1394
sudo modprobe video1394
sudo modprobe raw1394
sudo modprobe ohci1394

Getting read and write access:
> sudo chmod a+rw /dev/*1394 

---

