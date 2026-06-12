---
title: "Weak performance of i810 driver in X - Need help!"
date: 2006-06-19
forum: Multimedia &amp; Video
---

### Post by rverrips on 2006-06-19
Hi

I'm running Xubuntu 6.06 on an Acer Aspire 1642WLMi, but the important thing to note is it uses the onboard (obviously, it's a laptop) Intel 915GM/GMS 910GML Express and/or 900GMA display adapter, which shares memory with the 512MB base of the PC ('parently a maximum of 128MB, as needed?)

The buildin LCD display resolution is 1280x800 - to get X to load the correct resolution I needed to** apt-get install 915resolution**, and all was great.  (This seems to be a common problem)

However the performance I'm getting under X is nowhere near as good as that experienced in by dual-booted WindowsXP.  I was trying for ages to get Counter-Strike to work under wine at a level comparable to Windows, and the wine (and Cadega) guys kept telling me it should be working fine, but it wasn't - Under X it was slow.  I tried a native install of Army Ops for Linux and again had the same weak performance when compared to the windows version of the same game ... Mmm, I started to wonder.

Yesterday I got the Matrix Box set for Fathersday and decided to watch a bit on the Laptop under Linux, and suddenly realised it was dropping frames and the overall experiece of Trinity kicking butt just wasn't the same.  I switched to Windows and the comparison was almost of day/night values, and under windows it was almost as if I was there, clear, crisp and seamless.

So I started digging into it, firstly trying different media players - I prefer Xine, but gave Totem and Mplayer a chance to redeem themselves ... same performance.

Hit the forums/irc and was told to try different "drivers" such as xv, or opengl, or vidix, but no real difference.  However I did learn that running **xine verbose=9 | grep frames** clearly shows the problem.  Out of 200 frames, average of 60 are discarded ... There's 30% of my movie I'm not seeing! :confused:

So I started thinking there's something wrong with my xorg.conf, but after various attempts and crashed xsessions, I have made peace with the fact that tinkering is getting me no better performance than **dpkg-reconfigure -dhigh xserver-xorg** did, and all the possible modules, such as DRI and GLX, are installed and running.

IRC/Forums again didn't yield much, except one guy saying I could try the Intel site for an updated driver (i810) ... There wasn't one (latest being 2004) but at least it's given me direction.

Does anybody out there know if a more optimised driver for the Intel 915 exists.  It seems to be a very popular laptop display adapter, but doesn't have much in the way of support on linux / X???  Seems most folk have problem getting the resolution working (915resolution being the saviour of that bug) and then are happy with the i810 performance?

Also, any ideas or guidance on howto better describe / identify / quantify my problem would greatly be appreciated.

Thanks

Yours

Roy

---

### Post by localzuk on 2006-06-19
According to [http://ftp.x.org/pub/X11R7.0/doc/html/i810.4.html](http://ftp.x.org/pub/X11R7.0/doc/html/i810.4.html) you can only get 3d acceleration if you use 16bit colour. Have you tried this?

---

### Post by rverrips on 2006-06-19
[quote=localzuk]According to [http://ftp.x.org/pub/X11R7.0/doc/html/i810.4.html]("http://ftp.x.org/pub/X11R7.0/doc/html/i810.4.html") you can only get 3d acceleration if you use 16bit colour. Have you tried this?[/quote]

Thanks for the reply localzuk - I believe this was however addressed by the Ubuntu/Xorg guys somewhere between breezy and the final release for dapper ... 

glxinfo reports my **Direct Rendering: Yes** while in 24bit colour (I've tried 16bit and it made no difference to performance issues)

Do you know of any other way to confirm 3D is ok - When I do **glxgears -fullscreen -printfps **I get around 105 fps.  I know glxgears isn't is benchmark, but I'm sure there should be a bit more than that coming through, no?

---

### Post by Juzz on 2006-06-21
Have you tried looking at Intel's hp?
Specifically:
[http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=1862&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=1862&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

---

### Post by rverrips on 2006-06-21
[quote=Juzz]Have you tried looking at Intel's hp?
Specifically:
[http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=1862&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21]("http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=1862&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21")[/quote]  
Thanks Juzz - Intel is only offering a generic versions of the i810 driver bundled with XFree86 version 6.8 (i.e. Sept 2004) as a download from what I can work out.

---

### Post by rverrips on 2006-06-28
This is SO weird - I was trying a beta of Windows Vista and proceeded to destroy my /boot partition for Ubuntu, which was easy enough to fix, but in the process I dropped down to the 386 kernel image.

So I logged in, and while running **apt-get linux-686**, I decided to browse the internet a bit and notice my PC was responding a lot quicker, windows were opening a lot faster.  So I tried my xine --verbose=9 and watched a DVD and smiled from ear to ear as only 2 frames in 200 were dropped!

Yippee!  All working (must be some update?) imaging how much better when I reboot into the 686 kernel (I do afterall have a Intel Centrino so 686 should be better, no?

NO! Problem re-occurs with the 686 kernel ... Boot in 386 Kernel and all is ok?

***So to summarize - This issue is only present with linux-image-2.6.15-25-686*** and present in neither linux-image-2.6.15-23-686 nor linux-image-2.6.15-25-386 ... I logged in malone Bug #51237 - If anyone can suggest how best I define the problem, please let me know

---

### Post by Hellkeepa on 2006-06-29
HELLo!

This is already well known, and reported as a bug.
For more information, please read this thread (and the post I've linked to).
[http://ubuntuforums.org/showthread.php?t=204100](http://ubuntuforums.org/showthread.php?t=204100)

Happy codin'!

---

### Post by rverrips on 2006-06-29
Thanks, that did indeed solve it!  

I marked the bug as a dup' to #30557 

You're the man Hellkeepa!

---

