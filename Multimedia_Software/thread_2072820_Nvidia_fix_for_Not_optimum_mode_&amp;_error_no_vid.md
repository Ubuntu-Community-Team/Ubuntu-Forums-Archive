---
title: "Nvidia fix for Not optimum mode &amp; error no video mode activated"
date: 2012-10-18
forum: Multimedia Software
---

### Post by dwb814 on 2012-10-18
Hi,
Here's a list of what I tired so you know what I did:
Installed the driver from the hardware additional drivers, update manager added another driver this hosed the video completely. I formated, re-installed and  tried 

```
sudo sed -i -e 's/#GRUB_TERMINAL/GRUB_TERMINAL/g' /etc/default/grub
```for text mode which gave me a clue on what the problem was.
Read and tried the fixes on [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/699802](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/699802) 
Tried  in grub **NOMODESET. **Lastly I tried Commented #Grub_Hidden_Timeout

After all that, I finally got it! I've been beating this thing to death, with searching and experimenting. But here's the answer. If you have a Nvidia video card (mine is a Nvidia GeForce 7025 / nForce 630a). 
I kept getting Not optimum mode : Recommended mode 1280X1024 /60. 
When I commented out grub so I could see the boot sequence I founderror: no video mode activated.
So when in grub I noticed GRUB_GFXMODE= commented out, so I uncommented it and added the correct video specs of 1280X1024 to it. Saved it and rebooted and low and behold it works.

Here's the break down:
Open the terminal and paste this in:  ```
gksudo gedit /etc/default/grub
``` hit enter, enter your password, and about 10 lines up from the bottom you'll see
 # GRUB_GFXMODE=640X480.
You need to edit two parts, first remove the # from the line, then change the 640X480  to the video card specs, example: mine is 1280X1024.
Save the file and run ```
sudo update-grub
``` and reboot. Both errors went away after I did this. I hope it works for you as well.

---

