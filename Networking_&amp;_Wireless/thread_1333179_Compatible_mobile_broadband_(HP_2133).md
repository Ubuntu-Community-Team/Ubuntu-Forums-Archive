---
title: "Compatible mobile broadband (HP 2133)"
date: 2009-11-21
forum: Networking &amp; Wireless
---

### Post by judith_sw on 2009-11-21
Hi,

Although I'm still looking for ways to enable my 3mobile internet dongle, all attempts so far have failed. Wired and wireless internet work great.

I live in the UK and have an HP 2133 running Ubuntu 9.10. Does anyone know of a mobile broadband dongle that is compatible and easy to set up with my combination? I'm thinking it may be easier if Ijust go out and get another one. I bit of cost, but it need the connection.

Thank you! :P

---

### Post by alexfish on 2009-11-21
> **judith_sw said:**
> Hi,

Although I'm still looking for ways to enable my 3mobile internet dongle, all attempts so far have failed. Wired and wireless internet work great.

I live in the UK and have an HP 2133 running Ubuntu 9.10. Does anyone know of a mobile broadband dongle that is compatible and easy to set up with my combination? I'm thinking it may be easier if Ijust go out and get another one. I bit of cost, but it need the connection.

Thank you! :P

 there can be problems getting connected in the the version 9.10
   search the site mobile broardband "type of device"  

   look here it may help you decide

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

  worth reading

---

### Post by John Bean on 2009-11-21
I'm using a HP 6735s on mobile broadband and although I decided to stay with Jaunty (for now) I have run extensive tests with Karmic. I've read many reports of dongles not working in Karmic but the one I use - a Vodafone branded Huawei K3565 - actually works better with Karmic than it does with Jaunty, allowing use of all features like the micro SD card slot and even recognises the built-in "CD" drive which is invisible in Jaunty. Setup is automatic and everything works faultlessly.

Incidentally I'm currently using it on O2 - I unlocked it from Vodafone - and in my experience both Vodafone and O2 are far better and more reliable networks than 3 which I used for a time when they were the only PAYG mobile broadband operator available. Now that everyone and his dog offers PAYG, I wouldn't use 3 unless there's no other choice because of coverage issues.

Edit:

PS: The reason I use both Vodafone and O2 is down to pricing; Vodafone is expensive - £15 for only 1GB - but has no time limit so is ideal for low-volume sfuff like web-browsing and email. O2 on the other hand offers £2/day/500MB, £7.50/week/1GB or £15/month/3GB making it more useful and very flexible for bigger, one-off downloads.

---

### Post by judith_sw on 2009-11-21
Thanks for the advice. The Vodaphone deal sounds promising ... on the website it doesn't say which model is used, but I'll brave the weather and have a look in the local shop.

I presume it'll be OK with the HP 2133? I know it's impossible to tell, but any "real life" stories are always reassuring.

---

