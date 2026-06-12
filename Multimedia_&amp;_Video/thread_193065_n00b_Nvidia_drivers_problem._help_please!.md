---
title: "n00b Nvidia drivers problem. help please!"
date: 2006-06-09
forum: Multimedia &amp; Video
---

### Post by AlexBryan on 2006-06-09
Hi I have a Nvidia 6600GT and I'm trying to install the drivers. I'm following this HOWTO guide:
[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29)

I've followed the instructions carefully, at the point where it tells me to install "linux-restricted-modules" in Synaptic Package Manager it gives this as the example "linux-restricted-modules-amd64-k8". I installed the Intel x86 desktop version of Ubuntu (I have a pentium 4 processor) but I'm not sure what the equivilent to "linux-restricted-modules-amd64-k8" is for my kernal. On the list was "linux-restricted-modules-2.6.15-23-386" was is already installed and "linux-restricted-modules-386" which was also already installed, but in order to follow the guide completely I chose to reinstall the latter which sounded more like the example. I followed the guide up to the point where I type this into the terminal: "sudo nvidia-glx-config enable"
And I got this response

"Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia."

So I guess it didn't install properly. What Am I doing wrong? I also downloaded the nvidia drivers for linux from their website, I chose the Linux IA32 version because I guessed that Linux IA64 was 64-bit processors. Are they any use or am I installing the same drivers in doing the above?

Linux is very, very confusing for a n00b but it's also alot of fun!

---

### Post by tseliot on 2006-06-09
Please, try this guide of mine (see Method 2) or just use my script (which will install the driver for you):
[http://ubuntuforums.org/showthread.php?t=139264]("http://ubuntuforums.org/showthread.php?t=139264")

---

### Post by AlexBryan on 2006-06-09
Hi, thanks for the reply!

I have a wireless network card on my computer which worked out of the box with the default rt2500 drivers. On your guide it says don't use it if you have a wireless card because it deletes the restricted modules, are all wireless cards controlled by the restricted modules or will it be OK?

---

### Post by AlexBryan on 2006-06-09
tseliot, I went ahead and used your script. Brilliant! Thanks so much, worked perfectly!
Thanks again!

---

