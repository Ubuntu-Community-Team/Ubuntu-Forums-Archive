---
title: "Ubuntu not detecting Displayport connection"
date: 2011-04-23
forum: Multimedia Software
---

### Post by paulm on 2011-04-23
I have an 27" iMac which I wish to use as display for my Ubuntu machine using it's mini Displayport as per [http://support.apple.com/kb/ht3924](http://support.apple.com/kb/ht3924)

To that end I bought a new Intel DH67GD motherboard and 2600k CPU and a Displayport->Mini Displayport cable.

However it seems that X doesn't detect the displayport connection correctly. When I boot the Ubuntu machine the iMac correctly switches to that input and Intel motherboard screen appears on the display followed by the grub interface.

However it seems that when X should start it doesn't recognise the Displayport connection. The iMac goes back to displaying it's own screen and the X logs don't seem to recognise the connection

```
[    32.854] (==) intel(0): video overlay key set to 0x101fe
[    32.854] (II) intel(0): Output VGA1 using monitor section Configured Monitor
[    32.859] (II) intel(0): Output HDMI1 has no monitor section
[    32.860] (II) intel(0): Output DP1 has no monitor section
[    32.865] (II) intel(0): Output HDMI2 has no monitor section
[    32.870] (II) intel(0): Output HDMI3 has no monitor section
[    32.871] (II) intel(0): Output DP2 has no monitor section
[    32.872] (II) intel(0): Output DP3 has no monitor section
[    32.872] (II) intel(0): EDID for output VGA1
[    32.877] (II) intel(0): EDID for output HDMI1
[    32.878] (II) intel(0): EDID for output DP1
[    32.883] (II) intel(0): EDID for output HDMI2
[    32.888] (II) intel(0): EDID for output HDMI3
[    32.889] (II) intel(0): EDID for output DP2
[    32.890] (II) intel(0): EDID for output DP3
[    32.890] (II) intel(0): Output VGA1 disconnected
[    32.890] (II) intel(0): Output HDMI1 disconnected
[    32.890] (II) intel(0): Output DP1 disconnected
[    32.890] (II) intel(0): Output HDMI2 disconnected
[    32.890] (II) intel(0): Output HDMI3 disconnected
[    32.890] (II) intel(0): Output DP2 disconnected
[    32.890] (II) intel(0): Output DP3 disconnected
[    32.890] (WW) intel(0): No outputs definitely connected, trying again...
[    32.890] (II) intel(0): Output VGA1 disconnected
[    32.890] (II) intel(0): Output HDMI1 disconnected
[    32.890] (II) intel(0): Output DP1 disconnected
[    32.890] (II) intel(0): Output HDMI2 disconnected
[    32.890] (II) intel(0): Output HDMI3 disconnected
[    32.890] (II) intel(0): Output DP2 disconnected
[    32.890] (II) intel(0): Output DP3 disconnected
[    32.890] (WW) intel(0): Unable to find connected outputs - setting 1024x768 initial framebuffer

```

I have attached my xorg.conf and also an almost full X log (some trackpoint related lines removed to get it under the 19.5KB forum limit).


Any suggestions as to how I can get X to recognise and use the Displayport connection to my iMac?

---

### Post by slade969 on 2011-06-05
Go to intel's site and download the 
**[BIOS Update [BLH6710H.86A]]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=19831&ProdId=3285&lang=eng")**

BIOS version. It's version 0102, dated 2/11/11. It's the only BIOS version that has correctly ID'd my DH67GD's onboard graphics.

---

