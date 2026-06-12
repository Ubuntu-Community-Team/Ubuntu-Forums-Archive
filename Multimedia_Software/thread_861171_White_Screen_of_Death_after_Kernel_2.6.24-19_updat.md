---
title: "White Screen of Death after Kernel 2.6.24-19 update via Desktop Effects"
date: 2008-07-16
forum: Multimedia Software
---

### Post by aubreyisland on 2008-07-16
Okay, this is just like a bad marriage, I want it to work out, but she keeps treating me so badly!

Why is Ubuntu releasing unstable Kernel updates? I just updated to 2.6.24-19 (Generic), and mind you, I'm a super geek, but I enjoy not having to think or act like one when it comes to my OS!

I love linux the applications are above par and far beyond that of applications in Windows and at least to par, if not better, than Mac OSx applications.

I had to disable Desktop Effects to get my computer to (quote) turn the 'ef on! (end quote)

I got a white screen of death, and I only use the analogy because it is just as bad (if not worse) than the infamous blue screen of death Windows brought to the computing world. 

I am a typical user, because, generally I follow updates, click (it) whenever my computer (update manager) asks me to, and to tell the truth, I feel like I am getting a free as in beer quality product. I am drunk by the end of the night, and it still tastes like **** - but at least it's nice and cold - right?!

I just think there are a few things Ubuntu is missing - it's almost there, but here I continue to go, using a broken Kernel update until I see a compiz update or X update or who knows, I'll cross that bridge when I see that red arrow again. 

Then, maybe I will get my Desktop Effects back - God! They were awesome - and they will be missed! 

Ubuntu (Mark), please slow down - our hardware is too sensitive!

---

### Post by markbuntu on 2008-07-16
The problem is not just Ubuntu. It is every OS. To put things in perspective, there are over 500,000 different combinations of hardware for pcs. 

No one person or group, no matter how large and no matter how much money they spend can test them all and still meet a reasonable schedule of releases. So, they test as much as they can, release alphas and betas for wider testing but still, it will never be enough to keep up with new hardware let alone test the mountain of different hardware already out there. The only way to really test it is with widepread release and a robust bug reporting and fixing program which Ubuntu has in Launchpad.

As it is, Ubuntu is one of the quicker in fixing issues with hardware that come to light and of course, fixing some things sometimes breaks others because it is so intertwined. You really can't blame them because they did not test on a pc with your particular setup. if you want them to, send them one and they will, or get alphas and betas and REPORT THE BUGS.

If you find a bug, report it in Launchpad. It is the only way they will know about it so it can get fixed. I know of two particular bugs that I reported to Launchpad that people were complaining about here in the forums for a long time but nobody else reported them. When I found them on my system, I reported them. They got fixed within 2 weeks.

The microserfs could never move that fast.

---

### Post by andyvr4 on 2008-07-17
I've noticed this problem as well with an ATI Radeon 9600 Pro and would love to here any suggestions that you guys have.

---

### Post by sun2z_emily on 2008-07-17
Same thing happened to me, only it is not the generic kernel that is causing the problem, it is the realtime kernel.
I'm using Radeon X550 with the restricted driver.
Though it doesn't really matter, cos im using the realtime kernel for audio work, so the desktop effects will be turned off anyway.

Hmm, it will be helpful if you told us what graphic card you use, there are a few reports of white screen caused by nVidia driver, though if i remember, it had already been fixed by a newer driver.

It's a good idea that you provide a detailed report, hardware and other configurations. Im sure it wont be long for it to be fixed.

---

### Post by phoenix12345 on 2008-07-17
This also happened to me, i usualy don't use Compiz but for some unknown reason it's enabled by default on Ubuntu. I have a ATI HD 2600 XT AGP(little problem maker since i bought it) with **fglrx 8.501** .

---

### Post by aubreyisland on 2008-07-17
> **markbuntu said:**
> The problem is not just Ubuntu. It is every OS. To put things in perspective, there are over 500,000 different combinations of hardware for pcs. 

No one person or group, no matter how large and no matter how much money they spend can test them all and still meet a reasonable schedule of releases. So, they test as much as they can, release alphas and betas for wider testing but still, it will never be enough to keep up with new hardware let alone test the mountain of different hardware already out there. The only way to really test it is with widepread release and a robust bug reporting and fixing program which Ubuntu has in Launchpad.

