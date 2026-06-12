---
title: "[SOLVED] ATI drivers nightmare"
date: 2008-09-26
forum: Multimedia Software
---

### Post by Azazel on 2008-09-26
I have an ATI Radeon X300 and had it running great with fglrx drivers and xgl. For some reason, (dont ask why) I tried installing the envy drivers and control panel and they did not work. I removed the new drivers and as far as I can tell had my system the same as before. However the performance was extremely poor and I could also not adjust the resolution. When I go to 'System -> Preferences -> Screen Resolution' I get an error that says the X server does not support the xRandR extension. After trying to reinstall the drivers several times without different results, I tried installing the drivers from the AMD website. However I still have the same problems. Also Catalyst Control Center says I do not have ATI supported drivers installed.

What happened!?! I am not sure what my next step should be, someone please help!

Im using Hardy, Gnome and 2.6.24-19-generic kernel

---

### Post by peakshysteria on 2008-09-26
what does:
```
fglrxinfo
```
give you?

---

### Post by Azazel on 2008-09-26
fglrxinfo gives me:

```
display: :1.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.3)
```

---

### Post by peakshysteria on 2008-09-27
Meaning the ATI driver isn't installed at all. Try to have a look at:
[* BinaryDriverHowto * ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

If this doesn't help install [Envy]("http://albertomilone.com/nvidia_scripts1.html") via synaptic and install the driver with it and you should be good.

NB! If you are good with the terminal **[the Ubuntu Hardy Installation Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.8_or_8.9.29")** (method two) is the best and most successful alternative for most ATI users.

---

### Post by Azazel on 2008-09-27
Using Envy put me in the same situation, so i tried manual installation. At first i didnt think this would work because i thought i had already tried everything in the instructions. But there was one thing different. I had not been configuring aticonfig correctly. 

> Some people find that changes to xorg.conf don't get used by the driver. To force the ati driver to adopt changes made to xorg.conf, type the following command:

```
sudo aticonfig --input=/etc/X11/xorg.conf --tls=1
```


after editing aticonfig everyting worked great! including Catalyst Control Center and Screen Resolution.

Thanks for you help!

---

