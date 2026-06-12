---
title: "Nvidia FX5500 problem"
date: 2008-03-05
forum: Multimedia &amp; Video
---

### Post by Donnut on 2008-03-05
I have searched the threads to no avail for this problem, I have a 5500 PCI, and even though the OpenGL works, I have no 3D acceleration.  After I put it in my desktop, the OS installed a GeForce 4 generic driver, and I don't know how to changeit.  I have already tried the driver from their website...  Also, Envy will not work with ubuntu apparently.  Can anyone help?

---

### Post by sanddgroper on 2008-03-06
Hi
Well I can only suggest installing the drivers through synaptic.
For that you need to go to synaptic->settings->ubuntu software and
select the proprietary  drivers for devices (restricted)infact you could
probably check all the boxes in that section.
Then you need to select reload in synaptic then check for the package
nvidia glx and install it.

Cheers
 Sandy

---

### Post by Donnut on 2008-03-06
well, that just broke the installation of the drivers altogether.  Are there any walkthroughs on installation of the Nvidia Drivers?  And how do I cose Xserver without it just starting up again?

---

### Post by myoozeman on 2008-03-06
probably will sound dumb but have you tried using automatix? worked like a charm for me.

---

### Post by sanddgroper on 2008-03-06
Hi
Have you had a look at the stickies at the top of this forum.
Did you change your xorg.conf file in /etc/X11 in the device
section.
you could also have a look at these files in /var/log
dmesg
messages
syslog
To see if it showes up any errors to do with graphics

Cheers
Sandy

---

### Post by Donnut on 2008-03-09
I installed Automatix, but it doesn't have the option of installing my video card...
Is it because it is automatix 2?

---

