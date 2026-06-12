---
title: "Share usb storage with TP-Link wireless N router"
date: 2011-10-01
forum: Networking &amp; Wireless
---

### Post by cooco on 2011-10-01
I just bought TP-link wireless N gigabit router (model No. TL-WR1043ND). Everything is working fine except hdd connected via usb on router. I don't know where to find the disc. I can see the disc in router settings (picture_1) but I don't know how to acces it in ubuntu (10.10). There are 4 options under usb settings. Which one should I use? I tried different combinations but without sucess. Thank you for help.

[IMG]http://i55.tinypic.com/2ykkvgy.png[/IMG]

[IMG]http://i52.tinypic.com/dgt7wl.png[/IMG]

[IMG]http://i54.tinypic.com/2i7woli.png[/IMG]

---

### Post by mildenhall on 2012-01-10
Did you every resolve this problem, as I'm just got this router an am having exactly the same problem!!

---

### Post by landisl on 2012-12-27
Hi,

Are you give up with problem or maybe there is solution for it.
I bought WDR4300 and I have the same problem. 
I can't use it in ubuntu another way as only by ftp server.
In Win7 you are able to add it as a place from network (\\tplinklogin.net\volume1\)
It is not exactly network drive but it works and I you don't need start ftp server. 

Question how add this location/usb storage in ubuntu to use it as a network drive.

Many thanks for help

---

### Post by derekreilly on 2012-12-29
Did you ever get a fix for this? I have the same issue. I can access the External HDD with windows but not Ubuntu.

---

### Post by steeldriver on 2012-12-29
there seem to be 2 different routers mentioned in this thread so I'm not sure if this will help, but with my Netgear WNDR3800 I can just navigate to the attached USB drive using Nautilus

Go --> Location... 

and then type [FONT=Courier New]smb://wndr3800.local/usb1[/FONT] (you may need to use the router's IP if you don't have a working zeroconf setup, and you will need to check the USB device name)

---

### Post by derekreilly on 2012-12-29
I am using the TL-WR1043ND router like the original poster and I cannot locate it in Nautilus. 

We should click on ¨Open the disk¨ to access the HDD but it does nothing and following the url for that link
file://192.168.1.1/Volume1 results in webpage not found.

---

### Post by steeldriver on 2012-12-29
does it show up if you run the terminal command 'smbtree'?

---

### Post by haqking on 2012-12-29
> **derekreilly said:**
> I am using the TL-WR1043ND router like the original poster and I cannot locate it in Nautilus. 

We should click on ¨Open the disk¨ to access the HDD but it does nothing and following the url for that link
file://192.168.1.1/Volume1 results in webpage not found.

if the share name is as the original it will be a lower case v

---

### Post by landisl on 2012-12-29
> **steeldriver said:**
> does it show up if you run the terminal command 'smbtree'?

Hi,

