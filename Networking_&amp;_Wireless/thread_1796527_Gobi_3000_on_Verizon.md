---
title: "Gobi 3000 on Verizon"
date: 2011-07-03
forum: Networking &amp; Wireless
---

### Post by pinegreen on 2011-07-03
Hi,

I'm starting a new thread to keep gather info that people might have
on running Gobi 3000 modem with verizon. I think that nobody has
managed to do that, but maybe we can cobble something together.

Basic info:

Drivers for this modem can be found here:

[https://www.codeaurora.org/patches/quic/gobi/Gobi_Drivers/](https://www.codeaurora.org/patches/quic/gobi/Gobi_Drivers/)


These drives might need to have their USB id's changed. In my case, 
the 

lsusb command gives

Bus 002 Device 004: ID 1199:9013 Sierra Wireless, Inc. 

and so  I had changed the entries in GobiSerial.c and
GobiUSBNet.c

to 

```
 USB_DEVICE( 0x1199, 0x9013 ),

```

(just search for USB_DEVICE).

There are two drivers, because there are two ways of speaking to the
modem. In principle, you need just one of them, but at the moment none
work for me ... :) GobiSerial exposes the modem interface on
/dev/ttyUSB0 and GPS interface on /dev/ttyUSB1.  The GobiNet exposes a
network interface as usb0.

First however, you need to load in firmware in Windows. Just activate
your card and load the firmware.  The gobi_loader software doesn't
work, it is missing apps.mbn, so some things have changed from Gobi
2000. Make sure your card works under windows.

If firmware is loaded, the Network manager will recognize both
interfaces. It will see ubs0 as a ordinary network interface without
connection and /dev/USB0 as indeed a broadband modem, but it refuses to connect.

To check if modem interface works, download putty, open a serial
connection to /dev/ttyUSB0 and say

ATZ
AT

and the modem should say OK.

I've tried to set ut wvdial and it would't connect, see e.g this output:

```
--> Sending: ATZ
OK
--> Sending: AT Q0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
AT Q0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: ATE0V1
ATE0V1
OK
--> Sending: AT+CPIN?
+CPIN: READY
OK
--> Sending: AAT+CLCK="SC",2
+CLCK: 0
OK
--> Sending: AT+GCAP
+GCAP: +CIS707-A, CIS-856, CIS-856-A, CIS707,+MS, +ES, +DS, +FCL
OK
--> Sending: AT+CMEE=1
OK
--> Modem initialized.
--> Sending: atdt*99***3#
--> Waiting for carrier.
NO CARRIER


```

basically it hates any atdt command. What is really bad is that it really doesn't want the
at+cgdcont command. Even AT+CGDCONT=? doesn't work. 

I've tried sniffing what the Windows do, but they talk to the network
interface and the wireshark wouldn't sniff what the heck are they
doing.

Any ideas anyone?

---

### Post by pinegreen on 2011-07-04
I came up with a cunning plan to run device inside vmplayer (which allows USB devices to be handed to the guest OS) and then bridge it out to linux, but the main driver wouldn't start with error code 10. :(

---

### Post by alexfish on 2011-07-04
Hi don't know anything about this modem, however need to see the whole device > port mappings and the drivers.

can try these two commands
```
lsusb -t
```
or
```
usb-devices
```if usb-device work can post that info, also when posting ,locate the lines which indicate the device and post only those lines

---

### Post by pinegreen on 2011-07-04
Hi, 
I think the problem is not in drivers - the drivers are there. The problem is in establishing connection. For modem interface you need the correct AT incantation and for the network interface god knows what you need. :)

Anyway, here the the outputs of commands
```

root@basquiat: ~/howto # lsusb -t
...
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/3p, 480M
    |__ Port 1: Dev 2, If 0, Class=hub, Driver=hub/8p, 480M
        |__ Port 3: Dev 3, If 0, Class=vend., Driver=i2400m_usb, 480M
        |__ Port 4: Dev 4, If 0, Class=vend., Driver=GobiNet, 480M
        |__ Port 4: Dev 4, If 1, Class=vend., Driver=, 480M
        |__ Port 4: Dev 4, If 2, Class=vend., Driver=GobiSerial, 480M
        |__ Port 4: Dev 4, If 3, Class=vend., Driver=GobiSerial, 480M
...

```

