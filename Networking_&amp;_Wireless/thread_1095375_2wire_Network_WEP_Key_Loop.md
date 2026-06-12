---
title: "2wire Network WEP Key Loop"
date: 2009-03-13
forum: Networking &amp; Wireless
---

### Post by JerryI on 2009-03-13
Dual-boot XP/Hardy Laptop new hard disk installed last night.  In Hardy I can see my wireless network which I am trying to access via a 2wire USB adapter 802.11g.  But when I try to connect by selecting network 2wire411 (out of several 2wire networks in my neighborhood) and key in my wep key 0360663701, it seeks for a few seconds and comes back and asks for my wep key again.  I can connect via XP, Vista, and Intrepid (the computer I'm typing on now). So I'm confident the wep key is valid.

I have just now noticed that the wep box is asking for a passphrase, not a wep key.  When I change the option to WEP 64/128 ASCII, the connect box greys out so I cannot click it.

FYI

jerry@laptop:~$ sudo lshw -C network
[sudo] password for jerry: 
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:86:5c:8e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:1e:37:f6:cc:c4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b/g
jerry@laptop:~$

---

### Post by issih on 2009-03-13
AS I said previously your first port of call is to check that your wireless card is actually capable of working with the current driver, quite regardless of any encryption (i.e. WEP)

log into your router's setup page, find the bit relating to wireless security and, temporarily, set it so you have no security being used.

Can you then connect to your wireless network.

This is simply a case of building up from the bottom, WEP can't function if the basic wireless isn't working, so we have to go one step at a time.

---

### Post by JerryI on 2009-03-13
I have approximately zero useful experience with linux at this point, so please be patient. Someone has advised me to remove Network Manager and replace it with WICD.  I might be able to accomplish that within another day or so, but I decided not to attempt it yet.  Another person advised me to reset my 2wire router.  Since I can access the network via three or four operating systems in my house, I have not tried that yet.  One other thing puzzles me.  Hardy indicates that two updates are availabe.  How does the os know this if we cannot even access the network, much less the internet?  When I try to install the 2 updates, I get the message 'Failed to fetch [http://.](http://.)........  Could not resolve 'security.ubuntu.com.

Re your suggestion, log into your router's setup page, find the bit relating to wireless security and, temporarily, set it so you have no security being used, and having no idea how to unsecure my connection, I took a stab at system preferences encryption and keyrings and I see that encryption default key is 'None. Prompt for a key'   Password keyrings shows 'login. Automatically unlocked when user logs in.

So it is pretty apparent that you are working with a total basket case.  I have no idea how to proceed to follow your advice.  Can you give me some command line prompts that I can paste back to you for analysis?

It appears to me that I have no driver installed for my 2wire usb adapter. Do I need to start by getting ndiswrapper and finding some kind of generic linux usb driver and loading it?

---

### Post by issih on 2009-03-13
No nothing to do with changing anything on your ubuntu pc, leave it alone for now.

You need to change the settings in your router, so that it is supplies a wireless networking signal without requiring any encryption (WEP). Nearly all routers work by having a very small web server built into them, and you change the configuration by logging onto that webserver. Commonly you achieve this by simply entering the IP address of your router into a web browser on a machine connected to the router.

For instance, if I enter 192.168.0.1 into my web browser now, I get a web page from where I can configure my router.

In your case, go to one of the pc's that is connected and try:

[http://homeportal/setup](http://homeportal/setup)

as that appears to be something to do with 2wire, if that doesn't work, then you'll have to fish out the manuals/installation information that came with your router and find out what you should be entering.

Once you are in that configuration page, you need to find the settings for wireless security and turn it off (not wep or wpa, OFF) then apply those setting and try connecting with the ubuntu pc.

Hope that helps.

P.S. as for the update, I'd guess you were connected to the internet at some point (maybe via an ethernet cable?) and it downloaded the list of packages that should be updated..so the OS now knows that those packages are out of date, but because you currrently have no net connection cannot fetch the new versions.

---

### Post by JerryI on 2009-03-13
Thanks.  Now maybe I can take a few very small steps for one senior citizen.  BTW, I have managed to download ndiswrapper-1.54.tar.gz onto this computer into a directory somewhere called Downloads, I think.  If I ever get to the point where I want to install that app, how do I find the download directory and drag the file to my usb flashdrive so I can move it to the target computer that doesn't have internet access?

---

### Post by issih on 2009-03-13
On the assumption that you still have your ubuntu install cd lying around somewhere, we can grab any ndiswrapper packages off that if we need them, so don't worry about that.

No idea where that download folder will be anyway, it rather depends on the operating system and indeed how it is configured :)

Oh and just so you know, I'm in England, so I might disappear off to bed relatively soon, well in an hour or so

---

### Post by JerryI on 2009-03-13
I'm back.  I have opened my network to all my neighbors.  I cannot make a connection on Hardy.  I am typing to you on Intrepid.  I have Ubuntu Hardy CD.  I think we need to install a driver.  Pls help.  I suspect that we will find that the adapter does not have a viable linux driver.  That was a problem that I ran into with Intrepid earlier and I never found a viable solution on the internet.  The 2wire 802.11g I have (Model US-G-AT-02) is silver and is not pinchwaisted like the ones that are reported to work.  I have ordered a Belkin adapter that is supposed to work, but it is enroute from Hong Kong.  If all fails tonight, should I proceed to install ndiswrapper and re-arm my router?  Are there any tests to perform first?

---

### Post by issih on 2009-03-13
Well if you can't connect with an open network, then it is probably a driver module problem. To that end we need to work out what chipset your usb dongle uses, so for now can you post the output of running "lsusb" in a terminal window, and then turn wep back on on your router. I am signing off for today, I'll look back in on things when my morning rolls around.

---

### Post by JerryI on 2009-03-13
Bus 004 Device 003: ID 0ace:1215 ZyDAS WLA-54L Wifi

---

### Post by issih on 2009-03-14
First of all, could you do me a favour and post the output ```
lsmod | grep zd
```

That should help me work out what is going on, as there are apparently two different kernel modules for this card, an original vendor one, and a community rewrite, and we need to know which one we are dealing with.

I suspect we are playing with the rewrite zd1211rw driver, and after a bit of research, it looks like support for the chipset in your card was added into the driver that ships with the kernel from 2.6.22 onwards, but the usb id's were being updated right through that series.

There is also a possibility that it could be a firmware loading issue.

Can you, in addition to the command at the top, post the output of running:

```
uname - r
```

As I'm not sure what kernel hardy shipped with.

---

### Post by JerryI on 2009-03-14
jerry@laptop:~$ sudo ndiswrapper
[sudo] password for jerry: 
sudo: ndiswrapper: command not found
jerry@laptop:~$ ping 192.168.1.254
connect: Network is unreachable
jerry@laptop:~$ lsmod | grep zd
zd1211rw               56964  0 
ieee80211softmac       30976  1 zd1211rw
ieee80211              35528  2 zd1211rw,ieee80211softmac
usbcore               146412  5 zd1211rw,usbhid,ehci_hcd,uhci_hcd
jerry@laptop:~$ 
jerry@laptop:~$ 
jerry@laptop:~$ 
jerry@laptop:~$ 
jerry@laptop:~$ 
jerry@laptop:~$ uname -r
2.6.24-23-generic
jerry@laptop:~$ 


Recap: My chipset id is:
Bus 004 Device 003: ID 0ace:1215 ZyDAS WLA-54L Wifi
for 2wire 802.11g USB Adapter Model US-G-AT-02 

BTW, on the internet I found the following:

Petr Menšík has made a driver mod to use that chipset
[http://www.nabble.com/tp-link-WN322G-td21524214.html#a22508666](http://www.nabble.com/tp-link-WN322G-td21524214.html#a22508666)

On that link, Petr Menšík wrote:

Hi: thank you for your information, MAXIM_NEW_RF in TP-Link seems to be really uw2453 rf, because i made my model working with uw2453 initialization sequence. I only modified zd_rf.c and added rf type to uw2453.

I am sending tiny patch, you have to be in drivers/net/wireless directory of linux kernel.  I did not rough testing, but i can scan, i can change essid, i can connect to WPA PSK ap with supplicant. Also signal meter seems to report reasonable values. So, i report with patch in my attachment, TP-Link TL-WN422G (i think it is the same device as your TL-WN322G, but this does have RP-SMA connector present, which is reason i bought it), identified as 

Bus 007 Device 013: ID 0ace:1215 ZyDAS WLA-54L WiFi is working. 

I dont know other devices with same RF type, if they can be different or we need different HW initialization, but there is no device in supported table with this RF, so i cannot compare. It does work for me, YMMV.

Petr Mensik 
--------------------------------------------------------------------------------------------------------

---

### Post by issih on 2009-03-14
Whether that patch will do anything depends on if you have actually got that specific variant of the chipset that reports its RF hardware in such a way that the driver is not compiling. The only way to test that is to try to compile the driver from source (for which you will need the linux kernel header files installed, ad there is a good chance that is the only way we can proceed if we want a proper linux module.

First of all though can you try looking at your dmesg output to see if it reports any errors loading firmware.

try runninng:

```

dmesg | grep firmware

```

and:
```
dmesg | grep zd1211
```

and:
```
dmesg | grep zd1215:
```

and post any output that looks interesting.

If that shows nothing we are going to have to either try ndiswrapper or compilation from source.

The latter involves somehow getting internet onto the box in question in order to download the linux headers and the build essential packages (which are required to get anywhere with compilation)

Up to you what to try first

---

### Post by JerryI on 2009-03-14
As I mentioned earlier, I expect to obtain a Belkin USB converter in a week or so.  Thus, it's probably better not to fool with patching and recompiling some unknown driver.  If you think there is a 50:50 chance of getting it going with ndiswrapper, and are willing to help me with that, I would like to give that one last shot.  I really appreciate all your help on this.  Here's the output:

jerry@laptop:~$ dmesg | grep firmware
[   97.628657] zd1211rw 4-3:1.0: firmware version 4725

jerry@laptop:~$ dmesg | grep zd1211
[   26.557819] zd1211rw 4-3:1.0: eth1
[   26.557840] usbcore: registered new interface driver zd1211rw
[   97.628657] zd1211rw 4-3:1.0: firmware version 4725
[   34.446947] zd1211rw 4-3:1.0: zd1211b chip 0ace:1215 v4810 high 00-1e-37 AL2230S_RF pa0 g--N-

jerry@laptop:~$ dmesg | grep zd1215:
jerry@laptop:~$ 
jerry@laptop:~$ dmesg | grep zd1215
jerry@laptop:~$

---

### Post by issih on 2009-03-14
Ok, we'll play with ndiswrapper.
Here is what to try:

1)blacklist the current driver:
open a terminal and enter:
```
sudo gedit /etc/modprobe.d/blacklist
```
enter your login password when prompted and hit enter.

That should open a text editor on a file at the very bottom of that file add the line:
```
blacklist zd1211rw
```

That will stop your current (non functional) driver hijacking the hardware.

2) Install ndigtk:
put the cd, you used to install ubuntu onto the machine, into the cd drive.
Now open up software sources (System->Administration->Software Sources) entering your login password when prompted.
In that dialog tick the box to enable the cd rom as a software source, and apply those settings.

3) Install ndisgtk:
In a terminal run:
```
sudo apt-get install ndisgtk
```

