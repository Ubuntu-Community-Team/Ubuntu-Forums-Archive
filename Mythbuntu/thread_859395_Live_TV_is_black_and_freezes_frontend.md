---
title: "Live TV is black and freezes frontend"
date: 2008-07-14
forum: Mythbuntu
---

### Post by dannyboy79 on 2008-07-14
I have Feisty running mythtv-backend (= 0.20.2-0ubuntu0.7.04.1). PVR-350, NOT using PVR-350 out though, I use the Nvidia 6200 VGA out to my 17" Flat Panel Monitor. 
It's a Master backend/Frontend (rarely use it as a frontend) but all of a sudden one day ubuntu upgraded the kernel to 2.6.20-17-generic which broke my ledxmit which changes the channel on my STB that I am capturing from. It also broke xorg because I used Envy to install the latest Nvidia driver. I had to temporarily make xorg.conf use vesa, then change the menu.lst to use the old kernel because I didn't want to mess with ledxmit and changing channels on my SA3250HD cable box. Anyway, I changed back to kernel 2.6.20-16-generic and thought I fixed the xorg.conf back the way it was but apparently I didn't because now I can't watch livetv, it just goes to a black screen and the frontend freezes and I have to kill the process. There's a slave backend with a pvr-500 in it which is also in the mix. I can't figure out why the video isn't being displayed? I can cat /dev/video0 > test.mpg just fine, I can also change the channels with the external channel changing script just fine also. Can anyone help with this? I have also tried starting the mythtfrontend from the command line to see what the error was, it said this:

mythtvfrontend.log
[http://www.pastebin.org/51310](http://www.pastebin.org/51310)


My xorg.conf
[http://www.pastebin.org/51311](http://www.pastebin.org/51311)

---

### Post by dannyboy79 on 2008-07-15
bump, it's been a day, anyone got any suggestions?

---

### Post by dannyboy79 on 2008-07-16
another day, anyone please help.

---

### Post by blackoper on 2008-07-20
you are better off just starting from scratch with 8.04 then to try to track down what is wrong.. you could try removing all your video drivers and reinstalling them as well using envy.

---

### Post by nickrout on 2008-07-21
try turning the frontend loging up (mythfrontend --help for howto) and post back the results.

Also, does watching recorded shows work? 

Do shows still record?

And why did you fiddle with a working system???

---

### Post by dannyboy79 on 2008-07-22
> **nickrout said:**
> try turning the frontend loging up (mythfrontend --help for howto) and post back the results.

Also, does watching recorded shows work? 

Do shows still record?

And why did you fiddle with a working system???
recorded shows work fine.
shows still record from all tuners, the PVR-500 on the Slave Backend/frontend as well as the PVR-350 on the Master Backend/frontend. I just can't watch livetv on the master backend/frontend.

I didn't intentially fiddle with a working system, there were udgrades so I upgraded not realizing that it was going to upgrade my kernel and screw up my ledxmit as well as Envy nvidia driver install.

---

### Post by nickrout on 2008-07-22
A search of the mythtv mailing list archive seems to indicate that "Waited too long for decoder to pause" is associated with the PVR350 playback. Beyond that I can't really work out a clear fix.

---

### Post by dannyboy79 on 2008-07-24
> **nickrout said:**
> A search of the mythtv mailing list archive seems to indicate that "Waited too long for decoder to pause" is associated with the PVR350 playback. Beyond that I can't really work out a clear fix.
i saw that too but I am not using the PVR-350 to display the video, I am using a Nvidia 6200. Maybe in the frontend, something got check marked for using the PVR-350 video decoder. I'll look into that. thanks for the help.

---

### Post by LarryJ2 on 2009-02-21
I have an nvidia 7300 and the error shows still shows after watching a few minutes on a remote Frontend.  

Prior to the " Waited too long for decoder to pause"
I see
```
2009-02-21 18:45:56.822 [mpegvideo_xvmc @ 0xb7306a88]skipped MB in I frame at 9 30
2009-02-21 18:45:56.822 [mpegvideo_xvmc @ 0xb7306a88]skipped MB in I frame at 69 30
2009-02-21 18:45:56.822 [mpegvideo_xvmc @ 0xb7306a88]skipped MB in I frame at 43 31
2009-02-21 18:45:56.822 [mpegvideo_xvmc @ 0xb7306a88]skipped MB in I frame at 90 35
2009-02-21 18:45:56.822 [mpegvideo_xvmc @ 0xb7306a88]ac-tex damaged at 28 37
2009-02-21 18:45:56.822 [mpegvideo_xvmc @ 0xb7306a88]skipped MB in I frame at 23 38
2009-02-21 18:45:56.822 [mpegvideo_xvmc @ 0xb7306a88]invalid mb type in I Frame at 62 38
2009-02-21 18:45:56.822 [mpegvideo_xvmc @ 0xb7306a88]skipped MB in I frame at 59 39
2009-02-21 18:45:56.823 [mpegvideo_xvmc @ 0xb7306a88]skipped MB in I frame at 22 40
2009-02-21 18:45:56.823 [mpegvideo_xvmc @ 0xb7306a88]ac-tex damaged at 21 41
2009-02-21 18:45:56.823 [mpegvideo_xvmc @ 0xb7306a88]invalid mb type in I Frame at 92 42
2009-02-21 18:45:56.828 [mpegvideo_xvmc @ 0xb7306a88]Warning MVs not available
```

---