Port 4 Dev 4:
If 0 is the network interface
If 1 is the monitor interface (there is only windows driver)
If 2 is the modem interface
If 3 is the GPS interface

Also

```

usb-devices 
....

T:  Bus=02 Lev=02 Prnt=02 Port=03 Cnt=02 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1199 ProdID=9013 Rev=00.02
S:  Manufacturer=Sierra Wireless Inc
S:  Product=Sierra Wireless MC8355 - Gobi 3000(TM) Module
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=GobiNet
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 2 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=GobiSerial
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=GobiSerial


```

---

### Post by alexfish on 2011-07-05
Hi
from the info the device seems to have configured
of inteterest is the i2400m_usb and the gobi net (the i2400m_usb is a modified wimax driver) from reading the info this part of the device can at times switch off , but not sure if these parts are the main connection to the cells. (as said don't Know the device)

since the device may require specific commands to either switch the different modes , if modem-manager is preprobing the device with wrong commands then suggest disabling or uninstalling modem manager , (I would do this in any case , with a new modem), at least you will have a modem set up at default, IE knowning modem-manager has not sent the device into hibernation. then try experimenting with  the commands.

can use two terminal to communicate with the device, how to can be found here

[How To : Mobile Broadband Connections [ Ubuntu 10.10 : 10.04 : 9.10 ]]("http://ubuntuforums.org/showthread.php?t=1466490")

also look for the link to sierra wireless ( at the site are some basic sierra wireless AT commands
have you search the net for sierra wireless AT commands
**[*Supported* AT Commands.book - *Sierra Wireless*]("http://www.sierrawireless.com/resources/documents/support/2130617_Supported_AT_Command_Reference-v2.4.pdf")**

[www.**sierrawireless.com/resources](www.**sierrawireless.com/resources)**/**documents**/**support**/2130617_**Support**ed...
File Format: PDF/Adobe Acrobat
want to consult the other *documents* available  in the AC8xx/. MC87xx Development Kit or on our Internet site at [www.*sierrawireless](www.*sierrawireless)*.com **...**

see what happens , esp if modem-manager is dissabled

Does the network interface show up , or have you tried bringing up the net interface
from what I am seeing  all parts of the device may work at full speed by using the net interface, and the appropriate commands, but at that end I can't help. but will follow this thread with interest,

regards

alexfish

---

### Post by pinegreen on 2011-07-05
I haven't done much progress. One thing to note is that that this modem has a carrier dependent firmware. It can act as a GSM (HS.. whatever) model or as a CDMA modem. This depends on which firmware is loaded. If I load AT&T firmware in windows, then linux sees it as GSM modem (but I can't check if it works), if I load verizon firmware, it appears as CDMA modem. 
The problem is that I did try all these AT initializaitons strings before, but the model wouldn't take AT+CGDCONT and wouldn't take any ATDT command, always saying NO CARRIER immediately. The network-manager is not interfering with this, I can freely talk to modem. But thanks for your help anyway...

---

### Post by alexfish on 2011-07-06
Hi

this is just a thought , looking through the code for the i2400_usb driver , seems to indicate the probing set up  may force the device into wimax mode , can possibly try removing the driver or blacklisting this driver , if fail can try the same with the net driver

see what happens

alexfish

---

### Post by xiq on 2011-07-25
Hi there,

I have a ThinkPad X220 with a Gobi 3000 3G modem.

```

$ lsusb | grep Sierra
Bus 002 Device 003: ID 1199:9013 Sierra Wireless, Inc. 

```I  used to have it working using a combination of gobi-loader and a  modified version of the kernel qcserial.ko (with my vendor and device id  included). But just recently this stopped working for me (maybe there was a kernel update), and then I  found this thread. Fortunately, the linked GobiSerial driver works for  me, just like my old modified kernel driver used to (without all of the hassle of grabbing the whole kernel tree to compile one little module).

Here is what I have done:

Firstly  I had to get the modem working with my provider in Windows. I'm using  Telstra in Australia. It took a while to find the system update that included the data for my provider. After this terrifying ordeal, I was able to reboot into my cozy Ubuntu partition.

Back  in Ubuntu, I (apt-get) installed gobi-loader. This loads the firmware onto the modem. This needed to be told about my  particular modem, so I added the vendor and device ID into  /lib/udev/rules.d/60-gobi.rules (yay, no recompilation necessary!)

The line I added looks like:
```

ATTRS{idVendor}=="1199", ATTRS{idProduct}=="9013", RUN+="gobi_loader $env{DEVNAME} /lib/firmware/gobi"

```Then I needed to compile GobiSerial. Like the original poster, I changed GobiSerial.c to know about my modem:
```

static struct usb_device_id GobiVIDPIDTable[] = 
{
   { USB_DEVICE( 0x1199, 0x9013 ) },   // Gobi 3000 QDL device
   { }                               // Terminating entry
};

```Compiling was a simple as running "make".

Once  GobiSerial was compiled, I needed to copy the firmware from the Windows  partition into the /lib/firmware/gobi directory where gobi_loader can find it. Now, there are a few  different firmwares to choose from, and I want to try them all and see which works best, so I wrote this little script which  can list the available firmwares, or copy a selected firmware from my Windows partiton, and then  load the GobiSerial driver. It also deals with the mess of killing off  anything which is talking to the modem, and reloading the driver. You  will probably need to do something very different, but here is my  script as a guide:

```

#!/bin/bash
# this is the partition where windows lives on my computer
WIN_DEVICE=/dev/sda2
GOBI_DEVICE=/dev/ttyUSB0
# this is the directory containing the firmwares on the windows partition.
# each firmware is in a subdirectory (on my machine the subdirectories are just numbers)
WIN_GOBI_DIR="Program Files (x86)/Sierra Wireless Inc/Gobi/Images/3000/Generic/"
if [ -n "$1" ] ; then
  mount_point=$(mktemp -d)
  mount $WIN_DEVICE $mount_point
  if [ "$1" = "-l" ] ; then
    pushd "$mount_point/$WIN_GOBI_DIR" >/dev/null
    # im only interested in the firmware dirs containing this file
    for i in */amss.mbn ; do
      echo -n "$(dirname $i) "
    done
    popd >/dev/null
    echo
    umount $mount_point && rm -r $mount_point
    exit
  else
    cp "$mount_point/$WIN_GOBI_DIR/$1/"* /lib/firmware/gobi
  fi
  umount $mount_point && rm -r $mount_point
fi
if [ -c $GOBI_DEVICE ] ; then
    echo "Gobi device $GOBI_DEVICE is present."
    pids=$(lsof -t /dev/ttyUSB0)
    if [ -n "$pids" ] ; then
        echo "Gobi device is being accessed by:"
        ps -o pid,args --no-headers $pids
        echo "Killing these processes."
        kill $pids
    fi
fi
if grep -q "^GobiSerial" /proc/modules ; then
    echo "GobiSerial module is already loaded."
    echo -n "Removing GobiSerial module..."
    if rmmod -w GobiSerial ; then
        echo "Success"
    else
        echo "Failed"
    fi 
fi
echo "Loading GobiSerial module"
insmod $(dirname $0)/GobiSerial/GobiSerial.ko

```So  if I run this script with -l it will list the possible firmware  directories. Then if I run it with one of the names, it will copy over  that firmware and reload the GobiSerial driver. If I run the script  with no arguments, it will just load (or reload, if it's already loaded)  the GobiSerial driver (using the last firmware I copied over).

By the way, the script assumes that GobiSerial is in a subdirectory just below it.

Eg:
```

$ sudo ./load.sh -l
1 3 6
$ sudo ./load.sh 1
Gobi device /dev/ttyUSB0 is present.
Gobi device is being accessed by:
 3045 /usr/sbin/modem-manager
 3266  /usr/sbin/pppd nodetach lock nodefaultroute ttyUSB0 noipdefault noauth  usepeerdns lcp-echo-failure 0 lcp-echo-interval 0 ipparam  /org/freedesktop/NetworkManager/P
Killing these processes.
GobiSerial module is already loaded.
Removing GobiSerial module...Success
Loading GobiSerial module

```Almost there... Once the module is loaded, you can set up your connection using the  Ubuntu Network manager. Under System -> Preferences -> Network Connections  -> Mobile Broadband -> Add -> Sierra Wireless MC8355 -> etc (hopefully Ubuntu knows about your provider).

Hope this has been helpful to someone, and hope it works for you!

Thanks,
pix

---

### Post by jasaseo on 2011-07-25
thank you for the explanation .. I really can learn from here

---

### Post by pinegreen on 2011-07-29
I've got it working under AT&T as well, the problem really seems to be Verizon firmware as it is unwilling to dial.

Xiq, I think your gobi_loader doesn't do anything - you must have firmware still from windows.  If you look at gobi_loader source it loads three files,
amms.mbn, apps.mbn and UQCN.mbn. 

The second one is missing. I've contacted the author of gobi_loader and he is of no help, he doesn't have the gobi 3000 to play with.

Incidentally, they released API for working with the network driver (i.e not the modem driver). I couldn't get it to work, though it is sort of reporting sensible things...

 [https://www.codeaurora.org/patches/quic/gobi/Gobi_API/](https://www.codeaurora.org/patches/quic/gobi/Gobi_API/)

---

### Post by pinegreen on 2011-07-30
I've been playing a bit more today. Not much, but:

*) Sprint firmware: CDMA MODEM, #777 is doing something, but it understandably won't connect given that I'm not a customer.

*) Verizon firmware: CDMA MODEM, #777 returns NO CARRIER immediately, so it is not even doing anything. However, ATDT#anything else returns ERROR, so it is recognizing the command. The interesting AT commands I've learned today:
```

ATI 

Manufacturer: Sierra Wireless Inc
Model: Sierra Wireless MC8355 - Gobi 3000(TM) Module
Revision: D3600-STSUVH-1576  1  [Nov 23 2010 16:00:00]
SVN: 02
ESN: 0x803296C3
+GCAP: +CIS707-A, CIS-856, CIS-856-A, CIS707,+MS, +ES, +DS, +FCL

AT&V
&C: 1; &D: 2; &E: 0; &F: 0; &S: 0; &K: 3; &W: 0; E: 1; L: 0; M: 0; Q: 0;
V: 1; X: 1; Z: 0; \Q: 3; \S: 0; \V: 0; O: 0; S0: 0; S3: 13; S4: 10;
S5: 8; S6: 2; S7: 50; S8: 2; S9: 6; S10: 14; S11: 95; S30: 0; S103: 1;
S104: 1; +FCLASS: 0; +ICF: 3,3; +IFC: 2,2; +IPR: 115200; +DR: 0;
+DS: 0,0,2048,6; +CFUN:; +CMEE: 2; +EB: 1,0,30; +EFCS: 1; +ER: 0;
+ESR: 1; +ETBM: 1,1,20; +MA: ; +MR: 0; +MS: ; +MV18R: 0; +MV18S: 0,0,0;
+CXT: 0; +CDR: 0; +CDS: 0,1,2048,6; +CFC: 0; +CFG: ""; +CQD: 10; +CRC: 0;
+CMUX: 1,1; +CRM: 2; +CTA: 0;  +ES: 3,0,2; +ILRR: 0; +CMGF: 1;
+CPMS: "ME","ME","ME"; +CNMI: 0,0,0,0,0; +CPIN: ,; +FAA: 0; +FAP: 0,0,0;
+FBO: 0; +FBU: 0; +FCQ: 1,0; +FCC: 0,1,0,0,0,0,0,0; +FCR: 0; +FCT: 1E;
+FEA: 0; +FFC: 0,0,0,0; +FHS: 0; +FIE: 0; +FIP: 0; +FIS: 0,1,0,0,0,0,0,0;
+FLI: ""; +FLO: 1; +FLP: 0; +FMS: 0; +FNR: 0,0,0,0; +FNS: ""; +FPA: "";
+FPI: ""; +FPP: 0; +FPR: 8; +FPS: 1; +FPW: ""; +FRQ: 0,0; +FRY: 0;
+FSA: ""; +FSP: 0; ^PREFMODE: 0; ^CPIN: ,

OK


```

I bet one of the above settings is wrong.


*) AT&T firmware: GSM modem: connects and work.

