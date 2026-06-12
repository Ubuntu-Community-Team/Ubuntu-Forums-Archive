---
title: "Need hints on adding a new device to Network Manager"
date: 2009-07-13
forum: Networking &amp; Wireless
---

### Post by Macchi on 2009-07-13
[HERE YOU WILL FIND A WORKAROUND FOR THE HUAWEI E1550]("http://ubuntuforums.org/showpost.php?p=7622263&postcount=3") WHILE WE WAIT FOR A MORE PERMANENT SOLUTION.

Hello everybody!

I need hints on how to add a new device to the Network Manager packages in Ubuntu. New udev rules, etc are required. 

My immediate goal is to be able to handle the Huawei E1550 mobile broadband USB modem on Ubuntu with the Network Manager. The process of updating NM with a new device or new provider seems to to take many many months. The market has been offering new mobile broadband devices quite often and unfortunately the Network Manager is sometimes not capable of handling the devices without manual tweaks.

It would be very favorable for Linux and for Ubuntu to be able to follow the development of the market despite the fact that many equipment developers do not contribute for open source solutions.






OBS: The Huawei E1550 is very interesting for us since it is sold here in Sweden for 25&#8364; on certain foodstores (!) on prepaid plans with a fixed fee per month, day, or week. Presently it is the most flexible and cheapest device sold without attachments to other costs. It is locked to a single provider.

---

### Post by GeorgeVita on 2009-07-14
Hi **Macchi**,
possibly a helpful post from Sweden:
[http://ubuntuforums.org/showpost.php?p=7613936&postcount=6](http://ubuntuforums.org/showpost.php?p=7613936&postcount=6)

Fully agree with your thoughts:
> It would be very favorable for Linux and for Ubuntu to be able to follow the development of the market despite the fact that many equipment developers do not contribute for open source solutions.

A 'paspartu' user-definable option could be made within N.M specs.
If the user gain the /dev/tty... port must be simple to use it. Most mobile broadband modems have a minimum compatibility to ETS07.05 and ETS07.07 AT commands.

Regards,
George

---

### Post by Macchi on 2009-07-15
Here is a method (workaround) to use the Huawei E1550 Mobile Broadband HSDPA 3.6Mbps modem in Ubuntu with the Network Manager. Open a terminal and follow the three steps: 

1) Install udev-extras from the standard Ubuntu repositories: 
```

sudo apt-get update && sudo apt-get install udev-extras

```

2)  Add a custom udev rule for the Huawei E1550 by typing this line:
```

echo 'SUBSYSTEM=="usb", SYSFS{idProduct}=="1446", SYSFS{idVendor}=="12d1", RUN+="/lib/udev/modem-modeswitch --vendor 0x12d1 --product 0x1446 --type option-zerocd"' | sudo tee  /etc/udev/rules.d/45-huawei1550.rules

```

3) Configure explicitly the Mobile Broadband on Network Manager according to specific instructions from your provider. In my case I just had to fill in the APN. It is convenient to check the box that the connection will be activated automatically and will be available for all users.



OBS: This modem is interesting due to high flexibility, low cost, and quite reasonable performance for mobile broadband. Here in Sweden they are sold for approx 25€ on prepaid (no contract).
This is only a workaround before a definitive solution is created for udev and/or network manager and/or devicekit. 
The other solutions that I have seen involved installing from source software that is not yet on the repositories. I personally prefer to strive after standardization and resources available on the repositories. Observe that the modem-switch on udev-extras is not the same as usb_modeswitch! I hope that these tools will soon converge upstream.

---

### Post by ehabh on 2009-07-21
macci you are a genius it works with etisalat modem in Egypt [www.etisalat.com.eg]("http://www.etisalat.com.eg")
I am now answering on the modem and browsing my site [www.mashy.com]("http://www.mashy.com")

Thank you a million times over.

---

### Post by Macchi on 2009-07-23
Thanks Ehabh, I am glad that this workaround was also useful for you!
Let's hope the Huawei E1550 will soon work transparently in Ubuntu without the need for manual tweaks.

---

### Post by ubuntu_cork on 2009-07-26
This is great, is there a generic principle i can follow for example for getting the E160 or E180 using the same method that you used.

And I love going to Stockholm every year for a few days.  God bless Ryanair ;-)  Gammastan always fills my cameras memory card on each and every visit!  thats why I invested in a little nettop that will now connect with the aid of your little tweak.

F-spot + E1550 + this tweak + nettop + Camera + Stockholm/Oslo = Sheer unadulterated happiness

Mick.

---

