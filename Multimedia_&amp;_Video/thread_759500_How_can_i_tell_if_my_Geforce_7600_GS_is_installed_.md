---
title: "How can i tell if my Geforce 7600 GS is installed correctly"
date: 2008-04-19
forum: Multimedia &amp; Video
---

### Post by rideout on 2008-04-19
How do i tell if my geforce 7600 gs is installed correctly. Im new to ubuntu and already falling in love with it!
When i installed it, the restricted drivers manager came up and i clicked enable drivers. Is that the only thing I need to do? do i need to install anything from synaptic package manager? or are there any commands i need to type in the terminal? 

Any help would be greatly appreciated! Thanks guys.
Matt.

---

### Post by PmDematagoda on 2008-04-19
Clicking on "Enable" in the Restricted Drivers Manager should suffice, did you check it again to see if the driver shows up as "In Use"?

---

### Post by rideout on 2008-04-19
Yeah thats in use. So is that all i have to do to get the maximum use from my gfx card?

---

### Post by nicedude on 2008-04-19
Probably if its in use and you can set a decent screen resolution. Also you might right click on the desktop and click -> change desktop background then in the window that pops up click Visual Effects and then select extra and see if it activates OK or not. That setting is what has to be able to be enabled for you to use compiz ( "3D cube" desktop & other effects like "paint with fire" ). 

you can search the forums here as I am sure there are guides for configuring all the neat 3D effects in compiz . 

Glad to see your falling in love already just don't give up as its worth the effort.

Goodluck :-)

---

### Post by lswest on 2008-04-19
also run ```
glxgears
``` in the terminal and read the framerates outputted every few seconds, if they're in the 1000's or above, the drivers are installed.  also ```
glxinfo|grep direct
``` will tell you if direct rendering is enabled.

---

### Post by rideout on 2008-04-19
Thanks for your help guys:) Nice to see that these forums are a friendly place with no flaming. Everything is now working fine. Just trying to get Wine working now so i can mess around with Wow again!

---

### Post by nacho32 on 2008-04-19
I tried both of those commands  on my 7300 gs and got 3109 fps and yes to rendering, but my resolution wont go higher the 640x480 and max screen refresh is 56 mhz 
I upgraded to 8.04 and I no longer see the nivida boot up screen

---