---

### Post by pinegreen on 2011-08-05
After some fiddling I discovered the following:

On windows, verizon EZ access or whatever gives you option to connect either via modem port or network port. When you select the former it indeeds work over modem port as COM5 is busy and you can sniff it with USB sniffer to see nice things like ATS0=0 and ATDT#777. The port wouldn't be sniffed with any serial sniffer though.

On windows, one can open putty to COM5 port and say

ATZ
ATDT#777

and get back 

CONNECT 3100000

This is on completely fresh reboot without EZ Access running.

On linux, open putty and typing the above two still gives NO CARRIER.

I'm not sure how this is possible, to be quite honest, I think some driver initialization must whisper something nice to the modem.

---

### Post by MSwal2846 on 2011-09-09
I've followed the directions of xiq and am receiving this error:

```
mes@mes-ThinkPad-X220:~/Myfiles/Downloads/Gobi/Serial$ sudo ./load.sh -l
1 3 6 
mes@mes-ThinkPad-X220:~/Myfiles/Downloads/Gobi/Serial$ sudo ./load.sh 1
Loading GobiSerial module
insmod: error inserting './GobiSerial/GobiSerial.ko': -1 Unknown symbol in module

```

I have the same metrics, I believe:

```
mes@mes-ThinkPad-X220:~/Myfiles/Downloads/Gobi/Serial$ lsusb | grep SierraBus 002 Device 003: ID 1199:9013 Sierra Wireless, Inc.
```

