---
title: "Laptop's LCD has gone!"
date: 2009-02-21
forum: Multimedia Software
---

### Post by Daniel Song on 2009-02-21
Hi,

I am using Fujitsu laptop and DELL LCD monitor for dual screen. Somehow, I could get dual monitor setup.

Suddenly, I wanted to turn off laptop's lcd and keep external DELL monitor on. So, Using System->Preference->Screen Resolution, I changed main laptop lcd off and keep external DELL on.

However, both my laptop and external DELL monitor's backlights have gone and never come back.

I did CTRL+ALT+BACKSPACE to logout,and tried to login, but again two backlights are gone also. I couldn't see anything, and I couldn't do anything since all monitors are gone.

I am writing other computer to get any help about the problem I have.

Could you help this out for me, please?

Thanks,

---

### Post by xc3RnbFO8P on 2009-02-21
Did you try Save Mode or Live Disk?

---

### Post by damis648 on 2009-02-21
Shut the computer down and reboot. At the GRUB menu (press Esc to view it if you don't see it) select the topmost 'recovery mode' option. When it boots a menu will show up and there will be an option to attept to fix Xorg (xfix). Choose that option and then choose 'Resume Normal Boot' and you should be okay.

---

### Post by Daniel Song on 2009-02-21
Thank you for the information.

Thing is that I don't know how I can manipulate xorg.conf. I can't find where it turns off. Could you give me a little hint, please?

---

### Post by Daniel Song on 2009-02-21
I found how I revert the new setting for video.

```

# sudo dexconf

```

That's it. Then, it will create xorg.conf in /etc/X11/ for default setting. So, if you screw up with your screen setup, you can return to safe one.

---

