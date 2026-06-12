---
title: "GDM asking for password without end :-("
date: 2011-06-10
forum: Mythbuntu
---

### Post by jonatangee on 2011-06-10
Hello,

I found Mythbuntu as a perfect solution for my media center. I installed it and now I'm trying to make it work.
But after booting, it shows me the login prompt (although autologin is activated). If I put a wrong password, it states that it is wrong. If I put the right one, the screen becomes black and then the login prompt comes back without any message.
I tried to login about 30 times without success.

When I'm logged on a tty, the login list on GDM even shows me a green dot stating that I'm already logged in, but it doesn't work better.

The only "solution" I could find was to logout from GDM, go back to tty and launch sudo startx. Then I can find the MythTV frontend from the menu.

Could someone help me fixing that problem ?

Thanks !

Jonatan

---

### Post by superm1 on 2011-06-10
It sounds to me like X is crashing after it gets logged in.

Can you see anything about crashes in /var/log/Xorg.0.log /var/log/Xorg.0.log.old dmesg or /var/log/syslog?

---

### Post by agamotto on 2011-06-10
I am not firing on all cylinders today, so I am not sure this will help... I once had a similar problem, and if memory serves, I deleted the ICEauthority file... I just can't remember currently where it hides!

---

### Post by TelepathicSpy on 2011-06-12
Disabling composite via
> nvidia-xconfig --no-composite
did the thing for me (surely this works only with a nvidia card and the nvidia driver).

---

