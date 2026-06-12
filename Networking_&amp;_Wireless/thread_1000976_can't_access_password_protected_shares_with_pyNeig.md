---
title: "can't access password protected shares with pyNeighborhood"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by d_yat on 2008-12-03
So I've been trying to solve a minor problem I've been having with pyNeighborhood. Basically I'm trying to access some folders on my desktopPC from my laptop. I can mount folders that don't require a password, but not any that do (the "failed to mount" message appears).

Ok, yes, the simple solution would be to get rid of the password and allow anyone to access it. But I don't want to do that!

Help anyone?

p.s. other helpful info:
mount location is in my home directory.
doesn't work with SMB nor CIFS (unless password not needed)
yes I have smbfs, winbind, cifs installed, as well as midnight commander...
I can mount them if I am using WinXP on this laptop.

---

### Post by d_yat on 2008-12-07
no-one?

---

### Post by d_yat on 2009-08-29
haha, even I forgot about this. Still got this problem though.
So here's a long awaited BUMP.

---

### Post by ahood on 2009-08-29
Hello,

What version of Ubuntu are you using?

I have never used pyneighborhood. I have edited fstab to successfully automatically mount the shared drive every time the system boots and connected to the network.

If you are interested in the fstab method, then the following link may be helpful.

[https://help.ubuntu.com/community/ComprehensiveSambaGuide](https://help.ubuntu.com/community/ComprehensiveSambaGuide)

Reply with additional questions.

After using Ubuntu for the last 5+ years, It does seem strange to me that permanently mounting a shared directory is requires expert knowledge, where as temporarily mounting the same shared drive is quite easy using Nautilus. If you concur, perhaps vote for one of the solutions at the link in my signature below.

Hope this helps

---

### Post by d_yat on 2009-08-30
Yea, I don't want a permanent mount. pyNeighborhood is basically the updated version of LinNeighborhood (if you ever used that), where you can browse network shares, and then choose to mount/unmount whatever you want, whenever you want and use SMB or CIFS. That is why I like it.

Anyway, to answer your question. My laptop is running OpenGeu. Which is based on ubuntu but uses the E17 desktop with bits of Gnome too.
SO this means I use Thunar and not Nautilus, so I can't just browse the network like on ubuntu/Mint (or whatever uses nautilus)

I really like the pyNeighborhood method, and have considered using FUSE with thunar, but I'd rather not (yes, I'm stubborn!) as I prefer pyNeighborhood.

oh, just had a thought. Will let you know how this thought goes! Thanks for the idea anyway.

p.s. yea, it does seem silly that for a permanent mount one still has to manually edit files and not have a nice GUI to do so, a menu option would do!

---

