---
title: "Could you please test X video performance?"
date: 2006-09-08
forum: Multimedia &amp; Video
---

### Post by wkulecz on 2006-09-08
I've a performance issue with X video on Ubuntu 6.06 and Knoppix 5.0.1 using X.org 7.0.  It was fixed in Fedora Core 5, but hasn't seemed to find its way to Debian based distros!  Xorg bugzilla lists it as "fixed" and seems to think its confined only to Radon driver.  Its not, I see it on nv driver with GeForce 5500 on both i386 and x64 installs.  FC5 needed update of Xorg server on 386 and updated server and nv driver on x64.


Open a terminal window and run the command top.  Note that Xorg is 5% or less of CPU usage.

Start xawtv playing video (TV or composite, doesn't matter) or xine playing DVD and look at Xorg CPU usage in top, if you have the same performance issue I'm seeing it'll climb to 80% or more as the video window  resized to ~640x480.  Cover the video window and Xorg CPU usage goes way down!  Raise the xawtv (or xine) window and Xorg CPU goes way up!

I had this exact behaviour on FC5 initially, but they quickly had a fix.  Looks like Ubuntu and Knoppix need to talk to the Fedora X guys!  Both 10.2 and 10.4 servers have this issue!

--wally.

---

### Post by dannyboy79 on 2006-09-08
why are you using the "nv" driver for your nvidia card? You need to install the nvidia drivers by following this [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper) and you most likely won't have this problem anymore! I know I don't have any cpu spike while watching movies. I have a nvidia GeForce 6200 with the nvidia driver installed.

---

### Post by wkulecz on 2006-09-08
Why is everyone so hot for proprietary drivers?

I will try it and when it doesn't work I won't be back, I'll be busy installing Fedora Core 5.

If it does work I'll be back to report success, otherwise, bye bye!

--wally.

---

### Post by dannyboy79 on 2006-09-08
Everyone is "hot" for proprietery drivers because they actually allow the best capabilities of your video card to be utilized otherwise it's like driving a race car with normal unleaded gas when if you really want the race car to be at it's best you should be using hi-octane fuel! If it doesn't work and you go back to Fedora Core 5 then good luck to you!

---

### Post by wkulecz on 2006-09-08
I am very happy to report that the Proprietary glx drivers fixed the issue!

Method 1 of the install instructions worked perfectly.  A nice surprise is that the nvidia-xconfig step did not mess up the changes I'd made to the video modes in xorg.conf.

Ubuntu developers should still contact the Fedora Core developers to fix this issue in the open source nv driver.

Thanks!

--wally.

---

### Post by wkulecz on 2006-09-08
I'd be curious to know if this issue is confined to the xorg nv driver or occurs with other cards as well.

On FC5 required an update to the server but not the nv driver on i386, but required updtes to both server and driver on amd64.

I don't need any 3-D effects or eye candy so I'd be more than satisfied and happier with an open source driver if it worked :(

Since it does on Fedora, there is no reason it shouldn't on Ubuntu!

--wally.

---

