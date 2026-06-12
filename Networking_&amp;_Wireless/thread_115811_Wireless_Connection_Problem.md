---
title: "Wireless Connection Problem"
date: 2006-01-11
forum: Networking &amp; Wireless
---

### Post by IanM39 on 2006-01-11
I have an Amd64 system running windows xp and ubuntu in a dual boot.

I have a netgear wg111v2 wireless router attached to the machine which works fine in windows.

In ubuntu I have managed to install ndiswrapper-utils and the .inf drivers for the netgear card.  Whem I run ndiswrapper -l it tells me that driver installed and hardware found.

I have also run ndiswrapper -m, depmod -a and modprobe ndiswrapper as advised in other forum pages.

My problem is that ubuntu won't recognise wlan0, which means I can't configure it and can't get on the internet.

Please help a newbie as I really like ubuntu and linux and would love to be able to ditch windows.  But internet access is a must have for me.

Thanks

---

### Post by healychan on 2006-01-11
Please post the result of "lspci", "lsusb", "iwconfig" and "ifconfig".

> 
I have a netgear wg111v2 wireless router attached to the machine which works fine in windows.
As far as I know wg111v2 is an USB adapter, not a wireless router.

Are you sure you installed the correct Windows driver with ndiswrapper??

---

### Post by IanM39 on 2006-01-11
Sorry, yes it is a USB adaptor and I've installed the drivers from the configuration utility xp folder on my windows installation.

I have a 2nd pc purely running windows which is connected to a netgear DG834GUKAL router

---

### Post by emperor on 2006-01-11
There appears to be several different chipsets used on the wg111v2.
I would verify that you are using the tested and recommended drivers:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#N](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#N)

---

### Post by healychan on 2006-01-11
[QUOTE=emperor]There appears to be several different chipsets used on the wg111v2.
I would verify that you are using the tested and recommended drivers:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#N](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#N)[/QUOTE]
Yes he is right. There are so many different version of WG111v2. But you need to foucs on one thing which is the chipset. "lsusb" will show you the chipset and then go to find out which driver should be using.

I am using the same model as you. I used the WinXP driver that come with the CD. But I suggest that you better check before install since model can be the same but chipset could be different.

---

### Post by IanM39 on 2006-01-11
Thanks for that.

I ran lsusb as you suggested and it gave me an output of 0846:6a00 Netgear Inc.  I went to the website on the link suggested and found a link to realtec drivers for this usbid.  I downloaded and installed them on ndiswrapper but when I ran ndiswrapper -l, it told me they were invalid drivers.

I think I found the right drivers for the chipset, but when I ran lsusb it only gave me the numbers above, not a chipset name.  Could there be other drivers with the same usbid?  If so, any ideas where I can find them?

I really like ubuntu as an os, but I really do need internet access for it to be useful to me.  I can't afford to buy any new routers or adaptors so if you can help me get online with this one I'd be forever grateful.

Thanks for the prompt replies by the way.  Every day I get to learn a little more with your help.

Thanks again

---

### Post by emperor on 2006-01-11
This should tell you more about the device:
sudo lsusb -v

[http://linuxcommand.org/man_pages/lsusb8.html](http://linuxcommand.org/man_pages/lsusb8.html)

---

### Post by healychan on 2006-01-11
When you install the driver using ndiswrapper, make sure you have both .inf and .sys file in the same directory.

Do this
```
ls /etc/ndiswrapper/wg111v2
```
and check to see is there any .sys file.

If not, remove the driver by```
ndiswrapper -e wg111v2
```

Then install it again, [COLOR="Red"]this time make sure you have both .inf and .sys file in the same directory.[/COLOR]

I am sure your USB adapter is compatible with Ubuntu because I am using it as well.

---

### Post by IanM39 on 2006-01-12
Ok guys,

I ran sudo lsusb -v and it gave me a load of info (mostly numbers) but no chipset name as far as I can tell. It just gave me 0846:6a00 Netgear Inc.

When I ran is /etc/ndiswrapper/net111v2 it gave me the following output.

0846:6a00.0.conf net111v2.inf wg111v2.sys

The net111v2.inf part was highlighted in green if this makes any difference.

Does this mean I have the wrong .inf installed?

Once again, thanks for the quick responses.  

Can you tell me the commands I need to type in to get wlan0 to show up and the commands I need to use to configure it.

Also, once wlan0 is installed, where will I physically see it in Ubuntu?

Many thanks,

---

### Post by healychan on 2006-01-12
> I ran sudo lsusb -v and it gave me a load of info (mostly numbers) but no chipset name as far as I can tell. It just gave me 0846:6a00 Netgear Inc.The number it used to identify different chipsets. Find out what driver should you use with ndiswrapper by using that number.

> The net111v2.inf part was highlighted in green if this makes any difference.

Does this mean I have the wrong .inf installed?The colour of the file name is used to classify the type of files. Directory files should be blue, normal files white, and green should mean that the file is a link. You can confirm it by doing "ls -l" and check the first charater of the results.

d = directoty
l = link
- = normal file

there are more and more.......

> Can you tell me the commands I need to type in to get wlan0 to show up and the commands I need to use to configure it.First things to do is to check if you have a valid ndiswrapper. If not, remove the existing driver and install it again.
Once you have correct driver, try "ifconfig" and " iwconfig" on the command line. Your interface should be display. If you can see the interface show up, you can configure the interface with "iwconfig".
For example, to change the essid, do
```
sudo iwconfig wlan0 essid "XXXXX"
```
Read the manual page of iwconfig for more information.

"man iwconfig" will give you the page
If you have any problems, please post again and provide some useful information such as "ifconfig", "iwconfig", "ndiswrapper -l" etc..........

The more the information, the bigger the chance you get help.

Good luck:p

---

