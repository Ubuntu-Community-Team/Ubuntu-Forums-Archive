---
title: "HOWTO: Switch Matrox Triplehead2Go Digital Edition to Dualhead mode."
date: 2009-01-24
forum: Multimedia Software
---

### Post by Hans Bogar on 2009-01-24
Since there are (at this moment) only a few threads about connecting the Matrox Dualhead2Go / Triplehead2Go Digital Edition, I want to share my experience to successfully connect my Triplehead2Go Digital Edition in dualhead mode to Ubuntu.

My box is running on Ubuntu 8.04 - the Hardy Heron.
I have a nVidia GeForce NX6600GT video card with two monitor connectors. 
My monitors: one monitor is a Sony E400 VGA and the other is a BENQ FP937s VGA/DVI. Both have a 4:3 aspect ratio.
I've never been able to get both my monitors to work in Twinview with the nvidia driver.
Another solution is to use the Matrox Dualhead2Go / Triplehead2Go Analog or Digital Edition.

The NX6600GT video card has an analog VGA output (primary) and a digital DVI/analog VGA output (secondary).
For several reasons I have chosen to buy the Matrox TH2G-DE (T2G-D3D-IF) instead of DH2G-DE because of the fact that the TH2G-DE has both an analog and digital input. The analog input is needed for the NX6600GT video card. Since I have two monitors, I'll use the TH2G-DE in Dualhead mode.
And in the future I have the ability switch to completely digital and to connect three screens eventually.

By default the standard operating mode of the TH2G-DE is triplehead, three monitors, so I had to switch to Dualhead mode.

This is done with the Powerdesk utility from the accompanying CD. Since this utility only runs on XP/Vista or Apple OSX there are two possibilities:
1) I already installed Virtualbox with XP client. 
2) Connect the TH2G-DE temporarily to another PC/laptop with XP/Vista or OSX.
In both situations I was able to install and run the Matrox Powerdesk utility to switch the TH2G-DE to Dualhead mode.

The only other thing to do was to add "2560X1024@75" to the SubSection "Display" of xorg.conf.

In my case:
SubSection "Display"
    Viewport 0 0
    Depth 24
    Modes "2560x1024@75" "1280x1024@75" "1024x768@75" 
EndSubSection


By the way: 
The standard operating mode of the TH2G-DE is triplehead, three monitors (In four configurations: 4:3 and wide screen).
 So if you're using three monitors, after connecting the TH2G-DE, the only thing you have to do is to change the SubSection "Display" of xorg.conf to "3840X1024@75" (or the mode you need for your specific hardware situation).
  As far as I can see there is no direct need for the Matrox Powerdesk utility.


Hope this will be helpful to you.




Kind regards,
Hans

---

