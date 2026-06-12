---
title: "strange internet connectivity issues"
date: 2010-08-04
forum: Networking &amp; Wireless
---

### Post by Trugeek on 2010-08-04
I am new to Ubuntu although I've always had an interest in Linux. Been using Windows for the last several years and past due for a change!
Here's the best that I can describe the problem. This has happed twice and I am unable to find a resolve.
A few weeks back I installed Ubuntu 10.04 32 bit on a seperate HDD. I had connectivity issues with that install, the same issues that I am having with the new install from a few days ago.
After installing and rebooting into Ubuntu, I had no internet access with the exception of Google (I downloaded and installed Chrome with the same results). I would reboot again and notice a strange icon next to the network arrows. Clicking on this, would tell me that there is a video display driver that needed to be installed. I installed the driver and asked for a reboot. I did not reboot, but instead went to check updates and found over 200 updates. These downloaded and installed quickly. Another reboot request is refused, because I wanted to check to see if I had Internet access. Yes, I could go to any site and all pages would load quickly and perfectly. I played with the internet almost an hour without any problems. Time for the reboot...now no Internet with the exception of Google and one or 2 sites loaded slowly and not completely.
I went to Eth0 and checked IP, Net Submask, Gateway etc. All numbers are good. I created Eth1 as static and still the same results. I am wired to a Dlink 825 router, but I connected directly off the cable modem with same result. I tried to log into the Dlink router [http://192.168](http://192.168)... and it said connecting to Dlink, but never did. IP camera, same thing, put in the address and said connecting to camera but never did. So it appears to be more than just an Internet issue as it is affecting LAN as well. 
I read in an earlier post about making some speed changes with mii-tool, but I wouldn't even know how to access this.
Some stats: Acer desktop with SIS ethernet chipset. Multi OS machine with Ubuntu 10.04 32 bit and Windows 7 32 bit installed on seperate HDDs. When booting there are several options for Ubuntu and Windows is at the bottom of the list (where it belongs) I always choose the first option.
I would really like to get Ubuntu working like it did on the 2nd reboots, but I really don't know where to begin. I am just able to play with DHCP or static settings for now and that makes no difference. I do not believe there is a firewall that is in the original 10.04 installation, and I have not installed anything except the video driver, updates and Google Chrome
Any help or suggestions/recommendations would be greatly appreciated!
Thanks in advance!
Steve

---

### Post by Iowan on 2010-08-05
AAARRRGGG... Too blue!!! :cool:
From Code of Conduct:> # Please use color and font properties for highlighting portions of your text, and not for all of the text in your post.

There are some threads around that discuss disabling IPv6 - perhaps that might help...

---

### Post by lisati on 2010-08-05
> **Iowan said:**
> AAARRRGGG... Too blue!!!

Fixed

---

### Post by JBAlaska on 2010-08-05
[COLOR="Blue"]Ok here's what you need to do[/COLOR]...Just kidding,

Please open the terminal and post the output of:
```
ifconfig
```

---

### Post by Trugeek on 2010-08-08
Sorry about the blue text. I will study the "code of conduct" B4 I post next time.
Just wanted to let you know that the problem is solved.
I was going through some posts again and didn't realize there was issues with the SIS190 Ethernet chip set.
I came across a  post under the heading: "Brand New Install and no Internet" And a reply was posted by Sealbhach (5/14/2010) and I guess there is a bug report on the SIS chipset. Changing the MTU under "edit connections" from automatic to 1492 did the trick. I could not look at anything on my LAN until I did a reboot, but after that everything is working and continues to work without problem.

---

