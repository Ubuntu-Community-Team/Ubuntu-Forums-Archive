---
title: "Reliance Netconnect in Ubuntu 10.04"
date: 2010-05-20
forum: Networking &amp; Wireless
---

### Post by 14quartz on 2010-05-20
Hi,

I am using Reliance Netconnect(**ZTE AC 8710 **) I had used this in Ubuntu 9.10 and 9.04 successfully(Thou it is not so easy). I have not switched to 10.04(Lucid Lynx) yet. So i want to know whether Ubuntu 10.04 supports Netconnect?.

Even though I used Netconnect in ubuntu 9.10 and 9.04 I don't how to change the speed ie. between broadband,hybrid & 1x. For changing the speed i had to go to windows(friend's System) and use the software given by them and change the speed. Is there any way to change it from Ubuntu.

Thanks in Advance.

---

### Post by pdc on 2010-05-20
> **So i want to know whether Ubuntu 10.04 supports Netconnect?**.

safest way is to download the .iso; 

use Ubuntu's disk creator utility and burn the .iso to a USB disk

I was pleasantly surprised how well 10.04 has worked on usb modems: ZTE MF636; Huawei E220 and ZTE K3565 all good; 

but try the iso

---

### Post by 14quartz on 2010-05-20
> **pdc said:**
> 
I was pleasantly surprised how well 10.04 has worked on usb modems: ZTE MF636; Huawei E220 and ZTE K3565 all good; 
but try the iso


Are you sure 10.04 works well with USB Modems?

---

### Post by noren on 2010-05-20
any ideas how to configure the onboard 3g modem i am using olive zipbook with an inbuilt 3g modem... 

i am trying the live cd 10.04 on usb as of now.. i cant get the connection done with ubuntu.. but it works well in windows

---

### Post by pku on 2010-05-22
I was trying to configure Reliance NetConnect "Huawei EC1262" Modem.
Network Manager detected the modem but, after configuring it is not able to connect it.

Can anyone help me out?

---

### Post by pku on 2010-05-23
I got it working...
Just downloaded usb-modeswitch-data and usb-modeswitch from some other machine and installed in ubuntu 10.04... 

working out of the box!

---

### Post by CoolApputty on 2010-06-08
I have been searching for the same...
please let me know if anybody has figured it out.
i had used it in 9.04 changing the menu.lst, but in 10.04 i am not sure what to do..

---

### Post by pratheep on 2010-07-23
Hi,
 
I configured reliance EC1260 on 10.04, if any 1 still facing problem pls let me/forum know,
 
[EMAIL="pratheepseenu@yahoo.co.in"]pratheepseenu@yahoo.co.in[/EMAIL]
 
fyi, download speed in 10.04 is fast(250+)  than i got in win7(100+)
 
Regards,
PS.

---

### Post by amarjeet on 2010-08-03
hi 
i am new to ubuntu.
i have downloaded and install ubuntu 10.04 on my laptop.
can anybody help me step by step to install reliance netconnect (Huawei EC168c) on ubuntu 10.04 in simple way.
i have search on google  and found , it can be installed "using usb-modeswitch-data and usb-modeswitch " but how it can be achieved?
 
Thanks in advance.............

---