Unfortunately no.:(
WDR4300 has the same menu like 1043 and problem is the same.
It is strange that in windows you can use the same link but you have two ways of typing it:
1. any browser file or web than you have access to admin panel
2. typing link in field: run application in menu start. 

I think we have to ask TP link support for any suggestion or maybe someone already asked.

BR

---

### Post by derekreilly on 2012-12-30
Same for me. I have logged a tech request with TP Link, I will let you know if I have any success. I have also started a thread on their forum with no luck yet: [http://forum.tp-link.com/showthread.php?1760-Share-usb-storage-using-Ubuntu-on-TL-WR1043ND&p=3501#post3501](http://forum.tp-link.com/showthread.php?1760-Share-usb-storage-using-Ubuntu-on-TL-WR1043ND&p=3501#post3501)


> **landisl said:**
> Hi,

Unfortunately no.:(
WDR4300 has the same menu like 1043 and problem is the same.
It is strange that in windows you can use the same link but you have two ways of typing it:
1. any browser file or web than you have access to admin panel
2. typing link in field: run application in menu start. 

I think we have to ask TP link support for any suggestion or maybe someone already asked.

BR

---

### Post by derekreilly on 2012-12-30
neither lower or upper case works unfortunately.

> **haqking said:**
> if the share name is as the original it will be a lower case v

---

### Post by derekreilly on 2012-12-30
The annoying thing is that if I go to FTP Server or media server in the router and click on Add new folder, I can see all the folders that are in the HDD, I just cannot access them.

---

### Post by derekreilly on 2013-01-01
A TP Link "Engineer" just emailed me saying that this router does not support access by Ubuntu.  I replied by pointing out that according to the system requirements written on the box, it supports Windows, Mac and **Linux based operating systems**.

---

### Post by Shadowline on 2013-01-08
type this in Nautilus go-to.... smb://tplinklogin.net/volume1/
fixs it for me...

---

### Post by derekreilly on 2013-01-09
It works!!  Thanks Shadowline.

---

### Post by landisl on 2013-01-10
many thx
 also on 4300 it works.

---

### Post by Norwal on 2013-01-11
I have the 4300 and haven't been able to find any info on getting the shared printer work with Ubuntu.  Has anyone found a solution for the USB printer?

---

### Post by landisl on 2013-01-20
> **Norwal said:**
> I have the 4300 and haven't been able to find any info on getting the shared printer work with Ubuntu.  Has anyone found a solution for the USB printer?

Hi,

If you have problems with share printer at first please check on tp-link website is your printer is on compatibility list.

---

### Post by nigeldodd on 2013-03-03
I can find my usb disk connected to the router here:

[ftp://tplinklogin.net/folder1](ftp://tplinklogin.net/folder1)

or, on the command line:

~/.gvfs/FTP as nigel on tplinklogin.net/folder1

the spaces on the line above should be escaped.

Hope this helps

---

### Post by linuxiswindows on 2013-09-20
I found the solution to mount the usb drive connected to TPLink rount TL-WDR4300. It took me a long time to find it but it works wonderfully. I've not tested it with any other router so no idea if it will work or not. 


[LIST=1]
[*] In the terminal type sudo gedit /etc/fstab
[*]At the bottom of the file add the following line
[LIST]
[*]//192.168.0.1/volume1 /home/saket/MyDrive cifs sec=ntlm,uid=1000,gid=1000,user,_netdev 0 0[CODE]
[*]In more generic form //server/share /mount/sharefolder cifs sec=ntlm,uid=1000,gid=1000,user,_netdev 0 0
[/LIST]

[*]The important part is **sec=ntlm **and **user. **without these two parameters you will not be able to connect.
[*]Now you will be able to access the drive from anywhere i.e. open files, add attachment etc.
[/LIST]
For further explainations please have a look at the following links

[http://ubuntuforums.org/showthread.php?t=2139090](http://ubuntuforums.org/showthread.php?t=2139090)
and
[http://aptosid.com/index.php?name=PNphpBB2&file=viewtopic&t=2566](http://aptosid.com/index.php?name=PNphpBB2&file=viewtopic&t=2566)

---

### Post by Norwal on 2013-10-05
> **landisl said:**
> Hi,

If you have problems with share printer at first please check on tp-link website is your printer is on compatibility list.

That's why I bought that particular router because it is on the list.  It works fine in Win7 but never did get it working in Ubuntu.  Its a mute point now though because I just bought a Office Pro 8600 and installing the printer via WiFi was easier and quicker with Ubuntu than it was with Windows 7. :P

---

### Post by gr8siddharth on 2014-02-24
Hi,

Those for whom the browsing smb://tplinklogin.net/volume1 method did not work out, make sure you go to the User accounts section under USB Settings and add a user with the same name as your current ubuntu user.

---

### Post by saimis on 2014-05-09
> **gr8siddharth said:**
> Hi,

Those for whom the browsing smb://tplinklogin.net/volume1 method did not work out, make sure you go to the User accounts section under USB Settings and **add a user with the same name as your current ubuntu user**.

Thanks! 

Can confirm, this helped me on Ubuntu 14.04 default file explorer Files (v3.10) and router is TL-WDR3600.

---

### Post by emanuensis on 2014-07-11
Thanks to @Shadowline & @linuxiswindows
i now have access to the USB drive over ethernet!
Can anyone say how to get  access over WiFi?

--

Seems to work now,
sorry for the false alarm!

---

