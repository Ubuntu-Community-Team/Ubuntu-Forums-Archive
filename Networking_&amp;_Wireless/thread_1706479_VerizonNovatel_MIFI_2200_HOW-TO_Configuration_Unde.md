---
title: "Verizon/Novatel MIFI 2200 HOW-TO Configuration Under GNOME 2.30.2 Ubuntu 10.04 LTS"
date: 2011-03-13
forum: Networking &amp; Wireless
---

### Post by Firefishe on 2011-03-13
Verizon/Novatel MIFI 2200 HOW-TO Configuration Under GNOME 2.30.2 Ubuntu 10.04 LTS Lucid Lynx -- One User's Way, at least ;-).
--

This following document contains a few tweaks that users of the Verizon MIFI 2200 mobile broadband access point (router) may find useful.



***MAIN CAVEAT:  USE THE GNOME DESKTOP, NOT KDE.  (It doesn't seem to work for KDE at this point, at least, not for me.  WiFi Connectivity works fine on KDE, though, so use that if you need to use KDE.***

--


PART ONE - CDMA/USB Connectivity

This will be done in a step-by-step manner, to avoid confusion.

1.  Boot up the system, and log in to your normal user account.

2.  After everything has loaded, plug in your MIFI 2220's usb cable.

3.  Bring up a Nautilus Window. Look for the VZ Access Manager listing, and eject it.  Do this by pressing the eject icon, located to the right of the listing.;

4.  Left-click the nm-applet icon in the system tray, and select the indicated, new, available CDMA network.

5.  Using the wizard, select Verizon as your service provider, and Finish the wizard.

6.  Right-click on the nm-applet icon in the system tray, and select Edit Connections.

7.  Click the Mobile Broadband Tab, and double-click on the connection you just made, typically with the name Verizon in the title.  (It may also be the only one listed, unless you've got another phone configured.)

8.  There will appear a dialog with three editable text fields:  Number, Username, and Password.

Number:  This field should have:  #777   and nothing else.

Username:  This field should be blank.

Password:  This field needs to have the MIFI 2200's access password inputted to the field.  My particular unit had the Password listed on a sticker on the bottom of the unit, itself.  I'd start there.  (The SSID for the WiFi portion is also listed.)

9.  Click the Apply button, then the Close button.  This will take you back to the desktop.

10.  Check the MIFI 2200 to see if the Power Button Light is on (this should be on when you plug in the usb cable).  If it is on, good!  Now check to see if the Green Connectivity Light is on.  (This light is located to the left of the micro-usb jack on the MIFI, itself.

11.  If it is not on, then press the button for about half a second.  The light should come on within two-to-five seconds.  When it is on (and stays on), there will be one more thing to do, one more thing you have done when you first plugged in the usb cable to the computer.

***I can not stress this enough:  IF THE GREEN CONNECTIVITY LIGHT IS NOT ON, THEN YOU WILL NOT BE ABLE TO CONNECT TO THE 'NET!  Follow the instructions above!***

12.  Bring up Nautilus.  Eject the VZ Access Manager usb image (which is on the MIFI, incidentally, which is why it keeps coming up) by clicking on the Eject Button Icon, located to the right of the listing.

13.  After this is done, left-click on the nm-applet icon in the system tray, and select the Verizon listing you created earlier.  It will be located in the top-part of the listings, under Wired Connections.  The MIFI 2200's WiFi-SSID may be listed, but do not select that.  We're not wanting to connect via WiFi at this point, but rather by the faster CDMA/USB connection through the cable.

14.  If all goes well, you should be up and running, and connected to the MIFI 2200 via usb cable.  Bring up a browser to test this theory.
--
If you have trouble, please go back through the above and try it again.  Pay attention the Power Button/USB Image Eject instructions, at Numbers 10, 11, and 12.

----

**WiFI Considerations for the MIFI 2200**

When using the Verizon/Novatel MIFI 2200 for WiFi Connectivity to the Internet, a few things need to be kept in mind.

The first thing is realizing that the device must have been set up, either at the store on the store's computer, using VZ Access Manager, or via VZ Access Manager on a Windows or Macintosh machine.  (I don't like this any more than any other Ubuntu GNU/Linux User, but that's the hard fact of the matter for this device.

Assuming the above, let's continue.

Making sure that nothing is plugged into the MIFI's micro-usb/power jack, Power the MIFI 2200 on by pressing the Power Button.  The Green Power Icon Light in the middle of the Power Button should come on instantly.

This should be followed by the Green Connectivity Light--located to the left of the micro-usb/power jack--coming on after a few more seconds--typically two-to-four seconds or so.

It may take a few moments for the SSID to appear.  My SSID is 'Verizon MIFI2200 64B9' -- Yours may be different, so check the bottom label (or wherever it is indicated) on the MIFI, or with the instruction packet that came with it.

After the SSID becomes visible, simply click on it.  You may be prompted to enter your access password.  (Again, this is probably on the bottom of the MIFI, immediately under the SSID listing.)

***HIDDEN WIRELESS***

It may be that you've done all of the above, and the SSID still does not appear.  If it's not visible in nm-applet's listings, then you're going to have to do the following:

1.  Left-click on the wireless icon in the system tray.

2.  Select "Connect To Hidden Wireless Network..." which will be located at the bottom of the of nm-applet's listings.

3.  A dialog will appear showing the following: Connection (which is a drop-down menu), Network Name (an editable text field), and Wireless Security.

*Connection:  It should start with 'New...'  Click the down-arrow to the right of the field, and see if the "Verizon MIFI..." listing is visible there; if it is, select it.  If not, leave the setting at "New..."

*Network name:  This is where you need to write in the SSID for the MIFI 2200.  For example, I would write:  "Verizon MIFI2200 64B9" (minus quotes).

*Wireless Security:  Click the down-arrow to the right of the listing, and select "WPA & WPA Personal" .

Click the Connect Button in the lower-right-hand-corner of the dialog, and you should be on your way.

Normal Wi-Fi procedures--and those, as mentioned earlier--apply from here.

--

It is my hope that this information may prove useful.  It did for me, and, of course, your mileage may--and probably will--vary ;-).

Anyway, Have Fun With Your New (or Used) MIFI 2200 from Verizon!

Warm Regards,
Firefishe
firefisheATgmailDOTcom

P.S. Go ahead and email me if you have any problems.  I'll do what I can, although I can offer no promises of success.

---

