---
title: "Antec Fusion Remote LCD does not appear in lsusb"
date: 2009-11-13
forum: Mythbuntu
---

### Post by clconway on 2009-11-13
I've got at Antec Fusion Remote Black case with an ASUS M3N78-VM motherboard. I've installed Mythbuntu 9.10 and I'm trying to get the LCD and, more importantly, the remote control to work. I can't even get started, because the LCD does not appear in lsusb:

```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 099a:7202 Zippy Technology Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

(The Zippy entry is my keyboard.)

The LCD has a standard external USB connector and an adapter with a 4-pin internal connector. I've tried both with the same results.

Does this mean that the LCD needs to be replaced? Or is it possible I've set things up wrong somehow? E.g., maybe I've misunderstood and the lsusb line won't appear before I have the correct drivers installed? 

One cause for concern is that there is an unlabeled 3-pin female connector emanating from the LCD area in the case, which is not mentioned in the Antec manual and which I can find no suitable place to plug in. (The cable for it is quite short and doesn't quite reach the motherboard chamber in the case.)

Any advice would be much appreciated!

---

### Post by clconway on 2009-11-14
Thanks to a hint from a [user review from "RG" at Newegg]("http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16811129054"), I realized that 3-pin connector is the power for the LCD. Antec provides a extension cable for the 24-pin motherboard power connection, and that extension cable (which I didn't need for length) has a dongle for the LCD power (which I did need). This is mentioned in the manual, but I found it rather vague.

After plugging in the 3-pin connector, I see the LCD in lsusb, as expected. Stupid mistake. 

I would also note that many of the Fusion Remote/iMon 0038 howto's online are out-of-date wrt karmic. A simple "sudo dpkg-reconfigure lirc", choosing "Soundgraph iMon Antec Veris" is sufficient to get the remote working. This pulls in the packaged config file ```
/usr/share/lirc/remotes/imon/lircd.conf.imon-antec-veris
```.

---

### Post by caish5 on 2009-11-18
So....
does anyone know how to get the LCD working in karmic?
Mine's the ffdc type

---

### Post by vronp on 2009-11-22
Clconway,

Thanks very much for this post.

I'm sure this is the reason my lcd is not showing up as well.

I wonder if I could ask a favor.  I did not get the PSU with the Antec case and I ended up buying a different power supply.

Would you be able to describe for me what the 3 pin cable looks like for the lcd power?  Is it a tiny white connector on the cable and the wires are red, black, and brown?

Any help on that would be greatly appreciated.

I don't know how I will be able to power that connector if that is the one.

thanks,
Dave

---

### Post by clconway on 2009-11-22
Dave, your description of the connector sounds right. It's small. The pins are about the same size as an internal USB connector. The connection comes from a hole on the left side of the front of the case; the same hole where the USB connection for the LCD comes from.

My case didn't come with a PSU either. It came with an extension cable for the 24-pin power connector from the PSU. I.e., the connections look like 

```

power supply
  --> thick power cable with 24-pin connector 
    --> extension cable with 3-pin and 24-pin connectors 
      |-> motherboard power
      |-> LCD power

```

---

### Post by vronp on 2009-11-22
Ok, I went back to the box that contained the Antec case and found the 20 pin power extension cable with the special connector for the LCD.

Now, my LCD works, well sort of.

The remote seems to work but nothing displays on the LCD.  Also, the LCD backlight is always on despite my setting it to not always be on.

Dave

---

### Post by clconway on 2009-11-22
Mine works, but isn't really very useful. I just did ```
sudo service LCDd stop
``` to disable lcdproc. I prefer the clock it displays when disabled to the blinking "LCDProc Server" status display.

---

### Post by vronp on 2009-11-24
This site helped me a great deal:

[https://help.ubuntu.com/community/IMON_VFD_and_LCD_Karmic_9.10](https://help.ubuntu.com/community/IMON_VFD_and_LCD_Karmic_9.10)

Now, it's working "as expected" in Ubuntu.

Now, I have to get Mythbuntu fired up to see what gets displayed on the LCD running Myth.

---

