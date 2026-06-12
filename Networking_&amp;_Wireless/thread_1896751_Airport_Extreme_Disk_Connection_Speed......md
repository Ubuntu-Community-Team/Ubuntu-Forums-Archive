---
title: "Airport Extreme Disk Connection Speed....."
date: 2011-12-17
forum: Networking &amp; Wireless
---

### Post by alanshort on 2011-12-17
Hello, 

I have an Apple AirPort Extreme with an 2TB Elements disk attached with USB.

In OSX and Windows 7 I see very good connection speeds when transferring files from the networked drive to the workstation using wifi.

However, I also have this same disk mounted via wifi to my Ubuntu 11.10 laptop, and see very slow speeds when transferring files.

For OSX and Win7 i can transfer a 20MB file in just a few seconds, on Ubuntu, the same file take a few minutes, max transfer speed I see is around 260kb/s.... 

I get good speeds from the Ubuntu machine when downloading from the internet, its very fast, just not when accessing the networked drive....

Any ideas ???

Any help is very much appreciated.

Cheers
Alan

---

### Post by alanshort on 2011-12-17
well, have been looking at this and trying many different things, the auto mounting from Nautilus | Network is really slow, too slow to be useful, not sure if there is a problem with this that other people are seeing too with a similar configuration, my setup is out of the box, so it should work.

What I'm now doing is mounting the AirPort Extreme disk manually using : 

mount -t cifs //10.0.1.1/Elements01 -o username=alan,password=mypassword, /media/Elements01/

this works well and the transfer speed is good.

Hope this helps someone

Cheers
A

---

