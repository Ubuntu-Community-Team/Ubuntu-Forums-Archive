---
title: "vodafone mobile broadband (k3806-z) modem not listed by network manager"
date: 2011-02-04
forum: Networking &amp; Wireless
---

### Post by rdh61 on 2011-02-04
Hi,

I have a k3806-z vodafone mobile broadband modem, on ubuntu 10.04. I have added the  mobile broadband connection with the network manager wizard. But network  manager does not list my connection. I installed usb-modeswitch and  usb-modeswitch-data. Still nothing. The disc utility tells me it  recognises the modem as a cd drive and a storage device. Evidently  usb-modeswitch is not working.

Any help greatly appreciated.

---

### Post by alexfish on 2011-02-04
can post the results of this command from the terminal
```
usb-devices
```

post the results

---

### Post by rdh61 on 2011-02-04
Thanks for the support. The output is:

```
robert@robert-laptop:~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.32-28-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=03 Cnt=01 Dev#=  3 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=05e3 ProdID=0608 Rev=07.02
S:  Product=USB2.0 Hub
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=02 Prnt=03 Port=00 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1307 ProdID=0163 Rev=01.00
S:  Manufacturer=USBest Technology
S:  Product=USB Mass Storage Device
S:  SerialNumber=00000000000386
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=80mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=01 Lev=02 Prnt=03 Port=01 Cnt=02 Dev#=  5 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=093a ProdID=2510 Rev=01.00
S:  Manufacturer=PIXART
S:  Product=USB OPTICAL MOUSE
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid

T:  Bus=01 Lev=02 Prnt=03 Port=02 Cnt=03 Dev#=  6 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=1013 Rev=00.01
S:  Manufacturer=Vodafone (ZTE)
S:  Product=K3806-Z
S:  SerialNumber=9546CD5893AC2522193F727B1EE3AC6FE825D298
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-28-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-28-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=03f0 ProdID=7d04 Rev=01.00
S:  Manufacturer=HP
S:  Product=Deskjet F2100 series
S:  SerialNumber=CN7CO4R2N104TK
C:  #Ifs= 3 Cfg#= 1 Atr=c0 MxPwr=2mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=cc Prot=00 Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 3 Cls=07(print) Sub=01 Prot=02 Driver=usblp
I:  If#= 2 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-28-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
robert@robert-laptop:~$
```

---

