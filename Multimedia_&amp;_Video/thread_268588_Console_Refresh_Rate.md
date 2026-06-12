---
title: "Console Refresh Rate"
date: 2006-09-30
forum: Multimedia &amp; Video
---

### Post by woekele on 2006-09-30
Hi,

This is not a standard 'omg, I dunno how to set my refreshrate + resolution' thread, please read on...

My display is fine once X is running (1280x1024@75Hz), but in the console and startup/shutdown splashscreen it gives an 'out-of-range' error.

I installed Edgy on my parrents PC (Sis 650 Memory Sharing Integrated Graphics, BenQ FP747 LCD screen, native at 1280x1024@60H, but can do 75Hz as well). 

When entering the live-cd, I got the normal menu, when choosing 'start Ubuntu', my monitor displayed 'out-of-range', so I waited a long time and when X started, it displayed normally again. I also tried save-mode, but that didnt change anything. At this time I hoped the out-of-range wouldn't happen again after installing on HD.

So after X started, I doubleclicked 'install' and that all worked fine. But every time I boot, reboot orshut down and the splash screens are suposed to show, or when Ishut down X and the console is suposed to show, I get the error 'out-of-range' again. So while Im in X, everything is fine, but if it goes to console-mode or splas-screen-mode, theres the error.

So apparently, the console/splashscreen is running on a refreshrate/reso by default that my monitor does not support. I did some research and found out the console uses framebuffer. According to the info I found, by adding the 'vga=XXX' behind the kernelbootline in the grub-menu.list, a user can change the resolution + colordepth the console uses. I entered what I wanted: 795 (1280x1024 on highest colordepth) but when booting, it said it didnt know the mode and asked me to press 'return' to see the available modes. So I did. It only showed 0F00 - 0F07... I tried them all, but all gave the 'out-of-range' again. I also tried with '791', also the same error.

So I guess the problem is not with the resolution, but with the refreshrate. I dont know how to change this though. I installed 'fbset', but its giving an error, 'Inappropriate ioctl for device' when trying to apply settings to one of the /dev/fbx's.

Sumarry: X works fine, console gives 'out-of-range' error.

How can I fix this?

Tnx.

Edit: I tried adding video=vesafb to grubline (it uses vesa VGA by default I think) with all kinds of modes behind it and now I can enter a console when X was started by doing alt + ctrl + Fx, but it's always at 800x600@60, no matter what I set. Also before X is loaded, and it's suposed to display the splashscreen, it still doesn't work (out-of-range instead of splashscreen). The shutdown-logo works, but it looks very messy first and then goes normal just before it shuts down.

Edit2: found some info about the splashscreen at [http://www.ubuntuforums.org/showthread.php?t=266175](http://www.ubuntuforums.org/showthread.php?t=266175) , apparently, theres a .conf file for it. I'll try playing with that next time I'm at my parrents.

But still, I think both the splashscreen (both booting and shutting down) and the console should work properly by default.

---

### Post by woekele on 2006-10-02
Bump? :(

---

### Post by rmjb on 2006-10-02
> **woekele said:**
> But still, I think both the splashscreen (both booting and shutting down) and the console should work properly by default.

Yeah, it should, but keep in mind Edgy is still beta, things are broken, the devs know things are broken and they're working to fix it. This forum is for Dapper support so you probably wont get much help here. You can repost this in the Edgy Beta forum though. Or better yet see if there's a bug for this in Launchpad and give your experience on it, it'll help iron out this bug.

But by the time Edgy is released, this will be ironed out.

- rmjb

---

### Post by rmjb on 2006-10-02
Also, if your parents aren't tech savvy, they might be I dunno, it might be better to install Dapper for them since that's final and stable. Then when Edgy comes out you can upgrade properly.

- rmjb

---

### Post by woekele on 2006-10-02
Okay, fair enough, I'll try Dapper next time on their PC. :)

---

### Post by lennox on 2006-10-23
I got a similar problem too, but already in Dapper. My Monitor displays the Console framebuffer at 1280x1024 24 bit, but the refresh rate is wrong. This makes the console blurred and also make my display auto-configure everytime I switch between console and X, which shows an ugly message in the center.
Adding  video=vesafb:1280x1024-24@75 did not help.

---

