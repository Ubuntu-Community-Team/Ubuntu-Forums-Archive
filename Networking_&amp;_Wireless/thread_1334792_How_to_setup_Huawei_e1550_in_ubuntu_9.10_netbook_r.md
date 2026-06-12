---
title: "How to setup Huawei e1550 in ubuntu 9.10 netbook remix?"
date: 2009-11-22
forum: Networking &amp; Wireless
---

### Post by Jeboy on 2009-11-22
Hi,

I have SUN Broadband Wireless (an internet service in the philippines) that comes with Huawei e1550 usb modem, how can I setup that modem in ubuntu 9.10 netbook remix os? I tried these:

[COLOR=#000000][COLOR=#0000BB]sudo apt[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]get update [/COLOR][COLOR=#007700]&& [/COLOR][COLOR=#0000BB]sudo apt[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]get install udev[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]extras
[/COLOR][/COLOR]
but it returns an error [COLOR=Red]"Package udev-extras is not available... E: Package udev-extras has no installation candidate"[/COLOR]

Thank you

---

### Post by pdc on 2009-11-23
If you go down to the section that says 

"Create a mobile broadband connection":

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

does this help you?

I would just try the stock 9.10 and see what happens:

---

### Post by tonytinsay on 2009-12-13
hi, i am new to linux / ubuntu.

thus,i dont know yet the intricacies of compiling and generating a executable of ozerocdoff.

cud u please direct me where to download a ready to install file and instructions for a one click installation of  said file?

thanks.:(

---

### Post by adamdavidhughes on 2010-02-23
I've just installed ubuntu 9.10 netbook remix on my eeepc (901) and I found the automatic set up worked fine.
I set my connection by :

1. Log in to your pc as normal
2. Plug in your usb modem
3. Click on the network connection icon in the top menu bar (it's the icon that looks like the signal bar in a mobile phone, it's also the one nect tp the battery indicator on a default install)
4. Take option new obile broadband connection
5. You'll then start the new mobile broadband connection wizard. Click on forward
6. Select your country (mine was uk)
7. Select your provider (mine was 3)
8. Select plan handsets (I selected this one as the standard APN for 3 is three.co.uk and this is the one used by the handsets plan). If you don't know your APN , just ring your supplier and ask them, they will tell you.
9. Click forward and teh connection is set up and worked for me.

All worked (fantasic update by the way ubuntu, everything just seems to work on my eeepc)

---

### Post by adamdavidhughes on 2010-02-23
I did find one issue after installing it for the first time.
The first time it worked fine, but then afterwards when I inserted the usb modem it mounted it as a cdrom rather than a modem driver.

To get around this I installed usb-modeswitch. You need to be connected to the internet to do this , so either connect via another method or (as I did) simply unplug and replug the usb modem in, but as soon as you plug it in keep clicking on the network connections icon in the top menu bar, before the usb modem get's mounted as a cdrom it will allow you to connect using the profile you created (in my previous thread).

You can install it by doing the following:

1. Log into your pc as normal
2. start a terminal
3. enter command sudo apt-get install usb-modeswitch
4. You will be asked for your password. Enter it and usb-modeswitch will be installed.

Once installed []("http://www.draisberghof.de/usb_modeswitch/")mine worked fine from then on.

---

