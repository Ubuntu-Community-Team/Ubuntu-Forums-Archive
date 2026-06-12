---
title: "using TV as default monitor during install?"
date: 2006-07-23
forum: Multimedia &amp; Video
---

### Post by crispy_420 on 2006-07-23
Ok here is a little background, I'll keep it short.

I have an extra computer running WinXP Media Center that I rarely use and I want to install ubuntu on it and eventually mythtv. That is easy enough right? But here is the catch. It is in a entertainment center and fully wired into a TV and reciever. It is hooked up to the TV via S-Video and to the reciever via component audio in (eg. right front, left front, etc.). As you can imagine it would be a _HUGE_ hassle to remove it, set it up and then put it back.

Now to my problem. I can boot for install CD and go through the boot process up until I get to destop. As I expected I only get a black screen. That was no surprise at all.

Here is what I need help on:

1. Getting gui for install. (Can I modify xorg.conf in LiveCD to get TV out?)

2. Once installed will default drivers work tell fully setup.

3. Based on my hardware will this even work?

MY HARDWARE:

[PHP]Asus motherboard
NVidia GeForce MX440 (64MB)
512MB DDR
Intel Celeron 2.8GHz
Happauge PVR-150 MCE Low Profile
Windows Media Center Remote (official MS)
Lite-On DVD Burner[/PHP]

My main concern is install and getting to desktop. Also hardware is a major issue too. But from there I can do all setup and configuration over network via Remote Desktop.

Anyone accomplish this or that can lead me in the right direction will be helpfull.

Thanks in advance.

***** If all else fails I may get SageTV for linux, but I would like to avoid this if possible. *****

---

### Post by Dr. Nick on 2006-07-23
Have you tried it yet? I was able to install ubuntu using the live cd through a composite video out to a tv. Didnt really take much more than using a monitor, If I reacall I had to change a few of the video boot options on the live cd

---

### Post by crispy_420 on 2006-07-23
I did try it and only got a black screen. But I'll try again right now after I look at those options.

OK that was a step in the right direction. I booted with safe mode and now I can begin install.

Thanks for the tip.

---

### Post by tseliot on 2006-07-23
If nothing else works you can install Ubuntu using the alternate installation CD.

Then (after the installation) you can configure your xorg.conf.

---