### Post by jimmers on 2011-02-04
Hi,
Try this, worked for me, may not for you, but worth a try:

  	 	 	 	p { margin-bottom: 0.21cm; }  This file explains how to install VMC 3G connection manager using Ubuntu.tgz file, in a Ubuntu Jaunty (9.04) system.  
 

 This how-to is focused on console commands.  
 

 NOTE: Ubuntu.tgz file provides necessary packages to install vmc, but more updated ones are available at this url:  
 [https://forge.betavine.net/frs/?group_id=12](https://forge.betavine.net/frs/?group_id=12) 
 

 First of all we uncompress Ubuntu.tgz file:  
 $tar xvfz Ubuntu.tgz  
 

 and then some files are created:  
 

 Ubuntu/  
 Ubuntu/ozerocdoff_0.4-2_i386.deb  
 Ubuntu/usb-modeswitch_0.9.7_i386.deb  
 Ubuntu/vodafone-mobile-connect_2.20.01-1_all.deb 
 Ubuntu/INSTALL_UBUNTU.TXT  
 

 usb_modeswitch and ozerocdoff packages are needed for some usb devices to switch working mode from memory into modem.  
 

 vodafone-mobile-connect is the 3G manager itself.  
 

 INSTALL_UBUNTU.TXT is this file.  
 

 USB_MODESWITCH  
 Most usb modems need this package.  
 

 We install it:  
 $sudo dpkg -i usb-modeswitch_0.9.7_i386.deb  
 

 OZEROCDOFF  
 ozerocdoff is needed for some HSO cards.  
 

 We install it:  
 $sudo dpkg -i ozerocdoff_0.4-2_i386.deb 
 

 VMC PACKAGE  
 

 We install vmc dependencies prior to install vmc itself:  
 TODO: ADD MORE DEPENDENCIES.  
 $sudo aptitude install wvdial hal usb-modeswitch ozerocdoff python-twisted python-serial python-sqlite python-tz python-gobject python-dbus python-cairo python-crypto python-gtk2 python-gnome2 python-gnome2-extras lsb-release python-glade2  
 

 We install vmc package:  
 $sudo dpkg -i vodafone-mobile-connect_2.20.01-1_all.deb  
 

 EXECUTING THE APP  
 You could run vmc:  
 $vodafone-mobile-connect-card-driver-for-linux or if you want to obtain a log:  
 $vodafone-mobile-connect-card-driver-for-linux-debug root will always be able to execute the application.  
 

 IMPORTANT NOTE: A standard user needs to pertain to >> dialout << group to run vmc.  
 

Luck

---

### Post by moody_mark on 2011-02-04
A member of my family had a T-Mobile dongle, and I found although when I plugged it in, it was getting mounted like a USB device in Nautilus, which although ok, stopped it being useable as a dongle. Heres what I did, it might help you.

1. Plug in the dongle, open up Nautilus or your regular file browser.
2. Find the device, right click and choose "unmount"
3. Go to network manager right click on the icon and select "edit connections"
4. Select the "mobile broadband" tab, click the "add" button
5. Follow the setup screens, its usually pretty straightforward.
6. The device should then show up in network manager.

Everytime we plugged it in thereafter we had to unmount it before using it

Hope this might help some.

---

### Post by rdh61 on 2011-02-04
Thanks for taking the time. 

I had already installed the latest ozerocdoff, usb-modeswitch, and vodafone mobile connect packages. When I run vmc, I get a GUI asking me to select my device. The "Known devices" option is not available ("No known devices found"). The custom device settings asks me to provide the following info:
- Device type (drop down box, only entry says "Serial")
- Data port device 
- Control port device
- Speed connection

I do not know what to put in "data port device" or "control port device". In "speed connection" I find a default: 115200.

Unless I provide the info I can't proceed.

---

### Post by rdh61 on 2011-02-04
Hey Moody Mark, thanks. Progress: with your help now my broadband connection appears in Network Manager.

BUT

It won't connect.

If I run vodafone-mobile-connect, I get the following:

```
get_plugin_by_vendor_product_id called with 0x19D2 and 0x1015
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/twisted/application/app.py", line 693, in run
    runApp(config)
  File "/usr/lib/python2.6/dist-packages/twisted/scripts/twistd.py", line 23, in runApp
    _SomeApplicationRunner(config).run()
  File "/usr/lib/python2.6/dist-packages/twisted/application/app.py", line 411, in run
    self.application = self.createOrGetApplication()
  File "/usr/lib/python2.6/dist-packages/twisted/application/app.py", line 494, in createOrGetApplication
    application = getApplication(self.config, passphrase)
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/twisted/application/app.py", line 505, in getApplication
    application = service.loadApplication(filename, style, passphrase)
  File "/usr/lib/python2.6/dist-packages/twisted/application/service.py", line 390, in loadApplication
    application = sob.loadValueFromFile(filename, 'application', passphrase)
  File "/usr/lib/python2.6/dist-packages/twisted/persisted/sob.py", line 210, in loadValueFromFile
    exec fileObj in d, d
  File "/usr/share/vodafone-mobile-connect/gtk-tap.py", line 49, in <module>
    from vmc.gtk.startup import check_dependencies, GTKSerialService
  File "/usr/share/vodafone-mobile-connect/vmc/gtk/startup.py", line 41, in <module>
    from vmc.common.hardware.hardwarereg import hw_reg
  File "/usr/share/vodafone-mobile-connect/vmc/common/hardware/hardwarereg.py", line 27, in <module>
    from vmc.common.hardware._unixhardwarereg import hw_reg
  File "/usr/share/vodafone-mobile-connect/vmc/common/hardware/_unixhardwarereg.py", line 474, in <module>
    hw_reg = HardwareRegistry()
  File "/usr/share/vodafone-mobile-connect/vmc/common/hardware/_unixhardwarereg.py", line 122, in __init__
    d = self.get_devices()
  File "/usr/share/vodafone-mobile-connect/vmc/common/hardware/_unixhardwarereg.py", line 151, in get_devices
    d = self._get_devices_from_udis(parent_udis)
  File "/usr/share/vodafone-mobile-connect/vmc/common/hardware/_unixhardwarereg.py", line 184, in _get_devices_from_udis
    unknown_devs = map(self._get_device_from_udi, udis)
  File "/usr/share/vodafone-mobile-connect/vmc/common/hardware/_unixhardwarereg.py", line 177, in _get_device_from_udi
    device = self._get_device_from_info_and_ports(info, udi, ports)
  File "/usr/share/vodafone-mobile-connect/vmc/common/hardware/_unixhardwarereg.py", line 405, in _get_device_from_info_and_ports
    raise RuntimeError("Couldn't find a plugin with info %s" % info)
exceptions.RuntimeError: Couldn't find a plugin with info {'usb_device.vendor_id': dbus.Int32(6610, variant_level=1), 'usb_device.product_id': dbus.Int32(4117, variant_level=1)}

Failed to load application: Couldn't find a plugin with info {'usb_device.vendor_id': dbus.Int32(6610, variant_level=1), 'usb_device.product_id': dbus.Int32(4117, variant_level=1)}
```

---

### Post by rdh61 on 2011-02-04
And if I use Sakis3g, it seems to have succeeded, saying:

"K3806-Z connected to vodafone IT (22210)"

And the blue light stays on on the USB modem, indicating connection.

BUT

1) I can't browse or send/receive emails.

