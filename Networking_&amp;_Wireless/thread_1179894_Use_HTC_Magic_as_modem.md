---
title: "Use HTC Magic as modem"
date: 2009-06-06
forum: Networking &amp; Wireless
---

### Post by greew on 2009-06-06
Hi,

I've just bought the new HTC Magic here in Denmark, but when I plug it into my Ubuntu, I don't get the option to use it as a 3G modem.

Phone info:
```
Model number: HTC Magic
Firmware version: 1.5
Kernel version 2.6.27-dd63d1eb u70000@Android-X01
Build number: 2.16.401.5 146733 CL#33743 release-keys
```

Computer: Ubuntu 9.04

When I plug the USB cable into the phone, the following shows up in dmesg:
```
[295900.736046] usb 2-1: new high speed USB device using ehci_hcd and address 9
[295900.888577] usb 2-1: configuration #1 chosen from 1 choice
[295900.909075] scsi9 : SCSI emulation for USB Mass Storage devices
[295900.909164] usb-storage: device found at 9
[295900.909165] usb-storage: waiting for device to settle before scanning
[295905.910220] usb-storage: device scan complete
[295905.912237] scsi 9:0:0:0: Direct-Access     HTC      Android Phone    0100 PQ: 0 ANSI: 2
[295905.918219] sd 9:0:0:0: [sdb] Attached SCSI removable disk
[295905.918286] sd 9:0:0:0: Attached scsi generic sg2 type 0

```

Does anyone have any experience with using an Android-powered HTC phone as modem for Ubuntu?

If you need any more info, please let me know :)

Best regards,
Jesper

---

### Post by Holmen on 2009-06-06
Same here (but in Sweden :P). I also would like to get my lovely mobile to work as a modem in Ubuntu.

---

### Post by mattiask on 2009-06-08
I too want it to work!

---

### Post by mgade on 2009-06-08
Have u tried connecting via Bluetooth?
It works great with HTC Diamond and Ubuntu.

---

### Post by EvilDoctorK on 2009-06-10
No luck on bluetooth for me anyway  (With the UK Vodafone version)

Unlike previous Nokia phones the HTC magic doesn't appear to have a "Dial Up Networking" channel available when you scan the bluetooth services avaiable (only seems to have Headset / Mic etc.)

So I don't know what to do to get it to work ...   with previous Nokia phones you had to set the rfcomm to the correct bluetooth channel and then it worked fairly easily - but this doens't seem to be possible with the Magic as I can't find the channel at all.

---

### Post by easymike on 2009-06-10
There is a program in the android software repository  called "tether Blu" which allows you to basically use your mobile phone as a wifi device over a bluetooth connection, unfortunately it doesn't let you use your cell network internet. Perhaps a program like this can be written, and probably will soon, considering the open source nature of android ;)

---

### Post by mattiask on 2009-06-10
Almost got it to work using a app called android-wifi-tether. But this app needs a rooted system so you will have to root. **Rooting will woid your warranty.**

I am working on a guide on how to root a HTC Magic in ubuntu. However depending on where you brought your device some files is different. Doing this wrong can seriously destroy the phone.

