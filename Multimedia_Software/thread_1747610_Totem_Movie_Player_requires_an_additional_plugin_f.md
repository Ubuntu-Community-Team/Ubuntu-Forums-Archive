---
title: "Totem Movie Player requires an additional plugin for this operation"
date: 2011-05-02
forum: Multimedia Software
---

### Post by 55tptag on 2011-05-02
Hi,

Under Ubuntu things were easier for me; I was able to play my media files using the Totem Movie Player that were shared on my Windows 7 PC.  

Now, after a fresh install of Kubuntu 11.04 I can't play those shared files even though I installed Totem.  See attached screen shot for error.  If screen shot doesn't appear it says, "the following plugin is required: SMB protocol source".

I know this question has been around for a while and perhaps the only way to play samba shared media is by reading this post at [https://bugs.launchpad.net/ubuntu/+source/totem/+bug/119366](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/119366) or [https://answers.launchpad.net/ubuntu/+question/7857](https://answers.launchpad.net/ubuntu/+question/7857) .

KDE's Dragon doesn't work.  The VLC player on Ubuntu/Kubuntu don't work because I believe it's not compiled with --enable-smb.

So, just curious.  What do users of Kubuntu use to play multimedia files from a Microsoft Windows share?

Thanks for your thoughts.

---

### Post by Yellow Pasque on 2011-05-03
```
sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
```

---

### Post by geoaraujo on 2011-06-21
> **Temüjin said:**
> ```
sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
```
Unfortunaly that doesn't work. I have all those plugins installed and still... there are some audio and video streams that I can't play. If someone knows how to deal with this issue it would be very helpful.

---

