---
title: "Nvidia Driver 1.0-9629 issues"
date: 2006-11-12
forum: Multimedia &amp; Video
---

### Post by Elimist on 2006-11-12
'Ey, I just signed up here. I just started using Kubuntu 6.10 probably about two weeks ago. I've had a couple rough spots with it here and there.

Current issue:
I have a Nvidia GeForce 7300 GS
I installed the new nvidia drivers. And now, every time I restart my computer it boots in the console and I can't load the X Server.
Then I type in startx and I get an error message telling me I have no compatible screen.
Then I just reinstall the driver, I restart KDM, then everything works fine.

I'm installing the driver from the Nvidia Website.

I'm also going to attach my xorg.conf if anybody wants to see it.

---

### Post by CITguy on 2006-11-12
I had the same problem. I found out that it was due to a misconfiguration of the xorg.conf. You have to reconfigure the xorg.conf by entering the following command as superuser:

dpkg-reconfigure --force xserver-xorg

(there are two dashes in front of "force")

---

### Post by Elimist on 2006-11-13
Problem solved.

What I did was uninstalled the nvidia-kernal-common package.
The error I was getting said it was a different version than the driver. I uninstalled that package, then reinstalled the driver, restarted my computer again and it started up just fine.

---

### Post by budman21901 on 2006-11-13
Thanks for this.  I was having the same trouble.  Looks like i was in the perfect place at the perfect time.  Geforce fx 5500 here if anyone else is searching.

---

