---
title: "Pavilion dv1000"
date: 2005-12-14
forum: Networking &amp; Wireless
---

### Post by AtlantisDuelist on 2005-12-14
hi, I have a major problem, I use HP Pavilion dv1000 and I really like ubuntu, but I am just getting into Linux, and I want to use my Wireless NIC card (Broadcom Corp BCM4306 802.11b/g) it's built in. and I went to this website ([https://wiki.ubuntu.com//SetupNdiswrapperHowto](https://wiki.ubuntu.com//SetupNdiswrapperHowto)) that I got to step Seven and that step six was supposed to make 2 files and I only have one. is there someway that I can get modules for 2.6.12-9-386? that is ndiswrapper 1.7 or whatever, and then I can update wirelessly.

Thanks in Advance

---

### Post by quietglow on 2005-12-14
Yeah, that howto is way overdone--perhaps because the package wasn't available in Hoary, I dunno. Its much simpler now, though you'll HAVE to have both the driver files: I believe there is a .ini and .sys files. I spent a LONG time figuring that out.

1. Put those files somewhere in a folder, go to that folder in a terminal.
2. Open the package manager: System>Administration>SYnaptics. Search for ndiswrapper and install the ndiswrapper-utils. 
3. In your terminal window (where the drivers are) give this command:

```
sudo ndiswrapper -i bcmw15.inf
```

You shouldn't get any errors here. If so, you may have the wrong driver. Get the one from the CD which came with your machine. There are about 5 floating around on the web and not all work.

4. next give this command: ```
sudo modprobe ndiswrapper
```

Your wireless light should light up and the card should be active. On to setting up networking.

---

### Post by AtlantisDuelist on 2005-12-14
"you'll HAVE to have both the driver files: I believe there is a .ini and .sys files." which two files do I have to have? cause I have the tar.gz file, and the .deb file

---

### Post by Lambert on 2005-12-14
The link in my signature for ndiswrapper is a littler simpler/cleaner also if you need. There are links there to the ndiswrapper wiki with some help.

One of the main things is to pay attention to what driver you're using and make sure you include all files such as .inf .sys and sometimes .bin. The way they are written sometimes they link to each other so they need to be present on your harddrive in the same folder. 
Sometimes the drivers on the cd work, sometimes they don't. There are instructions in the link below to make sure you get a correct driver. If those don't lead you anywhere, try the ones on the cd.

---

### Post by quietglow on 2005-12-14
Yep, that howto is much better (than mine for sure!). The key really is getting the right driver. Get familiar with the ndiswrapper driver UNloading command. I had a DV1000 when I was still dual booting and I copied the drivers from my windoze setup--the ones on my HP install disk wouldn't work.

---

### Post by AtlantisDuelist on 2005-12-14
let me get this straight, since the computer I have this (ubuntu) is on my leg (yes, I have a big leg) I install the two links cause I have a internet access I download two files, and then I don't use my CD, but it's a working CD, 

this is the part that confuses me: Important: Do NOT use drivers on your CD. They may work, but you may experience kernel crashes etc., if the driver on your CD has not been tested. Instead, you need to download appropriate Windows XP driver for your card from the Wiki entry List. To identify the driver that you need, first identify the card you have with 'lspci' and note the first column such as 0000:00:0c.0 and then find out the PCI ID of the card that with 'lspci -n' corresponding to the first column of 'lspci' output. The PCI ID is third column or fourth in some distributions and of the form '104c:8400'. Now you need to get the Windows driver for this chipset. In the  list, find out an entry for the same PCI ID and download the driver corresponding to it (don't worry if the link is not under your exact card as many cards you the same chipsets). Unpack the Windows driver with unzip/cabextract/unshield tools and find the INF file (.INF or .inf extension) and the SYS file (.SYS or .sys extension). (this is important as some drivers have a connection with the .sys file which makes the driver work properly) If there are multiple INF/SYS files, you may look in the  List if there are any hints about which of them should be used. Make sure the INF file, SYS file and any BIN files for example, TI drivers use BIN firmware files are all in one directory on your harddrive. 

now don't get me wrong I know the command how to find out: it says 0000:02:06.0 Network Controller: Broadcom Corporation BCM 802.11b/g... do I plug that it with this? "note the first column such as 0000:00:0c.0 "

---

### Post by AtlantisDuelist on 2005-12-14
sudo dpkg -i ndiswrapper-utils_1.1-4ubuntu2_i386.deb

that command... I get error processing commands.

edit: neither does the other one

---

### Post by AtlantisDuelist on 2005-12-14
so do I use the Window OS disk to get my supplement of drivers?

---

### Post by Lambert on 2005-12-15
> sudo dpkg -i ndiswrapper-utils_1.1-4ubuntu2_i386.deb

that command... I get error processing commands.

edit: neither does the other one

When you run the command are you in the folder where the .deb file is? Or use the full path to the file. example.

sudo dpkg -i /home/name/downloads/ndiswr......deb

> so do I use the Window OS disk to get my supplement of drivers?

You can try the drivers on the disk. They usually work, but sometimes the drivers have a change made to them where they won't work with ndiswrapper. Just make sure you have all the files under the driver folder for the specific os folder copied to your drive. (that is there may be a driver folder for winxp and a folder for win2k. don't copy all drivers to your drive, just the ones in the winxp folder) If you do have seperate folders for winxp and win2k drivers on the disk, if the ones for winxp don't work, then remove those and try again with the win2k ones.

If you use a driver from the ndiswrapper wiki list that matches the chipset pciid, it's a known driver that works.

Hope this didn't confuse you more.

---

