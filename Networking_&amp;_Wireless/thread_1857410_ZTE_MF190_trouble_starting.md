---
title: "ZTE MF190 trouble starting"
date: 2011-10-10
forum: Networking &amp; Wireless
---

### Post by almursi on 2011-10-10
Hi, as I explained in the Spanish forum ([http://www.ubuntu-es.org/node/159880](http://www.ubuntu-es.org/node/159880)), I had some problems to initiate the connection in this USB modem,   
Support is full from Ubuntu 11.04, but I found many problems in connection start, so that had to unplug the modem 1 to 3 times until a successful connection.  The correct way to connect is to select these options (apologies for the re-translation into English): 

  Edit connections, Add new adsl modem with: 
1. Check Automatic connection.
2  Check For All users. 
3. Put PIN code. 
4. Select only CHAP, by uncheck others (I explain above)
(other options by default)

  In this way I managed to connect automatically as soon as eject the CD. But I still see a window asking for the PIN, which **is necessary to cancel**. It is probably a bug.  As for the password exchange protocols, my provider (movistar) only recognizes CHAP, at the time that it tries to anyone else, I get the typical response of PPP error &quot;line is not 8 bit clean&quot;, is impossible to connect again and I need to unplug.

  I believe that here unites two different errors. One, on the method to send the unlock PIN, which may be a bug itself: Two different processes seem to fight to activate the modem (possibly between ttyUSB2 -bad- and ttyUSB4 -good-). And the other on the PPP and the opacity of the phone provider, which urges us to use their proprietary software (although not working:)).  Best regards  
 Edit: vbulletin destroys all paragraphs, is not mine... Fixed by hand with html code  
 Edit2: This may need to manually update usb_modeswitch (only 11.04 users): 
[http://ubuntuforums.org/showpost.php?p=10793568&postcount=30](http://ubuntuforums.org/showpost.php?p=10793568&postcount=30) 
Another link, several ZTE MF190 
[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=420&sid=b4217ebdd15c270bbc9f2a461d4236f4](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=420&sid=b4217ebdd15c270bbc9f2a461d4236f4) 
**be careful**: seems that ZTE MF190 can not connect in ubuntu 11.10 again...

---

### Post by almursi on 2011-10-24
Hi, after getting tired of the problems, I ended up using wvdial and I have no problem connecting on any version. Best regards.

---

### Post by gradinaruvasile on 2011-10-24
Have you guys tried sakis3g?
It is a wonderful small all-in-one script that does wonders in connecting USB broadband modems. It doesnt depend on any other system component (it uses usb_modeswitch if its available). It worked with all modems i tried so far, even ones that werent recognized by the kernel as modem.

Here it is:

[http://www.sakis3g.org/#downloading](http://www.sakis3g.org/#downloading)

It has a graphical version if launched with no options, but i recommend it in console using --interactive --console options for best stability.

I made a small script that puts it in the system tray (it uses alltray):

```

#!/bin/bash
command="sakis3g --console --interactive"
FORCE_APN="internet" APN_USER="user" APN_PASS="pass" alltray --show --sticky "xfce4-terminal -T Broadband_connect -I $HOME/.local/share/icons/sakis3g.png  --disable-server -e '$command'"

```

The above is for xfce4 environment, but can be adapted by changing xfce4-terminal to gnome-terminal or whatever terminal you have AND of courser, that terminals command line options and the icon (if any).

Also, i have preset the FORCE_APN variable to my provider, also APN_USER and APN_PASS. You might have to change those or leave them out and you will be asked on every connect (APN is autodetected).

And MAKE SURE you put something(1 character is enough) in the user and pass fields even if you dont need user and password because the script is made that way.

NOTE: if you use network-manager, you will have to kill the modem-manager process to release the modem.

---

### Post by almursi on 2011-10-24
Hi, yes, but with wvdial you can see the activity of pppd by firestarter (i.e.). Whatever it is, the network monitor (and modem-manager) must be disabled and sakis3g is quite opaque (have you tried if it works with iptables? I would say no).  Edited: Anyway seeing your command line may be easy to do in xfce visible (although I doubt with iptables) :).  Best regards.

---

### Post by gradinaruvasile on 2011-10-24
> **almursi said:**
> Hi, yes, but with wvdial you can see the activity of pppd by firestarter (i.e.). Whatever it is, the network monitor (and modem-manager) must be disabled and sakis3g is quite opaque (have you tried if it works with iptables? I would say no).  Edited: Anyway seeing your command line may be easy to do in xfce visible (although I doubt with iptables) :).  Best regards.

What does it have to do with iptables? Iptables is used for packet filtering/firewall.
If you have rules for the ppp0 interface (that is the interface it uses ususally), it should work as any network interface.
Also Sakis3g is much more wvdial - for wvdial you have to rely on the kernel/other tools to configure your USB dongle as a modem AND you have to manually enter all your config options (APN etc).
Sakis3g does the modem configuration (which sometimes is not done by the kernel correctly if it doesnt recognize the USB device), asks for user/pass and autodetermines the APN and then uses external commands to establish the connection. It uses pppd or even wvdial if its available for that.

---

### Post by almursi on 2011-10-24
> **gradinaruvasile said:**
> If you have rules for the ppp0 interface (that is the interface it uses ususally), it should work as any network interface.

Hi, my experience over ubuntu (10.04/11.04) tells me that firewall is not rise up, so I only use the sakis3g as a last resort. It seems that sakis3g establishes its own connection pipe (this could be a bug) iptables outside. And in a direct internet connection seems to me basic there is a minimum firewall.

Edited: For this USB modem I just need wvdial.conf:


>  [Dialer Defaults] 
 Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGMM
Init4 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init5 = AT+CGDCONT=1,&quot;IP&quot;,&quot;movistar.es&quot;
Password = movistar
Phone = *99#
; apn = movistar.es
REMOTE_IP = 10.64.64.64
Modem Type = USB Modem
; Stupid Mode = 1
Baud = 115200
New PPPD = 1
LOCAL_IP = 0.0.0.0
Dial Command = ATD
Modem = /dev/ttyUSB4
ISDN = 0
NETMASK = 255.255.255.0
Username = movistar

[Dialer pin]
Init1 = AT+CPIN=xxxx
Modem = /dev/ttyUSB4
  Dialing is very fast.
.
Edited2: I forgot to mention that sakis3g also has problems (similar to modem-manager) to recognize the ttyUSB4 that use this modem..
.
Best regards.

---

### Post by gradinaruvasile on 2011-10-24
Sakis3g does not use anything of its own to create connections. It establishes connections via pppd or vwdial.
BTW if done correctly, the firewall does "rise up".

---

### Post by almursi on 2011-10-24
> **gradinaruvasile said:**
> Sakis3g does not use anything of its own to create connections. It establishes connections via pppd or vwdial.
BTW if done correctly, the firewall does &quot;rise up&quot;.

Hi, well, I don't know :o, it's my experience... (maybe a bug) Best regards.

---

### Post by agarroyo on 2012-03-12
My computer runs Ubuntu 11.10. 
I have a ZTE MF190 modem provided by my service provider Movistar/Telefonica SPAIN
I hit the problem mentioned in this thread. 

I found a "dirty" way to make things work: 

I remove /dev/ttyUSB2 and create it again as a symbolic link to 
/dev/ttyUSB4. 

Then network-manager connects to the 3G service provider with no problem. 

I post it  since it might help others to use the modem, before this "bug" is fixed.

---

### Post by drvista on 2012-03-15
hello
I have managed to find a work around for this 
the idea is to use agarroyo patch to be excuted as udev rule when the usb modem is pluged in 
first create the file
```
/etc/udev/rules.d/10-zte.rules
```
with the following contents 
```
ACTION!="add", GOTO="ZTE_End"
# Is this the ZeroCD device?
SUBSYSTEM=="usb", SYSFS{idProduct}=="2000",
SYSFS{idVendor}=="19d2", GOTO="ZTE_ZeroCD"
# Is this the actual modem?
SUBSYSTEM=="usb", SYSFS{idProduct}=="0001",
SYSFS{idVendor}=="19d2", GOTO="ZTE_Modem"
#LABEL="ZTE_ZeroCD"
# This is the ZeroCD part of the card, remove
# the usb_storage kernel module so
# it does not get treated like a storage device
#RUN+="/sbin/rmmod usb_storage "
LABEL="ZTE_Modem"
# This is the Modem part of the card, let's
# load usbserial with the correct vendor
# and product ID's so we get our usb serial devices
RUN+="/sbin/modprobe usbserial vendor=0x19d2 product=0x0001",
# Make users belonging to the dialout group
# able to use the usb serial devices.
MODE="660", GROUP="dialout"
RUN+="/usr/bin/fixUSB"
LABEL="ZTE_End"
```
**[COLOR="Red"]note to modify any value as you wish according to your modem model[/COLOR]**
then create 
```
/usr/bin/fixUSB
```
with the following content
```
#!/bin/bash
sudo rm /dev/ttyUSB2
sudo ln -s /dev/ttyUSB3 /dev/ttyUSB2
```
and make it excutable
```
sudo chmod +x /usr/bin/fixUSB
```
now restart udev
```
sudo restart udev
```
unplug your USB modem and replug it again
enjoy
thank you
and questions just email me dr3mro[at]gmail[dot]com

---

### Post by drvista on 2012-03-15
i have create a udev patch that fixes the issue in a dirty way until a fix is commited
this is the deb file

---

### Post by almursi on 2012-03-16
Hi, thanks drvista. Note that your pacth only work with your MF190, other MF190 variant users need to fix SYSFS{idProduct}=="XXXX" and ttyUSB port, but more easy way is:
```
sudo rm /dev/ttyUSB2
sudo ln -s /dev/ttyUSB4 /dev/ttyUSB2
```
case of ```
Model: MF190
Revision: MF190V1.0.0B07
Manufacturer's Revision: 
MF190V1.0.0B
```
Regards

---

### Post by drvista on 2012-03-16
i already wrote that you should modify the udev rules file according to your modem 
udev method is better as it will do remove and link the ttyUSB2 on modem insertion so make it behave like any other usb modem and the user don't have to fire a terminal every time he connect to the internet
wish you good luck

---

### Post by stefano_to on 2012-08-17
last solution doesn't work for me. :(
I have a zte mf190 internet key on Ubuntu 12.04 : appearently it works correctly for everybody out of the box, except for me.

It's recognized by the system , lsusb gives 
```
Bus 002 Device 008: ID 19d2:1245 ZTE WCDMA Technologies MSM
```

it correctly asks for my pin, internet plan, company and so on. It appears among the connections but as I try to connect it tells me that it's unable.

It works on windows, but I don't have it on my laptop (well, I have it in the proper place, a virtualbox... :p)

Thanks for any help and tell me if you need other info!

---

