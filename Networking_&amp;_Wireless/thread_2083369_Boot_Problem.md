---
title: "Boot Problem"
date: 2012-11-12
forum: Networking &amp; Wireless
---

### Post by norm.h on 2012-11-12
Since reporting all OK in this thread [http://ubuntuforums.org/showthread.php?p=12348975#post12348975](http://ubuntuforums.org/showthread.php?p=12348975#post12348975), I have a booting issue.

When I try to boot normally, the process hangs at the line:
35.189139 wlan0: no IP6 routers present.
I then have to power off to try again.

If I select Recovery Mode, followed by "resume normal reboot" all boots OK.

When I try to do a "restart" I just get a blank screen with none of the foregoing.


Other texts when the boot process hangs:

22.392410 ath9k wlan0 disabling HT as WMM Q05 isn't supported by the AP, and similar for VHT

wlan0 associates OK with the AP

wlan0 link becomes ready

no IP6 routers present

When I look into sudo less /var/log/dmesg.0, I get (amongst other things I don't understand):
ADDRSONF (NETDEV_UP) wlan0: link is not ready.

---

### Post by chili555 on 2012-11-12
What do you see here?> sudo gedit /etc/network/interfacesIf there is anything more than this, remove it.```
auto lo
iface lo inet loopback
```Proofread, save and close gedit.> When I look into sudo less /var/log/dmesg.0, I get (amongst other things I don't understand):Can you please capture 15 lines or so for posting here?

Reboot and see if your change helped.

---

### Post by norm.h on 2012-11-12
sudo gedit /etc/network/interfaces just shows:

auto lo
iface lo inet loopback 

From: sudo less /var/log/dmesg.0

13.083546] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.083552] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.959901] lp: driver loaded but no devices found
[   30.798095] Adding 4085756k swap on /dev/sda5.  Priority:-1 extents:1 across:4085756k 
[   30.858883] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   30.910432] init: failsafe main process (1182) killed by TERM signal
[   31.057755] init: udev-fallback-graphics main process (1194) terminated with status 1
[   31.072011] init: friendly-recovery post-stop process (874) terminated with status 1
[   31.103000] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   31.103003] Bluetooth: BNEP filters: protocol multicast
[   31.118547] ppdev: user-space parallel port driver
[   31.219363] Bluetooth: RFCOMM TTY layer initialized
[   31.219367] Bluetooth: RFCOMM socket layer initialized
[   31.219369] Bluetooth: RFCOMM ver 1.11
[   31.570951] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.574015] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.713145] r8169 0000:03:00.0: eth0: link down
[   31.713292] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   31.713577] ADDRCONF(NETDEV_UP): eth0: link is not ready
(END)

I also disabled IP6 tables in Firefox, but it made no difference.

---

### Post by norm.h on 2012-11-12
From sudo less /var/log/dmesg 

9.660860] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.660867] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.592774] lp: driver loaded but no devices found
[   27.448381] Adding 4085756k swap on /dev/sda5.  Priority:-1 extents:1 across:4085756k 
[   27.557417] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   27.634250] init: failsafe main process (1174) killed by TERM signal
[   27.812372] init: udev-fallback-graphics main process (1186) terminated with status 1
[   27.825998] init: friendly-recovery post-stop process (865) terminated with status 1
[   27.863791] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.863793] Bluetooth: BNEP filters: protocol multicast
[   27.917550] ppdev: user-space parallel port driver
[   28.017388] Bluetooth: RFCOMM TTY layer initialized
[   28.017393] Bluetooth: RFCOMM socket layer initialized
[   28.017394] Bluetooth: RFCOMM ver 1.11
[   28.458342] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.461322] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.593937] r8169 0000:03:00.0: eth0: link down
[   28.594083] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.594357] ADDRCONF(NETDEV_UP): eth0: link is not ready

---

### Post by chili555 on 2012-11-12
What extra settings have you placed in Network Manager. Ideally, with the exception of IPv6 and infrastructure, none are nneeded.> When I try to boot normally, the process hangs at the line:
35.189139 wlan0: no IP6 routers present.
I then have to power off to try again.

If I select Recovery Mode, followed by "resume normal reboot" all boots OK.
If you just wait, does it boot? When it does, do you have an active network connection?

---

### Post by norm.h on 2012-11-12
No "extra" settings in Network Manager.

Waiting, it just doesn't do anything - blank screen.
It only boots after I've powered off and restarted, choosing Recovery Mode, and then "resume normal reboot", and when it does, I'm connected OK.

EDIT: I've also renabled IP6 in FF

---

### Post by chili555 on 2012-11-12
Please reboot and let it fail. Power down and boot up from Rescue Mode. Then run:```
sudo cat /vat/log/dmesg.0 > norm.txt
sudo cat /var/log/dmesg >> norm.txt
zip norm.zip norm.txt
```Find the file norm.zip in your user directory and attach it to your reply using the paperclip tool at the top of the reply box.

---

### Post by norm.h on 2012-11-13
I hope I've done this right.

This morning I connected the laptop via ethernet cable to see if it worked, to eliminate the possibility of it being a wifi issue, but everything happened as I described yesterday.
I have logged my actions and will send them if you think it helpful.

BTW - typo in your first command - should be var not vat. This had me confused for a while;)

---