### Post by John Bean on 2009-11-21
> **judith_sw said:**
> I presume it'll be OK with the HP 2133? I know it's impossible to tell, but any "real life" stories are always reassuring.
I doubt it's sensitive to the exact model, but they have a return policy if it doesn't work for you. However, if I were you I'd avoid the whole "only works on Windows or OSX" argument by not telling them you're using Linux - even though Vodafone actually have Linux software available (you don't need or want it though).

Incidentally I just tried my old "soap on a rope" E220 dongle (on 3) and although it still works in Jaunty it doesn't work in Karmic. The newer Vodafone K3565 works in both along with anything else I've ever used it with.

---

### Post by judith_sw on 2009-11-21
Thanks for that. 

I've braved the wet and got the Vodaphone dongle from Tesco - it comes with 1GB preloaded, making it reasonably good value.

Just one further question prior to installing it ... is there anything I need to do on Windows first (- which I can do on my main computer), like activate the SIM card, or can I put it straight into the netbook running Ubuntu?

Cheers!

---

### Post by John Bean on 2009-11-21
> **judith_sw said:**
> Thanks for that. 

I've braved the wet and got the Vodaphone dongle from Tesco - it comes with 1GB preloaded, making it reasonably good value.

Just one further question prior to installing it ... is there anything I need to do on Windows first (- which I can do on my main computer), like activate the SIM card, or can I put it straight into the netbook running Ubuntu?

If it's preloaded you should be fine; just plug it in, wait for it to acquire a signal then right-click the network icon and select "Edit connections". Make a new connection using the defaults provided for UK/Vodafone "Top up and Go" and that should be that.

If after connection you can't seem to connect to anything try [https://online.vodafone.co.uk/](https://online.vodafone.co.uk/) which should always work. From there you can set up an account to allow you to check balance and top up as needed - which might apply if the credit is supplied as a top-up voucher for example.

Having said that you could try it on your Windows PC first if you want, but make sure you don't already have the 3 stuff on there, it doesn't play nice with the Vodafone software. Once installed the Vodafone software does everything without needing to visit the website.

---

### Post by judith_sw on 2009-11-21
Hi,

I've managed to connect - the Vodaphone TopUp and Go is showing as connected in the top bar, and the dongle has its blue light on. This is much further than I ever got with my 3internet dongle.

However, I cannot connect to any internet pages ... "server not found". I'm wondering if there are any settings I need to tweak?

---

### Post by alexfish on 2009-11-21
> **judith_sw said:**
> Hi,

I've managed to connect - the Vodaphone TopUp and Go is showing as connected in the top bar, and the dongle has its blue light on. This is much further than I ever got with my 3internet dongle.

However, I cannot connect to any internet pages ... "server not found". I'm wondering if there are any settings I need to tweak?

try disconecting and reconnect / you may have to a few times

also safely remove any device showing on the desktop try the above first

---

### Post by judith_sw on 2009-11-21
Thanks - I'll try that now. I'll also turn off the wireless broadband that I have at home.

---

### Post by judith_sw on 2009-11-21
Hi John and Alexfish,

I am now sending this message from my netbook using wireless broadband ... it works!!! I've spent a week trying to get my 3internet one going, with no success.

Thanks a million for your time and help - now I know I can go truly mobile from now on!

:biggrin:

---

### Post by John Bean on 2009-11-21
Sometimes for whatever reason you get a "dead" connection with no working DNS. I got this a lot with 3, much better with Vodafone and rarely with O2. Disconnecting and reconnecting usually does the trick, especially at busy times on the network.

Edit: I posted this before I read the last message, so I guess it's redundant. Anyway, glad to have been of help :-)

---

### Post by stefcep on 2009-11-21
> **judith_sw said:**
> Hi,

I've managed to connect - the Vodaphone TopUp and Go is showing as connected in the top bar, and the dongle has its blue light on. This is much further than I ever got with my 3internet dongle.

However, I cannot connect to any internet pages ... "server not found". I'm wondering if there are any settings I need to tweak?

With my E220 modem I had the same error on 3's network and I did this which worked:

I had to RT click on the network applet in the title bar->Edit connections->Mobile broadband->three->edit->ipv 4 settings->DNS Server. Here I deleted the existing numbers in there and replaced them with 208.267.222.222, 208.67.220.220

---

### Post by halj32 on 2009-12-04
with the 3 network I use

3 Internet    

Number
*99#           

APN
3internet        

thats it works fine  ( I got that from Linux Mint the windows number doesnt work *99***1#)
had a bit of a problem for the modem to show in the network manager though...
this worke for me

rmmod usb_storage
rmmod option
rmmod usbserial
echo "sleeping for 2 seconds to let the drivers unload...." && sleep 2
modprobe option
echo "sleeping for 2 seconds to make usb_storage detect the storage device..."
&& sleep 2 && echo "done sleeping"
modprobe usb_storage

got that from a search
below are other options I tried fro searches
[ How to get a Huawei HSDPA USB modem working in a new install of Karmic ]


Open up places, Computer & if you see a virtual CD ROM & HUAWEI SD Storage (for the microSD card if your modem Has one

right mouse click on the Virtual CD ROM (you don't need it as there windows drivers) & select safety remove device)

then when the HUAWEI SD Storage device & the virtual CD ROM has Gone , close the computer browser box


open a terminal up

Applications , Accessory , Terminal

then copy & paste these following commands (there just to get your modem to be seen by network-manager)

sudo rmmod usb-storage

[enter your user password if asked for it] then can follow on with the rest without entering your user password

sudo modprobe -r option

sudo modprobe -r usbserial

sudo modprobe usbserial vendor=0x12d1 product=0x1001

or

sudo modprobe usbserial vendor=0x12d1 product=0x1003 [If the first code doesn't work]


Then lastly

sudo pppd ttyUSB0

& don't forget to close the terminal box when finished with it


[Dialer three]
Phone =3D *99***1#
Username =3D 
Password =3D 
Stupid Mode =3D 1
Dial Command =3D ATDT
Modem =3D /dev/ttyUSB2
Baud =3D 460800
Init2 =3D ATZ
Init3 =3D ATE0V1&D2&C1S0=3D0+IFC=3D2,2
ISDN =3D 0
Modem Type =3D Analog Modem
Init5 =3DAT+CGDCONT=3D1,"IP","three.co.uk";
Modem Type =3D USB Modem

sudo depmod -a
sudo modprobe wl
sudo iwlist scan


then when you goto Network-Manager & right mouse , click on edit connections, Mobile broadband, Add a connection , your modem will now be showing like it is in the screen shot

[[ UPDATE ]] Just been told, if it doesn't work the first time around, insert a MicroSD card in the modem before inserting into the machine ??? funny that,, but somebody said it worked for them that way, thought I would mention it, other wise I would be getting told off

And the screen shots to show the modem not working before I used the following commands & the modem working after.


P.S you have to do the following the first time you want to connect using the connection. After that you can disconnect & connect all you want, just make sure you don't reboot other wise you will have to repeat the above to get the connection working again

"" If you do pull the modem out & plug it back in, just go back into places, Computer & safety remove the virtual CD & the connection will show back up in Network-Manager ""

now you can surf to your hearts content

sorry It's taken a bit to post back but just got in

Big shout out & credit goes to dmwelsch for letting me know about the MicroSD card tip & unpluging the modem & pluging it back in , that you have to either reboot the system to get the modem working or safety remove the virtual drive & HUAWEI SD Storage


OK, first make sure it works. Unload the module and reload it with the Force Modem parameter:

Code:

sudo modprobe -r usb-storage
sudo modprobe usb-storage  swi_tru_install=3

You might try the "option_zero_cd=1" parameter as well if "swi_tru_install" doesn't work.

If this loads the modem properly, you can add this line to /etc/modules to make it load that way at boot.

usb-storage swi_tru_install=3

The /etc/modules file must be edited as root. You can use "gksudo gedit /etc/modules"

You could also use a file in /etc/modprobe.d. See "man modprobe.conf" for details.




I had that problem initially as well, and I wrote a 3 line script (that I named a rather rude word) to sort it:

Code:

 
sudo /sbin/rmmod usb-storage
sudo /sbin/modprobe usbserial vendor=0x12d1 product=0x1003        (maybe 1001)
sudo wvdial


.in terminal type..

PHP Code:
sudo apt-get update && sudo apt-get install udev-extras 
then hit enter... then type..

PHP Code:
echo 'SUBSYSTEM=="usb", SYSFS{idProduct}=="1446", SYSFS{idVendor}=="12d1", RUN+="/lib/udev/modem-modeswitch --vendor 0x12d1 --product 0x1446 --type option-zerocd"' | sudo tee  /etc/udev/rules.d/45-huawei1550.rules 
and that's it!..




rmmod usb_storage
rmmod option
rmmod usbserial
echo "sleeping for 2 seconds to let the drivers unload...." && sleep 2
modprobe option
echo "sleeping for 2 seconds to make usb_storage detect the storage device..."
&& sleep 2 && echo "done sleeping"
modprobe usb_storage


Hey guys,

i just bought a Reliance Netconnect HUawei EC 168C rotable USB Stick.

No need for any configuration or drivers on Ubuntu 9.04 Jaunty Jackalope.

Just plug it in.

"Preferences>Network Connections> Mobile Broadband" should detect "Auto Mobile Broadband CDMS connection"

select the connection to add phone number "#777" and you username/ password, both of which should be your 10 digit phone number.

that is all. choose the connection from notification area and enjoy.

in case it does not work. just try the following command on the terminal.

"sudo wvdialconf /etc/wvdial.conf" which will
detect the modem and install it for internet connection.

the process is much simpler than configuring the modem on windows.




Sabayon
May 09, 2009
O2 Huawei E169 USB modem Gentoo GNU/Linux

This post is for anyone having problems getting the O2-provided Huawei E169 USB modem to work under Linux. I&#65533;ll assumed you&#65533;ve searched elsewhere and have an idea of what is going on.

In my case, I had a Gentoo GNU/Linux desktop without internet access although I did have a Windows XP laptop to help me. The best thing to do is use the USB modem on the laptop, connect up your desktop by ethernet cable and share the Dial-up connection in order to download any packages you may need.

gentoo-sources-2.6.28 is a good enough kernel to get things to work.

emerge usbutils ppp wvdial

cd /usr/src/linux
sudo make menuconfig
(Refer to Gentoo handbook for full details of installing a new kernel.)

Device drivers --->
    Network device support --->
        <M> PPP (point-to-point protocol) support
        <M> PPP support for async serial ports 
    USB support --->
        <M> OHCI HCD support
        <M> USB Mass Storage support (provides usb-storage so it can be unloaded)
        <M> USB Serial Converter support (provides usbserial, very important)
            [*] USB Generic Serial Driver
            <M> USB driver for GSM and CDMA modems (provides 'option' module, v. important)

sudo make -j 3

---

### Post by sumedhamahajan on 2010-01-19
Hi, I am having the same Reliance connection with Huawei 168C modem n using it on 9.04. but it is not detecting the modem.. i have tried the command 
sudo wvdialconf /etc/wvdial.conf
but even dis isnt helping. please help me out as u have exactly the same combination

---

### Post by alexfish on 2010-01-19
> **sumedhamahajan said:**
> Hi, I am having the same Reliance connection with Huawei 168C modem n using it on 9.04. but it is not detecting the modem.. i have tried the command 
sudo wvdialconf /etc/wvdial.conf
but even dis isnt helping. please help me out as u have exactly the same combination

Hi

could you have a look here and see what think

[http://reliancewireless.wordpress.com/](http://reliancewireless.wordpress.com/)

---

