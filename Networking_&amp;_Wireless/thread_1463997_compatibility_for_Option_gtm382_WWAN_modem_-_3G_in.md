---
title: "compatibility for Option gtm382 WWAN modem - 3G internal mini-PCI"
date: 2010-04-27
forum: Networking &amp; Wireless
---

### Post by ahoros on 2010-04-27
I want to add WWAN connectivity to my Latitude E6400 laptop - and I am considering new GSM modem (so called 4th generation) made by Option designated as GTM382E miniPCI card (embedded module)

I believe previous generation GTM380 was used by Dell in some of their laptops - and likely supported by Linux kernel.

Does any one have any first-hand experience with this newer modem  - and by what version of kernel/Ubuntu it might be supported ?
 
My web searches came back inconclusive
some reseller claims compatibility:
[http://www.novamedia.de/option/e_gtm382.html](http://www.novamedia.de/option/e_gtm382.html)

while the manufacturer web page is vague:
[http://www.option.com/en/products/products/modules/gtm382e/](http://www.option.com/en/products/products/modules/gtm382e/)


(BTW where could I find some authoritative source of kernel hardware compatibility?)
Thanks!@

---

### Post by alexfish on 2010-04-27
Hi

Until someone   posts they had success with the device and also any workarounds . and irrespective of , would recommend the following

1. Ask if they do a money back guarantee and the time limit, if not think twice
2. As said they provide the hso drivers for Linux, these are used if the Kernel does not support the device, so they can be installed if required , try the device first  it may work. as far as I am aware the hso drivers should work with ubuntu 8.04 onward but can't confirm prior to, there has been known issues with certain drivers relative to the version of linux to that end would recommend Ubuntu 9.04 onwards
3. Your option for types of connect are varied as the accept AT commands , so may work with the Network Manager , HSO Connect , or Gnomeppp and wvdial, HSO connect is often used.
4.If you can't get connected,and assuming they have a buy back guarantee ,take it back

regards

alexfish

and hope you get connected  a site worth a visit,
[http://www.pharscape.org/](http://www.pharscape.org/)
also read before you commit

---

### Post by pdc on 2010-04-27
I see Ubuntu already has this device on its website;

[https://wiki.ubuntu.com/NetworkManager/Hardware/3G](https://wiki.ubuntu.com/NetworkManager/Hardware/3G)

seems it needs "hal tweaks" 

which it seems as though Colin Watson can help you with 

[https://wiki.ubuntu.com/ColinWatson](https://wiki.ubuntu.com/ColinWatson)

the folks at PHARscape oversee the ozerocdoff software

[http://www.pharscape.org/](http://www.pharscape.org/)

that is mentioned in the ubuntu post and by alex: ozerocdoff seems to be the way to go to switch option devices

sounds as though the device would give

> ID 0af0:7501     on lsusb

---

### Post by ahoros on 2010-04-28
Thanks for prompt answers.:smile:

The modem is fast and price is attractive, looks like good value for the money.
This site in particular: [http://www.pharscape.org/](http://www.pharscape.org/) makes me hopeful that it can be made to work.
so I am gonna go ahead and order one.

I will report more on it in a week or two  once it arrives.

---

### Post by size_XXM on 2010-05-30
Hi, has your modem arrived yet? I ordered one for my FSC Esprimo U9200 (should arrive in a few weeks). I'm interested in a few details, if you don't mind:
[list][*]Which version of Ubuntu are you using with it - the information on that wiki was entered in January 2009 and may be outdated for Jaunty and newer.
[*]Are you using Ubuntu, Gnome and all that, not KDE? I'm staying with Kubuntu Karmic for various reasons. Hopefully the mobile broadband works in knetworkmanager, which is noticeably behind the gnome applet.[/list]

AFAICT, there are usually two kinds of problems with internal 3G modems:
[list][*]The device not showing up at all - this is usually due to problems between Linux (kernel) and the laptop's wireless killswitch implementation (ACPI perhaps). This may or may not get worse if you use hardware that isn't normally sold with the laptop - the switch may not work or its state may be ignored.
[*]The device shows up as a storage device (typically CD-ROM). This is to provide drivers (for Windows, of course) without having to ship a CD (these things are used typically on netbooks with no optical drive, remember?) and the device needs to be "switched" from the storage-device mode to modem mode. This is (expectedly) undocumented and vendor/product-specific command sent to the device, though some have seen the light and switch from CDROM to modem mode on "ejecting" the disc (see eject utility). Reading articles on this topic, these 'hacks' should be (already?) integrated with udev requiring no user intervention, but if you only see a storage device and no modem, try [here](http://www.draisberghof.de/usb_modeswitch/) and use the usb_modeswitch utility found in the repos.[/list]

---

### Post by pdc on 2010-05-30
you provide very good detail and substance there;

for Option devices, the folks at ozerocdoff recommend their software;

usb_modeswitch is said to cover the option devices also; 

as alexfish rightly said, if someone can source this device as a trial; they can investigate;

I have been very impressed that 10.04 seems to flip devices by itself; (some say usb_modeswitch is part of the build?)

so firstly; if one plugged the device in, and looked at the ID: it may just flip by itself ... before adding ozerocdoff or usb_modeswitch; 

already one user (using MF112) has found removing the usb_modeswitch he added made the device work ... it seems ..

as 10.04 would flip automatically

---