4) Locate the *.inf file:
Find the file from the windows drivers associated with your hardware, that has the file extension ".inf". Basically fish around in the files on the driver cd, and if you are lucky it will be obvious, if not we will need to be  bit more creative.

5) Install the *.inf file:
Open the windows wireless drivers app (its under System somewhere, cant recall if its preferences or admin)
then click to install and select the *.inf file located in step 4

6) Test your wireless.

If that works come and shout about it, and I will tell you how to make sure ndiswrapper is loaded by default at logon.

---

### Post by JerryI on 2009-03-14
Tried and failed.  Got message that the info about available sw is out-of-date and that I need a working internet connection to continue.  Tried to continue but could not.  Can I somehow use this machine that I am typing on to load the stuff onto a usb flash drive?

---

### Post by issih on 2009-03-14
At what point did you get that error?, and can you provide that actual text of the error it spits out?

You might be able to get things to behave be issuing the command: "sudo apt-get update" but I suspect that won't help.

More importantly, have you got a network cable lying around you can temporarily plug the machine into the router with, that is by far the easiest solution.

---

### Post by JerryI on 2009-03-14
Found an ethernet cable and accessed network.  My 2wire cd had a driver directory with a cardbus_xp(64bit) subdirectory with file bcmwl5.inf which would not install (incompatible error)  cardbus_xp32 directory contains only file 2wire_for_xp32_installer.exe which i tried to run, which it would not install because it is not an inf file.