2) If I click on the Vodafone broadband connection listed under Network Manager, I get a window saying: "GSM Network Disconnected".

---

### Post by alexfish on 2011-02-04
HI

after sakis3g connects

if using firefox check the menu file work off line / mode

or can try from the terminal

check primary and secondary servers are in resolv.conf

```
cat /etc/resolv.conf
```can also try

```
sudo su
``````
printf "\niface eth111 inet dhcp\n" >> /etc/network/interfaces
```also need to know if modem-manager  still exists after installing vmc

```
which modem-manager
```

looking at previous posts
if the eject command works try making a rule

  #[**36**]("http://ubuntuforums.org/showpost.php?p=9953330&postcount=36")

edit the ID's of the Device According to this prt of the result of "usb-devices"

P: Vendor=[COLOR=Blue]1d6b[/COLOR] ProdID=[COLOR=Blue]0001[/COLOR]

---

### Post by rdh61 on 2011-02-04
> **alexfish said:**
> HI

after sakis3g connects

if using firefox check the menu file work off line / mode




Good. Had tried this before but hadn't waited long enough. Requires 15 seconds then connects and can browse. Many thanks.

Network manager still behaving odd. "Mobile broadband" is labelled "not enabled" even though am browsing. If I right click on network manager icon then click "enable broadband", nothing happens: it is still "not enabled".


> **alexfish said:**
> 
or can try from the terminal

check primary and secondary servers are in resolv.conf

```
cat /etc/resolv.conf
```

robert@robert-laptop:~$ cat /etc/resolv.conf
nameserver 83.224.70.93
nameserver 83.224.66.134
# Generated by NetworkManager

> **alexfish said:**
> 
can also try

```
sudo su
``````
printf "\niface eth111 inet dhcp\n" >> /etc/network/interfaces
```

Nothing happens.

> **alexfish said:**
> 
also need to know if modem-manager  still exists after installing vmc

```
which modem-manager
```

/usr/sbin/modem-manager

> **alexfish said:**
> 
looking at previous posts
if the eject command works try making a rule

  #[**36**]("http://ubuntuforums.org/showpost.php?p=9953330&postcount=36")

edit the ID's of the Device According to this prt of the result of "usb-devices"

