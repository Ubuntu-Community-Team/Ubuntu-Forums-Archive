---
title: "Setting up ADSL Model"
date: 2006-06-10
forum: Networking &amp; Wireless
---

### Post by rajarshi on 2006-06-10
Hi,

I'm completely new to Linux. I've been with MSWin all along. Some months back, I was introduced to Opensource and Linux. I've been slowly transitioning to opensource ever after. As a final step, I'd downloaded a Live CD of Ubuntu. Now, I'm having trouble getting my modem to work. What's amazing is no matter how much I google the problem, all I get are pages and pages of instructions on how to get the darned thing done through command line. Isn't there a simpler way to do it through the GUI? My modem is branded Beetel 100CX. On my windows system, the software reads Conexant AccessRunner.

I really am disillusioned. Is it nowhere possible to get linux working without reading stacks of geeky books? How is linux better? On my copy of XP, all I needed to do was connect the USB cable, the system detected it, and installed all the necessary drivers. Isn't there are similar process for Ubuntu? How on earth is Linux better than XP otherwise? As I see it, for a successful transition, all one needs is the ability to get connected to the net - thereafter, everything can be searched and figured out. I suppose it's back to XP for me unless I get a truly dumbed down walk-through for all this.

Truly Disillusioned,

Rishi

---

### Post by pnael on 2006-06-10
Well on one side you have an already installed Windows Xp fully supported by loads of hardware manufacturers, on the other side a non installed Linux system with much less support from hardware manufacturers !!!

If you want to invest time learning a new system go to Linux, if you don't want, stay with Windows XP if it suits you. 

For your problem, i can't help a lot. Check if the manufactuer provides a linux driver. If this modem has an ethernet interface it is easier to setup (does not
need nay driver) : sudo pppoeconf

---

### Post by RRS on 2006-06-10
The primary GUI interfaces for network setups are;
System>Administration>Networking and Networking Tools

USB modems seem to be a particular problem with Linux (as compared to ethernet cable) I haven't worked with one so can't help you myself but you might try searching the networking section of these forums, someone elses solution may also be yours.

> Is it nowhere possible to get linux working without reading stacks of geeky books?  
Hate geeky books myself, these forums are far better for finding answers to specific questions, often in a decidedly non-geeky manor.

Though a lot things seem to "just work" in windows, remember, usually it was the computer mfg who installed and set everything up for you, thats part of what your purchase price paid for.

> .........pages of instructions on how to get the darned thing done through command line.

Actually command line instructions are easier then GUI, "type blah, blah, blah, and 'enter' " instead of "click here, then move mouse to.... and right click, then...." and so on.

Also with time you'll discover that the command line provides a very powerful tool unavailable in windows to make changes (and repairs). Even for simple tasks, a couple words typed in will accomplish the same thing as several mouseclicks.

Sorry to divert from your original problem, here's a suggestion till you get internet access from Ubuntu;

In windows create a plain text document in a folder where it'll be easy to find. Then copy any instructions, hints, etc you find here and elsewhere. Using the directions from [this site]("http://www.psychocats.net/ubuntu/mountwindows.php") and/or [this one]("http://easylinux.info/wiki/Ubuntu#Windows") you'll be able access this file from Ubuntu and make use of any directions and hints you've saved. You'll be able to copy and paste from the file for command line entries without worry of typo's.

I hope I've given you some helpfull info and encouragement. I also got involved with Ubuntu from my discovery of the open source world thru windows applications

---

### Post by kagashe on 2006-06-10
[QUOTE=rajarshi]Hi,

I'm completely new to Linux. I've been with MSWin all along. Some months back, I was introduced to Opensource and Linux. I've been slowly transitioning to opensource ever after. As a final step, I'd downloaded a Live CD of Ubuntu. Now, I'm having trouble getting my modem to work. What's amazing is no matter how much I google the problem, all I get are pages and pages of instructions on how to get the darned thing done through command line. Isn't there a simpler way to do it through the GUI? My modem is branded Beetel 100CX. On my windows system, the software reads Conexant AccessRunner.

I really am disillusioned. Is it nowhere possible to get linux working without reading stacks of geeky books? How is linux better? On my copy of XP, all I needed to do was connect the USB cable, the system detected it, and installed all the necessary drivers. Isn't there are similar process for Ubuntu? How on earth is Linux better than XP otherwise? As I see it, for a successful transition, all one needs is the ability to get connected to the net - thereafter, everything can be searched and figured out. I suppose it's back to XP for me unless I get a truly dumbed down walk-through for all this.

Truly Disillusioned,

Rishi[/QUOTE]

Hi Rishi,

Your name and "Beetel" suggests you are from India and you are using Broadband service other than BSNL/MTNL and it may be Airtel.

Did you buy this modem or is it given on monthly rent by the ISP?

If it is on monthly rent demand the Linux driver and support from the ISP.

If you bought it then you should have checked Linux compatibility before buying and to make it work on Linux you really need to learn things. Since you mentioned "Conexant AccessRunner" here is a site which may be useful.
[URL="http://accessrunner.sourceforge.net/index.shtml"]http://accessrunner.sourceforge.net/index.shtml
[/URL]

Please don't blame Linux and Linux users community for such things. Most Hardware manufacturers market the products with Windows drivers only and the Linux community tries to make it work on Linux. If you want to use Linux check before you buy any hardware.