Conclusion: the only inf file on the 2wire cd, for driver bcmwl5 is an invalid driver, acc to Wireless Network Drivers.

On another note, last night I installed VMWare server on the Intrepid partition of my Vista computer (the computer that I cannot get my USB SoundBlaster card to work with), but I cannot find it and run it.  Someone told me it should be in the System Directory of the Applications Directory, but there is no such directory and I cannot find it in any subdirectory of Applications.  Someone else said f2 vmware should make it run, which produced nothing.  Any hints in that regard?  VMWare gave me multiple indications that my installation was fine when I installed it.

Am I butting my head into more dead ends than I should expect with Ubuntu?

---

### Post by issih on 2009-03-14
Assuming you have installed the 32 bit ubuntu we need to hack into that .exe file. 

install cabextract:

```
sudo apt-get install cabextract
```

copy the .exe file from the cd into your home directory, and then rename the file windriver.exe

make a directory in your home directory caled extractedfiles.

open a terminal and enter the following commands in sequence.

```
cd ~
cabextract -d extractedfiles windriver.exe
```

Once that is done there will (hopefully) be a load of files plucked from inside the .exe file within the extracted files directory.

Grab the .inf file from there and try that.


As for your having a lot of issues, this is what you should expect to happen. You are installing an operating system of which you have no knowledge, so there is going to be a steep learning curve. I expect you have never installed an OS before, not even a microsoft one. All operating systems take time to get sorted out after installation, especially when you don't have the appropriate drivers. You are actually learning a great deal by dealing with all these things the way you are having to, for instance if I just tell you that ls is the commonly used terminal abbreviation for list, you can see that lshw is list hardware, lsusb is list usb devices, and plain old ls will list the contents of the current directory

