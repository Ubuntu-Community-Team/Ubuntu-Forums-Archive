---
title: "Getting dwl-g630 to work after install"
date: 2006-06-13
forum: Networking &amp; Wireless
---

### Post by mkruse on 2006-06-13
I should have had my dwl-g630 wifi card plugged in during installation but I forgot. So now I plug it in to my dapper laptop and nothing happens (the light doesn't even come on). How do I get it working?

iwconfig does not list ath0 or any other wireless extensions.

Here is the relevant output from lshw:

```
     *-network UNCLAIMED
          description: Ethernet controller
          product: Marvell W8300 802.11 Adapter
          vendor: Marvell Technology Group Ltd.
          physical id: 0
          bus info: pci@03:00.0
          version: 07
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          resources: iomemory:36000000-3600ffff iomemory:36010000-3601ffff irq:169
```

So it looks like there is no driver loaded (no "config=" line). How can I load the correct driver and have it bind to this card and create a new interface (if that is the correct terminology)?

I know this card should use ath_pci. I can do "modprobe ath_pci" with no problems, but this doesn't start the card. 

I've also tried the instructions [here]("https://wiki.ubuntu.com/WifiDocs/WirelessTroubleShootingGuide?action=show&redirect=WirelessTroubleshootingGuide#head-87da1b42f569991f8579034710220c47504eccaa") for modifying /etc/pcmcia/config.opts based on the output of "sudo cardctl ident" but this does nothing. And when I try to do ```
sudo kill -HUP `cat /var/run/cardmgr.pid`
``` I find that cardmgr.pid does not exist.

I think this may be of interest: here's what happens when in /var/log/messages I plug the card in:

```
Jun 13 00:16:51 lcbtd kernel: [4295507.978000] pccard: CardBus card inserted into slot 0
Jun 13 00:16:51 lcbtd kernel: [4295507.978000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
Jun 13 00:16:51 lcbtd kernel: [4295507.978000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 169
Jun 13 00:16:51 lcbtd kernel: [4295507.992000] ACPI: PCI interrupt for device 0000:03:00.0 disabled
Jun 13 00:16:51 lcbtd kernel: [4295507.992000] mrv8k: probe of 0000:03:00.0 failed with error -2

```

---

### Post by mkruse on 2006-06-13
[COLOR="DimGray"]*bump*[/COLOR]  ...eh?

---

### Post by mkruse on 2006-06-14
Well, no thanks to anyone, I got it to work late last night. ;) 

Actually, some thanks goes to the authors of about twelve forum posts and how-tos, and whoever helped write ndiswrapper.

(Jes' so you know, I'm not an ubuntu or linux expert, but I have a basic familiarity with commands like "ls" and "sudo apt-get".)

[LIST=1]
[*] From [This wifi troubleshooting guide]("https://wiki.ubuntu.com/WifiDocs/WirelessTroubleShootingGuide?action=show") I determined that the card had a driver loaded that wasn't working properly. I tried using the steps to edit /etc/pcmcia/config.opts but that didn't work at all.
[*] As noted above, I could see that when I inserted the card, something called "mrv8k" was failing. I did a search for this in the forums.
[*] The forum thread called [ndiswrapper stuff]("http://ubuntuforums.org/showthread.php?t=190726") mentioned that **the mrv8k driver that comes with ubuntu is defective and needs to be deleted**. So I moved it to my home directory and renamed it (rather than deleting it, just in case), then rebooted.
[/LIST]

It turns out that the solution is to disable mrv8k (as I said above) and use ndiswrapper instead. For those who don't know, ndiswrapper is a tool that can load Windows wifi drivers. All you need is the driver file and the .inf file that windows would use when installing the driver.

So I went to D-Link's support website and downloaded the zipfile of the XP driver for my card, and unzipped the driver and INF file into my home directory.

Then, I basically followed the instructions in [this post]("http://ubuntuforums.org/showpost.php?p=1103610&postcount=2"):

```
sudo apt-get install ndiswrapper-utils
ndiswrapper -i DRIVER.INF
ndiswrapper -l     
  [should list your driver]
sudo modprobe ndiswrapper
```

At that point, the lights on my card came on and I was ready to configure the wireless network using the System > Networking utility. I then edited /etc/modules by adding another line that just says "ndiswrapper" ([see here]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Load_module")) to load the module at boot time.

---

### Post by 944jon on 2006-08-24
Ok, did everything listed here. I have a DLink DWL-G630 A1 with a Marvell W8300 chipset. 
Deleted the defective mrv8k.ko driver, then installed the DLink ver1 driver I downloaded using,
ndiswrapper -i MRV8K51.INF
There are 4 drivers from DLink Win2K Win98 WINME and WINXP
If I use the WinXP driver it says:

Parse error in in inf. Unable to find section W8100PCI.zerocfg
Parse error in in inf. Unable to find section W8100PCI.zerocfg
Parse error in in inf. Unable to find section W8100PCI.zerocfg

If I use the Win 98 2k or ME driver:

Installing mrv8k51
but then ndiswrapper -l gives me:
Installed mrv8k51

then:
ndiswrapper -l 
gives me,
Installed ndis drivers:
mrv8k51 invalid driver!

I don't know where to go from here.

---

### Post by 944jon on 2006-08-24
If I try to install the XP driver from the directory it is originally in after unzipping instead of copying the .inf file elsewhere It gives me the same as the others, but still no luck.

---

### Post by 944jon on 2006-08-24
ok, still tinkering trying to figure this out. I got it to work with the Win98 driver from DLink. The XP driver will not work. 
sudo ndiswrapper -l
gives me invalid driver 

I guess the .INF driver will not work if it is not in its original directory with the .SYS file to accompany it? 

I restarted after getting it working and the laptop freezes at the initial Compaq screen before even starting grub?!](*,) ](*,) restarted again and it booted up?!

Now it seems to be working ok after the restart. Hope all this babbling helps someone.

---

### Post by loupadrino on 2007-08-05
I have to say as a newbie it was difficult as I couldn't find the mrv8k and instead I had to disable them using: 
ndiswrapper -r "name of the driver"
But finally thanks to you it work
Thank you.

PS : ok now I have to install the right driver for my ati agp2 8mb graphic card ;-)

---

### Post by gba3 on 2007-11-24
I've just installed Gutsy on Compaq Armada M700 with D-Link DWL-G630 and can't get wifi working.

I already installed ndiswrapper, got the right id of the card, downloaded the XP driver for it, installed it in ndiswrapper.

The problem I guess may be with atheros... I can't get it not to load in start up. Every time I type ndiswrapper -l it shows:
net5211 : driver installed
device (168C:001A) present (alternate driver: ath_pci)

I tried the "blacklist ath_pci", but it doesn't work... I probably missed something...

---

### Post by gba3 on 2007-11-25
> **gba3 said:**
> I've just installed Gutsy on Compaq Armada M700 with D-Link DWL-G630 and can't get wifi working.

I already installed ndiswrapper, got the right id of the card, downloaded the XP driver for it, installed it in ndiswrapper.

The problem I guess may be with atheros... I can't get it not to load in start up. Every time I type ndiswrapper -l it shows:
net5211 : driver installed
device (168C:001A) present (alternate driver: ath_pci)

I tried the "blacklist ath_pci", but it doesn't work... I probably missed something...

I unonstalled ndiswrapper, cleared all blacklists concerning ath_pci and ath_hal, everything was put to the starting position couse there were some topics writing about ndiswrapper to be the last option to try etc. And the fact that the dwl-g630 is atheros chipset card made the sense.

Now it seems everything works out from the box!
Wireless works. And I'm happy with Gutsy on my Compaq Armada M700!

Really I dont't know what was wrong and why my dwl-g630 wasn't working at the very beginning. Maybe I was in a very rush. But anyway... after reboot it still was not showing any signs of working.
It seems it needed some kind of tackling, that's all.

---

