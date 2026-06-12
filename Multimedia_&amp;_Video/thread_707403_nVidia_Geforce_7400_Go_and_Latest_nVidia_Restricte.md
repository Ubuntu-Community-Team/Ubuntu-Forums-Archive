---
title: "nVidia Geforce 7400 Go and Latest nVidia Restricted Drivers"
date: 2008-02-25
forum: Multimedia &amp; Video
---

### Post by JCoster on 2008-02-25
Hi.

I'm trying to install the latest nVidia drivers (169) on a fresh install of Ubuntu 7.10 with an nVidia Geforce 7400 Go card on a Sony Vaio VGN-SZ4XWN.

I have followed the installation walkthrough on the nvidia site yet I just can't seem to get the nvidia restricted driver working.

If I select to enable it from Restricted Drivers Manager then it asks me to reboot.  When I reboot, Ubuntu boots into safe-graphics mode.

If I go to Screens and Settings in this safe-graphics mode then I cannot select nvidia- just nv or VESA, whereas after enabling the driver and before rebooting I can select nvidia.

Sorry if this doesn't make much sense.

Thanks.

---

### Post by Sam Lars on 2008-02-25
Sounds similar to this...
[http://ubuntuforums.org/showthread.php?t=707178](http://ubuntuforums.org/showthread.php?t=707178)

What do you get to with the Nvidia driver?

---

### Post by JCoster on 2008-02-26
Yeahh that sounds pretty similar.

I don't understand the last sentence; 'what do you get to with the nvidia driver'.

If you meant 'where do you get to with the nvidia driver?' then my answer is that I can install it (it informs me of no kernel so it creates a module for it or something and then it installs and then if I run nvidia-xconfig whilst still in command line it outputs about 20 lines of errors. 

If you meant, 'what do you get to do with the nvidia driver?' then it basically just lets me use the visual effects and at the moment my laptop seems abnormally slow and jerky which may or may not be due to this, but the nvidia 100 driver used to work fine on here on my old install and it seemed relatively fast **and** let me run visual effects.

Thanks.

---

### Post by Sam Lars on 2008-02-26
Sorry I wasn't clearer... yes, that answered my question.  What are the errors you get from nvidia-xconfig?

---

### Post by JCoster on 2008-02-26
It was something about a Kernel mismatch?

---

### Post by Sam Lars on 2008-02-26
Are you using the Ubuntu kernel?  If you are, it should be fine... if not, then I'm not sure...
Does the xorg.conf say that it's using the driver "nvidia"?
What do you get from
```
cat /var/log/Xorg.0.log | grep EE
```
after it puts you into safe graphics?

---

### Post by JCoster on 2008-02-26
Right well I've got it fixed.

I installed all High Priority and Recommended updates, did a system reboot, installed Envy, uninstalled the nVidia driver through Envy and then installed the latest nVidia driver with Envy and that seemed to do the trick.

I'm not sure what Envy did differently to me (although I did let it auto-config the xorg.conf file) but it seemed to do the trick.

Thanks for all your help.

---