And I have the same location in Windows for the files and am able to successfully connect under Windows.

So what did I miss?

---

### Post by MSwal2846 on 2011-09-11
Ok, got it to work but I had to manually execute "sudo modprobe qcserial" to get the /dev/ttyUSB* created (which what was missing causing the module from loading - see my previous post).  I would have thought that qcserial would do this while booting.

By creating the ttyUSB's, I was able to successful execute "sudo ./load.sh -l" and "sudo ./load.sh 1" and then wait a minute or so for NetworkManager to spot the card.

Am I correct in thinking that qcserial should recognize the device, build the ttyUSB*'s, then execute the loaded modules to load the card so that NetworkManager should recognize it when I get fully booted up?

---

### Post by pinegreen on 2012-02-19
Just to update things:

Lates version of drivers fixes the problem. The modem seems to not have been powered up in the CDMA mode (or at least a line in changelog seems to suggest this).

---

### Post by xiq on 2012-04-05
> **pinegreen said:**
> 
Xiq, I think your gobi_loader doesn't do anything - you must have firmware still from windows.  If you look at gobi_loader source it loads three files,
amms.mbn, apps.mbn and UQCN.mbn. 


Hi Pinegreen,

I've been reinstalling my machine recently and found myself back at this post trying to find out what I did to get it working last time.

