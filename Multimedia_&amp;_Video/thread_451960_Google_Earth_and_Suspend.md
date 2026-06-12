---
title: "Google Earth and Suspend"
date: 2007-05-22
forum: Multimedia &amp; Video
---

### Post by mwacky on 2007-05-22
Google Earth is working great on Feisty and an Hp pavilion zv6000, problem is I close the laptop lid, which causes the computer to suspend mode, and when I come back to it Google Earth will not fire up, it hangs with the splash screen up and does not use any cpu.  Nothing is displayed in the terminal, and I eventually just have to kill the process.  If I restart it will work fine.  Any Ideas?  Something might be happening to my graphics card when I suspend?

---

### Post by magicfab on 2007-05-23
I would suspect wireless not coming back to life. Are you bale to access any network ?

---

### Post by mwacky on 2007-05-24
Wireless is fine.  Thanks though!  Everything is operating normally after coming out of suspend mode, I'm guessing something happens that affects the graphics card when I go into suspend, but I really don't use any other graphics intensive programs like GE to verify or know how to diagnose the graphics card problems, I'm using a hp pavilion with the ATI Radeon Xpress and getting that to work was a pain, have beryl and envy installed...

---

### Post by mwacky on 2007-06-12
Anybody out there experiencing the same issues with a laptop?  Any advice on testing the graphics card after suspend?

---

### Post by mwacky on 2007-07-02
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/84991](https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/84991) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Finally solved this problem thanks to launchpad.  The problem is with the video card.  I am running an ATI Radeon Xpress 200M, if you are having a problem with suspend, edit the /etc/default/acpi-support and change the settings.

```
gksudo gedit /etc/default/acpi-support
```

change the following:
```
SAVE_VBE_STATE=false
POST_VIDEO=true
USE_DPMS=false
```

---

### Post by kyle01 on 2007-07-03
> 
SAVE_VBE_STATE=false
POST_VIDEO=true
USE_DPMS=false


Thanks a lot! This has fixed the problem (Google Earth not running after resume from hybernate mode) for me. I am running Kubuntu 7.04 on a Toshiba Satellite M30x (Ati Mobility Radeon 9700)

Best regards,
Kyle.

---

