---
title: "Usb-modeswitch out of the box so that 3g dongles work?"
date: 2010-05-10
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Johnsie on 2010-05-10
Hi,
    I recently bought a mobile Internet dongle. The problem is that I need to install usb-modeswitch to get it working. Can this be added to Maverick?


Downloading the package using my ethernet connection worked for me, but If the usb dongle is the only way the user can get online then this is going to be a big problem. 

Many people use these dongles as part of their job so that they can get online when out of the office or on the move. As hsdpa dongles are becoming alot more popular I think that the next version of Ubuntu needs to do more to support them out of the box.

---

### Post by caryb on 2010-05-10
I.m sort of relating to this! in Kubuntu you need to install Kppp to connect to the net with a modem. That is a problem if you only have dialup access.


Cary

---

### Post by phenest on 2010-05-20
I'm using Debian Squeeze without the usb-modeswitch package on a 3g network, and it works fine.

---

### Post by taavikko on 2010-05-20
> **phenest said:**
> I'm using Debian Squeeze without the usb-modeswitch package on a 3g network, and it works fine.

Yeah, some of the dongles work, some not, hence the need for usb-modeswitch.

---

### Post by phillw on 2010-05-20
And, oddly enough, mine works on the development kernel but not *22

Still, the dev kernel should hit 10.10 at some point :-)

Regards,

Phill.

---

### Post by Slug71 on 2010-05-20
> **Johnsie said:**
> Hi,
    I recently bought a mobile Internet dongle. The problem is that I need to install usb-modeswitch to get it working. Can this be added to Maverick?


Downloading the package using my ethernet connection worked for me, but If the usb dongle is the only way the user can get online then this is going to be a big problem. 

Many people use these dongles as part of their job so that they can get online when out of the office or on the move. As hsdpa dongles are becoming alot more popular I think that the next version of Ubuntu needs to do more to support them out of the box.

While i dont use a USB dongle, i can agree with this. They are becoming very popular.

---

### Post by uRock on 2010-05-21
Not sure what a dongle is, never seen it on the packaging of a product. Would having usb-modeswitch make usb wireless NICs work? I have on that is not recognized in Lucid.

---

### Post by uRock on 2010-05-21
> **phenest said:**
> I'm using Debian Squeeze without the usb-modeswitch package on a 3g network, and it works fine.

Check the Screenshot.

---

### Post by phenest on 2010-05-22
> **uRock said:**
> Check the Screenshot.

If you're referring to the "On Debian, this is not needed..." bit, then that applies to Ubuntu too.

And I've also found installing that package does not hide the storage device.

---

### Post by cariboo on 2010-05-22
@uRock. check [this]("http://en.wikipedia.org/wiki/Dongle") out for more info on dongles.

---

### Post by Slug71 on 2010-05-23
> **uRock said:**
> Not sure what a dongle is, never seen it on the packaging of a product. Would having usb-modeswitch make usb wireless NICs work? I have on that is not recognized in Lucid.

A USB wireless NIC would be a dongle.

---

### Post by rajeev1204 on 2010-06-04
This should definitely be there in 10.10 .

In india 3g has just been launched, but even the older data cards for mobile broadband dont work without the usb modeswitch package.

So that means alt least some thousand users in india dont get connectivity out of the box.


For those who dont know, the mode switch package allows detection of the usb mobile device as a gsm modem instead of a usb storage device.


rajeev

---

### Post by phenest on 2010-06-04
Perhaps I could recommend the Huawei E169 usb dongle, as it works fine without that package and operates both modem and storage simultaneously. Although, lsusb shows it as a Huawei E620, but it's definitely an E169.

---

### Post by bennachie on 2010-06-04
Quite a few of the later model 3g dongles do require usb-modeswitch, either directly or indirectly. From recent personal experience, I can confirm that Vodafone dongles issued in the UK or AU and using the Huawei 3765 modem come into that category. 

Mint 9 does come with usb-modeswitch installed out of the box.

---

### Post by phillw on 2010-06-04
There's an elephant in the room :mad:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/529794?comments=all](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/529794?comments=all)

I'm still awaiting some one to get back in touch, I even keep the deb package for the 999 kernel on my system.

It's a very lonely bug, especially annoying that they could ask me for any logs / traces between it working and not working.

And there was me, thinking that they took regressions seriously

C'est la vie :confused:

Regards,

Phill.

---

### Post by mahela007 on 2010-06-28
I have a Huawei E1569G. Did USB modeswitch work without any hitches ? Did y'all install it from the repos?

---

### Post by teh603 on 2010-06-29
I've been using a SierraWireless Mercury since Intrepid, and have never had to install usb-modeswitch. I've had to haxx the fark out of Hal, but that's another story entirely.

---

