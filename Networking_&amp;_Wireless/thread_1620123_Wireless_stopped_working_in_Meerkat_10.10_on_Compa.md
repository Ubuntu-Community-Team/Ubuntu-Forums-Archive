---
title: "Wireless stopped working in Meerkat 10.10 on Compaq Presario CQ60-419wm"
date: 2010-11-12
forum: Networking &amp; Wireless
---

### Post by FetchDoggie! on 2010-11-12
Hello Friends.  I'm an Ubuntu newbie.  I recently installed Maverick Meerkat (dual booting it with Windows 7) and while the wireless worked for a few days, it recently stopped.

I have a compaq presario CQ60-419WM.

I've been looking through the wireless troubleshooting guide when I came to step 3.2, which suggested that I take my problem to the forums.

When I run the 'rfkill list' command I get the following:
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

My wireless card still works in windows.  Though I know very little about Ubuntu, from reading other threads and the troubleshooting guide it seems that there's nothing wrong with my hardware or the driver, but something else is not allowing my wireless card to function.

Any help would be appreciated.  Thank you in advance.

---

### Post by FetchDoggie! on 2010-11-12
Ok, looks like I posted my problem to the forum too soon.

I ran 'rfkill unblock wifi' and my wireless card started working again.

I then edited /etc/rc.local and added the above command to it.  I'm new to linux, but I guess /etc/rc.local is a script that runs on bootup?

Anyway, wireless internet works now.  Success!

---

### Post by grahammechanical on 2010-11-13
rfkill list showed Soft blocked: Yes. So, the wireless device was switched off by software. the command rfkill unblock wifi switch the device back on. Thank you for informing the forum of the solution. Please mark your post as solved.

Regards.

---

