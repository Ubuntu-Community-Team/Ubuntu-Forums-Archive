---
title: "Wireless networking stops working when installing nvidia-glx"
date: 2006-01-08
forum: Multimedia &amp; Video
---

### Post by jbjoerk on 2006-01-08
I have a Nvidia Ti-4600 card in a Athlon based box that connects to the local lan using an acx111 based wifi card. It runs Kubuntu breezy.
 
The nv drivers work just fine but when installing the nvidia drivers to get tv-out working (properly) the wifi card loses connection. disabling the drivers and rebooting gets the network back up and running again. This happens with both ndiswrapper and native drivers and the generic 386 kernel and the k7 kernel.
 
Just copying the old xorg.conf file back in place and restarting X does not work. I have to run the nvidia-glx-config tool and reboot.
 
I'm thinking that the nvidia drivers grab resources from the wifi card but I have no idea on how to proceed. Are there plans to backport the new nvidia drivers? Anywhere I can look for more information? My google-fu is failing me on this subject.

---

### Post by darkpark on 2006-01-08
have you treid using a different version of the nvidia-glx drivers?

---

