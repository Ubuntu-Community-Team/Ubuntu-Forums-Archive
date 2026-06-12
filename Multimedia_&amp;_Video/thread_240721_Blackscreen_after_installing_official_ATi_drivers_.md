---
title: "Blackscreen after installing official ATi drivers for X700 on x64-system"
date: 2006-08-21
forum: Multimedia &amp; Video
---

### Post by forteller on 2006-08-21
Hi all! First time poster and Linux user here, so please have patience.. :)

I've searched for the answer to this, but I couldn't find it. 

My system is a Acer Ferrari 4005 (often just called 4000) laptop with a AMD Turion 64 CPU and a ATi X700 graphics card

I've installed Ubuntu 6.06 and downloaded all updates without any problems. But then I wanted to get my graphics card to work correctly. I followed the [method 2 instruction]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.28.8_drivers_in_Ubuntu_Dapper_Manually") at the Unofficial ATI Linux Driver Wiki. As far as I'm aware I did exactly as it said.

After that the screen is black every time I reach the logon screen. Everything else seems to work normaly. I hear the drum sound, and when I enter my username and password I hear the logon sound, but it's still completely black.

I've tried to connect an external screen to see if it just asumes that an external screen is the default screen, but that didn't do anything. I've also booted the recovery mode and gone through this:```
sudo dpkg-reconfigure xserver-xorg
```But still no luck.

I would apreciate any help!

---

### Post by Ziox on 2006-08-21
> **forteller said:**
> Hi all! First time poster and Linux user here, so please have patience.. :)

I've searched for the answer to this, but I couldn't find it. 

My system is a Acer Ferrari 4005 (often just called 4000) laptop with a AMD Turion 64 CPU and a ATi X700 graphics card

I've installed Ubuntu 6.06 and downloaded all updates without any problems. But then I wanted to get my graphics card to work correctly. I followed the [method 2 instruction]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.28.8_drivers_in_Ubuntu_Dapper_Manually") at the Unofficial ATI Linux Driver Wiki. As far as I'm aware I did exactly as it said.

After that the screen is black every time I reach the logon screen. Everything else seems to work normaly. I hear the drum sound, and when I enter my username and password I hear the logon sound, but it's still completely black.

I've tried to connect an external screen to see if it just asumes that an external screen is the default screen, but that didn't do anything. I've also booted the recovery mode and gone through this:```
sudo dpkg-reconfigure xserver-xorg
```But still no luck.

I would apreciate any help!

it's a confirmed bug for X700 cards: [https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-ati/+bug/22985](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-ati/+bug/22985)

---

### Post by forteller on 2006-08-21
I don't think that is the same thing. It says: > It
has to do with X mis-detecting which is the primary display and which is the
secondary display.But as I said in my original post I have tried to connect an external monitor without any luck. I the bug you're linking to is something that has to do with the previous Ubuntu release.

---

