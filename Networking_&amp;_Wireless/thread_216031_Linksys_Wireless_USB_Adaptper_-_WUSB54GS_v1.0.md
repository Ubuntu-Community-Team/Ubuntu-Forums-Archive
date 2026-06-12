---
title: "Linksys Wireless USB Adaptper - WUSB54GS v1.0"
date: 2006-07-14
forum: Networking &amp; Wireless
---

### Post by javaJake on 2006-07-14
I've done some research on this topic, but haven't found a scrap of anything in the forums.

Does anyone know if the Linksys Wireless USB Adapter (WUSB54GS v1.0) works in Ubuntu? And how to get it to work?

Thanks in advance!

---

### Post by plbeane94 on 2006-07-14
I would also be interested in if that specific USB Adapter works because I am trying to get it to work in ubuntu at the moment.

Thanks

Patrick.

---

### Post by wieman01 on 2006-07-15
Hey Guys, 

Look for "ndisrapper" which is a module making use of the native Windows drivers. It's fairly easy to configure and there are tons of howtos out there. Good luck.

Should you - against all odds - find nothing useful, then let me know.

---

### Post by javaJake on 2006-07-15
AHA! I've googled the internet with the USBID (duh) and the second search item was this:
[http://www.linuxquestions.org/questions/showthread.php?t=356315](http://www.linuxquestions.org/questions/showthread.php?t=356315)

It looks like a number of users have successfully installed v1 using these instructions. It's a long read, but if you go through it carefully you can pull out some good instructions that'll help. I'll compile it into an easier-to-find post here later.

I'll let you guys know how this goes in my next post.

---

### Post by javaJake on 2006-07-18
OK, so it didn't work. I'll keep Googling, but if anyone has any ideas, let me know!

---

### Post by javaJake on 2006-07-18
Wow. Only about 30 minutes later I found the solution. I hope.

This was the second to last search result in Google. I'm going to download the ndiswrapper from SVN and see if that works...
[http://article.gmane.org/gmane.linux.drivers.ndiswrapper.general/5768](http://article.gmane.org/gmane.linux.drivers.ndiswrapper.general/5768)

---

### Post by wieman01 on 2006-07-18
NDiswrapper is the the right way to go. Keep trying & let us know what difficulties your are facing. Then we can help.

But don't give up, this is the right track. NDiswrapper is very simple to configure & reliable once set up.

---

### Post by javaJake on 2006-07-19
OK, so here's my first newbie problem. I finally got things to compile and whatnot, but now when I run it it says

bash: /usr/sbin/ndiswrapper: /usr/bin/perl^M: bad interpreter: No such file or directory

ndiswrapper IS in /usr/sbin, by the way. Strange.
I'm using a fresh install of xubuntu with ndiswrapper revision 1940.

---

### Post by wieman01 on 2006-07-19
Have you used the ndiswrapper version from the repository? There is no need to compile it from scratch... Could you install the one that comes with Ubuntu?

---

### Post by stricevics on 2006-07-19
Hi,

There's a nice little manual in "Ubuntu Forums > Dapper Drake 6.06 Release  > Hardware Help  > Wireless Support" called  "[How to install WUSB54G for Dapper Drake]("http://www.ubuntuforums.org/showthread.php?t=192588")". It's short and straight to the point, used it myself just the other day. It's for the v4, however ndiswrapper is using Windows drivers anyway so I would imagine that as long as you get proper drivers set, the install procedure itself is quite "generic" and should work OK. In my case, WUSB54G v4 works great with rt2500usb drivers that came with it on the Windows installation CD. [Wiki page]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation") on the Ndiswrapper's site is a little bit more in detail, however, I don't think it mentiones blacklisting the rt2700 driver.

I've downloaded ndiswrapper from the [http://sourceforge.net/projects/ndiswrapper]("http://sourceforge.net/projects/ndiswrapper").

After you're done with that, if you're using WPA there's also [a nice little article]("http://www.ubuntuforums.org/showthread.php?t=31418") about automating connection with WPA-PSK. There's a note, however, regarding this manual. While executing wpa_supplicant there's flag [SIZE="2"][FONT="Courier New"]-D[/FONT][/SIZE] where the driver to be used should be specified. Now, manual says that [FONT="Courier New"][SIZE="2"]-Dndiswrapper[/SIZE][/FONT] should be used, but that's probably not going to work. After some [surfing]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/WPA"), I found out that after ndiswrapper version 1.12 [FONT="Courier New"][SIZE="2"]-Dwext[/SIZE][/FONT] should be used.

Hopefully, this helps.

Stan

---

### Post by javaJake on 2006-07-20
> **stricevics said:**
> Hi,

There's a nice little manual in "Ubuntu Forums > Dapper Drake 6.06 Release  > Hardware Help  > Wireless Support" called  "[How to install WUSB54G for Dapper Drake]("http://www.ubuntuforums.org/showthread.php?t=192588")". It's short and straight to the point, used it myself just the other day. It's for the v4, however ndiswrapper is using Windows drivers anyway so I would imagine that as long as you get proper drivers set, the install procedure itself is quite "generic" and should work OK. In my case, WUSB54G v4 works great with rt2500usb drivers that came with it on the Windows installation CD. [Wiki page]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation") on the Ndiswrapper's site is a little bit more in detail, however, I don't think it mentiones blacklisting the rt2700 driver.

I've downloaded ndiswrapper from the [http://sourceforge.net/projects/ndiswrapper]("http://sourceforge.net/projects/ndiswrapper").

After you're done with that, if you're using WPA there's also [a nice little article]("http://www.ubuntuforums.org/showthread.php?t=31418") about automating connection with WPA-PSK. There's a note, however, regarding this manual. While executing wpa_supplicant there's flag [SIZE="2"][FONT="Courier New"]-D[/FONT][/SIZE] where the driver to be used should be specified. Now, manual says that [FONT="Courier New"][SIZE="2"]-Dndiswrapper[/SIZE][/FONT] should be used, but that's probably not going to work. After some [surfing]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/WPA"), I found out that after ndiswrapper version 1.12 [FONT="Courier New"][SIZE="2"]-Dwext[/SIZE][/FONT] should be used.

Hopefully, this helps.

Stan

"Seems that the ndiswrapper package on the cd is not enough, the link provided by the OP worked." OK, so I'll download the link provided on the site and see if that works. I'll try the drivers mentioned too.

Will let you know how that goes.

---

### Post by javaJake on 2006-07-25
Well, I got everything running, but now ndiswrapper says "invalid driver". I don't have the sys file. Does that make a difference? In fact, there isn't any sys files that I can find anywhere on the CD or download from Linksys.

Could someone e-mail me (fun 2 program 8 (A><T) yahoo d.o.t. com) (talk about over-doing spam protection :D) the WUSB54GS v1 drivers that at least load into ndiswrapper?

---

### Post by stricevics on 2006-07-25
> **javaJake said:**
> Well, I got everything running, but now ndiswrapper says "invalid driver". I don't have the sys file. Does that make a difference? In fact, there isn't any sys files that I can find anywhere on the CD or download from Linksys.


OK, just downloaded drivers from Linksys' website. It's self-extracting .exe so all you have to do is either extract it under windows or using wine. After you do that, go to ```
<extract_dir>/WUSB54G_20040903/Drivers/WUSB54Gv1/
```

and the .inf and .sys files are there.

---

### Post by javaJake on 2006-07-25
> **stricevics said:**
> OK, just downloaded drivers from Linksys' website. It's self-extracting .exe so all you have to do is either extract it under windows or using wine. After you do that, go to ```
<extract_dir>/WUSB54G_20040903/Drivers/WUSB54Gv1/
```

and the .inf and .sys files are there.

I notice that you are not downloading the WUSB54G***S***v1, but the WUSB54G v1 drivers. Is this on purpose?

---

### Post by javaJake on 2006-07-25
Hmmm... looking back at that post I found on Google (the second one) the guy mentioned that it might not find the sys files, and to copy them... maybe THAT'S why the sys files aren't in the folder, because Windows already has them...

Worth a shot. :)

---

### Post by javaJake on 2006-07-25
THat was it! Drivers are working! Ndiswrapper recognizes device, but now things freeze.

OK, so here's what I did. I modprobed ndiswrapper, then plugged in the device. Now khubd is running like mad (71% CPU) and lsusb, ndiswrapper -l, and etc. won't work. dmesg says this:

[17179792.568000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179792.896000] usbcore: registered new driver ndiswrapper
[17179824.156000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[17179824.336000] ndiswrapper: driver wusb54gs (Linksys,06/18/2004, 3.60.9.0) loaded


Any ideas?

---

### Post by stricevics on 2006-07-25
> **javaJake said:**
> Hmmm... looking back at that post I found on Google (the second one) the guy mentioned that it might not find the sys files, and to copy them... maybe THAT'S why the sys files aren't in the folder, because Windows already has them...

Worth a shot. :)

Have you seen [this article]("http://article.gmane.org/gmane.linux.drivers.ndiswrapper.general/5768")?

This site may also help.

EDIT: Nevermind the site. They charge for DLLs!? :( Hopefully, the article may give you some clues.

---

### Post by wieman01 on 2006-07-25
Just 2 things...

1. You can extract .exe archives using the "zip" command in a terminal. Works like the Windows program.

2. The freeze happens with the current version of ndiswrapper that comes with the Live CD. You may want to upgrade.

If you are interested in WPA2 and encryption, this may help:

[http://www.ubuntuforums.org/showthread.php?t=202834&highlight=wpa+rsn]("http://www.ubuntuforums.org/showthread.php?t=202834&highlight=wpa+rsn")

---

### Post by javaJake on 2006-07-27
> **wieman01 said:**
> Just 2 things...

1. You can extract .exe archives using the "zip" command in a terminal. Works like the Windows program.

2. The freeze happens with the current version of ndiswrapper that comes with the Live CD. You may want to upgrade.

If you are interested in WPA2 and encryption, this may help:

[http://www.ubuntuforums.org/showthread.php?t=202834&highlight=wpa+rsn]("http://www.ubuntuforums.org/showthread.php?t=202834&highlight=wpa+rsn")

1. Thanks a ton!
2. I don't have the one on the CD. I have 1.18 from apt-get. :confused:

---

### Post by javaJake on 2006-07-27
OK, here's my progress so far:

I went to a friend's house, and worked on it with him. (He's 10 times smarter then I am.) We found some messages in dmesg about a security manager not letting something else do something (can't remember now), and another message saying that "wait_for_sysfs" failed. After looking on the ndiswrapper list of supported devices again, I found that someone posted a new device, WUSB54GS v1, along with links to drivers and some directions!

I'm going to try this out, and let you guys know how it goes!

---

### Post by javaJake on 2006-07-27
Drat. No luck. No matter what I do, khubd seems to crash, or run in a loop (it hogs my CPU). syslog says this:

[quote]Jul 27 17:15:24 localhost kernel: [17179999.328000] ndiswrapper: driver wusb54gs (Linksys,06/18/2004, 3.60.9.0) loaded
Jul 27 17:15:30 localhost udevd-event[5287]: wait_for_sysfs: waiting for '/sys/devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/bus' failed[/quote

Both methods mentioned on the ndiswrapper list do this same thing.

If anyone gets this to work, the best way to help me out would be to post the drivers under the /etc/ndiswrapper/<devicename> folder.

Any ideas? ](*,)


**Edit**: Nothing new, but I found that anything connected with USB freezes when I try to run it. This is probably because khubd crashed, so commands like "ndiswrapper -l", "lsusb", and others like it don't work.

---

### Post by stricevics on 2006-07-27
Did you try to examine /var/log/udev? Maybe you can find some clues in it.

Also, did you try that method with manually copying windows drivers into ndiswrapper's directory? The ones that come with windows?

---

### Post by javaJake on 2006-07-28
> **stricevics said:**
> Did you try to examine /var/log/udev? Maybe you can find some clues in it.

Also, did you try that method with manually copying windows drivers into ndiswrapper's directory? The ones that come with windows?

I have tried drivers from Windows as well. They all do the same thing - freeze up khubd. (As a side question, has anyone else got this to work?

And, if dmesg appends new devices to the end of the list, there was nothing in /var/log/udev. I can post the whole file just after plugging in the device if you want.

---

### Post by javaJake on 2006-07-29
OK! I finally got it to work! Once it works, it acts just like it had native drivers. In other words, network-admin, networkmanager, and many other apps recognize, configure, and use it well! Here's the link to my HOWTO I made on this subject:
[http://www.ubuntuforums.org/showthread.php?t=225206](http://www.ubuntuforums.org/showthread.php?t=225206)

---

### Post by wieman01 on 2006-07-29
Well done. Yes, ndiswrapper works like any other Linux driver. So you can configure wireless security using any of the howto found in this forum. Good luck!

If you have problems with setting up wireless security & encryption, etc. let us know. That's the interesting part.

---

### Post by javaJake on 2006-07-30
> **wieman01 said:**
> Well done. Yes, ndiswrapper works like any other Linux driver. So you can configure wireless security using any of the howto found in this forum. Good luck!

If you have problems with setting up wireless security & encryption, etc. let us know. That's the interesting part.

Hmmm... yea... well, now that all the wireless computers that are on the network are Linux, I think I'll turn the network into a WPA encrpyted one instead of WEP. What do you think? Is it more secure?

Also, is there any software that will store a bunch of keys for me so that I don't have to reconfigure the network every time I move my laptop to a new location?

---

### Post by wieman01 on 2006-07-30
> **javaJake said:**
> Hmmm... yea... well, now that all the wireless computers that are on the network are Linux, I think I'll turn the network into a WPA encrpyted one instead of WEP. What do you think? Is it more secure?

Also, is there any software that will store a bunch of keys for me so that I don't have to reconfigure the network every time I move my laptop to a new location?

You can install a tool called NetworkManager if you are using a laptop. However, it has 2 restrictions:

1. No static IP, DHCP only.
2. No hidden ESSIDs

[http://www.ubuntuforums.org/showthread.php?t=125150]("http://www.ubuntuforums.org/showthread.php?t=125150")

If you need either static IPs or you want to turn off ESSID broadcasting, then you need to configure your network manually:

[http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

WPA2 is the most secure way to encrypt your network traffic. WEP is unsecure and WPA is based WEP so I usually recommend WPA2. Check it out and let us know if you need further help.

---

### Post by stricevics on 2006-07-30
> **javaJake said:**
> Hmmm... yea... well, now that all the wireless computers that are on the network are Linux, I think I'll turn the network into a WPA encrpyted one instead of WEP. What do you think? Is it more secure?

It is more secure than WEP. Actually, the very reason why I have bought my WUSB54G was inability of my old Netgear MA101 to handle WPA(2). If you read articles on Wikipedia about WEP and WPA you'll get the idea how insecure WEP is. 

Hope this helps.


P.S. Congratulations on getting this whole thing to work properly.

---

### Post by javaJake on 2006-07-30
Thanks for the help everyone. I just got to get multiple access points set up (you know, so that if I move to another location, it would recognize, and use the appropriate encryption key) and I'll be all set.

Any ideas how to get this to work?

---

### Post by stricevics on 2006-07-31
> **javaJake said:**
> Thanks for the help everyone. I just got to get multiple access points set up (you know, so that if I move to another location, it would recognize, and use the appropriate encryption key) and I'll be all set.

Any ideas how to get this to work?


I think it may be set by using wpa_supplicant. Take a look at the man pages for wpa_supplicant.conf and see if that is what you need.

---

### Post by Arken on 2007-03-22
> **wieman01 said:**
> NDiswrapper is the the right way to go. Keep trying & let us know what difficulties your are facing. Then we can help.

But don't give up, this is the right track. NDiswrapper is very simple to configure & reliable once set up.

I can't get it to work. In the gzip there was no "Install" file or anything... the guide sucked too. It needed the internet.

---

### Post by javaJake on 2007-03-24
> **Arken said:**
> I can't get it to work. In the gzip there was no "Install" file or anything... the guide sucked too. It needed the internet.

My guide only requires you to download the attachment. Try it out:
[http://ubuntuforums.org/showthread.php?t=225206](http://ubuntuforums.org/showthread.php?t=225206)

---

