---
title: "3d acceleration and desktop effects"
date: 2011-01-25
forum: Multimedia Software
---

### Post by Bigredjeep on 2011-01-25
I have been trying for a while to get 3d acceleration and desktop effects working and have not had any success. I have tried so many different things that I don't know if I can even post it all. So i think its time to hit the basics again or try and gather some minds to assist with this. This used to work but I got a new video card and upgraded to ubuntu 10.10 at the same time. Someone suggested that I just re-install using a 10.10 download ( to avoid issues that may have arrived when i upgraded my distro ). I really don't want to do this as I would rather fix it. Fixing it will give me a better understanding of linux and push me farther to removing windows. Where should I start first? What info would you guys like me to post?

Thanks for taking the time to help out.

---

### Post by BicyclerBoy on 2011-01-25
Post (attachment file) your /var/log/Xorg.0.log file.

This website requires  attachments have to have dos 8.3 filename extensions

---

### Post by Bigredjeep on 2011-01-26
Sorry it took me so long. I had some family stuff to take care of and didn't have any time to focus on this. Attached should be the log you asked for.

---

### Post by Bigredjeep on 2011-01-27
Anyone?

---

### Post by BicyclerBoy on 2011-01-28
The nvidia GLX module did not load properly.

Edit your /etc/X11/xorg.conf and remove the lines in modules.

extmod
glx
dbe
record

Save & restart/reboot.
Re-post the Xorg.0.log

How did you install the nvidia driver ?
jockey
synaptic
nvidia installer script ?

---

### Post by Bigredjeep on 2011-01-28
Thanks. I will try that as soon as I get home tonight. I used the nvidia installer script originally and someone else suggested another site to install from ( i don't remember the specifics on that site ). I have a feeling when i tried the install from that other site is when things went wrong.

---

### Post by Bigredjeep on 2011-01-28
I snuck home real quick on my lunch to give that a shot. no effect on the 3d. Decided i would post my xorg.conf as well as the log.

---

### Post by BicyclerBoy on 2011-01-28
Okay.
Delete your xorg.conf file 
There is nothing in there you need & the files section needs to go.

reboot
run nvidia-settings GUI utility (install if required)
config as required
save to xorg.conf file
exit nvidia-settings.

---

### Post by beew on 2011-01-28
Actually, if all you want is 3d desktop effects you don't even need the Nvidia driver. The noveau open source drivers are getting very good on that. You only need to install the package libgl1-mesa-dri-experimental from Synaptic and reboot and that's it. I just tried it yesterday, installed the package in a Ubuntu system running on an external drive, plugged it into my laptop which has a Nvidia card and rotating cube etc worked flawlessly. I have Ubuntu also installed in the laptop with the Nvidia driver, couldn't tell the difference.

But with things like vdpau you would still need the proprietary driver.

---

### Post by BicyclerBoy on 2011-01-28
Warning to the OP..
Do NOT let update manager update Xorg from 1.9 to 2.0.

This will break all the current close source drivers. Nouveau might be okay.

The OP did say 3d acceleration & may have meant video decode ..therefore nvidia.

---

### Post by Bigredjeep on 2011-01-28
> **BicyclerBoy said:**
> Warning to the OP..
Do NOT let update manager update Xorg from 1.9 to 2.0.

This will break all the current close source drivers. Nouveau might be okay.

The OP did say 3d acceleration & may have meant video decode ..therefore nvidia.

Thank you so much for you time and help. Your suggestion worked. Removed the old xorg.conf file and had the nvidia config remake it and it works like a charm now.

---

