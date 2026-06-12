---
title: "NVIDIA Jaunty 180.44 Wont load on boot"
date: 2009-05-06
forum: Multimedia Software
---

### Post by punzada on 2009-05-06
So here is my current issue, been happening ever since I upgraded to jaunty, unsure if its a driver issue or an xorg issue or what exactly ...

Since upgrading from ibex (full format and reinstall) I can never seem to maintain a stable graphical system. On boot (I have my kernel parameters in grub to see the boot process and hide the graphics) it appears to load as normal, flicks over to a screen with a simple '_' on it, shows the nvidia logo for the driver, and returns to a login prompt, it will cycle through this process around 5 times before telling me that my configuration is not well and i'll either need to fix it through the prompts, or exit back to console etc etc. 

If I exit back to console and run nvidia-xconfig as root it will replace my defunct xorg with a working one, and then if I startx it loads as normal. From here once logged in to get a fully flushed out xorg I run gksu nvidia-settings and save to the xconfig. 

From there I log out, shut down. On a restart, it *still* fails to load, I wait for it to cycle 5 times, I cat /etc/X11/xorg.conf and it appears to have taken all the working values from the nvidia-settings still there, but still for some reason on boot just refuses to load it. 

This is where it gets odd, if I simply exit to console, log in and startx manually from this point -- it appears to load fine (and is how I'm typing this post now incidentally). 

Some other information of things I've already tried/odd occurrences are: when first trying jaunty i used ext4 and encrypted home from the alt installer, that's when i first realized I had this problem and tried to fix it with updating to the newest 185.x drivers that I was used to installing/configuring in ibex without issue, that didn't seem to help and i found a few other issues with ext4 that made me decide I wasn't ready for it, so i'm now working with a clean amd64 jaunty install with ext3 without any home encryption, and without even touching any beta drivers simply using the 180.44 that is supplied through the 'hardware drivers' gui prompt. 

It's an ibuypower laptop this is occurring on, which is simply a compal hl90 barebones with an nvidia 9600m and core2 p9500 and intel wireless, i can get the exact specs if requested and will gladly post any type of logs or outputs that may help

I also noticed occasionally that while having these graphical issues, if i decided to say boot into low-graphics mode ... my intel wireless simply wouldn't work ... I found it to be a *very* odd coincidence. 


anyone that can shed *any* type of light on this for me would be greatly appreciated, it's been kind of hell trying to troubleshoot it myself. I just cant seem to grasp why it wont load the gdm like normal, but if i startx myself it will load just fine, not really my area of expertise. thanks again in advance

---

### Post by punzada on 2009-05-06
just going to bump this once to see if it ends up helping anyone else with a similar problem

---

