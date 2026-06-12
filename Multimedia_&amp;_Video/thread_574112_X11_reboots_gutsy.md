---
title: "X11 reboots gutsy"
date: 2007-10-12
forum: Multimedia &amp; Video
---

### Post by Lars Noodén on 2007-10-12
I'm trying to make a multi-seat workstation using Kubuntu Gutsy beta for x86.

I've got a Dell Optiplex GX 620 with the following video, according to lspci | egrep -i "display|vga"

	00:02.0 Display controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
	00:02.1 Display controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
	04:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage II+ 215GTB [Mach64 GTB] (rev 9a)

I've installed Gutsy several times.  Once with just the built-in Intel controller, and modified /etc/X11/xorg.conf so that it works with everything under a layout called seat1.  The second time  with the ATI card added, and modified /etc/X11/xorg.conf so that it works with everything under the layout seat0.

Now when I test the system, the ATI setup will fire up the X-server properly:
	X -novtswitch -sharevts -nolisten tcp -layout seat0 :0
but the Intel setup will make kind of a buzzing sound and reboot the server:
	X -novtswitch -sharevts -nolisten tcp -layout seat1 :0
and
	X -novtswitch -sharevts -nolisten tcp -layout seat1 :1

If I just let the system boot, then only the ATI controller is activated.  

Where should I look to get both displays going so I can have Multi-seat?  Attached is the offending xorg.conf

---

### Post by Lars Noodén on 2007-10-12
Running X in the background prevents the reboot, most of the time.  e.g.

X -novtswitch -sharevts -nolisten tcp -layout seat1 :1 &

Now I am able to see the error messages, depending on whether I try to specify the i810 driver or the intel driver:

[INDENT]
(WW) I810: No matching Device section for instance (BusID PCI:0:2:0) found
(WW) intel: No matching Device section for instance (BusID PCI:0:2:0) found
[/INDENT]

The xorg.conf that produces the second error above is the following:

[FONT="Courier New"]Section "Device"
        # "ntel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)"
        Identifier      "Intel 1"
        Driver          "intel"
        BusID           "PCI:0:2:1"
EndSection

Section "Device"
        # "ntel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)"
        Identifier      "Intel 0"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection[/FONT]

---

