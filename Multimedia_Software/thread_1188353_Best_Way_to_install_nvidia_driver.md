---
title: "Best Way to install nvidia driver?"
date: 2009-06-15
forum: Multimedia Software
---

### Post by keypox on 2009-06-15
Is it best to just let ubutnu install it via hardware drivers? Or should I use the newer 185 from nvidia website?  

I actually tried both methods but the second method didnt go to well...

---

### Post by lukeiamyourfather on 2009-06-15
I'd just use the Ubuntu supplied drivers since they already have all the dirty work done for you. If you choose to download the nVidia drivers then you'll also have to download the kernel packages and developer tools to compile a new kernel to work with the nVidia drivers. Cheers!

---

### Post by keypox on 2009-06-15
> **lukeiamyourfather said:**
> I'd just use the Ubuntu supplied drivers since they already have all the dirty work done for you. If you choose to download the nVidia drivers then you'll also have to download the kernel packages and developer tools to compile a new kernel to work with the nVidia drivers. Cheers!

Any extra settings you use? I still have tearing in videos.  AHHH... i just got rid of ATI 4870 for this reason.

Nevermind restarted VLC using xvideo.  And all seems good, at least on one monitor, seems like you can vsync to only one monitor... interesting.

---

### Post by kg87 on 2009-06-15
ENVY - [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Was pretty straight forward, and gives you the option to update from there aswell.

---

### Post by Arup on 2009-06-15
185 will get you more performance, better vdpau compatibility, the 180.44 which is in the Ubuntu repos has regression issues with vdpau. In case you do wish to install from 185, make sure your exisiting drivers are removed totally, go to synaptic and remove linux restricted modules and linux restricted modules common by marking total unisntall. Then do a sudo apt-get install build-essential and afte that, do a ctrl+alt+F1 and login to tty and do a sudo /etc/init.d/gdm stop 

Make sure your nvidia driver is in HOME folder and nowhere else.

Do a sudo .sh NVIDIA and hit tab

Say yes to everything including .32 compatibility and then do a sudo reboot.

---

### Post by keypox on 2009-06-16
> **Arup said:**
> 185 will get you more performance, better vdpau compatibility, the 180.44 which is in the Ubuntu repos has regression issues with vdpau. In case you do wish to install from 185, make sure your exisiting drivers are removed totally, go to synaptic and remove linux restricted modules and linux restricted modules common by marking total unisntall. Then do a sudo apt-get install build-essential and afte that, do a ctrl+alt+F1 and login to tty and do a sudo /etc/init.d/gdm stop 

Make sure your nvidia driver is in HOME folder and nowhere else.

Do a sudo .sh NVIDIA and hit tab

Say yes to everything including .32 compatibility and then do a sudo reboot.

Ok thanks I think i will try this.  Can you tell me how to uninstall if I want to go back? To the restricted?

---

### Post by keypox on 2009-06-16
> **kg87 said:**
> ENVY - [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Was pretty straight forward, and gives you the option to update from there aswell.

envy installs the old drivers though?

---

### Post by keypox on 2009-06-16
thanks i have the newest drivers installed again... can't tell a difference though lol

Any recommendations on settings in nvidia x server settings?

---

### Post by Shibblet on 2009-06-16
The best way I've done it is, save the NVIDIA driver on your desktop.

Press Ctrl+Alt+F3
Put in your name and password.

type: sudo /etc/init.d/gdm stop
then: cd Desktop
then: sudo sh NVIDIA*

Answer Yes to everything Nvidia driver installation asks.

after it's installed
type: sudo /etc/init.d/gdm start

You're done.

---

### Post by izizzle on 2009-06-16
I'd just use the ones provided in restricted drivers. 

Short. Fast. Easy.

---

### Post by gzenitsky on 2009-06-16
What is the process Ubuntu follows to add new drivers to the repository? Will we see 185 as an update or do we have to wait for the next full release (9.10?)? Thank you!

---

### Post by Arup on 2009-06-16
If you want it in the repos, you have to add it via ppa. Some good places to get them is [http://www.avenard.org/media/Home.html](http://www.avenard.org/media/Home.html) or [https://launchpad.net/~brandonsnider/+archive/ppa](https://launchpad.net/~brandonsnider/+archive/ppa) but best way to keep the latest is to download and install it from nvidia.

---

### Post by izizzle on 2009-06-16
Iv'e had nasty expieriences with instlling the drivers manually, mostly because they override some of th 32-bit libs on my 64-bit system which caused some incompability issues...

So, I just use the restricted hardware drivers.

---

