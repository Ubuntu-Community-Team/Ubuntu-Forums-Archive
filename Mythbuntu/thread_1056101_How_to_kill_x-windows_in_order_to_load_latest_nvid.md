---
title: "How to kill x-windows in order to load latest nvidia drivers (Mythbuntu 8.10)"
date: 2009-01-31
forum: Mythbuntu
---

### Post by Ductilemelon on 2009-01-31
Hi does anyone know how to kill x-windows in order to load latest NVIDIA drivers. I have an ASUS M3N78-VM which has an onboard NVIDIA GeForce 8200 and would like to get better picture out of the HDMI interface. The 180.22 drivers seem to have a lot of improvements. I have tried stop gdm, inet 3 ctrl alt backspace, ctrl alt F1, F2, F3, F4 but every time I launch the NVIDIA drivers it tells me that X is still running.

Also this MOBO has high def sound however I have not been able to get it to work over HDMI in fact I have only been able to get stereo out (only after unmuting alsa mixer which b.t.w. took a long time to find) any thoughts? I have not tried the optical audio yet. Driver seems to recognize high def sound hardware. There seems to be some options in the bios for sound and someone mentioned that you need to "tickle" something in the MOBO HDMI sound driver (not sure what that means). Any Ideas?

This mythtv box has been a lesson in futility.  At almost every turn something was broken or crippled. While I find open source to be really interesting the issues have been really trying. I'm still a noobee and am at my wits end with this project. I'm learning command line stuff on installs and creating .conf files etc... but at a cost of many frustrating hours. 

I've bought two different mobo's for this project and gone through 4 different versions of Mythbuntu to get something to work with my hardware as well as tried Mythdora (where I saw a post stating that "it just worked" ya right couldn't get past boot with ATI mobo).

I know that my hardware selection is probably my biggest problem but this "free" ADS Instant HDTV PCI PTV-380 card that someone gave me is what spawned the interest in Myth. Now $320 later have it working albeit in somewhat crippled form i.e. no working analog tv (card is dual tuner) I can watch and record HDTV and watch DVDs (rip function sends files to never never land???? arrggghh). Schedules direct does not work on my cable QAM channels for comcast in 60532 zip however works fine with ATSC off air so not sure how to schedule recordings off cable. 

Also very strange tuner card has two F-connectors and QAM and ATSC are on opposite which is different from the 7.XX Mythbuntu series (when I had both tuners working albeit with no sound on alalog {emulating Kworld 115/110 nxt2004 firmware needed})at that time not enough CPU/GPU to run HD hence the hardware upgrade and $320 investment)

My new hardware is as follows
MOBO: ASUS M3N78-VM
Processor: AMD Athlon X-2 64 5600+
Memory: 4GB DDR2 800
Opical:52xCDR, Memorex DVDROM (both IDE)
2 -500GB Segate SATA-2 drives (was going to raid 0 however that's the next config nightmare)
16dB proc fan (still to loud for my liking as a front end)
and USB mouse (after getting MOBO home to find 1PS2 Keyboard No PS2 mouse)
Pinnacle Remote Kit for Windows Media Center (posted a request last night to help with a Pinnacle MCE remote that doesn't work (there's another $32 to the pot) 

At any rate if anyone feels compelled to help It would be greatly appreciated. I'm probably into this thing over 100hrs by now between the three different hardware configs I've tried (with only one partially usable). 

Thanks,

Chris

---

### Post by august495 on 2009-01-31
ctrl alt f2

then 
sudo /ect/init.d/gdm stop  (start will start it)

---

### Post by Ductilemelon on 2009-01-31
Thanks for the info. Your post worked and I was able to run the updates.

As luck would have it the update didn't take and when I restarted x it blew up. It went into low graphics mode and I was barely able to see the menu's enough to get back to a usable x configuration. Oh well it doesn't surprise me nothing else works right why should this. I have a friend with the same mobo who had no problems with the 180.22 driver on freebsd and shading and other advanced features were working.

This sucks!

Thank your for your help! I must have done something wrong last time I tried ctrl alt F2. Your post worked like a charm to bad the drivers didn't.

Thanks....Chris

---

### Post by Ductilemelon on 2009-02-01
Now I've got trouble! I rebooted again and video is all messed up! replaced the x11.conf with the backup file that I'd created but still no luck. I went from a usable but crippled system to an unusable system! 

Great, just F#&%ing great!

I should have known better than to mess with this. Now I have no idea how to fix this short of rebulding the entire system. What an F#&%ing nightmare and to top it off I did it before the superbowl so I can't record! What did I do!

---

