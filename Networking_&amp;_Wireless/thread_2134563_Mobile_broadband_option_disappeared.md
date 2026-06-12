---
title: "Mobile broadband option disappeared"
date: 2013-04-11
forum: Networking &amp; Wireless
---

### Post by anthoj on 2013-04-11
Hello, I'm new to this forum. I've just joined in hopes of learning more about my freshly installed Ubuntu. I am also new to the Linux world so please excuse my lack of general knowledge in this field. I successfully installed Ubuntu 12.10 (64 bit) on my Thinkpad X201 with built-in Qualcomm Gobi 2000 WWAN Modem today. At first, everything worked right out of the box. I was able to select and connect (after going through a configuration wizard), to my network provider just as I usually do on my Windows side. I'm not sure if it was the 300 mb worth of update I did afterwards or something else, but as I am typing this now, mobile broadband no longer shows up on the list of things I can connect to (I only have Wifi and VPN now). I tried opening the Network Manager and it doesn't show up there either. When I hit edit connections under the wireless icon on the top right of my screen, one of the tabs there (aside from wifi and vpn) is my Mobile Broadband, with my previous working configuration that I did through the wizard.

Can someone please tell me what happened to my mobile broadband? I looked through several forums and I'm pretty positive that my system still recognizes the device, but somehow not letting me activate the connection. I tried running a number of commands in terminal, although I must admit I haven't got a single clue as to what I'm doing... But here are some of the things I've tried:

```
rfkill list
```

which resulted in the following output:

```
1: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: tpacpi_wwan_sw: Wireless WAN
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

and this command:

```
usb-devices
```

which generated a list of components, with the following as its last entry:

```
T:  Bus=02 Lev=02 Prnt=02 Port=03 Cnt=01 Dev#=  3 Spd=480 MxCh= 0D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=05c6 ProdID=9204 Rev=00.02
S:  Manufacturer=Qualcomm Incorporated
S:  Product=Qualcomm Gobi 2000
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=qcserial

```

These are things that lead me to believe that the device is detected and recognized by my system, but again, I have no way of activating the connection.

Does anyone know what the problem might be? I would really appreciate any input you can give me. Thanks in advance.

---

### Post by alexfish on 2013-04-11
Don't know much about gobi ,

see what nm-tool shows,

```
nm-tool
```

can possibly try deleting the original connection details in Network Manager , disconnect the device ,
reboot , as you would have done normally, this used to do the trick on earlier versionof Ubuntu , but not sure about 12 +

then see if it will configure.

Since U can not get a conection , possible Modem-manager is not seeing the device , 

can also look at the syslog , see what is happening , Modem-Manager normal logs the details there.

Alex

---

### Post by tehwizardd on 2013-04-11
I have this same issue with Huawei 353. It's there, but sometimes it dissappears from the panel. When I turn WIFI off and on, it appears to be back after some time. Weird.

---

### Post by anthoj on 2013-04-11
> **alexfish said:**
> Don't know much about gobi ,

see what nm-tool shows,

```
nm-tool
```

can possibly try deleting the original connection details in Network Manager , disconnect the device ,
reboot , as you would have done normally, this used to do the trick on earlier versionof Ubuntu , but not sure about 12 +

then see if it will configure.

Since U can not get a conection , possible Modem-manager is not seeing the device , 

can also look at the syslog , see what is happening , Modem-Manager normal logs the details there.

Alex

Thanks for the reply Alex. I ran the network manager tool as you suggested. And you're right, the network manager is not seeing the device. Here's what shows up:

```

NetworkManager Tool


State: connected (global)


- Device: wlan0  [Deimos] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        00:27:10:9D:18:E4


  Capabilities:
    Speed:           39 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    Callisto:        Infra, 00:25:9C:F6:EB:49, Freq 2452 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2
    MY INTERNET:     Infra, 20:AA:4B:CC:86:C6, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    Chronos:         Infra, 00:16:B6:E1:27:6C, Freq 2462 MHz, Rate 54 Mb/s, Strength 64 WEP
    *Deimos:         Infra, C8:D7:19:AE:D9:83, Freq 2462 MHz, Rate 54 Mb/s, Strength 48 WPA2


  IPv4 Settings:
    Address:         192.168.1.125
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             208.67.222.222
    DNS:             208.67.220.220
    DNS:             202.73.99.2




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        F0:DE:F1:8E:2E:C1


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off

```

Looks to me like only wifi and ethernet are detected here. 

I also looked at my syslog, here's what I've been able to find in relation to my 3G modem:

```

