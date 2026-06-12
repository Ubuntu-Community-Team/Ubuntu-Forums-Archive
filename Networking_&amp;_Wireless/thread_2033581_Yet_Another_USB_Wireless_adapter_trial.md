---
title: "Yet Another USB Wireless adapter trial"
date: 2012-07-26
forum: Networking &amp; Wireless
---

### Post by foberle on 2012-07-26
I tried out Ubuntu on my laptop (using wubi with Windows). I really like it so I 
decided to do the same on my Windows desktop, which uses a NetGear WMA3100 USB wireless dongle to access my wireless hotspot.

Of course, Ubuntu doesn't recognize it and, after searching the web, I realized I 
might need to get something else, since the kind folks at Netgear seemed surprised that there were any operating systems other than Windows, and claimed that the WMA3100 wouldn't work on anything but Windows.

But I did some more searching and found that many folks claim to have made the WMA3100 work using ndiswrapper. So, based on what I found on the web, I decided to take a shot at getting the thing to work (Obviously I didn't succeed). I downloaded the following files (32 bit versions) from another computer on to a USB drive:

ndiswrapper-common_1.50-1ubuntu1_all.deb
ndiswrapper-utils-1.9-1.50-1ubuntu1_i386.deb
ndisgtk_0.8.5-1_i386.deb

I right-clicked on the first of these on the USB folder display, then selected "Open with Archive Manager", after which I highlighted the three lines Debian, sbin and usr, and then clicked the "Extract" command at the top of the page. It looked like something good happened, but I am too new to Ubuntu to know for sure.

When I tried the same thing with ndiswrapper-utils-1.9-1.50-1ubuntu1_i386.deb, I ran into trouble. The following is the result that appeared:

tar: ./usr/share/doc/ndiswrapper-utils-1.9/changelog.Debian.gz: Cannot create 
symlink to `../ndiswrapper-common/changelog.Debian.gz': Operation not permitted 
tar: ./usr/share/doc/ndiswrapper-utils-1.9/NEWS.Debian.gz: Cannot create symlink to `../ndiswrapper-common/NEWS.Debian.gz': Operation not permitted 
tar: ./usr/share/doc/ndiswrapper-utils-1.9/AUTHORS: Cannot create symlink to 
`../ndiswrapper-common/AUTHORS': Operation not permitted 
tar: ./usr/share/doc/ndiswrapper-utils-1.9/README: Cannot create symlink to 
`../ndiswrapper-common/README': Operation not permitted 
tar: Exiting with failure status due to previous errors 
dpkg-deb: error: subprocess tar returned error exit status 2 

Obviously I didn't try the same process with ndisgtk_0.8.5-1_i386.deb, since it is 
clear that ndiswrapper needs to be working for ndisgtk to work.

So, now I'm at a loss on how to proceed. The repetitive phrase "Operation not 
permitted" leads me to suspect this might be some sort of permission thing, and I really have no clue what a symlink is.

I've attempted to read all of the postings concerning this subject, but it sounds 
like most of the issues discussed assume that the ndis stuff was already 
successfully installed, and I haven't spotted anything that seems relevant to my situation.

I would certainly appreciate any suggestions anyone has. And, oh, by the way, the Ubuntu version is 12.04, downloaded fresh about four days ago, and I do have the original Windows installation CD for the Netgear WMA-3100.

Failing that, if anyone knows of a USB wireless adapter that works on both 
Windows and Ubuntu, I would appreciate hearing about it. I looked at the lists of 
compatible devices on line, but they seem to mostly list stuff that isn't still 
available so I quit poking through it. I called a lot of local places, but I got only one recommendation (from Tiger for a TrendNet TEW-664UB). The rep assured me that this would work on Linux and Windows but, cynic that I am, I contacted TrendNet, and the rep there said he didn't think it would work without Windows.

Thanks for any advice ...

---