Change the ISP if the hardware is provided by them or replace the modem. There are so many ADSL modems (including USB) supplied by MTNL/BSNL which are working on Ubuntu "out of the box".

kagashe

---

### Post by rajarshi on 2006-06-11
Hi,

You are right. I'm from Gurgaon, India. I've an airtel broadband connection. I did call up the ISP for help, but they told me that a USB modem cannot be run on any Linux distro - that I know is not true, but I can't really ask them much after that. What they did suggest is that I use a card instead of a modem, which would not require any extra  drivers. 

As you suggest, I perhaps will have to change my ISP. 

I'm not really blaming the Linux community for any of this - just am a little frustrated at not getting any help from the ISP. Something HAS to be done about that!

Thanks,

Rishi

---

### Post by kagashe on 2006-06-11
[QUOTE=rajarshi]Hi,

You are right. I'm from Gurgaon, India. I've an airtel broadband connection. I did call up the ISP for help, but they told me that a USB modem cannot be run on any Linux distro - that I know is not true, but I can't really ask them much after that. What they did suggest is that I use a card instead of a modem, which would not require any extra  drivers. 

As you suggest, I perhaps will have to change my ISP. 

I'm not really blaming the Linux community for any of this - just am a little frustrated at not getting any help from the ISP. Something HAS to be done about that!

Thanks,

Rishi[/QUOTE]I could have helped you but I am out of Delhi at prsent and would reach by June end. But let me try to help now.

You said you have Ubuntu Live CD so it must be Breezy or Dapper. Put the CD in the drive and boot in Ubuntu. Then click on System/Administration/Networking. You will see following connections:
Ethernet Connection (eth0)
Modem Connection (ppp0)

Click on "Ok" or "Cancel" to exit.

Now plug-in your modem in the USB port and switch its power on. After waiting for a few seconds click on System/Administration/Networking once again. If Ubuntu has driver for your USB modem (believe me it has drivers for many including one I have) you will see another connection.
Ethernet Connection (eth1)
Ethernet Connection (eth0)
Modem Connection (ppp0)

If you see a new connection (e.g. eth1) then the driver is already loaded. If you don't then you have to search for the driver and ask for help on the site I recommended earlier.

Whatever is the result please post here.

kagashe

---

### Post by jvictor on 2006-06-11
Hi there, ask if airtel can give you a DSL 502-T router , I use one of those and it works with a lil push here and there, during set up ;) Basically DHCP is flimsy

---

### Post by eX0r on 2006-06-11
I've successfully compiled the drivers for and got on the net with my Conexant Accessrunner PCI ADSL modem in Dapper. Shouldn't be too difficult to get the USB version working.

Have you been to [http://accessrunner.sourceforge.net](http://accessrunner.sourceforge.net)  ?

It took lots of reading of conflicting information, hacking some source files and much pulling of hair to make it work.  I am currently working on a "one click" setup script so that others don't have to go through this hell. :-)

---

### Post by Malac on 2006-06-13
Here is a walkthrough for a UK Zoom 5510 USB Modem, it uses the Connexant Chipset so the process should work with yours.
[http://www.ubuntuforums.org/showthread.php?t=194237](http://www.ubuntuforums.org/showthread.php?t=194237)

Let me know if it does.

Hope this helps.

---

### Post by lokeshwer on 2006-07-04
follow this link
[http://rajeshjayaprakash.in/conexant.html](http://rajeshjayaprakash.in/conexant.html)
Never blame linux

---

### Post by Evilgenius on 2006-07-07
> **eX0r said:**
> I've successfully compiled the drivers for and got on the net with my Conexant Accessrunner PCI ADSL modem in Dapper. Shouldn't be too difficult to get the USB version working.

Have you been to [http://accessrunner.sourceforge.net](http://accessrunner.sourceforge.net)  ?

It took lots of reading of conflicting information, hacking some source files and much pulling of hair to make it work.  I am currently working on a "one click" setup script so that others don't have to go through this hell. :-)


is there any chance you could share that file, id like to get my pci adsl modem running too :)

---

### Post by johnnymac75 on 2006-07-30
Hi, 

I have an E-Tech USB ADSL modem (base on Conexant AccessRunner chipset) that I've been using regularly on Ubuntu for some time now. 

The driver is already included in Ubuntu since version 6.06 LTS (and is pretty good), the only missing part is the firmware, which must be loaded when the modem USB cable is plugged in. The [Wiki documentation]("https://help.ubuntu.com/community/UsbAdslModem/AccessRunner") explains all the instructions to install it.

Once this is done, the light on the modem should stop blinking and remain on. We can now configure the ppp connection. 
Here are the steps that worked for me: 

[LIST=1]
[*]Add a configuration file for your ISP in /etc/ppp/peers. The file name should help you identify the connection and is usually named as your ISP (e.g.: myprovider). I have attached a template based on the file I'm using. 

[*]Add your username and password in /etc/ppp/pap-secrets and/or /etc/ppp/chap-secrets

[*]```
pon <myprovider>
``` to connect

[*]```
poff <myprovider>
``` to disconnect
[/LIST]

I hope this can help you. And I would be glad to hear if there's a more user-friendly way to configure and start/stop USB ADSL connections.

---

