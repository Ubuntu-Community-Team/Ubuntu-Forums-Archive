---
title: "PMServ - PS3 Media Server Linux Distribution on NAS"
date: 2011-06-25
forum: Multimedia Software
---

### Post by Straumoy on 2011-06-25
Hello and thank you for taking your time reading,

I've been looking for a way to get the PMServ to work on my NAS, but with little success. 

About my hardware:
I recently became the proud owner of a BlackArmor® NAS 220 2TB [http://www.seagate.com/www/en-us/products/external/blackarmor/blackarmor_nas_220/](http://www.seagate.com/www/en-us/products/external/blackarmor/blackarmor_nas_220/), hoping it would allow me to have access to my media (music and video mainly) without having my computer running 24/7. 

On-the-fly transcoding is not an issue, as I'll be using video and audio formats that the PS3 can handle right out of the box. I'd use the media server functionality that came with the NAS, but several files are either listed as corrupted or not at all, despite that the files works just fine when copying them to a USB stick, then plug it in the PS3. Even *.divx files created with the official converter are not listed. :confused:

So the big question is how to install it? Click the link below to see the details about the software:
[http://www.ps3mediaserver.org/forum/viewtopic.php?f=3&t=5991](http://www.ps3mediaserver.org/forum/viewtopic.php?f=3&t=5991)

What I tried is to take out one of the HDD from the NAS, plug it into my computer, boot the computer from the live CD and install it. Once that was done, I put the HDD back into the NAS. No dice... When I tried to PING the NAS from my computer with the newly installed HDD inside, I go *"destination host unreachable"* error. My computer is currently running Win 7 Ultimate 64bit.

I tried to put the NAS HDD into my computer and boot from it, got confirmed that the PS3 media server was running, but I couldn't find it on the PS3, even when I scanned after it.

There isn't much response from the official thread, so I decided to try my luck here. As I understand it, it's probably just some sort of configuration issue, but I have no idea what that might be.

I'd be grateful for any assistance you can provide and if you need more info, I'll answer as best I can.

---

### Post by fuglett on 2011-08-07
hey buddy. i'm having some crazy issues streaming to my PS3 too, but i think i can at least provide some insight here.

PS3 Media Server is an application that runs on top of your operating system.  That NAS drive that you have has just enough software in it to talk on your network, but it's nowhere near smart enough to know how to run PS3 Media Server, nor will it try to do so automatically. it's like expecting your dog's food bowl to fill itself because you gave it the key to the closet where you keep the food.  you still need a computer to point to that media and serve it to your PS3.  however, if that drive has a usb port on it, your PS3 might be able to get at your media itself when plugged into the drive.

---

