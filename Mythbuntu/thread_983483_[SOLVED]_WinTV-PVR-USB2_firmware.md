---
title: "[SOLVED] WinTV-PVR-USB2 firmware"
date: 2008-11-15
forum: Mythbuntu
---

### Post by Buschbarber on 2008-11-15
I have successfully gotten MythTV to work on my Ubuntu Ultimate 1.9 machine with an Nvidia Gforce 6200 OC and WinTV HVR 1600 card. I found a page with very explicit instructions, for a newbie like myself. I followed the very detailed list of codes and successfully installed the CX18 firmware which then allowed me to set up the MythTV Backend.

I now have a new problem. I am working on a friend's PC, installing Mythbuntu 8.04.1. V8.10 did not like my Nvidia card so I opted, on his PC, to try 8.04.1 first.

Mythbuntu is installed and I can run the Backend Setup, but when I configure the Capture Card and choose WinTV, instead of V4L, it says Probe Failed. I know I need to install the Firmware, but I again need a very detailed list of instructions in order to install the Firmware and get the MythTV Backend setup for the WinTV-PVR-USB2 card. Mike Isley's instructions were confusing to me.

Can someone help?

---

### Post by Buschbarber on 2008-11-15
This is the page with the Install guide for the WinTV HVR 1600. Every time I have had to redo this, because the kernel had changed, it worked perfectly and restored my MythTV to full functionality.

Could someone provide instructions or point me to a page of instructions that are Newbie proof, like these are, for the WinTV-PVR-USB2?

---

### Post by danbodoh on 2008-11-15
The firmware comes with mythbuntu, so you don't need to install it.

Choose the pvr-x50 option (MPEG2 encoder card).  The device will probably be /dev/video0.

The only problem I had was that a built-in webcam was coming up as /dev/video0, so the pvr-usb2 usually came up as /dev/video1. Eventually, I hacked at the udev rules to make it come up as /dev/pvrusb2.

Check out [http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV-PVR-USB2](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV-PVR-USB2) (Issues and Problems) for some issues with the pvr-usb2.

Dan Bodoh

---

### Post by Buschbarber on 2008-11-15
I went back to the Backend Setup and chose the PVR-X50 option. Under Probe Info, it said Failed. I finished and re entered it again and I finally got it to work.

Other than Schedules Direct, is there a free version of the Program Guide that is worth trying to configure? If so, what is it?

Is there a list of Keyboard Commands for operating MythTV?

---

### Post by Mythgruntled on 2009-02-14
This post by Dono answers the question about why some folks are finding it difficult to add the Hauppauge USB card:
_[[COLOR=#444444]http://ubuntuforums.org/showthread.p...55#post6732655[/COLOR]]("http://ubuntuforums.org/showthread.php?p=6732655#post6732655")_

---

### Post by Buschbarber on 2009-02-14
I seem to have a hardware conflict on my PC that does not permit My Nvidia card to work when I also have the driver loaded for my WinTV-PVR-1600. MythTV works fine with the Onboard Intel Graphics adapter, after I install the CX18 firmware, but then I cannot get the Nvidia restricted drivers to load for my 8400GS card. If I unload the WinTV drivers, then I can load the Nvidia drivers. Google Earth will not load unless the Nvidia drivers are loaded.

---

