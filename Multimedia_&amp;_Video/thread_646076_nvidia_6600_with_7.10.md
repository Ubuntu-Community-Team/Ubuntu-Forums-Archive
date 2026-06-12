---
title: "nvidia 6600 with 7.10"
date: 2007-12-20
forum: Multimedia &amp; Video
---

### Post by neuman1812 on 2007-12-20
HI all, Please forgive me for posting a redundant question and for being a linux newb, but I just can't seem to get this to work. 

I have a Geforce 6600 AGP and recently installed Ubuntu 7.10 version.  I was unable to install using the regular mode, so i selected the "Safe Graphics mode"  on the install CD. and that worked fine.    Currently I can only run at 800x600  or 640x480  Those are the only two options I have.   

After reading the web and trying different things I still cannot get this right.

First thing I tried after the install, was I selected the "restricted drivers" option and installed the Nvidia driver that way.   When I rebooted the computer, my screen went..funky..almost matrix like.  So I re-installed Ubuntu (I dont know the command line that well yet to do  a repair )

Next I tried ENVY... that too: same issue.
Next I used the package manager and installed the nvidia-glx-new,  After installing that I ran << sudo dpkg-reconfigure -phigh xserver.org >>   in the terminal and selected the options for 640x480 800x600 1024x768  These are the only modes I figure my monitor can handle.   (nokia 447l)


I'm out of options.....  Can anyone assist and make sense of the web information?

---

### Post by neuman1812 on 2007-12-27
Bump and Fixed.   

I found a Solution in-case anyone reads this.

I had installed Gutsy 7.10 with a Nvidia Geforce 6600 Video card.   I was never able to get the 3d rendering to work correctly until now.

Step 1: Go to Applications - Add/Remove
Step 2: Set the SHOW option to "All available applications"
Step 3: Search for" NVidia binary X.Org driver ('new' driver)"
Step 4: After installing - reboot the system
Step 5: Install the "Restricted driver"
Step 6: reboot.
Step 7 enjoy.    !

---

### Post by adrian_pozo on 2007-12-31
Thanks dude

---

