---
title: "Toshiba Gigabeat access via Linux?"
date: 2007-02-11
forum: Multimedia &amp; Video
---

### Post by YoungCthulhu on 2007-02-11
Gidday!

I have a Toshiba Gigabeat and it is a constant source of annoyance to me that I can only use Windows 2000 + the "Gigabeat Room" program to transfer CDs from my collection onto the player.  I know that Windows Media Player will transfer directly to the Gigabeat but that runs under XP and I don't want to install it.

I have just found that I can access the files, copy and re-name them using Thunar on my Xubuntu 6.06 desktop (running 686 kernel on and old PIII) but as expected, cannot play the special .wma.sat files that the Gigabeat runs on.

Has anybody else who owns this music player found a way round this using this?  Can you convert wma.sat files (or even just wma files) to mp3 flies and back again? :confused:

Cheers

---

### Post by DerArzt on 2007-02-13
I've had some of the same issues and i ended up putting linux on my gigabeat as a result. :lolflag: If your interested, look at [www.rockbox.org](www.rockbox.org). It took me a while to figure it all out but in the end its pretty cool. IM me if you are interested and/or have questions.

---

### Post by trippinnik on 2007-02-24
Ok I've got the libmtp2, amarock compiled to use mtp, but mtp isn't detecting my device.  it's a gigabeat p20, i haven't been able to find a supported device list except for the XNJB project which uses the same lib [http://www.wentnet.com/projects/xnjb/device-list.html](http://www.wentnet.com/projects/xnjb/device-list.html) 
the P10 is listed and the USB ID i got from lsusb is the same, but mtp doesn't detect the device.  On the list it says it is untested.  Anyone have one of these devices or have any ideas?

---

### Post by headontheground8 on 2007-05-14
I'm having the same problem. I had it with windows, and finally got rid of it and got Ubuntu just last night. No complaints except I forgot about my media player. I checked out the Rockbox program, looks good but will not work with the Gigabeat S. It doesn't look hopeful, but anyone got any ideas?

---

### Post by trentend on 2007-06-16
> **trippinnik said:**
> Ok I've got the libmtp2, amarock compiled to use mtp, but mtp isn't detecting my device.  it's a gigabeat p20, i haven't been able to find a supported device list except for the XNJB project which uses the same lib [http://www.wentnet.com/projects/xnjb/device-list.html](http://www.wentnet.com/projects/xnjb/device-list.html) 
the P10 is listed and the USB ID i got from lsusb is the same, but mtp doesn't detect the device.  On the list it says it is untested.  Anyone have one of these devices or have any ideas?

The rockbox gigabeat S port, is in development, and making decent progress.

[http://www.rockbox.org/twiki/bin/view/Main/GigabeatSInfo](http://www.rockbox.org/twiki/bin/view/Main/GigabeatSInfo)

---

### Post by YoungCthulhu on 2007-06-19
I finally got round to installing RockBox firmware and bootloader on my Toshiba F20 over the weekend, and after a few minor teething problems it works and I couldn't be happier!  \\:D/

After ripping a few CDs to the FLAC format I have suddenly lost interest in the Toshiba files I took so long to load on, using Gigabeat Room!.  I have backed all of the .wav.SAT files off to make room for a completely Open Source set up :D .  Who cares if I can't get as many files on to the 20Gb disk, the quality is amazing, and moving stuff across from the computer HD to the Gigabeat takes at most a few seconds.

Thanks for your advice, Artz!! 

Cheers

---

### Post by Afkpuz on 2007-11-16
I'm not sure if you still want to know how to convert your .sat files, but here is how to do it.  You'll need a windows box with the latest windows media player installed.

In the normal gigabeat environment (not rockbox), goto Settings>Pc Connections
Tell it to use windows media player.

Then, plug the gigabeat into cradle with cradle set to "usb".  Plug in power and usb cable to comp and turn on your gigabeat.  

Gigabeat should come up in windows explorer.  If it can't find driver, make sure you have gigabeat room installed and set gigabeat to use gigabeat room first.  Windows should install driver for it.  Then, go back to settings and tell it to use media player.

Navigate to the music folder on your gigabeat and begin copying files.  You should notice that the music is in normal .wav format.  Copy from here.  Just note that for some reason, it runs at usb 1.x speeds, so be patient.  

Thats all!   This info is also available on the rock box website.

---

