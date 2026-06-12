---
title: "Trouble with a PVR-USB2 Hauppauge"
date: 2008-08-22
forum: Mythbuntu
---

### Post by ArcadePride on 2008-08-22
I have a clean install of mythbuntu, and I can't get my pvr-usb2 external tuner working. I have a pvr-150 that works when hooked up, but there is to much interferance in the case for a good picture. In the mythtv-backend setup under capture cards I scroll through all the types, but they all say "Failed to open" for probed info. Here is the output of dmesg when I plug the usb card in
> [ 1561.984757] usb 1-1: new full speed USB device using uhci_hcd and address 7
[ 1562.108648] usb 1-1: device descriptor read/64, error -71
[ 1562.332454] usb 1-1: device descriptor read/64, error -71
[ 1562.548270] usb 1-1: new full speed USB device using uhci_hcd and address 8
[ 1562.668165] usb 1-1: device descriptor read/64, error -71
[ 1562.891971] usb 1-1: device descriptor read/64, error -71
[ 1563.107787] usb 1-1: new full speed USB device using uhci_hcd and address 9
[ 1563.515434] usb 1-1: device not accepting address 9, error -71
[ 1563.627343] usb 1-1: new full speed USB device using uhci_hcd and address 10
[ 1564.034986] usb 1-1: device not accepting address 10, error -71

On th wiki ([http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV-PVR-USB2](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV-PVR-USB2)) it mentions this page ([http://www.isely.net/pvrusb2/pvrusb2.html](http://www.isely.net/pvrusb2/pvrusb2.html)) for driver install, but i have never manualy done a linux driver setup before and the directions arent detailed enough. I thought mythbuntu supported pvr-usb2 "out of the box" though, so is installing these drivers even the route to take?

---

### Post by ArcadePride on 2008-08-22
Does anyone have any ideas on this? What the dmesg information might mean? I am dead in the water.

---

### Post by LarryJ2 on 2008-08-25
1.  Do you have the pvr2 hardware described in the wiki.  If so, it's supported directly by mythbuntu8.04-1. There are two look a like systems.  The good one is labeled pvr2.  I have one and it works.

2.  In capture Card in Backend setup,  Left Right in order to select  MPEG encoder.  Nothing is shown in probed info.  Then type in /dev/video0 or video1 depending on how your system assigned the output of the WinTV usb box.  Then press enter.  Only then do you see "Probed Info = Hauppauge ...USB (words like that).  You can find out what /dev/videoX to type in by looking at dmesg after a reboot.  In there it should say should say something like,  pvrusb...assigned  /dev/video somenumber.  Try

dmesg | grep pvr

For example, I see  
[   39.610067] pvrusb2: registered device video1 [mpeg]



Larry

---

### Post by house82 on 2008-09-23
Try plugging the card directly into USB 2.0 port. Your card is running in USB 1.1 mode.

---

### Post by Mythgruntled on 2009-02-14
ArcadePride, this post by Dono answers the question about why some folks are having the issue you describe while trying to add the Hauppauge USB card:
_[[COLOR=#444444]http://ubuntuforums.org/showthread.p...55#post6732655[/COLOR]]("http://ubuntuforums.org/showthread.php?p=6732655#post6732655")_

---

