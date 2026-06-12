---
title: "nvidia glx complete freeze"
date: 2006-06-16
forum: Multimedia &amp; Video
---

### Post by boronk on 2006-06-16
Hello,

I have a freshly installed Dapper Drake on a Dual Opteron Workstation with a GF6600 GT Graphics Card.

My System freezed sporadic completely. I have tried various Boot Paramaters and nvidia settings in my xorg.conf, but that did not help. 

So I investigated a little bit further:

If I use a default kde account I can use programms like Google Earth or glxgears without any problems. They run accelerated as they should.

Now, if I start kpager, that is that little virtual screens tool for kde which kann embed little screenshots for the running windows, everything is ok UNTIL I activate the "little screenshots" by selecting "Pixmaps" as Windowtyp. Normally, the system freezes shortly after that, if a GLX-App is running. And with freeze, I mean no remote ssh-login, no keyreaction, no logwriting, nothing.
If no GLX App is running, then I have sporadic freezes with the pixmap-feature.

Not so ddeply tested is the effekt of gkrellm, which shows up the same freezes at least sometimes.

So, I don't think this is a AGP or something problem but more a GLX/nvidia problem with a broken binary driver. This problem didnt occur with Breezy.

---

### Post by tofudrifter on 2006-06-17
i may have had a similar problem, after installing and enabling nvidia-glx my system would within 5 minutes of login lock up with nothing working except mouse (needed to hit reset switch, ie no crtl+alt+backspace, crtl+alt+f1, etc). i followed the instructions on this page: 

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

specifically step 4 in the problems section. hope this helps
btw i got a geforce6600gt too.

---

### Post by boronk on 2006-06-17
As I read there this would mean disabling AGP completely. In addition to that, I had a _real_ freeze. No Mouse.

Not a solution.

And what is really annoying is, that the nvidia.ko is with the "restricted modules" an not seperate, so if I want to use my own, I have tu complete purge restricted modules...

These should be seperated.

---

### Post by tseliot on 2006-06-17
[QUOTE=boronk]As I read there this would mean disabling AGP completely. In addition to that, I had a _real_ freeze. No Mouse.[/QUOTE]
Please, try point for as the other user suggested and see if anything changes.

[QUOTE=boronk]And what is really annoying is, that the nvidia.ko is with the "restricted modules" an not seperate, so if I want to use my own, I have tu complete purge restricted modules...

These should be seperated.[/QUOTE]
That's the way Debian works (and therefore also Ubuntu).

I don't like it but I think it makes sense since the Nvidia module is a restricted module.

---

### Post by boronk on 2006-06-17
The Problem is not, that it is seperate from the kernel but that all restricted modules are in one big *.deb. They should be seperated in restricted-nvidia, restricted-madwifi, restricted-fritz and so on, so that I can uninstall the nvidia-modules without the need to uninstall the others.

If I would now have a wifi card with a restricted module, If I want to replace my nvidia.ko with newer ones from nvidia.com, I am also forced to compile my wifi module by hand which can be annoying.

Btw, I've reinstalled the original nvidia drivers and set the AGP-Speed manually to 4x. (Another point which sucks... why is this not a module-parameter or a xorg.conf option...) Now, it seems to be more stable... I had only one freeze since then...

---

### Post by tseliot on 2006-06-17
[QUOTE=boronk]The Problem is not, that it is seperate from the kernel but that all restricted modules are in one big *.deb. They should be seperated in restricted-nvidia, restricted-madwifi, restricted-fritz and so on, so that I can uninstall the nvidia-modules without the need to uninstall the others.

If I would now have a wifi card with a restricted module, If I want to replace my nvidia.ko with newer ones from nvidia.com, I am also forced to compile my wifi module by hand which can be annoying.[/QUOTE]
I agree with you

[QUOTE=boronk]Btw, I've reinstalled the original nvidia drivers and set the AGP-Speed manually to 4x. (Another point which sucks... why is this not a module-parameter or a xorg.conf option...)[/QUOTE]
Ask Nvidia developers about that

---

