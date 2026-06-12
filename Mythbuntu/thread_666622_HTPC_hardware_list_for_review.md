---
title: "HTPC hardware list for review"
date: 2008-01-13
forum: Mythbuntu
---

### Post by ltullos on 2008-01-13
I am still a relative newb with Linux & Ubuntu having played with distros for last year and installing a few programs; but I'm ready to take the plunge in building a HTPC box.  I've searched and read enough to see that there is a high risk of making subtle mistake in H/W selection such that driver won't support some needed function; so I want to run by list by the experts here first.  I have checked the incompatibility list and believe everything passes it.
 
First, for objectives of this box: Primary use is Mythbuntu HTPC paired with my Sony KDS-R50XBR1 SXRD TV and my Motorola DCT6412 Series III Cable STB.  Will do mostly HDTV, movies (Netflix), and web surfing. I plan to connect my STB to HTPC via Firewire for capturing broadcasts that I want to burn to DVD.   I also plan to dual boot and dedicate one drive to WindowsXP (or XP MCE) for some game playing (flight simulaton, racing simulation)
 
Second, for the H/W I've selected:
 
   Gigabyte GA-P35-DS3L MB with CORE 2 DUO E4600 2.4G (800Mhz) and 2 X 1 GB DDR2 667 RAM
   XFX PVT84JUDD3 GeForce 8600GT SLI Supported Video Card
   SAMSUNG SpinPoint T Series HD501LJ 7200 RPM 16MB Cache SATA 3.0Gb/s Hard Drives
    (2 200GB and 1 500GB) 
   SAMSUNG DVD Burner with LightScribe (SATA)
   Hauppauge WinTV-PVR-500 MCE (still considering HDHomeRun)
   nMEDIAPC HTPC 600SAR Case (with MCE remote)
   Antec earthwatts EA430 power supply
   ADESSO slimtouch touchpad keyboard 2.4ghz wireless
 
I'm most looking for feedback on MB & video card capability & compatibility with my objectives; but would also appreciate comments re: nMedia cases, HDHomeRun, and ADESSIO keyboard.  
 
As a note to offer something back to people here, in pricing this out, I found newegg to be unbeatable for prices with EXCEPTION of MB bundle.  Here mwave offers better deals and will assemble & test for $10 which can save a lot of time & heartache.  I've used both many times and never had a problem with either.

---

### Post by newlinux on 2008-01-13
Just a couple comments:

1. Make sure you can record via firewire the stations you want from the cable box by checking the 5c setting.

2. I noticed you are buying a PVR-500 and considering an HDhomerun. Just want to make sure you know they capture different types of signals. You probably already know, but just want to make sure.

Otherwise, it looks good to me...

---

### Post by ltullos on 2008-01-13
Thanks for taking time to review & reply!  I was going to ask what is 5c setting; but Google search answered it for me.

---

### Post by newlinux on 2008-01-14
[http://en.wikibooks.org/wiki/How_to_use_a_Motorola_DVR/Configuration#How_To_Check_If_5C_DTCP_is_Enabled](http://en.wikibooks.org/wiki/How_to_use_a_Motorola_DVR/Configuration#How_To_Check_If_5C_DTCP_is_Enabled)

If you want to check on your box...

---

### Post by anand on 2008-01-16
I have the nMediaPC case you are looking at.  The remote will not work with the version of LIRC included in Mythbuntu 7.10.  I recompiled the LIRC mceusb2 module including the 1 line of code to allow LIRC to detect the remote and it works like a charm though.  

I am planning on writing up a little guide to this one of these days.  Until then, what you need to do is edit lirc_mceusb2.c and add the bolded line below:

 	{ USB_DEVICE(VENDOR_MITSUMI, 0x2501) },
 	/* Topseed eHome Infrared Transceiver */
 	{ USB_DEVICE(VENDOR_TOPSEED, 0x0001) },
 	/* Topseed HP eHome Infrared Transceiver */
 	{ USB_DEVICE(VENDOR_TOPSEED, 0x0006) },
[B] 	/* Topseed eHome Infrared Transceiver */
 	{ USB_DEVICE(VENDOR_TOPSEED, 0x0007) },
[/B] 	/* Topseed eHome Infrared Transceiver */
 	{ USB_DEVICE(VENDOR_TOPSEED, 0x0008) },

The case is a bit cramped but that is be expected for this type of case.  Having a SATA optical drive would help out with the cable clutter as would a power supply with modular cables.

---

### Post by ltullos on 2008-01-26
> Until then, what you need to do is edit lirc_mceusb2.c and add the bolded line below:

{ USB_DEVICE(VENDOR_MITSUMI, 0x2501) },
/* Topseed eHome Infrared Transceiver */
{ USB_DEVICE(VENDOR_TOPSEED, 0x0001) },
/* Topseed HP eHome Infrared Transceiver */
{ USB_DEVICE(VENDOR_TOPSEED, 0x0006) },
/* Topseed eHome Infrared Transceiver */
{ USB_DEVICE(VENDOR_TOPSEED, 0x0007) },
/* Topseed eHome Infrared Transceiver */
{ USB_DEVICE(VENDOR_TOPSEED, 0x000 },


I received my H/W and am well on the way to having my new HTPC working, but have not been able to find this lirc_mceusb2 file.  Can you point me to it and also tell me what I need to open to edit it?  Sorry for such a basic question, but I'm just getting my feet wet here (though it feels great!)

---

