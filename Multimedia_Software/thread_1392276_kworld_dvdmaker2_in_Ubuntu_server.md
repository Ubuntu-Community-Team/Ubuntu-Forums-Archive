---
title: "kworld dvdmaker2 in Ubuntu server?"
date: 2010-01-27
forum: Multimedia Software
---

### Post by vk7krj on 2010-01-27
Hi, thanks for reading this. I have been using ubuntu server 9.04 for a few months now, but am still very much a newby. I am now trying to set up a firewatch camera that can be viewed via my web page. I have used motion and an el-cheepo webcam to test the idea out, that works ok but the resolution of course is very poor.
Now I want to use an old analogue video camera I have as it has a much better sensor and lens. I have a kworld dvdmaker2 usb video capture device but cannot get it working under ubuntu server. When connected to the server, lsusb reports it as

1b80:e304

I have searched the forums and google, and found quite a bit of info, most of it well above my head and all of it for the gui version of ubuntu.
According to one thread I read, the version of ubuntu I am using should have the driver for this device, maybe this is only in the gui version?

Does anyone have any ideas on how I can get this working?

Thanks, Ken, vk7krj
[www.vk7krj.com]("http://www.vk7krj.com")

---

### Post by sports.car.guy on 2010-01-28
> **vk7krj said:**
> Hi, thanks for reading this. I have been using ubuntu server 9.04 for a few months now, but am still very much a newby. I am now trying to set up a firewatch camera that can be viewed via my web page. I have used motion and an el-cheepo webcam to test the idea out, that works ok but the resolution of course is very poor.
Now I want to use an old analogue video camera I have as it has a much better sensor and lens. I have a kworld dvdmaker2 usb video capture device but cannot get it working under ubuntu server. When connected to the server, lsusb reports it as

1b80:e304

I have searched the forums and google, and found quite a bit of info, most of it well above my head and all of it for the gui version of ubuntu.
According to one thread I read, the version of ubuntu I am using should have the driver for this device, maybe this is only in the gui version?

Does anyone have any ideas on how I can get this working?

Thanks, Ken, vk7krj
[www.vk7krj.com]("http://www.vk7krj.com")


Odds are you need the firmware for it. If you go through everything step by step it shouldn't seem like rocket science. It has nothing to do with the fact of GUI or no GUI. All Ubuntu Server is, is a version that does not load a GUI by default and also uses a kernel optimized for running on a high demand server, nothing most of us out here will ever need the use of in all honesty. Why run the server version. Is this an actual server. i have a Xeon server server and run normal Kubuntu on it and never had a problem going that route.

If you go into whatever package manager you are using and bring search for restricted firmware I bet installing the package which contains the firmware for v4l devices will get you going in the right direction. It is probably looking for the firmware, can't find it, and because of it only spitting out a hex value with no additional information.

---

### Post by vk7krj on 2010-01-28
Thanks sports.car.guy, yes, it is a server, and as I read about it, it is supposed to be more secure than the gui version. 
Could you be more specific in your reply please- how do I "search for restricted firmware", and what am I searching for?
Is there a cli command that will list packages I need for this?

Thanks, Ken, vk7krj
[www.vk7krj.com](www.vk7krj.com)

---

### Post by sports.car.guy on 2010-01-28
> **vk7krj said:**
> Thanks sports.car.guy, yes, it is a server, and as I read about it, it is supposed to be more secure than the gui version. 
Could you be more specific in your reply please- how do I "search for restricted firmware", and what am I searching for?
Is there a cli command that will list packages I need for this?

Thanks, Ken, vk7krj
[www.vk7krj.com]("http://www.vk7krj.com")

You can enable the same security measures on a GUI system. Out of the box the server version might be more secure, but for most, like 90% + using the server is overkill. To me unless you are running a corporate, major learning institute's, or financial's internal networks and their connection to the Internet there is no need for the server. In part because of the extra security it can mess with your normal use. Not only that, as with all Ubuntu variants there are a lot of things installed and enabled by default that the average user will have no need for or if they do, it won't be to the scale or using the capabilities added for the true server environment.

Also take into account the kernel written for the server is designed to take and use features such as memory quantities that no average user could even fit into their system. We are talking quantities of physical ram exceeding 64GB's, and is optimized for those quantities. It actually slows your system down in all honesty if it is not a server designed to take advantage of the kernel optimizations. Run what you feel is necessary, but I am telling you how for most of us out here it is overkill to run the server. Lets get onto the capture card.

Well, I was referring to in part searching online to see what the Ubuntu restricted firmware package contained for firmware. I am not even positive if your USB capture card needs a firmware, or if it is included in this package. This package only contains DVB/ATSC tuners and some capture cards. It is far from a complete list of firmware included with it.

Okay, wait, I thought you were using 9.10. You are going to have to place the firmware in for the device if it needs one into the /lib/firmware directory yourself. Then you need to do a compile of video4linux's latest release along with a kernel as well. Not in that order. You are best to upgrade to 9.10 if you want to use the card.

Support is ending for 9.04 in far under a year, the firmware is I am talking about has been packaged for it along with a version of video4linux that supports the capture device most likely. Either way you are looking at a couple hours of you life, why not get yourself set for updates over the next couple of years?

---

### Post by vk7krj on 2010-01-28
I had a good read of the forums this morning, and based on that I think I wll wait until April when 10.04 is due to be released- from what I read, 9.10 has a few issues which (as a beginner) I can do without.

Thanks again for your help sports.car.guy, it is appreciated.

Ken, vk7krj
[www.vk7krj.com](www.vk7krj.com)

---

### Post by sports.car.guy on 2010-01-29
> **vk7krj said:**
> I had a good read of the forums this morning, and based on that I think I wll wait until April when 10.04 is due to be released- from what I read, 9.10 has a few issues which (as a beginner) I can do without.

Thanks again for your help sports.car.guy, it is appreciated.

Ken, vk7krj
[www.vk7krj.com]("http://www.vk7krj.com")

Not a problem. I would look at giving it a shot myself, but I am not one who likes to wait..lol

---

