---
title: "Intel wifi 1000 BGN installation on Back Track"
date: 2011-10-20
forum: Networking &amp; Wireless
---

### Post by seoisfree on 2011-10-20
Hi guys,

I've been struggling with it for quite sometime and wanted to know, how do i install my driver on Ubuntu (back track 5).

when i type iwconfig it doesn't recognizes the card and not showing anything. how ever i am able to access the internet (it's on vmware).

 Also i've downloaded the iwlwifi-1000-ucode-39.31.5.1 from Intel site and put it in the right folder (i don't know if the installation went well as i don't understand the syntax at all)

I will be very thankful if any of you guys can help me out on this one. 

Thanks a lot

---

### Post by chili555 on 2011-10-23
Please open a terminal and run and post:```
sudo modprobe iwlagn
dmesg | grep iwl
ls /lib/firmware | grep ucode
```Thanks.

Sorry for the delay.

---

### Post by haqking on 2011-10-23
> **seoisfree said:**
> Hi guys,

I've been struggling with it for quite sometime and wanted to know, how do i install my driver on Ubuntu (back track 5).

when i type iwconfig it doesn't recognizes the card and not showing anything. how ever i am able to access the internet (it's on vmware).

 Also i've downloaded the iwlwifi-1000-ucode-39.31.5.1 from Intel site and put it in the right folder (i don't know if the installation went well as i don't understand the syntax at all)

I will be very thankful if any of you guys can help me out on this one. 

Thanks a lot

If you are running BT on a virtual machine like you say it will use the virtualised hardware, it cant use wifi unless you use say a USB device you plug in to the VM

You cant use internal WIFI with virtual machines, you need to use a supported USB device for backtrack if used in a virtual machine

---

### Post by seoisfree on 2011-10-23
thanks [haqking]("http://ubuntuforums.org/member.php?u=1317912"),

just to set the record straight, i need an external wireless device for it to be monitoring and could sniff packets  (assuming the BT is running on VMware) is that what you're saying?

thanks

---

### Post by haqking on 2011-10-23
> **seoisfree said:**
> thanks [haqking]("http://ubuntuforums.org/member.php?u=1317912"),

just to set the record straight, i need an external wireless device for it to be monitoring and could sniff packets  (assuming the BT is running on VMware) is that what you're saying?

thanks

yes, you need to find a supported USB wifi device and use that, virtualisation and BT in virtualisation can only use USB WIFI devices, it doesnt need to be supported in your HOST, as long as the VM devices menu can see it you can use it

---

### Post by seoisfree on 2011-10-23
cool man, thanks!

Any idea of a good but cheap USB wireless card that BT 5 Supports by default?

---

### Post by haqking on 2011-10-23
> **seoisfree said:**
> cool man, thanks!

Any idea of a good but cheap USB wireless card that BT 5 Supports by default?

you can find all you need here

