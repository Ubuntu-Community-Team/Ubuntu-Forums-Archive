---
title: "Huawei EC1261 Problem in 10.4"
date: 2010-08-17
forum: Networking &amp; Wireless
---

### Post by dannelb on 2010-08-17
Hello,

I have looked all around this forum and some other websites. I did see the other thread about this same device and tried all the things suggested there, but it didn't work.

My problem is that Ubuntu is not able to connect to the internet using my Huawei EC1261.

I have two laptops, one is an old Dell Inspiron 9300 and I also have a Samsung NC10 Netbook. The Inspiron is set up as dual boot with XP and Ubuntu 9. The Samsung is set up as a single boot Ubuntu 10.4.
The Inspiron will connect in Ubuntu only if I first connect it in XP and then boot into Ubuntu. It connects automatically.
The Samsung will not connect at all.

I tried to install USB Modeswitch on the Samsung and I think that I did everything right. But, when I run lsusb it shows up as 12d1:1001. Shouldn't it be showing up as 12d1:140b?

I did also try to use the sakis3g tool. But realized that it does not work for CDMA based devices. It seems like the sakis3g tool made a permanent change for my EC1261 device to switch to 12d1:1001 instead of 12d1:1446. How can I change this?

The built in network manager recognizes the device when I go through the Mobile Broadband Connection wizard, but it won't actually connect. I put in the number to dial and the username and password correctly.

I really want to be able to use Ubuntu on the netbook instead of XP....so, who has an idea about how to fix this?

---

### Post by Sakis3G on 2010-08-17
Hi dannelb,

Unfortunately Sakis3G script does not yet support CDMA connections, and I really cannot help you with your connection problem.

Regarding your modem being permanently altered in some way, be pleased to know that:

[LIST]
[*]Sakis3G script does not change any files on your filesystem(s). If you count bytes one-by-one, before and after invoking Sakis3G script, you will discover no change. This allows Sakis3G script to operate even if filesystem(s) are mounted read-only, which had been one of my personal needs.
[*]All changes performed on your system/setup are volatile. Although not required, a reboot session is capable to completely clear all setup/customization performed by Sakis3G script.
[*]Sakis3G script does not include statements/methods for permanently altering device setup, even for devices for which this is actually possible. If your modem is indeed permanently altered in some way, it must had been something else you tried and not Sakis3G script.
[/LIST]
  
Before going disappointed with your modem being permanently harmed, please read this. ZeroCD USB modems (those which need to be mode switched before becoming usable) do not usually express a deterministic behavior, in the usual sense common other hardware does. This mainly happens due to manufacturers violating convention that each USB device should have its own unique product ID (as shown by lsusb command). Instead, they provide customized OEM revisions, which behave differently, still advertise same USB IDs.

As an example, there are both Huawei devices which appear with ID 12d1:1001 during their storage-mode, and others which appear with ID 12d1:1001 while being in modem-mode. Determining which device is actually plugged on a computer can be a really hard procedure (and this is the reason behind Usb-ModeSwitch employing such "nusty" tricks: to determine which one device is actually connected, of those sharing same USB IDs).

These all mean you shouldn't be relying on information you encounter on the internet, based solely on USB IDs, for determining which IDs your device should have on its usable state, especially if you own a recent one device. Most reliable way to determine them, is by examining modem's ID on Windows (they refer to these codes as VID and PID I think).

Like this had not been enough trouble already, some devices may appear with more than just two pairs of USB IDs, according to switching command they are sent. This is usually implemented, on some modem&firmware versions, for allowing manufacturer to sell the exact same device&firmware combination to more than one operators, while providing different software routines to each one of them.

As an example, same modem may be sold to operator A and to operator B, each one being provided just a differently colored cover, to match their respective logo colors. Device recognizes two switching commands. Operator A is only given command which switches modem to 141a, while operator B is only given command which switches modem to 141b. Each operator then manufactures software which operates only with its own assigned IDs. Still, under the hood, both are the exact same modem, offering exact same functionality under both IDs.

On free world (which is not just Linux world), neither manufacturer nor operator provide details/instructions/driver/software (exceptions apply). Whole switching operation is performed by Usb-ModeSwitch, based on "sniffing" information provided by device owners, based on their Windows driver's attitude. This might mean that user who "sniffed" fore-mentioned device, might had operator-A's driver, which results into device being switched to 141a. Users who have operator-B's version, when using Usb-ModeSwitch, will have their device instructed to be switched to operator-A's version.

