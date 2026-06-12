---
title: "Opera Nvidia and flash"
date: 2011-11-10
forum: Multimedia Software
---

### Post by beew on 2011-11-10
I am having problems viewing flash videos with Opera and using the Nvidia proprietary graphic card when hardware accleration is enabled for flash.

On Youtube Opera freezes when video is maximized and then minimized again, on Vimeo flash just crashes. It has been going on for quite a while and I have patiently gone through several updates for Opera (now 11.60), flash (now 11.2.202 beta installed through flash-aid) and Nvidia graphic driver (now 285.03, the latest stable release) since the problem first occured, but the problem persists.

The flash and Nvidia combo has been working for Firefox without issue, but not with Opera. I have tested on 11.04 and 10.10, in 10.10 the problem is more severe.

The problem seems to have something to do with hardware acceleration video decoding with flash. I have another installation where I use the open source nouveau driver,--hence no accelerated decoding,--and there is no problem (tested on same machine), also the 11.xx stable version of flash (from repo) as well as the flash 11.xx pre releases (installed with flash-aid)  don't support hardware decoding on Linux and they worked fine with Opera. It is just that whenever hardware acceleration works (which is desirable as Firefox is my main browser) it breaks Opera.

Flash 10.XX apparently worked with both Opera and Firefox with hardware decoding for a while and then this problem occured. Upgraded with flash-aid to flash 11 pre-releases and it worked with both but with no hardware decoding, same with flash 11 stable. Then hardware decoding is restored with the latest flash 11.2.202 beta but flash stops working on Opera again.

I am also checking out Adobe's website. Somehow it doesn't list Opera as a supported browser under Linux (but it appears under Windows and OSX), [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)

Can anyone tell me what is going on? Thanks.

---

### Post by beew on 2011-11-14
Bump!

---

### Post by beew on 2011-11-18
Any insight, me too???

---

### Post by lovinglinux on 2011-11-18
I don't have any insight, but from my experience with Opera before Firefox 4, flash didn't work well with it.

---

### Post by beew on 2011-11-19
Hi, Lovinglinux,

Thanks for the reply. But there is a difference between not working well and not working at all. It seems that with vdpau enabled Opera doesn't work with flash at all, otherwise it works though not steller,--but then neither is firefox (that's why I always use your flashvideoreplacer addon for Firefox if vdpau is not available)  I think there may be an option in Opera for hardware acceleration which has been turned on and that is what causing the problem. I am wondering if you or anyone knows if it exists and how to turn it off if it does. 

Also it is kind of strange that Adobe doesn't list Opera as a supported web browser under Linux. I don't know if it is recent or it has always been this way.

---

### Post by cuyo01 on 2011-11-19
for me opera is working fine with hardware acceleration, im using opera 11.52 in ubuntu 11.10 with proprietary driver from nvidia repository, GT240 video card and flash plugin 11.1.102.55.

---

### Post by beew on 2011-11-19
I am using the same flash version, Nvidia 285.05 and Opera 11.60 in both Natty and Maverick. In Maverick the problem is worse. I tried downgrade to Opera 11.52 but the problem actually became worse, Opera started freezing even before the Youtube page is loaded! (I have Opera's "flash block" on, but with Opera 11.52  as soon as I put the cursor on the big triangle thing without even clicking it Opera began to freeze and turned grey)

---

