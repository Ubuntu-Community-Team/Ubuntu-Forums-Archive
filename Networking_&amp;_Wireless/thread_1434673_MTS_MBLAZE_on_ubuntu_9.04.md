---
title: "MTS MBLAZE on ubuntu 9.04"
date: 2010-03-20
forum: Networking &amp; Wireless
---

### Post by ravi00ei51 on 2010-03-20
Hi All,

          I got a new MTS MBLAZE mobile broadband usb device(mobile broadband provider in India). It works well on Windows. But I want it to work on ubuntu 9.04. I tried somethings given on few forums but nothing worked. If anyone have any idea please share it with me.

Thanks
-R/\\/I-

---

### Post by ramakant2k on 2010-08-19
Inserting the data card brings up the USB drive in the list of drives in menu-> Computer.

On ubantu 8.10:
1. Double clicked on CrossPlatformUI-V1.0.27-SSTL-i386-ubuntu.deb file in the USB drive.
2. It installed the crossplatform UI on the internet menu.
3. Restarted, inserted card, started the crossplatform UI from the internet menu.

I did the following on 10.04[One extra step is needed]
1.  Double clicked on CrossPlatformUI-V1.0.27-SSTL-i386-ubuntu.deb
2. It installed the crossplatform UI on the internet menu.n Ubantu 10.04:
1. Double clicked on CrossPlatformUI-V1.0.27-SSTL-i386-ubuntu.deb
2. It installed the crossplatform UI on the internet menu.
3. Then right clicked on ZTE cd rom. Clicked eject.
4. Shut down and start computer.
5. Inserted the data card and start the crossplatform UI from the internet menu.

I guess it should work on 8.04 too. I am using ZTE AC 2746 modem. We need the GUI for switching from the hybrid to broadband mode as well as activating the recharge coupons. Without the GUI, its not possible to activate a new recharge coupon.

---

### Post by sunsing2000@hotmail.com on 2010-10-15
[SIZE=4]well i got mine connected
i hav ubuntu 9.04

system>administrator>synaptic package manager[/SIZE] [SIZE=4]
open it
setting>repositories
new window opens
click to open third party software from top menu

click add[/SIZE] [SIZE=4]
copy and past this: 
[/SIZE] [SIZE=4]deb http://[mirrors.kernel.org/ubuntu]("http://mirrors.kernel.org/ubuntu/pool/universe/u/usb-modeswitch/usb-modeswitch_1.1.0-2_i386.deb") lucid main universe

click close
say yes to all
click reload
after loading from internet completes
click origis from left menu
look for 
[mirrors.kernel.org/ubuntu]("http://mirrors.kernel.org/ubuntu/pool/universe/u/usb-modeswitch/usb-modeswitch_1.1.0-2_i386.deb")
click it
find usb-modeswitch in left menu
add it by clicking to install
installation complete then ur ready t go

insert ur mblaze modem
open network connection
find in ur wireless device 
mobile cdma connection
edit it
put
no: #777
user name: internet@internet.mtsindia.in
password: mts
save it
n ur ready to go
[/SIZE]

---