You are right, it seems that gobi_loader just fails because it doesn't have the apps.mbn file. I tried poking around for one, but then, after hearing that the firmware maybe be pre-loaded, I tried an ATI (like post #11) after a fresh boot, and it seems to be pre-loaded with the D3200-STSUGN-1575 firmware.

This seems to correlate with one of the UQCN files on my Windows partition, which has an internal name of 03-umts_gen-02304-008 (found by doing "strings uqcn.mbn | tail").

It is possible that this was loaded by the Windows driver and has since persisted over reboot?

Also, on 11.10, the included qcserial module seems to work fine (including recognising my device ID) and I don't need to use the GobiSerial code any more.

I did go on a bit of a derpy goose-chase because I had the SIM card in upside down and was using the wrong APN, but after sorting all that out, it "just works" for me.

pix

---

### Post by hyperion917 on 2012-04-17
Hi guys--I'm thinking of using the Gobi 3000 on an embedded Ubuntu platform (11.10) and was hoping for a little advice/info:

1) I haven't chosen a carrier yet.  My platform doesn't have a SIM card, can I still use AT&T with just the Gobi 3000?  Or do I need to add a SIM card reader too?

2) At the present moment, is one of the carriers (AT&T, Sprint, or VZW) notably easier to configure?

3) What kind of account do I need to purchase/provision from the carrier?  Just a data account?

I'm a bit of a noob here so any light you can shed on this would be super helpful.  My platform now only has WiFi but adding mobile broadband is really important to my project.  Thanks in advance!

-hyp

---

