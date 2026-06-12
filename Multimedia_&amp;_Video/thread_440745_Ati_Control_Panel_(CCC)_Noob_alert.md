---
title: "Ati Control Panel (CCC)? Noob alert"
date: 2007-05-11
forum: Multimedia &amp; Video
---

### Post by trajik78 on 2007-05-11
I'm trying my hands at Linux again to see if I can finally break the barrier and join the other side :D

everything is installed properly, and easily got the Ati driver installed via the driver Ubuntu v7 came with. I'm simply perplexed on how to install the Catalyst Control Pannel (CCC.) I downloaded the latest "Driver package"? from Ati's (AMD) web site but have no idea on how to extract or run the installer. I'm so used to simply double-clicking it in order to install.

Q2 - whats the Linux equivalent to Windows Device Manager.

tx!

---

### Post by crispy_420 on 2007-05-12
ATI Driver howtos:

[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

---

### Post by trajik78 on 2007-05-12
yeah went through that page and as it got the driver installed it doesnt explain as to how to install CCC control panel (if there is such a thing.) 

...i may be wrong but command line code is like reading Chinese to me, so any quote that has "sudo" in it is like working Pi out in my head, heh.

Linux is getting a bit easier to understand although it still feels some what like a jackhammer continuously pounding a hole into my head.

---

### Post by 3rdalbum on 2007-05-12
I thought the Catalyst Control Panel was Windows-only? I also thought it was something the ordinary user shouldn't mess with.

There is the "fglrx-control" package, which installs a very basic control panel. However it doesn't add itself to the menus, so you have to create a menu item that runs the command:

```
fireglcontrol
```

---

### Post by airflow on 2007-09-01
Hi!

I tried to install and use the ati control panel (installed fglrx-control via synaptics), but when I try to run it, I get the error-message "**Driver does not provide the FireGL X11 extensions! Panel components will operate only partially.**" The control-panel which comes up then is completely useless and just gives the name of the graphics-adapter, nothing more. I use the binary drivers of ATI (which I enabled via the restricted drivers manager). The drivers work well (I also have 3D-desktop functionality enabled).

Any idea what's the problem with the control panel?

Thanks,
airflow

---

### Post by likemindead on 2007-10-06
I'm getting the same error and my monitor says "Signal frequency is out of range."

Help?

**[COLOR="Red"]***EDIT: A big nevermind. If I would've just left things alone, I would've been fine! I reconfigured xorg back to ATI and all is well with my ATI Mobility FireGL T2.***[/COLOR]**

---

