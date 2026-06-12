---
title: "How to install drivers"
date: 2012-04-30
forum: Networking &amp; Wireless
---

### Post by jbocean on 2012-04-30
I have an older Dell Dimension 4550 on which I did a fresh install of 12.04 from 10.04. My wireless used to work fine.

No Proprietary Drviers were detected
So I found and downloaded the driver and extracted (is this the correct term?) it in Downloads folder. I don't know what to do next. Ubuntu is of no use to me if I can't get wireless going

This is what I see in my Downloads folder.

/home/john/Downloads/WUSB300N_20071204
/home/john/Downloads/WUSB300N_20071204.exe
/home/john/Downloads/setup.exe

---

### Post by mörgæs on 2012-04-30
Did you have wired internet access while installing, and did you add all updates? 

Which network card do you have?

By the way, it's an older computer so Lubuntu might be a better choice.

---

### Post by TBABill on 2012-04-30
To find out which wireless device you have, including it's system ID, open a terminal and enter ```
lspci
```That will give you a rundown of all your PCI devices in the system. If you paste the pertinent part to your wireless we can give you a hand. 
 
If you want to limit your results to only wireless, you can instead use ```
lspci | grep Network

```

---

### Post by jbocean on 2012-04-30
Thank-You TBABill & Morages for responding. 

Yes, I did have wired internet connected and I did check the boxes for installing propriety drivers and software updates when I did the install. 

I will have to check which card-type on a terminal after work and get back to you. 

I did download the driver for the WUSB-300N driver adapter. 
But I am confused about what to do w/ the files that are in my download folder. I don't understand what Archive Manager means and what I need to do to install the drivers which I downloaded. 

fyi TBAbill, noticed that you are from Maryland ... i grew up in Maryland.

Thanks Again.
jbocean

---

### Post by jbocean on 2012-04-30
Me again,
I noticed I forgot to mention its a 
_LINKSYS_ WUSB-300N adapter.

---

### Post by TBABill on 2012-04-30
I love living in MD. Didn't grow up here, but glad I'm here now :)
 
Maybe this can help: [http://foofooey.wordpress.com/2011/01/02/linksys-wusb300n-tar-download-ubuntu-linux-drivers/](http://foofooey.wordpress.com/2011/01/02/linksys-wusb300n-tar-download-ubuntu-linux-drivers/)

---

### Post by jbocean on 2012-04-30
I went to the website and followed the directions:
I downloaded the WUSB300N driver
 
**When I went to terminal to install ndiswrapper I got this**:
john@john-Dimension-4550:~$ sudo apt-get install ndisgtk
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndisgtk is already the newest version.
The following packages were automatically installed and are no longer required:
  language-pack-zh-hans language-pack-kde-en language-pack-kde-zh-hans
  language-pack-kde-en-base kde-l10n-engb calligra-l10n-engb kde-l10n-zhcn
  calligra-l10n-zhcn language-pack-zh-hans-base firefox-locale-zh-hans
  language-pack-kde-zh-hans-base
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I see the WUSB300N.tar icon in downloads.
**When I went to terminal to extract the file I got this**:
john@john-Dimension-4550:~$ tar -xvf WUSB300N.tar
tar: WUSB300N.tar: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

When I went to terminal to install the driver I got this:
john@john-Dimension-4550:~$ sudo ndiswrapper -i netmw245.inf
[sudo] password for john: 
couldn't open netmw245.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.

**When I went to terminal to check if the driver is installed correctly I got this**:
john@john-Dimension-4550:~$ sudo ndiswrapper -l
john@john-Dimension-4550:~$ 

I don't know if this will turn out or not but here is a screenshot of FileSystem & Downloads Folder
/home/john/Pictures/Screenshot from 2012-04-30 19:38:23.png

PLEASE HELP
Thanks
j

---

### Post by chili555 on 2012-04-30
> I see the WUSB300N.tar icon in downloads.
When I went to terminal to extract the file I got this:
john@john-Dimension-4550:~$ tar -xvf WUSB300N.tarYou need to navigate to Downloads:```
cd Downloads
```See if you are in the correct directory containing the .tar file with:```
ls
```If so, proceed as before.

ndiswrapper requires the Windows **XP** drivers. Please be sure those are the ones you are installing.

Back to your regularly scheduled guru, TBABill.

---

### Post by jbocean on 2012-05-08
Resolved - I did it!
Someone I met at a local Linux users group suggested I extract the driver to a folder I create w/in the file system and so I did and then I ran ndiswrapper and had it point to the .inf file (i think). Anyway, I now have a working wireless connection :) 

Thanks to all the moderators who patiently help noobs.

J

---