### Post by livewire98801 on 2012-05-08
I think I'm running into a NetworkManager problem.  I finally gave up on loading firmware and activating my Gobi3000 card in Ubuntu and put in the Win7 drive.  It updated programming and connected, so I came back to my beautiful Ubuntu 12.04 desktop and... fail.

Here's the interesting thing.  I installed gnome-ppp, and it will connect, but when I try to connect with NetworkManger, it fails and takes its time doing it.  

Can anyone tell me what I might be missing here?  Or where I can find better logs from NetworkManager that might give me some useful info?

I'm using the same settings on both.... dialing #777, user: [phonenum]@vzw3g.com pass: vzw


```
livewire@lwmobile3:~$ sudo gnome-ppp
WVCONF: /root/.wvdial.conf
GNOME PPP: Connecting...
GNOME PPP: STDERR: --> WvDial: Internet dialer version 1.61
GNOME PPP: STDERR: --> Cannot get information for serial port.
GNOME PPP: STDERR: --> Initializing modem.
GNOME PPP: STDERR: --> Sending: ATX3
GNOME PPP: STDERR: ATX3
GNOME PPP: STDERR: OK
GNOME PPP: STDERR: --> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
GNOME PPP: STDERR: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
GNOME PPP: STDERR: OK
GNOME PPP: STDERR: --> Modem initialized.
GNOME PPP: STDERR: --> Please enter password (or empty password to stop):
GNOME PPP: STDERR: --> Sending: ATM1L3DT#777
GNOME PPP: STDERR: --> Waiting for carrier.
GNOME PPP: STDERR: ATM1L3DT#777
GNOME PPP: STDERR: CONNECT 3100000
GNOME PPP: STDERR: --> Carrier detected.  Waiting for prompt.
GNOME PPP: STDERR: --> Don't know what to do!  Starting pppd and hoping for the best.
GNOME PPP: STDERR: --> Starting pppd at Tue May  8 18:50:16 2012
GNOME PPP: STDERR: --> Pid of pppd: 3743
GNOME PPP: STDERR: --> Using interface ppp0
GNOME PPP: STDERR: --> pppd: &#65533;[7f]

(gnome-ppp:3735): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed
GNOME PPP: STDERR: --> pppd: &#65533;[7f]

(gnome-ppp:3735): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed
GNOME PPP: STDERR: --> pppd: &#65533;[7f]

(gnome-ppp:3735): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed
GNOME PPP: STDERR: --> local  IP address 75.196.42.142
GNOME PPP: STDERR: --> pppd: &#65533;[7f]

(gnome-ppp:3735): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed
GNOME PPP: STDERR: --> remote IP address 66.174.201.132
GNOME PPP: STDERR: --> pppd: &#65533;[7f]

(gnome-ppp:3735): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed
GNOME PPP: STDERR: --> primary   DNS address 66.174.92.14
GNOME PPP: STDERR: --> pppd: &#65533;[7f]

(gnome-ppp:3735): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed
GNOME PPP: STDERR: --> secondary DNS address 69.78.235.35
GNOME PPP: STDERR: --> pppd: &#65533;[7f]

(gnome-ppp:3735): Gtk-CRITICAL **: gtk_text_buffer_emit_insert: assertion `g_utf8_validate (text, len, NULL)' failed


