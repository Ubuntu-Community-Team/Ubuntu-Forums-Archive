---
title: "Install NVIDIA GeForce4 MX4000"
date: 2007-06-03
forum: Multimedia &amp; Video
---

### Post by drietow on 2007-06-03
I'm new at this.
This is an attempt to upgrade from my on board i810 controller to a PCI with 128MB.
I cannot get my PCI card to work.  When I boot my message "Fatal Server Error", "No Screen Found", "X10 Fatal IO error 104".  I did the command "lspci" to get the BUSid of the NVIDIA card.  
I installed the "NVIDIA-glx-new" file using the i810 controller.  I rebooted using my NVIDIA card and when it failed and ran the command "sudo nvidia-gls-config enable" and then tried to start xserver.  That failed.  I then looked up the BUSid using the command "lspci".  The ID was "01:0a.0".  I ran the command "sudo dpkg-reconfigure xserver-xorg".  Now I'm confused because I don't know how to correctly enter the BUSid.

My test machine is a COMPAQ 5003us PIII, 512MB.

---

### Post by drew_t on 2007-06-03
I believe you need to use the Legacy driver for that card.

---

### Post by Titus A Duxass on 2007-06-03
Try a sudo apt-get install nvidia-glx-legacy followed with a sudo dpkg-reconfigure xserver-xorg

That should get you up and running.

---

### Post by drietow on 2007-06-03
The answer to all my problems was a program called ENVY.  It automaticly loaded all my drivers correctly. I'm now up and running.  See link to Envy Home Page.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by ElijahLynn on 2008-06-21
> **drietow said:**
> The answer to all my problems was a program called ENVY.  It automaticly loaded all my drivers correctly. I'm now up and running.  See link to Envy Home Page.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Thanks, I am going to use this to upgrade my video card tonight.
Going from a GeForce2 MX400 to a MX4000.

---

### Post by blackbird020377 on 2008-07-17
hello... i have a nvidia geforce4 mx 4000 and this is what i have done for it to work.

1. remove all previous nvidia driver, nvidia settings and nvidia-xconfig
2. restart your pc
3. set temporary setting for your screen/display
4. install nvidia-glx
5. run nvidia-xconfig on terminal
6. install nvidia-settings
7. restart your pc
6. viola! your nvidia geforce4 mx4000 is now working

---

