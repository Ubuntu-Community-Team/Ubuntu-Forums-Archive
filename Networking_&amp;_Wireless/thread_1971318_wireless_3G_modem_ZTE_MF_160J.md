---
title: "wireless 3G modem ZTE MF 160J"
date: 2012-05-02
forum: Networking &amp; Wireless
---

### Post by moma on 2012-05-02
Hello,
I have ZTE MF160J 3G-modem from the Portuguese TMN. 

It does not work in Ubuntu 12.04. The led-light turns red, then after 5 secs to green, but no connection. I have created an entry under "Mobile BroadBand" in the network manager (see the picture).

Do you have instructions for how to make this 3G-modem to work in Linux?

$ lsusb
Bus 001 Device 002: ID 19d2:1542 ZTE WCDMA Technologies MSM 

$ usb-devices
T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=1542 Rev=00.01
S:  Manufacturer=ZTE
S:  Product=MF190J
S:  SerialNumber=9BB27BAF013DFB85103C397DCB576 <snip>
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

The config looks like this
[http://bildr.no/view/1170463](http://bildr.no/view/1170463)
and
[http://bildr.no/view/1171194](http://bildr.no/view/1171194)

The actual USB-pen from the Portuguese TMN.
3G-pen 14.4Mbits/sec ZTE MF190J, max 15GB download/month.
[http://tinyurl.com/7v6yvh9](http://tinyurl.com/7v6yvh9)


Output from modem test (after eject/unmount)
$ modemtest --hide-possible /dev/ttyACM0   # or /dev/ttyACM1
```
Device::SerialPort v1.40.0 loaded.
Port '/dev/ttyACM0' open
can ioctl: Yes
Got handshake: none
Got baud: 9600
Got databits: 8
Got parity: none
Got stopbits: 1
Modem status = 0x0126 (DTR=ON  CTS=ON  RTS=ON  DSR=ON  RNG=off CD=off)

Activated DTR(okay) and RTS(okay) ... pausing for 3 seconds
Modem status = 0x0126 (DTR=ON  CTS=ON  RTS=ON  DSR=ON  RNG=off CD=off)

Deactivated DTR(okay) and RTS(okay) ... pausing for 3 seconds
Modem status = 0x0122 (DTR=ON  CTS=ON  RTS=off DSR=ON  RNG=off CD=off)

Activated DTR(okay) ... pausing for 3 seconds
Modem status = 0x0122 (DTR=ON  CTS=ON  RTS=off DSR=ON  RNG=off CD=off)

Activated RTS(okay) ... pausing for 3 seconds
Modem status = 0x0126 (DTR=ON  CTS=ON  RTS=ON  DSR=ON  RNG=off CD=off)

read: 0
saw -><-
wrote: 5
written ->ATE1{0x0D}<-
read: 25
saw ->{0x0D}{0x0A}NO CARRIER{0x0D}{0x0A}ATE1{0x0D}{0x0D}{0x0A}OK{0x0D}{0x0A}<-
read: 0
saw -><-
Modem status = 0x0126 (DTR=ON  CTS=ON  RTS=ON  DSR=ON  RNG=off CD=off)
Port closed
```

// Moma

---

### Post by collisionystm on 2012-05-02
Generally a 3g air card needs to be activated with the software from the manufacture before it can be used. You may need to use Windows and the software for that card to activate it and then it will work on Ubuntu.

---

### Post by alexfish on 2012-05-02
> **moma said:**
> Hello,
I have ZTE MF160J 3G-modem from the Portuguese TMN. 

It does not work in Ubuntu 12.04. The led-light turns red, then after 5 secs to green, but no connection. I have created an entry under "Mobile BroadBand" in the network manager (see the picture).

Do you have instructions for how to make this 3G-modem to work in Linux?

$ lsusb
Bus 001 Device 002: ID 19d2:1542 ZTE WCDMA Technologies MSM 

$ usb-devices
T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=1542 Rev=00.01
S:  Manufacturer=ZTE
S:  Product=MF190J
S:  SerialNumber=9BB27BAF013DFB85103C397DCB576 <snip>
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

The config looks like this
[http://bildr.no/view/1170463](http://bildr.no/view/1170463)
and
[http://bildr.no/view/1171194](http://bildr.no/view/1171194)

The actual USB-pen from the Portuguese TMN.
[http://tinyurl.com/7v6yvh9](http://tinyurl.com/7v6yvh9)

// Moma

according to the info the device has not switched

try using the Disk Utility , and eject the device
if the Device appears on the desktop , right click with the mouse > select eject
the use the "usb-devices" command , see if any change

---

### Post by moma on 2012-05-04
Hello,
@alexfish: 
Yes, the device has switched and loaded the "cdc_acm" driver.  
Take a look at this thread.It has additional data.
[https://lists.ubuntu.com/archives/ubuntu-pt/2012-May/009503.html](https://lists.ubuntu.com/archives/ubuntu-pt/2012-May/009503.html)

@collisionystm: 
Yes, we have tested this 3G-pin on Windows an dit works well. So it should have been initialized.

---

### Post by alexfish on 2012-05-04
**ZTE EJECT.RULES:** wrighting a UDEV rule will save time
```
sudo gedit /etc/udev/rules.d/zte_eject.rules
```**add line :** Other readers Edit the Device Id's highlighted , accoring to the "lsusb" command from the terminal device
```
ATTRS{idVendor}=="[COLOR=Blue]19d2[/COLOR]", ATTRS{idProduct}=="[COLOR=Blue]1542[/COLOR]", RUN+="/usr/bin/eject %k", OPTIONS+="last_rule"
```save and exit ; re-plug the device

alexfish

---

### Post by moma on 2012-05-04
@alexfish:
Your command disables the automount and that is good.
But I still have no internet connection.
Have tested this on 2 laptops with fresh Ubuntu 12.04.

I need to consider other alternatives.

---

### Post by alexfish on 2012-05-04
need more info , can post the results of these commands from the terminal

```
usb-devices
```post only the lines pertaining to the device
```
ls -al /dev/serial/by-id
```

---

### Post by moma on 2012-05-04
```
$ usb-devices
T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=02(commc) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=1544 Rev=00.01
S:  Manufacturer=ZTE
S:  Product=MF190J
S:  SerialNumber=9BB27BAF013DFB85103C397DCB576195D5417DF5
C:  #Ifs= 7 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 0 Cls=00(>ifc ) Sub=08 Prot=00 Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#= 2 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I:  If#= 3 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#= 4 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I:  If#= 5 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#= 6 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
```
```
$ ls -al /dev/serial/by-id
lrwxrwxrwx 1 root root  13 May  4 19:49 usb-ZTE_MF190J_9BB27BAF013DFB85103C397DCB576195D5417DF5-if01 -> ../../ttyACM0
lrwxrwxrwx 1 root root  13 May  4 19:49 usb-ZTE_MF190J_9BB27BAF013DFB85103C397DCB576195D5417DF5-if03 -> ../../ttyACM1
lrwxrwxrwx 1 root root  13 May  4 19:49 usb-ZTE_MF190J_9BB27BAF013DFB85103C397DCB576195D5417DF5-if05 -> ../../ttyACM2
```
I noticed that the ProdID is 1542 before eject/umount and 1544 after.
Many thanks for your help.

---

### Post by alexfish on 2012-05-04
```
I:  If#= 0 Alt= 0 #EPs= 0 Cls=00(>ifc ) Sub=08 Prot=00 Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm /dev/ttyACM0
I:  If#= 2 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I:  If#= 3 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm /dev/ttyACM1
I:  If#= 4 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I:  If#= 5 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm /dev/ttyACM2
I:  If#= 6 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm

```normally ZTE CONNECT ON last port / = /dev/ttyACM2 but here going to see what response getting for each port

may have to open up four terminals and enter the following commands
terminal 1
```
sudo killall modem-manager
```wait for about 1 minute for Network Manager to do its job
see if the device is recognised
```
nm-tool
```you may see the device , if so will network manager connect , if not Continue
if any problems in terminal enter as root for each terminal
```
sudo su
``````
cat /dev/ttyACM0
```terminal two
```
cat /dev/ttyACM1
```terminal3
```
cat /dev/ttyACM2
```open up forth terminal and enter the following commands
```
echo -e "ATZ\r" > /dev/ttyACM2
``````
echo -e "ATDT*99#\r" > /dev/ttyACM2
```if get CONNECT * message halt
```
echo -e "ATZ\r" > /dev/ttyACM1
``````
echo -e "ATDT*99#\r" > /dev/ttyACM1
```if get CONNECT * message halt
```
echo -e "ATZ\r" > /dev/ttyACM0
``````
echo -e "ATDT*99#\r" > /dev/ttyACM0
```post any results

---

### Post by moma on 2012-05-05
```
$ nm-tool
NetworkManager Tool
State: disconnected

- Device: ttyACM1 --------------------------------------------------------------
  Type:              Mobile Broadband (GSM)
  Driver:            cdc_acm
  State:             disconnected
  Default:           no

  Capabilities:
- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        06:9A:7B:17:07:25

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        81:A1:B3:E7:3F:39

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    DLink-B66F96:    Infra, 00:24:01:B6:6F:96, Freq 2437 MHz, Rate 54 Mb/s, Strength 49 WPA
    Kennedy:         Infra, 00:0C:F6:23:93:3D, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA
    TELEPAC-39143F:  Infra, 58:98:35:39:14:3F, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    marinawifi:      Infra, 00:27:22:10:AC:FB, Freq 2422 MHz, Rate 54 Mb/s, Strength 22
    marinawifi:      Infra, 00:27:22:10:AC:E7, Freq 2462 MHz, Rate 54 Mb/s, Strength 17
    marinawifi:      Infra, 00:27:22:10:AE:EF, Freq 2437 MHz, Rate 54 Mb/s, Strength 37
---------------------
```
```
echo -e "ATZ\r" > /dev/ttyACM2
echo -e "ATDT*99#\r" > /dev/ttyACM2

	cat /dev/ttyACM2:
	ERROR
	ERROR
----------

echo -e "ATZ\r" > /dev/ttyACM1
echo -e "ATDT*99#\r" > /dev/ttyACM1

	cat /dev/ttyACM1:
	ATZ
	OK
	ATDT*99#
	CONNECT 14400000
------------------------------------------

	cat /dev/ttyACM0:

	+CSQ: 14,0
	OK
	%NWSTATE: 4,26806,3G,-,0
	OK
	+CSQ: 14,0
	OK
	%NWSTATE: 4,26806,3G,-,0
	OK
	+CSQ: 15,0
	OK
	%NWSTATE: 4,26806,3G,-,0
	OK
	+CSQ: 14,0
	OK
	%NWSTATE: 4,26806,3G,-,0
	OK
	+CSQ: 15,0
	OK
	%NWSTATE: 4,26806,3G,-,0
	OK
	+CSQ: 15,0
	OK
	%NWSTATE: 4,26806,3G,-,0
	OK
	+CREG: 2,1,"0387","0022937E",6
	OK
	+CGREG: 2,1,"0387","0022937E",6,"01"
	OK
	+CSQ: 14,0
	OK
	%NWSTATE: 4,26806,3G,-,0
	OK
```

It seems to connect, but then after a second it simply cuts off.
I will do the same thing on the other Ubuntu-laptop. I´ll let you know.

Maybe I should go back to the TMN-shop and do a proper registration. I got this pin for testing/evaluation because I wanted to test it for Linux and I did not have a portuguese "Identificaçao Fiscal" to complete the registration. This pin has ca. 10EUR for evaluation. Anyway, this 3G-pin works in Windows. 

Thanks again!

---

### Post by alexfish on 2012-05-05
Hi the device has notified , CONNECT , that means it ready to negotiate
> echo -e "ATZ\r" > /dev/ttyACM1
echo -e "ATDT*99#\r" > /dev/ttyACM1

    cat /dev/ttyACM1:
    ATZ
    OK
    ATDT*99#
    CONNECT 14400000 [COLOR=Blue]<<<<< ready to Connect[/COLOR]next need to issue the pppd command or other possible network command , will post later on what to do next , need to read and digest [FONT=monospace]
[/FONT]```
$ nm-tool
NetworkManager Tool
State: disconnected

- Device: ttyACM1 --------------------------------------------------------------
  Type:              Mobile Broadband (GSM)
  Driver:            cdc_acm
  State:             disconnected
  Default:           no

  Capabilities:
- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        06:9A:7B:17:07:25

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        81:A1:B3:E7:3F:39

  Capabilities:
```Do you know all of these devices on the system

Also when get the Connect message does anything change in Network Manager

Does this device Have 3.5,g 4g or Lte capabilities , ask your supplier
ADDED:: reason : have look at the info , decoded part of messages gives "135.3.0.0,126.147.34.0" is server waiting for response to this message , but more on that later
**these are the bits I am looking at for decoding::**    
```
+CREG: 2,1,"0387","0022937E",6     
OK 
    +CGREG: 2,1,"0387","0022937E",6,"01"
```**ADDED::**
Also since this device appears to be new And as said , have for evaluation , can you have a look at these Posts in my How To , there are some scripts , that will test the device and also check if Modem-Manger can negotiate with the device

can post any findings ,, But Take You Time as regards using the scripts , the one script uses tcl #[**61**]("http://ubuntuforums.org/showpost.php?p=11458739&postcount=61") , so may have to download tcl , there is a Link  in "how to"  the easy way , or if 
have network connection can see if tcl is available in the Software Centre

modem-manager test :   #[**62**]("http://ubuntuforums.org/showpost.php?p=11585976&postcount=62")

if can get connected , will post a script to help

:: Checked up on this device looks like a 3.5/ 4g/lte

regards

alexfish

---

### Post by moma on 2012-05-12
Re-hello,
Ok, I have now bought this 3G-pin and made a contract for a year with 14.4Mbits/sec and upto 15GB download pr. month.  

>Do you know all of these devices on the system?
Yes I do.

Device: ttyACM1 
  Type:              Mobile Broadband (GSM)
  Driver:            cdc_acm
  State:             disconnected
  Default:           no
This is the 3G USB-pin from the Portuguese TMN. This is what we try fix.

Device: eth0 
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        06:9A:7B:17:07:25
This is the wired ethernet connection. This works well.

Device: wlan0
  Type:              802.11 WiFi
  Driver:            ath9k
This is the builtin wifi based on Atheros' chipset and its ath9k driver. I use this while the 3G-pin does not work. Normal wireless connection works very well.
-----------------

$ [COLOR="DarkGreen"]lsusb[/COLOR]
```
Bus 003 Device 003: ID 19d2:1544 ZTE WCDMA Technologies MSM 
Notice: The ProductID is 1542 before eject/umount and 1544 after.
```

$ [COLOR="DarkGreen"]ls -l /dev/serial/by-id/* [/COLOR]
```
lrwxrwxrwx 1 root root 13 May 12 12:57 /dev/serial/by-id/usb-ZTE_MF190J_9BB27BAF013DFB85103C397DCB576195D5417DF5-if01 -> ../../ttyACM0
lrwxrwxrwx 1 root root 13 May 12 12:57 /dev/serial/by-id/usb-ZTE_MF190J_9BB27BAF013DFB85103C397DCB576195D5417DF5-if03 -> ../../ttyACM1
lrwxrwxrwx 1 root root 13 May 12 12:57 /dev/serial/by-id/usb-ZTE_MF190J_9BB27BAF013DFB85103C397DCB576195D5417DF5-if05 -> ../../ttyACM2
```

[COLOR="Red"]SCRIPT #61:[/COLOR]

$ [COLOR="DarkGreen"]./61-script.sh eject sr[/COLOR]
```
ejectable or remove device /dev/sr1
19d2:1542
Device: 19d2:1542
ATTRS{manufacturer}=="ZTE"

19d2:1542
```

$ [COLOR="DarkGreen"]./61-script.sh eject sr 1[/COLOR]
```
ejectable or remove device /dev/sr1
19d2:1542
Device: 19d2:1542
Trap2 19d2:1542
Device: 19d2:1542 :ERR :Driver missing

Driver=usb-storage
Driver=ehci_hcd/2p
Driver=hub/6p
Driver=ehci_hcd/2p
Driver=hub/6p
Driver=usbhid
Driver=usbhid
Driver=usbhid
Driver=uvcvideo
Driver=uvcvideo
Driver= None
Driver= None
eject rule :
ATTRS{idVendor}=="19d2",ATTRS{idProduct}=="1542",RUN+="/usr/bin/eject %k", OPTIONS+="last_rule"

usb_modeswitch.d rule :
ATTRS{idVendor}=="19d2",ATTRS{idProduct}=="1542",RUN+="usb_modeswitch '%b/%k'"

ATTRS{manufacturer}=="ZTE"

19d2:1542
```

$ [COLOR="DarkGreen"]./61-script.sh eject sr 2[/COLOR]
```
ejectable or remove device /dev/sr1
device /dev/sr1 ejected
19d2:1542
Device: 19d2:1542
ATTRS{manufacturer}=="ZTE"

19d2:1542
Wait
Device: 19d2:1542 :ERR :Driver missing

Driver=usb-storage
Driver=ehci_hcd/2p
Driver=hub/6p
Driver=ehci_hcd/2p
Driver=hub/6p
Driver=usbhid
Driver=usbhid
Driver=usbhid
Driver=uvcvideo
Driver=uvcvideo
Driver= None
Driver= None
```

Notice: 
I added these udev-rules to zte_modem.rules. This is based on the above output from 61-script.sh. 
$ [COLOR="DarkGreen"]sudo gedit /lib/udev/rules.d/zte_modem.rules[/COLOR]

```
# TMN ZTE MF190J
ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="1542", RUN+="/sbin/modprobe  option"

# From script 61-script.sh
ATTRS{idVendor}=="19d2",ATTRS{idProduct}=="1542",RUN+="/usr/bin/eject %k", OPTIONS+="last_rule"
ATTRS{idVendor}=="19d2",ATTRS{idProduct}=="1542",RUN+="usb_modeswitch '%b/%k'"
ATTRS{manufacturer}=="ZTE"

ACTION=="add", SUBSYSTEM=="net", ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="1544", RUN="/sbin/ifconfig %k -arp"
```

Then I re-connected the 3G-pen.
Now it automatically ejects/unmounts the pen and it appears in the network-manager list.
Ref: [http://ubuntuforums.org/showpost.php?p=9201405&postcount=2](http://ubuntuforums.org/showpost.php?p=9201405&postcount=2)
-------

Lsusb shows now ProductID 1544.
$ [COLOR="DarkGreen"]lsusb[/COLOR]
```
Bus 003 Device 005: ID 19d2:1544 ZTE WCDMA Technologies MSM 
```
$ [COLOR="DarkGreen"]usb-devices[/COLOR]
```
T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=02(commc) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=1544 Rev=00.01
S:  Manufacturer=ZTE
S:  Product=MF190J
S:  SerialNumber=9BB27BAF013DFB85103C397DCB576195D5417DF5
C:  #Ifs= 7 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 0 Cls=00(>ifc ) Sub=08 Prot=00 Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#= 2 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I:  If#= 3 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#= 4 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
I:  If#= 5 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#= 6 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
```

$ [COLOR="DarkGreen"]sudo ./61-script.sh tty[/COLOR]
```
/dev/serial/by-id:

total 0
lrwxrwxrwx 1 root root 13 May 12 13:45 usb-ZTE_MF190J_9BB27BAF013DFB85103C397DCB576195D5417DF5-if01 -> ../../ttyACM0
lrwxrwxrwx 1 root root 13 May 12 13:45 usb-ZTE_MF190J_9BB27BAF013DFB85103C397DCB576195D5417DF5-if03 -> ../../ttyACM1
lrwxrwxrwx 1 root root 13 May 12 13:45 usb-ZTE_MF190J_9BB27BAF013DFB85103C397DCB576195D5417DF5-if05 -> ../../ttyACM2

--------- Udevadm device info-------
--usb-ZTE_MF190J_9BB27BAF013DFB85103C397DCB576195D5417DF5-if01: 
/dev/ttyACM0 : Status : CTS 1 DSR 1 RING 0 DCD 0
AT
OK

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1c.1/0000:08:00.0/usb3/3-1/3-1:1.1/tty/ttyACM0':
    KERNEL=="ttyACM0"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:1c.1/0000:08:00.0/usb3/3-1/3-1:1.1':
    KERNELS=="3-1:1.1"
    SUBSYSTEMS=="usb"
    DRIVERS=="cdc_acm"
    ATTRS{bInterfaceNumber}=="01"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="01"
    ATTRS{bInterfaceClass}=="02"
    ATTRS{bInterfaceSubClass}=="02"
    ATTRS{bInterfaceProtocol}=="01"
    ATTRS{supports_autosuspend}=="1"
    ATTRS{bmCapabilities}=="7"

  looking at parent device '/devices/pci0000:00/0000:00:1c.1/0000:08:00.0/usb3/3-1':
    KERNELS=="3-1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 7"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bMaxPower}=="500mA"
    ATTRS{urbnum}=="599"
    ATTRS{idVendor}=="19d2"
    ATTRS{idProduct}=="1544"
    ATTRS{bcdDevice}=="0001"
    ATTRS{bDeviceClass}=="02"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="3"
    ATTRS{devnum}=="5"
    ATTRS{devpath}=="1"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="ZTE"
    ATTRS{product}=="MF190J"
    ATTRS{serial}=="9BB27BAF013DFB85103C397DCB576195D5417DF5"

  looking at parent device '/devices/pci0000:00/0000:00:1c.1/0000:08:00.0/usb3':
    KERNELS=="usb3"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="69"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0002"
    ATTRS{bcdDevice}=="0302"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="3"
    ATTRS{devnum}=="1"
    ATTRS{devpath}=="0"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="2"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 3.2.0-24-generic-pae xhci_hcd"
    ATTRS{product}=="xHCI Host Controller"
    ATTRS{serial}=="0000:08:00.0"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1c.1/0000:08:00.0':
    KERNELS=="0000:08:00.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="xhci_hcd"
    ATTRS{vendor}=="0x1033"
    ATTRS{device}=="0x0194"
    ATTRS{subsystem_vendor}=="0x1179"
    ATTRS{subsystem_device}=="0xfc50"
    ATTRS{class}=="0x0c0330"
    ATTRS{irq}=="17"
    ATTRS{local_cpus}=="ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{dma_mask_bits}=="64"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{enable}=="1"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00/0000:00:1c.1':
    KERNELS=="0000:00:1c.1"
    SUBSYSTEMS=="pci"
    DRIVERS=="pcieport"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x1c12"
    ATTRS{subsystem_vendor}=="0x1179"
    ATTRS{subsystem_device}=="0xfc50"
    ATTRS{class}=="0x060400"
    ATTRS{irq}=="16"
    ATTRS{local_cpus}=="ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{enable}=="2"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}=="1"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""
--------- Udevadm device info-------

--usb-ZTE_MF190J_9BB27BAF013DFB85103C397DCB576195D5417DF5-if03: 
/dev/ttyACM1 : Status : CTS 1 DSR 1 RING 0 DCD 0
AT
OK

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1c.1/0000:08:00.0/usb3/3-1/3-1:1.3/tty/ttyACM1':
    KERNEL=="ttyACM1"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:1c.1/0000:08:00.0/usb3/3-1/3-1:1.3':
    KERNELS=="3-1:1.3"
    SUBSYSTEMS=="usb"
    DRIVERS=="cdc_acm"
    ATTRS{bInterfaceNumber}=="03"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="01"
    ATTRS{bInterfaceClass}=="02"
    ATTRS{bInterfaceSubClass}=="02"
    ATTRS{bInterfaceProtocol}=="01"
    ATTRS{supports_autosuspend}=="1"
    ATTRS{bmCapabilities}=="7"

  looking at parent device '/devices/pci0000:00/0000:00:1c.1/0000:08:00.0/usb3/3-1':
    KERNELS=="3-1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 7"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bMaxPower}=="500mA"
    ATTRS{urbnum}=="621"
    ATTRS{idVendor}=="19d2"
    ATTRS{idProduct}=="1544"
    ATTRS{bcdDevice}=="0001"
    ATTRS{bDeviceClass}=="02"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="3"
    ATTRS{devnum}=="5"
    ATTRS{devpath}=="1"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="ZTE"
    ATTRS{product}=="MF190J"
    ATTRS{serial}=="9BB27BAF013DFB85103C397DCB576195D5417DF5"

  looking at parent device '/devices/pci0000:00/0000:00:1c.1/0000:08:00.0/usb3':
    KERNELS=="usb3"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="69"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0002"
    ATTRS{bcdDevice}=="0302"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="3"
    ATTRS{devnum}=="1"
    ATTRS{devpath}=="0"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="2"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 3.2.0-24-generic-pae xhci_hcd"
    ATTRS{product}=="xHCI Host Controller"
    ATTRS{serial}=="0000:08:00.0"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1c.1/0000:08:00.0':
    KERNELS=="0000:08:00.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="xhci_hcd"
    ATTRS{vendor}=="0x1033"
    ATTRS{device}=="0x0194"
    ATTRS{subsystem_vendor}=="0x1179"
    ATTRS{subsystem_device}=="0xfc50"
    ATTRS{class}=="0x0c0330"
    ATTRS{irq}=="17"
    ATTRS{local_cpus}=="ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{dma_mask_bits}=="64"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{enable}=="1"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00/0000:00:1c.1':
    KERNELS=="0000:00:1c.1"
    SUBSYSTEMS=="pci"
    DRIVERS=="pcieport"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x1c12"
    ATTRS{subsystem_vendor}=="0x1179"
    ATTRS{subsystem_device}=="0xfc50"
    ATTRS{class}=="0x060400"
    ATTRS{irq}=="16"
    ATTRS{local_cpus}=="ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{enable}=="2"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}=="1"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

--------- Udevadm device info-------

--usb-ZTE_MF190J_9BB27BAF013DFB85103C397DCB576195D5417DF5-if05: 
/dev/ttyACM2 : Status : CTS 1 DSR 1 RING 0 DCD 0
AT
ERROR

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1c.1/0000:08:00.0/usb3/3-1/3-1:1.5/tty/ttyACM2':
    KERNEL=="ttyACM2"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:1c.1/0000:08:00.0/usb3/3-1/3-1:1.5':
    KERNELS=="3-1:1.5"
    SUBSYSTEMS=="usb"
    DRIVERS=="cdc_acm"
    ATTRS{bInterfaceNumber}=="05"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="01"
    ATTRS{bInterfaceClass}=="02"
    ATTRS{bInterfaceSubClass}=="02"
    ATTRS{bInterfaceProtocol}=="01"
    ATTRS{supports_autosuspend}=="1"
    ATTRS{bmCapabilities}=="7"

  looking at parent device '/devices/pci0000:00/0000:00:1c.1/0000:08:00.0/usb3/3-1':
    KERNELS=="3-1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 7"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bMaxPower}=="500mA"
    ATTRS{urbnum}=="643"
    ATTRS{idVendor}=="19d2"
    ATTRS{idProduct}=="1544"
    ATTRS{bcdDevice}=="0001"
    ATTRS{bDeviceClass}=="02"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="3"
    ATTRS{devnum}=="5"
    ATTRS{devpath}=="1"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="ZTE"
    ATTRS{product}=="MF190J"
    ATTRS{serial}=="9BB27BAF013DFB85103C397DCB576195D5417DF5"

  looking at parent device '/devices/pci0000:00/0000:00:1c.1/0000:08:00.0/usb3':
    KERNELS=="usb3"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="69"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0002"
    ATTRS{bcdDevice}=="0302"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="3"
    ATTRS{devnum}=="1"
    ATTRS{devpath}=="0"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="2"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 3.2.0-24-generic-pae xhci_hcd"
    ATTRS{product}=="xHCI Host Controller"
    ATTRS{serial}=="0000:08:00.0"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1c.1/0000:08:00.0':
    KERNELS=="0000:08:00.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="xhci_hcd"
    ATTRS{vendor}=="0x1033"
    ATTRS{device}=="0x0194"
    ATTRS{subsystem_vendor}=="0x1179"
    ATTRS{subsystem_device}=="0xfc50"
    ATTRS{class}=="0x0c0330"
    ATTRS{irq}=="17"
    ATTRS{local_cpus}=="ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{dma_mask_bits}=="64"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{enable}=="1"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00/0000:00:1c.1':
    KERNELS=="0000:00:1c.1"
    SUBSYSTEMS=="pci"
    DRIVERS=="pcieport"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x1c12"
    ATTRS{subsystem_vendor}=="0x1179"
    ATTRS{subsystem_device}=="0xfc50"
    ATTRS{class}=="0x060400"
    ATTRS{irq}=="16"
    ATTRS{local_cpus}=="ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{enable}=="2"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}=="1"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""
```
-----------------
The device (with ProdID 1542 or 1544) is NOT in the database.
$ [COLOR="DarkGreen"]./61-script.sh database  | grep  -i 19d2[/COLOR] 
```
19d2:0003
19d2:0013
19d2:0026
19d2:0040
19d2:0053
19d2:0083
19d2:0101
19d2:0103
19d2:0110
19d2:0115
19d2:0146
19d2:0149
19d2:0166
19d2:0169
19d2:1001
19d2:1007
19d2:1009
19d2:1013
19d2:1171
19d2:1175
19d2:1179
19d2:1201
19d2:1216
19d2:1224
19d2:1517
19d2:1520
19d2:2000
19d2:bccd
19d2:ffde
19d2:ffe6
19d2:fff5
19d2:fff6
```
=====================================

[COLOR="Red"]SCRIPT #62:[/COLOR]

$ [COLOR="DarkGreen"]./62-dbus-test-nm.sh[/COLOR] 
```

 ----*-----* MM-TEST DEVICE_ENABLE_DISABLE *-----*----

 DEVICE ENABLED : true
 ACTION :disconnect
 DEVICE ENABLED : false
 ACTION :enable
 DEVICE ENABLE : true

 ----*-----* MM-TEST DEVICE_INFO *-----*----

 DEVICE :1
 MASTER_DEVICE :/sys/devices/pci0000:00/0000:00:1c.1/0000:08:00.0/usb3/3-1
 ENUMERATED DEVICE TYPE :1
 DEVICE INFO :ZTE MF190J BD_TMNMF190JV1.0.0B03
 MODEM TYPE :GSM
 DIAL COMMAND :*99#
 NETWORK MCC :268
 NETWORK MNC :06
 PROVIDER   :P
 REGISTERED :TMN

 ----*-----* MM-TEST MM-INFO *-----*-----

 DRIVER :cdc_acm
 DEVICE :/dev/ttyACM1
 PIN STATUS :""
 ENUMERATED IP METHOD :Static configuration, the modem will provide IP information.
 DEVICE ENABLED : true
 ACTION :disconnect
 DEVICE ENABLE : false
```


I also copied these results from "61-script.sh" and "62-dbus-test-nm.sh" to [http://pastebin.com/YYEzAt6G](http://pastebin.com/YYEzAt6G)

The network-manager (network listing) shows this 3G modem. The 3G-pin first flashes red light, then turns to green.  A notification message says ""**You are now registered on the home network**"".

EDIT: It says only "You are now registered on the home network.". That´s all. 

Please see the picture.
[[img]http://bildr.no/thumb/1179117.jpeg[/img]](http://bildr.no/view/1179117)
The 3G-pen is shown as "TMN tmn internet 1" in the menu.

But still, no internet connection.
I am still offline with this 3G-pin, but I think there is a solution, and I need your help. Last time we saw that [the modem]("http://tinyurl.com/7v6yvh9") said "CONNECT 14400000". Many thanks so far!

>If can get connected , I will post a script to help.
Ok, can´t wait.

---

### Post by alexfish on 2012-05-12
Looks as if wrong data in the mcc code + provider and registered are reversed / not sure if fault in MM driver ? ADDED the Service Providers data base is showning 268 , checked this one at
[http://en.wikipedia.org/wiki/Mobile_Network_Code](http://en.wikipedia.org/wiki/Mobile_Network_Code) : So disregard
```
[COLOR=Blue]NETWORK MCC :268 << This bit[/COLOR]
NETWORK MNC :06
[COLOR=Blue]PROVIDER   :P  <<<< ?
REGISTERED :TMN <<<< ?[/COLOR]

```the service providers data base shows this config / compare the two / Database wrong info
```
gsm TMN
network-id mcc="[COLOR=Blue]286[/COLOR]" mnc="[COLOR=Blue]06[/COLOR]"
apn="internet"
username=tmn
password = tmn
DNS1=194.65.3.20
DNS2=194.65.3.21 
```NM need to configure for IPv4 Automatic address only enter in DNS SERVERS box ```
194.65.3.20,194.65.3.21
```before trying any connections with NM - lets check some info just in case / if get error at any stage use AT command "ATZ" then go to next command
open up first terminal
```
cat /dev/ttyACM0
```open up second terminal
```
cat /dev/ttyACM1
```open up third terminal
```
echo -e "AT+CGDCONT?\r" > /dev/ttyACM1
``````
echo -e "AT+COPS?\r" > /dev/ttyACM1
``````
echo -e "AT+COPS=0,2\r" > /dev/ttyACM1
```this command will take time while the modem searches for providers
```
echo -e "AT+COPS?\r" > /dev/ttyACM1
```noted from the script modem-manager is hanging onto the device , IE not disengaging after probing
```
[COLOR=Blue]DEVICE ENABLED : true <<<< this bit should show false[/COLOR]
ACTION :disconnect
DEVICE ENABLED : false
ACTION :enable
DEVICE ENABLE : true
```can try
```
sudo killall modem-manager 
```or a kinder way is to use the test script , it will tell MM to disable from the device

see if NM can connect , + post any data
found this info
> <network-id mcc="268" mnc="06"/>
<apn value="internet">
<plan type="postpaid"/>
<usage type="internet"/>
<name>Tmn Internet</name>
<username>tmn</username>
<password>tmn</password>
<dns>88.214.178.1</dns>
<dns>88.214.182.2</dns>
</apn><apn value="mmsc.tmn.pt">
<plan type="postpaid"/>
<usage type="mms"/>
<name>Tmn Mms</name>
<username>tmn</username>
<password>tmnnet</password>
<dns>194.65.3.20</dns>
<dns>194.65.3.21</dns>

NOTE: this may be what is required for the servers  AS from previous post the device is returning possible server id's ""135.3.0.0,126.147.34.0"" , IF NM not
connecting then will have to try alternate method of connecting:: or keep testing the device if this address is CONSTANT , more on that later

---

### Post by moma on 2012-05-13
Hello,

1) The DNS-values. 
These DNS values (194.65.3.20 and 194.65.3.21) do not work with  APN="internet". I tried them carefully both in Linux and Windows and they fail. Please take a look at this picture:
[[img]http://bildr.no/thumb/1180250.jpeg[/img]](http://bildr.no/view/1180250)

The correct DNS values for APN="internet" are 88.214.178.1 and 88.214.182.2. These worked well in my Windows test where I entered DNS-values manually.

I got these values from the serviceproviders.xml file.
$ [COLOR="DarkGreen"]sudo updatedb[/COLOR]
$ [COLOR="DarkGreen"]locate serviceproviders.xml[/COLOR]
/usr/share/mobile-broadband-provider-info/serviceproviders.xml 

Ok, I now understand that you took the DNS value for APN="mmsc.tmn.pt". Anyway, I think we should use the DNS 88.214.178.1, 88.214.178.2.

```
	<provider>
		<name>TMN</name>
		<gsm>
			<network-id mcc="268" mnc="06"/>
			<apn value="internet">
				<plan type="postpaid"/>
				<usage type="internet"/>
				<name>Tmn Internet</name>
				<username>tmn</username>
				<password>tmn</password>
				<dns>88.214.178.1</dns>
				<dns>88.214.182.2</dns>
			</apn>
			<apn value="mmsc.tmn.pt">
				<plan type="postpaid"/>
				<usage type="mms"/>
				<name>Tmn Mms</name>
				<username>tmn</username>
				<password>tmnnet</password>
				<dns>194.65.3.20</dns>
				<dns>194.65.3.21</dns>
			</apn>
```

The connection configuration wizard (for the modem) lets me choose between <apn value="internet"> and <apn value="mmsc.tmn.pt">. I have regularly chosen the "internet" because this is what I see in the Windows` configuration dialog. I have also tested the "mmsc.tmn.pt" in Linux. No success. I do not even know what it is.

2) The AT-commands:
 
# [COLOR="DarkGreen"]echo -e "AT+CGDCONT?\r" > /dev/ttyACM1[/COLOR]

```
    # cat /dev/ttyACM1:
    +CSQ: 16,0
    OK

    %NWSTATE: 4,26806,3G,-,0
    OK

    +CGDCONT: 1,"IP","internet","",0,0
    +CGDCONT: 2,"IP","internet","",0,0
    +CGDCONT: 3,"IP","internet.zon.pt","",0,0
    +CGDCONT: 4,"IP","mmsc.tmn.pt","",0,0
    +CGDCONT: 5,"IP","tmn","",0,0
    +CGDCONT: 6,"IP","tmn.pt","",0,0
    OK

    +CSQ: 14,0
    OK

    %NWSTATE: 4,26806,3G,-,0
    OK

```
[COLOR="DarkGreen"]echo -e "AT+COPS?\r" > /dev/ttyACM1
[/COLOR]
```
    # cat /dev/ttyACM1:
    +CSQ: 15,0
    OK

    +COPS: 0,0,"P TMN",6
    OK

    %NWSTATE: 4,26806,3G,-,0
    OK

    +CREG: 2,1,"0387","00229383",6
    OK

```
[COLOR="DarkGreen"]echo -e "AT+COPS=0,2\r" > /dev/ttyACM1
[/COLOR]
```
    # cat /dev/ttyACM1:
    +CGREG: 2,1,"0387","00229383",6,"01"
    OK
    OK
```

[COLOR="DarkGreen"]echo -e "AT+COPS?\r" > /dev/ttyACM1
[/COLOR]
```
    # cat /dev/ttyACM1:
    +CSQ: 15,0
    OK

    %NWSTATE: 4,26806,3G,-,0

    OK
    +COPS: 0,2,"26806",6
```

Notice: This last command is the same as the second one. Is this right?

The network-manager icon now tries to connect properly a few seconds time. At least it tries. And the menu selection changes too (like it already connected), but then it times out or something and returns to disconnected state.

Do not give me up. Not just yet!
----------------------------------------------------

[COLOR="Red"]EDIT:[/COLOR]
I made and experiment with the wvdial`er.

First, I ran wvdialconf that created a default /etc/wvdial.conf. 
$ [COLOR="DarkGreen"]sudo wvdialconf[/COLOR]

# from: wvdialconf
# Ref: [http://thesandeep.wordpress.com/2007/04/05/using-a-gsm-cellphone-as-a-gprs-modem/](http://thesandeep.wordpress.com/2007/04/05/using-a-gsm-cellphone-as-a-gprs-modem/)

$ [COLOR="DarkGreen"]cat /etc/wvdial.conf[/COLOR]
```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
#I have disabled the PIN-code in Windows.
#Init3 = AT+CPIN=0123
Init5 = AT+CGDCONT=1,"IP","internet"
Modem Type = USB Modem
Baud = 38400
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
Phone = *99#
Password = tmn
Username = tmn
Stupid Mode = 1
```

Here is the output of wvdial. 
$ [COLOR="DarkGreen"]sudo wvdial[/COLOR]
```
--> WvDial: Internet dialer version 1.61
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","internet"
AT+CGDCONT=1,"IP","internet"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
%NWSTATE: 3,26806,3G,R99,0
%NWSTATE: 3,26806,3G,R99,0
CONNECT 14400000
~~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Mon May 14 13:00:19 2012
--> Pid of pppd: 19706
--> Using interface ppp0
--> pppd: PQ< &#65533;P< 
--> pppd: PQ< &#65533;P< 
--> pppd: PQ< &#65533;P< 
--> pppd: PQ< &#65533;P< 
--> pppd: PQ< &#65533;P< 
--> local  IP address 95.69.73.81
--> pppd: PQ< &#65533;P< 
--> remote IP address 10.0.0.1
--> pppd: PQ< &#65533;P< 
--> primary   DNS address 88.214.182.1
--> pppd: PQ< &#65533;P< 
--> secondary DNS address 88.214.178.2
--> pppd: PQ< &#65533;P<
```

--------------------------

$ [COLOR="DarkGreen"]sudo wvdialconf create[/COLOR]
```
Editing `create'.
Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   S4   S5   S6   S7   
Modem Port Scan<*1>: S8   S9   S10  S11  S12  S13  S14  S15  
Modem Port Scan<*1>: S16  S17  S18  S19  S20  S21  S22  S23  
Modem Port Scan<*1>: S24  S25  S26  S27  S28  S29  S30  S31  
WvModem<*1>: Cannot get information for serial port.
ttyACM0<*1>: ATQ0 V1 E1 -- OK
ttyACM0<*1>: ATQ0 V1 E1 Z -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyACM0<*1>: Modem Identifier: ATI -- MF190J-2.0.0
ttyACM0<*1>: Speed 4800: AT -- OK
ttyACM0<*1>: Speed 9600: AT -- OK
ttyACM0<*1>: Speed 19200: AT -- OK
ttyACM0<*1>: Speed 38400: AT -- OK
ttyACM0<*1>: Speed 57600: AT -- OK
ttyACM0<*1>: Speed 115200: AT -- OK
ttyACM0<*1>: Speed 230400: AT -- OK
ttyACM0<*1>: Speed 460800: AT -- OK
ttyACM0<*1>: Max speed is 460800; that should be safe.
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
WvModem<*1>: Cannot get information for serial port.
ttyACM2<*1>: ATQ0 V1 E1 -- ERROR
ttyACM2<*1>: failed with 2400 baud, next try: 9600 baud
ttyACM2<*1>: ATQ0 V1 E1 -- ERROR
ttyACM2<*1>: failed with 9600 baud, next try: 115200 baud
ttyACM2<*1>: ATQ0 V1 E1 -- ERROR
ttyACM2<*1>: and failed too at 115200, giving up.

Found an USB modem on /dev/ttyACM0.
Modem configuration written to create.
ttyACM0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
```

---

### Post by moma on 2012-05-14
Re-hello,
I added a test with "wvdial" to my prev.posting.

[COLOR="Red"]EDIT:[/COLOR]
[SIZE="4"]**I think I got an internet connection with this 3G (UMTS) pin.**[/SIZE]

I just need to find out how?  I will come back with more info.

---

### Post by moma on 2012-05-14
**SUCCESS.**
Ok, I got internet access.

This is what I do.
1) Disable any ordinary (non 3G) wireless connection.
I simply rmmod the Atheros' wifi-driver just to make sure it does not interfere with my test. This 3G-pen may start roaming if it finds open wifi-networks.
$ [COLOR="DarkGreen"]sudo rmmod ath9k[/COLOR]
And the wireless drops down. 
This is for testing only. You don't need to do this.

2) Mode-switch requires these udev rules.
This ensures that the modem switches from USB-storage to USB-modem mode.** I think the /usr/bin/eject is the only required line.**
$ [COLOR="DarkGreen"]sudo gedit /lib/udev/rules.d/zte_modem.rules[/COLOR]

```
# Mode-switch of TMN ZTE MF190J modem.
# ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="1542", RUN+="/sbin/modprobe  option"

# From script 61-script.sh
ATTRS{idVendor}=="19d2",ATTRS{idProduct}=="1542",RUN+="/usr/bin/eject %k", OPTIONS+="last_rule"
ATTRS{idVendor}=="19d2",ATTRS{idProduct}=="1542",RUN+="usb_modeswitch '%b/%k'"
ATTRS{manufacturer}=="ZTE"

# ACTION=="add", SUBSYSTEM=="net", ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="1544", RUN="/sbin/ifconfig %k -arp"
```
Then re-boot, re-connect your 3G-modem.
Now the driver will load and create all necessary device files /dev/ttyACM0.../dev/ttyACM2.

3) Create or modify your /etc/wvdial.conf file. 
First, use the "sudo wvdialconf create" command to print all necessary info. 
$ [COLOR="DarkGreen"]sudo wvdialconf create[/COLOR]
In my case it says that the modem device is /dev/ttyACM0, so I set Modem=/dev/ttyACM0.

The APN (Access Point Name) may be different in your case. Portuguese TMN uses "internet" as APN name. I copied it from the Network/Modem Manager configuration. You may also try to comment it out, or simply ask your internet provider. 
#Init3 = AT+CGDCONT=1,"IP","internet"

$ [COLOR="DarkGreen"]cat /etc/wvdial.conf[/COLOR]

```
# This file was generated by "sudo wvdialconf".
# I edited it a bit.

[Dialer Defaults]
Init1 = ATZ
#This should set PIN-code but it fails.
#Init2 = AT+CPIN=0123  
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","internet"
Modem Type = USB Modem
Baud = 14400000
New PPPD = yes
#I changed this back to ttyACM0 !
Modem = /dev/ttyACM0
ISDN = 0
Phone = *99#
Password = tmn
Username = tmn
Stupid Mode = 1
```

4) Start the wvdial'er.
$ [COLOR="DarkGreen"]sudo wvdial[/COLOR]
```
--> WvDial: Internet dialer version 1.61
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT 14400000
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Mon May 14 14:16:16 2012
--> Pid of pppd: 13696
--> pppd: P1&#65533; &#65533;0&#65533; 
--> Using interface ppp0
--> pppd: P1&#65533; &#65533;0&#65533; 
--> pppd: P1&#65533; &#65533;0&#65533; 
--> pppd: P1&#65533; &#65533;0&#65533; 
--> pppd: P1&#65533; &#65533;0&#65533; 
--> local  IP address 188.140.83.77
--> pppd: P1&#65533; &#65533;0&#65533; 
--> remote IP address 10.0.0.1
--> pppd: P1&#65533; &#65533;0&#65533; 
--> primary   DNS address 88.214.182.1
--> pppd: P1&#65533; &#65533;0&#65533; 
--> secondary DNS address 88.214.178.2
--> pppd: P1&#65533; &#65533;0&#65533; 

```

Check syslog.
$ [COLOR="DarkGreen"]tail -F /var/log/syslog[/COLOR]
```
May 15 12:05:30 precise32 NetworkManager[1093]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
May 15 12:05:30 precise32 pppd[26660]: Connect: ppp0 <--> /dev/ttyACM0
May 15 12:05:30 precise32 pppd[26660]: Remote message: Icera PPP - Password Verified OK
May 15 12:05:30 precise32 pppd[26660]: PAP authentication succeeded
May 15 12:05:30 precise32 kernel: [ 1358.736795] PPP BSD Compression module registered
May 15 12:05:30 precise32 kernel: [ 1358.767152] PPP Deflate Compression module registered
May 15 12:05:33 precise32 pppd[26660]: local  IP address 188.140.83.77
May 15 12:05:33 precise32 pppd[26660]: remote IP address 10.0.0.1
May 15 12:05:33 precise32 pppd[26660]: primary   DNS address 88.214.182.2
May 15 12:05:33 precise32 pppd[26660]: secondary DNS address 88.214.178.1
```

And I have a good internet connection, but the network-manager or the nettwork applet has no idea what's going on. 
Take a look at this picture. 

[[img]http://bildr.no/thumb/1180868.jpeg[/img]](http://bildr.no/view/1180868)

The speed and feeling of the connection is exactly the same I get in Windows7. And the 3G-pen also blinks green as it does in Windows. EDIT: The (top)download speed in Linux is about 5% higher than in Windows7. I have data over several speed-tests. 

Now I need to reset this 3G-pen. Then I simply repeat this test in Linux.

BTW1: How to bake this in the network-manager/network-applet so it displays correct status for the connection? Now it simply hangs idle (ref. the picture).

BTW2: I have to run wvdial as sudo even my username is in "adm" and "dialout" groups. 
Are these groups important here?
$ groups
moma adm dialout cdrom sudo dip plugdev lpadmin sambashare

BTW3: The [Install]-button in the Ubuntu Software Center (USC) is disabled, and there is a text underneath saying "No network connection". But I can execute Install from the menu. I think USC consults the network-manager (NM) via DBus and gets wrong info (as said NM do not know better...). Not a big deal!

**Using gnome-ppp**
You can also use gnome-ppp with this (ZTE MF160J) 3G-modem. (I connect to my Portuguese TMN internet provider). 
$ [COLOR="DarkGreen"]sudo apt-get install gnome-ppp[/COLOR]

I like gnome-ppp because it has a [Disconnect]-button that hangs up the modem properly (sends necessary AT commands and disconnects the line). Its notification icon does not work in the Unity-desktop, but you can control it from the dialog.
Ref: [[img]http://bildr.no/thumb/1182904.jpeg[/img]](http://bildr.no/view/1182904)

[COLOR="Red"]Please notice:[/COLOR]
Add your username to the "dialout" group so you can run the gnome-ppp as ordinary user (do not need sudo). 
$ [COLOR="DarkGreen"]sudo usermod -a -G dialout $USER[/COLOR]
This will avoid the "Cannot open device /dev/ttyACM*..." messages.

Then logout/login. The change take effect after re-login. Ok?
Then check groups with 
$ [COLOR="DarkGreen"]groups[/COLOR]
Ref: [guide...]("http://polishlinux.org/linux/ubuntu/three-uk-3g-modem-in-ubuntu-linux/")

Start gnome-ppp and type in the configuration.

One option is quite important.
In the Setup/Options page, set the option "Ignore terminal strings (stupid mode)") ON. Ok?
This makes the connection much faster/immediate.

Here is my config file for gnome-ppp. 
It's saved in your $HOME-folder as a ".wvdial.conf" file.
Notice again that the phone number (*99#) and the /dev/tty* devices and APN-name may be different in your case. 
For TMN, I can pick the APN-value from the serviceproviders.xml file.
$ cat /usr/share/mobile-broadband-provider-info/serviceproviders.xml | grep -A 20 TMN

$ [COLOR="DarkGreen"]cat $HOME/.wvdial.conf[/COLOR]

```
[Dialer Defaults]
Modem = /dev/ttyACM0
ISDN = off
Modem Type = Analog Modem
Baud = 144000000
Init = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
# TMN uses "internet" as APN-name.
# Init3 = AT+CGDCONT=1,"IP","internet";
#
# Phone number for TMN 3G.
Phone = *99#
Dial Prefix = 
Dial Attempts = 1
Dial Command = ATM1L3DT
Ask Password = off
# Username / password.
Password = tmn
Username = tmn
Auto Reconnect = off
Abort on Busy = off
Carrier Check = on
Check Def Route = on
Abort on No Dialtone = on
# Notice: Set this option ON (In the GUI see: "Ignore terminal strings (stupid mode)")
Stupid Mode = on
Idle Seconds = 0
Auto DNS = on
;Minimize = off
;Dock = off
```

---

### Post by alexfish on 2012-05-14
Hi that be good news



should be able to connect without WVdial , some users may not , be able to download it
Was just about to post this ,:-
Can try this , go to yor post where the dial command was used , and got CONNECT message , repeat the process , you where using /dev/ttyACM1 .. but can change to ttyACM0

first going to try and connect trying to see if peer will give DNS , the next use peers DNS with passwords , see what happens
```

sudo pppd ttyACM1  nodetach defaultroute noipdefault noauth lock usepeerdns
```or with password ,
```
sudo pppd ttyACM1 nodetach defaultroute noipdefault noauth lock usepeerdns user <your-username> password <your-password>
```Note: this is a connection when primary and secondary servers show , from your wvdial
```
--> primary   DNS address 88.214.182.1 --> 
secondary DNS address 88.214.178.2
```

ADDED:
AS you mentioned MM is using ttyACM1 so seems reasonable Network manager is Trying to connect to wrong port via modem-manager
will  look into mm rules to see if can be rectified

---

### Post by alexfish on 2012-05-14
for modem manager can try edit mm port type rules
ADD:-
```
sudo gedit /lib/udev/rules.d/77-mm-zte-port-types.rules
``````
ATTRS{idProduct}=="1544", ENV{.MM_USBIFNUM}=="01", ENV{ID_MM_ZTE_PORT_TYPE_MODEM}="1"
ATTRS{idProduct}=="1544", ENV{.MM_USBIFNUM}=="03", ENV{ID_MM_ZTE_PORT_TYPE_AUX}="1"
```see what happens , use the test script ,

but also just try the connection

---

### Post by moma on 2012-05-15
Re-hi,
I will make a reinstallation of Ubuntu 12.04 just to make sure all config files are reset (if I had btrfs filesystem it could simply rollback). It may take couple of days before I can do the tests. I can already say that the /dev/ttyACM1 device indeed connected with success. Anyway, talk to you later. Thanks. Meanwhile I use the gnome-ppp because it can also disconnect/hang up properly.

---

### Post by alexfish on 2012-05-15
If can connect on both ports , monitor the speeds , one port could be 3g and other lte

got me thinking the device may also have , ether type connection[FONT=monospace], but not sure , once done what you got to do , then can start look at the modalias
of the device .. this port has no driver so may be worth looking at
as regards lte
[/FONT]```
I:  If#= 0 Alt= 0 #EPs= 0 Cls=00(>ifc ) Sub=08 Prot=00 Driver=(none)
```

---

### Post by moma on 2012-05-17
Re-hi,
I have now reinstalled Ubuntu 12.04.
The situation is unchanged. The network-manager does not connect but wvdial and gnome-ppp do.

1) Here are all syslog messages when I physically plugin the 3D-modem to this laptop. It shows couple of error messages that can be essential when debugging the source code of NM.

Please see: [http://pastebin.com/CMLRQUvJ](http://pastebin.com/CMLRQUvJ)
Study all the <warn> messages. Eg. it reports:

<[COLOR="Red"]warn[/COLOR]> GSM connection failed: (32) Unknown error
<[COLOR="Red"]warn[/COLOR]> Activation (ttyACM1) failed.
---------

2) I want to show you all messages when I start the gnome-ppp. I think its front-end to the wvdial command. This will also show all related syslog messages.

I have added my username the "dialout" group, so I can run gnome-ppp as an ordinary user (avoiding root/sudo).
$ [COLOR="DarkGreen"]sudo usermod -a -G dialout $USER[/COLOR]
This requires logout/re-login.

This listing shows that only root and "dialout" can access the devices:
$ [COLOR="DarkGreen"]ls -l /dev/ttyACM*[/COLOR]
crw-rw---- 1 root dialout 166, 0 May 17 12:38 /dev/ttyACM0
crw-rw---- 1 root dialout 166, 1 May 17 12:38 /dev/ttyACM1
crw-rw---- 1 root dialout 166, 2 May 17 12:36 /dev/ttyACM2

Study the following syslogs.

The modem device is **/dev/ttyACM0**.
See: [http://pastebin.com/yEj0Pp3w](http://pastebin.com/yEj0Pp3w)

Now the modem device is **/dev/ttyACM1**.
See: [http://pastebin.com/Dnwe6z8A](http://pastebin.com/Dnwe6z8A)

Both devices connect well. The speed seems to be pretty much the same. Individual tests varies more than than differences between ttyACM0 and ttyAC1, and I do not dare to download too much  because my contract has 15GB/month limit (all providers in Portugal set the same limit).
---------

3) Now to your pppd command. 
All of the sudo ppdd commands failed.

$ [COLOR="DarkGreen"]sudo pppd ttyACM0 debug nodetach defaultroute noipdefault noauth lock usepeerdns[/COLOR]
using channel 22
Using interface ppp0
Connect: ppp0 <--> /dev/ttyACM0
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xe9d0a053> <pcomp> <accomp>]
Hangup (SIGHUP)
Modem hangup
Connection terminated.
-----------

$ [COLOR="DarkGreen"]sudo pppd /dev/ttyACM0 debug nodetach defaultroute noipdefault noauth lock usepeerdns user tmn password tmn[/COLOR]
using channel 20
Using interface ppp0
Connect: ppp0 <--> /dev/ttyACM0
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xb5d40008> <pcomp> <accomp>]
Hangup (SIGHUP)
Modem hangup
Connection terminated.
-------------

/dev/ttyACM1 reported exactly the same; "Modem hangup".
-------------

4) Switching the ports in 77-mm-zte-port-types.rules.

$ [COLOR="DarkGreen"]sudo gedit /lib/udev/rules.d/77-mm-zte-port-types.rules [/COLOR]

```
ATTRS{idProduct}=="1544", ENV{.MM_USBIFNUM}=="01", ENV{ID_MM_ZTE_PORT_TYPE_MODEM}="1"
ATTRS{idProduct}=="1544", ENV{.MM_USBIFNUM}=="03", ENV{ID_MM_ZTE_PORT_TYPE_AUX}="1"
```

This did not help. I re-booted and re-connected, but for no help. The network-manager fails as usual.

The beginning of the rules file seems to have a check for the ATTRS{idVendor}=="19d2". So I added the new line at the very bottom.
----------

5) Next: I may dig to the source code of network-manager and modem-manager. What are the relevant packages?
$ [COLOR="DarkGreen"]apt-cache  search manager | egrep -i "modem|network" [/COLOR]
```
libnm-gtk-common - network management framework (common files for wifi and mobile)
libnm-gtk-dev - network management framework (dialogs development libraries)
modemmanager - D-Bus service for managing modems
modemmanager-dbg - D-Bus service for managing modems - debugging symbols
network-manager - network management framework (daemon and userspace tools)
network-manager-dev - network management framework (development files)
network-manager-gnome - network management framework (GNOME frontend)
network-manager-pptp - network management framework (PPTP plugin core)
network-manager-pptp-gnome - network management framework (PPTP plugin GNOME GUI)
```

---

### Post by alexfish on 2012-05-17
using the pppd commands directly fail ?

did you dial the modem first IE
```
echo -e "ATDT*99#\r" /dev/ttyACM0
``` and did you monitor the device in another terminal , if get the CONNECT message , then try the pppd command

When connected with wvdial can post results of
```
route -n
```
```
ifconfig
```need only post part of the pppd* connection

---

### Post by moma on 2012-05-17
Ok, let's try again.
# [COLOR="DarkGreen"]echo -e "ATDT*99#\r" > /dev/ttyACM0[/COLOR]

```
# cat /dev/ttyACM0:
NO CARRIER
ATDT*99#
CONNECT 14400000
~~
```
# [COLOR="DarkGreen"]pppd ttyACM0 nodetach defaultroute noipdefault noauth lock usepeerdns[/COLOR]
Using interface ppp0
Connect: ppp0 <--> /dev/ttyACM0
Modem hangup
Connection terminated.
----
Now the modem hangs up very quickly. It does not timeout. Here is the syslog for it. The pppd command blocks if I do  "cat /dev/ttyACM0", so here is the syslog.

$ [COLOR="DarkGreen"]tail -F /var/log/syslog[/COLOR]
```
May 17 18:20:05 precise32 pppd[7458]: pppd 2.4.5 started by moma, uid 0
May 17 18:20:05 precise32 NetworkManager[1119]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
May 17 18:20:05 precise32 NetworkManager[1119]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
May 17 18:20:05 precise32 pppd[7458]: Using interface ppp0
May 17 18:20:05 precise32 pppd[7458]: Connect: ppp0 <--> /dev/ttyACM0
May 17 18:20:05 precise32 pppd[7458]: Hangup (SIGHUP)
May 17 18:20:05 precise32 pppd[7458]: Modem hangup
May 17 18:20:05 precise32 pppd[7458]: Connection terminated.
May 17 18:20:05 precise32 NetworkManager[1119]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
May 17 18:20:06 precise32 pppd[7458]: Exit.

```
Results for the ttyACM1 are the same.
----
I'll come back with output from route -n and ifconfig.

$ [COLOR="DarkGreen"]gnome-ppp[/COLOR] (or sudo wvdial)
...

# [COLOR="DarkGreen"]route -n[/COLOR]
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
10.0.0.1        0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
```

# [COLOR="DarkGreen"]ifconfig[/COLOR] 
```
...
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:89.414.183.111  P-t-P:10.0.0.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:58 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:14200 (14.2 KB)  TX bytes:7137 (7.1 KB)
```

---

### Post by alexfish on 2012-05-17
the only dif can find in the paste bin is this line 
```
May 17 14:32:45 precise32 pppd[6427]: Remote message: Icera PPP - Password Verified OK
```this is been done by pppd , so something needs to be changed in the command line call ,
anyway for now wvdial works for you , but should be able to replicate using ppp direct
can make connections by calling pppconfig
```
sudo pppconfig
``` have fun

alexfish

---

### Post by moma on 2012-05-18
Yes, pppd connects fine after configuration.
$ [COLOR="DarkGreen"]sudo pppconfig[/COLOR]
I named this configuration to "portugalTMN".

It generated these three (3) files.
$ [COLOR="DarkGreen"]sudo updatedb[/COLOR]
$ [COLOR="DarkGreen"]locate portugalTMN[/COLOR]
 /etc/ppp/peers/portugalTMN
 /etc/chatscripts/portugalTMN
 /etc/ppp/resolv/portugalTMN

$ [COLOR="DarkGreen"]cat /etc/ppp/peers/portugalTMN[/COLOR]
```
# This optionfile was generated by pppconfig 2.3.18. 
hide-password 
noauth
connect "/usr/sbin/chat -v -f /etc/chatscripts/portugalTMN"
debug
/dev/ttyACM0
115200
defaultroute
noipdefault 
user "tmn"
remotename portugalTMN
ipparam portugalTMN
```

$ [COLOR="DarkGreen"]cat /etc/chatscripts/portugalTMN[/COLOR]
```
# This chatfile was generated by pppconfig 2.3.18.
# Please do not delete any of the comments.  Pppconfig needs them.
# 
# ispauth PAP
# abortstring
ABORT BUSY ABORT 'NO CARRIER' ABORT VOICE ABORT 'NO DIALTONE' ABORT 'NO DIAL TONE' ABORT 'NO ANSWER' ABORT DELAYED
# modeminit
'' ATZ
# ispnumber
OK-AT-OK "ATDT*99#"
# ispconnect
CONNECT \d\c
# prelogin

# ispname
# isppassword
# postlogin

# end of pppconfig stuff
```

$ [COLOR="DarkGreen"]cat /etc/ppp/resolv/portugalTMN[/COLOR]
```
# resolv.conf created by pppconfig for portugalTMN
#
```

Then connecting to the internet with pppd. **This works very well.** 
$ [COLOR="DarkGreen"]pppd debug call portugalTMN[/COLOR]

$ [COLOR="DarkGreen"]tail -F /var/log/syslog[/COLOR]
```
May 18 10:27:24 precise32 pppd[9619]: pppd 2.4.5 started by moma, uid 1000
May 18 10:27:25 precise32 chat[9621]: abort on (BUSY)
May 18 10:27:25 precise32 chat[9621]: abort on (NO CARRIER)
May 18 10:27:25 precise32 chat[9621]: abort on (VOICE)
May 18 10:27:25 precise32 chat[9621]: abort on (NO DIALTONE)
May 18 10:27:25 precise32 chat[9621]: abort on (NO DIAL TONE)
May 18 10:27:25 precise32 chat[9621]: abort on (NO ANSWER)
May 18 10:27:25 precise32 chat[9621]: abort on (DELAYED)
May 18 10:27:25 precise32 chat[9621]: send (ATZ^M)
May 18 10:27:25 precise32 chat[9621]: expect (OK)
May 18 10:27:25 precise32 chat[9621]: ATZ^M^M
May 18 10:27:25 precise32 chat[9621]: OK
May 18 10:27:25 precise32 chat[9621]:  -- got it
May 18 10:27:25 precise32 chat[9621]: send (ATDT*99#^M)
May 18 10:27:25 precise32 chat[9621]: expect (CONNECT)
May 18 10:27:25 precise32 chat[9621]: ^M
May 18 10:27:25 precise32 chat[9621]: ATDT*99#^M^M
May 18 10:27:25 precise32 chat[9621]: CONNECT
May 18 10:27:25 precise32 chat[9621]:  -- got it
May 18 10:27:25 precise32 chat[9621]: send (\d)
May 18 10:27:26 precise32 pppd[9619]: Script /usr/sbin/chat -v -f /etc/chatscripts/portugalTMN finished (pid 9620), status = 0x0
May 18 10:27:26 precise32 pppd[9619]: Serial connection established.
May 18 10:27:26 precise32 pppd[9619]: using channel 16
May 18 10:27:26 precise32 pppd[9619]: Using interface ppp0
May 18 10:27:26 precise32 NetworkManager[961]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
May 18 10:27:26 precise32 NetworkManager[961]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
May 18 10:27:26 precise32 pppd[9619]: Connect: ppp0 <--> /dev/ttyACM0
May 18 10:27:27 precise32 pppd[9619]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x70cb5845> <pcomp> <accomp>]
May 18 10:27:27 precise32 pppd[9619]: rcvd [LCP ConfReq id=0x1 <mru 1600> <auth pap> <magic 0x66c117c0> <asyncmap 0x0> <pcomp> <accomp>]
May 18 10:27:27 precise32 pppd[9619]: sent [LCP ConfAck id=0x1 <mru 1600> <auth pap> <magic 0x66c117c0> <asyncmap 0x0> <pcomp> <accomp>]
May 18 10:27:27 precise32 pppd[9619]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x70cb5845> <pcomp> <accomp>]
May 18 10:27:27 precise32 pppd[9619]: sent [LCP EchoReq id=0x0 magic=0x70cb5845]
May 18 10:27:27 precise32 pppd[9619]: sent [PAP AuthReq id=0x1 user="tmn" password=<hidden>]
May 18 10:27:27 precise32 pppd[9619]: rcvd [LCP EchoRep id=0x0 magic=0x66c117c0]
May 18 10:27:27 precise32 pppd[9619]: rcvd [PAP AuthAck id=0x1 "Icera PPP - Password Verified OK"]
May 18 10:27:27 precise32 pppd[9619]: Remote message: Icera PPP - Password Verified OK
May 18 10:27:27 precise32 pppd[9619]: PAP authentication succeeded
May 18 10:27:27 precise32 pppd[9619]: sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
May 18 10:27:27 precise32 pppd[9619]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 18 10:27:27 precise32 pppd[9619]: rcvd [IPCP ConfReq id=0x1 <addr 10.0.0.1>]
May 18 10:27:27 precise32 pppd[9619]: sent [IPCP ConfAck id=0x1 <addr 10.0.0.1>]
May 18 10:27:27 precise32 pppd[9619]: rcvd [IPV6CP ConfReq id=0x1 <addr fe80::c464:7457:a52c:0996>]
May 18 10:27:27 precise32 pppd[9619]: Unsupported protocol 'IPv6 Control Protocol' (0x8057) received
May 18 10:27:27 precise32 pppd[9619]: sent [LCP ProtRej id=0x2 80 57 01 01 00 0e 01 0a c4 64 74 57 a5 2c 09 96]
May 18 10:27:27 precise32 pppd[9619]: rcvd [LCP ProtRej id=0x0 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f 32]
May 18 10:27:27 precise32 pppd[9619]: Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
May 18 10:27:27 precise32 pppd[9619]: rcvd [IPCP ConfRej id=0x1 <compress VJ 0f 01>]
May 18 10:27:27 precise32 pppd[9619]: sent [IPCP ConfReq id=0x2 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 18 10:27:30 precise32 pppd[9619]: sent [IPCP ConfReq id=0x2 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
May 18 10:27:30 precise32 pppd[9619]: rcvd [IPCP ConfNak id=0x2 <addr 188.140.91.196> <ms-dns1 88.214.182.1> <ms-dns2 88.214.178.2>]
May 18 10:27:30 precise32 pppd[9619]: sent [IPCP ConfReq id=0x3 <addr 188.140.91.196> <ms-dns1 88.214.182.1> <ms-dns2 88.214.178.2>]
May 18 10:27:30 precise32 pppd[9619]: rcvd [IPCP ConfAck id=0x3 <addr 188.140.91.196> <ms-dns1 88.214.182.1> <ms-dns2 88.214.178.2>]
May 18 10:27:30 precise32 pppd[9619]: local  IP address 188.123.91.123
May 18 10:27:30 precise32 pppd[9619]: remote IP address 10.0.0.1
May 18 10:27:30 precise32 pppd[9619]: primary   DNS address 88.214.182.1
May 18 10:27:30 precise32 pppd[9619]: secondary DNS address 88.214.178.2
May 18 10:27:30 precise32 pppd[9619]: Script /etc/ppp/ip-up started (pid 9624)
May 18 10:27:31 precise32 pppd[9619]: Script /etc/ppp/ip-up finished (pid 9624), status = 0x0
```

Closing down the connection.
$ [COLOR="DarkGreen"]pkill pppd[/COLOR]
```
May 18 10:27:57 precise32 pppd[9619]: sent [LCP EchoReq id=0x1 magic=0x70cb5845]
May 18 10:27:57 precise32 pppd[9619]: rcvd [LCP EchoRep id=0x1 magic=0x66c117c0]
May 18 10:28:01 precise32 pppd[9619]: Terminating on signal 15
May 18 10:28:01 precise32 pppd[9619]: Connect time 0.6 minutes.
May 18 10:28:01 precise32 pppd[9619]: Sent 190225 bytes, received 8152860 bytes.
May 18 10:28:01 precise32 pppd[9619]: Script /etc/ppp/ip-down started (pid 9868)
May 18 10:28:01 precise32 pppd[9619]: sent [LCP TermReq id=0x3 "User request"]
May 18 10:28:01 precise32 pppd[9619]: rcvd [LCP TermAck id=0x3]
May 18 10:28:01 precise32 pppd[9619]: Connection terminated.
May 18 10:28:01 precise32 NetworkManager[961]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
May 18 10:28:03 precise32 pppd[9619]: Script /etc/ppp/ip-down finished (pid 9868), status = 0x0
May 18 10:28:03 precise32 pppd[9619]: Exit.
```

Many thanks for your help Alexfish.
This has been an interesting ride. I have learned so many new things. And wvdial, gnome-ppp and this new pppd command give me a perfect internet connection over this 3G-pen. I'm sure we'll find a fix for the modem-manager or network-manager too.  So long... ;-) All good fish.

---

### Post by surja on 2012-05-22
when are we going to get a fix for this? I had to install Linux Mint 12 because of this very irritating time wasting problem with 3G modems on Ubuntu 12.04.
the reported bug on Launchpad has been sitting idle for quite some now. Alexfish, since you seem to know a lot about this problem, can't you push out an update to fix this painful mess?

---

### Post by alexfish on 2012-05-22
> **surja said:**
> when are we going to get a fix for this? I had to install Linux Mint 12 because of this very irritating time wasting problem with 3G modems on Ubuntu 12.04.
the reported bug on Launchpad has been sitting idle for quite some now. Alexfish, since you seem to know a lot about this problem, can't you push out an update to fix this painful mess?[FONT=monospace]
[/FONT]```
sudo pppconfig
```
```
pon my-connetion
```
NEED FULL USE OF YOUR DONGLE
```
sudo apt-get install gammu
```:P

---

### Post by old_man0 on 2012-06-06
Ok, same her with Huawei E173.
Since precise nothing is working, even popup for pin is not any more. :(
Have to try in detail to be able to report later.

---

### Post by alexfish on 2012-06-06
> **old_man0 said:**
> Ok, same her with Huawei E173.
Since precise nothing is working, even popup for pin is not any more. :(
Have to try in detail to be able to report later.

Hi 
can post the results of this command from the terminal
```
usb-devices
```

regards

alexfish

---

