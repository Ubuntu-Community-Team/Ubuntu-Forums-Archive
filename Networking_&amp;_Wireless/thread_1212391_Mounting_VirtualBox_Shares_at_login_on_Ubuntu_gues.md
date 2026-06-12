---
title: "Mounting VirtualBox Shares at login on Ubuntu guest"
date: 2009-07-13
forum: Networking &amp; Wireless
---

### Post by Zeedok on 2009-07-13
I am setting up virtualbox shared folders between an Ubuntu host and an Ubuntu guest (I know it's weird, I'm just getting it sorted so that I can boot into vista (I dual boot) and then fire my virtual ubuntu on my vista host.

I can mount the drives I need access to with the following commands at the terminal:
```

sudo mount -t vboxsf storage /media/Storage-Laptop
sudo mount -t vboxsf documents /media/Documents-Laptop
```

but I don't know how to have these automatically mount on login.

Do I edit the guest FSTAB - what should I right for full access read/write?
Should I write a script and have it run on login?

Will either of these work with Vista, when I have to use that??

Thanks

---

