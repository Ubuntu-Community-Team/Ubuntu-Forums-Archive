---
title: "Is it hardware or software?"
date: 2012-10-07
forum: Multimedia Software
---

### Post by Desert Sailor on 2012-10-07
I have a new (to me) laptop.  I have cleaned and wiped the windows, and I am up and running on Ubuntu 12.4. 

Everything is working ok, with the exception of my ability to play videos.  I have followed the instructions in the "sticky" and most of them are working OK.  Some videos refuse to play however and either are blank (thumb doesn't even show), or just hang when I click on the play button.  

My laptop is an HP-Pavillion DVD-7.  500-Gig Hard Drive, 4-gig memory, graphics processor is VESA:RS780, running on an AMD Turion X2, Mobile RM-72.  I am running the 32-bit Ubuntu. 

Can you tell from my specifications, if the problem is the hardware, or if I need to keep pounding away on the codecs and 'add-ons'???

---

### Post by inobe on 2012-10-07
If you did 

```
lspci | grep VGA
```

in terminal, you should get vga hardware listed.

Example:

```
01:00.0 VGA compatible controller: NVIDIA Corporation GF104 [GeForce GTX 460] (rev a1) 
```

These applications require gpu hardware acceleration.

Your model should sport an ati 3200 gpu, you have to be certain, I would do much research before activating the ati proprietary video driver.

These drivers may not be stable from AMD, at the moment your system may be using Opensource ati drivers which are very good.

However researching may save you trouble.

So, yes, it's software/ drivers.

Here is how to install the proprietary driver.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Stick with the recommended way!

---

### Post by myromance123 on 2012-10-08
Before trying to install the Proprietary drivers manually, please check Jockey (a.k.a Additional Drivers). This tool will help you install the proper Proprietary Driver automatically, if one is available.

In your Ubuntu dash, type jockey. Additional Drivers should appear. Click on that.

Once it has opened up, do you see any ATI/AMD lines that end with "driver"?
If you do, then highlight the recommended one and install that. This should hopefully rectify any problems related to playing high quality or HD videos. You will need to restart after having installed the driver for it to take effect.

Lets say its not a driver problem in the end however, can you list the software you've used to try and watch these video files?
When all else fails for me, I will usually revert to using VLC. VLC is readily available in the Ubuntu Software Center for you to install. It is free.

---

### Post by GeForce 9500GT on 2012-10-08
> **Desert Sailor said:**
>  Some videos refuse to play however and either are blank (thumb doesn't even show), or just hang when I click on the play button.
 
Did those movies played under Windows? Before we jump to some conclusions that it is hardware related, tell us if those movies played good under Windows.

---

### Post by Desert Sailor on 2012-10-08
Windows?  I've heard about that, I think it's some kind of wanna-be computer operating system or something like that.  Sorry, I can't answer your question, I don't use Windows, don't have it on my laptop, and frankly consider it a virus. ;)

I did take a look at the lspci | grep VGA and it was the ati 3200 gpu. Which got me thinking maybe it was a driver issue.  So I dumped the ATI proprietary driver in favor of the generic open source driver, but that didn't change anything.  

I am a little embarrassed to discuss this, but the main failing is when I visit Xtube.  The normal xtube videos play just fine, but at the bottom of the list there are some thumbnails with links to "our friends" which seem to be other sites.  THESE are the thumbnails which don't display and I can not play. 

Also, when I am on hard news sites there are sometimes links to stories, or political ads, or other video clips.  Some of these play, and some times they just freeze, however it could just as likely be a server problem on their end, not mine.  

And finally, this laptop while new to me, isn't on the bleeding edge of technology, it could just be that the gpu isn't up to the task, but I am more willing to doubt that, because it plays so much other material.

---

### Post by inobe on 2012-10-09
Yeah, Well, At least we have an idea now :lol:

We can guess rite and assume that maybe flash is the culprit?

[https://addons.mozilla.org/en-us/firefox/addon/flash-aid/](https://addons.mozilla.org/en-us/firefox/addon/flash-aid/)

This wonderful person developed FlashAid.

 [http://ubuntuforums.org/showthread.php?t=1487327](http://ubuntuforums.org/showthread.php?t=1487327)

---

