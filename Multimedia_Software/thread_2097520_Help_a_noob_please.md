---
title: "Help a noob please?"
date: 2012-12-23
forum: Multimedia Software
---

### Post by akagetsu on 2012-12-23
Hi guys. This is my first post and I've taken quite a while to get the balls to post this. I've been searching quite a lot on the internet how to make this work and found a number of solutions but apparently none actually, fully worked for me.
I have basically 1 major problem and 1 minor problem. The minor one is that I'm running Ubuntu 12.04 on a Samsung, which apparently has some complications as it is (backlight, processor, function keys). I have found the Linux on my samsung page and downloaded from that repository and well, I think everything works. The luminosity doesn't fully go down with the function keys, only 1 step. To bring the luminosity down I have to go to the System Settings. Also I think I can do CPU undervolting (which the drivers on windows apparently do that by themselves) but I have no idea how to do that in Ubuntu (it would be nice to have a greater battery life than 2-3 hours when on windows it gets to 5-6 hours).
The major problem is that my laptop has an nvidia gt 520mx graphics card and I've been searching the internet high and low to try and make it work on ubuntu. I tried about 4-5 different ways to make it work but apparently there's no real change (if I type lspci in command line, under VGA it still tells me Intel blabla).
Now a very important note here is that I'm pretty much a noob and I'm learning as I go. But it would be nice to actually get things working properly since I wanna use Ubuntu as my main OS.

TL;DR: HOW TO MAKE NVIDIA GRAPHICS CARD WORK ON UBUNTU?!?

Thank you very much for taking the time to help me and apologies to those whom this post might have bothered. :)

---

### Post by SuperFreak on 2012-12-23
On my Ubuntu machine which uses Cinnamon DE rather than Unity I find "Additional Drivers" under Menu/Preferences. This will allow you to search for the appropriate proprietary driver for Nvidia

---

### Post by Petro Dawg on 2012-12-23
> The major problem is that my laptop has an nvidia gt 520mx graphics card  and I've been searching the internet high and low to try and make it  work on ubuntu. I tried about 4-5 different ways to make it work but  apparently there's no real change (if I type lspci in command line,  under VGA it still tells me Intel blabla).
Now a very important note here is that I'm pretty much a noob and I'm  learning as I go. But it would be nice to actually get things working  properly since I wanna use Ubuntu as my main OS.Have you tried installing any additional drivers by using the "Additional Drivers" app?  If so, which ones?

> I tried about 4-5 different ways to make it workAlso, what have you tried so far, and what were the results if any?

---

### Post by akagetsu on 2012-12-23
Upon clicking Additional Drivers in the System Settings menu, it just appears with an empty list, nothing in it.

I tried installing the drivers from the original repository with sudo apt-get install nvidia-current. Then I also tried manually installing the driver after downloading it from the nvidia homepage. Trust me, I've been through 3 or 4 tutorials on how to make it work top to bottom. The first few times I either got my screen resolution to 800x600 without possibility of change, or got the gnome interface disabled and stuff like that..but the last few times nothing changed..I just finished the steps in the tutorials and...that's it..nothing changed..I don't know what to do..there should really be a place or page or something covering absolutely everything related to this issue...

---

### Post by Pjotr123 on 2012-12-24
> **johnsmith000 said:**
> I have basically 1 major problem and 1 minor problem. 

Please create a hardware list in this fashion:
[https://sites.google.com/site/easylinuxtipsproject/tips#TOC-Make-automatically-a-nice-document-with-all-your-hardware-information](https://sites.google.com/site/easylinuxtipsproject/tips#TOC-Make-automatically-a-nice-document-with-all-your-hardware-information)

...and attach it to your answering message.

---

### Post by akagetsu on 2012-12-24
I made it into a .tar since it didn't let me upload directly html.
Thank you very much for taking the time! :)

---

### Post by Pjotr123 on 2012-12-24
> **akagetsu said:**
> I made it into a .tar since it didn't let me upload directly html.
Thank you very much for taking the time! :)

OK... It seems that your laptop has no Nvidia graphics card at all, but an Intel, which runs on the i915 driver, as it should. So no need for additional drivers.

So as far as video is concerned, there's no problem at all....

---

### Post by akagetsu on 2012-12-25
Well maybe...but I definitely know I have an Nvidia geforce 520mx. I'm using it in Windows, and playing games and such..
I want to make it work in Ubuntu as well.
Or I don't know..maybe you guys might suggest that I don't need the nvidia to work with ubuntu, I don't know...I'm accepting of any help and tips.

---

### Post by Pjotr123 on 2012-12-25
OK... It may be a dual graphic card situation, for which you need Bumblebee.

In the terminal (use copy/paste to avoid errors):
```
sudo add-apt-repository ppa:bumblebee/stable
```

Press Enter. Your password won't show, not even dots, that's normal.

Then in the terminal (copy/paste):
```
sudo apt-get update && sudo apt-get install bumblebee bumblebee-nvidia
```

Press Enter again.

When this job is done, reboot your computer. All should be well now. :)

To run your application with the discrete NVIDIA card run in the terminal:
```
optirun [options] <application> [application-parameters]
```

Example:
```
optirun firefox
```

For a list of options for optirun run:

```
optirun --help
```

Normally you do not use optirun for your window manager, installations or other non graphic heavy demanding programs. The optirun command is mainly used for graphic demanding programs or for games.

---

### Post by offgridguy on 2012-12-25
> 

(it would be nice to have a greater battery life than 2-3 hours when on windows it gets to 5-6 hours). 
A lot of threads deal with this issue, unfortunetly  you probably won't get much more
than this with ubuntu.

---