### Post by Macchi on 2009-07-27
> **ubuntu_cork said:**
> This is great, is there a generic principle i can follow for example for getting the E160 or E180 using the same method that you used?


This tweak is for USB modems that first appear as a storage device and then have to be actively switched to the modem-mode. I used modem-modeswitch from udev-extras, and create a custom udev rule. Try to substitute the vendor and product ID with the actual values for you modem. Hopefully it works with the network manager in the standard way.






PS: Clearly off-topic, but regarding a comment on Sweden: Stockholm is probably among the most beautiful capitals of the world. On your next visit I would recommend seeing the archipelago in the summer: It has more that 20 thousand islands and fantastic places can be reached by regular bus and boat tours.

---

### Post by farbird on 2009-08-02
u the man...

mine was a lengthy method..

yours shrink it down to less than 3 lines.



> **Macchi said:**
> Here is a method (workaround) to use the Huawei E1550 Mobile Broadband HSDPA 3.6Mbps modem in Ubuntu with the Network Manager. Open a terminal and follow the three steps: 

1) Install udev-extras from the standard Ubuntu repositories: 
```

sudo apt-get update && sudo apt-get install udev-extras

```

2)  Add a custom udev rule for the Huawei E1550 by typing this line:
```

echo 'SUBSYSTEM=="usb", SYSFS{idProduct}=="1446", SYSFS{idVendor}=="12d1", RUN+="/lib/udev/modem-modeswitch --vendor 0x12d1 --product 0x1446 --type option-zerocd"' | sudo tee  /etc/udev/rules.d/45-huawei1550.rules

```

3) Configure explicitly the Mobile Broadband on Network Manager according to specific instructions from your provider. In my case I just had to fill in the APN. It is convenient to check the box that the connection will be activated automatically and will be available for all users.



OBS: This modem is interesting due to high flexibility, low cost, and quite reasonable performance for mobile broadband. Here in Sweden they are sold for approx 25€ on prepaid (no contract).
This is only a workaround before a definitive solution is created for udev and/or network manager and/or devicekit. 
The other solutions that I have seen involved installing from source software that is not yet on the repositories. I personally prefer to strive after standardization and resources available on the repositories. Observe that the modem-switch on udev-extras is not the same as usb_modeswitch! I hope that these tools will soon converge upstream.

---

### Post by eeBus on 2009-08-23
Hi Macchi,

I've been struggling to get my Huawei E1750 modem to work on Ubuntu.

See [http://ubuntuforums.org/showthread.php?t=1246293](http://ubuntuforums.org/showthread.php?t=1246293)

Have you any ideas or pointers?

Thanks
eeBus

---

### Post by GOwin on 2009-08-27
Is there any way of sending init strings to the modem? The windows program that comes with the modem has means to set the modem to "WCDMA only" to ensure that you only connect using the 3.5G.

Looking for an option to the same in Linux/Ubuntu in the NM applet

Looking at my modem, I see a steady blue light and according to Huawei that means I'm on 3G instead of 3.5G (Cyan)
- Green Light You are connected to the GPRS/EDGE network (fast)
- Blue Light You are connected to the 3G network (faster)
- Cyan Light You are connected to the HSDPA or Turbo network (fastest)

---

### Post by Dr.AMA on 2009-08-27
**[COLOR="DimGray"]Macchi, i Can't  say anything to you Describes what i want to say , you solved my biggest problem that make me go back to the hell again " Windows " , thanks and Mellon Thanks .......[/COLOR]**

---

### Post by vkrk on 2009-09-13
**MACCHI**

Your work around connected instantly but the connection keeps dropping ever 5 seconds or so despite the signal strength being excellent. any thing else I should do? I am on 3uk
thanks

---

### Post by vkrk on 2009-09-13
didnt realise that i've to restart like in windows. Solved now

---

### Post by chkhurum on 2009-09-17
I tried the method you explained but whenever i plug in my E1550 modem it shows a window with modem content in it. I think system still treats it as USB memory stick.
I checked in /lib/udev/ and noticed that I don't have modem-modeswitch. How can I install it?

When I run the following command  **sudo apt-get update && sudo apt-get install udev-extras** I got this error on terminal
**W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]**

Rest of the other were downloaded fine. BTW I am using Ubuntu 8.04

---

### Post by Ralph386 on 2009-09-27
Hi, I have Ubuntu 8.04 and an E1552 modem. I tried your method but seems that it does not work with Hardy, any idea to make it rock?

---