P: Vendor=[COLOR=Blue]1d6b[/COLOR] ProdID=[COLOR=Blue]0001[/COLOR]

Instructions from link were:

______________________________________________________________________

Code:

sudo gedit /lib/udev/rules.d/40-usb_modeswitch.rules

scroll down to the line which shows the id's of the device

EXAMPLE:

# Huawei E169
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1001", RUN+="usb_modeswitch '%b/%k'"

disable the line with a # . Add a line so it looks like the below . also double check the ID's prior to saving

# Huawei E169
#ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1001", RUN+="usb_modeswitch '%b/%k'"
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1001", RUN+="/sbin/modprobe option"

save the file : unplug the device then reconnect : note changes by using the "usb-devices" command

this will hopefully do two things

1. device should no longer appear on the desktop
2. load the option driver

________________________________________________________________________


40-usb_modeswitch.rules file was empty. I added the following:

#Vodafone K3806-Z
#ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="1013", RUN+="usb_modeswitch '%b/%k'"
ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="1013", RUN+="/sbin/modprobe option"

This made no difference. The device still appears on the desktop, and I still have to eject the device in Nautilus.

---

### Post by rdh61 on 2011-02-04
It would be really nice if you could help me make that usb-modeswitch rule effective, and to be able to connect automatically without having to go through Sakis3g every time, which is a bore. Many thanks.

---

### Post by alexfish on 2011-02-04
not sure if all of the link was read from start to fin

try this , as related to the link , but here is the how to with , your device ID's


```
sudo gedit /etc/udev/rules.d/zte_eject.rules
```add this line edit the device ID's according to the device

```
SYSFS{idVendor}=="1d6b", SYSFS{idProduct}=="0001", RUN+="/usr/bin/eject %k", OPTIONS+="last_rule"
```save exit and reboot with the device attached.

see what happens

Not all devices require usb_modeswitch to work , if the device appears in disk utilty or on the desktop
can try eject or safely remove , but monitor the results

Sakisg 3g may seem a bore from an aspect of , it can take time ,
 if you try sakis3g in debug mode , and read , the results , see what it does ,then perhaps you will have an understanding of how it works,to put into words, this thread would not be long enough

if you need sms facilities etc , and have a connection , could try
wammu, which will install gammu, 

enjoy,
 at least for now the device connects , build on that

also noted that after running sakis3g , the device was recognized by NM

alexfish

---

### Post by rdh61 on 2011-02-09
Thanks for the "how to" Alexfish. Unfortunately my device still doesn't switch and needs to be manually ejected.

My comments re Sakis3g were prompted by the quite long-winded procedure. After ejecting my device and waiting 20 seconds for it to fire up again, Sakis3g requires several steps of option-choosing, including putting in administrator password, and choosing one of three interfaces. This choice is hazardous: the "right" interface seems to change each time, and if you get it wrong you have to unplug the device and start again.

I appreciate what you say about reading up how to use it, but this involves A LOT of time, interpreting (probably wrongly) unclear instructions, and doing lots of command-line stuff, trials and false leads... and honestly, if you have a life outside computers, and just want stuff to work as it should (and isn't that what ubuntu is about?)... well, it's too much for me.

I tried to install the devices own drivers using ndiswrapper. Got an error message, driver however installed but then unusable (labelled "invalid driver").

Ho hum... Can anybody help me as to why Network Manager will not manage this device properly? It lists the connection, but if I click on it, I am told "GSM network disconnected".

Thanks again.

---

### Post by rdh61 on 2011-02-09
I add this just in case it may help others. Vodafone mobile connect software for Ubuntu DOES NOT WORK with this device. But I found it can be made to work like this:

1) As root browse for the "zte_k3805.py" file. There are 2 instances of it: 
usr/share/vodafone-mobile-connect/plugins/devices
home/yourhome/.vmc2/plugins/devices (hidden file: click "view"->"show hidden files")

2) Copy the file and change the name of the copy to "zte_k3806.py".