For those of you who are a bit familiar with swedish the beta-version of the guide can be found here. Please try it out and give feedback
[http://www.swedroid.se/forum/showthread.php?t=158](http://www.swedroid.se/forum/showthread.php?t=158)

When it have been tested I will translate it and publish it. For lots of information about rooting and such I strongly recomend [http://forum.xda-developers.com/](http://forum.xda-developers.com/)

---

### Post by Shwan.c on 2009-06-12
Hi 
Tha last Magic android kernel has no Iptabels /firewall, it will result in wifi teathering not working even if you have a rooted phone.
I have tested Azilink , NO NEED for root access ! 
[http://code.google.com/p/azilink/]("http://code.google.com/p/azilink/")

I have posted a swedish guide , it is easy and what you need to do can be found there and you can use google to translate it .
I will just post the terminal command here . 

Make sure usb debogging is on in the phone

download Android sdk or just adb from the link above
, then unzip it in some directory like below and 

```

sudo cp ~/android-sdk-linux_x86-1.5_r2/tools/adb /usr/bin/adb
sudo chmod a+x /usr/bin/adb

```

This step is not needed , do it just if adb cant see the device ; 
```

sudo gedit /etc/udev/rules.d/50-android.rules

```
paste this in , change username to you username in ubuntu 
```

SUBSYSTEM=="usb",SYSFS{idVendor}=="0bb4",ATTR{idProduct}=="0c02",SYMLINK+="android_adb",MODE="0666",OWNER="USERNAME"
SUBSYSTEM=="usb",SYSFS{idVendor}=="0bb4",ATTR{idProduct}=="0c01",SYMLINK+="android_fastboot",MODE="0666",OWNER="USERNAME"

```

```

sudo chmod a+x /etc/udev/rules.d/50-android.rules
sudo /etc/init.d/udev restart

```

connect the phone and don't mount, you should get this if you run 

```

adb devices
HT95xxxxxxxx	device

```
now 
```

sudo apt-get install network-manager-openvpn openvpn
sudo /etc/init.d/networking restart
sudo /etc/init.d/NetworkManager restart

```
use the phone to install this [http://lfx.org/azilink/azilink.apk](http://lfx.org/azilink/azilink.apk)
or just 
```

mkdir azilink
cd azilink
wget http://lfx.org/azilink/azilink.apk
adb install azilink.apk
wget http://azilink.googlecode.com/files/azilink.ovpn

```
make this file in the same directory 
```

sudo nano resolv.conf

```
 and paste this in it if you use Networkmanager
```

domain lan
search lan
nameserver 192.168.56.1

```

then start the app on the phone , make sure it is connected to the pc , and if you have fire wall open the portet used bellow 
```

adb forward tcp:41927 tcp:41927
sudo cp resolv.conf /etc/
sudo openvpn --config azilink.ovpn

```
now yo can have fun , to stop the connection use ctrl+c , yo ushould run this three  last lines every time you need to connect to the phone as modem

[http://www.swedroid.se/forum/showthread.php?t=196]("http://www.swedroid.se/forum/showthread.php?t=196")
[IMG]http://dl.getdropbox.com/u/185312/Screenshot.png[/IMG]

I have done another change to automate this let me post it later today .

---

### Post by andersg on 2009-06-30
Thanks a lot azirlink works perfect for me. Only I have one problem, it doesn't seem like I can use "knock" to open up ssh connection when I use my magic as my network connection. Do you have any idea about this ??

---

### Post by hotweiss on 2009-07-01
Thanks for the instructions they worked.  I noticed that the new Hero ROM has USB tethering enabled in the menu. Have you figured out how to use the Hero's built-in tethering?  I am hoping that tethering could be a plug-n-play event...

---

### Post by hotweiss on 2009-07-02
Is there no way to create an Azinet opvn profile for network manager?  This way all of the copying and pasting would be eliminated.

I get this error if I try to import the Azilink profile:

> The file 'azilink.ovpn' could not be read or does not contain recognized VPN connection information

Error: The file to import wasn't a valid OpenVPN client configuration..

---

### Post by Shwan.c on 2009-07-02
> **hotweiss said:**
> Is there no way to create an Azinet opvn profile for network manager?  This way all of the copying and pasting would be eliminated.

I get this error if I try to import the Azilink profile:

I will try to look on it, I think you need first to make a fake interface and then try it. problem is that azilink bypasses encryption. I will try to ask ubuntudevs list later.

---

### Post by Shwan.c on 2009-07-03
Well 
if you make this file and then let it make the work for you you are no more in need of running commands in terminal. 
you need to change the XXX to exact path to your files, you can make a smarter script , but I am a lazy and bad programmer for that . 
```

nano /home/XXX/resolv_azilink.conf
and paste :

domain lan
search lan
nameserver 192.168.56.1

now save it and then : 

sudo nano /usr/bin/azilink_vpn

and paste this, and change XXX to your patches : 

#! /bin/sh
/home/XXX/adb forward tcp:41927 tcp:41927
/etc/init.d/NetworkManager stop
cp /home/XXX/resolv_azilink.conf /etc/resolv.conf
openvpn --config /home/XXX/azilink.ovpn
/etc/init.d/NetworkManager start

then you can just run :
sudo azilink_vpn
and then you have you internet working to stop use ctrl+c

you can make a launcher as application in terminal and ask it to run the same command.


```

---

### Post by hotweiss on 2009-07-05
> **Shwan.c said:**
> Well 
if you make this file and then let it make the work for you you are no more in need of running commands in terminal. 
you need to change the XXX to exact path to your files, you can make a smarter script , but I am a lazy and bad programmer for that . 
```

nano /home/XXX/resolv_azilink.conf
and paste :

domain lan
search lan
nameserver 192.168.56.1

now save it and then : 

sudo nano /usr/bin/azilink_vpn

and paste this, and change XXX to your patches : 

#! /bin/sh
/home/XXX/adb forward tcp:41927 tcp:41927
/etc/init.d/NetworkManager stop
cp /home/XXX/resolv_azilink.conf /etc/resolv.conf
openvpn --config /home/XXX/azilink.ovpn
/etc/init.d/NetworkManager start

then you can just run :
sudo azilink_vpn
and then you have you internet working to stop use ctrl+c

you can make a launcher as application in terminal and ask it to run the same command.


```

Thanks, I will try it:)

---

### Post by hotweiss on 2009-07-05
> **Shwan.c said:**
> Well 
if you make this file and then let it make the work for you you are no more in need of running commands in terminal. 
you need to change the XXX to exact path to your files, you can make a smarter script , but I am a lazy and bad programmer for that . 
```

nano /home/XXX/resolv_azilink.conf
and paste :

domain lan
search lan
nameserver 192.168.56.1

now save it and then : 

sudo nano /usr/bin/azilink_vpn

and paste this, and change XXX to your patches : 

#! /bin/sh
/home/XXX/adb forward tcp:41927 tcp:41927
/etc/init.d/NetworkManager stop
cp /home/XXX/resolv_azilink.conf /etc/resolv.conf
openvpn --config /home/XXX/azilink.ovpn
/etc/init.d/NetworkManager start

then you can just run :
sudo azilink_vpn
and then you have you internet working to stop use ctrl+c

you can make a launcher as application in terminal and ask it to run the same command.


```

The only problem here is that adb has to be run as root.  How do you run an application as root in a shell script?

Edit: Nevermind, I just added echo "password" and it worked

---

### Post by hotweiss on 2009-07-05
> **hotweiss said:**
> The only problem here is that adb has to be run as root.  How do you run an application as root in a shell script?

Edit: Nevermind, I just added echo "password" and it worked

Actually here are the instructions that I used to get it working:

1) > sudo nano /home/name/azilink/resolv_azilink.conf

2) Paste the following:

> domain lan
search lan
nameserver 192.168.56.1

3) CTRL-O, then CTR-X

4) > sudo nano /usr/bin/azilink_vpn

