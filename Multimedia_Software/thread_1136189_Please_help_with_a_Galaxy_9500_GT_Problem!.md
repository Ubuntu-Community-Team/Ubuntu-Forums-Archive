---
title: "Please help with a Galaxy 9500 GT Problem!"
date: 2009-04-24
forum: Multimedia Software
---

### Post by IceRayn on 2009-04-24
Hello,

I just purchased a Galaxy 9500GT with 1GB of RAM, and I'm having install troubles.

I've tried all the solutions I could find, some ending with no X Server, and me having to go into recovery mode. Some ending with the correct resolution: 1280x1024, but no acceleration, and no OpenGL, so no games, and no compiz-fusion. 

Quick rundown of all solutions I've tried:
Install normal with login, Ctrl+Alt+F1 FAIL No X
Install then use (fix?)x in recovery 1280x1024 X, but no acceleration

When I use sudo lspci | grep VGA

02:00.0 VGA compatible controller: nVidia Corporation Unknown device 0640 (rev a1)

And I'd really like a solution fast, or I'll have to use Windows (Never) or return the card (I really don't want to.)


I haven't used WinBl0ws in almost 1 month now, but this is making me think about going back. If it doesn't work, then I probably will.

Thank You,
IceRayn

---

### Post by inobe on 2009-04-24
i will say this, ubuntu 8.04 has trouble detecting 9xxx series nvidia cards for whatever reason.

your best solution is ubuntu 8.10 intrepid.

i guessed that you are using 8.04 because i have seen this before and experienced it myself.

you don't need to reinstall' you can upgrade to 8.10

[http://www.howtoforge.com/how-to-upgrade-ubuntu-8.04-to-ubuntu-8.10-desktop-and-server](http://www.howtoforge.com/how-to-upgrade-ubuntu-8.04-to-ubuntu-8.10-desktop-and-server)

once the upgrade is complete do the system updates before activating or installing drivers !

once done reboot, at this point you should be able to activate the hardware drivers.

---

### Post by overdrank on 2009-04-24
> **IceRayn said:**
> Hello,

I just purchased a Galaxy 9500GT with 1GB of RAM, and I'm having install troubles.

I've tried all the solutions I could find, some ending with no X Server, and me having to go into recovery mode. Some ending with the correct resolution: 1280x1024, but no acceleration, and no OpenGL, so no games, and no compiz-fusion. 

Quick rundown of all solutions I've tried:
Install normal with login, Ctrl+Alt+F1 FAIL No X
Install then use (fix?)x in recovery 1280x1024 X, but no acceleration

When I use sudo lspci | grep VGA

02:00.0 VGA compatible controller: nVidia Corporation Unknown device 0640 (rev a1)

And I'd really like a solution fast, or I'll have to use Windows (Never) or return the card (I really don't want to.)


I haven't used WinBl0ws in almost 1 month now, but this is making me think about going back. If it doesn't work, then I probably will.

Thank You,
IceRayn

Hi did you remove the drivers for the previous graphics card?
Which nvidia drivers have you tried to manually install?

---

### Post by inobe on 2009-04-24
hi overdrank :) 

notice his grep vga output, his card isn't detected.

i helped out a young lady last month, her output was the same, she was running 8.04, i had her upgrade to 8.10 and her card was detected and was notified for restricted drivers.

i assume IceRayn couldn't get onboard video to work and purchased the video card.

i hope i assumed correctly

---

### Post by IceRayn on 2009-04-25
Right about everything but the upgrade reason. Onboard worked fine! GeForce 680**i**(ntegrated) worked fine, but had bad framerates, approx. 30 in Halo under Wine, faster than a native code Windows install for some reason though. (THIS IS WHY I HATE WINDOWS! One of the many reasons. 10 minute boot time vs. 57 second in Ubuntu, no compiz, not as much open source software... The list goes on!)

I'm upgrading to 8.10 now. My ISP (Qwest) is so slow, it's taken more than 24 hours to get to half of Installing the upgrades.

Thank You, I'll tell you how it goes.
IceRayn

---

### Post by IceRayn on 2009-04-25
Well, I updated, and activated the driver to find that I was kicked back to Ubuntu Low Graphics mode, with distorted red lines on the top, and a doubled screen. After booting to recovery mode, I got back into X, but no acceleration, and because of the basic config file, I have no effects of any sort, including if I try to run glxgears the response is: 

Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

Urban Terror just never launches, and the Wine version of UT.exe shows no OpenGL.

This is turning out to be more of a pain than it should...

Thank you for your help,
IceRayn

Hope a solution is found soon.

(I should add that I've tried 180 and 173. Not 177, but I read that that had more problems.)

---

### Post by inobe on 2009-04-25
show me grep vga and do lspci by itself.

i would like to verify all hardware.


some things we should look out for, make sure you are plugged into the actual video card and not onboard.


also if there is an option in the bios to disable onboard video please do so.

edit: may may also want to consider adding this repo to get the very latest nvidia driver.

[http://ubuntuforums.org/showpost.php?p=7132429&postcount=2](http://ubuntuforums.org/showpost.php?p=7132429&postcount=2)

---

### Post by IceRayn on 2009-04-25
Yes, I'm very sure that it is plugged into the card, booted into Vista for the first time in a month, and got 300FPS in the original Halo!

I'll try booting back into 8.10 and seeing if the extra repo works.

There is no option to disable, but there is an option to select my preferred video device: PCI, Integrated or PCIE.

Seeing as my card is PCI-E, I selected PCIE, and that causes it to show up, but the driver always causes a crash of X.

Trying that new repo now,
IceRayn

---

### Post by inobe on 2009-04-25
yes add the repo and as described, you should then be prompted by update manager of the new driver, if not open terminal and run 

```
sudo apt-get update
```

if your not getting any notifications to update open synaptic once more and search **nvidia** give me a list of what's install on your next post.

---

### Post by IceRayn on 2009-04-25
Well, I installed the driver with no adverse affects, but I still get an error when using games, and Desktop effects will not enable.

I'm attempting to add a busid to xorg.conf, restarting X now, I'll let you know how it goes.

Here is the full output of lspci

00:00.0 Host bridge: nVidia Corporation MCP73 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)
00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:03.0 ISA bridge: nVidia Corporation MCP73 LPC Bridge (rev a2)
00:03.1 SMBus: nVidia Corporation MCP73 SMBus (rev a1)
00:03.2 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:03.4 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP73 [nForce 630i] USB 2.0 Controller (EHCI) (rev a1)
00:08.0 IDE interface: nVidia Corporation MCP73 IDE (rev a1)
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
00:0a.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0b.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0e.0 IDE interface: nVidia Corporation Device 07f0 (rev a2)
00:0f.0 Ethernet controller: nVidia Corporation MCP73 Ethernet (rev a2)
01:06.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
01:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 9500 GT (rev a1



Thank You,
IceRayn

---

### Post by IceRayn on 2009-04-25
Well, adding a busid didn't do anything bad nor good, so I have another idea.

Could anyone send me the contents of their xorg.conf?

I need something to compare against.

Thank you,
IceRayn

---

### Post by inobe on 2009-04-25
> **IceRayn said:**
> Well, I installed the driver with no adverse affects, but I still get an error when using games, and Desktop effects will not enable.

I'm attempting to add a busid to xorg.conf, restarting X now, I'll let you know how it goes.



please tell me you rebooted ?

edit: don't worry about xorg for now, we won't even go there' you shouldn't haver to !

---

### Post by IceRayn on 2009-04-25
> **inobe said:**
> please tell me you rebooted ?

edit: don't worry about xorg for now, we won't even go there' you shouldn't haver to !

I did restart, but that didn't help.

Any more suggestions? I'm really confused now, it should be so much easier...

Might it be Galaxy? Or should the driver work across all makers?

As always, thank you for your help,
IceRayn

---

### Post by inobe on 2009-04-25
here are things i need.

in synaptic search nvidia, give me everything that is installed for 180 driver.

also what do you see in system> administration> hardware drivers ?


we will do this one step at a time, have patience we are doing good :)

---

### Post by IceRayn on 2009-04-25
Again, thank you for being so patient with me.

Both Screenshots have been hosted on my apache server.

97.114.90.124

I also have a domain, and I can PM that if needed.

---

### Post by inobe on 2009-04-25
> **IceRayn said:**
> 

97.114.90.124

I also have a domain, and I can PM that if needed.


can you change that to a link

---

### Post by IceRayn on 2009-04-25
[http://97.114.90.124]("http://97.114.90.124")

---

### Post by IceRayn on 2009-04-25
Sorry, my router won't open the port for some reason... I'll attach them to this post.

---

### Post by inobe on 2009-04-25
i thought there was a problem !

having issues connecting, can you just use a free image hosting or type the information.


here's what i have installed in synaptic

nvidia-180-libvdpau
nvidia-settings
nvidia-180-kernel-source
nvidia-common
nvidia-modealiases
nvidia-glx-180
jockey-common
jockey-gtk

---

### Post by inobe on 2009-04-25
> **IceRayn said:**
> Sorry, my router won't open the port for some reason... I'll attach them to this post.

install nvidia-glx-180 and whatever else i listed

---

### Post by IceRayn on 2009-04-25
> **inobe said:**
> install nvidia-glx-180 and whatever else i listed

Should I restart then?

Restarting now.

---

### Post by inobe on 2009-04-25
i would restart.

---

### Post by IceRayn on 2009-04-25
> **inobe said:**
> install nvidia-glx-180 and whatever else i listed

No dice, same errors.

---

### Post by inobe on 2009-04-25
we are close troubleshooting this.

we probably should have disabled the driver in "hardware drivers"

lets do that and restart once more !

upon restarting you should get a prompted for restricted drivers...

later on when we get this working' i will explain what went wrong so that you can prevent it next time :)

---

### Post by IceRayn on 2009-04-25
It has a box saying "A different version is in use", and offers me Activate, not deactivate. What should I do?

---

### Post by inobe on 2009-04-25
that's weird, is nvidia-173-kernel-source still installed in synaptic ?

---

### Post by IceRayn on 2009-04-25
No, and the problem in the previous post is over 180.

---

### Post by IceRayn on 2009-04-25
Never mind, I clicked activate, then deactivate, and I'm now restarting.

---

### Post by inobe on 2009-04-25
when you restart activate 180.

assuming you have all these 

nvidia-180-libvdpau
nvidia-settings
nvidia-180-kernel-source
nvidia-common
nvidia-180-modealiases
nvidia-glx-180
jockey-common
jockey-gtk 

there shouldn't be a problem, once activated you can restart hopefully for the last time.

---

### Post by IceRayn on 2009-04-25
TTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTTT
HHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHHH
AAAAAAAAAAAAAAAAAAAAAAAAAA
NNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNNN
KKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKK

YOU!!!

I was about to go to Windows, but you saved me from the horror of using an inferior OS!
How do I thank you?
New to this forum.

---

### Post by inobe on 2009-04-25
you can add me to your buddy list :)

if there's anything you need and can't find a way out' simply send me a pm and we will start a topic and fix it !


the initial problem, when adding cards, you must be sure the restricted driver is deactivated, also make sure hardware settings are correct, linux will fuss because it's too perfect and specific.

the distro play a big role as well, ubuntu 8.04 is not meant for frequent kernel updates or xorg updates because it's an LTS "long term support"

that means it's good with existing hardware and shouldn't upgrade that hardware with specific models.

---

### Post by inobe on 2009-04-25
example 8.04

02:00.0 VGA compatible controller: nVidia Corporation **Unknown device** 0640 (rev a1)

and the difference with 8.10

02:00.0 VGA compatible controller: nVidia Corporation GeForce 9500 GT (rev a1

8.04 is a great os for like workstations and recycled computers that never get upgraded :)

---

