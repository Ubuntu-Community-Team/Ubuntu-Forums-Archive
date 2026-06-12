---
title: "Netgear WG511 V2 (China)"
date: 2009-12-17
forum: Networking &amp; Wireless
---

### Post by no_id on 2009-12-17
Hello Guys,
 
As most of us say that we are new to Linux, i can confirm i am as well.
 
I have read on Ubuntu, and searched on Google, and some people are saying it has worked and some are saying its not.
 
So can someone please tell me what i need to do to get my wireless working please.
 
Many Thanks,
No_ID

---

### Post by chili555 on 2009-12-17
This should do it! [http://ubuntuforums.org/showthread.php?t=76804](http://ubuntuforums.org/showthread.php?t=76804)

The file you need to add prism54 to is now /etc/modprobe.d/blacklist.conf instead of what is listed in the HOWTO. I just tried the download (wget) and it is still live. 

Please post back if you get stuck.

---

### Post by no_id on 2009-12-18
Hello,

THank you for the information, can you please confirm what i need to download from here.

[http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)

and then download this.

[http://sourceforge.net/projects/ndiswrapper/files/](http://sourceforge.net/projects/ndiswrapper/files/)

But then where do i type this?

```
sudo apt-get install ndiswrapper-utils
```

and should i follow the post which is 2nd, as mine isnt a 3rd version.

Many Thanks.

---

### Post by no_id on 2009-12-18
Hello,

Can someone please tell me how to find if i have SUDO is installed.

Thank you

---

### Post by chili555 on 2009-12-18
You have *sudo* installed by default. You will type those commands in a terminal. If you use Gnome, it's Applications -> Accessories -> Terminal. You need nothing from kernel.org. Also, the commands assume you have an internet connection; that is, you can drag that laptop over to the router, modem or otherwise, connect an ethernet cable and install things over the internet. Post back, we will help you.

---

### Post by no_id on 2009-12-18
Hello,

After typing this,

[FONT=Courier New]sudo apt-get install ndiswrapper-utils[/FONT]

[img]**[http://img692.imageshack.us/img692/8733/screenshotpc.png](http://img692.imageshack.us/img692/8733/screenshotpc.png)**[/img]

Is this fine? Or do i need to change something or carry on?

Many Thanks

---

### Post by no_id on 2009-12-18
also after that i still went forward and download the file by using the command, after that i tried to unzip the file and i got the following code, can you please tell me what it means.

```
unzip:  cannot find or open AVDR_2802wV.2_WHQL.zip, AVDR_2802wV.2_WHQL.zip.zip or AVDR_2802wV.2_WHQL.zip.ZIP.

```

I know what it means but i dont know where the file is, as i typed the command and it downloaded the file.

Many Thanks Guys

---

### Post by chili555 on 2009-12-18
> **no_id said:**
> Hello,

After typing this,

[FONT=Courier New]sudo apt-get install ndiswrapper-utils[/FONT]

[img]**[http://img692.imageshack.us/img692/8733/screenshotpc.png](http://img692.imageshack.us/img692/8733/screenshotpc.png)**[/img]

Is this fine? Or do i need to change something or carry on?

Many ThanksIt suggests *ndiswrapper-common*, so I suggest:```
sudo apt-get install ndiswrapper-common
```

---

### Post by chili555 on 2009-12-18
> **no_id said:**
> also after that i still went forward and download the file by using the command, after that i tried to unzip the file and i got the following code, can you please tell me what it means.

```
unzip:  cannot find or open AVDR_2802wV.2_WHQL.zip, AVDR_2802wV.2_WHQL.zip.zip or AVDR_2802wV.2_WHQL.zip.ZIP.

```

I know what it means but i dont know where the file is, as i typed the command and it downloaded the file.

Many Thanks GuysBy default, Ubuntu downloads to your desktop. In your home directory, there is a subdirectory called *Desktop*. In the terminal, do:```
cd Desktop
unzip AV*
cd AV   <---press Tab, it will fill in for you
cd Driver/WinXP/
ndiswrapper -i 2802W.inf

```Carry on with the instructions as listed in the forum post.

---

### Post by no_id on 2009-12-19
Hello,

the problem is i dont have a CD with the drivers, will that be a problem?

Many Thanks.

---

### Post by chili555 on 2009-12-19
No problem. The file we downloaded and unzipped contains everything we need.

---

### Post by Wins2LinX on 2010-01-30
Hi to all Linx gurus.

I am a windows user. now totally fedup. trying to move in to Ubuntu.
I have installed the OS in my old laptop and I am trying to connect to internet using my NetGear WG511v2 wireless PC card.

As i am used to windows exe installations, I am finding very difficult to understand/follow  the installation methods described in this forum.

Can you please provide me a step-by-step process I need to follow to install install the relevant drivers and make it work.

I appreciate your guidance and your patience.

May god bless your heart.

Thanks,

---

### Post by chili555 on 2010-01-30
Grab this file on a USB key or similar: [http://www.smc.com/files/AV%5CDR_2802wV.2_WHQL.zip](http://www.smc.com/files/AV%5CDR_2802wV.2_WHQL.zip) Copy it over to a convenient place, such as your Desktop. When you right-click it and select, 'Extract Here,' a folder will be created, called V\DR_2802wV.2_WHQL. Drill down to Drivers and WinXP. The files *2802W.inf *and *2802W51.sys* are the files you need.

Proceed as outlined here:  [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Wins2LinX on 2010-01-30
Thanks you Chili555.

After 5 long hrs of research i was able to find the Ubuntu 'Windows Wireless Drivers' installation process. but I was not able to install the Netgear WG511v2 PCI card.

The INF file mentioned in all the forms I read did not mention that the file name may vary. Later I downloaded the WinXP drivers from another website, which has driver WG511v2.INF as a driver. I used it. to my surprise it just worked fine.

So this is a lesson I learn on my 1st Ubuntu day.

Kep up the good work Ubuntuoos..

---

