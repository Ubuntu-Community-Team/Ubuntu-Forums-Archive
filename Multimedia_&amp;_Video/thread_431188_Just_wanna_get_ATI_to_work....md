---
title: "Just wanna get ATI to work..."
date: 2007-05-02
forum: Multimedia &amp; Video
---

### Post by FlyingIsFun1217 on 2007-05-02
Hey!

I have a desktop computer using a NVidia 6150 LE card, and with the nvidia driver, it works perfectly. Absolutely wonderful. As good, if not better, than windows.

Now I am having trouble getting my ATI Radeon Mobility M6 LY to work as well. Testing an OpenGL program I built on windows gives a frame rate of approximately 65-70 fps. On Ubuntu, about 6-15.

First off, how do I find the driver I am currently using?
Second off, who knows what should give me better performance (which driver is the best?)? I have no preference to it being open or free.

Thanks for any help!
FlyingIsFun1217

---

### Post by RandySavage on 2007-05-03
Any of the various system administration tools, like info center, will tell you what driver you're running.  

If you aren't running proprietary drivers then likely you're running Vesa or x.org drivers.  The proprietary drivers (non-open source) are definitely quicker and offer more capability than the open source drivers.

If you think computers and politics don't mix, then run the proprietary drivers.  There's a utility in Ubuntu called "Restricted Manager."  I don't know if it comes with the base setup or if you have to add it to a base installation.  I'm running Kubuntu and I had to add it.

Simply go into that, click on whatever to agree that binary data processing equipment and political snobs make poor bed-fellows, and it'll let you go pick the proprietary driver for your ATI that will already be included.  You have several choices, but I chose flgrx.  Dunno if its the best, but it works for me.

---

### Post by FlyingIsFun1217 on 2007-05-03
> **RandySavage said:**
> 
Simply go into that, click on whatever to agree that binary data processing equipment and political snobs make poor bed-fellows, and it'll let you go pick the proprietary driver for your ATI that will already be included.  You have several choices, but I chose flgrx.  Dunno if its the best, but it works for me.

Yep, I have that. Actually one of the bigger reasons that I upgraded to feisty.

Thing is, all it shows is the following:

[IMG]http://i71.photobucket.com/albums/i127/FlyingIsFun1217/RDM.png[/IMG]

So... why is there nothing to install further restricted drivers?

Thanks again!
FlyingIsFun1217

---

