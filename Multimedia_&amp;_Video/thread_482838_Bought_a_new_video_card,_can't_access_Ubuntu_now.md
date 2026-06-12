---
title: "Bought a new video card, can't access Ubuntu now"
date: 2007-06-24
forum: Multimedia &amp; Video
---

### Post by Archel on 2007-06-24
I used to have a Geforce2 mx/mx 400. I bought a Radeon 9550 now and because I had NVIDIA drivers on Ubuntu, I get an xconfig error every time I try to log into Ubuntu. Does anyone know of a way to remove the old Nvidia drivers so I can log in?

---

### Post by ubu-for on 2007-06-24
Start Ubuntu in recovery mode, login and type the following.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Archel on 2007-06-24
> **ubu-for said:**
> Start Ubuntu in recovery mode, login and type the following.

```
sudo dpkg-reconfigure xserver-xorg
```

Thanks. I'll try it out.

---

### Post by Archel on 2007-06-24
> **ubu-for said:**
> Start Ubuntu in recovery mode, login and type the following.

```
sudo dpkg-reconfigure xserver-xorg
```

Just tried it. I reconfigured it but I got the same error again afterwards. Is there any way to just reset the xconfig to the default configuration it comes with when you first install it?

---

### Post by ubu-for on 2007-06-24
> **Archel said:**
> Is there any way to just reset the xconfig to the default configuration it comes with when you first install it?

You already did.

Please post your xorg.conf. You can find it at "/etc/X11/".

```
gedit /etc/X11/xorg.conf
```

---

### Post by swudee on 2007-10-13
Hey it worked for me.
I had to answer a LOT of questions for the Xorg set up but rebooted and away she went.
Thanks Ubu-for 
I knew the command was something like that, just hadn't had to use it before!

---

### Post by ubu-for on 2007-10-13
> **swudee said:**
> 
Thanks Ubu-for 


You're welcome!

---

### Post by Fingolfin on 2007-10-13
I have once had Radeon 9550 card and was unable to activate OpenGL rendering/acceleration with ATI drivers on Ubuntu (no matter what I tried). Gave up at some point and took Nvidia card instead.
To check if OpenGL has been activated, type in the terminal:

% glxinfo 
or
% glxinfo | grep rendering

if it says something like Rendering: Yes, you are all right there.

% glxgears
will run a nice animation to confirm this.

---