3) Open each "zte-k3806.py" file and in the code change each instance of "zte_k3805.py" to "zte-k3806.py".

4) You will also need to change the lines:

__properties__ = {
        'usb_device.vendor_id': [0x19d2],
        'usb_device.product_id': [0x1003],

to

__properties__ = {
        'usb_device.vendor_id': [0x19d2],
        'usb_device.product_id': [0x1015],

N.B. This device's product id appears (output of usb-devices command) as 1013 before ejecting manually (i.e. as a storage device), and 1015 after ejecting (when it is recognised as a mobile internet key).

5) Save and exit.

Vodafone mobile connect now works. Better from the command line (vodafone-mobile-connect-card-driver-for-linux) as sometimes it freezes when using the GUI.

I guess betavine-forge haven't got round to putting the plugin for this device in their package yet.

To the technosavvy, is there any way I can automate things so the vmc launch command gets executed when I start my computer or plug in my device? Probably not, as I'd still need to eject it manually first.

---

### Post by alexfish on 2011-02-09
hi
been through earlier post and seen above as regards ID's and the rules: IE re comments edit the rules according to the device

this device ZTE EJECT rule should be

```
SYSFS{idVendor}=="19d2", SYSFS{idProduct}=="1013", RUN+="/usr/bin/eject %k", OPTIONS+="last_rule"
```

It may help if can post version of VMC or BMC to which the device connects 

If all successful mark thread as solved 

It may help others

---

### Post by rdh61 on 2011-02-10
Thanks, the eject rule now works.

VMC version 2.25.01.

I'll mark this thread solved, but could you let me know if I can automate the command "vodafone-mobile-connect-card-driver-for-linux" with a script? I'd be very grateful.

---

### Post by rdh61 on 2011-03-01
I've had to mark this thread unsolved again. I have not used mobile broadand since my last message. This morning, when I tried to connect with Sakis3G (which we had got working, thanks to the advice received in this thread), no matter which of the 3 interfaces I chose (interfaces 1, 3 or 5 are offered), I persistently got the error essage that the port coudn't be liberated by modem manager. After trying and trying, I find now that my system does not mount my USB device at all (either as a storage drive or as a modem. And when I try to run Sakis3G, it freezes on "preparing modem". HELP!

---

### Post by alexfish on 2011-03-01
> **rdh61 said:**
> I've had to mark this thread unsolved again. I have not used mobile broadand since my last message. This morning, when I tried to connect with Sakis3G (which we had got working, thanks to the advice received in this thread), no matter which of the 3 interfaces I chose (interfaces 1, 3 or 5 are offered), I persistently got the error essage that the port coudn't be liberated by modem manager. After trying and trying, I find now that my system does not mount my USB device at all (either as a storage drive or as a modem. And when I try to run Sakis3G, it freezes on "preparing modem". HELP!
Hi rdh61

I have been on a Thread concerning a Vodafone K3085

 [SOLVED] [**Vodafone USB (K 3805-z)**]("http://ubuntuforums.org/showthread.php?t=1669429")

best read last page 2pages .. can suggest undoing everything VCM and install BCM ( for Ubuntu Versions 10 * )

readers note there are a few devices of ZTE which have a ICERA chipset
which will require  special init codes and a unique udev rule , these seem to available
in latest version of BCM

My advice to all users is this

if installing BCM, have available on your system a alternate means of dial up such as sakis3g and WVdial : think Latest version WVdial is a Dependency : please check after installation

Also suggest read most of the above thread as to why BCM may be required for these devices . 

see what happens ,

alexfish

ADDED: if successful, It may help others , to list how the install was done
also the mention Freeze situation seem to a problem with the wader core , but not sure if this after recent ubuntu update .. DID this occur after ubuntu update
, monitor what happens , the message may read , caused
by loop back on tty*: users should report this back to BCM , they now have a report back to paste bin : the developer site now looks good.
vast improvement , [B]YOUR input is needed if you want your devices and system working
[http://developer.vodafone.com/](http://developer.vodafone.com/)

ADDED { 3 march 2011} did further update 2/march/ Loop back tty* error ,, fixed
[/B]

---

### Post by rdh61 on 2011-03-02
Thanks for your reply. Unfortunately I have to leave this for a while. I'll be back in a month. In the meantime I'll look into the info you have provided. I'll give you feedback when I'm back.

---

### Post by rdh61 on 2011-04-05
@Alexfish,

Hi, I'm finally back to this and it is still proving something of a nightmare. I've followed your instructions at: [http://ubuntuforums.org/showthread.php?t=1669429&page=10](http://ubuntuforums.org/showthread.php?t=1669429&page=10)

In addition, I had to download and install usb-modeswitch-data_20100826-1betavine1_all.deb and python-gudev_147+20100209-0ubuntu2_i386.deb (for wader-core), as well as wmctrl_1.07-6_i386.deb (for bcm): somewhat difficult if you cannot connect...! Luckily I had another older computer running Karmic which connects with the same dongle without trouble with Sakis3g (ain't life strange), so I found and downloaded the packages on that before transferring them to the Lucid computer on a memory stick.

So, bcm successfully installed, but when I run it with the device connected and the blue light flashing, I get "No device". Any further help greatly appreciated.

---

### Post by rdh61 on 2011-04-06
Update:

Yesterday evening, just as I left it a month ago, I could not connect with Sakis3g. Either I was told that the port couldn't be liberated by modem manager. Other times the application would freeze on "preparing modem".

This morning, I tried again and it worked first time. Worked several times in a row. Then ran update manger, which among other things installed a new kernel (2.6.32-30), after which Sakis3g wouldn't connect (behaviour as before). I notice now that the system isn't even recognising my usb modem any more (doesn't appear on desktop or in Nautilus or in Disk Utility). 

Why so erratic?!!!

---

### Post by alexfish on 2011-04-06
hi
updates can effect udev rules (ie they can be overwritten upon update) depending on where placed

for now can look how it is seen by the system, post results of usb-device from the terminal
```
usb-devices
```also check the rules regarding the device,see if still exist, if missing , reinstate

see what happens

alexfish

ADDED:
had post saying it worked out of the box in natty , although Beta1 has just been released

Natty Narwhal
2011/03/31 Beta 1
2011/04/14 Beta 2 & Final Freeze
2011/04/28 Ubuntu 11.04
[Natty Narwhal Testing and Discussion]("http://ubuntuforums.org/forumdisplay.php?f=394")
may be worth testing : but all at own risk , post all back to "Natty Narwhal Testing and Discussion"

---

### Post by rdh61 on 2011-04-06
1) udev rules are as we left them (as per your advice), unaffected by recent updates.

2) This afternoon on plugging in device, it WAS recognised and appeared on desktop. (But Sakis3g just stalls on "preparing modem"). This erratic behaviour is just CRAZY.

3) BCM says "no device".

3) usb-devices:

robert@robert-laptop:~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.32-30-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=05 Cnt=01 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=02(commc) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=1015 Rev=00.01
S:  Manufacturer=Vodafone (ZTE)
S:  Product=K3806-Z
S:  SerialNumber=9546CD5893AC2522193F727B1EE3AC6FE825D298
C:  #Ifs=10 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 0 Cls=02(commc) Sub=08 Prot=00 Driver=option
I:  If#= 1 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=option
I:  If#= 3 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=option
I:  If#= 4 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=option
I:  If#= 5 Alt= 0 #EPs= 1 Cls=02(commc) Sub=06 Prot=00 Driver=option
I:  If#= 6 Alt= 0 #EPs= 0 Cls=0a(data ) Sub=00 Prot=00 Driver=option
I:  If#= 7 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
/usr/bin/usb-devices: line 79: printf: 08: invalid octal number
I:  If#= 0 Alt= 0 #EPs= 0 Cls=02(commc) Sub=0b Prot=00 Driver=option
/usr/bin/usb-devices: line 79: printf: 09: invalid octal number
I:  If#= 0 Alt= 0 #EPs= 0 Cls=0a(data ) Sub=00 Prot=00 Driver=option

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-30-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-30-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-30-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
robert@robert-laptop:~$

---

### Post by alexfish on 2011-04-06
Hi

can try looking at usb_modeswitch

cat /etc/usb_modeswitch.d/19d2:1013

if the file exists then the possibility the rule for switching need to be disabled

look in the /lib/udev/rules.d/40-usb_modeswitch.rules

should find a line
```
ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="1013", RUN+="usb_modeswitch '%b/%k'"
```edit to look like 
```
#ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="1013", RUN+="usb_modeswitch '%b/%k'"
```possible that usb_modeswitch sending the device_id to the file option new_id , not what is required for this device, if still a problem will have to look further

ADDED:
need to see results of **usb-devices** before running Sakis3g : Reason Sakis3g may also be setting up option/new_id

alexfish

---

### Post by rdh61 on 2011-04-07
Hi,

1) The file 19d2: 1013 in /etc/usb_modeswitch.d contains only the following text:

# Vodafone (ZTE) K3806-Z
#
# Note:
#      This device has multiple USB profiles. Depending upon how it is flipped
#      from storage mode to modem mode determines its final PID and the packages
#      shown on its ISO CD image.

DefaultVendor= 0x19d2
DefaultProduct=0x1013

TargetVendor=  0x19d2
TargetProduct= 0x1015

MessageContent="5553424312345678000000000000061b000000020000000000000000000000"

NeedResponse=1

CheckSuccess=20

2) In the /lib/udev/rules.d/40-usb_modeswitch.rules the line
Code:
ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="1013", RUN+="usb_modeswitch '%b/%k'"
is enabled. I have not yet disabled it as suggested, because this morning Sakis3g connects.

The problem is one period it connects immediately, the next (without changing anything) it resolutely refuses.

3) BCM still not recognising the device.

