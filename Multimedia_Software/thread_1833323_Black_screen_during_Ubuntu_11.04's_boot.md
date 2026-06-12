---
title: "Black screen during Ubuntu 11.04's boot"
date: 2011-08-25
forum: Multimedia Software
---

### Post by Dr. James on 2011-08-25
Hello, my name is Dr. James and yes, I have a problem.

I've installed Ubuntu 11.04 and I love it. The only thing is that I have a black screen during the boot. I mean, I see the GRUB, I select from the grub, but then the screen turns black, until the login screen that appears just fine.

I have an NVIDIA card and yes, the driver is updated, I have full Unity functionality. I've tried uninstalling and installing it again, but the problem persists.

Notice that when I shut down my PC, the boot screen appears ok. It's just at the boot that the problem exists.

Could anybody help me? Thanks in advance.

**Dr. James**

---

### Post by Mark Phelps on 2011-08-29
Maybe the reason that no one replied is ... what you'e seeing is  routine for 11.04.  I've been using Ubuntu versions for years, and the way I know that 11.04 is FINALLY getting ready to show a desktop is when the screen turns from dark grey to black.

If the desktop is OK otherwise, this is just something you have to live with in 11.04.

---

### Post by BicyclerBoy on 2011-08-29
It is not normal..but the splash screen (plymouth) seem to get broken by updates on a regular basis.
[https://wiki.ubuntu.com/Plymouth](https://wiki.ubuntu.com/Plymouth).
Works well most of the time with my nVidia & intel graphics PCs.

The nVidia & AMD proprietary drivers do **not** provide any console framebuffer or non-X server screen support.

Apart from the plymouth debug options; there are VGA mode & vt handoff options in GRUB.
How these interact with plymouth is unclear (to me).

---

### Post by Dr. James on 2011-08-31
> **Mark Phelps said:**
> Maybe the reason that no one replied is ... what you'e seeing is  routine for 11.04.  I've been using Ubuntu versions for years, and the way I know that 11.04 is FINALLY getting ready to show a desktop is when the screen turns from dark grey to black.

If the desktop is OK otherwise, this is just something you have to live with in 11.04.

Yes, that's exactly what happens. Isn't there a way to fix the boot? Btw, I'm not using the propetary drivers, but the free ones (I've used the first ones but the problem persists).

---

### Post by oscarivera9 on 2011-09-15
What is it exactly that you want to see between Grub and login?  Is it the usual 'Ubuntu 11.04' screen with the dots that indicate the OS is loading up?  That's the only thing I can think of that you are asking about.  I used to see that screen in previous releases, but now I see it very briefly (for like 2 seconds) right before the login screen.  However, the time it takes to go from Grub to login is under 5 seconds, so I just figured that the boot screen was slower than the operating system.

---