Apr 11 18:36:27 ubuntu kernel: [   68.043484] qmi_wwan 2-1.4:1.0: >cdc-wdm1: USB WDM device
Apr 11 18:36:27 ubuntu kernel: [   68.043633] qmi_wwan 2-1.4:1.0: >wwan0: register 'qmi_wwan' at usb-0000:00:1d.0-1.4, Qualcomm WWAN/QMI device, 7a:ee:0a:8d:cf:7e
Apr 11 18:36:27 ubuntu kernel: [   68.043651] qmi_wwan 2-1.4:1.1: >not on our whitelist - ignored
Apr 11 18:36:27 ubuntu kernel: [   68.043665] qmi_wwan 2-1.4:1.2: >not on our whitelist - ignored
Apr 11 18:36:27 ubuntu kernel: [   68.043674] qmi_wwan 2-1.4:1.3: >not on our whitelist - ignored
Apr 11 18:36:27 ubuntu kernel: [   68.043700] usbcore: registered new interface driver qmi_wwan

Apr 11 18:36:27 ubuntu kernel: [   68.827001] thinkpad_acpi: rfkill switch tpacpi_wwan_sw: radio is unblocked

Apr 11 18:36:31 ubuntu NetworkManager[7274]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/net/wwan0, iface: wwan0)
Apr 11 18:36:31 ubuntu NetworkManager[7274]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/net/wwan0, iface: wwan0): no ifupdown configuration found.

Apr 11 22:00:22 ubuntu kernel: [   35.131433] thinkpad_acpi: rfkill switch tpacpi_wwan_sw: radio is unblocked

Apr 11 22:52:54 ubuntu kernel: [   23.170371] thinkpad_acpi: rfkill switch tpacpi_wwan_sw: radio is unblocked



```


Do you see anything out of the ordinary?

Tony

---

### Post by anthoj on 2013-04-11
> **tehwizardd said:**
> I have this same issue with Huawei 353. It's there, but sometimes it dissappears from the panel. When I turn WIFI off and on, it appears to be back after some time. Weird.

Tehwizardd, which version Ubuntu are you running? Is your Huawei detected in the network manager tool?

Tony

---

### Post by anthoj on 2013-04-11
Alright so I figured out that the firmware have somehow disappeared after the first install (Thanks Alex for making me realize that my card is not detected by nm-tool). I don't know how this is possible but I did find a way to get my GSM modem back. Here are the steps for future reference, specifically for people with Gobi 2000 hardware:

First install gobi-loader-tp by adding a new repo from linrunner (thinkpad-extras):

```

sudo add-apt-repository ppa:linrunner/thinkpad-extras
sudo apt-get update
sudo apt-get install gobi-loader-tp

```

Then either download the driver package directly from Lenovo ([Lenovo X201 Qualcomm Gobi 2000 WWAN Driver]("http://download.lenovo.com/ibmdl/pub/pc/pccbbs/mobiles/7xwc48ww.exe")) and extract, or smply grab it from your windows folder under C:\Program Files (x86)\QUALCOMM\Images\Lenovo\, which contains 11 folders (C:\Program Files\QUALCOMM\Images\Lenovo\ for 32-bit OS).

There are 3 files that you need: amss.mbn, apps.mbn, and UQCN.mbn, but they may be located in one or more folders of the 11 mentioned earlier. These files are carrier dependent, so you have to choose the right one depending on your modem. To know which files you need, go to the [Qualcomm Gobi Thinkpad Wiki site]("http://www.thinkwiki.org/wiki/Qualcomm_Gobi_2000") and see the table under "Choosing The Right Firmware". Mine was found under "6" folder and the "UMTS" folder because I have an unlocked modem.

Once you have acquired the files, create a new folder under /lib/firmware/ and call it "gobi" with no quotes. You will need to do a gksudo nautilus to use the GUI. Then copy the three files above into your newly created folder. Restart and you should now have your modem back.

I hope that will help anyone with mobile broadband disappearing from the network applet dropdown.

Tony

---

### Post by alexfish on 2013-04-12
Hi  anthoj

I think you are amazing , puting two and two together makes 4 , in Luxux terms , A ok

Think will go far, 

Thanks From Ubuntu and Ubuntu Forums ,

Br

Alex

PS Mods Log this this one.

+ I need new key key oaed

Have fun.

---

### Post by anthoj on 2013-04-13
Hi Alex, thanks for the compliments, but it looks like there's another issue with Ubuntu, and I think this is what[COLOR=#000000] [/COLOR]Tehwizardd was talking about. My connection would work for like an hour before it just disappears. Then I'll have to turn on/off the WiFi and then it'll come back and work for another hour before it happens again. I wonder what's going on. But for now, I can live with having to reset my connection every hour when I'm mobile.

---

