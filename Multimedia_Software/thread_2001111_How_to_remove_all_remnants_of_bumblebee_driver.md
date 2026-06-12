---
title: "How to remove all remnants of bumblebee driver?"
date: 2012-06-10
forum: Multimedia Software
---

### Post by MiD-AwE on 2012-06-10
Please help if you can.

I recently ugraded my graphics card to nvidia GTX550ti and after some searching I found information for getting it working with dual displays at full resolution. I ran blender and found that I had no cuda support, so I kept looking and someone suggested installing bumblebee driver with a line of code to enter after install that was "suggested by the developer". After I did this everything broke and I only get one display and my graphics card is no longer recognized. I check the additional drivers and I get a message that the drivers are installed but are not being used. I've tried to uninstall everything nvidia related and start over but I still see bumblebee appearing but it's not installed in synaptic. I can't seem to find the original post that I followed and I can't get this corrected. How do I remove everything and fix this. I can live without cuda even though It is the reason that I upgraded my card from GTX260 to the GTX560ti.

I'm exasperated having worked all night on this. Please, help if you can. (I'll be back in a bit, as I'm going to try my install live CD again for good measure.)

Desperate for a fix. Some brilliant person must have an answer please.

---

### Post by MiD-AwE on 2012-06-10
I found this and I am trying it now.

[http://sn0v.wordpress.com/2012/05/11/installing-cuda-on-ubuntu-12-04/](http://sn0v.wordpress.com/2012/05/11/installing-cuda-on-ubuntu-12-04/)

BTW: the Live CD will not load.

---

### Post by MiD-AwE on 2012-06-10
Ok, the instructions at the above link seem to be working but I still do not have dual displays.

I have opened NVIDIA X Server Settings and in X Server Display Configuration I have enabled both displays. Both displays are 1920x1080. The second display is still off even after clicking apply. Should I be setting them to TwinView or Separate X screen?

Please help.I'm giving it my best.

---

### Post by gordintoronto on 2012-06-10
I don't know if this will help you:
Add this in Software Sources: ppa:ubuntu-x-swat/x-updates
Now you can install a later version of the video driver, which works for most systems.

---

### Post by MiD-AwE on 2012-06-11
Thank you. The link that I posted helped to clean everything up, then I installed the CUDA 4.1 drivers. I know that CUDA 5 will be available soon but I had no luck getting any other than 4.1 installed and working. All is working well now. :guitar:

---

### Post by firekage on 2012-08-25
> **MiD-AwE said:**
> Thank you. The link that I posted helped to clean everything up, then I installed the CUDA 4.1 drivers. I know that CUDA 5 will be available soon but I had no luck getting any other than 4.1 installed and working. All is working well now. :guitar:

Could you tell me how did you install cuda drivers? Can you write know-how?

Thanks.

---

### Post by MiD-AwE on 2012-08-25
> **firekage said:**
> Could you tell me how did you install cuda drivers? Can you write know-how?

Thanks.

[The easiest information that I found.]("http://sn0v.wordpress.com/2012/05/11/installing-cuda-on-ubuntu-12-04/") ):P

---

### Post by firekage on 2012-08-25
> **MiD-AwE said:**
> [The easiest information that I found.]("http://sn0v.wordpress.com/2012/05/11/installing-cuda-on-ubuntu-12-04/") ):P

Thank you, i have to missed it, it's linked few post above, my mistake ;)

---

### Post by MiD-AwE on 2012-08-26
No problem, I'm glad I could help.

BTW - Every time you update your Kernel you'll have to redo step one. It'll take very little time and it keeps everything working. Occasionally, you have to use the fail-safe video display mode just to be able to redo step mode but that's easy also if you are using grub. 

I run GNOME 3 so I know when to redo step one whenever I get the old GNOME at launch instead of GNOME 3. That just means that 3D is not working and a few minutes later I have it back after doing step one again.

---