5) Paste the following:

> #! /bin/sh
sudo /home/XXX/adb forward tcp:41927 tcp:41927
echo "password"
/etc/init.d/NetworkManager stop
cp /home/XXX/resolv_azilink.conf /etc/resolv.conf
openvpn --config /home/XXX/azilink.ovpn
/etc/init.d/NetworkManager start

Please note that you have to enter the correct path of where adb is, and enter you real password (keep quotation marks) after echo.

6) CTRL-O, then CTR-X

7) > chmod +x /usr/bin/azilink_vpn


Thank-you Shawn.c.

---

### Post by szandor on 2009-08-04
perfect. your udev lines got me going. this is working on the new t-mobile mytouch.

-t-mobile mytouch
-dell mini 9
-ubuntu 9.04 (2.6.28-14)
-eclipse 3.4 (ganymede)
-android sdk 1.5 r3
-adt 0.9
-network-manager-openvpn 0.7.1~rc4
-openvpn 2.1~rc11
-azilink 2.0.2

---

### Post by mlaverdiere on 2009-08-06
I would also be interested to have network-manager deal with the ovpn connexion with HTC/Android/Azilink...  I'm pretty sure that it's just a mather of taking the content of the azilink.ovpn file and puting it at the right place in the network-manager vpn config dialog box...

