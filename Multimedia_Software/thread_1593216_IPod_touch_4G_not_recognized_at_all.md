---
title: "IPod touch 4G not recognized at all"
date: 2010-10-11
forum: Multimedia Software
---

### Post by Jeffouille on 2010-10-11
Hello all,

I do not manage to get my my ipod touch 4g recognized by ubuntu 10.04.  First time I tried, it was recognized as a camera and not as a media  player. I tried to install a few other packages. Now it is not  recognized at all....
I followed guidelines on the forum and installed libimobiledevice,  ifuse, usbmuxd and libplist. Note I unlock my ipod before connecting it.

Here is what I get with ideviceinfo

jean-francois@Sony:~$ ideviceinfo
usbmuxd_get_device_list: error opening socket!
No device found, is it plugged in?

I see a lot of post related to new ipod touch 4g installation but I think I screwed up somewhere in my configuration since the ipod is not recognized at all

Your help would be greatly appreciated....

---

### Post by conorsulli on 2011-02-23
Seems to be a new version of libimobiledevice called libimobiledevice2 instead of libimobiledevice1 in natty can anybody confirm if their ipod is working with this package maybe or even the libimobiledevice1? with the development build of Ubuntu Natty Narwhal 11.04?

[http://packages.debian.org/experimental/libimobiledevice2](http://packages.debian.org/experimental/libimobiledevice2)

I might give this a try later on and just upgrade my system altogether ;-)

Wish me Luuccckkk!

---

### Post by dirt912 on 2011-02-25
I'm having the same issue except I have an ipod 3G that was updated to the new ios a couple months ago.  I plug it in and nothing happens.  Not even a desktop image.

---

### Post by conorsulli on 2011-02-26
installed some stuff from upstream and could not get it to work well, however i probably did it totally wrong too

---

### Post by NJPinator on 2011-02-26
The iPod Touch's previous models are recognised as media players, as their filesystem was identical to other iPods such as the Nano and Classic. In those models and previous iPod Touch generations, the media/music was in a hidden folder. The recognition of all iPhones and the 4th generation iPod Touch as a camera is due to the fact that they are cameras and so filesystem being encrypted, such that only the DCIM folder is available for the system to read --  It's like a **virtual partition**.

The only way you can get access to your device's other media, such as its music, is to connect it and open a media manager (such as Rhythmbox) and NOT a regular file manager (such as Nautilus).

If your device is "jailbroken", you can download OpenSSH from the Cydia application via your iPod Touch and then SSH into your device via the "Connect to Server" feature under the "Places" menu in the top panel of your Ubuntu machine. This will give you root access to your Apple filesystem, allowing you to browse and modify all contents of your iPod as you wish.

P.S. If you are not sure what it means to be "jailbroken", you probably aren't. If you're just not sure, check if you have either the "Installer" or "Cydia" app on your iPod's home screen. If you are, there are a ton of tutorials on [YouTube]("http://www.youtube.com/") on how to SSH into your iPod.

If you're confused in any way by these instructions, I'll be happy to help!

Also, I DO NOT RECOMMEND installing extra packages...they've never worked for me and haven't seemed to be beneficial to others -- including you! -- but it's your choice after all.

---

