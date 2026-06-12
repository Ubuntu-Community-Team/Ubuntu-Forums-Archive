---
title: "Wireless card - belkin, hp laptop"
date: 2009-08-06
forum: Networking &amp; Wireless
---

### Post by cbia on 2009-08-06
I am having problems having ubuntu recognize my wireless card. I am a complete noob when it comes to this OS. I did successfully install on my desktop last night without an issue.

Here are my specs:
Laptop:
hp pavilion ze4600 (ze4610us)
amd athlon xp-m

card:
Belkin wireless g plus notebook card - p81989-a


Everything was working fine in Windows XP.

Thanks.

---

### Post by wojox on 2009-08-06
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

---

### Post by cbia on 2009-08-06
brian@brian-laptop:~$ sudo apt-get install wireless-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wireless-tools is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
brian@brian-laptop:~$ lspci | grep Network
brian@brian-laptop:~$ lspci | grep Network
brian@brian-laptop:~$ 


I got to here. i guess I need to know the chipset of he card, but it is not telling me. An advice?

---

### Post by MaindotC on 2009-08-06
It looks like a PCMCIA card not a PCI card.  Use the following in place of "lspci":
```

sudo lspcmcia

```

---

### Post by cbia on 2009-08-06
Thanks in advance:

brian@brian-laptop:~$ sudo lspcmcia
[sudo] password for brian: 
Socket 0 Bridge:       [yenta_cardbus]     (bus ID: 0000:00:0a.0)
brian@brian-laptop:~$ lspcmcia | grep Network
brian@brian-laptop:~$ 

Mind if i ask what next?

---

### Post by cbia on 2009-08-06
Or how about: is there a usb wifi connector out there will will install without too much hassle?

---

### Post by Buuntu on 2009-08-06
Ndiswrapper helps install wireless cards that aren't compatible with Linux. 
 
Try this:
 
```
 
sudo apt-get install ndisgtk

```
 
Then you need to find and download the windows drivers for your card.  Once that is done, run:
 
```
 
sudo ndiswrapper -i ~/drivers/drivername.inf

```
 
Replace the filelocation to where the .inf file is in the driver you downloaded.  Usually it will be something like /WinXP/drivers/drivername.inf or something.  Next is:
 
```
 
sudo depmod -a
sudo modprobe ndiswrapper

```
 
Then that's it.  If network manager doesn't see your wireless network, you might have to add it on your own.  Just add a new wireless network, and enter the SSID.  SSID is the name of the network.  For example, mine is linksys.
 
This site explains everything in greater detail: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by cbia on 2009-08-06
Thanks.

I found the driver but it is in .exe format. I can extract some or all (there are only 2 .inf files - 1 is autorun.inf so I take it that one isn't it). After I extract it, where do I put it?

Also, FYI, when running in windows it uses its own belkin software to access wireless.

---

### Post by cbia on 2009-08-06
I tried to install both .inf files. The one said installing netani.inf... Then back to the prompt. The next wouldn't install or said it was incomplete (autorun.inf). ??? no idea.

---

### Post by skovy on 2009-08-06
i am having problems also with my belkin wireless n usb, but i think you have done something wrong, linux cant run .exe files.  you need to find the .inf alone.  and copy that to another folder, along with the .sys file, once you have those loaded into ndiswrapper, it should notice your hardware.  after that i have no idea, i keep getting 

all config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release?

i opened text editor, but there was a huge list that listed several things over and over, in different languages, i have never compiled code before and have no idea what im looking at, if someone could direct me to where i can find information on what i need to do next that would be wonderful.

---

### Post by Buuntu on 2009-08-06
cbia:
 
Extract the whole file you downloaded, not just the .inf file.  You can either put the .inf, .sys, and .bin files in a seperate folder, or you can just run it in the folder it is already in (much easier), once you have extracted the whole thing.  
 
skovy:
 
```
 
all config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release?


```
 
 That is just a warning, it is not actually affecting it from being run as of yet.  To avoid future problems though, you might want to change ndiswrapper to ndiswrapper.conf.  You do not have to open it in a text editor, just change the file name.  Once that is done, the error should go away.

---

### Post by cbia on 2009-08-07
Got it extracted to a "drivers" folder in home. Then went to prompt and typed everything in, and it is still not working.

If this doesn't work, does anyone know of a usb wifi connector that will plug-n-play or work with minimal prompt work?

---

