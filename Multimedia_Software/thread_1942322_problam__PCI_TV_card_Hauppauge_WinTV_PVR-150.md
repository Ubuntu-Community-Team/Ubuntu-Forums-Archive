---
title: "problam  PCI TV card Hauppauge WinTV PVR-150"
date: 2012-03-17
forum: Multimedia Software
---

### Post by offir on 2012-03-17
I have a PCI TV card Hauppauge WinTV PVR-150
"iTVC16 (CX23416) MPEG-2 Encoder"
And Ubuntu 10.04


I want to use the card video and audio inputs
I have been trying for several hours
I removed and installed a full drivers
But it does not work

I tried to using the software vlc
The option of video capture device
Nothing happens
It just does not work

The system detects the card
And even registered the name
But at the name appears a question mark



I use the Device Manager "gnome-device-manager 0.2"
To see this

---

### Post by wyliecoyoteuk on 2012-03-17
Is that a Digital TV card?
If so it will not appear as /dev/video0, but as /dev/dvb/adapter0/dvr0

---

### Post by offir on 2012-03-17
It's an analog card
Our analog broadcasting is dead
This card also has entries of audio and video
Where I want to use
Connect a video signal to S-VIDEO connection OR RCA


Another question might be related
Why in Device Manager
Some devices on the computer appear with a question mark

---

### Post by Autodave on 2012-03-17
[QUOTE=offir;11772809]I have a PCI TV card Hauppauge WinTV PVR-150
"iTVC16 (CX23416) MPEG-2 Encoder"
And Ubuntu 10.04


I hope someone has an answer for you.  I went to the search function for the identical thing you are looking for and I have the same problem: everything you typed is identical on my end!

---

### Post by wyliecoyoteuk on 2012-03-17
try the following in a terminal:

ls /dev | grep video*

the devices should be /dev/video0, unless you have anothe v4l device.
The device name /dev/video0 for example is the name you need to enter in the video capture device entry in VLC

---

### Post by wyliecoyoteuk on 2012-03-17
Are you running the device manager as root?
the questin marks may be because it does not have read permissions on those devices.

---

### Post by Autodave on 2012-03-17
> **wyliecoyoteuk said:**
> try the following in a terminal:

ls /dev | grep video*

the devices should be /dev/video0, unless you have anothe v4l device.
The device name /dev/video0 for example is the name you need to enter in the video capture device entry in VLC


I get this:
video1
video2
video25
video33

---

### Post by offir on 2012-03-17
I got this message

video0
video24
video32

[http://marksnotebook.com/PVR-150_capture](http://marksnotebook.com/PVR-150_capture)
I got here
I wrote down what was on line 5
[PHP]v4l2-ctl -i 2[/PHP]
and it work
For some reason the first time I got a message that there is no video device

---

### Post by wyliecoyoteuk on 2012-03-18
If you want to identify the video device, cut and paste this code into a terminal.

```
sudo udevadm info -a -p $(udevadm info -q path -n /dev/video*) | grep ATTR{name}
```

---

### Post by offir on 2012-03-18
This is what I received

"ivtv0 encoder MPG"

This problem solved




How do I run the device manager as root ?

---

### Post by Autodave on 2012-03-18
> **wyliecoyoteuk said:**
> If you want to identify the video device, cut and paste this code into a terminal.

```
sudo udevadm info -a -p $(udevadm info -q path -n /dev/video*) | grep ATTR{name}
```


When I run that in a terminal, I am getting my web cam and that's all.  How do I find my PVR-150?

---