[http://www.backtrack-linux.org/wiki/index.php/Wireless_Drivers#Tested_and_working_cards](http://www.backtrack-linux.org/wiki/index.php/Wireless_Drivers#Tested_and_working_cards)

Some cards work with certain tools better than others.

---

### Post by seoisfree on 2011-10-23
Great man, you've been very helpful... thanks a lot!

---

### Post by seoisfree on 2011-10-23
> **chili555 said:**
> Please open a terminal and run and post:```
sudo modprobe iwlagn
dmesg | grep iwl
ls /lib/firmware | grep ucode
```Thanks.

Sorry for the delay.

G chili, I just noticed your post. 

Thanks for the Tip,

This is what i got [PHP]root@bt:~# sudo modprobe iwlagn
WARNING: All config files need .conf: /etc/modprobe.d/ipwraw, it will be ignored in a future release.
root@bt:~# dmesg | grep iwl
[ 2120.105448] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[ 2120.105467] iwlagn: Copyright(c) 2003-2010 Intel Corporation
root@bt:~# ls /lib/firmware | grep ucode
iwlwifi-1000-3.ucode
iwlwifi-1000-5.ucode
iwlwifi-1000-ucode-39.31.5.1
iwlwifi-100-5.ucode
iwlwifi-3945-2.ucode
iwlwifi-3945.ucode
iwlwifi-4965-2.ucode
iwlwifi-5000-1.ucode
iwlwifi-5000-2.ucode
iwlwifi-5000-5.ucode
iwlwifi-5150-2.ucode
iwlwifi-6000-4.ucode
iwlwifi-6000g2a-5.ucode
iwlwifi-6000g2b-5.ucode
iwlwifi-6050-4.ucode
iwlwifi-6050-5.ucode
LICENSE.iwlwifi-1000-ucode
README.iwlwifi-1000-ucode
root@bt:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

root@bt:~# 
[/PHP]

Thanks man

---

### Post by haqking on 2011-10-23
> **seoisfree said:**
> G chili, I just noticed your post. 

Thanks for the Tip,

This is what i got [PHP]root@bt:~# sudo modprobe iwlagn
WARNING: All config files need .conf: /etc/modprobe.d/ipwraw, it will be ignored in a future release.
root@bt:~# dmesg | grep iwl
[ 2120.105448] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[ 2120.105467] iwlagn: Copyright(c) 2003-2010 Intel Corporation
root@bt:~# ls /lib/firmware | grep ucode
iwlwifi-1000-3.ucode
iwlwifi-1000-5.ucode
iwlwifi-1000-ucode-39.31.5.1
iwlwifi-100-5.ucode
iwlwifi-3945-2.ucode
iwlwifi-3945.ucode
iwlwifi-4965-2.ucode
iwlwifi-5000-1.ucode
iwlwifi-5000-2.ucode
iwlwifi-5000-5.ucode
iwlwifi-5150-2.ucode
iwlwifi-6000-4.ucode
iwlwifi-6000g2a-5.ucode
iwlwifi-6000g2b-5.ucode
iwlwifi-6050-4.ucode
iwlwifi-6050-5.ucode
LICENSE.iwlwifi-1000-ucode
README.iwlwifi-1000-ucode
root@bt:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

root@bt:~# 
[/PHP]

Thanks man

YOU CANT USE BUILT IN WIRELESS FOR BACKTRACK IN A VIRTUAL MACHINE !

get a USB adapter

That just shows the module is loaded which of course it is as part of BT

---

### Post by seoisfree on 2011-10-23
> **haqking said:**
> YOU CANT USE BUILT IN WIRELESS FOR BACKTRACK IN A VIRTUAL MACHINE !

get a USB adapter

That just shows the module is loaded which of course it is as part of BT

No Disrespect haqking, Just wanted to hear a second review, you know...

I'll get the adapter :D

---

### Post by haqking on 2011-10-23
> **seoisfree said:**
> No Disrespect haqking, Just wanted to hear a second review, you know...

I'll get the adapter :D

yeah no worries, Chillis advice was great as always, he really knows his wireless, but i think he missed the part that you were running a VM.

A virtual machine cannot use built in wireless like this, thats why you need an external device such as USB.

Those commands show that iwlagn module was loaded, which it is in BT cos you might be using the hardware directly, but in the case of the VM it is not.

Hope this helps

Peace

---

### Post by chili555 on 2011-10-23
> i think he missed the part that you were running a VM..ko-rrect! Unless you need further assistance getting it going in the *host* machine, I will go back to sleep.

---

### Post by haqking on 2011-10-23
> **chili555 said:**
> .ko-rrect! Unless you need further assistance getting it going in the *host* machine, I will go back to sleep.

ha ha sorry to wake you, sleep tight ! ;-)

---

### Post by seoisfree on 2011-10-23
[COLOR=Black]Just Got me a Fresh [/COLOR][COLOR=#339966][COLOR=Black]Linksys WUSB54GC

Thanks guys, i guess we talk again soon on a new Thread haha [/COLOR]:D
[/COLOR]

---

### Post by haqking on 2011-10-23
> **seoisfree said:**
> [COLOR=Black]Just Got me a Fresh [/COLOR][COLOR=#339966][COLOR=Black]Linksys WUSB54GC

Thanks guys, i guess we talk again soon on a new Thread haha [/COLOR]:D
[/COLOR]

should work fine, from memory it uses the rt73USB so that should work out of the box.

good luck, but not a good idea to post any threads relating to BT or aircrack etc as it is usually not supported here, i offered assistance as it was more related to Virtualisation than Backtrack itself.

peace

---

### Post by Dangertux on 2011-10-23
I'm confused? 

Did the answer you received here over a month ago not work?

[http://www.backtrack-linux.org/forums/backtrack-5-beginners-section/45093-intel-wifi-1000-bgn-airmon-ng-help-needed.html](http://www.backtrack-linux.org/forums/backtrack-5-beginners-section/45093-intel-wifi-1000-bgn-airmon-ng-help-needed.html)

In any case you won't be able to utilize your built in wifi in a virtual machine as was stated.

---

