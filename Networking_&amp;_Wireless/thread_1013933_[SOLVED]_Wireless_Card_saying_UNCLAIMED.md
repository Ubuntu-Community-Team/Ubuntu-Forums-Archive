---
title: "[SOLVED] Wireless Card saying UNCLAIMED"
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by trendyabinash on 2008-12-17
Sir I have a wireless card I use it to connect to net, It is not working by default so I searched for and found this on help.ubuntu.com

```
trendyabinash@abinash-desktop:~$ sudo lshw -C network
[sudo] password for trendyabinash: 
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 1
       bus info: pci@0000:05:01.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32

```

In this [How to install windows drivers]("https://help.ubuntu.com/8.10/internet/C/ndiswrapper.html")site it is asking for .inf file but I have an exe file as it's driver, how will I get the .inf file???

PLEASE HELP ME ITS URGENT

---

### Post by Ayuthia on 2008-12-17
You might first try to extract the .exe file by doing:
```
unzip file.exe
```Replace file with the name of the .exe file.  If that does not work and you have a working internet connection in Ubuntu, you can install cabextract.```

sudo apt-get install cabextract
cabextract file.exe
```

In some cases, the .exe file contains the .inf inside of it.  So either unzip or cabextract could help extract the file.  Hope that helps.

---

### Post by trendyabinash on 2008-12-17
Thanks for replying so fast I needed it.

here is the results which I have obtained
```
trendyabinash@abinash-desktop:~$ cabextract setup.exe
setup.exe: no valid cabinets found

All done, errors in processing 1 file(s)
trendyabinash@abinash-desktop:~$ unzip setup.exe
Archive:  setup.exe
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  setup.exe may be a plain executable, not an archive
unzip:  cannot find zipfile directory in one of setup.exe or
        setup.exe.zip, and cannot find setup.exe.ZIP, period.

```

---

### Post by Ayuthia on 2008-12-17
Sorry.  I did not realize that it was the setup.exe file.  Here is a link that might help:
[http://ubuntuforums.org/showthread.php?t=374167](http://ubuntuforums.org/showthread.php?t=374167)

It points to another link that has instructions on how to get your card working.  Hope it helps.

EDIT:
You can most likely use the newer version of ndiswrapper that is in the repository.  If you have not done it already, you can install the ndiswrapper-utils-1.9 package.

---

### Post by trendyabinash on 2008-12-17
thanks sir But it is quite complicated for me. Don't I have any other choices??

---

### Post by Ayuthia on 2008-12-17
You don't really need those instructions.  You just need the driver from there.  Download this file:
[http://downloads.trendnet.com/TEW-421PC_b1%5CDriver%5CUtility_Driver_TEW-421PC_423PI_b1_2.00.zip](http://downloads.trendnet.com/TEW-421PC_b1%5CDriver%5CUtility_Driver_TEW-421PC_423PI_b1_2.00.zip)

If you have not done so already, install ndiswrapper:
```
sudo apt-get install ndiswrapper-utils-1.9
```

I am assuming that you have not installed any drivers yet.  If that is the case, you will need to extract the file in the link above:
```
unzip TEW-421PC_b1\\Driver\\Utility_Driver_TEW-421PC_423PI_b1_2.00.zip 
```

Then go into the directory where the driver is located:
```
cd Drivers/Windows\ XP/
```

Install the driver:
```
sudo ndiswrapper -i Mrv8000c.INF 
```

Make sure that the driver is installed:
```
ndiswrapper -l
```It should show that the driver is installed and the hardware is present.  If it is there, do the following:
```
sudo ndiswrapper -ma
sudo modprobe ndiswrapper
```

If you are able to connect, add ndiswrapper to the list of modules to load:
```
cat ndiswrapper | sudo tee -a /etc/modules
```

---

### Post by trendyabinash on 2008-12-17
I found that my device can work using ndiswrapper but I am not able to find the .inf file for it's installation I found the ,sys file though. But ndiswrapper is stating not a valid .inf file.

Please help

---

### Post by trendyabinash on 2008-12-17
> **Ayuthia said:**
> You don't really need those instructions.  You just need the driver from there.  Download this file:
[http://downloads.trendnet.com/TEW-421PC_b1%5CDriver%5CUtility_Driver_TEW-421PC_423PI_b1_2.00.zip](http://downloads.trendnet.com/TEW-421PC_b1%5CDriver%5CUtility_Driver_TEW-421PC_423PI_b1_2.00.zip)

If you have not done so already, install ndiswrapper:
```
sudo apt-get install ndiswrapper-utils-1.9
```

I am assuming that you have not installed any drivers yet.  If that is the case, you will need to extract the file in the link above:
```
unzip TEW-421PC_b1\\Driver\\Utility_Driver_TEW-421PC_423PI_b1_2.00.zip 
```

Then go into the directory where the driver is located:
```
cd Drivers/Windows\ XP/
```

Install the driver:
```
sudo ndiswrapper -i Mrv8000c.INF 
```

Make sure that the driver is installed:
```
ndiswrapper -l
```It should show that the driver is installed and the hardware is present.  If it is there, do the following:
```
sudo ndiswrapper -ma
sudo modprobe ndiswrapper
```

If you are able to connect, add ndiswrapper to the list of modules to load:
```
cat ndiswrapper | sudo tee -a /etc/modules
```
Thank you sir for your support, but before rechecking the forum I was searching the net for how tos and I found the site from where I can download my driver files
I downloaded them and used ndisgtk to install them and NOW I am UP and RUNNING.
I used the following steps to install my device drivers
I first installed ndisgtk from synaptic package manager
then I opened the terminal and typed "lspci", it showed a list, I recorded the number infront of my device and then typed "lspci -n" I found my device ID and searched for the required .inf in google and found it in the following site
[http://lonehacks.blogspot.com/2008/03/marvell-technology-group-ltd-88w8335.html](http://lonehacks.blogspot.com/2008/03/marvell-technology-group-ltd-88w8335.html)

I downloaded them put them in a folder and used system-->Administration-->Windows Wireless Drivers to install it.
And it was done.

Thank you a lot. I love ubuntu community

---

### Post by albinootje on 2008-12-18
> **trendyabinash said:**
> 
I downloaded them and used ndisgtk to install them and NOW I am UP and RUNNING.
I used the following steps to install my device drivers
I first installed ndisgtk from synaptic package manager
then I opened the terminal and typed "lspci", it showed a list, I recorded the number infront of my device and then typed "lspci -n" I found my device ID and searched for the required .inf in google and found it in the following site
[http://lonehacks.blogspot.com/2008/03/marvell-technology-group-ltd-88w8335.html](http://lonehacks.blogspot.com/2008/03/marvell-technology-group-ltd-88w8335.html)

I downloaded them put them in a folder and used system-->Administration-->Windows Wireless Drivers to install it.
And it was done.

Thank you a lot. I love ubuntu community

Awesome. Well done! :)

---

