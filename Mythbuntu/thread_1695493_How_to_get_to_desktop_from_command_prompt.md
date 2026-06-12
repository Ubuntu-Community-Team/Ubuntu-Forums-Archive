---
title: "How to get to desktop from command prompt?"
date: 2011-02-26
forum: Mythbuntu
---

### Post by vskatusa on 2011-02-26
I installed the backend/frontend combo. When I rebooted the desktop came up. However when cold shut down the computer and restarted again I get the command prompt! How do I get to the desktop from command prompt? Sorry for this newbie question!

---

### Post by abn91c on 2011-02-26
startx

---

### Post by winewood on 2011-02-28
Lets preface this by saying I used the Mythbuntu install.

This could mean a few things.  I got this when I screwed up my grub booter and I was left having to login manually.  If you are not logging in manually, and you didnt see a boot option for the kernel.. I had to run the following:
```
apt-get --reinstall install grub
update-grub
```

and then my system booted properly into my desktop.

If you are auto logging in, but not getting your desktop on a Mythbuntu installed system, I used:

gdm start

---