Someone knows how to do it?

---

### Post by kingcharles1666 on 2009-08-08
> **hotweiss said:**
> Thanks for the instructions they worked.  I noticed that the new Hero ROM has USB tethering enabled in the menu. Have you figured out how to use the Hero's built-in tethering?  I am hoping that tethering could be a plug-n-play event...

I am typing this on a Ubuntu Hardy 64 bit machine with the HTC Hero for the internet access.
If you connect the USB cable and enable the internet sharing in the wireless settings menu of the Hero you will find a "unknown usb communications interface" in network manager of your ubuntu desktop.
If you select that it will connect and voila.
Plug and play :-) (for once...)

---

### Post by Shwan.c on 2009-08-11
> **kingcharles1666 said:**
> I am typing this on a Ubuntu Hardy 64 bit machine with the HTC Hero for the internet access.
If you connect the USB cable and enable the internet sharing in the wireless settings menu of the Hero you will find a "unknown usb communications interface" in network manager of your ubuntu desktop.
If you select that it will connect and voila.
Plug and play :-) (for once...)

We use Hero rom on magic and then The old Magic kernel ... so it will not work for us Plug and PLay , waitng for HTC to release source code first , until they do so , azilink is good .

we can't use networkmanager-openvpn because the encryption is off using azilink.

---

### Post by GoodPanos on 2009-09-23
Wow this is a little hidden treasure. :KS Great post!  Thank you Shawn.c. and hotweiss.  I was thinking of rooting my phone but I think I'll wait now.

---

### Post by Pioden on 2010-01-11
Any update on this situation? I have a HTC Magic and would like to be able to use it as a 3G modem occasionally - but I'd really prefer not to root the phone :-) !!

---

### Post by GoodPanos on 2010-01-28
Yes, read the thread.  It explains it all :)

However, is there way to do this with bluetooth?

---

### Post by mack-fu on 2010-02-15
Hi,

You can achieve tethering without rooting your phone. All the information is here in this topic but to summarise:

1) Download the Azilink zip and apk from [here ]("http://code.google.com/p/azilink/")

2) Download the Android SDK from [here ]("http://developer.android.com/sdk/index.html")

3) Download Open VPN using:```
 sudo apt-get install openvpn
```

4) Install azilink onto your Magic following the instructions [here]("http://code.google.com/p/azilink/")

5) Follow the instructions in post #16 in this topic to configure azilink on the ubuntu side

6) Run the Azilink application on the magic

7) Run /usr/bin/azilink_vpn on the ubuntu side

8) Connected!

I got this working over the weekend with Ubuntu 9.10 and HTC Magic on a Vodafone UK contract.

Mark

---

### Post by meatball on 2010-03-10
Excellent! 

Working on Ubuntu 9.10 with an unrooted HTC Eris Verzon US.

Thanks to everyone who contributed to this thread.

---

### Post by orzechowskid on 2010-05-27
Verizon Droid Eris, adb binary from the Android 2.1 SDK, and Azilink 2.0.2 (downloaded 2.0.2 .zip file, but the About screen on the phone says 2.0.1) here.

I can run the azilink_vpn script created upthread, but can only browse to one or maybe two websites before things stop working.  The terminal running azilink_vpn doesn't show any unusual output, and the app on the phone says "connected to host", but the byte counters are not changing.  Playing with the advanced settings doesn't seem to do anything.  Anyone else see this or have any idea what's going on?

thanks

---

