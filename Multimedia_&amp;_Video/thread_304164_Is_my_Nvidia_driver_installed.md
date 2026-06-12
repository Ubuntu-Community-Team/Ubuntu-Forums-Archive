---
title: "Is my Nvidia driver installed?"
date: 2006-11-21
forum: Multimedia &amp; Video
---

### Post by Dave54 on 2006-11-21
In short:
I followed [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") to install my Nvidia graphics card. It failed and the x server could not load. I restored my xorg.conf file and my desktop works again, but I have the Nvidia splash screen at start up. Does this mean my Nvidia driver is installed?

I'm running Ubuntu 6.10 Edgy Eft, a clean original install.
My graphics card is "NV34 [GeForce FX 5200]" according to Device Manager.
EDIT: I have "linux-image-2.6.17-10-generic" and "linux-restricted-modules-2.6.17-10-generic" installed. I did not install these, they were installed by default. (Should I install others?)

Here is a step-by-step list of everything that I did.

Using synaptic, install nvidia-glx and nvidia-glx-dev
```
sudo nvidia-glx-config-enable
``` came back with an error. So I used ```
sudo gedit /etc/X11/xorg.conf
``` and under Driver, changed "nv" to "nvidia".
Now ```
sudo nvidia-glx-config-enable
``` complained that my xorg file has been changed, so I used ```
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
```
Then ```
sudo nvidia-glx-config-enable
``` worked and I hit ctrl+alt+backspace. The x-server couldn't load even after rebooting.
Finally I used ```
cp /var/backups/xorg/xorg.conf.2006-11-20-11\:51\:47 /etc/X11/xorg.conf
``` to restore my previous settings. However, now I have the Nvidia splash screen at start up. Does this mean my Nvidia driver is installed?

Can anyone please tell me what is the state of my computer or where to go from here?

---

### Post by Jimmey on 2006-11-21
If the nVidia splash screen came up, then you're probably okay. 

I've forgotten how to check...

Maybe try > glxgears -printfps
If you get under 500, then no.
If you get nearer 2,000, then yep :-P

---

### Post by Dave54 on 2006-11-21
If it runs and I don't touch it, it gets as high as 1068 fps. However, if I move around the window or other windows, it drops to about 20 fps.

Does anyone know of a way to see the speed of a processor, amount of ram, speed of graphic card, ram on graphics card, etc. so I can see if my computer is just that slow?

---

### Post by Martin A on 2006-11-21
> Is my Nvidia driver installed?

Type glxinfo in the terminal. You should get loads of crap in the terminal window.. look for the part that says "Direct Rendering", if this has a yes, the nVidia driver is working, if not, then maybe the driver isnt installed correctly....

hih

Martin

---

### Post by Dave54 on 2006-11-21
Thanks Marten.

I tried "glxinfo" and got a "yes" for "direct rendering". I have no idea what my computer did, but I guess my driver is installed OK. I'll just remember what I did in case I run into trouble in the future.

---

