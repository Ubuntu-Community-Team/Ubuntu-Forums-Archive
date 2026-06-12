---
title: "Sooo close to native res I can taste it!"
date: 2007-10-06
forum: Multimedia &amp; Video
---

### Post by smh449 on 2007-10-06
OK.  I've read a zillion posts on this forum and elsewhere but I still don't have it (almost not quite).  My 24in Soyo LCD has a native res of 1920x1200.  The closest I can get is 1600x1050.  If I select 1920x1200 I get it but the screen is compressed leaving part of the left side blank.  All the desktop is there but it's narrower (kind of like watching a wide screen DVD at 4:3 aspect ratio.  Narrow and Tall!  I've edited xorg.conf to the point I can see it in my sleep.  Before I did that I could only get 1280x1024 so I've done good, yes?  I have it set up for dual boot and windows can do the native res, so I know my hardware can handle it.  I have an iDeq 200n small form factor pc with integrated nvidia  mx440 agp graphics.  Not the latest but still nice.  I've tried 3 or 4  of the settings calculators that are out there and I have a feeling that I'm so close all I probably need to do is change one or two of the numbers they print out and I'll have it.

Any thoughts?
Sean

---

### Post by RomeReactor on 2007-10-06
Hi. I don't know if you've tried this: If you have the restricted drivers installed--the official nvidia drivers--try running nvidia settings:
```
gksudo nvidia-settings
```
and see if you can set that resolution there.

---

### Post by smh449 on 2007-10-06
I'll try it first thing Tuesday morning.  The computer in question is at work so I'll have to wait till then.  It isn't connected to the company LAN so I'm somewhat limited.  Not as limited as I am with the company machine that is on the LAN though.

Many thanks, I'll let you know how it goes.
Sean

---

### Post by smh449 on 2007-10-09
OK, I ran gksudo nvidia-settings.  Nothing happened.  Well, I did have to ener my password but then nothing.  This machine isn't on the internet.  Does it have to be for this command to work?

Sean

---

### Post by wolfen69 on 2007-10-09
try
```
nvidia-settings
```

---

### Post by smh449 on 2007-10-09
I get 'command not found'

Sean

---

### Post by wolfen69 on 2007-10-09
did you install the nvidia driver from restricted drivers manager? if not, it wont show up.

---

### Post by smh449 on 2007-10-09
This machine isn't on the internet.  Can I install it from the CD or DVD?

Sean

---

### Post by RomeReactor on 2007-10-09
> **smh449 said:**
> This machine isn't on the internet.  Can I install it from the CD or DVD?

Sean

Unfortuntely, no, the nvidia drivers are not in the CD. The CD comes with an open source **nv** driver for your card. So you would either have to download the **nvidia-glx-legacy** package *and* its dependencies [from here]("http://packages.ubuntu.com/feisty/misc/nvidia-glx-legacy"), or download the official Nvidia installer [from their site]("http://www.nvidia.com/object/linux_display_x86_96.43.01.html"). You could probably go with the official installer, as it will be a single download, and since your PC isn't connected to the internet, you wouldn't have to re-install it every time you downloaded a new kernel.

If you decide to go with the [official nvidia installer]("http://www.nvidia.com/object/linux_display_x86_96.43.01.html"), then steps to install it are:

[LIST]Download installer to your home folder, or move it there once it finishes downloading.[/LIST]
[LIST]Open a terminal (Applications->Accessories->Terminal) and enter: ```
sudo sh NVIDIA-Linux-x86-96.43.01-pkg1.run
```[/LIST]
[LIST]Once that finishes, run ```
sudo nvidia-xconfig
```[/LIST]
[LIST]Restart your X server (the display) by pressing CTRL+ALT+BACKSPACE; or reboot.[/LIST]

Note that installing the official drivers is not a guarantee that you'll be able to get that resolution.

---

### Post by smh449 on 2007-10-10
OK!  I finally got it working.  I took my machine home, did a clean install of Edgy, downloaded all updates, installed restricted drivers and got the same results.  Except now I had accelerated graphics.  Then by doing a Google with just the right wording I get the modeline for my monitor.  None of the calculators I had tried worked.  My monitor is a Soyo Topaz S and these are the instructions that made it all work.  Pure luck but here it is.

"In case anyone else runs into X11 configuration issues with the 
Soyo Topaz S LCD Monitor ( Model MT-GW-DYLM24D6 ), using the following 
settings in the xorg.conf seems to make it display the 1920 x 1200 resolution correctly.

In “Monitor” Section:

Modeline “1920×1200@SOYO” 154 1920 1968 2000 2080 1200 1203 1209 1235 -HSync +Vsync

In “Screen” Section:

Add “1920×1200@SOYO” into the Modes

I guess I’ll let you know if this setting eventually results in a smoldering heap of burnt 
LCD parts in couple of weeks"

Thanks for all your help,
Sean

---

### Post by mesterha on 2007-10-16
Could you paste your xorg.conf.  I still can't get mine working.

Thanks

---

### Post by dbrossard on 2007-10-19
This also still does not work for me. Are you using DVI or Analog as a connection? I am using DVI and this doesn't seem to work....

---

### Post by Castaa on 2008-02-08
> **dbrossard said:**
> This also still does not work for me. Are you using DVI or Analog as a connection? I am using DVI and this doesn't seem to work....

I have this very same display as well.  **This Soyo display doesn't appear to plug and play correctly in Ubuntu via a DVI connection.**  I actually got it to run at native resolution using the restricted nvidia driver but then after a reboot one day out of the blue completely stopped working.  I connected it to the VGA port on my card and boom it game up in analog 1920x1200 automatically.

---