It is then possible to witness behavior you describe: device demonstrating different IDs across free and non-free operating systems. It is not yet proved (thankfully) that users experiencing such an attitude, also experience limited functionality. If this ever turns out to be the case, we will end-up being asked by Usb-ModeSwitch about sticker being printed on modem (Orange? T-mobile? Verizon? Vodafone? etc.)

Sakis3G script relies on Usb-ModeSwitch (either system provided or, if not present, on embedded version) for mode switching devices. Therefore, same restrictions apply for Sakis3G script as well.

Continuing the quest, a device might appear with a completely new set of USB IDs if a firmware update procedure is involved (i.e. when attempting to unlock a locked-to-operator modem).

Last but not least, there are devices which do not have their IDs changed at all, when being mode switched. Instead, they retain same ID, and they only change "Configuration" or "Class".

These all mean that the only one, who can tell you, what your modem's IDs "should be", after being mode switched, is someone who bought the exact same modem from the exact same operator as you did. However, now that you know the truth, you realize there is no "should-be-ID" thing.

You just have to choose whether to take the blue pill, or the red pill.

Going back to Linux kernel, a (usual-cheap-monkey) mode switched modem should be usable if all of the following apply:

[LIST=1]
[*]    Device provides at least one non-storage class interface (class!=05) which encloses exactly one endpoint of "Interrupt" transfer mode, and one or two more endpoints with "Bulk" transfer mode,
[*]Fore-mentioned interface is claimed by appropriate driver (option, sierra, cdc_acm are some them),
[*]Driver provides a device major and minor numbers referring to that interface,
[*]A character device file, yielding exported major and minor numbers, is created (usually in /dev directory) and actually behaves like being one,
[*]Fore-mentioned character device file provides AT commands (Hayes) functionality (usually one of the many /dev/ttyUSB* or /dev/ttyACM* devices appearing after modem is switched).
[/LIST]
  
If all of those are satisfied, still modem does not work as expected, then it is user-space software, other than Usb-ModeSwitch, which fail to make it work (i.e. Network Manager, gnome-ppp, wvdial, kppp, umtsmon, comgt, Sakis3G), and trust me, kernel is doing fine since 2.6.26.

For determining if all of those are satisfied, execute Sakis3G with "setup" argument. This will let it setup your modem up to the point that /dev/tty* devices are created, which is common procedure for both GSM and CDMA modems. You then need other software for establishing CDMA data connection through correct /dev/tty* device.

I hope I helped you more than I scared you,

Sakis

---

### Post by dannelb on 2010-08-17
Hey Sakis,

Thanks so much for your response. Was very informative and I am happy to hear that it didn't change anything.
I did use your tool in Setup mode. NetworkManager can recognize the modem when I go through the Mobile Broadband connection tool. But when I actually try to connect, it won't. It tries for a minute or so and then gives up.
I also tried wvdial from the command line. But that said that the ppp daemon failed. Gnome-ppp ends with the same failure.
Any more ideas?

Thanks.

---

### Post by alexfish on 2010-08-17
hi dannelb

until Sakis3g replies to your post 

have you tried setting gnomeppp  setup/ options / and tick stupid mode

regards 

alexfish

---

### Post by Sakis3G on 2010-08-17
> **dannelb said:**
> 
I also tried wvdial from the command line. But that said that the ppp daemon failed. Gnome-ppp ends with the same failure.
Any more ideas?


You first need to make sure that all your attempts target /dev/ttyUSB* node which derives from interface including interrupt-type endpoint. Maybe I could tell you which one it is from the output of:
```
lsusb -v -d 12d1:1001
```Other than that, since problem is consistent across software used, you could extract debug information from **pppd**. This can be established by uncommenting/appending "debug" option on your /etc/ppp/options file:
```
$ sudo bash
Password:
# echo debug >> /etc/ppp/options

```Then attempt to connect (using wvdial, gnome-ppp etc.). This will dump pppd negotiation on your syslog (including LCP negotiation). You then need someone experienced with CDMA connections to tell you what's wrong.

Sakis

---

### Post by dannelb on 2010-08-19
Ok, apparently it is working. Though not as well as I would like.

I got it to work via wvdial. Network manager doesn't seem to want to work with the EC1261 as of now (hopefully it will in a future update).

Here is what I did:
1. Use Sakis3g to setup modem, this switches it to 12d1:1001
2. Changed the wvdial.conf to work with my provider here in Ethiopia
3. Run sudo wvdial
4. Connected!

Thanks for all the help!

---