### Post by chili555 on 2012-11-13
I see a lot of these:> [    1.409256] ACPI Error: Field [CMDX] at 224 exceeds Buffer [SCBF] size 168 (bits) (20110623/dsopcode-236)
[    1.409350] ACPI Error: Method parse/execution failed [\GTFB] (Node f30408a0), AE_AML_BUFFER_LIMIT (20110623/psparse-536)
[    1.409490] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT2._GTF] (Node f30409f0), AE_AML_BUFFER_LIMIT (20110623/psparse-536)You might Google the error and see if you can see a cause. You might also look in the computer's BIOS to be sure there are no funny ACPI settings. In many cases, resetting the BIOS to DEFAULT, often F9, cures a lot of ills.

I also see:> [    0.523814] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12)
[    0.524054] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 10 12)
[    0.524273] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 6 7 10 12)
[    0.524492] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 12)
[    0.524708] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 12) [COLOR="Red"]*0, disabled.[/COLOR]
[    0.524971] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 12) [COLOR="Red"]*0, disabled.[/COLOR]
[    0.525237] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 10 12)
[    0.525455] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 12)I don't know why some IRQs would be disabled. Again, in the BIOS, if there is an IRQ selection page, I'd recommend 'Auto Select.' Please see attached. Although this is an ABIT BIOS page, many are quite similar. 

I see nothing in either dmesg that is an error with wireless. The last messages before you apparently froze look...well, normal.

I suggest you address the issues above and then give us an update.

---

### Post by norm.h on 2012-11-13
As you suggested, I googled the errors, but it's all way above my head.

I looked in the BIOS and there's no way to look at IRQs nor ACPI settings.

I reset (F9) and all that did was disabled something called PXE boot, and hasn't made any difference.

---

### Post by norm.h on 2012-11-13
I googled "ACPI error in Linux" and found this, from here:
[http://www-uxsup.csx.cam.ac.uk/pub/doc/suse/suse9.3/suselinux-adminguide_en/sec.pmanage.acpi.html#sec.pmanage.probs:](http://www-uxsup.csx.cam.ac.uk/pub/doc/suse/suse9.3/suselinux-adminguide_en/sec.pmanage.acpi.html#sec.pmanage.probs:)

[I]16.3.4. Troubleshooting

There are two different types of problems. On one hand, the ACPI code of the kernel may contain bugs that were not detected in time. In this case, a solution will be made available for download. More often, however, the problems are caused by the BIOS. Sometimes, deviations from the ACPI specification are purposely integrated in the BIOS to circumvent errors in the ACPI implementation in other widespread operating systems. Hardware components that have serious errors in the ACPI implementation are recorded in a blacklist that prevents the Linux kernel from using ACPI for these components.

The first thing to do when problems are encountered is to update the BIOS. If the computer does not boot at all, one of the following boot parameters may be helpful:

pci=noacpi
    Do not use ACPI for configuring the PCI devices.
 
acpi=oldboot
    Only perform a simple resource configuration. Do not use ACPI for other purposes.
 
acpi=off
    Disable ACPI.

[Warning]	Problems Booting without ACPI

Some newer machines (especially SMP systems and AMD64 systems) need ACPI for configuring the hardware correctly. On these machines, disabling ACPI can cause problems.[/I]

Do you think it's worth a try?

---

### Post by norm.h on 2012-11-13
I found this on the Linux Mint forums and I'm tempted to try, but I'd value your opinion before I do.

[http://forums.linuxmint.com/viewtopic.php?f=46&t=114697&p=640433&hilit=acpi#p640433](http://forums.linuxmint.com/viewtopic.php?f=46&t=114697&p=640433&hilit=acpi#p640433)

---

### Post by chili555 on 2012-11-13
I am not sure. My specialty is wireless and networking. Here is additional information: [https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI)

All I can say is that there is no evidence I've seen that suggests the freeze is caused by or related to wireless. 

You might ask over in General Help: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331) 

Since we've already done some troubleshooting, you should certainly refer back to this thread. Sorry I can't be of more help.

---

### Post by varunendra on 2012-11-13
norm.h,
Quite hesitatingly, I wish to share something I noticed-

In your attachment, I see a few "remount" attempts for sda1. [COLOR=Navy]*(notice the dmesg log at times 1.773503, 1.773546 and 84.492881)*[/COLOR] This indicates a possible problem on the filesystem. Although this may be a **result** of, rather than the cause of, your problem. But just to make sure, do this -

[LIST]
[*]boot  your live cd, and run 'fsck' on the sda1 (if it is named otherwise in  the live session, change it accordingly). Commandline method - **sudo fsck  /dev/sda1** (make sure the partition is **unmounted** before you do this).
[*]Or, you can run Gparted from the live cd, and Right-click > "Check" the EXT4 partition for errors and fix them.
[/LIST]
Then reboot normally and see if the boot problem persists. Moreover, if the same "remount" messages still occur in dmesg.


If  this doesn't solve your problem, you should start a new thread in  "General Help" section as chili555 suggested. Post a  reference link in that thread to this one, and also mention the 'fsck'  thing you performed on sda1.


Hope you get it sorted.


**PS :**
To learn about the acpi + other boot options you are interested in -
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) (scroll down to "Common kernel boot options")


[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
(read the first post)

---

### Post by norm.h on 2012-11-14
@varunendra & chili555

Many thanks for your help and interest.
I shall do as you suggest.
N

---