### Post by alexfish on 2010-07-27
There is much work still to be done in this area


  usb-modeswitch is on going and progressive, it will now activate on the connection of the device
 however when installed it will switch some devices back to storage mode.  
 Sakis3g over comes this by recognising if the device is switched or unswitched state, so if in the uswitched state it will call the usb-modeswitch ,  
 

 udev attempts are not as progressive ,one has to learn how to write the rules etc if the device is not recognised, not the way to go if your a newbie to linux ,  even if the device is recognised , that  mass storage device still appears on the desktop, leaving the user to eject or safely remove it , this to also posses problems as how the device is switched. It will present a port recognition problem where by Network Manager : Modem Manager  fails to see the device ports correctly , this may be a bug caused by the device its self , or by the driver failing to set the [COLOR=#000000]CTS,DCD and DSR lines of the serial port. So [/COLOR]**[COLOR=#000000]probing the correct ports can be an issue[/COLOR]**
 

  [COLOR=#000000][How To : Mobile Broadband Connections [ Ubuntu 10.04 : 9.10 : 9.04 ]]("http://ubuntuforums.org/showthread.php?t=1466490")   post #[/COLOR]**[[COLOR=#000000]16[/COLOR]]("http://ubuntuforums.org/showpost.php?p=9483244&postcount=16")**
 

 **[[COLOR=#000000]Huawei 3G modem[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1436954")**
 

 [COLOR=#000000]From where I sit usb-modeswitch is a must on system  although should only be called when required[/COLOR]
 [COLOR=#000000]IE :done by the Manager responsible for the connection as in Sakis3g, only hoping usb-modeswitch is maintained in the longterm { think this is an area Ubuntu could look at as it is in the repos }[/COLOR]
 

 [COLOR=#000000]Finally UDEV . I think the wings are spreading to far into a ever changing technology ,{can't keep up }[/COLOR]

---

### Post by x-shaney-x on 2010-07-28
Isn't that what modemmanager is supposed to be doing eventually?

Though I do agree USB modeswitch should be there by default.
mobile broadband compatibility seems to have regressed since karmic.
I have 2 old dongles that worked out of the box on karmic but wouldn't work on lucid or maverick without modeswitch.

---

### Post by recluce on 2010-07-29
No idea what package in Ubuntu is to blame here, but I have issues with my Huawei E220 (Vodafone) stick since the beta versions of Lucid. Unfortuntately, I cannot really test this, since I only use that stick when visiting Germany (a couple of times a year) and there are no obvious error messages.

In Jaunty (and early Lucid alpha versions): perfect function, storage device invisible, reliable fast connections

Since Lucid betas: stick is recognized, but storage device is visible. Connections are flakey, Ubuntu tends to "loose" the stick - so you need to disconnect and reconnect it to make it work again. Communication is much slower and there are frequent disconnects/reconnects. I verified that it was indeed the OS (and not network issues) by booting back into Jaunty, were everything worked as it should.

@phillw: I also tend to loose faith that any of the developers take regressions seriously, unless it bites them personally

---

### Post by alexfish on 2010-07-29
> **recluce said:**
> No idea what package in Ubuntu is to blame here, but I have issues with my Huawei E220 (Vodafone) stick since the beta versions of Lucid. Unfortuntately, I cannot really test this, since I only use that stick when visiting Germany (a couple of times a year) and there are no obvious error messages.

In Jaunty (and early Lucid alpha versions): perfect function, storage device invisible, reliable fast connections

Since Lucid betas: stick is recognized, but storage device is visible. Connections are flakey, Ubuntu tends to "loose" the stick - so you need to disconnect and reconnect it to make it work again. Communication is much slower and there are frequent disconnects/reconnects. I verified that it was indeed the OS (and not network issues) by booting back into Jaunty, were everything worked as it should.

@phillw: I also tend to loose faith that any of the developers take regressions seriously, unless it bites them personally

if your modem is k3565

if so ,the vodafone Model {k3565} list on the system as E220 because of the ID's it gives, and is a known problematic device

this is how it goes 

I have a vodafone k3565 ids 12d1:1003 so the system will see it as a huawie E220 E270

this device may be a  E620 USB Modem true IDS are 12d1:1001

so depending on how it is configured it can present it,s self as two different modems

also it has different actions depending how it is switched , { number of ports and port sequence can vary }

this is not a regression as one may think , the kernels are improving at recognising more devices and act on the device id, 

this a problem for the Huawie the services providers as regarding firmware and software etc , as to the ID's it presents to the system

there are instances of firmware upgrades changing the device id's of other models , and the only solution is to use usb-modeswitch

---

### Post by plun on 2010-07-29
> modemmanager (0.3-2) unstable; urgency=low

  [ Alexander Sack ]
  * also bump debhelper build-depends to >= 7
    - update debian/control
  * **recommend usb-modeswitch**
    - update debian/control

[https://lists.ubuntu.com/archives/maverick-changes/2010-July/003688.html](https://lists.ubuntu.com/archives/maverick-changes/2010-July/003688.html)


Updated July 20

---

### Post by alexfish on 2010-08-01
> **phillw said:**
> And, oddly enough, mine works on the development kernel but not *22

Still, the dev kernel should hit 10.10 at some point :-)

Regards,

Phill.

                                 **Usb-ModeSwitch** provides a way for switching USB devices which need to be [mode-switched]("http://wiki.sakis3g.org/wiki/index.php?title=Mode_switch") before becoming usable. Seems like [USB modems]("http://wiki.sakis3g.org/wiki/index.php?title=USB_modem") had been one of the first consumer products widely adapting this attitude, which settles **Usb-ModeSwitch** a *must* tool for anyone holding such a device.  
 While new [switchable]("http://wiki.sakis3g.org/wiki/index.php?title=Mode_switch") devices keep popping up every day (given the high penetration rate of [3G USB modems]("http://wiki.sakis3g.org/wiki/index.php?title=USB_modem")), most distributions either:  
 
[LIST]
[*]have not yet adopted     **Usb-ModeSwitch** within their repositories, or
[*]provide an outdated version of     **Usb-ModeSwitch**, or
[*]do not provide updates to its     *device database* in a timely manner, or
[*]still use the, [now     obsolete]("http://markmail.org/message/k662fucn5ab2gfc5"), Modem-modeswitch for providing similar services only     for a limited subset of devices **Usb-ModeSwitch** does.
[/LIST]
 after reading will now understand the problems with modem-modeswitch
incorrectly switched devices fail to assert the serial lines / have see many post regarding this problem , even when r a successful connection fails
a typical solution is to use a script / zip file see attatchments

 Source
 [http://wiki.sakis3g.org/wiki/index.php?title=Usb-ModeSwitch](http://wiki.sakis3g.org/wiki/index.php?title=Usb-ModeSwitch)

---

