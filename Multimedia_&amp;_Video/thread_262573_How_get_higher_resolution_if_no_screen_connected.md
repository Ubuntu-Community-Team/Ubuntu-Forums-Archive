---
title: "How get higher resolution if no screen connected?"
date: 2006-09-21
forum: Multimedia &amp; Video
---

### Post by Azyx on 2006-09-21
Have Dapper-desktop installed and a S3 Inc. VT8375 [ProSavage8 KM266/KL266-driver. When i have the screen connected i can get, 1600x1200 in resolution, but if i don't have any connected i can only get 640x480.  I controll the computer thrue Remotedesktop (VNC), and use the screen to another computer. So it a problem if I reboot, I can't change the resolution if I not  connect the screen.
Is it possible to let the computer start in another resolution without the screen connected?

---

### Post by sp4rd on 2006-09-21
I had the same problem.  I think what I did was set gdm to login automatically on the computer that was running headless and set values for HorizSync and VertRefresh for my monitor under the Monitors section in my xorg.conf.  Gdm I guess still probes the monitors section for those values and I was able to connect and use resolutions other than 640x480 with VNC without a monitor connected.

---

### Post by Azyx on 2006-09-22
> **sp4rd said:**
> I had the same problem.  I think what I did was set gdm to login automatically on the computer that was running headless and set values for HorizSync and VertRefresh for my monitor under the Monitors section in my xorg.conf.  Gdm I guess still probes the monitors section for those values and I was able to connect and use resolutions other than 640x480 with VNC without a monitor connected.

 I have automatic login. I can´t see where I should edit in xorg.conf. Even if i don't have connected any screen, it says that there are my screen and possible to change resolution, according to xorg.conf, I think.

---

### Post by sp4rd on 2006-09-22
Ok, you're going to have to edit your /etc/X11/xorg.conf file.
First thing I would do is back it up. Do a

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup1

in case we mess up something you have a clean copy to replace your edited one.

next we will edit your /etc/X11/xorg.conf file

sudo gedit /etc/X11/xorg.conf

What you want to look for is the section describing your monitor, it usually follows your Section "Device.  On mine it looks like this.

Section "Monitor"
	Identifier	"Monitor0"
	Option		"DPMS"
EndSection
^^^^^^^^original monitor section^^^^^^^
yours might look like the above

When my xorg.conf file was originally created there was no 
HorizSync and VertRefresh entries in my Monitor description I added those manually.
Section "Monitor"
	Identifier	"Monitor0"
	Option		"DPMS"
	HorizSync	30-85    <-- entries I
	VertRefresh	48-120   <-- added
EndSection
^^^^^^^^modified monitor section^^^^^^^

If you don't know the values for your monitor you can probably just use standard SVGA ones.  All I know is that I couldn't get higher resolutions until something was entered into those two entries.

After you edited xorg.conf save it and exit gedit.
Next you'll have to restart your xserver or gdm for the new edited /etc/X11/xorg.conf to take effect.  Or you can just reboot.  To restart gdm if you don't want to reboot you can do a
Ctrl-Alt-F1 to get to a console login screen, login with your username and do a 
sudo /etc/init.d/gdm restart

---

### Post by Azyx on 2006-09-23
Thanx! It worked fine. :)
/azyx

---

### Post by pratik5705 on 2007-06-04
thanks.. worked great.

thanks to the active community here  most of my problems have been solved.

---

