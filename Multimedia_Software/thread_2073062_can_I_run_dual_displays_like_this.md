---
title: "can I run dual displays like this?"
date: 2012-10-18
forum: Multimedia Software
---

### Post by T Stew on 2012-10-18
Hello all, new to Unbuntu. Just built a new machine a couple weeks ago and have been running 12.04 LTS on it, and a 27" LED.  It is my intention to buy another 27" or similar for a dual monitor setup. Due to the cost though I planned it for a future upgrade.

In the mean time I thought I could use my old 17" trinitron CRT thats not being used otherwise. I have the 27" LED hooked up to the DVI-D on my Radeon 7770, and my 17" CRT hooked up to the VGA port on my mobo (asrock z77 pro4).

At first I got the word Unbuntu on the CRT with some red dots under it, but thats it, and Ubuntu didnt detect any monitors other than my 27". When I shut the system down, command line information about the shutdown pops up on the CRT. But after reboot, still cannot get Ubuntu to see this monitor is there. In the cmos the only thing I can find about the onboard video is to select which one is primary, and its set to PCI-E since my Radeon is primary. 

Anyone have any suggestions? 
Thanks!

---

### Post by Metalpen1984 on 2012-10-19
So, do you mean:
When startup :  CRT up,   27" down
During Usage :  CRT down, 27" up
Shutting Down:  CRT up,   27" down
Are you able to set up the monitors through "Monitors" in setup?

My only experience is my 12.04 HP laptop with only Intel HDG2000/3000, and works fine with dual monitor, though they were all automatically set as 1024*768.

---

### Post by T Stew on 2012-10-19
27" remains fine the whole time. It is the only monitor that shows up in Ubuntu display settings.

17" does display some wierd stuff but never usable. The very first time I plugged it in it said "Unbuntu" in the center of the screen. When I shut the system down it displays some of the command line info about the shutdown (or more like flickers it since it only takes less than a second to shut the system off). Right now its got a couple lines of random characters on the top left corner.

---

### Post by Metalpen1984 on 2012-10-21
This is really wired. Hope there will be another expert to answer this question. 

Here is my opinion.

Did you try using another LCD monitor (from friends, perhaps) to "try and error"? If you find another display and it works fine, that means it's the CRT problem (not able to be detect). 

If the problem remain the same, the other reason might be:

1. The driver of your display card.
2. Malfunction of the card, if you are "too lucky", you will get a bad display card.
3. Setting.

Good luck!

---