```





```
May  8 18:51:42 lwmobile3 NetworkManager[2461]: <info> Activation (ttyUSB1) starting connection 'Verizon'
May  8 18:51:42 lwmobile3 NetworkManager[2461]: <info> (ttyUSB1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May  8 18:51:42 lwmobile3 NetworkManager[2461]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) scheduled...
May  8 18:51:42 lwmobile3 NetworkManager[2461]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) started...
May  8 18:51:42 lwmobile3 NetworkManager[2461]: <info> (ttyUSB1): device state change: prepare -> need-auth (reason 'none') [40 60 0]
May  8 18:51:42 lwmobile3 NetworkManager[2461]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) complete.
May  8 18:51:42 lwmobile3 NetworkManager[2461]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) scheduled...
May  8 18:51:42 lwmobile3 NetworkManager[2461]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) started...
May  8 18:51:42 lwmobile3 NetworkManager[2461]: <info> (ttyUSB1): device state change: need-auth -> prepare (reason 'none') [60 40 0]
May  8 18:51:42 lwmobile3 NetworkManager[2461]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) complete.
May  8 18:52:43 lwmobile3 NetworkManager[2461]: <warn> CDMA connection failed: (32) No service
May  8 18:52:43 lwmobile3 NetworkManager[2461]: <info> (ttyUSB1): device state change: prepare -> failed (reason 'none') [40 120 0]
May  8 18:52:43 lwmobile3 NetworkManager[2461]: <warn> Activation (ttyUSB1) failed.
May  8 18:52:43 lwmobile3 NetworkManager[2461]: <info> (ttyUSB1): device state change: failed -> disconnected (reason 'none') [120 30 0]
May  8 18:52:43 lwmobile3 NetworkManager[2461]: <info> (ttyUSB1): deactivating device (reason 'none') [0]
May  8 18:52:43 lwmobile3 NetworkManager[2461]: nm_system_iface_flush_routes: assertion `ifindex > 0' failed
May  8 18:52:43 lwmobile3 NetworkManager[2461]: nm_system_iface_flush_addresses: assertion `ifindex > 0' failed
May  8 18:52:43 lwmobile3 NetworkManager[2461]: <info> Policy set 'lwhome' (wlan0) as default for IPv4 routing and DNS.
May  8 18:52:43 lwmobile3 NetworkManager[2461]: <info> Policy set 'lwhome' (wlan0) as default for IPv4 routing and DNS.

```

---

### Post by xiq on 2012-05-08
Hi livewire,

> **livewire98801 said:**
> 
Can anyone tell me what I might be missing here?  Or where I can find better logs from NetworkManager that might give me some useful info?


To get more logging information you can try adding "--log-level=DEBUG" to the "exec NetworkManager" line near the end of /etc/init/network-manager.conf then do "sudo service network-manager restart" or just reboot.

Also, a lot of the fine detail about the 3G connection is logged by ModemManager, and you can add the same "--log-level=DEBUG" option to its starting command in /etc/init/modemmanager.conf to increase its verbosity too. Restarting NetworkManager again should restart both.. I think.

Remember to double check things like the access point name. I was running in circles for a while before I spotted that the APN that the Ubuntu wizard had chosen for my carrier wasn't quite right.

pix

PS: there is probably a config file you can put that log-level into which would be cleaner, but hacking the init scripts is the first way I got working.

---

### Post by livewire98801 on 2012-05-08
> **xiq said:**
> Hi livewire,



To get more logging information you can try adding "--log-level=DEBUG" to the "exec NetworkManager" line near the end of /etc/init/network-manager.conf then do "sudo service network-manager restart" or just reboot.

Also, a lot of the fine detail about the 3G connection is logged by ModemManager, and you can add the same "--log-level=DEBUG" option to its starting command in /etc/init/modemmanager.conf to increase its verbosity too. Restarting NetworkManager again should restart both.. I think.

Remember to double check things like the access point name. I was running in circles for a while before I spotted that the APN that the Ubuntu wizard had chosen for my carrier wasn't quite right.

pix

PS: there is probably a config file you can put that log-level into which would be cleaner, but hacking the init scripts is the first way I got working.
Well, that made a lot of noise.  I reduced the loglevel to INFO, and it was a little cleaner, but I couldn't see anything that stood out either way.  I don't wanna post the whole thing here as it's really ... loud.  Maybe someone can tell me what to look for?  

I don't understand how it will connect with gnome-ppp (screws up my routing tables though), but not NetworkManager.

---

### Post by qobi on 2012-09-03
I have a Lenovo W530 that has a Gobi 3000. I'm running Debian Wheezy. I would much appreciate if someone could send me the following:

 1. the firmware for AT&T
     (or point me to where I might obtain it)
 2. an /etc/wvdial.conf file that works with AT&T
     or tell me the alternate to the command
     AT+CGDCONT=1,"IP","isp.cingular"
 3. I currently use AT&T but in case I switch to T-Mobile, Verizon, or Sprint,
     the firmware for the other carriers and /etc/wvdial.conf entries for the other
     carriers.
 4. Does the Gobi 3000 support LTE on Verizon, Sprint, or AT&T?

Thanks,
Jeff
[email]qobi@purdue.edu[/email]

---

