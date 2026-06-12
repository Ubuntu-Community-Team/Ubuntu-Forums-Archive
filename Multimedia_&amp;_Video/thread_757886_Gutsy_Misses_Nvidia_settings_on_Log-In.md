---
title: "Gutsy Misses Nvidia settings on Log-In"
date: 2008-04-17
forum: Multimedia &amp; Video
---

### Post by pushin50 on 2008-04-17
I've looked but haven't seen posts on this particular issue:

1) installed GeForce 6200 card with restricted Nvidia drivers enabled

2) no problem with Nvidia user interface - set resolution to 800 x 600 to give large enough typfaces; did this in both Nvidia UI and in Gnome preferences

3) when I log in to Gnome desktop, particulary from cold boot, Linux sometimes fails to pick up the 800 x 600 resolution setting and opens in 1024 x 768

4) I can fix this simply by logging out and logging back in (without need to reboot). On the second log-in, Linux will apply the 800 x 600 setting I want.

Not a killer problem but can be a serious annoyance.

Can anyone explain this and suggest a fix?

Thanks

---

### Post by wolfen69 on 2008-04-17
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by pushin50 on 2008-04-17
That worked.

Thank you so much!

---

### Post by pushin50 on 2008-04-18
Sorry . . . on further checking, did not work.

Same issue.

---

