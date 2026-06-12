---
title: "Ubuntu 13.04 No wireless desktop"
date: 2013-05-16
forum: Networking &amp; Wireless
---

### Post by roygbiv808 on 2013-05-16
I just started using Linux so please be patient. I have a desktop with a USB internet adapter. It works fine on the windows side, but Linux will not run it. I have 13.04 32bit. I figured out it has a Broadcom BCM 4323/0846:9011 in the netgear adapter. There is not even an option to turn on wireless. Wired is fine. 
Thanks in advance!

---

### Post by roygbiv808 on 2013-05-17
So I have figured out how to fix it. If you have a desktop and the option for wi-fi is not there in networks and you have a USB wi-fi adapter hopefully this helps.  I was able to use these intructions since I had a wired connection. 
The following I copied directly from the ubuntu docs but I made a change since I came across a problem part way through. To see the original instructions: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Install ndiswrapper it allows you to use wireless cards and in this case usb adapters

```

*sudo apt-get install ndisgtk*
```

Then check the chipset on your usb device

```
*lsusb*
```

It will look something like this: 104c:8400 mines was just numbers. 

Next go to the ndiswrapper list: [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page) 
you can also find it here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) Step 3.2 number 1.

Find your driver: I have a netgear 3100 so I chose that one. 
Download using archive manager to extract the files and remember where you saved it on your computer

Next install the driver:
Check the folder for the .inf file and make note of the name. It is case sensitive. 

```
[I]
sudo ndiswrapper -i <DRIVERNAME>.inf[/I]
```

To make sure it was installed run the command

```
[I]
ndiswrapper -l[/I]
```

 If the driver is installed correctly, you should see the following output: 


Installed ndis drivers: {name of driver} driver present, hardware present or: 

{name of driver} : driver installed device ({Chipset ID}) present

Next load the driver:

```
[I]
sudo depmod -a sudo modprobe ndiswrapper

[/I]
```

To check it again try the commands
```

[I]
ip addr iwconfig[/I]
```

If this worked great. But if you get an error when trying to run the command 
```
[I]
sudo modprobe ndiswrapper[/I]
```
 
and this is your error: 
**[FONT=arial narrow][SIZE=3]"FATAL: Module ndiswrapper not found"         [/SIZE][/FONT]**

it has already been solved in another forum: [http://ubuntuforums.org/showthread.php?t=1987695](http://ubuntuforums.org/showthread.php?t=1987695) just install the rest of the package. Then run the commands that are listed. I did see that Mint was not able to use the same steps..FYI 


```
[I]
sudo depmod -a sudo modprobe ndiswrapper

[/I]
```

again and it came right up for me.

---

