---
title: "SOLVED- No graphics - Dell Optiplex (PCI Graphics card)"
date: 2007-10-17
forum: Multimedia &amp; Video
---

### Post by candtalan on 2007-10-17
Dell Optiplex GX110 ( PIII )
This model has bios as follows: 
NVIDIA TNT2 model 64 VGA BIOS
Version 2.05.17.02.01

(bios revision 05)

It has on board Intel (i810) graphics and also an installed PCI Graphics Card. 

Problems of no graphics at all were resolved by finding and inserting appropriate values for Driver and BusID in xorg.conf

The BIOS has a limited function for selection of integrated graphics, and the integrated chipset is set to AUTO in the bios (Note 1). I guess that when a PCI graphics card is inserted and the PC turned on, the bios graphics AUTO then keeps the on board stuff disabled.

Most live CDs gave no graphics display at all (Note 2) - a totally unresponsive PC at the stage of trying to start x. Using live cd (7.04 or 7.10rc) in Safe graphics mode leads to a flashing cursor (which becomes a command line after Ctrl Alt F1 is used).

In fact I had not tried a live cd at first in this pc, it has about 180MB ram and I installed edubuntu workstation 7.04 with a text installer. Install went well but when booting and then trying to start x display, it became unresponsive. I could get to a command line by using the grub menu choice of Recovery mode.

dpkg-reconfigure of the server-xorg was not immediately useful but the various error messages were useful, and I had also looked at knoppix live cd xorg.conf too - knoppix worked ok.

The installed file /etc/X11/ xorg.conf contained 
Section "Device"
	Identifier	"Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
	Driver	         "i810"
	BusID		"PCI:0:1:0"
EndSection

This seems to relate to the on board graphics chip (supposedly disabled!), not the installed PCI card. I guess that the installer did not see the PCI graphics card because maybe the onboard graphics was not disabled 'fully' even though the text install process was displayed ok - from the PCI card.

For success I needed to change the values of both the Driver and the BusID to suit the installed PCI card. I now know that the command lspci is very useful in that situation :-)

However I saw information in error messages as mentioned above.

For the PCI card in my particular PC the information in xorg.conf which now works is:
Section "Device"
	Identifier	"Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
	Driver	         "nv"
	BusID		"PCI:1:7:0"
EndSection

Note: the Identifier above is now technically incorrect (it is a nvidia card PCI card)  and before I change the value I want to ensure I know if or where it is referred to elsewhere, and anyway it works as it is now! 

I can understand that the Driver value must be appropriate for the card, but I am a complete novice about BusID in the PCI functions. There are a number of PCI slots in this PC and the card is in one which presumably has the logical address which relates to 
"PCI:1:7:0"     The command lspci reveals good information about the PC settings for PCI.

Note 1: the bios integrated chips alternative is OFF and when I tried that I got no display from either the on board or the installed card, and had to reset the bios (remove battery briefly) to see anything again.

Note 2: knoppix 5.1.1 was ok

hth

---

