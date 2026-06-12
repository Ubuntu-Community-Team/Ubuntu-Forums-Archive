---
title: "Touchpad not working"
date: 2010-09-14
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by mauro24 on 2010-09-14
After upgrading from 10.04 to 10.10 everything worked just fine.  I logged in, and all hardware was working, then I tried to update the system, restarted the computer, the loging screen loaded up, but the touchpad wasn't working.  For now, I can use the computer but it's a pain without the touchpad.  I have a laptop gateway nv53 AMD athlon II X2 M300.  Thabks in advanced.

---

### Post by mauro24 on 2010-09-15
can anybody give me some help with the touch pad issue

---

### Post by VinDSL on 2010-09-16
I'm doing a 10.10 update, in the background, and noticed a *Synaptics TouchPad Driver for X.Org Server* update in the mix.

Give it a whirl, and see what happens... ;)

---

### Post by soapytheclown on 2010-09-16
> **VinDSL said:**
> I'm doing a 10.10 update, in the background, and noticed a *Synaptics TouchPad Driver for X.Org Server* update in the mix.

Give it a whirl, and see what happens... ;)

just done the update and a full restart to double check and mine is still dead too

---

### Post by gwu777 on 2010-09-16
I am having the same issue after an maintenance upgrade on 10.04. USB Mouse works fine but not the pad furthermore, I have created a new guest profile, the pad works fine, in my case, there is something wrong in the config of the pad in my profile but no-one answered me yet about what it can be. Maybe this could be a lead for you...

[*My original thread - other seems to have this issue.*]("http://ubuntuforums.org/showthread.php?t=1572996")

---

### Post by mauro24 on 2010-09-16
> **gwu777 said:**
> I am having the same issue after an maintenance upgrade on 10.04. USB Mouse works fine but not the pad furthermore, I have created a new guest profile, the pad works fine, in my case, there is something wrong in the config of the pad in my profile but no-one answered me yet about what it can be. Maybe this could be a lead for you...

[*My original thread - other seems to have this issue.*]("http://ubuntuforums.org/showthread.php?t=1572996")
Thanks for the help so far, my tochpad is not working still, I'm using a mouse.  Making another profile could be a good solution, but this computer is not mine, so making a back up to transfer the settings to the new profile is something I'm not good at, I've been updating the computer everyday but nothing has fixed the touchpad.

---

### Post by cariboo on 2010-09-16
@mauro24, why on earth are you using Maverick on someone else's computer? I would suggest installing Lucid, and just keep up with the bug fixes. Maverick won't be released until 10.10.10.

---

### Post by mauro24 on 2010-09-16
> **cariboo907 said:**
> @mauro24, why on earth are you using Maverick on someone else's computer? I would suggest installing Lucid, and just keep up with the bug fixes. Maverick won't be released until 10.10.10.
The main point here is that I'm reporting this problem so it can be fixed, not to make opinions about what should or shouldn't do with a computer.  Like I said, I could make another profile, but how do I back up like the settings for the way the GUI looks?  Thanks

---

### Post by cariboo on 2010-09-17
Compare the files in ~/.gconf/desktop/gnome/peripherals/touchpad/ between the two home directories to see if there is any difference.

You will have to use gconf-editor to edit/change any values.

---

### Post by doughless on 2010-09-18
> **cariboo907 said:**
> Compare the files in ~/.gconf/desktop/gnome/peripherals/touchpad/ between the two home directories to see if there is any difference.

You will have to use gconf-editor to edit/change any values.

Open gconf-editor, go to desktop/gnome/peripherals/touchpad, and check the option touchpad_enabled. My touchpad immediately started working.

---

### Post by gwu777 on 2010-09-18
> **cariboo907 said:**
> 

You will have to use gconf-editor to edit/change any values.

> **doughless said:**
> 

Open gconf-editor, go to desktop/gnome/peripherals/touchpad, and check  the option touchpad_enabled. My touchpad immediately started working.

Thank you so much for taking the time to answer. touchpad_enabled wasn't checked, now it is and it worked immediatly. Again thank you, very simple solution, but my laptop is now happy!

---

### Post by soapytheclown on 2010-09-18
hmm mine was already enabled in gconf and still doesnt work on my sony vaio ive done an lspci and an lsusb to try and work out which make it is but i cant tell:

> 
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series]
01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 SD Host controller: Ricoh Co Ltd Device e822
03:00.1 System peripheral: Ricoh Co Ltd Device e230
03:00.4 SD Host controller: Ricoh Co Ltd Device e822
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8059 PCI-E Gigabit Ethernet Controller (rev 11)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)


> 
us 002 Device 003: ID 04d9:1133 Holtek Semiconductor, Inc. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 064e:a213 Suyin Corp. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


any other ideas anyone??

---

### Post by Fr3eMaN on 2010-09-18
hey,

here is the same problem, but in kubuntu and ther is no .gconf folder...

---

### Post by mauro24 on 2010-09-18
> **cariboo907 said:**
> Compare the files in ~/.gconf/desktop/gnome/peripherals/touchpad/ between the two home directories to see if there is any difference.

You will have to use gconf-editor to edit/change any values.

Thanks for your help.  I follow everything to the letter and I made a new profile but the touchpad in the new profile didn't work either.  I did the gconf-editor and the option "enable touchpad" was already selected, but the touchpad wasn't working, that is in both home folders, the new one and the old.  thanks for your time

---

### Post by cariboo on 2010-09-18
I don't know if you want to go this far, but if you rename the ~/.gonf directory to something like ~/gconf-bak, then log out, and back in again, a new ~/.gconf directory will be created to see if that makes a difference, if it doesn't you can always reuse the original ~/.gconf directory.

I did try it on my netbook, but Unity doesn't have an option to enable/disable the touch pad. All it did for me was create a new ~/.gconf directory

---

### Post by jlblanco on 2010-09-20
The same problem here: after upgrading to Ubuntu 10.10, the touchpad stopped working at all. 

The enable_touchpad entry in gconf was already set to true, and deleting the .gconf directory didn't solve it either. 

Any other hint? Is there anything I could do to debug this?

---

