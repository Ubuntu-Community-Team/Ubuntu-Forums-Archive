---
title: "can't connect using ZTE MF637 HSUPA modem"
date: 2009-08-07
forum: Networking &amp; Wireless
---

### Post by Risay on 2009-08-07
[FONT=Georgia][SIZE=3]it seems that **Ubuntu 9.04** does not recognize some types of USB modems, I have **ZTE MF637 HSUPA** modem and when i insert it to my laptop, Ubuntu fails to recognize it !!!

where is the problem and what is the solution ??

[/SIZE][/FONT]

---

### Post by sanya-vl on 2009-11-25
the same problem ((( how to fix it??? zte mf 637, ubuntu 9.10

---

### Post by c1rider on 2009-11-25
I had same problem with 9.10 and 627 modem.  The solution for me was simple.

Boot netbook as normal, plug in dongle, once dongle appears in "Volumes" eject it.

Dongle will connect again, this time correctly as modem ( it's first connect is as drive )

use set up wizard to enter your password, default settings in 9.10 are OK.

My Netbook is Acer Aspire One, Ubuntu 9.10 and "3" dongle in UK.

---

### Post by sanya-vl on 2009-11-25
Hmm, lucky... I "ejected" it and I have settings in Network Settings, but how to connect?

---

### Post by pdc on 2009-11-26
[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

go half-way down this page, to where it says 

"Create a mobile broadband connection":

it should cover what you need;

let us know if it does

---

### Post by game_cat on 2009-11-27
HI- just got a new netbook and install ubuntu...
 
This worked for me... I had to eject the storage device on my hsupa usb modem and then i could set up the connection using network manager. The T-Mobile default settings worked fine (i got the modem this week).
 
One thing that did give me trouble was having a Micro SD card inserted. Even after ejecting it it still did not recognise it. It only worked after i removed the SD card from the modem.
 
thanks for the help

---

### Post by guarana5 on 2009-12-11
> **game_cat said:**
> HI- just got a new netbook and install ubuntu...
 
This worked for me... I had to eject the storage device on my hsupa usb modem and then i could set up the connection using network manager. The T-Mobile default settings worked fine (i got the modem this week).
 
One thing that did give me trouble was having a Micro SD card inserted. Even after ejecting it it still did not recognise it. It only worked after i removed the SD card from the modem.
 
thanks for the help

Hej!

So you've got a ZTE MF637 working under Ubuntu? What Ubuntu version do you use?

Thanks!
guarana

---

### Post by empr on 2009-12-22
I can connect to my network, but I have no internet.  There is no incoming data.  Does anyone think they might be able to diagnose my problem?

---

### Post by Pulka on 2010-01-19
I'm loosing my mind here.

Already managed to recognize the modem, and it shows up in the network manager, but i always get a message saying "modem not responding". Something is missing. Can anyone help me?



these are the steps i did so far:


**1) Download and install usb_modeswitch**

**2) Edit /etc/usb_modeswitch.conf to apply to the MF628+**

Either comment the first modem configuration out, then find and uncomment the section for the MF628+, or (more easily) replace the content of the file with:

Code:

########################################################
# ZTE MF628+ (tested version from Telia / Sweden)
#
# Contributor: Joakim Wennergren
#
# Also applies to MF627 (Tested 3 UK) JF

DefaultVendor=  0x19d2
DefaultProduct= 0x2000

TargetVendor=   0x19d2
TargetProduct=  0x0031

MessageEndpoint=0x01
MessageContent="55534243123456782000000080000c85010101180101010101000000000000"



**3) Create a udev rule to automatically run usb_modeswitch when the modem is plugged in**

Create a new file called 999-zte-rules:
gksudo gedit /etc/udev/rules.d/999-zte.rules

Its content should be as follows:
Code:

SUBSYSTEM=="usb", SYSFS{idProduct}=="2000", SYSFS{idVendor}=="19d2", RUN+="/usr/sbin/usb_modeswitch"



**4) Add device information to HAL so network-manager recognises the device as a modem**


gksudo gedit /usr/share/hal/fdi/information/20thirdparty/20-zte-mf627.fdi


<!-- -*- SGML -*- -->
<deviceinfo version="0.2">
  <device>
      <!-- ZTE MF627 HSDPA USB dongle -->
      <match key="@info.parent:usb.vendor_id" int="0x19d2">
        <match key="@info.parent:usb.product_id" int="0x0031">
          <match key="@info.parent:usb.interface.number" int="3">
            <append key="modem.command_sets" type="strlist">GSM-07.07</append>
            <append key="modem.command_sets" type="strlist">GSM-07.05</append>
            <append key="info.capabilities" type="strlist">modem</append>
          </match>
        </match>
      </match>
  </device>
</deviceinfo>

---

### Post by pdc on 2010-01-19
try the suggestions of George Vita in post #10 here

[http://ubuntuforums.org/showthread.php?t=1382277](http://ubuntuforums.org/showthread.php?t=1382277)

maybe post back the dmesg and lsusb results ??

---

### Post by gillblu on 2010-03-12
Guys,
I have solution that works for me.
Using ZTE MF 637
Ubuntu 9.10

1. Add a Mobile Broadband network in Network Manager, configure the number, APN and PIN. In some cases username and password is required.
2. Give it a name you'd recognize.
3. IPv4 settings method should be "Automatic (PPP) addresses only.
4. Add DNS servers (Google's are 8.8.8.8 and 8.8.4.4) and apply

5. $ sudo aptitude install udev-extras (credit: volaer)
6. $ sudo update-usbids.sh (credit: Sergiu Bivol)
7. $ lsusb should show: 19d2:0031 ONDA Communication S.p.A. ZTE MF636
8. Plug in the mdoem to a usb port and wait for the modem icon on the desktop
9. Right click and eject the drive and unplug it
10. Replug the drive. The 4GB drive should appear.
11. Wait 1 minute. Broadband network should appear
12. Try opening [https://72.14.221.99](https://72.14.221.99) (google.com)
13. If the DNS in the broadband network config is OK, you will be able to use normal urls.

Enjoy.

---

