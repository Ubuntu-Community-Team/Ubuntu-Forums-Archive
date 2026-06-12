---
title: "Dual monitor"
date: 2010-04-24
forum: Multimedia Software
---

### Post by Vistz on 2010-04-24
I'm trying to use my second monitor so that it appears to be an extension of my original monitor. When I plug in my second monitor, it just mirrors my laptop screen. 

Here's what I got from lcpci
```

01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)

```

I downloaded EnvyNG but when I clicked to run it, it wouldn't open.

---

### Post by wojox on 2010-04-24
Have you gone into System > Admin > Hardware Drivers and activated the driver?

---

### Post by Vistz on 2010-04-24
> **wojox said:**
> Have you gone into System > Admin > Hardware Drivers and activated the driver?

Thank you. I can't believe I missed that.

---

### Post by wojox on 2010-04-24
If you want to configure it run:

```
sudo nvidia-xconfig
```

```
gksudo nvidia-settings
```

---

### Post by Vistz on 2010-04-24
> **wojox said:**
> If you want to configure it run:

```
sudo nvidia-xconfig
```

```
gksudo nvidia-settings
```

When I run ```
sudo nvidia-xconfig
```

I get
```
Using X configuration file: "/etc/X11/xorg.conf".

WARNING: No Layout specified, constructing implicit layout section using screen
         "Default Screen".


WARNING: Unable to find CorePointer in X configuration; attempting to add new
         CorePointer section.


WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: Unable to find CoreKeyboard in X configuration; attempting to add new
         CoreKeyboard section.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```

But I managed to configure my displays using the second command. I also have another question. Is it possible to display 2 different desktops using dual monitor display?

---

### Post by wojox on 2010-04-24
It's been about four months since I had dual monitors. I could never get it to work. You can add panel, add panel and add panel to put a panel on the other monitor. Then just delete the side panels.

---

### Post by Vistz on 2010-04-24
I think I got it but there's just one small thing. When I choose the "Separate X Screen" choice under Configuration, I am able to get 2 separate desktops. However, when I move from one desktop to another, I lose focus (as if I clicked out of the window) in the application I am running (Firefox).  Is there any way to prevent this?

---

### Post by wojox on 2010-04-25
Not sure. I could never get Separate X Screen to function properly. Why not just set up Twin-View? Then you have on screen with your panels and your other screen empty to run other apps in.

---

### Post by Vistz on 2010-04-26
> **wojox said:**
> Why not just set up Twin-View? Then you have on screen with your panels and your other screen empty to run other apps in.

When I'm running an application in one monitor, the window loses focus if I click anywhere on the second monitor. I realize that this is normal considering that the second monitor is merely an extension of my original desktop. It's just a matter of convenience, nothing serious.

---

