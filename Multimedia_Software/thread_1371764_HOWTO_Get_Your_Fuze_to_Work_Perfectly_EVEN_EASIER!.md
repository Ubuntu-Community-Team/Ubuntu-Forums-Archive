---
title: "HOWTO: Get Your Fuze to Work Perfectly EVEN EASIER!!!"
date: 2010-01-03
forum: Multimedia Software
---

### Post by N00b-un-2 on 2010-01-03
Okay, so after a couple weeks of research and messing around with my Fuze, being frustrated by the fact that it only showed up as a USB storage drive and not a Music player I came up with some solutions, but until today my 'solutions' were hacks at best.  This howto offers an actual SOLUTION, and not just a workaround that lets you sync your Fuze with SOME music players (Banshee and Rhythmbox).  This solution should also work for audio players that are not recognized properly.  In this tutorial I will use the word HAL several times.  HAL stands for *Hardware Accession Layer*, and it can be thought kind of the same way as the device manager on Windows.  It's a list of all the devices plugged into your computer, basically.

**Step 1: Dump Your HAL Output** 
With you Fuze plugged into your computer, in a terminal type
```
lshal
```
and look through the output for SanDisk.  Something that will make this easier is:
In a terminal navigate to 'edit>current profile>scrolling' and set the 'Scrollback' output to 1000 lines instead of 500, since the *lshal* output can be HUGE.

**Step 2: Find your Fuze's ID Codes in the HAL**
Then, copy all of the output (or as much as is shown)) of *lshal* to a gedit document, so that you can search your vendor.  In this case, SanDisk.  In your gedit document, hit *ctrl+f* and search for SanDisk.  There will be a whole lot of output but you are looking for a section that looks something like this:

```
 usb_device.product = 'SanDisk Sansa Fuze'  (string)
  usb_device.product_id = 29891  (0x74c3)  (int)
  usb_device.serial = 'F320E40B8038B6A80000000000000000'  (string)
  usb_device.speed = 480.0 (480) (double)
  usb_device.speed_bcd = 294912  (0x48000)  (int)
  usb_device.vendor = 'SanDisk Corp.'  (string)
  usb_device.vendor_id = 1921  (0x781)  (int)
  usb_device.version = 2.0 (2) (double)
  usb_device.version_bcd = 512  (0x200)  (int)
```

Specifically we are looking for the lines *usb_device.product_id* and *usb_device.vendor_id*.  We need to verify that the six digit codes (the ones in parenthesis) match up to what is in your HAL.  Which brings us to the next step.

**Step 3:  Correcting Your Computers HAL Config (for Music Players)**

in the terminal enter
```
sudo gedit /usr/share/hal/fdi/information/10freedesktop/10-usb-music-players.fdi
```

In the document, search for your devices section (hit *ctrl+f* and search for 'SanDisk').  You should be looking at a section that looks like this

```
<!-- SanDisk -->
	<match key="@storage.originating_device:usb.vendor_id" int="0x781">
```

As you can see, the vendor id code matches the output from *lshal* so we're good  to go there.  if they do not match, then change the code "0x781" to match whatever the output from *lshal* was.

Then scroll down a bit and look for a section that looks like this (for your device)
```
<!-- Sansa Fuze -->
	  <match key="@storage.originating_device:usb.product_id" int="0x74c1">
```
As you can see, the codes do NOT match.  Change the 6 digit code for usb.product_id to match the output from *lshal*.  In my case I changed it to "0x74c3".
NOTE: You may want to update this section to reflect any other audio codecs that your device is compatible with.  In my case, I just copied the same section from the Sansa Clip because it had all other codecs (ogg, flac, etc.)

Save the document, disconnect the Fuze from your computer and reboot to reload your HAL.  The next time you plug in your Fuze, it should pop up with a message asking if you want to open it with your music player.

I've tested this fix with several music players.  It works with Banshee and Rhythmbox.  No luck on Amarok for some reason.

---

