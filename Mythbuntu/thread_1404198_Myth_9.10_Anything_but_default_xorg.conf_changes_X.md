---
title: "Myth 9.10 Anything but default xorg.conf changes Xsplash logo"
date: 2010-02-11
forum: Mythbuntu
---

### Post by rodercot on 2010-02-11
Hey All,
 
 A couple weeks back I posted about loosing my xpslash logo from the black back with mythbuntu and the white progress bar in the middle of the screen this was replaced by a grey rectangle with the old mythlogo in the top left corner of my screen. 

 yesterday I am testing new gt 220 and 240 nvidia cards and on a fresh build of 9.10 I started to cutomize my xorg.conf file and as soon as I changed to my custom xorg file which locks in 1080p 60hz native modeline and a few other options and reboot my xplash image is back to the grey rectangle and I loose the mythbuntu xsplash logo.

 Can someone please xplain Xsplash to me, is there a command you need in the xorg file or is there a place to set the res. Has anyone else seen this or is an option I am using that is breaking xspalsh. until now I just renamed the exec file and got rid of it all together as I did not know what was breaking it. 

 I should also point out that this is a fresh build again and up to date via JYA's repos and the front end it still 40+ seconds to load up a useable front end from a useable desktop after booting or switching from XBMC to Myth FE with appswitch. Could the XORG file have a bearing on this as well. I have NO delays contacting my backend in my log files. My back end is 8.10 updated to .22 BUT it is using the mythbuntu weekly US builds not avenards.

 Regards,

 Dave

---

### Post by SiHa on 2010-02-11
FWIW, I have exactly the same, it occurred when I disable composite extensions to stop tearing with VDPAU playback. This is with a stock Mythbuntu 9.10 Install and no updates.

To be honest, it's not that big a deal for me, so I've just left it. Just thought you should know you're not alone

---

### Post by rodercot on 2010-02-11
> **SiHa said:**
> FWIW, I have exactly the same, it occurred when I disable composite extensions to stop tearing with VDPAU playback. This is with a stock Mythbuntu 9.10 Install and no updates.

To be honest, it's not that big a deal for me, so I've just left it. Just thought you should know you're not alone

 Thanks,

 OK then that makes sense, I just added option composite disable last week and I thought I had removed it, but I guess not. Like I said I too just rename the xspalsh exec and that stops it all together which is fine with me.

 thanks for posting.

 rgds,

 Dave

---

