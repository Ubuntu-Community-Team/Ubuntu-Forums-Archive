---
title: "Ubuntu Atrix Problems"
date: 2011-05-10
forum: Multimedia Software
---

### Post by MikeyDL on 2011-05-10
I just got a Motorola Atrix yesterday.  Figured I could just use Banshee to manage the device in Ubuntu like I did with my prior IPhone.  However, banshee doesn't seem to pick up the device.  I found a bug report on it which stated to add the following to recognize the device.

<MassStorageDevice class="Banshee.Dap.MassStorage.AndroidDevice"
vendor-name="Motorola" product-name="Atrix"
vendor-id="0x22b8" product-id="0x7086"/>

However, they dont' tell you what file to add it to.  I did add those lines to /home/michael/.config/banshee-1/addin-db-001/config.xml which was the only xml file I could find for banshee.  However, still doesn't work.  

Does anyone have any experience getting the Atrix to work in banshee.  

Or does anyone know of another manager I would be able to use to manage music and video on Ubuntu.  

The only official way to do this is to use Windows Media Player or the motorola app both of which are Windows/Mac.

Thanks!

---

### Post by mlwalla on 2011-06-24
I would be equally curious to get this working with rhythmbox... just got the phone yesterday.

---

### Post by mlwalla on 2011-06-24
*UPDATE*

Here's an alternate fix, which works for Rhythmbox as well:
From [http://www.webupd8.org/2010/06/how-to-use-rhythmbox-to-transfer-music.html](http://www.webupd8.org/2010/06/how-to-use-rhythmbox-to-transfer-music.html)

1. Set the Atrix to interact as a USB Mass Storage Device under the phone's usb menu (accessible via the notifications drop down while plugged in).
2. Create the file **.is_audio_player** in the Atrix's top directory
3. Add the following lines to the new file:
> audio_folders=mp3/
folder_depth=1




The fix alluded to in the previous post is meant to work if you're building from source.  I haven't tried this yet, because I still use rhythmbox and also not too comfy building from source, but here's some links anyway

Here's the original workaround:
[http://banshee-media-player.2283330.n4.nabble.com/Motorola-Atrix-support-td3336278.html#a3336298](http://banshee-media-player.2283330.n4.nabble.com/Motorola-Atrix-support-td3336278.html#a3336298)

Source available on banshee download page:
[http://banshee.fm/download/](http://banshee.fm/download/)

Here are some old instructions on how to install banshee from source:
[http://vivapinkfloyd.blogspot.com/2008/08/how-to-compile-and-install-banshee-120.html](http://vivapinkfloyd.blogspot.com/2008/08/how-to-compile-and-install-banshee-120.html)

---

### Post by Veritas_08 on 2011-06-24
I was having a similar problem with my Droid X and Banshee. I then downloaded Rhythmbox to see if it would work. Nothing there either. There was no syncing of music files. 

In the readout for my SD card, it showed all my files were filed under "Other". For the music files I use iSyncr (paid app) to sync my iTunes library to the DX. I looked in my music file on the phone with Astro File Manager (free app on the Market,) and all my files were in a file called syncr, which is why it seems Banshee didn't seem to pick them up. With Astro, I copied all my files from syncr file to the music file. 

I then hooked up to the computer, selected the USB Mass Storage option and Banshee started reading the files. I think Rhythmbox could read them then, too. I have no sound working now so I can't verify that the songs do play. I read posts similar to the one above but it seems that only works if your phone is rooted which mine is not. 

I'm a newb to Ubuntu and Linux so I didn't wanna mess with rooting yet, though it seems straightforward enough. It does however void the warranty on your phone. 

Anyways, hope this helps :)

---

