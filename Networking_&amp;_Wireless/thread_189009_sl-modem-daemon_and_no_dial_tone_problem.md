---
title: "sl-modem-daemon and no dial tone problem"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by habib_seif on 2006-06-04
Hi dear friends,
I have an intel modem witch is recognized by dialer programs like wvdial in dapper. the only package I installed is sl-modem-daemon and /dev/modem was created automatically.
But my problem is that dialer programs complains there is no dial tone in dialing ISPs. I checked the wire and it worked with another modem.
By the way, after surfing the web, I figured out that it may be because of a bug in dapper([https://launchpad.net/distros/ubuntu/+source/sl-modem/+bug/31640)](https://launchpad.net/distros/ubuntu/+source/sl-modem/+bug/31640)), A solution has been introduces in [https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto) or some threads in the forum, but first, it seems so confusing and second it references to some locations that no file is there!!! for example, it says I have to download slmodem-2.9.11-20051101.tar.gz from [http://phep2.technion.ac.il/linmodems/packages/smartlink/](http://phep2.technion.ac.il/linmodems/packages/smartlink/) but nothing is there :-(
Do any of you have experience in installing smartlink drivers?
Cheers,
Habib

---

### Post by Killjoy23 on 2006-06-06
I don't have an intel modem like the one you've got anymore, but I had the same problem. I have the packages you mentioned, that particualr driver is actually the only one i've managed to get working on any distro at all. I put a direct link to the file at the bottom of the post. 

Slmodem driver package:

[http://linmodems.technion.ac.il/packages/smartlink/slmodem-2.9.11-20051101.tar.gz](http://linmodems.technion.ac.il/packages/smartlink/slmodem-2.9.11-20051101.tar.gz)

I need to have access to my desktop system to be of further help, I wrote down how I got it working just in case I had to reinstall(my memory isn't that great). I will edit this to be a bit more useful when I get home..

Jas

EDIT: you may also need the following file...

Ungrab-winmodem:

[http://phep2.technion.ac.il/linmodems/packages/ungrab-winmodem.tar.gz](http://phep2.technion.ac.il/linmodems/packages/ungrab-winmodem.tar.gz)

---

### Post by Killjoy23 on 2006-06-06
Edit...again....this was a double post, but I can't friggen delete it for some wierd reason.

---

### Post by habib_seif on 2006-06-06
Thanks for the reply...
but another question:
My modem id is 8086:266d. Is it intel? One of the people in linmodems.org and scanModem tool too say that the modem is intel but the codecs of it is from Conexant and because of that sl-modem-daemon doesn't work for this modem and the only choice for me is linuxant non-free drivers :-(
Do you have any experience in area?
yet another question:
what's the job of ungrab-winmodem?
Cheers,
Habib

---

### Post by Matchless on 2006-06-06
Habib,
            I have posted a new howto but still awaiting moderater release. In the meantime here is a guide;
[U]Howto get Conexant HSF modem to work in Dapper Kubuntu
[/U]
Conexant modems can mostly be made to work in linux by using older drivers that were open source and thus free. Do not laugh, but presently Conexant drivers are free for Windows, but have to be purchased seperately at about $15 for free linux! These purchased drivers are said to be free, but the free version only supports speeds up to14400 and if you want maximum 56k you have to pay. Below you will find two different methods for installing the open source drivers that run at the full 56k and this should work in Ubuntu Dapper and other versions, but I have only tested in Dapper Kubuntu. This came about when Rafael Espíndola ported the latest Conexant open source version to 2.6.x kernels. AlexandreOttoStrube packaged it for Ubuntu Breezy using kernel 2.6.12-9 The.deb file thus will not work on any newer kernel unless you compile it yourself as below. The files can be downloaded from  [http://www.surak.eti.br/linux/ubuntu/deb/conexant/](http://www.surak.eti.br/linux/ubuntu/deb/conexant/) or [ftp://ftp.wizzy.com/pub/wizzy/conexant/](ftp://ftp.wizzy.com/pub/wizzy/conexant/) courtesy AndyRabagliati and [https://wiki.ubuntu.com/DialupModemHowto?action=AttachFile&do=get&target=modem-hsfpci.tar.bz2](https://wiki.ubuntu.com/DialupModemHowto?action=AttachFile&do=get&target=modem-hsfpci.tar.bz2)
Firstly to ensure you have a modem that may work with these drivers, look at the make and model of your modem, by looking at the chipset. If it shows HSF and the number CX11252 (maybe other numbers here) on the chip then you have a softmodem/winmodem/linmodem and this driver should work. You can also install it on a Windows pc and do a modem query and if it shows PCI/VEN_14F1&DEV2F00 then you know it should work. 
The best way is to use your terminal to check your Vendor:Device pci id with "lspci" :
lspci
     0000:01:0b.0 Communication controller: Conexant HSF 56k Data/Fax Modem (rev 01)
Then, type "lspci -n" and look at the same identifying numbers to get the vendor:device id
lspci -n
     0000:01:0b.0 0780: 14f1:2f00 (rev 01)
In this example, it's 14f1:2f00. Vendor ID is first part (14f1), then a ":"  separates the Device ID (2f00).

Vendor ID's that are suported are listed here:

VendorID=14F1 : DeviceID=2F00 Tested and works on Dapper
VendorID=14F1 : DeviceID=2F01
VendorID=14F1 : DeviceID=2013 Tested and works
VendorID=14F1 : DeviceID=2014
VendorID=14F1 : DeviceID=2015
VendorID=14F1 : DeviceID=2016
VendorID=14F1 : DeviceID=2F10
VendorID=14F1 : DeviceID=2F11
VendorID=14F1 : DeviceID=2F12
VendorID=14F1 : DeviceID=2F13
VendorID=14F1 : DeviceID=2F14
VendorID=14F1 : DeviceID=4311
VendorID=127A : DeviceID=1025
VendorID=127A : DeviceID=2004
VendorID=127A : DeviceID=2005
VendorID=127A : DeviceID=2013
VendorID=127A : DeviceID=2014
VendorID=127A : DeviceID=2015
VendorID=127A : DeviceID=2016
VendorID=127A : DeviceID=4311
VendorID=127A : DeviceID=2114
VendorID=8086 : DeviceID=2416
VendorID=8086 : DeviceID=2446
VendorID=8086 : DeviceID=2486
VendorID=1106 : DeviceID=3068
VendorID=10B9 : DeviceID=5453
VendorID=10B9 : DeviceID=5457
VendorID=14F1 : DeviceID=2043
VendorID=14F1 : DeviceID=2044
VendorID=14F1 : DeviceID=2045
VendorID=14F1 : DeviceID=2046
VendorID=14F1 : DeviceID=2443
VendorID=14F1 : DeviceID=1631
VendorID=14F1 : DeviceID=1636
VendorID=14F1 : DeviceID=1637

Download the following files:
modem-hsfpci.tar.bz2 from [https://wiki.ubuntu.com/DialupModemHowto?action=AttachFile&do=get&target=modem-hsfpci.tar.bz2](https://wiki.ubuntu.com/DialupModemHowto?action=AttachFile&do=get&target=modem-hsfpci.tar.bz2) 
conexant_192-1ubuntu-1.tar.gz from [ftp://ftp.wizzy.com/pub/wizzy/conexant/conexant_192-1ubuntu-1.tar.gz](ftp://ftp.wizzy.com/pub/wizzy/conexant/conexant_192-1ubuntu-1.tar.gz)

This software supports the Conexant HSF 56k HSFi Modem, and was not tested with all models, anyone varifying a model to please update this with &#8220;tested and works&#8221; next to the ID list for help to others.
As you are going to compile your own drivers it is necessary that the required files are installed, check and/or install with Synaptic that the following are there:
build-essential, linux-headers-ARCH, debhelper and fakeroot is installed, ARCH is the result you get if typing uname-r in a terminal &#8211; version of kernel.

Method A:
This comprises of creating a .deb file and then using that to install and configure the driver.
1.Create a folder called HSFmodem on your Desktop and put both downloaded files in it, modem-hsfpci.tar.bz2 and conexant_192-1ubuntu-1.tar.gz
2.Now right click on modem-hsfpci.tar.bz2 and Extract Here (in same folder) a folder and a folder modem-hsfpci-0.1 and a file HOWTO.txt will be created.
3.No go to the konsole and enter:
cd Desktop/HSFmodem
./HOWTO.txt
and a file modem-hsfpci_0.1-0ubuntu1_386.deb will be created in folder /HSFmodem
4.You can install it with
sudo dpkg -i modem-hsfpci_0.1-0ubuntu1_i386.deb
5.Go to file    /etc/modem-hsfpci/modem-hsfpci.conf  Right click, click Actions then Edit as Root and Kwrite should open file modem-hsfpci.conf
Remove the comment # from your country and also from the Vendor:Device ID number determined above. If your ID are not shown you can try to create it in a new line, but there is no guarentee that it will work. If you do not do this the country will default to USA and the script will try to determine the Vendor ID with lspci.
6.Now you have to do the following to compile and install the configuration files and modules for your kernel version.
sudo /usr/sbin/modem-hsf    --install 
You should see the last line refering to modem installed and available on /dev/modem A symlink has also been created to the /dev/ttySHSF0 device.
7.You may have to reboot. The modem can be tested in Kppp by using Modem Query on /dev/modem. If it sees it you are OK and ATI 5 should show your country code.
8.You can uninstall by using Synaptic to completely uninstall modem-hsfpci_0.1-0ubuntu1

Note: Everytime you install a new kernel, especially after an update you will have to use the sudo /usr/sbin/modem-hsf    --install command to build kernel modules for it.

It has been suggested that you also try ATW2DT instead of ATDT when setting up your dialler (Kppp).

Method B:

1.Put the downloaded file  conexant_192-1ubuntu-1.tar.gz on your Desktop and right click &#8220;Extract  Here&#8221; and a folder &#8220;conexant&#8221; will be created on your Desktop.
2.Read the txt files in the folder for more info.
3.Open the folder &#8220;conexant/modules/makefile&#8221;, right click on makefile, click Actions, then Edit as Root and Kwrite should open the file /conexant/makefile. Now find the 2 lines that start with # KERNELDIR? = /lib/modules..... etc. and KERNELDIR?= /usr/src... etc Remove the comment # in the first line and insert comment # on second line and save changes.
4.Now open the /conexant/makefile in the same way and find the commented line # rm -rf $$DESTDIR/dev/ttySHFS0. Remove the comments from the mentioned line and the following 3 lines up to &#8220;update modules&#8221; and save changes
5.cd Desktop/conexant
6.make
7.sudo make install
8.sudo modprobe hsfserial     (you should get no result report if OK)
9.dmesg | grep hsfserial         ( you should get no result report if OK)
10.The /dev/ttySHFS0 is created for the modem
11.To test, use the query modem on Kppp

To remove the installation:
rm /dev/ttySHFS0
rm -r /etc/hsf
rm /lib/modules/ARCH/misc/hsf*

_Howto get Smartlink winmodem working in dapper_

Smartlink soft modems work quite well in ubuntu, but some problems have been found and the process below works in Dapper. It also seems as if the Smartlink modems with Netodragon chip MDV92XP do not work, but the ND92XPA chip works with the process below. Also read the ubuntu wiki dialupmodemhowto for details and other methods.
Use Synaptic to ensure that you have all the necessary packages installed for compiling your drivers. This includes build-essential, linux-headers-ARCH (where ARCH is your kernel version  and can be found with uname -r in the terminal), fakeroot, module-assistant and debhelper.
Basically the sl-modem-source has to be installed first and then the sl-modem-daemon. It seems as if the latest daemon also looks for ungrab-winmodem so download and install this from the linmodem website.

Method A:

This method uses the latest packages from linmodems and the latest daemon on the Dapper repository or from the Debian repositories and works well.
 1.Download  slmodem-2.9.11-20051101.tar.gz from [http://phep2.technion.ac.il/linmodems/packages/smartlink/](http://phep2.technion.ac.il/linmodems/packages/smartlink/) . This package seems to work better in breezy and dapper and does not give the dialing problem that causes the modem to fail on ATDT and not dial out.
 2.Also download and install the ungrab-winmodem from the [http://phep2.technion.ac.il/linmodems/packages/smartlink/](http://phep2.technion.ac.il/linmodems/packages/smartlink/). linmodem website by using make and sudo make install.
 3.Copy the sl-modem-2.9.11-20051101.tar.gz file to your Desktop and right click on it and select &#8220;Extract here&#8221; and a folder wth the same name will be created with the extracted files on your Desktop.
 4.Now rename the folder to an easier name such as &#8220;slmodem&#8221;
 5.Open a terminal and cd in to the slmodem folder
 6.Type make
 7.Type sudo make install
 8.Type sudo modprobe slamr
 9.Type dmesg | grep slamr
 10.Now enable your repositories and install sl-modem-daemon_2.9.10+2.9.9d+e-pre2-5build1_i386.deb with Synaptic.
 11.Use Kppp to query the modem, if this works you are there!
 12.Edit  /etc/default/sl-modem-daemon to change the line SLMODEMD_COUNTRY= USA to i.e SOUTHAFRICA or your country
 13.Type sudo /etc/init.d/sl-modem-daemon restart to restart the daemon.
 14.If you do a &#8220;Query modem&#8221; in Kppp and you will see that your country has changed.

Method B:

This method uses the latest matched packages from the Debian repositories and did work, but then after an update and installation of other packages suddenly stopped working together. the debian daemon though works well together with the sl-modem-2.9.11-20051101.tar.gz package.
1.Download sl-modem-daemon2.9.9d+e-pre2-5.deb and sl-modem_2.9.9d+e-pre2.orig.tar.gz from the debian website [http://packages.debian.org/unstable/misc/sl-modem-daemon](http://packages.debian.org/unstable/misc/sl-modem-daemon).  
I have found that the slmodem-2.9.11-20051101.tar.gz works better in dapper and this can also be downloaded from the linmodem website if you want to try this one rather. (suggested as other package may fail on ATDT and then does not dial out)  [http://phep2.technion.ac.il/linmodems/packages/smartlink/](http://phep2.technion.ac.il/linmodems/packages/smartlink/).
2.Also download and install the ungrab-winmodem from the [http://phep2.technion.ac.il/linmodems/packages/smartlink/](http://phep2.technion.ac.il/linmodems/packages/smartlink/). linmodem website  by using make and sudo make install.
3.Copy the sl-modem-daemon file to your local repository and update your Packages.gz file, this will allow you to install with Synaptic etc. Or use your favourite way to install a .deb file.(dpkg etc)
4.Copy the sl-modem_2.9.9d+e-pre2.orig.tar.gz ( or preferably the slmodem-2.9.11-20051101.tar.gz) file to your Desktop and right click on it and select &#8220;Extract here&#8221; and a folder wth the same name will be created with the extracted files on your Desktop.
5.Now rename the folder to an easier name such as &#8220;slmodem&#8221;
6.Open a terminal and cd in to the slmodem folder
7.Type make
8.Type sudo make install
9.Type sudo modprobe slamr
10.Type dmesg | grep slamr
11.Now install sl-modem-daemon2.9.9d+e-pre2-5.deb with Synaptic or in your own favourite way.
12.Use Kppp to query the modem, if this works you are there!
13.Edit  /etc/default/sl-modem-daemon to change the line SLMODEMD_COUNTRY= USA to i.e SOUTHAFRICA or your country
14.Type sudo /etc/init.d/sl-modem-daemon restart to restart the daemon.
15.If you do a &#8220;Query modem&#8221; in Kppp and you will see that your country has changed.



Method C:
( At the moment this fails and the sl-modem-module is not created when installing with Synaptic, the install is successful if the install is done with sudo module-assistant  auto-install sl-modem, sudo depmod -a The modem is then detected but fails on ATDT and does not dial out) This problem was also noted in Breezy. We need a .deb file made from  slmodem-2.9.11-20051101.tar.gz that has already been proven to work in Breezy and Dapper)
1.Also download and install the ungrab-winmodem from the [http://phep2.technion.ac.il/linmodems/packages/smartlink/](http://phep2.technion.ac.il/linmodems/packages/smartlink/). linmodem website.
2.Enable the universe/multiverse repositories
3.Use Synaptic to search for sl-modem
You will find 2 files called sl-modem-daemon_2.9.10+2.9.9d+e-pre2-5build1_i386.deb and sl-modem-source_2.9.10+2.9.9d+e-pre2-5build1_i386.deb
4.Install the sl-modem-source and then the sl-modem-daemon
5.Now go to /etc/default/sl-modem-daemon, right click, Action, Edit as Root, find the line SLMODEMD_COUNTRY=USA and change the USA to SOUTHAFRICA or your country name.
6.Go to the konsole: 
7.sudo  modprobe slamr
8.sudo  /etc/init.d/sl-modem-daemon  restart
9.Now go to Kppp and select /dev/modem and use the Query Modem to test you modem. Now setup Kppp and go on line!

Note: If you are going to use Kppp it is advisable that you first activate the line #noauth by removing the # comment in  /etc/ppp/peers/kppp-options.

To release a locked up Smartlink modem use  sudo modprobe ungrab-winmodem, then sudo modprobe slamr, then restart the daemon with sudo /etc/init.d/sl-modem-daemon restart. This may help you from rebooting.

Footnote:
The daemon package shown above, whether from the debian repo or ubuntu repos works with any of the driver packages, but only the linmodem driver package  slmodem-2.9.11-20051101.tar.gz seems to be fairly stable with the dapper kernel version. We thus need this package to be put on the ubuntu repos. The ungrab-winmodem package should also be a 'dependancy&#8221; for the daemon package and also be installed together by Synaptic. Will pass this on to the motu that is concerned with the modem drivers.

---

### Post by Killjoy23 on 2006-06-06
Habib, 

Well, looks like I've been beaten to the punchline...I can confirm with some authority that you've got a conexant modem. it's an intel ICH hsf modem and the newer (totally crippled and worthless unless you fork over cash)linuxant drivers do support them. Unfortunately I've got to get ready for work, but let us know how this turns out! If you've got any other questions, don't hesitate to ask!
To answer the ungrab-winmodem question, it's a driver that (if I understand this right)fixes problems with errors involving the modem driver not detecting a modem even though everything was installed correctly.

Jas

EDIT: I will attempt to compile some packages for the driver listed below, but it may take a day or two. I will post the results of that adventure when it's finished.

---

### Post by gesho on 2006-06-07
or go to linuxant.com
and there is scan&install soft which will do the whole job for you.
though for free you only get 14 kb/sec
full speed worth some $20

---

### Post by habib_seif on 2006-06-08
[QUOTE=Killjoy23]Habib, 
drivers do support them. Unfortunately I've got to get ready for work, but let us know how this turns out! If you've got any other questions, don't hesitate to ask!
[/QUOTE]

Thanks a lot Killjoy23...
I also think 8086:266d is a Conexant modem. because scanModem says that... 
but unfortunately, the free driver introduced in DialupModemHowto can't support it. 
If I set 8086:266d as device id and issue the command: /usr/sbin/modem-hsf --install, it is encounterd to the Segmentation fault and ubuntu freezes after that time and if I set 14f1:5423 as device id and issue the command: /usr/sbin/modem-hsf --install, the installation is completed but /dev/modem isn't created meaning that this driver doesn't support my modem :-(
By the way, I havn't tried the driver when ungrab-winmodem is installed.....
I hope these information can help you to correct the driver ;) 
Cheers,
Habib

---

### Post by mesocool on 2006-06-09
[QUOTE=habib_seif]Thanks a lot Killjoy23...
I also think 8086:266d is a Conexant modem. because scanModem says that... 
but unfortunately, the free driver introduced in DialupModemHowto can't support it. 
If I set 8086:266d as device id and issue the command: /usr/sbin/modem-hsf --install, it is encounterd to the Segmentation fault and ubuntu freezes after that time and if I set 14f1:5423 as device id and issue the command: /usr/sbin/modem-hsf --install, the installation is completed but /dev/modem isn't created meaning that this driver doesn't support my modem :-(
By the way, I havn't tried the driver when ungrab-winmodem is installed.....
I hope these information can help you to correct the driver ;) 
Cheers,
Habib[/QUOTE]

For my desktop, after I upgrade the driver, it works. But for my laptop, it doesn't work with no dial tone error message. (Both are internal modems)

So no dial tone means not supported?? ](*,)

---

### Post by gesho on 2006-08-02
**Matchless**: great job.
my conexant modem has id: 24c6, not in the list of modem-hsfpci.conf

any hope? would it work if I add the line in the file? or is it hopeless?

---

### Post by gesho on 2006-08-02
**Matchless**: great job.
my conexant modem has id: 24c6, not in the list of modem-hsfpci.conf

any hope? would it work if I add the line in the file? or is it hopeless?

---

