---
title: "Toshiba Satellite 4030CDT"
date: 2009-01-30
forum: Multimedia Software
---

### Post by theprofessor13 on 2009-01-30
Hi everyone

I already posted this issue over in "Hardware & Laptops" but "73ckn797" suggested that I post it here as well.
Anyway, this is my issue:

> So I've got my old Toshiba 4030CDT out and decided to install Xubuntu 8.10 on it. Everything is running fine and even fast. Not as fast as my Core i7, or when the laptop was running XP but fast none the less. Except for the display. I can run at 800x600x24 but not 1024x768x16. I would much prefer the extra screen real estate than the extra colours :). I could do it with Windows XP but for the life of me can not figure out how to do it under Linux. Any help would be greatly appreciated.

What I have already tried ant what went wrong:
> 
Did you check System/Administration/Hardware Drivers to see whether there are any restricted drivers available for the video?
> **theprofessor13 said:**
> I haven't yet, but I'll have a look.

Thanks for the reply :).

Edit:
OK, because I am using Xubuntu, there is no "System/Administration/Hardware Drivers". It's just "System/Hardware Drivers".
Anyway, the Hardware Drivers window pops up and in it it says "No Proprietary Drivers are in use on the System". I don't see anywhere to check for driver updates in the window either :(.

> **73ckn797 said:**
> I am not familiar with Xubuntu all that much. Look around the forums as I am sure there are other posts that have addressed your particular situation. Maybe post your question in the video forum.

> **theprofessor13 said:**
> I was going to post in the "Multimedia and Video" section but I places it here as it was an issue with a laptop. The sub-sections need to be less broad. We have the same issue over at nVidia Forums.

Anyway, thanks for your help :). Any suggestions on what I should search for? I'm not all that fluent in the Linux "lingo". I own Windows though.

> **73ckn797 said:**
> Go into System/Administration/Software Sources and enable the restricted (multiverse) repositories. Then reload as directed and then use System/Administration/Update Manager to check for more updates. It may then give you notice of restricted video drivers to install. If there is a "recommended" driver, use that one. If that is the case and you install it you will probably have to restart the computer for it to take effect. 

See how that will work.
 I will look here later today to see any response.

> **theprofessor13 said:**
> OK, I went into "Applications/System/Software Sources" but the "restricted (multiverse) repositories" option was already enabled.
I'm checking the updates list now. It might take a while as there are 161 of them.

Edit:
Apparently my system is up to date. I know this isn't right as just last night I disabled automatic update downloading and installing as it was to resource intensive (mouse lag:()and there were 161 updates. I can now not get back into the updater's preferences to re-enable automatic download and installation.

Any ideas?

---

### Post by overdrank on 2009-01-30
Hi and could you give us some system specs?
Also what is the graphics model? You can identify your hardware with the command lspci in the terminal which is located under applications, accessories.

---

### Post by theprofessor13 on 2009-01-30
> **overdrank said:**
> Hi and could you give us some system specs?
Also what is the graphics model? You can identify your hardware with the command lspci in the terminal which is located under applications, accessories.

Hi

Sure can. Don't laugh to hard, my other laptop and desktop are much better. Just wanted to try Linux out properly.

CPU: Intel Celeron 300MHz 128KB Cache
Chipset: Intel 440DX
RAM: 128MB (one 64MB stick, the rest is intergrated
Graphics Card: Trident Cyber 9525 PCI

---

### Post by overdrank on 2009-01-30
> **theprofessor13 said:**
> Hi

Sure can. Don't laugh to hard, my other laptop and desktop are much better. Just wanted to try Linux out properly.

CPU: Intel Celeron 300MHz 128KB Cache
Chipset: Intel 440DX
RAM: 128MB (one 64MB stick, the rest is intergrated
Graphics Card: Trident Cyber 9525 PCI

Hi and the trident graphics are not well supported. You may try the xfix option when booting into recovery mode to correct the graphics. Recovery mode is usually the second choice from the grub when booting.

---

### Post by theprofessor13 on 2009-01-31
Right, ran "xfix" but I still only have the option to use 800x600x24 and no higher. Is there any way to force 1024x768x16? I know that Damn Small Linux can display 1024x768x16 and so can the Edubuntu installer.

---

### Post by theprofessor13 on 2009-02-02
Bump for the sake of me trying Linux properly.

---

### Post by kerry_s on 2009-02-02
post your /etc/X11/xorg.conf

dsl uses vesa, so you'll probably want to try that driver and set the modes:

```
Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth 16 
	SubSection "Display"
		Viewport   0 0
		Depth     16
		Modes "1024x768"
	EndSubSection
EndSection
```

---

### Post by theprofessor13 on 2009-02-02
> **kerry_s said:**
> post your /etc/X11/xorg.conf

dsl uses vesa, so you'll probably want to try that driver and set the modes:

```
Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth 16 
	SubSection "Display"
		Viewport   0 0
		Depth     16
		Modes "1024x768"
	EndSubSection
EndSection
```

Thanks, I'll give that a try :).

---

