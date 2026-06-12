---
title: "Need drivers for Clear's Motorola WiMax USB Modem"
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by kneedalz on 2009-12-06
Just got Clear service here in Chicago. Got the service that included a Motorola WiMax USB Modem. When I plug the modem in, it isn't recognized. How do I find the Drivers for it, if there are any. The model number for the modem is USBw 25100. Thanks in advance!

---

### Post by mikew.clear on 2009-12-25
I also need the drivers for the usbw25100, CLEAR USB Modem. Please let me know if you find them or have found them. Thanks

---

### Post by Conzar on 2009-12-28
I also am looking for drivers.  I am using 9.10 on my MacBook.

Interesting to note, the Clear Manager is available for OSX.  I'm not sure if these driver's could be reverse engineered...

---

### Post by capcadetjc on 2010-02-27
I also need these drivers. Is there any updates on this?

---

### Post by princemanjee on 2010-04-04
I also looked into this... so far there is an effort going on
Here:
[http://wireless80211.wordpress.com/2009/11/15/beceem-wimax-on-2-6-30/](http://wireless80211.wordpress.com/2009/11/15/beceem-wimax-on-2-6-30/)
and supposedly Here:
[http://developer.xohm.com/issues/show/51#change-8](http://developer.xohm.com/issues/show/51#change-8)

Looking into it further My computer recognizes it as a Beecam USB Device Recognizes (lsusb) but will not utilize or allow me to use to connect to any network.

And I thought hey all else fails I'll try NDISWrapper.... that didn't work either... Any one else hate proprietary hardware? If you [Motorola] wanna lock it up fine just make it work then so we don't have to.

I could use some help here I don't wanna lug around a big RSU and battery pack thats just retarded for "mobile computing" at the same time I hate the idea of always being forced to carry something running Wintendo and I am tired of dual boot thats why I have two separate laptops... Some one please connect the dots on this one and get it working...

---

### Post by schmickey on 2010-04-04
My Clear 4G WiMax USB doesn't say Motorola on it.  It says only Clear 4G Mobile USB, model PXU190 (as reported by Windows) or PXU1900 (what's printed on the back of the dongle).

It's a terrific service.  I hope they or someone comes up with Linux software/drivers soon.  I hate having to have a dual-boot setup with Windows just so I can use my mobile broadband.

---

### Post by princemanjee on 2010-04-05
Agreed, someone from Motorola and the maker of the PXU1900 (Diff model modem), should follow through and release either the schematics/source needed for the community to provide one OR more appropriately since it is there hardware they should do the responsible thing and support it's users by writing and releasing a drive. You would think that would be easier and cheaper than writign one for Windows since Microsoft charges such ridiculous fees for Licenses of Visual Studio and the Windows API isn't exactly open source for anyone to manipulate like EVERY flavor of linux... Basically Linux makes it easier and provides all the tools yet the people from Motorola seem to be so far up steve balmers nether regions to actually figure it out... by the way Hello Moto, Hows that taste?

They know full well at least a large piece of the market for their offering is going to be the Geek community and that largely includes NON WINDOWS users. Alienating these folks only serves to push for competition from companies like Google that plan to offer GB Speeds on their upcoming FREE WiMax Offering... Free unlimited access internet or $30 limited access from Clear... (Limited by their ability to support their product) Who is gonna win?

I was on line with Clear's customer support for over an hour yesterday trying to come to a solution. Listing to their support staff is like taking advice from a monkey to do a math problem. As far a I can see the only thing good about clear is the network speed. Hardware is limited, sales staff is sleazy and will say anything to get you to buy it (including lie to me since I was told the USB device would work on ANY system), and their support staff is filled with idiots reading from a script or knowledge base with no ability to comprehend the questions being asked of them. (Which means I understand how the product works better than the guy providing support... BAD).

---

### Post by schmickey on 2010-04-06
Prince:  Yes, you're right about the sales staff and the support people.  I have the newer and slightly larger USB modem.  It's made in China by a company called Ubee.  It might be just a re-branded Motorola, I don't know.  This newer unit is designed to be used (if you want to) in a "dock" they call it.  Supposedly to improve reception -- but if you're near a tower, it only impedes the signal, not improve it.  The "dock" is just a little platform that acts like an antenna and signal booster but it really isn't worth anything unless you're in an area with a weak signal.

The connection software and drivers come from a company called Smith Micro Software.  I emailed their developers and they replied that they will only write drivers/software that are requested by Clear.  Talking to the salesman I bought from, he said there just wasn't enough demand for Linux software/drivers and he didn't think they'd be providing any.  I think the best hope is for someone to reverse-engineer the Mac OSX software and driver since OSX is a *nix variant, like Linux.  I think it's based on BSD.

Did you say "FREE" WiMax from Google?  I wonder if our Clear modems would work with that.  Probably not.  The Clear account is based on the MAC address of the USB unit you have.  Google might work the same way unless you can buy a "generic" USB modem.

---

### Post by Shazzner on 2010-06-08
Supposedly they're working on them: [http://forums.clear.com/clearcom/topics/will_there_be_usb_modem_drivers_for_linux](http://forums.clear.com/clearcom/topics/will_there_be_usb_modem_drivers_for_linux)

No ETA on their release however.

---

### Post by princemanjee on 2010-06-08
> **Shazzner said:**
> Supposedly they're working on them: [http://forums.clear.com/clearcom/topics/will_there_be_usb_modem_drivers_for_linux](http://forums.clear.com/clearcom/topics/will_there_be_usb_modem_drivers_for_linux)

No ETA on their release however.

Clear Waited too long and I was able to get out of any early termination fee thanks to a loophole in clear's agreement, and I switched out for an EVO 4G. Works on the same network as clear and only costs me 10 bucks more a month instead of 30. Clear choice is not Clear anymore.

Their sales person Chris in the Chicago area was a sleazy, shifty douche bag anyways, I caught him in so many lies just trying to close the deal, totally unscrupulous. Almost a great offering but they screwed it up with cheap hardware and cheap support staff.

---

### Post by JasonSpradlin82 on 2010-12-02
Latest update I can find on this is this git repository where someone has been working on it, but suddenly no changes since Nov 1, 2010:

[http://git.kernel.org/?p=linux/kernel/git/shemminger/beceem.git;a=blob;f=drivers/staging/bcm/TODO;h=366634be5fe1d4cf2065f57d480230dbc1a754d9;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/shemminger/beceem.git;a=blob;f=drivers/staging/bcm/TODO;h=366634be5fe1d4cf2065f57d480230dbc1a754d9;hb=HEAD)

---

### Post by jacky.alcine on 2012-09-25
Hey everyone.

I might have revived an old forum thread, but I'm looking into some of this work myself.

After reading [http://geek.the-daver.com/clear-usb-4g-on-linux-a-saga](http://geek.the-daver.com/clear-usb-4g-on-linux-a-saga) and seeing the results of one of the commenter's successes, I'm going to take a dive and see if it can be done. 

If so, I'd begin setting up a PPA so that we could all use this.

[FONT="Courier New"]uname -a[/FONT] reports:
```
Linux jalcine-laptop 3.2.0-31-generic-pae #50-Ubuntu SMP Fri Sep 7 16:39:45 UTC 2012 i686 i686 i386 GNU/Linux
```

Wish me luck!

---

### Post by jacky.alcine on 2012-09-26
> **Shazzner said:**
> Supposedly they're working on them: [http://forums.clear.com/clearcom/topics/will_there_be_usb_modem_drivers_for_linux](http://forums.clear.com/clearcom/topics/will_there_be_usb_modem_drivers_for_linux)

No ETA on their release however.

This doesn't exist anymore :/

---

