---
title: "Downloading Package Indexes Failed [Atheros AR8161 &amp; Broadcom 4313]"
date: 2012-09-10
forum: Networking &amp; Wireless
---

### Post by anime4eva on 2012-09-10
Hi all,


  I just finish dual booting Windows 7 and Ubuntu 12.04. Now facing  problem with my Ethernet and Wireless.

I had installed patch, dkms, fakeroot and bcmwl  from LiveCD, however, when I click on ADDITIONAL DRIVERS, I only received  Downloading Package Indexes Failed.

I also type[COLOR=#CC0000]
~$ sudo modprobe -r b43 ssb wl[/COLOR][COLOR=#CC0000]
~$ sudo modprobe wl

[COLOR=Black]and this time no Fatal Error on wl but the STA just wont load.

Anything I did not do? Also for Atheros AR8161 is there any way to install the driver without internet? Is it because of my Atheros that's why wireless won't load? By the way, when I use LiveCD, it auto load STA but I still cannot detect wireless connection.

Besides that, is there any other drivers needed to install? This is my  first time install Ubuntu so I not sure what else is needed here. 

Thanks in advance![/COLOR][/COLOR]

---

### Post by chili555 on 2012-09-11
I'm not sure the STA driver is correct for your device, but let's identify it first:```
lspci -nn | grep -e 0200 -e 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \.> Also for Atheros AR8161 is there any way to install the driver without internet?Of course. My code above will identify it, too, and we'll proceed.> Is it because of my Atheros that's why wireless won't load?You can't download the needed (and probably wrong) files without an internet connection. Thanks.

---

### Post by anime4eva on 2012-09-12
Thanks for your help!

I found your nice and simple thread 
 				 				**Re: Lenovo G480 / Atheros AR8162 woes: unable to initiate wired/dsl **and managed to temporary use my wired to download and now wireless is working while my wired need to recompile again.

Now my issue is with downloading Google Chrome as when I download halfway, it give me the message that 'the deb is not supported and cannot be read' and ended my download.

You happen to know what happen? Also when I click on nVidia setting, it says that my laptop is not using it. I think mine have Intel 4000 and nVidia, I wonder any setup I need to do to let Ubuntu to switch the graphic card when more graphic power is required?

I had installed Ubuntu restricted package, nVidia setting, wireless and wire driver, Gnome, Flash for Firefox, OpenJava, VLC, Skype. Is there anything else I would need to install in my Ubuntu?

I plan to learn how to use C++, any recommendation for the program to use and files to learn?

If you happen to be able share some lights with me, that will be great. Thanks!

---

### Post by chili555 on 2012-09-12
> **anime4eva said:**
> Thanks for your help!

I found your nice and simple thread 
 				 				**Re: Lenovo G480 / Atheros AR8162 woes: unable to initiate wired/dsl **and managed to temporary use my wired to download and now wireless is working while my wired need to recompile again.

Now my issue is with downloading Google Chrome as when I download halfway, it give me the message that 'the deb is not supported and cannot be read' and ended my download.

You happen to know what happen? Also when I click on nVidia setting, it says that my laptop is not using it. I think mine have Intel 4000 and nVidia, I wonder any setup I need to do to let Ubuntu to switch the graphic card when more graphic power is required?

I had installed Ubuntu restricted package, nVidia setting, wireless and wire driver, Gnome, Flash for Firefox, OpenJava, VLC, Skype. Is there anything else I would need to install in my Ubuntu?

I plan to learn how to use C++, any recommendation for the program to use and files to learn?

If you happen to be able share some lights with me, that will be great. Thanks!Sorry, I am not experienced in graphics, C++, OpenJava, etc. I suggest you ask over on General Help.

[http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

---

### Post by anime4eva on 2012-09-13
OK!

Thank you very much for the network and wireless driver!

---