As it is, Ubuntu is one of the quicker in fixing issues with hardware that come to light and of course, fixing some things sometimes breaks others because it is so intertwined. You really can't blame them because they did not test on a pc with your particular setup. if you want them to, send them one and they will, or get alphas and betas and REPORT THE BUGS.

If you find a bug, report it in Launchpad. It is the only way they will know about it so it can get fixed. I know of two particular bugs that I reported to Launchpad that people were complaining about here in the forums for a long time but nobody else reported them. When I found them on my system, I reported them. They got fixed within 2 weeks.

The microserfs could never move that fast.

Also (bugs), grandmaw isn't going to want to report bugs - in fact she may get a little "cranky" from even the word.

I understand your understanding and passion for the issue, and you're right, but wrong...

All my gripe was, was if you're going to mess something up, or take the risk, make sure my computer at least turns on. I called it the White Screen of Death for a reason...

---

### Post by aubreyisland on 2008-07-17
> **sun2z_emily said:**
> Same thing happened to me, only it is not the generic kernel that is causing the problem, it is the realtime kernel.
I'm using Radeon X550 with the restricted driver.
Though it doesn't really matter, cos im using the realtime kernel for audio work, so the desktop effects will be turned off anyway.

Hmm, it will be helpful if you told us what graphic card you use, there are a few reports of white screen caused by nVidia driver, though if i remember, it had already been fixed by a newer driver.

It's a good idea that you provide a detailed report, hardware and other configurations. Im sure it wont be long for it to be fixed.

I was using an ATI Radeon Express on Acer 5050 Aspire (3319 Bios, I think)

But, that wasn't my point. I think it's strange, though, I think if something went wrong, Desktop Effects (what grandmaw calls it) would disable itself - I don't mind it being disabled because the update doesn't support it anymore, but like I keep saying: White Screen of Death. If I was grandmaw, I'd be on my grandson's *** for breaking my computer!

:guitar:

---

### Post by Cone on 2008-07-17
> **aubreyisland said:**
> 
All my gripe was, was if you're going to mess something up, or take the risk, make sure my computer at least turns on. I called it the White Screen of Death for a reason...

It's impossible to be aware that it will "mess something up" on your computer unless someone with a similar configuration tested the release and discovered that, oh no, compiz makes the screen go white! (I have the problem on my Fedora desktop too with a Nvidia GeForce 8800 GT, by the way)

I don't know what the problem is, but it's entirely in the rendering and not the desktop itself -- if I hit space on the manager in Fedora (has an Enable/Disable button) after clicking "Enable" it'll disable it again.  I figure that also means if this happens to you, you can Alt+F2 and type "metacity --replace" and get out of compiz.

*shrug*

---

### Post by markbuntu on 2008-07-17
Well, this problem did not happen to me and it did not happen to a lot of other people. I am running flgrx8.6 and compiz with my HD 3650 on both 32bit and 64bit. I fully expect that some future update is going to mess with this, but that is my problem, not Ubuntu's

One thing I know for sure is that a lot of people using the newest drivers directly from nvidia and a few from ati or got them with ENVY also had this problem. 

There is a reason why Ubuntu and Fedora for that matter do not support this sort of activity and you just found out why. If you didn't get it from the official repository, it is your problem and the people you got this from, not Ubuntu's, or Fedora's.

If you did get something from the repos and you have a problem, report a bug.

---

### Post by aubreyisland on 2008-07-17
> **Cone said:**
> It's impossible to be aware that it will "mess something up" on your computer unless someone with a similar configuration tested the release and discovered that, oh no, compiz makes the screen go white! (I have the problem on my Fedora desktop too with a Nvidia GeForce 8800 GT, by the way)

I don't know what the problem is, but it's entirely in the rendering and not the desktop itself -- if I hit space on the manager in Fedora (has an Enable/Disable button) after clicking "Enable" it'll disable it again.  I figure that also means if this happens to you, you can Alt+F2 and type "metacity --replace" and get out of compiz.

*shrug*

Yeah, I guess there should be some quick-key to disable desktop effects! And yes, when I hit CTRL + BKSPCE + ALT I saw my wallpaper, so, hmmm... I think the 'failsafe' option should assume you had a rendering problem, and disable anything (compiz, since it's new) that would cause rendering problems for the default session.

But, still! I liked Desktop Effects, I am without until they update it!!!

I just think so many Kernel updates make me dizzy! I didn't even know what to do when it asked me about GRUB! I just picked one!

---

### Post by Cone on 2008-07-18
> **markbuntu said:**
> 
There is a reason why Ubuntu and Fedora for that matter do not support this sort of activity and you just found out why. If you didn't get it from the official repository, it is your problem and the people you got this from, not Ubuntu's, or Fedora's.


Mine were straight from the repositories on Fedora, and I didn't have the problem on Ubuntu (which I'm no longer using since prior to this problem popping up) (and my drivers on Ubuntu, by the way, were straight from the repositories as well).

