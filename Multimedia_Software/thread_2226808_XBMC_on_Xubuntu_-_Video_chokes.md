---
title: "XBMC on Xubuntu - Video chokes"
date: 2014-05-29
forum: Multimedia Software
---

### Post by paul143 on 2014-05-29
Hello,

its been a very long time since I tried linux. I decided to try it on our HTPC and went for Xubuntu.
Because it's an HTPC it needs a media player and the family is used to XBMC so thats what I installed.

Everything worked fine, smooth and fast. Until i tried to play a video.. it runs smooth for 1 second then slow for another and pretty much halts after that.


[LIST]
[*]Xubuntu version installed: xubuntu-14.04-desktop-amd64.iso (via usb stick)
[*]Checked the third party driver thing during installation.
[*]Downloaded XBMC via the software center
[/LIST]
Motherboard: E-35M1-M[B]
[http://www.asus.com/Motherboards/E35M1M/](http://www.asus.com/Motherboards/E35M1M/)[/B]


Xubuntu is installed on a 60Gig SSD and the content is located on separate HDs.


UPDATE: Fixed! Fired up the system today, tried playing a video and it worked..

---

### Post by dannyboy79 on 2014-05-29
trying to figure out what GPU your motherboard has and when I click the link I get "Service Unavailable". Can you provide some info
```
lspci -v
```

```
sudo lshw -C display
```

---

