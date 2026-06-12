---
title: "3DSP Wireless 802.11 b+g USB Adapter"
date: 2012-02-07
forum: Networking &amp; Wireless
---

### Post by jkokky on 2012-02-07
Hello everybody and thank you for your help in advanced!

I have a mini netbook "TurboX" 10.1'' that has the 3DSP Wireless 802.11 B+G USB Adapter. My Ubuntu 10.04 installation does not recognize nor see my wireless adapter. I've tried downloading and installing the wireless drivers but no matter what version of the Ubuntu 10.04 drivers I run I keep getting the same message after the execution of the Install_3DSPUSB.sh file!

 * Checking user...                                     [ Ok ]
 * Verifying kernel...                                  [Fail]
Notice: The kernel "2.6.32-38-generic" is NOT supported by this package.
Exit.

I don't have any problems with wireless networking using the windows OS. Can anyone help me out by guiding me through? I new in the Linux Community so I'm in a beginners' level with such an OS.

Thank you again for your help and time!

---

### Post by SLI-X on 2012-03-05
Hi Mate,

I too have the same issue with my tablet, file I am trying to install is:
BlueW-2310U_2.4.4_100823_Ubuntu10.04_withouthotkey

and heres what I get when trying install it:

* Checking user... [ Ok ]
* Verifying kernel... [Fail]
Notice: The kernel "3.2.6" is NOT supported by this package.
Exit. 

have tried many attemps I did how ever see somwhere that installing this software ndisgtk_0.8.5-1 in your linux distro will allow to install windows drivers but you will need the raw driver files not the installation exe. In those files you will have a .inf file and this is the file you browse for in the ndisgtk_0.8.5-1

I havnt got this far as I am a noob with linux but please if you manage to install it please tell me how.

Also whats the difference between
 BlueW-2310U_2.4.4_100823_Ubuntu10.04_withouthotkey
&
 BlueW-2310U_2.4.4_100823_Ubuntu10.04_withhotkey 

because talks about these 2 types in the readme in the tar.gz file

I hope this helps

---

### Post by SLI-X on 2012-03-06
[B][SIZE=2]Saw this and this might help need to get hold of the .inf files again though which I can t find[/SIZE]
[/B]
**3.4. Installing Windows driver**

  
**3.4.1. Installing Windows driver using ndisgtk (ndiswrapper graphical interface)**

 
[LIST]
[*]If you chose to install ndisgtk, the graphical interface for ndiswrapper, after installation click on **System** | **Administration** | **Windows wireless drivers** and follow the instructions on-screen. For an idea of what to expect, some screenshots of ndisgtk can be found [here]("http://lxer.com/module/newswire/view/46385/"). 
If this works, and you have a network connection, then you can skip to [Automatically loading at Startup]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#autostart") - ndisgtk will load the driver if it installs correctly. 
[/LIST]
 
**3.4.2. Installing Windows driver using command line**

 In a Terminal, run the following command: 

sudo ndiswrapper -i ~/drivers/drivername.inf

(assuming the driver is in a directory in your home folder called drivers, and is named drivername.inf) 
ndiswrapper then copies the .inf and sys files into /etc/ndiswrapper/.... Don't forget that the filename you type in is case-sensitive. 
 
**3.4.2.1. Check to make sure the driver was installed correctly**

 Run the following command from a Terminal:

ndiswrapper -l

If the driver is installed correctly, you should see the following output: 

Installed ndis drivers:   {name of driver} driver present, hardware present

or 

{name of driver} : driver installed        device ({Chipset ID}) present

If you don't see this message: 
[LIST=1]
[*]Try a different driver such as the drivers for Windows 2000, or another driver matching the PCI ID on the [ndiswrapper list]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List"). 
[*]This document has a [troubleshooting]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#trouble") section which may provide an answer. 
[*]Look for additional help. Read [HowToGetHelp]("https://help.ubuntu.com/community/HowToGetHelp") for more information. 
[/LIST]
 
**3.5. Load the new driver module**

 If  ndiswrapper correctly associates the driver to the wireless adapter,  you are now ready to load the driver into memory, and try to establish a  network connection. 

Open a Terminal and run the following commands:

sudo depmod -a   sudo modprobe ndiswrapper

Then, also in a Terminal, check for error messages: 

tail /var/log/messages

Alternatively, open a Terminal and try the commands ip addr and iwconfig. Your wireless card should appear with an interface name of *wlan0*. 
If it doesn't appear here, then the driver is not working properly. If no errors are given, you should now be able to configure the network connection.

---