### Post by fullmoon13 on 2010-08-03
go to this link
[http://packages.ubuntu.com/lucid/allpackages](http://packages.ubuntu.com/lucid/allpackages)
 then search for usb-modeswitch-data and usb-modeswitch
download them and that is it.
( I downloaded them but didn't use any modem yet, i'll do soon when Allah wish)

I hope it will work.:p

---

### Post by Kbipinkumar on 2010-08-07
there is a bug in the modem manager package shipped in lucid. distros such as fedora 13 that comes with a newer version are capable of connecting to net using 3G usb modems like EC1260

  for ubuntu one will have to install these packages from a ppa. execute the following commands from the terminal first

(**a word caution the packages in this ppa may contain bugs. use at your own risk. however it works for me without any problem**)
        
  1. ** sudo add-apt-repository [B]ppa:network-manager/trunk**[/B]
    
  2.  **sudo aptitude update**
   
  
close the terminal

now go to** System > Adminstration > Synaptic package manager**

in the quick search box type "**modemmanage**r"   to locate the package. it will have a star icon to the left the name indicating a newer  version is available. left click and select the option " Mark for upgrade". this will prompt you for upgrading other packages as well to meet the dependecies click ok to accept it. similarly mark install/upgrade for the package "**usb-modeswitch**" and "**usb-modewsitch-data**" as well.

now click "**Apply**" to perform the actual upgrades. once its complete, restart your system, plugin your modem configure your connection and you are good to go

gud luck

---

### Post by yndesai on 2010-08-31
> **pratheep said:**
> Hi,
 
I configured reliance EC1260 on 10.04, if any 1 still facing problem pls let me/forum know,
 
[EMAIL="pratheepseenu@yahoo.co.in"]pratheepseenu@yahoo.co.in[/EMAIL]
 
fyi, download speed in 10.04 is fast(250+)  than i got in win7(100+)
 
Regards,
PS.

I am having Reliance EC1260 : It is working fine on 9.04 but not on 10.04, the modem gets detected as CD ROM and I am trying with the usbmodeswitch but not having any sucess. 

PLEASE HELP

---

### Post by raunhar on 2010-10-23
I am having Reliance Netconnect ZTE AC-2736 device.
Under windows it works just fine. But when connected to Ubuntu 10.04, it just tries to connect, but is unable to.
The CrossplatformUI that came on the Cd is also not installing.
I tried using The Dialler for ZTE-2726/8710 from the reliance website, but it also does not help.

usb-modeswitch-dat conf is empty.
lsusb shows the device as 19d2:fff1 Onda

Pl. suggest

---

### Post by gobindaghosh on 2011-03-01
> **fullmoon13 said:**
> go to this link
[http://packages.ubuntu.com/lucid/allpackages](http://packages.ubuntu.com/lucid/allpackages)
 then search for usb-modeswitch-data and usb-modeswitch
download them and that is it.
( I downloaded them but didn't use any modem yet, i'll do soon when Allah wish)

I hope it will work.:p

You are right dude. After that configure wireless broadband from Network Connection... Give dial number, user id and pass... Make the connection Available to all users. 
When  everything is done, it takes few seconds to load  the Reliance Netconnect connection name to appear  in the network connection list in the top panel of the desktop. Click Connect and Done.

---

### Post by rrameshreddy on 2011-09-08
hi 
i am new to ubuntu.
i have downloaded and install ubuntu 11.04 on my laptop.
can anybody help me step by step to install reliance netconnect (Huawei EC150) on ubuntu 11.04 in simple way.
i have search on google and found , it can be installed "using usb-modeswitch-data and usb-modeswitch " but how it can be achieved?

Thanks in advance.............

---

### Post by raunhar on 2011-09-08
If you are using 11.04 I believe, there should be no problem.
After plugging in the device into USB, did you go to Network Connections-->Mobile Broadband. There the device should show up.

If it is not showing, go to Terminal, type lsusb. There the device should be showing. In no, then check the USB port

---

### Post by rrameshreddy on 2011-09-08
I did that but I am not able to find the device in the Network Connections-->Mobile Broadband.

after that I did the lsusb in Terminal I am able to see the device.

But it's not connected.

---

### Post by raunhar on 2011-09-08
Go to Synaptic Manager (under system settings).
Search for these two packages, through the Search Box.
select them, and click on Mark for installation. You will require Internet to install these files.

Click on Apply. It will install the files. then the device should work.

---

### Post by raunhar on 2011-10-21
Enabled the 3g Hotspot and it was done.
Another way was enabled USB Tethering and the laptop showed Connected to Wired Netwrok.

---

