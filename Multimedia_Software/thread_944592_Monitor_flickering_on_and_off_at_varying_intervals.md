---
title: "Monitor flickering on and off at varying intervals"
date: 2008-10-11
forum: Multimedia Software
---

### Post by f3rodieman on 2008-10-11
Hey, 

Somewhat seasoned on Ubuntu.  I have been searching around for this problem on the forums and only came up with one unsolved post about this.  It just went away for him.  Not really sure whats going on, but as the title says it flickers on and off, doesn't actually turn off.  It doesn't do it on my windows xp partition.  The monitor is an Envision G2219w1 and the Graphics card is an ati radeon 9600 pro (i think it's pro here's what I get in terminal when I identify it:

bren@bren-desktop:~$ sudo lshw -class display
  *-display:0             
       description: VGA compatible controller
       product: RV350 AP [Radeon 9600]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-3.0 pm vga_controller bus_master cap_list
       configuration: driver=fglrx_pci latency=255 mingnt=8 module=fglrx
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV350 AP [Radeon 9600] (Secondary)
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 mingnt=8

The thing is though, the card is not PCI it's AGP 4x/8x.  Hardware drivers say they're running official ati drivers.  I'm running 8.04 and my system is updated.  When I check under the monitor it says I'm running a plug n play and that the card is using flgrx.  I just turned compiz back and didn't have it on when the flickering started.

Other system info is a p4 3.0 ghz with hyper-threading and 2 gigs of ram.  Any other system info needed let me know.  Like I said I know a bit about ubuntu and have been using it for a little under a year.  Thanks for any help.

---

### Post by BMWDriver on 2008-10-11
Hi,
I also had that problem with Ubuntu when I had my Radeon 9600 Pro installed on my system. I also had issues with the X800XT that replaced it. 

For me the solution came frome here :
[Unofficial Wiki for the ATI Linux Driver]("http://wiki.cchtml.com/index.php/Main_Page")

You will get alot of info regarding the ATI proprietary drivers and troubleshooting. Simply clicking the "Enable Proprietary Drivers" option in the Ubuntu control pannel simply is not enough.

At this point, I would suggest trying this command to enable 2D acceleration:[FONT="Courier New"]
sudo aticonfig --overlay-type=Xv[/FONT]

This should be done no matter what proprietary ATI driver you have installed. However, I cannot guarantee this will solve the issue. But it will enable better video rendering (upscaling DVD for example). Just be sure you don't see any **Mesa** entry with the command [FONT="Courier New"]fglrxinfo[/FONT]. If you do, then the driver has not been installed properly, though I think you checked that out already.

You may try to get the most recent drivers from ATI (Catalyst 8.9) and follow the instructions given on the Wiki above to install. Ubuntu repo gives Catalyst 8.3 drivers.

I've had a lot of headaches with my ATI cards, but that Wiki did the trick when I chose to go with the latest ATI drivers. My feeling is that the compilation and install is done better that way.

---

