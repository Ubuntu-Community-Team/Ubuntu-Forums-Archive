---
title: "iBurst PCMCIA How-TO"
date: 2006-02-23
forum: Networking &amp; Wireless
---

### Post by Skrewdriver on 2006-02-23
***](*,) WARNING: This HOW-TO is only good for Dapper (6.06) and earlier distros. Changes in Edgy are not compatiable with this doc. Edgy 6.10 iBurst How-To is here: [http://ubuntuforums.org/showthread.php?p=1794253](http://ubuntuforums.org/showthread.php?p=1794253)***

Ok, here's the (very) long awaited iBurst PCMCIA how-to.
#1 Rule - don't plug the card in until I tell you to. Thanks.

[LIST=1]
[*]First thing is you need to download the iBurst drivers from our good friends at sourceforge:
[http://sourceforge.net/projects/ibdriver/]("http://sourceforge.net/projects/ibdriver/")
[*]Then download the Roaring Penguin PPPOE dialer (I can't get it working with the Debian dialer):
[http://www.roaringpenguin.com/penguin/open_source_rp-pppoe.php/]("http://www.roaringpenguin.com/penguin/open_source_rp-pppoe.php/")
[*]Open up a terminal and make sure the two tarballs (files) you just downloaded are in the directory you want to work in. Extract the two tar files:
```
tar -xf ibdriver*
tar -xf rp-pppoe*
```
[*]You need to have installed the build-essentials package, plus the linux kernel headers. For some reason ibdriver only compiles with gcc3.4, so you need to get that too.
EDIT Note: Dapper does not require gcc3.4 installed to build the drivers!
```
sudo aptitude install build-essential gcc-3.4 linux-headers-386 linux-kernel-headers
```
[*]Sometimes you need to make a symbolic link to the headers. Better safe than sorry, so do it anyway:
```
sudo ln -s /usr/src/linux-headers-$(uname -r) /lib/modules/$(uname -r)/build
```
[*]Now cd to the directory with the ibdriver source, then make and install the drivers.
```
make
sudo make install
```
If all goes well you will get no error messages, the output of the **make** command should look something like this:
```
make -C /lib/modules/2.6.12-10-686/build SUBDIRS=/home/mark/build/ibdriver-1.2.8 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-686'
  CC [M]  /home/mark/build/ibdriver-1.2.8/ib-net.o
  CC [M]  /home/mark/build/ibdriver-1.2.8/ib-pcmcia.o
  CC [M]  /home/mark/build/ibdriver-1.2.8/ib-usb.o
  CC [M]  /home/mark/build/ibdriver-1.2.8/ib-file.o
  Building modules, stage 2.
  MODPOST
  CC      /home/mark/build/ibdriver-1.2.8/ib-file.mod.o
  LD [M]  /home/mark/build/ibdriver-1.2.8/ib-file.ko
  CC      /home/mark/build/ibdriver-1.2.8/ib-net.mod.o
  LD [M]  /home/mark/build/ibdriver-1.2.8/ib-net.ko
  CC      /home/mark/build/ibdriver-1.2.8/ib-pcmcia.mod.o
  LD [M]  /home/mark/build/ibdriver-1.2.8/ib-pcmcia.ko
  CC      /home/mark/build/ibdriver-1.2.8/ib-usb.mod.o
  LD [M]  /home/mark/build/ibdriver-1.2.8/ib-usb.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686'

```
... and the ouput of the **sudo make install** command will look like this:
```
cp *.ko /lib/modules/2.6.12-10-686/kernel/drivers/net/
echo checking module dependancies...
checking module dependancies...
depmod -a

```
... and you have successfully compiled and installed the driver modules. Now we gots to change a few configuration files.
EDIT: For USB (desktop) modems, skip the PCMCIA steps and go straight to configuring the dialer
[*] First change is the PCMCIA configuration file.
```
sudo gedit /etc/pcmcia/config.opts
```
At the end of this file, paste the following:
```
device "iburst_cs"
   class "network" module "ib-pcmcia"

card "ArrayComm ut02"
    manfid 0x02e3, 0x0001
    bind "iburst_cs"

card "ArrayComm ut02"
    manfid 0x02e3, 0x0002
    bind "iburst_cs"

```
Save the file and exit
[*]Next file:
```
sudo gedit /etc/default/pcmcia
```
Look for a line that says **CORE_OPTS**. Change it to the following:
```
CORE_OPTS="unreset_check=20 unreset_delay=100 unreset_limit=100"
```
Save the file and exit
[*]Next file:
```
sudo gedit /etc/modprobe.d/iburst
```
The only text in this file should be:
```
options ib-net ifname="ib"
```
Save the file and exit
[*]Okay, that is the PCMCIA stuff configured. Restart the PCMCIA system
```
sudo /etc/init.d/pcmcia restart
```
Then **plug your card in.** :KS  If sound is enabled, you should hear two beeps, and eventually the status light goes from [COLOR="Magenta"]purple[/COLOR] to [COLOR="Blue"]blue[/COLOR]. That means your card is plugged in and happy. You can check this by listing the loaded modules:
```
lsmod | grep ib_
```
.. if all is well you will see **ib_net** and **ib_pcmcia** listed.
[*]Now we configure the dialer. cd to the directory where you extracted the Roaring Penguin source, then run the setup script:
```
sudo ./go
```
... wait for a bit while the script works it's magic, then answer the questions the script asks. Answers are:
[LIST=2]
[*]**Username:** your mobile broadband provider would have told you this eg. [email]yourname@isp.com.au[/email]
[*]**Ethernet interface:** ib0
[*]**Demand value:** no
[*]**DNS**: server
[*]**Password**: The password supplied by your mobile broadband ISP.
[*]**Firewall**: 1
[/LIST]
... check the settings are correct and accept them if so.
[*] One last config file to change:
```
sudo gedit /etc/network/interfaces
```
Insert the following code at the end of the file:
```
# iBurst
iface ib0 inet manual
   up ifconfig $IFACE up
   up pppoe-start
   down pppoe-stop
   down ifconfig $IFACE down

```
Save the file and exit.
[*] Now we will test the connection. Make sure you are somewhere with good reception, so the reception quality light on your card should be [COLOR="Green"]green[/COLOR]. Run the command to initialise a pppoe connection:
```
sudo ifup ib0
```
... and (fingers crossed) you should get a connection!
To stop the connection use the command:
```
sudo ifdown ib0
```
[*] And that's it. 
[/LIST]
\\:D/ Too easy (unless there is errors in this how-to!).
If your iBurst card is inserted when you boot the laptop then it will connect automatically. Otherwise use the ifup command above (don't forget to use sudo).
Good luck, and enjoy the freedom of using free software wherever you want (coverage permitting of course). My favourite is sitting on the bus, and everyone thinks you are a right knob-end.:) :)

---

### Post by davidgypsy on 2006-03-05
Will this work with the desktop model as well?

---

### Post by Skrewdriver on 2006-03-21
Check the readme that comes with ibdriver, see what the differences are.
Obviously you won't be doing any PCMCIA configuration, but the pppoe stuff should be the same.

---

### Post by Skrewdriver on 2006-03-30
I have now set up a wiki page at the official Ubuntu wiki, and that will be the only text that I update (unless there is glaring errors!)

[https://wiki.ubuntu.com/MobileWirelessBroadband]("https://wiki.ubuntu.com/MobileWirelessBroadband")

---

### Post by edwardvankuik on 2006-05-03
I plugged in my PCMCIA iBurst UTC-SA card before I read that bit about not plugging it in.
I managed to compile the modules, but they don't load automatically when I (re)plug the card in. They load ok manually if i use modprobe. 

But dmesg just says:
[4296021.214000] cs: pcmcia_socket0: time out after reset.

What do I do now?

Edward

---

### Post by Skrewdriver on 2006-05-03
Are you using Breezy or Dapper?
Double check that all the data is entered correctly, with no extra spaces or missing characters.
Did it compile with no errors?

---

### Post by edwardvankuik on 2006-05-04
I'm using Breezy. 
It compiled perfect as in the example.
I'll double check everything now. Could it be that I have another type of card. It says 'iBurst' on it though.

---

### Post by Nitrogen on 2006-10-05
Fantastic How-To. I am glad that there are people with i
burst problems like me. I used the how-to and my pcmcia modem connected once then, on my next restart the iburst never worked again. when I try to connect it tells me that the device could not be found (invalid flag?)

---

### Post by correim on 2006-11-05
I am using Ubuntu for the first time and installed version 6.10, but I am struggling to get my iBurst modem installed.

I get the following error when I execute the "make" command during step number 6:

michael@michael-desktop:~/michael/downloads/iBurst_Drivers/ibdriver-1.2.9$ make
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/michael/michael/downloads/iBurst_Drivers/ibdriver-1.2.9 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/michael/michael/downloads/iBurst_Drivers/ibdriver-1.2.9/ib-pcmcia.o
/home/michael/michael/downloads/iBurst_Drivers/ibdriver-1.2.9/ib-pcmcia.c:103: error: field ‘link’ has incomplete type
/home/michael/michael/downloads/iBurst_Drivers/ibdriver-1.2.9/ib-pcmcia.c: In function ‘ib_pcmcia_deregister’:
/home/michael/michael/downloads/iBurst_Drivers/ibdriver-1.2.9/ib-pcmcia.c:255: error: dereferencing pointer to incomplete type
/home/michael/michael/downloads/iBurst_Drivers/ibdriver-1.2.9/ib-pcmcia.c: In function ‘ib_pcmcia_release’:
/home/michael/michael/downloads/iBurst_Drivers/ibdriver-1.2.9/ib-pcmcia.c:269: error: ‘dev_link_t’ undeclared (first use in this function)
etc.....

Any suggestions?

---

### Post by DocMSK on 2006-11-19
I am also using 6.10 and get the same error quoted above by correim. Help appreciated.
Rgds
Doc

---

### Post by Skrewdriver on 2006-11-19
I'm still running Dapper on my laptop and the desktop USB. Had problems compiling the drivers using Edgy (6.10). I *think* the problem is due to the different kernels - there is a patch on the sourceforge site that updates the code for 2.6.17 kernels but I could not get it to work. I will investigate a bit further, but at the moment I am sticking with the 2.6.15 kernel in Dapper so I can use my modems. My immediate advice is to install the 2.6.15 kernel plus headers, make sure you are running that kernel when you compile and install the drivers. Let me know if it still craps out.

---

### Post by DocMSK on 2006-11-19
Thanks for your swift response Skrewdriver, and your time, will update here if I manage to get it to work.

Rgds
Doc

---

### Post by Skrewdriver on 2006-11-21
Just got this message from Sourceforge:
> By: nik777

I have just released ibdriver 1.3.1

If your kernel is indeed 2.6.17 or greater then you should download the
ibdriver-1.3.1-linux-2.6.17.tar.gz file.
If your kernel is 2.6.16 or earlier, you should download
ibdriver-1.3.1-linux-2.6.tar.gz.
Download page is here: [https://sourceforge.net/project/showfiles.php?group_id=138984&package_id=212373](https://sourceforge.net/project/showfiles.php?group_id=138984&package_id=212373)


I compiled the ibdriver-1.3.1-linux-2.6 driver with the last Dapper kernel 2.6.15-27 and everything worked fine - will try the upgrade to Edgy tomorrow night.

---

### Post by DocMSK on 2006-11-21
Thanks Skrewdriver. I downloaded the latest ibdriver from Sourceforge. It does compile fine. However, following thru your original HOW-TO there seem to be some some changes. Everything goes fine until step 8. There is no pcmcia file on my version of Edgy Eft. I had to create "iburst" in step 9. Can't execute the command in step 10.

Was reading the README that came with the iburst driver. I am a total newbie. It mentions a system called PCCARD instead of PCMCIA in the README. Could Edgy be using that? RP installed fine. Whenever I try doing a:

```
@Ubuntu:~$ sudo ifup ib0

ib0: ERROR while getting interface flags: No such device
Failed to bring up ib0
```


```

@Ubuntu:~$ pccardctl info
PRODID_1="Kyocera Corporation"
PRODID_2="Access Card"
PRODID_3=""
PRODID_4=""
MANFID=02e3,0002
FUNCID=6
PRODID_1="O2Micro"
PRODID_2="SmartCardBus Reader"
PRODID_3="V1.0"
PRODID_4=""
MANFID=ffff,0001
FUNCID=255

@Ubuntu:~$ pccardctl status

Socket 0:
  5.0V 16-bit PC Card
  Subdevice 0 (function 0) bound to driver "iburst_cs"
Socket 1:
  5.0V 16-bit PC Card
  Subdevice 0 (function 0) [unbound]

@Ubuntu:~$ pccardctl ident

Socket 0:
  product info: "Kyocera Corporation", "Access Card", "", ""
  manfid: 0x02e3, 0x0002
  function: 6 (network)
Socket 1:
  product info: "O2Micro", "SmartCardBus Reader", "V1.0", ""
  manfid: 0xffff, 0x0001

```

The system seems to recognise the card, and the driver.

Any help appreciated.

Regards
Doc

---

### Post by Skrewdriver on 2006-11-21
Good to hear the compile went fine, that is the first sticking point out of the way. One of the big changes from Dapper to Edgy is the use of 'upstart' to kick everything off. This is where you are having problems - we need to edit a config file *somewhere*, but I am not sure where. I will install Edgy tonight when I am at work (instead of working) and hopefully have an answer for you within 24hrs.

---

### Post by Nitrogen on 2006-11-22
I have tried a few distro's suse 10.1 uses the pccard system it works like a charm. All you have to do is make the drivers, make install. Then install rp-pppoe (./go details) then pppoe-start.
I have been using my iBurst with suse 10.1 for 3 months now.

I do like the simplicity of Ubuntu ,but I just cant seem to get my iBurst to work under Dapper Drake.(pcmcia user terminal)
So I do hope that Edgy Eft is using the pccard system.

Will wait to hear!

---

### Post by Skrewdriver on 2006-11-22
Okay I sorted out my laptop upgrade to Edgy and got everything working.
The new Edgy iBurst How-to is here: [http://ubuntuforums.org/showthread.php?p=1794253](http://ubuntuforums.org/showthread.php?p=1794253)

.. the main change is that the interface is called 'ib', not 'ib0'. Keep that in mind!

---

### Post by DocMSK on 2006-11-23
Skrewdriver, u da man! Thanks, got it working... I think I will do a fresh install of Edgy Eft and cleanly install the ibdriver, since I have been hacking away at various files not quite knowing what i was doing trying to get this to work before you posted your new HOW-TO.

Thanks again!
Doc

---

### Post by Nitrogen on 2006-11-27
sudo ppoeconf (ppoeconf not found)


This command will not work. I have checked with synaptic and ppoeconf is installed.

Have also installed build essentials.

How do I get this to work?

---

### Post by Skrewdriver on 2006-11-27
Run Synaptic and reinstall pppoeconf package.
Try ```
sudo /usr/sbin/pppoeconf
```

---

### Post by Skrewdriver on 2006-11-27
I just had a second look at your post ...
the correct command is:
```
sudo pppoeconf
```

*not* ppoeconf

I apologise if there is a typo in the How-to .. will check it now.

EDIT: Sure enough, there was. I have corrected the typo. Sorry bout that!

---

### Post by Nitrogen on 2006-11-27
Sweet I will try that when I get home from work. Thanks for the help, your a machine!

---

### Post by Nitrogen on 2006-12-10
I found that this line made, the iburst pcmcia terminal show up in Networking as eth02:

sudo gedit /etc/modprobe.d/iburst, and insert the line:

      options ib-net ifname="eth%d"

I could not get the terminal to work with:

sudo gedit /etc/modprobe.d/iburst

options ib-net ifname="ib%d"

---

### Post by nortis on 2006-12-20
```
sudo ln -s /usr/src/linux-headers-$(uname -r) /lib/modules/$(uname -r)/build
```

My Ubuntu laptop is not connected to the net (yet:) ) is there anyway I can download these files from the net and install them manually by transfering them to my Ubuntu Laptop.

Thanks

---

### Post by Skrewdriver on 2006-12-20
It you download the Alternate Install CD-ROM from the Ubuntu site it will have the packages you need, excluding the Sourceforge ibdriver tarball.  Download the ISO file, burn the CD, then make sure you register the CD with Synaptic.
Otherwise you can go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and download them one by one but you will get stuck in dependency hell.
Are you running Dapper (6.06LTS) or Edgy (6.10) ?

---

### Post by krugazul on 2006-12-21
So i did everything in the HOW-TO and got it right, but when i dial up it just time out
I am Noob

Please Help Warwick.

ps when i type the following in i get this

lsmod | grep ib
speedstep_lib           4484  0


krug@krug-linux:~/rp-pppoe-3.6$ sudo pon dsl-provider
Plugin rp-pppoe.so loaded.
/usr/sbin/pppd: In file /etc/ppp/peers/dsl-provider: unrecognized option 'nic-ib0'

krug@krug-linux:~$ sudo ifup ib0
................TIMED OUT
Failed to bring up ib0.

krug@krug-linux:~$ tail /var/log/dmesg
[4294688.751000] NET: Registered protocol family 17
[4294689.464000] lp0: using parport0 (interrupt-driven).
[4294689.513000] Adding 3036244k swap on /dev/hdd5.  Priority:-1 extents:1 across:3036244k
[4294689.642000] EXT3 FS on hdd1, internal journal
[4294689.803000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294689.803000] md: bitmap version 4.39
[4294690.010000] eth0: Media Link On 100mbps full-duplex
[4294690.322000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294691.783000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[4294691.798000] NTFS volume version 3.1.

---

### Post by nortis on 2006-12-21
I'm using Breezy 5.10 and tried to install my iBurst pcmcia modem using the information on the wiki  [https://help.ubuntu.com/community/MobileWirelessBroadband]("https://help.ubuntu.com/community/MobileWirelessBroadband")
I followed everything step by step.

I the installation of the driver seemed to be done ok, and when I put the modem in the PC the light turns from purple to blue. However when I type```
lsmod | grep ib_
``` nothing is listed.

If I then try ```
sudo ifup ib0 
```
I get the error
```

ib0: ERROR while getting interface flags: No such device
Failed to bring up ib0

```

---

### Post by Skrewdriver on 2006-12-21
Krugazul / Nortis:

For both of you it looks like the drivers are not loading. If they were loading properly then they would show up in the lsmod. So it could be:
(a) the drivers are not compiling properly
or
(b) something is wrong with the configuration files.

Are you 100% sure the drivers are compiling properly? If you have the slightest doubt, then recompile and install them, and post the output from both commands in this thread.
Make sure you are in the ibdriver source directory and do
```
make clean
```
before you do the
```
make; sudo make install
```

---

### Post by nortis on 2006-12-21
When I run make I get a warning, here is the output
```
make -C /usr/src/linux-headers-2.6.12-10-386/  SUBDIRS=/home/neil/Desktop/Neil/i bdriver-1.3.1-linux-2.6 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /home/neil/Desktop/Neil/ibdriver-1.3.1-linux-2.6/ib-net.o
  CC [M]  /home/neil/Desktop/Neil/ibdriver-1.3.1-linux-2.6/ib-pcmcia.o
/home/neil/Desktop/Neil/ibdriver-1.3.1-linux-2.6/ib-pcmcia.c: In function `ib_pcmcia_exit':
/home/neil/Desktop/Neil/ibdriver-1.3.1-linux-2.6/ib-pcmcia.c:1048: warning: suggest explicit braces to avoid ambiguous `else'
  CC [M]  /home/neil/Desktop/Neil/ibdriver-1.3.1-linux-2.6/ib-usb.o
  Building modules, stage 2.
  MODPOST
  CC      /home/neil/Desktop/Neil/ibdriver-1.3.1-linux-2.6/ib-net.mod.o
  LD [M]  /home/neil/Desktop/Neil/ibdriver-1.3.1-linux-2.6/ib-net.ko
  CC      /home/neil/Desktop/Neil/ibdriver-1.3.1-linux-2.6/ib-pcmcia.mod.o
  LD [M]  /home/neil/Desktop/Neil/ibdriver-1.3.1-linux-2.6/ib-pcmcia.ko
  CC      /home/neil/Desktop/Neil/ibdriver-1.3.1-linux-2.6/ib-usb.mod.o
  LD [M]  /home/neil/Desktop/Neil/ibdriver-1.3.1-linux-2.6/ib-usb.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'

```

---

### Post by nortis on 2006-12-22
I'm thinking about upgrading Breezy to Dapper, would this effect the installation of the modem. Other than needing to use the different driver?

---

