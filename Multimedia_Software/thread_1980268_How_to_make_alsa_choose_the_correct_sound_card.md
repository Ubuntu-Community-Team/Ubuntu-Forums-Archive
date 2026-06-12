---
title: "How to make alsa choose the correct sound card"
date: 2012-05-14
forum: Multimedia Software
---

### Post by Herpythebrony on 2012-05-14
A new problem that some had with the new release of Lubuntu 12.04 (myself included). Well here is an easy fix.

 Go to the terminal and check to see which sound device it picked up

     Code:
     alsamixer 
In my case it picked up my usb mic and my eyetoy webcam as default

now to find out the name of the device go to the terminal and type in

     Code:
     less /proc/asound/modules 
In my case it was named snd_usb_audio

now become a super user with this command

     Code:
     sudo su 
now type in

     Code:
     nano /etc/modprobe.d/sound 
It should bring you to a terminal text editor now in this text editor type in

     Code:
     options name_of_offending_device index=1 
So in my case it's

     Code:
     options snd_usb_audio index=1 
Reboot and it should load the correct sound device!

Herpythebrony~

---

### Post by Yellow Pasque on 2012-05-15
All file names in /etc/modprobe.d should end in .conf
Actually, usb devices should not grab index 0 because of the configuration in /etc/modprobe.d/alsa-base.conf

Also, rebooting is unnecessary, Just:
```
sudo depmod -a
sudo alsa force-reload
```

---

### Post by Herpythebrony on 2012-05-15
> **Temüjin said:**
> All file names in /etc/modprobe.d should end in .conf
Actually, usb devices should not grab index 0 because of the configuration in /etc/modprobe.d/alsa-base.conf

Also, rebooting is unnecessary, Just:
```
sudo depmod -a
sudo alsa force-reload
```
I see, well I had that problem but then again I grabbed the iso on release day, thanks for the info, the way I did was the way I used to do it on slack based distros like Vector Linux.

---

