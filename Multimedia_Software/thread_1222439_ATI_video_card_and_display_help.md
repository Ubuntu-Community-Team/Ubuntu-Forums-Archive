---
title: "ATI video card and display help"
date: 2009-07-24
forum: Multimedia Software
---

### Post by thundaraptor on 2009-07-24
Am somewhat of a basic user and not sure I understand enough about video card stuff.  Just built new system have an ATI hd3200 onboard video card and external ATI hd 4670 expansion card installed.  Have Jaunty 9.04 for 64 bit installed on AMD Phenom II 2.6 quad core with 4 gb 1066 and blueray reader.  

Curious about following things.

(1) Have two acer HD monitors plugged into expansion card and getting a clone desktop.  
  How do I make this 2 separate desktops or at least something extended?  

(2) What is Catalyst 9.xx and how do I know if I have the most recent version (whatever it is)

(3) How do I know if I am displaying in hd resolution?

(4) Where do I begin hashing out trying to get crossfire working?  Have seen some other forums and feel that I need to answer above question (2) first.

Have the FGLRX driver installed and can edit video card with "ati catalyst control center" function contained in accessories area.

---

### Post by automaton26 on 2009-07-29
1) You would normally be able to get multiple desktops by using the "System Settings" application. I use KDE (kubuntu), not GNOME (ubuntu), so I can't direct you to the exact location - there should be a "Desktop" applet somewhere. However, if you have "Catalyst Control Center" available, it's probably needs configuring in there.

2) Catalyst 9.7 is just the latest ATI's graphics driver package. They have a new point release every month I think. There are version numbers visible in the "Information" section of the "Catalyst Control Center" (but not the 9.7 !). My installation says "2D Driver Version" is 8.63.2.

3) Depends what your monitor supports (HD usually refers to 1920x1080) - just make sure the multiple desktops are configured to match the physical monitor resolutions.

4) Crossfire is where the machine has multiple physical graphics cards of the same type, so you would need two or more identical HD2670s and a special cable to connect them (it doesn't apply to an "onboard" card, which is integrated into the motherboard).

Hope that helps.

---

### Post by markbuntu on 2009-07-29
The driver frm hardware manager does not allow you to set a big desktop unless you turn randr off. The latest driver from ati Catalyst9.7 does not have this problem. There are some threads around here about Catalyst 9.5, 9.6 and 9.7 which discuss this and other things it would be good for you to know. You should go look at them.

Catalyst x.x is the driver package and is numbered year.month. This package includes the latest driver release and driver kenrel modules, the driver itself is called fglrx and is numbered 8.xx.x, 8.63.2 is the latest. Also included is the Catalyst Control Center which is the configuration gui and amdccle which is the command line configuration app. Also included is atieventsd which is the acpi interface for the driver.

Also installed is an unistallation script fglrx-unistall.sh in user/share/ati. This should be used to remove the driver and must be used before installing a new driver. Failure to do this may result in the kernel modules failing to load, wrong configuration files being used and other more or less serious difficulties.

---