apt-get is the terminal based package manager (synaptic is the gui version), so you now know how to install any package available in the Ubuntu repositories:

You just do "sudo apt-get install <packagename>"

As for programs, they don't get put into standard places, but and its a big useful but, they do get put somewhere in your PATH. The path is a system wide list of places to look for a command when it is entered on the terminal. So just entering the name of the program at the command line and hitting enter will work 99% of the time.

So in a terminal enter:
```

vmware
```
and hit enter and it will launch, it will be tied to that terminal window though, and will die if you close the terminal window. Instead you can hit alt and F2 simultaneously and get the run dialog, from there you still just enter vmware and hit go, the PATH variable will sort it all out.

If you really care where things are installed just open up synaptic package manager and navigate to the installed package in question, in the properties of that package it will tell you where it is installed.

Alternatively jsut typing "locate vmware" in a terminal should give you a pretty good idea.

You have to accept that you are in a foreign land, and you will have to slowly learn the language, don't worry about it, and keep going, it gets easier every day.

Hope that helps

---

### Post by JerryI on 2009-03-14
I set up a directory called Extracts and extracted the 2wire_driver32_64 exe file into Extracts\Disk1 and there were no inf files: only data1.cab, data1.hdr, data2.cab. ikernal.ex_, layout.bin, setup.inx, Setup.exe, and Setup.ini

---

### Post by issih on 2009-03-14
run cabextract on all the .cab files and probably any .exe files while you are at it, see if you can find another .inf file

