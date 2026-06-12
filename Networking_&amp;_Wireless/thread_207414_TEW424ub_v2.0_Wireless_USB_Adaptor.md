---
title: "TEW424ub v2.0 Wireless USB Adaptor"
date: 2006-07-01
forum: Networking &amp; Wireless
---

### Post by arkuen on 2006-07-01
Hi, Im brand new to ubuntu and kubuntu and the computer I have ubuntu on right now is not able to reach a wired router with cable so I have a wireless adapter. Ive been searching all over the forums to try and answer this issue first and there doesnt seem to be anything that gets me anywhere.  I followed some instructions to install ndiswrapper from the cd and then i ran the command

ndiswrapper -i /media/WLAN/Drivers/Windows_XP/SiS163u.INF and it came up with SiS163u already installed. Use -e to remove it. So then I did the ndiswrapper -l command and it listed SiS163u invalid driver!

I dont know what to do or why none of this will work for me. Ive seen lots of other people on the web get this exact adapter working but none of their guides have done anything to help me. Can anyone point me to the right direction

---

### Post by Caim on 2006-07-01
If your TEW 424UB uses ZD1211 this might help

[http://ubuntuforums.org/showthread.php?t=195259&highlight=wireless](http://ubuntuforums.org/showthread.php?t=195259&highlight=wireless)

---

### Post by arkuen on 2006-07-01
Sadly V1.0 has the ZD1211 chipset. V2.0 uses a different chipset.

as listed in this guide, but it didnt work like the guide states [http://www.smallwhitecube.com/php/dokuwiki/doku.php?id=howto:tew424ubv2](http://www.smallwhitecube.com/php/dokuwiki/doku.php?id=howto:tew424ubv2)

---

### Post by arkuen on 2006-07-02
anyone?

I cant figure out why the sis162u is an invalid driver or how it says it was installed before i even gave it the driver.

---

### Post by arkuen on 2006-07-02
also if i use the -e switch to remove the driver i get an error stating that driver is not installed.

---

### Post by joereid on 2006-12-11
try the -r switch and give the name of the driver.  the one listed with -l
for instance, on driver.inf  ndiswrapper -r driver

---

### Post by joereid on 2006-12-11
i've gotten this driver to work in ubuntu 6.10 edgy eft.
i am sorry that i do not remember every exact step to do it, but hopefully this will get ya'll headed in the right direction.
i can confirm that it will work in ubuntu. i have done it. it worked.
the zd1211 or other drivers that i see people talking about isn't made for the particular chipset in the tew-424ub usb wireless thingy.
the zd1211 or whatever driver is made for the older model. the A series. we have the b series/model. mine is blue with a flippy cover for the usb thing.
here is how i did it.
i went to ndiswrapper home page, [http://ndiswrapper.sf.net](http://ndiswrapper.sf.net) and got their latest release. this might not be entirely neccessary.
then i got all the build tools for ubuntu from synaptic. gcc g++ etc.
look for a howto if you need help with that part. i always refer to howtos.
next, i built and installed ndiswrapper.
now you may not need the latest version. it may be possible to skip those steps, and just install the ndiswrapper that is in synaptic.
after installing ndiswrapper, make sure you have the wireless tools, iwconfig and iwpriv and iwlist. its all in a wireless tools package or something in synaptic.
next, get your windows driver or the new driver for it off the [www.sis.com](www.sis.com) website. i used both, so either will work.
then give the command, ndiswrapper -i /path/to/driver.inf which is the windows driver. i think it is named 163u.inf or something.
that installed the driver.
next, run the command, depmod -a (this should only have to be run the first time, or only once.)
next run the command, modprobe ndiswrapper
you should have wlan0 now. its like eth0.
iwconfig will allow you to set essid and stuff.
and dhclient is already running on it.
your hardware is working now, all you have to do is configure it.
so to sum up, install ndiswrapper, get windows driver, run ndiswrapper -i driver.inf, the first time you use ndiswrapper after installing it you have to run depmod -a, then run modprobe ndiswrapper.
next, commands like iwconfig wlan0 essid s0me_id, iwlist scan, and man iwpriv should be helpful for setting it up. if i remember correctly, i just had to set essid, and used ifconfig to set the ip (no base station or dhcp here, i used ad-hoc mode and talked between two of them)
sorry this post is so sloppy, and fast.
i just wanted to give yall the info i know about this quickly and wanted to share. i hope it helps you. and if you get it working, please post instructions here and anywhere else you can find. like better directions than these. also, i expect that i would have had a lot easier time setting it up the first time if i had had dhcp and a base station.
you won't need the ifconfig command if you have dhcp.
after i got it set up here, i broke it somehow and then finals came in college and i'm waiting to finish before delving into it.
you can check back in a week or two from this post and i'll probably put up a much better howto. again, sorry its not exactly step by step.
this should get you headed into the right direction, and let you know its possible. i surfed from the couch for the first time in my life. it worked, for sure. hope this helps.

---

### Post by FrodoB on 2006-12-11
Version 2 requires ndiswrapper and the sis NDIS files for Windows.

---

### Post by joereid on 2007-01-09
todays date is jan. 8 2007.
i figured out the problem i was having with this card, the tew424ub from trendnet.
ndiswrapper versions larger than 1.23 don't work with them.
i downloaded ndiswraper-1.23.tar.gz and compiled it, installed it, ran depmod -a,  and then ran the commands:
sudo ndiswrapper -i /path/to/sis163u.inf 
sudo modprobe ndiswrapper
sudo iwconfig wlan0 essid MyEssid
sudo dhclient wlan0
then my wireless worked.
as of today, the latest ndiswrapper is 1.34 
it doesn't work with the tew424ub.  i submitted a bug report and chatted with a developer on #ndiswrapper
he is aware of the problem and it will probably be fixed soon.
in the future, it would be worth checking if the latest ndiswrapper works, and if not, the grap ndiswrapper-1.23 and compile and install it.  see install file in .tar.gz for install instructions.  
do a depmod -a after installing.  also remove the driver listed by ndiswrapper -l 
probably sudo ndiswrapper -r sis163u  or sudo ndiswrapper -e sis163u
make sure the module is unloaded, sudo rmmod ndiswrapper
then use it like normal.  (i listed the steps above)
this ought to make some people happy. 
after a little time passes from now, it will be worth checking if the problem has been fixed in latest ndiswrapper. 
i'm using the tew424ub right now.  i'm wireless ! :)

---

### Post by joereid on 2007-01-29
it works now.  it has been fixed. i tested it too.  it works. :)
the date is 1-28-2007 
currently, its in the svn revision 2186.
the current stable version is 1.35  but it doesn't work in this version.
it will in the next version, 1.36 or later
to get the svn version, run this command.
svn co [https://svn.sourceforge.net/svnroot/ndiswrapper/trunk/ndiswrapper](https://svn.sourceforge.net/svnroot/ndiswrapper/trunk/ndiswrapper) 
now you will have a folder called ndiswrapper.  
to install it, run these commands.  doesn't matter if the first two give errors or not.

sudo rmmod ndiswrapper
sudo ndiswrapper -e sis163u
cd ndiswrapper
sudo make uninstall     # might try running that twice
make
sudo make install

you have it installed now.  next plug in your trendnet thingy if it isn't already, and set it up. for example:
sudo ndiswrapper -i /path/to/sis163u.inf
sudo modprobe ndiswrapper

hardware is up and working now.
iwlist wlan0 scan  should give you results. get your essid and type:
sudo iwconfig wlan0 essid YourEssid
sudo dhclient3 wlan0  #to do dhcp   else, use ifconfig wlan0.
you should be set.  

with svn you can use svn up -r XXXX  to go back or forward through revision numbers. shouldn't need that.
2186 is the latest and the first to work with this card in ubuntu.
after ndiswrapper 1.36 comes out, it and every one after should work.  :)
i'll follow [https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/index.html](https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/index.html)  and make a package for it, but i don't know if it will make it to any repositories.   
enjoy !  and i'm using the card now. it works.
i'm using the [http://downloads.trendnet.com/TEW-424UB_v2%5CDriver_Utility%5CUtility_Driver_TEW-424UB(v2.x).zip](http://downloads.trendnet.com/TEW-424UB_v2%5CDriver_Utility%5CUtility_Driver_TEW-424UB(v2.x).zip)
driver for windows.  found it of the [www.trendnet.com](www.trendnet.com) site.  easy to find.

---

### Post by minority on 2007-02-08
I am a complete newbie to ubuntu. and dont understand this command

run this command.
svn co [https://svn.sourceforge.net/svnroot/...nk/ndiswrapper](https://svn.sourceforge.net/svnroot/...nk/ndiswrapper)

---

### Post by joereid on 2007-02-09
well...
you need svn to run it.
svn i s the command and all the rest are options to svn.
best to get the tarball from the website.
[http://ndiswrapper.sf.net](http://ndiswrapper.sf.net)
and install it.
i think version 1.37 or so i s out and it works.  i'm using it now.
svn is like cvs.
its a way to get development code.
best for you to get the release.
get it, install the build tools,   apt-get install gcc  and whatever else you need with it.  you can search here on the forums for a howto on the build-tools or i think the ubuntu guide has it.
its like libc and libc-headers or something.  short list of stuff to get.
let me know if i can help you with anything else.
so go get the 1.37  (or later) version of ndiswrapper,
then find the howto that gives you the list of build tools to apt-get install
then tar xf ndiswrapper-whatever.tar.gz
then cd into it.
then sudo make uninstall  then make then sudo make install
then sudo depmod -a
you should be all ready to go.
again let me know if i can help you more.  find that build tools list.  like gcc and libc
:)

---

### Post by GodsMadClown on 2007-02-11
Here's a thread about installing the "build-essential" package so that things will compile.
[http://ubuntuforums.org/showthread.php?t=103714](http://ubuntuforums.org/showthread.php?t=103714)

Here's how you do it.

```
sudo apt-get install build-essential
```

---