4) The usb-devices results posted earlier were obtained before running Sakis3g.


I'm afraid to change anything now until the next time (probably this afternoon!) that Sakis3g doesn't work.

Why do you think BCM does not "see" the device? I'd like to use BCM as it might be more reliable than Sakis3g. I'm confused now by this off/on behaviour. What should I do?

Many thanks.

---

### Post by alexfish on 2011-04-10
Hi

wader-core (part of BCM ) , wader core replaces modem-manager , a network manger dependacy)

from the rules in wader core
> 
# Vodafone (ZTE) K3805-Z
ACTION=="add", SUBSYSTEM=="net", ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="1003", RUN="/sbin/ifconfig %k -arp"

# Vodafone (ZTE) K3806-Z
ACTION=="add", SUBSYSTEM=="net", ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="1015", RUN="/sbin/ifconfig %k -arp" the rules indicate this device could have a "ether type interface" , so I assumed it could or should have a cdc_ether interface (there again could be proved wrong)
+ a standard cdc-acm interface , this could be the reason for BCM not seeing the device as the option driver has loaded
had noticed in upstream info , for usb_modeswitch to use option driver

so need to find out if this particular device requires cdc_ether interface (faster than standard option) or the option driver

as regards the rules these can easily reinstated by removing the "#"

also from previous post you mention that the following rule worked
> SYSFS{idVendor}=="19d2", SYSFS{idProduct}=="1013", RUN+="/usr/bin/eject %k", OPTIONS+="last_rule"it is pointless having two eject rules for the same device

to find possible solution , disable usb_modeswitch rule

note any changes with the usb-devices command , 

also of note as regards BCM , BCM has necessary intit codes for this device

alexfish

---

### Post by rdh61 on 2011-04-14
Hi, 

I'll bear all this in mind. (At least as much as I understand: I didn't understand the bit about the different kinds of interface - a little too technical for me).

But for the moment I'm sitting tight. Since my last message Sakis3g has continued to connect for me without further problems. I had made no changes at all to make it come to life, so it's a mystery.

While this is working, I'll refrain from any tinkering and leave BMC for now.

Watch this space!

Thanks for all your help.

---