One quick question though, are you sure this is the driver cd that came with the adapter? as from what we have done I know it is a usb dongle, and cardbus interfaces (which the .exe's you have mentioned proclaim to be for) are a totally different thing.

---

### Post by JerryI on 2009-03-14
It is the driver CD that came with the device.  I see now that I should be fooling around with 2wire_USB_2K.exe, which I will do now.  That will take me a while, and I realize that you are in the wee hours.  I will report my "progress" asap.  Thanks.

---

### Post by JerryI on 2009-03-14
gai@ubuntu:~/Desktop$ sudo cabextract -d ~Extracts 2W*.exe
2WIRE_USB_2K.exe: library not compiled to support large files.
2WIRE_USB_2K.exe: library not compiled to support large files.
Extracting cabinet: 2WIRE_USB_2K.exe
  extracting ~Extracts/Disk1/data1.cab
  extracting ~Extracts/Disk1/data1.hdr
  extracting ~Extracts/Disk1/data2.cab
  extracting ~Extracts/Disk1/ikernel.ex_
  extracting ~Extracts/Disk1/layout.bin
  extracting ~Extracts/Disk1/Setup.exe
  extracting ~Extracts/Disk1/Setup.ini
  extracting ~Extracts/Disk1/setup.inx

All done, no errors.

Aha, I suppose I continue now to cabextract the cabs, right?  I'll try that.

---

### Post by JerryI on 2009-03-14
Obviously, I haven't mastered this command line stuff yet, but I used to know how to do similar stuff in msdos 1.0 or so.  Does the following really mean there are no inf files in data1.cab, or does it mean I don't know what to type yet?


gai@ubuntu:~$ ls Disk1
data1.cab  data2.cab    layout.bin  Setup.ini
data1.hdr  ikernel.ex_  Setup.exe   setup.inx

gai@ubuntu:~$ sudo cabextract Disk1/data1.cab
Disk1/data1.cab: WARNING; found InstallShield header. This is probably an InstallShield file. Use unshield (from the unshield package) to unpack it.
Disk1/data1.cab: no valid cabinets found

All done, errors in processing 1 file(s)
gai@ubuntu:~$

---

### Post by JerryI on 2009-03-14
unshield, if I used it correctly, didn't get rid of the error.  I have a bit of trouble deciphering syntax, but I don't think there's an inf in there, do you?

Syntax:

	unshield [-c COMPONENT] [-d DIRECTORY] [-D LEVEL] [-g GROUP] [-GhlOrV] c|g|l|t|x CABFILE

Options:
	-c COMPONENT  Only list/extract this component
	-d DIRECTORY  Extract files to DIRECTORY
	-D LEVEL      Set debug log level
	                0 - No logging (default)
	                1 - Errors only
	                2 - Errors and warnings
	                3 - Errors, warnings and debug messages
	-g GROUP      Only list/extract this file group
	-h            Show this help message
	-j            Junk paths (do not make directories)
	-L            Make file and directory names lowercase
	-O            Use old compression
	-r            Save raw data (do not decompress)
	-V            Print copyright and version information

Commands:
	c             List components
	g             List file groups
	l             List files
	t             Test files
	x             Extract files

Other:
	CABFILE       The file to list or extract contents of


gai@ubuntu:~$ sudo unshield c Disk1/data1.cab
Cabinet: Disk1/data1.cab
<Data>
<Support>\Engine\Kernel
<Support>\Engine
<Support>\Main Installation\Setup
<Data>\Disk<1>
<Data>\Main App
<Support>\Main Installation\StrTbl
<Support>
<Support>\Main Installation
<Support>\Engine\Log
<Support>\Main Installation\Resource
<Support>\Main Installation\Script
<Support>\Main Installation\RunTime
-------
13 components
gai@ubuntu:~$ sudo cabextract Disk1/data1.cab
Disk1/data1.cab: WARNING; found InstallShield header. This is probably an InstallShield file. Use unshield (from the unshield package) to unpack it.
Disk1/data1.cab: no valid cabinets found

All done, errors in processing 1 file(s)
gai@ubuntu:~$

---

### Post by JerryI on 2009-03-14
VMWare starts by opening a web browser that hangs on this computer.  I have a suspicion that this is because my processor is an AMD64 instead of Intel.  Now that I have my temporary umbilical cord attached to my laptop for internet access I am going to try to load VMWare into the laptop tonight to see if it will run there.  I'm guessing we will have to wait for the Belkin adapter to get wireless running on the laptop.  Thanks for all your help.  If you have any further suggestions, I would really appreciate hearing from you.

---

### Post by issih on 2009-03-15
Urrgh I hate install shield. Go through all the .exe and .cabs fomr what you extract, and actually drop the files into a directory, using either:

cabextract -d directorypath filetoopen

or unshield -d directorypath filetoopen

start from a clean slate and split open the 2wire_USB_2K.exe, then go into the results of that and split open the setup.exe file, and if that hasn't got anything promising try unshield on the cabs.

Unfortunately installshield being used makes this harder, and I admit the last time I did this I cheated and installed wine (MS emulator) and ran the MS installer. I then found the inf file by searching through the files in the virtual c drive.

If you can't find it this way that might be your best bet.

I'm afraid I don't use a virtual machine, so I can't really comment on using vmware..there are lots and lots of people that do though, so make another thread if you can't find the solution by searching the forums.

---

### Post by JerryI on 2009-03-15
I will work on this 'little project' today, i.e., to try to find the inf file via your suggestion.  I will use the computer I am typing on now, i.e, my dual-boot Vista/Intrepid, since it has a full keyboard and two 22-in monitors and I can sit in my desk chair instead of kneeling on the floor tied to a laptop that is tethered to a 6-ft ethernet cable.  Then if I can find the inf file I can transfer it to the laptop with a USB flashdrive.

You might want to explain the wine thing a little better.  Or maybe I wouldn't have to use wine.  Since I have Vista on this computer why would I have to emulate ms?

One more issue (hah):  

The reason I embarked on this roller coaster ride is that I was frustrated by Vista, but I wanted to have functionality to run some MS apps.  At first I tried to 'downgrade' my Vista OS to XP, but I found that virtually impossible because the XP install disk didn't include SATA drivers for my cd and hard disk.  After a couple futile attempts to slipstream the SATA drivers onto an install disk clone, I abandoned that idea.

Now, if I were to manage to install VMware on this computer, I should be able to run a virtual XP machine inside Intrepid (or perhaps inside Hardy which may be a better choice).  But since this computer has SATA drives, I'm anticipating that I might not be able to install any of my apps via CD/DVD from within the virtual XP box.  

My question is this.  Is it possible to bypass the cd drive and install an app  by creating a virtual drive, so to speak?  I know that I installed Hardy on the laptop w/o burning a Ubuntu install CD, i.e., by downloading the iso file to a 2GB flashdrive or something.  So it would seem that I should be able to create something to emulate the cd drive and install software within the XP virtual box w/o using the physical CD during the install operation inside the XP virtual box.

I realize that I still have several hurdles before I might get to that point, but is the plan conceivably viable, i.e., have a machine that will run a couple ms apps without going through Vista?

---

### Post by JerryI on 2009-03-15
No Luck.  Now can you tell me an efficient way to remove all these useless directories and files without rm removing one file at a time and rmdir one empty directory at a time from the bottom up?  The pascal option doesn't seem to remove a directory with files in it.


gai@ubuntu:~/working$ ls
2k  xp3264

gai@ubuntu:~/working/xp3264$ ls
data1.cab  data2.cab  Setup.exe

gai@ubuntu:~/working/xp3264$ sudo cabextract data1.cab
[sudo] password for gai: 
data1.cab: WARNING; found InstallShield header. This is probably an InstallShield file. Use unshield (from the unshield package) to unpack it.
data1.cab: no valid cabinets found

All done, errors in processing 1 file(s)

gai@ubuntu:~/working/xp3264$ sudo cabextract data2.cab
data2.cab: WARNING; found InstallShield header. This is probably an InstallShield file. Use unshield (from the unshield package) to unpack it.
data2.cab: no valid cabinets found

All done, errors in processing 1 file(s)

gai@ubuntu:~/working/xp3264$ sudo cabextract Setup.exe
Setup.exe: no valid cabinets found

All done, errors in processing 1 file(s)

gai@ubuntu:~/working/xp3264$ sudo unshield c Setup.exe
Failed to open Setup.exe as an InstallShield Cabinet File

gai@ubuntu:~/working/xp3264$ sudo unshield c data1.cab
Failed to open data1.cab as an InstallShield Cabinet File

gai@ubuntu:~/working/xp3264$ sudo unshield c data2.cab
Failed to open data2.cab as an InstallShield Cabinet File

gai@ubuntu:~/working/2k$ ls
data1.cab  data2.cab  Setup.exe

gai@ubuntu:~/working/2k$ sudo unshield c data1.cab
Failed to open data1.cab as an InstallShield Cabinet File

gai@ubuntu:~/working/2k$ sudo unshield c data2.cab
Failed to open data2.cab as an InstallShield Cabinet File

gai@ubuntu:~/working/2k$ sudo unshield c Setup.exe
Failed to open Setup.exe as an InstallShield Cabinet File

gai@ubuntu:~/working/2k$ sudo cabextract Setup.exe
Setup.exe: no valid cabinets found

All done, errors in processing 1 file(s)

gai@ubuntu:~/working/2k$ sudo cabextract data1.cab
data1.cab: WARNING; found InstallShield header. This is probably an InstallShield file. Use unshield (from the unshield package) to unpack it.
data1.cab: no valid cabinets found

All done, errors in processing 1 file(s)

gai@ubuntu:~/working/2k$ sudo cabextract Setup.exe
Setup.exe: no valid cabinets found

All done, errors in processing 1 file(s)

---

### Post by issih on 2009-03-15
rm -r is recursive, i.e. it will drill down into files and subdirectories, it will however ask if you mean to delete each file in turn. you can also add a -f flag for force which will then do it without asking, but be VERY VERY careful as using rm -r with the -f will delete things permanently and irretrievably all the way down the directory structure from the directory you specify as the start point. It is the cause of much anguish as you can imagine.

Alternatively just use the gui file manager and select more than one file, i.e. use ctrl and click or shift and click

I know nothing about VM's sorry, can't comment..

The reason I used wine to find the inf file is that the virtual c drive of wine is almost empty, certainly in comparrison to a windows installation. Therefore finding the file was a much less arduous task.

There isn't much for it at this point other than to install wine and try running the exe file..if you can find the inf file after that then al well and good, other than that the only hope is searching the internet.

---

