---
title: "Can't get my 3-monitors to work."
date: 2011-07-22
forum: Multimedia Software
---

### Post by xBkS on 2011-07-22
Hi guys, I'm not new to this distro or the forum I only decided to register today seeing as I actually do have a problem and need help because I can't work it out myself. :( I'm currently trying to get my 3-monitor set-up to work with Natty but I just can't get it to work. I can get 2 of my monitors to work fine in twin-view, and I can move windows between them, but I want to be able to move windows between all three of them. Now, I've tried many different configurations, I've tried making them all Seperate X's, but that didn't work as only two of them turned on and it was like Xorg crashed because Ubuntu would login, but nothing would come up after that it was just like the default Ubuntu wallpaper with no launcher, or desktop or even management. I tried ctrl+alt+f2 to try bring up terminal but that never worked either. i then tried using 2 monitors in twin-view and 1 as a seperate X, but that didn't work either as the same problem happened when I made them seperate X's. 

My current specs are;

x1 nVidia GeForce 9500M GS graphic card.
x1 VGA/DVI 19" Acer P193w monitor
x1 HDTV
x1 Default Laptop monitor. 

running on my Acer Aspire 6920. 

My problem is sort of similar to the guy [in this thread.]("http://ubuntuforums.org/showpost.php?p=11067615&postcount=1") I have searched the forum before I posted. :) 

Any help would be greatly appreciated! 

- BkS.

---

### Post by jk121960 on 2011-07-22
I am having the same problem, I went back to 10.04 and had more luck, if you dont mind losing compiz in 10.04 you can use Xinerama and it will work with 3, but I tried Xinerama in ii.04 and it crashed X. I am still attempting to find out what some of these guyts are doing to get more then 2 with compiz but6 so far no luck. But as I said if you can live without compiz drop back to 10.04 and use Xinerama and it will work. Use the Ubuntu binaries for the driver and make sure you use the latest ones, update your package listing and look for the latest version and load that. Dont use the download from NVIDIA for 10.04. 

--jerry

---

### Post by xBkS on 2011-07-22
> **jk121960 said:**
> I am having the same problem, I went back to 10.04 and had more luck, if you dont mind losing compiz in 10.04 you can use Xinerama and it will work with 3, but I tried Xinerama in ii.04 and it crashed X. I am still attempting to find out what some of these guyts are doing to get more then 2 with compiz but6 so far no luck. But as I said if you can live without compiz drop back to 10.04 and use Xinerama and it will work. Use the Ubuntu binaries for the driver and make sure you use the latest ones, update your package listing and look for the latest version and load that. Dont use the download from NVIDIA for 10.04. 

--jerry

I might wait till 11.10 to see if nVidia and/or Ubuntu dev's try see what the problem is. I'm currently using 2 of the monitors just now which will just have to do for the time being. I love this Unity desktop a lot, and I don't think I could go back to Gnome. Last time I tried to install 10.04 it took me ages, I had to get a buddy from another forum to help me, because there was so many different issues with hardware. I'll bide my time. 

- BkS

---

### Post by khelben1979 on 2011-07-22
Are you using the latest version of the non-free nVidia drivers? Might be a driver issue causing the problem.

---

### Post by altometer on 2011-07-22
[http://www.intel.com/p/en_US/support/highlights/chpsts/965m/](http://www.intel.com/p/en_US/support/highlights/chpsts/965m/)

Your graphics chipset doesn't support more than 2 video outputs. Get one of these.(or a similar model)
[http://www.amazon.com/StarTech-External-Monitor-Adapter-USB2DVIE2/dp/B002ZT08U6](http://www.amazon.com/StarTech-External-Monitor-Adapter-USB2DVIE2/dp/B002ZT08U6)

---

### Post by xBkS on 2011-07-22
> **khelben1979 said:**
> Are you using the latest version of the  non-free nVidia drivers? Might be a driver issue causing the  problem.

Are you talking about nVidia's own binary drivers? or the default ones that come with Natty?  

> **altometer said:**
> [http://www.intel.com/p/en_US/support/highlights/chpsts/965m/](http://www.intel.com/p/en_US/support/highlights/chpsts/965m/)

Your graphics chipset doesn't support more than 2 video outputs. Get one of these.(or a similar model)
[http://www.amazon.com/StarTech-External-Monitor-Adapter-USB2DVIE2/dp/B002ZT08U6](http://www.amazon.com/StarTech-External-Monitor-Adapter-USB2DVIE2/dp/B002ZT08U6)


I believe it does, as I had all three monitors running nicely when I had windows vista (ew). I will look into getting one of those though! thanks.

- BkS

---

### Post by khelben1979 on 2011-07-23
> **xBkS said:**
> Are you talking about nVidia's own binary drivers? or the default ones that come with Natty? 
- BkS

Yes, nVidias own drivers.

---

### Post by xBkS on 2011-07-23
> **khelben1979 said:**
> Yes, nVidias own drivers.

Those are the drivers I have been using all a long. The default Ubuntu ones won't pick up my other 2 monitors, nor will it even pick-up the name of the laptop monitor.

---

