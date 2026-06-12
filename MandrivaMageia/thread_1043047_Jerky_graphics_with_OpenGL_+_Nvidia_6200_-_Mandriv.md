---
title: "Jerky graphics with OpenGL + Nvidia 6200 - Mandriva 2009"
date: 2009-01-18
forum: Mandriva/Mageia
---

### Post by BigSilly on 2009-01-18
Hi there. I've posted this up in the Mandriva forums, but they seem to be down right now, so I'm hoping someone here can help.

I re-installed Mandriva 2009 KDE4 yesterday after having these issues a while ago, but they even though it was fine before switching off the problems have arisen again today. How, I don't know. Basically I'm using the latest Nvidia driver available from Mandriva (180.22) and I'm getting juttery graphics when using OpenGL applications. Chiefly, I'm thinking of Mupen64Plus 1.5, and Gens/GS, both from the PLF repositories, and both use OpenGL. I had this issue on the last Nvidia driver too. I actually don't think the driver is to blame, though I can't imagine what else it could be.

The performance is really slow and stuttery, and the sound is similarly affected too. I should mention that I have a monitor that Linux has problems with. I have to manually add an option to the xorg.conf with every distro I install. I've acquired the EDID.bin file, and I have to point xorg at it like thus -
```

Option         "CustomEDID" "DFP-0:/home/username/Nvidia/edid.bin"
```

If I don't do this the monitor has no output. This is fine for almost every distro, but with Mandriva 2009 I have had issues with OpenGL as above. I also have to add the autostart option nvidia-settings -l to Mandriva too, so it remembers my vsync settings etc.

Can anyone help me with this issue on Mandriva? I've tried all sorts of distros recently, but I still end up back on Mandriva simply because I love it so much. It's always been my no.1 dual boot option for years alongside my Ubuntu main install. I really don't want to change to something else. 

Thanks all.

---

### Post by BigSilly on 2009-01-18
Bloody idiot! I've found the problem, and it's simply that the refresh rate was set to "auto" rather than the 60hz it should be at. Good grief, I'm getting worse at this! I spent ages trying to find the solution!

All seems to be fine now. Always one thing you forget to do isn't there? Glad my Mandy's back anyway. Thrilled with it. :biggrin:

---

### Post by BigSilly on 2009-01-18
What the...

It's gone all juddery again. It was OK when I left it. What the hell is going on? If anyone has any ideas please let me know.

I'm fed up with it.

---

### Post by BigSilly on 2009-01-19
Sod it. Installed the Gnome edition instead today. Hopefully, that'll be better...

/crosses fingers

EDIT: 24 hours later, all is well with the Gnome edition. Thank gawd for that. :biggrin:

---

