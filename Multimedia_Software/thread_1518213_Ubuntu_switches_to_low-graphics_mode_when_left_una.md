---
title: "Ubuntu switches to low-graphics mode when left unattended for some specific time"
date: 2010-06-26
forum: Multimedia Software
---

### Post by etdsbastar on 2010-06-26
Hello Friends,

When I leave my computer and  later return, depending on how long I've been away, I find the  screen-saver running, the screen turned off, or the computer suspended, i get the error as specified below on a black screen:
> [COLOR=Navy]Ubuntu is running in low-graphics mode.

Your screen, graphics card, and input device settings could not be  detected correctly. You will need to configure these yourself.[/COLOR] The message gives several options.  Despite some experimentals, The only solution which I have found is to reboot and everything becomes fine as before.

Do you have any idea what is happening or, better, how to fix it?

I have Lucid 10.04.

---

### Post by etdsbastar on 2010-06-26
bump

---

### Post by weigh2tall on 2010-06-30
I get the same problem with an Intel GMA 3100 video card, but I've noticed (and I'm still testing) that if I leave just Rythmnbox running, it won't do this.  I left Thunderbird running last night with no issues this morning.  

I think it might have something to do with Firefox, as it has seemed to fail immediately after turning the screen off if I leave Firefox open.  

I also turned off the "password protection" on the screen saver to see if that helped (not by itself)

Can you see if your experience is similar? I'm on a desktop.

---

### Post by etdsbastar on 2010-07-01
bumping topic after waiting for a long time...

---

### Post by etdsbastar on 2010-07-01
> **weigh2tall said:**
> I get the same problem with an Intel GMA 3100 video card, but I've noticed (and I'm still testing) that if I leave just Rythmnbox running, it won't do this.  I left Thunderbird running last night with no issues this morning.  

I think it might have something to do with Firefox, as it has seemed to fail immediately after turning the screen off if I leave Firefox open.  

I also turned off the "password protection" on the screen saver to see if that helped (not by itself)

Can you see if your experience is similar? I'm on a desktop.

I am too on desktop and still the problem persists... no proper solution... till now...

---

### Post by JonnyRocket on 2010-07-25
I'm also experiencing this problem as well.  Its quite annoying.  Has anyone confirmed that FireFox is causing the problem?  I'm not 100% i'm leaving it open, but its a good possibility.

---

### Post by jerrykenny on 2010-07-25
Something must be repeatedly crashing your xserver . . . . 


Can you check your log files for your xservers and see if anythings popping up there ? ideally, see if anythings common to the the guys having this problem.

I wouldnt rule out the highly-fancy-3d-screen savers even, some of them used to make the processor work surprisingly hard. . .. try and go for a blank screensaver and see if that cures it.

---

### Post by JonnyRocket on 2010-07-26
I changed my screensaver back to just the little Ubuntu graphics floating around and it seems to have cured it.  I had it on the one that had the name and version floating around in 3d-ish.  Must be a bug there somewhere.  Easy fix, but still a little concerning.

---

### Post by weigh2tall on 2010-07-29
I don't think that it's Firefox itself because sometimes FF has been left open and I've not had problems the next time I come back, but last night I was watching YouTube and having a terrible time with lag in Flash Player.  (I restarted my modem, firewall and Firefox to no avail).  I'm pretty sure that I closed FF when I went to bed, but this morning when I got up Ubuntu was in 'low graphics mode'. I chose the option to 'Run once ...' and just for giggles tried Youtube again.  It was fast and what you'd normally expect.  Not sure if it's related.  

Can you describe how to get the x logs info you're talking about?  

This is my 4th or 5th distro of Ubuntu on this computer and the first to have this problem.  It's also the first that I haven't customized 'X11' to give me a higher screen resolution on my monitor.

I'm using the GL Slideshow as my screensaver.

I found this in the /var/log/Xorg.0.log file:

```

(II) UXA(0): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): No memory allocations

Fatal server error:
Failed to submit batchbuffer: Input/output error

```

---

### Post by nairda on 2010-10-16
I can confirm this happening to me too, the only way to get it back is through a reboot.

In a related note, it has also happened while using some intensive graphics like with Mathematica's plotting abilities.

---

### Post by weigh2tall on 2010-10-18
I have not had this issue again since switching my screensaver.  I'm using the F-Spot favorite pictures screensaver now.  I had been using one that was using OpenGL I believe.

---

### Post by Marc Higgins on 2011-04-25
I can confirm this problem magically disappeared for me after I dropped the GL screensaver. I miss the matrix screensaver but as my friends say after +10 years it was time for a change anyway!

dell-inspiron-640m:~$ lspci | grep Graphics
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

---

