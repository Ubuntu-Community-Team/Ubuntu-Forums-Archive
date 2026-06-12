---
title: "Ubuntu Studio and Tablet PC"
date: 2007-05-13
forum: Multimedia &amp; Video
---

### Post by samba on 2007-05-13
Hi,

I've just installed Ubuntu Studio on my tablet PC, which is amazing btw, good work folks! But I now have problems with setting up my wacom pen and on-the-fly screen rotation. Everything worked fine with Feisty, but somehow after installation of Ubuntu Studio it doesn't work anymore. For instance, the command "xrandr --orientation right", which is supposed to rotate the screen, does not work anymore: it says, as output:

```

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12

```

The pen is also recognized, but for instance when I try to use it in Xournal well it is not calibrated properly, i.e. it doesn't write where the pen points. 

So I don't know what has been changed from Fesity to Studio that mixed up these commands, but it would be very nice to have them back! :-)

For information my laptop is a Toshiba Portege M405, tablet. 

Cheers :-)
vince

---

### Post by samba on 2007-05-13
Ok I think I solved the problem. Basically, the Ubuntu Studio installer didn't recognize my video card and used instead the generic "vesa" driver. So in my xorg.conf file, the installer wrote

```

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
EndSection

```

which I now changed to

```

Section "Device"
	Identifier	"Intel Corporation Mobile Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

```

and I modified other occurances of "Generic Video Card" accordingly. Now I can use xrandr to rotate the screen on-the-fly, and I think the problem with the wacom pen is also gone.

So it would be nice to modify the installer of Ubuntu Studio so that it acts like the usual installer of Ubuntu, which did recognize my video card without any problem. 

Cheers
vincent

---

