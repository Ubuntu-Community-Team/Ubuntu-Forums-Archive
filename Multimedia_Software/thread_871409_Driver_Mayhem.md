---
title: "Driver Mayhem"
date: 2008-07-26
forum: Multimedia Software
---

### Post by FLCL on 2008-07-26
Alright, so i've had everything working perfect for a while now. Today i installed virtual box following the tutorial in the help guides. After installing i noticed an notice saying i needed to restart my system, so i did.
I cam back to my computer and was at a black screen with a gray box alerting me ubuntu was now running in low graphics mode. After a failed attempt to configure it from that box, i just continued in low graphics mode.
Upon logging in a found that i no longer have audio or video drivers.
My screen resolution is less than that of a fresh install of ubuntu; this makes no sense to me. Please help!

---

### Post by overdrank on 2008-07-26
> **FLCL said:**
> Alright, so i've had everything working perfect for a while now. But today,being sick of physically opening my case and swapping drives for xp for certain apps, i decided to install Virtualbox..bad idea i guess. 
So i installed virtualbox following the tutorial in the help guides, and after installing I decided i would wait to install xp. I noticed at the top that i had an notice that my system needed to be restarted, so i restarted, and thats when it happened. I came back to my computer and it was at a black screen with a gray box alerting me that ubuntu was now running in low graphics mode and that i would need to configure it myself. 
This failed, i found the drivers and selected them, but to no avail. So i hit ok, continued with low graphics mode, and then i found that not only is it my video, but also audio. What happened? How do i fix this? PLEASE help. :confused:

Hi and could you give us some system specs? I have seen this before on the forums and when you installed VB it must have altered your Kernel.

---

### Post by FLCL on 2008-07-26
Ubuntu Hardy 8.04
1 gig of ram
Nvidia 7600 gs
On-board sound(SoundMax i believe) 

I tried uninstalling VB and restarting but no result. Any idea?

---

### Post by overdrank on 2008-07-26
> **FLCL said:**
> Ubuntu Hardy 8.04
1 gig of ram
Nvidia 7600 gs
On-board sound(SoundMax i believe) 

I tried uninstalling VB and restarting but no result. Any idea?

Hi and yes uninstalling VB will have no effect. Do you have drivers listed under system, administration, hardware drivers?

---

### Post by FLCL on 2008-07-26
No, there are none there. Tried Envy, but it fails at installing them, says an error occured during the installation process.

---

### Post by pietjanjaap on 2008-07-27
Start up in safe mode , choose fix x server, then reinstall video driver.

I use envy, first uninstall driver, then install again. You can also use envy in textmode, see envy website.

---

### Post by FLCL on 2008-07-27
OMG THANK YOU, that fixed my video problem and it is working perfect now. The only problem i have left is the audio is still not working.

This is the icon it shows me:
[IMG]http://imagedash.com/images/opt1217140116i.png[/IMG]

And this is the message i receive upon trying to open volume control:
[IMG]http://imagedash.com/images/arx1217140254z.png[/IMG]

---

