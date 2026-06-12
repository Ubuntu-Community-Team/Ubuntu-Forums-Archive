---
title: "where did my gui go ?"
date: 2009-11-11
forum: Multimedia Software
---

### Post by nss0000 on 2009-11-11
Gents:

Running x32_Jaunty on AMD_965/MSI_gd70/BFG_9800-gtx+

At one time everything ran "normally ... then I obeyed prompts and did a partial_update. Stuff got hosed.

Now when I boot, I boot into text_screen. I give LOGIN / PASSWD and type <startx> ... and up comes the expected Jaunty GUI. AND a perfectly working NV_gui for controlling the graphics card & monitor display complete with the latest 190.47 NV driver.  

sys-> pref -> display assures me it is not compatible with the current graphics driver. I can find GDM in /etc. Yes I'm also missing the <control> button in the upper r.h.s. LOGOUT & SHUTDOWN now reside under the <<system>> control_name. 

I don't so much mind the retro ( like RedHat_6.0 ) boot, or magically appearing native NV_drivers as I am bewildered by having no idea why Jaunty control-stuff works or does not work.  

My 2-yo UBUNTU x64-8.04.1_LTS running my AMD_5400+ kit has never behaved at all like Jaunty.

---

### Post by HappyFeet on 2009-11-11
Doing a partial upgrade with a graphics driver that does not use DKMS is most likely the reason why things got hosed. That's why it is recommended to use the nvidia driver as suggested in system>administration>hardware drivers. You could try recompiling the nvidia drivers via command line, but other than that, it seems your "partial upgrade" did not take too well.

---

### Post by nss0000 on 2009-11-12
> **HappyFeet said:**
> Doing a partial upgrade with a graphics driver that does not use DKMS is most likely the reason why things got hosed. That's why it is recommended to use the nvidia driver as suggested in system>administration>hardware drivers. You could try recompiling the nvidia drivers via command line, but other than that, it seems your "partial upgrade" did not take too well.

Yes -- after scrambling to make it work well myself, I foolishly allowed Jaunty to do its advised "upgrade". The NV engineers had performed a clever integration which UBUNTU promptly destroyed. Silly me.

Well yes, I do pay (opportunity cost ) Jaunty to manage its own business ... a casual Linux_lusr can hardly be expected to do more. I'm not the only poster to have "gone the extra mile" ... and paid for it.

But, there's HOPE !! Now <update manager> lists a HUGE list of new(er) software to be installed ... including a new(er) kernel version. The old system remains blissfully ignorant of the havoc it caused ... but I will carry on. No telling under what circumstances or OS I will make my next post. May well be that Jaunty will become the VISTA of the Linux world.

---

### Post by nss0000 on 2009-11-12
> **nss0000 said:**
> Yes -- after scrambling to make it work well myself, I foolishly allowed Jaunty to do its advised "upgrade". The NV engineers had performed a clever integration which UBUNTU promptly destroyed. Silly me.

Well yes, I do pay (opportunity cost ) Jaunty to manage its own business ... a casual Linux_lusr can hardly be expected to do more. I'm not the only poster to have "gone the extra mile" ... and paid for it.

But, there's HOPE !! Now <update manager> lists a HUGE list of new(er) software to be installed ... including a new(er) kernel version. The old system remains blissfully ignorant of the havoc it caused ... but I will carry on. No telling under what circumstances or OS I will make my next post. May well be that Jaunty will become the VISTA of the Linux world.

Well well ... back again so quickly after the "update" ... all the previous problems remain. AND -- I have lost webcam and EVOLUTION function. Prolly boring emails from the ex-galpal this morning anyway. Let's hear-it for JAUNTY --- makes me think about that x64_Jaunty IMAGE-cd I burned before installing the "factory"_CD and wondering if I should give it a test. 

In other news, <Update-manager> continues to prompt for an upgrade to U_9.1 and I have nothing to lose. Perhaps if all_goes_well I'll be presented with a DOS_6.22 screen. Hasta-LaVista

:p

---

### Post by HappyFeet on 2009-11-12
I, and others find jaunty a pleasure to use. I suggest reinstalling, then updating, then locking it down. You should have no issues if you don't upgrade. Good luck.

---

### Post by nss0000 on 2009-11-12
> **HappyFeet said:**
> I, and others find jaunty a pleasure to use. I suggest reinstalling, then updating, then locking it down. You should have no issues if you don't upgrade. Good luck.

Well yes I'm eating_some_crow.

U_9.1 DLoaded, installed, scrubbed and rebooted without issue. A few simple tests shows no evident flaws. NV 190.47 driver installed. Utube, sound, webcam & email seem to function properly. No test yet on fullscreen DVDs. I am amazed.... 


As it should be.

---

