---
title: "Stuck on 640x480"
date: 2008-05-26
forum: Multimedia Software
---

### Post by IainPurdie on 2008-05-26
I'm remote-administering a 6.06 LTS box via VNC. When the machine's rebooted with no monitor attached, it default to 640x480 and there's no option to select another resolution. That's what we're stuck with. If I go to the video settings, 640x480 is the *only* resolution on offer. If the machine's rebooted with a monitor attached then the resolutions on offer are higher (and if I recall correctly the system defaults to 800x600).

I can't access safe mode, as VNC will only work once the machine's up and logged in, which is a shame as I read that there was an option of redetecting the VGA settings on reboot. I'm not sure if this would have helped though.

There is nobody on site who I can really trust to do something under my instruction. I had a look in package manager for the Envy package mentioned elsewhere on the forum, but the only one I could spot detected sound cards, not VGA ones.

Any help much appreciated! It's not a showstopper, but being on a "small" screen when remotely administrating is a pain!

---

### Post by Aearenda on 2008-05-26
You'll need to edit /etc/X11/xorg.conf to override the 'detected' minimal settings. I have done this before, but the machine is remote and presently off and I can't get it turned on to check what I did at the moment! IgnoreEDID comes to mind.

I think the settings are dependent on the video driverdriver - what model is it?

EDIT: Alternatively, you could configure VNC to give you a new login, akin to XDMCP. There are 'howto's around for that.

---

### Post by IainPurdie on 2008-05-26
Good question about the video driver... I think it's an onboard Intel VGA driver. The machine's an old Windows 2000 desktop I "rescued" to use as a basic fileserver.

I did have a look at the xorg.conf file, but just have no idea what to do with it!

I'm guessing this is the relevant section of the xorg.conf file:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82815 CGC [Chipset Graphics Controller]"
	Monitor		"StudioWorks"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "720x450" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "720x450" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "720x450" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "720x450" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "720x450" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "720x450" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

