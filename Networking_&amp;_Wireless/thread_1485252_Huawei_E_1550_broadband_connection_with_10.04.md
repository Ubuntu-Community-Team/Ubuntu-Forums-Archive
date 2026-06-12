---
title: "Huawei E 1550 broadband connection with 10.04"
date: 2010-05-16
forum: Networking &amp; Wireless
---

### Post by airper on 2010-05-16
Hi,

I use a Huawei E 1550 mobile connection, which worked fine in Ubuntu 9.10.

I've got it working okay in 10.04, having installed modeswitch. However, it will not automatically reconnect if it drops out. 

I can force a reconnection, only if I remove the dongle and then plug it in again. Although it shows in network manager, clicking on the list entry for the dongle, just produces a disconnected dialogue message. The only way to get it to reconnect is to remove the dongle and plug it in again.

I know there have been a few posts about getting mobile dongles to work in 10.04, but I can't see any solutions to this little issue yet.

Is this a known bug, or is there a workaround for this?

Airper

---

### Post by mgco on 2010-05-25
@airper sorry if i'm not posting a solution, but rather a +1 to this issue as I'm experiencing the same problem. I'm about to decide to roll back to Karmic just to have the E1550 get detected and reclaim some internet connection through it!

---

### Post by sesso on 2010-06-04
Hey guys ....

just to to this page and 110% your Modem gonna work , ill spent hours on finding someway to get my modem online and just use it and works no mumbo jumbo

[www.sakis3g.org](www.sakis3g.org) and follow the guide even with a video to shoe how

Sesso:popcorn:

---

### Post by spaceshipguy on 2010-07-25
I have the same problem. E1550 connects. Waits between 2 and 20 minutes then disconnects. Then refuses to reconnect. I  must pull it out and push it back in for another 2 to 20 minutes of internet.
I tried sakis3G, but it was anything but intuitive.
I'm on the 3 network in Austria, when it eventually connected me it connected me to their competitor. I pulled out the dongle before I could rack up huge roaming charges. 
Most frightening and unsatisfactory.

I'm still searching for a E1550 answer.:(

---

### Post by pdc on 2010-07-26
> I'm still searching for a E1550 answer

sounds more like network issues, than modem issues

is your network manager setup the same as in the screenshot?

.. that is attached ...

sorry to hear you found sakis 3g "anything but intuitive"

I used it for UK vodafone and NL vodafone recently and it worked well

---

### Post by ukblacknight on 2010-08-23
I too am having this problem with the same device.  On the 3 network.  Oddly enough, the connection lasts a lot longer on one user account on the same laptop than my own.

I'm tempted to install network-manager 0.8.1 which can show signal strengths on GSM networks to see if it's a network related problem, although, the dongle has worked fine for a couple of months prior to these issues.

---

### Post by ashoku22 on 2010-08-27
Configuration of 3G Datacard (Huwaei) in Ubuntu Linux for BSNL
Details to help configure BSNL 3G - August 2010
Frequency - 2100 Mhz
A variant of 3G called as 3.5G or HSDPA
Speed 3.6Mpbs, 7.2Mbps
apn name or acesspoint name - bsnlnet (Other values like username just nothing)
BS L 3G data card USB models:
Micromax MMX 300G
Micromax E156G
Huawei E156 (3.6Mbps)
Huawei E176 (7.2Mbps)
Huawei 210
SimU6T
SimU9T
BS L 3G (HSDPA) Data Card using wvdial in Ubuntu 9.10
Select Applications, Accessories, Terminal
sudo <space> wvdialconf <enter>
-------------
Found a modem on /dev/ttyUSB0
Modem configuration written to /etc/wvdial.conf.
-------------
sudo <space> gedit <space> /etc/wvdial.conf <enter>
[Dialer Defaults]
Modem Type = Analog Modem
Phone = *99#
ISDN = 0
Baud = 460800
Username = " "
Password = " "
Modem = /dev/ttyUSB0
Init1 = ATZ
Init2 = at+cgdcont=1,"ip","bsnlnet"
Stupid Mode = 1
Run the following command to connect to Internet
sudo <space> wvdial <enter>
Huawei E1550 3g modem not switching to modem mode automatically in Ubuntu 10.04 &#8211; Solution
sudo <space> gedit <space> /etc/udev/rules.d/15-huawei-e1550.rules
Paste the below lines into the file. These lines tell udev that when this device is plugged in it should be switched to modem
mode.
SUBSYSTEM=="usb",
SYSFS{idProduct}=="1446",
SYSFS{idVendor}=="12d1",
RUN+="/lib/udev/modem-modeswitch --vendor 0x12d1 --product 0x1446 --type option-zerocd"
Select File, save. Close all. Restart computer and configure using Network Manager.

---

