---
title: "Others experience with the AR928X wireless card, need opinions."
date: 2009-09-13
forum: Networking &amp; Wireless
---

### Post by derrick1985 on 2009-09-13
Hi,

I wanted to ask some other users of the AR928 wireless card, what their experience with it was. It is what came by default with my Asus EEEPC 1000HE but I have always had some problems with it, in both Windows and even worse in Ubuntu. I have my home network set to broadcast in N only (Dlink DIR-655) as my EEE is the only wireless device, and works at N speed. When connected in Windows, it would work at the full 300mbps but would occasionally cut out. This was really annoying, as sometimes in order to get it to connect again I would have to do a repair. 

I installed Linux last week (finally convinced my wife not to use the laptop :D) and I love it, much snappier than XP, but I still got the same problems with my wireless connection, except now it would cut out more frequently. So, trying to fix the problem rather than go back, I downloaded the compat-wireless drivers and compiled from source and installed (2.6.30, ath9k driver) and while it connected quicker, it would still cut out. The last idea I had that popped into my head, I decided to set my router to G only mode, and have not since had a single problem since. I know the router will work in N mode, because the laptop I had before, (Macbook Pro 2.33gGHz) worked fine in N only mode at 300mbps. 

My question I am asking I guess is, the problems that I am having, is it common to anyone else with the same card or router (or even both), or is this just a driver issue that will have to be worked out? If it's a driver issue, is the driver for the Intel 4965 A/B/G/N card any better, or is there another wireless N PCI-E card that I can buy that will work at N speed (preferably 300) and not constantly cut out?

Thanks,

---

### Post by inzaneg on 2009-09-18
hi.

I have a 1000he and dlink 615. I have done a lot of distrohopping on this cool netbook, and the one distro that worked perfect out of box, with wireless, was fedora 11(pulseaudio is horrific in fedora 11). It's running kernel 2.6.29.4. I tested this with auto n/g and hidden network + wpa2. 

I'm running jaunty with 2.6.29.4 and it runs great :)
Got the three debs from here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

To your question, this is a driver issue.

---