### Post by Ralph386 on 2009-10-15
Hi again, I have Huawei E1552 with a contract with Sonera in Finland. I had Ubuntu 8.04 and I never managed to make it work. I tried Ubuntu 9.04 live CD and it recognizes the usb flawlessly. I decided it was time for a change then I installed Ubuntu 9.04. I know the solution is a bit to extreme, however now I can focused in something else.

Ubuntu ROCKS!!!!!!!:guitar:

---

### Post by duleep on 2009-11-08
my huawei e1552 was not working in 9.04 but it autorun work and show mobile partner icon on Desktop. this is  work well before few week. plz help to me

---

### Post by kiruri on 2009-12-24
> **Macchi said:**
> Here is a method (workaround) to use the Huawei E1550 Mobile Broadband HSDPA 3.6Mbps modem in Ubuntu with the Network Manager. Open a terminal and follow the three steps: 

1) Install udev-extras from the standard Ubuntu repositories: 
[code]
sudo apt-get update && sudo apt-get install udev-extras


Do you know how to workaround the problem of unmet dependencies?

If I try [sudo apt-get install udev-extras] it says that it depends on udev:
[INDENT]The following packages have unmet dependencies:
  udev-extras: Depends: udev (>= 136-1) but it is not going to be installed
[/INDENT]I have udev (147~-6.1) on my Ubuntu 9.10

I can not downgrade udev package, so I can not uninstall udev-extras. Nor a I can install udev-extras from downloaded debian package manually.

My repositories list is ok, [sudo apt-get update] also has been run.


Thanks.

---

### Post by JeevesBond on 2010-06-26
Seems that the udev-extras package no longer exists.

These modems are still a problem in Ubuntu, a shame since it should be easy for upstream to fix.

I'm going to do some searching and maybe raise a bug on this.

---

### Post by JeevesBond on 2010-06-26
Sorry for the double-post but I've been doing a bit of research:

Firstly, it *seems* that udev-extras has been rolled into udev, since I was able to run ```
/lib/udev/modem-modeswitch --vendor 0x12d1 --product 0x1446 --type option-zerocd
``` and ```
/etc/udev/rules.d/
``` exists and there's some stuff in it.

Secondly, several (if not all) Huawei USB modems have the same manufacturer and product id, since I'm using an E182E here and its manufacturer and product id strings are the same as the OP (who has an E1550). This means the workaround posted by Macchi should work for other models too.

Thirdly, while the instructions from the OP worked, the long-term solution seems to be to [install usb-modeswitch](https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/521578), which also worked in my case and hopefully others too.

The usb-modeswitch solution seems like a bit of a nasty kludge though, a quick-fix when the problem should be handled by the kernel.

**TL;DR go into *Ubuntu Software Centre*, type 'usb-modeswitch' and *Install*.**

---

### Post by Georg Kaufmann on 2010-08-15
> **Macchi said:**
> Here is a method (workaround) to use the Huawei E1550 Mobile Broadband HSDPA 3.6Mbps modem in Ubuntu with the Network Manager. Open a terminal and follow the three steps: 

1) Install udev-extras from the standard Ubuntu repositories: 
```

sudo apt-get update && sudo apt-get install udev-extras

```2)  Add a custom udev rule for the Huawei E1550 by typing this line:
```

echo 'SUBSYSTEM=="usb", SYSFS{idProduct}=="1446", SYSFS{idVendor}=="12d1", RUN+="/lib/udev/modem-modeswitch --vendor 0x12d1 --product 0x1446 --type option-zerocd"' | sudo tee  /etc/udev/rules.d/45-huawei1550.rules

```3) Configure explicitly the Mobile Broadband on Network Manager according to specific instructions from your provider. In my case I just had to fill in the APN. It is convenient to check the box that the connection will be activated automatically and will be available for all users.



OBS: This modem is interesting due to high flexibility, low cost, and quite reasonable performance for mobile broadband. Here in Sweden they are sold for approx 25€ on prepaid (no contract).
This is only a workaround before a definitive solution is created for udev and/or network manager and/or devicekit. 
The other solutions that I have seen involved installing from source software that is not yet on the repositories. I personally prefer to strive after standardization and resources available on the repositories. Observe that the modem-switch on udev-extras is not the same as usb_modeswitch! I hope that these tools will soon converge upstream.



Hello macchi

i tried to install my huawei1550 with your steps. The last term in the second step doesn't work. Do you know why? I use a netbook with ubuntu 9.10. If I write    sudo tee /lib/udev/rules.d/45-huawei1550.rules    there is an empty line and nothing other.

Greeting from Germany

Georg:(

---

