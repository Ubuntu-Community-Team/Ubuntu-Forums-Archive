---
title: "[SOLVED] Dual Monitors treated as one display... what am I doing wrong?"
date: 2008-02-08
forum: Multimedia &amp; Video
---

### Post by duwanis on 2008-02-08
Sorry if this is something that's already been addressed elsewhere in the forums... I've been nosing around for a while and can't seem to find anyone with a similar question.

I've installed Ubuntu on my work PC. I had a couple of issues, but eventually got everything working, including my two Dell 1280x1024 LCD monitors. The only problem I have is that the two screens are being treated as one display - if I try to maximize a window, it stretches across both screens, and anything that comes up centered (password prompts, and a lot of new windows, for example) is placed so that it straddles both monitors. I'd prefer that maximized windows stay on their respective screens, and that the indicated main monitor is the one that receives all the new centered windows.

I configured the setup using the System --> Administration --> Screens and Graphics item in Gnome.
Looking in xorg.conf (attached) it looks like it installed using Xinerama. I try running the nvidia-settings application, in the hopes of maybe enabling twinview, but it tells me that I'm not using the nvidia driver (although I clearly am, according to both xorg.conf and the restricted drivers manager).

I feel like I've got to be missing something simple, since this seems to be more of an application issue (since the displays are working fine, Gnome just isn't treating them as separate displays). Is it possible to do what I'm looking to do?

Thanks in advance.

---

### Post by duwanis on 2008-02-08
Well, I've done some more playing with... here are some more specifics in the hopes that it rings a bell for somebody.

When I try to run the nvidia-settings program, this is the error message I get:
"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

After running `sudo nvidia-xconfig` I can see that some changes were made to xorg.conf, but neither restarting the X server (Ctrl-Alt-Bksp) nor restarting the computer nets me any change in nvidia-settings behavior.

I also re-ran the envy install routine to no effect.

---

### Post by duwanis on 2008-02-11
Just to close this out in case somebody trips across it...
The reason I wasn't able to run nvidia-settings is because I had xserver-xgl installed. Once I removed that I was able to go and configure twinview in nvidia-settings and my problem was solved.

---

