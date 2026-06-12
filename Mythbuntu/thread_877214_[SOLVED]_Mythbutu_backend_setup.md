---
title: "[SOLVED] Mythbutu backend setup"
date: 2008-08-01
forum: Mythbuntu
---

### Post by dmdbdd on 2008-08-01
Good morning:

The installation manual for 8.04 chapter 9.1, page 75, shows a backend setup screen. However it never tells how to activate this screen and I'm unable to figure it out, as I'm new to Linux.

Regards,

dmdbdd

---

### Post by newlinux on 2008-08-01
type:
```

mythtv-setup 

```
at a terminal or launch it from the mythtv configuration screen of Mythbuntu-control-center

---

### Post by dmdbdd on 2008-08-01
> **newlinux said:**
> type:
```

mythtv-setup 

```
at a terminal or launch it from the mythtv configuration screen of Mythbuntu-control-center
Good afternoon:

OK, I had already tried both of those. What I get is a big blue bordered screen asking for preferred language. Next is another big blue screen with a "No UPnP backends found". When I click on "OK" (the only option), I get another big blue "Database Configuration 1/2" screen. Completing these screens as best I know how, I get a whole screen of warnings: "Unable to locate theme engine in module_path 'pixmap'.

All I want to do is get a backend installed so I can test the front end to determine if MythTV is for me - I really think it is what I'm looking for.

Regards,

dmdbdd

---

### Post by newlinux on 2008-08-01
sounds like you have some other problems, but mythtv-setup is how you configure the backend and that is how you get the screen on that page in the manual. You might want to consider reinstalling. how did you install?

---

### Post by dmdbdd on 2008-08-02
Good morning:

OK, your question regarding how I installed may be the key. I have not installed anything yet. I'm trying to run the "Live CD Frontend". However according to the installation manual, this requires a master backend! This was the cause for my initial question. So maybe I can't get there from here? Maybe I have to do a complete install? Can you verify this.

Although I'm new to Linux, I have over 15 years experience as a computer consultant and Windows programmer - I'm usually very good about working through a problem, given adequate documentation. I'm dedicated to learning  Linux, so please bear with me.

Thanks,

dmdbdd

---

### Post by newlinux on 2008-08-02
If there is no backend installed, you certainly can't configure it, so there's your problem. The liveCD (and any mythfrontend) is intended to connect to an existing master backend. So yes, you'd need to install a backend. I'm not sure if you can install a backend in the liveCD session without installing the OS but I don't know for sure...

---

### Post by dmdbdd on 2008-08-08
This issue has been resolved - thanks to those who tried to help :)

Regards,

dmdbdd

---