You're making assumptions.

---

### Post by gmstalk on 2008-07-19
Is there a way to undo, or perhaps view the previous update history. My fully functioning formerly awesome system pretty much stinks after the last update I ran. I cannot even start it unless I go through recovery mode. Even using grub to boot the prior -18 release is a pain. All the desktop effects are insufferably slow. I would like to undo that latest update. Does anyone know how I can updo this mess?

---

### Post by aubreyisland on 2008-07-20
I would usually hit escape in grub and launch the last version kernel. But, I refuse, because grandmaw wouldnt!

---

### Post by aubreyisland on 2008-07-23
I just wanted to let everyone what I just did...

I found out there is a Startup Manager in the Add Remove menu, so I added it. And, since my computer worked rather well in -18 kernel I selected it as the default and probably will leave it there.

Got my desktop effects back! By the way Banshee 1.0 rocks! 

:guitar:

Maybe, when a Kernel is released they could have the option of choosing to upgrade in plain english: If your computer appears to be working, skip this step kind-of thing...???

---

### Post by markbuntu on 2008-07-24
Well, I just got an update to the -20 kernel yesterday and as it was loading/configuring itself it had a message something like

"...do not know what to do with fglrx DKMS modules use manual method."

So when I rebooted and was unable to initiate desktop visual effects. I knew what to do and loaded the fglrx-kernel-source modules into the kernel. Rebooted and everything was back to normal, no big deal.

It is important to watch the messages in the terminal when you install anything, especially a new kernel. They will usually tell you if something is wrong or if it broke something and will sometimes tell you what to do about it.

This is probably what is going on with those of you whose nvidia drivers were broken with the -19 kernel update.

---

### Post by AaronMT on 2008-07-24
I just got an update for 2.6.24-20-generic, rebooted and got the white screen, went into failsafe mode and changed my startup script back to metacity and here I am posting.

What is the temporary way of fixing this?

---

### Post by Derviansoul on 2008-07-25
Hello

I've not being getting white screen of death but with kernel 2.6.24-19-generic i got all kinds off hangs from the OS, i thought it was firefox, and then it started happening when i'm watching a movie when i moving a window, just whenever it felt like, my solution was to put the first kernel that hardy came with 2.6.24-16-generic, and the system became stable back again, the thing is that this doesn't happens with my macbook laptop, maybe it's something to do with ati drivers i really don't know what i know is but 2.6.24-16-generic works allot better for me.
if anyone felt the same us can all put the old kernel back again using a tool qgrubeditor to do it.
regards

---

### Post by markbuntu on 2008-07-25
It may be a good idea to disable desktop visual effects, ie compiz when updating video drivers or kernels.

It just so happened that I had compiz off when I updated the kernel so that is probably what avoided the white screen of death issue which most likely would have occured as soon as I logged in.

If you are using the 8.5 0r 8.6 or 8.7 ati driver you can load the fglrx modules into the -20 kernel with this command once you navigate to the place where you have stored the debs. (You really should keep this stuff around):

```

sudo dpkg -i fglrx-kernel-source_*.deb

```

If you did not keep the debs you need to dpkg the driver again before doing this.

---

### Post by dirtyworks on 2008-09-05
Hello!

I've bumped into this problem too. Here's what worked for me:

First of all I've noticed that the fglrx module wasn't loaded (lsmod), and modprobe failed to load it - it said it wasn't listed in Xorg.conf.
I checked Xorg.conf and discovered that after a recent update, Xorg has backed up my conf file and replaced it with a default one. I've undone the replace and it looks like:

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
	Driver		"fglrx"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

Section "Module"
	Load		"glx"
EndSection
```

Next I've opened the Restricted Drivers window and there was no driver listed.
So I did:

```
sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r`
```

Then the driver appeared in the list of Restricted Drivers, but strangely it was marked as Enabled but Not in use. So I unticked Enable and then re-ticked it. Ubuntu installed the flgrx packages and requested a restart.

After restart: Success! Direct rendering: Yes. On enable compiz worked! No more white screen.

Cheers!
Hope this helps!

Matei

---

