---
title: "Linux driver for  iFox HSPA 820 AirCard"
date: 2010-06-01
forum: Networking &amp; Wireless
---

### Post by Sisophon2001 on 2010-06-01
Hi,

I am hoping somebody will have some information about a driver or instructions to use the iFox HSPA 820 AirCard. I sent an email to their contact address but have had no reply after two working days. Perhaps two days is not so long to wait?

Anyway, according to their site, one of the supported OS is Linux

**[See: iFox HSPA 820]("http://www.ifoxonline.com/product-detail.php?ProductID=72")**

So I hoped somebody else has used this device with Ubuntu.

Thanks,

Garvan

---

### Post by Sisophon2001 on 2010-06-07
one more try ...

---

### Post by pxr on 2010-06-21
Hi, I've just been playing with an iFox EDGE 700 and finally got it to work by:-

right-clicking on the icon that comes up on the desktop and choosing 'eject'

Then it shows up in 'Network Manager' against my pre-set mobile broadband for AIS (I'm in Thailand) - clicked it and it connected.

But that was on an Acer laptop running Ubuntu 9.10.

On an Eee PC running eeebuntu 3.0 I did the same and /var/log/messages shows it as recognized and loads the kernel module:-

cdc_acm: v 0.26:USB Abstract Control Model driver for USB modems and ISDN adapters

and gives it the address tty/ACM0

but for some reason it won't show in Network manager, though I'm sure if you know how to make it dial with some other program that would work.

Hope this helps

---

### Post by Sisophon2001 on 2010-06-21
Hi,

On my Ubuntu computers the iFox 820 dose not even show up as an icon, so I cannot click eject like you describe. Still your post has given me some hope that it can work.

I use a TRUE sim when I visit Bkk, but I guess it makes no difference from AIS. I also have an EeePC running ubuntu 9.10 that is currently doing service as a music player, so I must try it on that.

Thanks for your help,

Garvan

---

### Post by anurak_d on 2010-07-11
Am,too.
I just buy it today,unfortunately for me.
How should we do next?

---

### Post by Sisophon2001 on 2010-08-11
In am not in Thailand now, but I just got the iFox working with a local sim card in Cambodia, and I hope I will be able to get it working when I return to Thailand.

First I ran the command
```
lsusb
```
to get a list of installed usb devices.

Then I plugged in the iFox usb modem, and after waiting a few seconds, I ran the same command again.

It reported a new USB device as follows

BUS 003 Device 003: ID 1c9e:6061

I could see it was the iFox modem because it was the only line that did not identify the USB device by name, and it had changed from the last time I ran the command.

I then ran this command

```
sudo modprobe usbserial vendor=0x1c9e product=0x6061
```

and the modem was recognised automatically by ubuntu, so I could use it via the network icon on the top panel.

When in Thailand next I will test it with my TRUE sim.

Garvan

---

### Post by anurak_d on 2010-08-19
Oh.. Thanks alots Garvan
I just know how to make it work!
But, an old one 820 series have a problem then am get a new one from service center
They change a new 800 series for me, it work! just install a usb-modeswitch command.
I found this trick from Thai local community.

---

### Post by Sisophon2001 on 2010-08-19
> **anurak_d said:**
> Oh.. Thanks alots Garvan
I just know how to make it work!
But, an old one 820 series have a problem then am get a new one from service center
They change a new 800 series for me, it work! just install a usb-modeswitch command.
I found this trick from Thai local community.

Can you give a link to the article in the Local Thai Community? If the article is in Thai, I can have it translated.

Thanks,

Garvan

---

### Post by anurak_d on 2010-08-20
Certainly, here you are
[http://forum.ubuntuclub.com/forum/topic,17176.0.html](http://forum.ubuntuclub.com/forum/topic,17176.0.html)
but, it is in Thai, may be you can use a google's translator it fairly to used, not best.
goto [http://translate.google.com/](http://translate.google.com/) then past above link into text box and click translate button

---

### Post by Sisophon2001 on 2010-08-21
> **anurak_d said:**
> Certainly, here you are
[http://forum.ubuntuclub.com/forum/topic,17176.0.html](http://forum.ubuntuclub.com/forum/topic,17176.0.html)
but, it is in Thai, may be you can use a google's translator it fairly to used, not best.
goto [http://translate.google.com/](http://translate.google.com/) then past above link into text box and click translate button

Thanks, Garvan

---

