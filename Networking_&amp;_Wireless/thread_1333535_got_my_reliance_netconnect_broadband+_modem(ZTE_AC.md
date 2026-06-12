---
title: "got my reliance netconnect broadband+ modem(ZTE AC8710) working in ubuntu 9.10!!!"
date: 2009-11-21
forum: Networking &amp; Wireless
---

### Post by drbsjtmndl on 2009-11-21
got my reliance netconnect broadband+ modem(ZTE AC8710) working in ubuntu 9.10!!! 
 
 
1. connect your modem. after a while it shows up as a cd rom drive and you'll see the desktop icon. 
   now open terminal and give the command "lsusb". a list will come up showing all the connected devices. 
   find something like this "Bus 004 Device 003: ID 19d2:fff6". here fff6 is the device id. all we have to  do is to change it from fff6 to fff1. for this we need a package called "usb_modeswitch". 
 
2. [http://www.draisberghof.de/usb_modeswitch/usb_modeswitch-1.0.5.tar.bz2](http://www.draisberghof.de/usb_modeswitch/usb_modeswitch-1.0.5.tar.bz2) 
   this is the link to download. get it anyhow(by using windows or using mobile broadband or from another  computer).then extract it in a directory accessible by linux. 
3. now open terminal and get root privilage.(to do this type "sudo su" and press enter. you will be prompted for password.  type it. it will be invisible, but don't worry. just type and press enter. you should see the command  line ending with #. that means you got the privilage.) 
4. now go to the directory in which you extracted the usb_modeswitch from terminal with root privilage. 
5. give the command "make". 
6. then give the command "make install". 
7. the package will be installed.
8. now a file will be created naming "usb_modeswitch.conf" in the directory "/etc". now you have to edit this file with root privilage.
9. to do this give the command in terminal "sudo gedit /etc/usb_modeswitch.conf"
10.this file will be opened in gedit text editor. now scroll below and find your device. it will be displayed like this:
    
    # ZTE MF622 (aka "Onda MDC502HS")
    #
    # Contributor: andylog

    ;DefaultVendor=  0x19d2
    ;DefaultProduct= 0x2000

    ;TargetVendor=   0x19d2
    ;TargetProduct=  0x0002

    # only for reference and 0.x versions
    # MessageEndpoint=0x04

   ;MessageContent="55534243f8f993882000000080000a85010101180101010101000000000000"

11.find your device and delete the semicolon signs of lines starting with ";"(simply unquote). it should look like this:

   # ZTE MF622 (aka "Onda MDC502HS")
   #
   # Contributor: andylog

   DefaultVendor=  0x19d2
   DefaultProduct= 0x2000

   TargetVendor=   0x19d2
   TargetProduct=  0x0002

   # only for reference and 0.x versions
   # MessageEndpoint=0x04

   MessageContent="55534243f8f993882000000080000a85010101180101010101000000000000"
12.save the file.
13.give the command "usb_modeswitch" with root privilage.
14.after the execution give command "lsusb". you will see that the device id has been changed from "fff6"
   to "fff1".
15.the 1st stage is complete. now Give parameters to kernel for identification of the modem. to do this
   give the command "modprobe usbserial vendor=<vendor id> product=<product id>" (just type the target vendor id and target product id from usb_modeswitch)
16.you must have "libusb" installed.if not then get a temp net connection and run "sudo apt-get install libusb-dev" with root privilage.if u face any problem then update packeges and try again.now use wvdialconf to configure internet.to do this you have to install the package named "wvdial"
   you can try downloading from another computer but i tried and failed. so i used my mobile to get the net connection in my linux and gave the command in terminal "sudo apt-get install wvdial". the package will be installed. a file named "wvdial.conf" will be created in "/etc".
17.to activate give command "wvdialconf /etc/wvdial.conf".
18.now you have to edit the file "wvdial.conf". to do this give command "sudo gedit /etc/wvdial.conf"
19.when the file opens in gedit Enter the following Details.
20.Phone=#777
   username=<phone number>
   password=<phone number>
   and don't forget to delete the semicolons of the above lines.
21.now you are done. run the command "wvdial" in terminal with root privilage. your internet connection will be established.
   (N.B.-the network icon will not show any active connection. but that will be no problem.)

please inform me if it helped u. good luck!!!

---

### Post by friendlyboy777 on 2009-11-25
Hi,

Iam unable to connect to net through Reliance netconnect ZTE, it's not detecting, other connections were easily detected, can anyone help me? Fast?

Regards.

---

### Post by amitauti on 2009-12-30
it works!!! But please mention proper ways to install wvdial to get it started. 

Got many problems while installing this!

But Thanks very much! :)

---

### Post by pku on 2010-05-22
Can someone let me know the procedure using Network Manager in 10.04.
Network Manager was able to detect  but could not connect.

I have Huawei EC1262 modem.

thanks

---

### Post by alexfish on 2010-05-22
> **pku said:**
> Can someone let me know the procedure using Network Manager in 10.04.
Network Manager was able to detect  but could not connect.

I have Huawei EC1262 modem.

thanks

  	 	 	 	 	 	  Hi  
 

 your device  is not relevant to device title of the thread IE : the thread is for a **zte** , your device is **Huawei EC1262**
 

 advise to start new thread  at
 

 [Networking & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336")
 

 look at the top left of the page , find button New Thread
 

 

 then possibly use the title  
 

 **Huawei EC1262 modem not recognised Ubuntu 10.04**
 

 
try to give as much info as possible 

regards

alexfish

---