```

---

### Post by Aearenda on 2008-05-26
Maybe it's NoDDC. 

xorg.conf is the file that controls XWindows - it has details of the keyboard, mouse, tablet, and screens. The driver name is set in here. There has been a lot of work since 6.06 to make it simpler to configure, and I honestly can't remember how to do what you want in 6.06. However, the machine I referred to earlier is still on 6.06, and I should be able to get it turned on sometime in the next 24 hours, after which I can tell you what driver it uses and what the settings needed were. In the mean time, someone else may jump in and supply the details I have forgotten.

---

### Post by IainPurdie on 2008-05-26
> **Aearenda said:**
> EDIT: Alternatively, you could configure VNC to give you a new login, akin to XDMCP. There are 'howto's around for that.

Not sure how this would get around the resolution issue?

Thanks for your help so far. No rush on the info - next day or so would be fine! It's not a show-stopper, as I said, just a little annoying when my shell windows are so small I have text-wrap everywhere!

A shame I didn't have time to move it to the latest version before I left site, but at the time, 6.06 was the most up-to-date LTS. 8.04 (if I have the right version) was released as LTS just as I was tidying up to leave site.

---

### Post by Aearenda on 2008-05-26
For remote shells, use SSH! I always install OpenSSH-server on my remote systems, set to use a high port, and to accept key authentication only - no passwords, no root access. Then you can tunnel Xwindows through it using ssh -X -C <servername>. It's faster than VNC over slow links.

The VNC new-login thing gives you a session that is not tied to the actual hardware screen - it's not 'remote control', more like 'remote desktop', or XDMCP. You configure the supported screen resolutions on the vnc server.

Sorry I can't give more detail at this point, I have to go out.

---

### Post by IainPurdie on 2008-05-26
Hum, but would all of the above be configurable remotely? With no risk? As the server is in France and I'm in the UK about to head for the Baltics and the SE Asia! Not ideal if I'm to crash it.

Also bear in mind that the server is an aging desktop. It's one reason I put Ubuntu on, rather than Windows - trying to get every bit of performance out of it I could. I swear, the mice on their little pushbikes inside it work up a sweat every time a backup cron job ticks over...

---

### Post by Aearenda on 2008-05-26
I'm back, but now it's late. From what you have said, if this is truly a server, I would ditch the whole GUI thing and just run SSH for remote management. No VNC, no auto login, do everything from the command line. I'm told it's a 'new feature' of Windows Server 2008 that you can do exactly this! And don't forget you can still run GUI apps using X tunneling.

There's always a risk - but SSH is much less complex for the computer than trying to do things via VNC, and it will work much faster, so long as you are confident with command line working. I would try it first with a local test server. The only things you are likely to get wrong are:
1. Port forwarding on the firewall, if there is one
2. Key-based authentication - you might lock yourself out until you get this right (there are 'howto's on this around as well). But if you leave VNC in place until it is working then you can always dig yourself out of a hole.

---

### Post by IainPurdie on 2008-05-26
As I said, this level of work simply isn't an option.

1) I'm just not that familiar with Ubuntu or UNIX/Linux as a whole so I wouldn't know what I was doing.

2) There is nobody on site with any technical knowledge who could sort anything out should I balls it up. I am in a different country to the server and soon to be on a different continent. The server is in use every day, therefore if I screw it then they're without access to all their data till I fix it.

3) I can't configure port-forwarding on the firewall as it's a hardware one built into the router to which I have no access as I'm not physically on site and nobody there can do it. It's configured, it's stuck like it is.

4) Seems like a *huge* amount of work just to change a screen resolution that I only need sorted on the off-chance I need to connect in and update a .ini or a .conf file! Seriously, thanks for the help but we're looking at serious "industrial earth mover to crack walnut" territory here :)

---

### Post by Aearenda on 2008-05-26
You da boss!

But you'll need the VNC port forwarded too...

Or if you're vpn-ing, you don't need the port forwarded in either case.

I should have the xorg settings today.

---

### Post by Aearenda on 2008-05-26
Ok, I got my server turned on. The screen driver is set to 'vesa' because the native Intel driver didn't respond to these settings. The vesa driver is a generic driver, slower than the native driver - but for a server, it should not matter. However, changing it needs a GDM restart (sudo \etc\init.d\gdm restart) and this will knock you off your VNC session. You may wish to leave things as they are for the present! Here are the screen settings from xorg.conf:

```
Section "Device"
	Identifier	"Intel Corporation Integrated Graphics Controller"
	Driver		"vesa" 
# "intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"DELL D825TM"
	Option		"DPMS"
	Option		"UseEDID" "False"
	Option		"NoDCC" "True"
	HorizSync	30.0 - 81.0
	VertRefresh	56 - 75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Integrated Graphics Controller"
	Monitor		"DELL D825TM"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
EndSection


```

However, I was wrong about the Ubuntu version - it's 7.10, not 6.06. The other server there is 6.06, but it has no difficulty with the screen being absent using the 'nv' driver.

So there you are - I hope this helps!

---

### Post by IainPurdie on 2008-05-27
VNC port is already forwarded - I've been using it fine for the last few days since I left France.

Wow, I remember VESA drivers from the old days of the 486 and early Pentiums!

I'll have a go with the settings and see what happens. Fingers crossed!

Oh, when you say it will "kick me off" the VNC session, does this mean just for the current boot session? i.e. if the machine reboots will VNC work again? Or does this change the desktop session (pardon my terminology if I've got that wrong) to one that's not configured to work with VNC, and will therefore need configuring? And if *so* will it be on 5900/:0 or on 5901/:1?

I think that's all for now ;)

---

### Post by Aearenda on 2008-05-27
It'll just log you off forcibly while GDM restarts with the new driver. The machine will not restart and will continue to provide other services while this is going on.

However, to me, this is more risky than installing SSH! If the GDM restart fails, you will have no way to recover remotely without SSH. Perhaps you could arrange a cron job to return the existing settings in 30 minutes, just in case.

---

