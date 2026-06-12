---
title: "Linksys WUSB11 in 10.04 Lucid Lynx"
date: 2010-05-15
forum: Networking &amp; Wireless
---

### Post by opensourceguy on 2010-05-15
Hello, I just got my Linksys WUSB11 (atmel chip) version 2.8 working on my 10.04 Lucid Lynx system and just thought I'd share the steps I went through to get it working for those in a similar predicament.


[LIST=1]
[*]Download at76_usb-firmware-0.1.tar.gz from [http://at76c503a.berlios.de](http://at76c503a.berlios.de)
[*]Extract it somewhere
[*]Change to extracted directory
[*]In terminal type > sudo cp *.bin /lib/firmware
[*]In terminal type > sudo gedit /etc/modprobe.d/blacklist.conf and enter > blacklist at76c50x-usb  at end of file (I had to do this because without blacklisting this driver I could only view networks but not connect)
[*]Install linux-image-2.6.31-10-rt from Ubuntu Lucid repos
[*]Reboot into new kernel at Grub menu
[*]Plug in your WUSB11 device
[*]Presto! You should now have a working wireless card.
[/LIST]
I would greatly appreciate some feedback as to whether this solution worked for you too.  Happy surfing!

-- OpenSourceGuy

---

### Post by Jurgen Oscar on 2010-06-02
downloading the package...

---

### Post by Jurgen Oscar on 2010-06-04
> **Jurgen Oscar said:**
> downloading the package...

installed....

got only black screen and a mouse pointer...

what happened ?

sigh......

help me....

---

### Post by AlanMacdonald on 2010-06-07
Thanks for posting the steps.  I am going to try this tonight as I figured out to download the firmware but I then experienced this issue of being able to view the network but not connect.  I don't know much about blacklisting so thanks for the tip.

I'll let you know if it works and if it does I owe you one :-).

Jurgen did you experience the black screen after downloading the firmware or the kernel?  I'm guessing kernel?

---

### Post by Jurgen Oscar on 2010-06-08
> **AlanMacdonald said:**
> Thanks for posting the steps.  I am going to try this tonight as I figured out to download the firmware but I then experienced this issue of being able to view the network but not connect.  I don't know much about blacklisting so thanks for the tip.

I'll let you know if it works and if it does I owe you one :-).

Jurgen did you experience the black screen after downloading the firmware or the kernel?  I'm guessing kernel?


Hello AlanMacdonald,

Yes, black screen...with just the mouse pointer on the screen...and it hangs there.

Cheers,

---

### Post by Linux000 on 2010-07-19
Um, that firmware file no longer exsits, or I just can't find it. The only one I can find doesn't have a .bin file in it, just a bunch of headers, is this the wrong file, or do I have to compile it for my computer?

---

### Post by bkratz on 2010-07-19
> **Linux000 said:**
> Um, that firmware file no longer exsits, or I just can't find it. The only one I can find doesn't have a .bin file in it, just a bunch of headers, is this the wrong file, or do I have to compile it for my computer?



There may be some help for you here, at least a good explanation.

[http://georgia.ubuntuforums.org/showthread.php?p=9302171](http://georgia.ubuntuforums.org/showthread.php?p=9302171)

---

### Post by Linux000 on 2010-07-19
Found the file, 
[http://prdownload.berlios.de/at76c503a/at76_usb-firmware-0.1.tar.gz](http://prdownload.berlios.de/at76c503a/at76_usb-firmware-0.1.tar.gz)
Thanks for the help. Hope this works. BTW, does anyone know how(if you can) get WPA2 to work in this card?

---

### Post by bkratz on 2010-07-19
> **Linux000 said:**
> Found the file, 
[http://prdownload.berlios.de/at76c503a/at76_usb-firmware-0.1.tar.gz](http://prdownload.berlios.de/at76c503a/at76_usb-firmware-0.1.tar.gz)
Thanks for the help. Hope this works. BTW, does anyone know how(if you can) get WPA2 to work in this card?




Well, I don't know how to tell before installation, but once installed you will be able to run

```
sudo iwlist wlan0 auth
```

substituting  wlan0 with whatever your wireless name is ( could be several different ones ( like ra0, eth1, etc.)).  This will give the encryption details.

---

### Post by deverne on 2010-08-01
Thanks very much for the workaround by using the 2.6.31 staging driver at76_usb, it worked for me. Just to let you know that this issue is tracked at kernel level and is still not resolved.

You can follow the progress with this URL.
[http://marc.info/?l=linux-wireless&w=2&r=1&s=at76&q=b](http://marc.info/?l=linux-wireless&w=2&r=1&s=at76&q=b)

This is special research inside linux-wireless list archive hosted by marc.info.

Hope this bug will be solved soon.

Deverne

---

