---
title: "Need Wireless help"
date: 2011-03-04
forum: Networking &amp; Wireless
---

### Post by slomo5793 on 2011-03-04
Hi
i recently installed ubuntu netbook remix on my laptop (this is my first experience with ubuntu)
and i am able to use wired internet just fine but when i click the network connection button on the top, next to wireless, it says "device not ready (missing firmware)"
i tried to use the additional drivers application and attempt to activate the driver but it gives me an error
i tried looking for solutions to my porblem, but i really cant find any that work for me
please help me with this
and plz try to keep it on  a noob level
it hasnt even been a week since i installed ubuntu

---

### Post by mikewhatever on 2011-03-04
Make sure to hook up a cable before activating the driver. Can you post the exact error message or use the PrntScrn button to take a screenshot.

---

### Post by slomo5793 on 2011-03-04
here's the error and additional drivers screen

---

### Post by mikewhatever on 2011-03-04
Can you post the output of the **lspci | grep -i net** command. It should show your wifi card model.

---

### Post by slomo5793 on 2011-03-05
the output is:

02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5702X Gigabit Ethernet (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02)

---

### Post by mikewhatever on 2011-03-05
Having searched around, it looks like you chipset, BCM4309, is unsupported, and the best option is to use Ndiswrapper and a Windows driver. Check out the walkthrough.
[http://johnnydopefish.blogspot.com/2009/02/ubuntu-810-dell-inspiron-5100-broadcom.html](http://johnnydopefish.blogspot.com/2009/02/ubuntu-810-dell-inspiron-5100-broadcom.html)

---

### Post by slomo5793 on 2011-03-05
i got up to: mkdir ~/downloads/wireless  and the  cd ~/downloads/wireless

and it returns that it cant create the directory, no such file or directory

when i try to extract the sp33008, it gives me an error saying that

  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/____/Downloads/sp33008 (1).exe or
          /home/___/Downloads/sp33008 (1).exe.zip, and cannot find /home/_____/Downloads/sp33008 (1).exe.ZIP, period.

where _____ is the username i.e. my name

i tried to download from other locations but i get the same error
and i really cant go on further without getting past these steps

---

### Post by chili555 on 2011-03-05
> 02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02)Maybe there's a better way. Please post:```
lspci -nn | grep -i 14e4
```

---

### Post by slomo5793 on 2011-03-05
here is the return to   lspci -nn | grep -i 14e4



02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5702X Gigabit Ethernet [14e4:16a6] (rev 02)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4309 802.11a/b/g [14e4:4324] (rev 02)



btw, how do you guys post the terminal results in a box?

---

### Post by chili555 on 2011-03-05
We post code in a box by highlighting with the mouse and clicking the pound sign **[SIZE="3"]#[/SIZE]** at the top which surrounds the highlighted text in a code block.> Broadcom Corporation BCM4309 802.11a/b/g [[COLOR="Red"]14e4:4324[/COLOR]] (rev 02)Your device is supported by the driver combination ssb and b43. As you have surmised, it requires firmware. The 'Additional Drivers' tool will download it and install it if you have an ethernet connection in order to reach the firmware files. Can you please walk the netbook over to the router, hook up and try again? After a reboot, you should be all set.


PS - For the hard-core student of drivers: ```
$ modinfo ssb | grep 4324
alias:          pci:v0000[COLOR="Red"]14E4[/COLOR]d0000[COLOR="Red"]4324[/COLOR]sv*sd*bc*sc*i*
```

---

### Post by slomo5793 on 2011-03-05
i tried again and i still get the same error as before
i also tried resetting it, but that's no help either

---

### Post by chili555 on 2011-03-05
Please run and post:```
dmesg | grep b43
```Let's see what firmware it wants.

I am wondering why the Additional Drivers tool wants to install b43legacy. I don't believe it's correct for your device.

---

### Post by slomo5793 on 2011-03-05
this is what i get


```
[    1.761471] b43-pci-bridge 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
```


according to mikewhatever above and other people, my card model, b4309, isnt compatible with ubuntu
and according to the walkthrough by johnnydopefish as posted before i need to install ndiswrapper and do some other things, but as i explained, i am getting problems following that walkthrough

---

### Post by chili555 on 2011-03-05
Before we try ndiswrapper, let's try one other thing:> sudo modprobe b43
sudo modprobe ssb
dmesg | grep b43Thanks.

---

### Post by slomo5793 on 2011-03-05
sudo modprobe b43

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: /etc/modprobe.d/blacklist line 8: ignoring bad line starting with 'blackslist'

sudo modprobe ssb

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: /etc/modprobe.d/blacklist line 8: ignoring bad line starting with 'blackslist'

dmesg | grep b43

[    1.761471] b43-pci-bridge 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5



yea....
i tried a bunch of different stuff before regarding this so its blacklisted i guess
could u tell me how to un-blacklist it plz?  :]

---

### Post by bkratz on 2011-03-06
> **chili555 said:**
> Before we try ndiswrapper, let's try one other thing:Thanks.


Dr Chili, just woke up and saw this.

From the table at     [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

it shows the following:

"

PCI-ID    Supported  Chip   Modes  PHY version  Alternative
14e4:4324     no?     ?      ?      ?              wl

"
Maybe it really isn't supported by b43 and needs the STA?

---

### Post by chili555 on 2011-03-06
Please let us see:```
cat /etc/modprobe.d/blacklist
```> dmesg | grep b43

[ 1.761471] b43-pci-bridge 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
That's it? No more lines?

---

### Post by chili555 on 2011-03-06
> **bkratz said:**
> Dr Chili, just woke up and saw this.

From the table at     [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

it shows the following:

"

PCI-ID    Supported  Chip   Modes  PHY version  Alternative
14e4:4324     no?     ?      ?      ?              wl

"
Maybe it really isn't supported by b43 and needs the STA?That puzzles me, too. However, as I said above, *modinfo ssb* suggests it's a b43/ssb device. The best way to be sure is to try with the OP's card.

Gosh, I wish you and I and Iowan had one of everything ever made! We could write a wiki!

---

### Post by slomo5793 on 2011-03-06
yup, thats all i get from dmesg | grep b43

as for cat /etc/modprobe.d/blacklist
i get: 


```
blacklist bcm43xx
blacklist wl
blacklist b43
blacklist b43legacy
blacklist bcm43xx
blacklist wl
blacklist b43
blackslist b43legacy

```

did that just blacklist every driver having to do with wireless?

---

### Post by chili555 on 2011-03-06
> did that just blacklist every driver having to do with wireless?Yes; twice! Let's just try again before we give up on the native drivers:```
sudo rm /etc/modprobe.d/blacklist
```Now reboot and try this:```
dmesg | grep b43
```Thanks.

---

### Post by slomo5793 on 2011-03-06
```
[    1.733339] b43-pci-bridge 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   23.583131] b43legacy-phy0: Broadcom 4306 WLAN found
[   23.608253] b43legacy-phy0 debug: Found PHY: Analog 1, Type 2, Revision 1
[   23.608278] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   23.632113] b43legacy-phy0 debug: Radio initialized
[   24.262974] b43legacy-phy0 debug: Ignoring unconnected 802.11 core
[   24.925769] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[   24.925885] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
```


so should i download the correct firmware from that site?

---

### Post by chili555 on 2011-03-06
You could do that or you could grab the file I've attached. Transfer it to your desktop. Right-click it and select 'Extract Here.' Now, in a terminal, do:```
sudo mkdir /lib/firmware/b43legacy
sudo cp Desktop/ucode4.fw /lib/firmware/b43legacy
sudo rmmod -f b43legacy
sudo modprobe b43legacy
iwconfig
```Is your wireless working now?

---

### Post by slomo5793 on 2011-03-06
when i do the first command, nothing shows up
then when i do the second, it says

```
cp: missing destination file operand after `desktop/ucode4.fw/lib/firmware/b43legacy'
Try `cp --help' for more information.
```

is that supposed to happen?
should i stop or should i continue?

---

### Post by chili555 on 2011-03-06
> desktop/ucode4.fw/lib/firmware/b43legacyThat's not the command. It is:```
sudo cp Desktop/ucode4.fw /lib/firmware/b43legacy

```Desktop is capital D, not lower case, and there is a space in there. I'll exaggerate it for you:```
sudo cp Desktop/ucode4.fw     /lib/firmware/b43legacy
```Linux wants the exact location, spelling, spacing, etc. It won't accept, "Oh well, you know what I mean." I've tried and it just won't budge!

---

### Post by slomo5793 on 2011-03-06
i rlly didnt know the upper case mattered

after doing all that, i get the following for iwconfig


```
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

---

### Post by chili555 on 2011-03-06
Well it rlly does matter.

Now you have an interface wlan0. When you click the Network Manager icon, do you see networks? Can you connect? What does this tell us?```
sudo iwlist wlan0 scan
```

---

### Post by slomo5793 on 2011-03-06
when i click the network manager, the wired connection shows up, which im using and next to wireless network, it says device not ready (firmware missing), which it said before

the result of sudo iwlist wlan0 scan is



```
wlan0     Interface doesn't support scanning : Network is down

```

---

### Post by chili555 on 2011-03-06
Let's check again:```
dmesg | grep b43
```

---

### Post by slomo5793 on 2011-03-06
```
[    1.729447] b43-pci-bridge 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   24.009894] b43legacy-phy0: Broadcom 4306 WLAN found
[   24.048465] b43legacy-phy0 debug: Found PHY: Analog 1, Type 2, Revision 1
[   24.048487] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   24.073335] b43legacy-phy0 debug: Radio initialized
[   24.622026] b43legacy-phy0 debug: Ignoring unconnected 802.11 core
[   25.457069] b43legacy-phy0 ERROR: Firmware file "b43legacy/pcm4.fw" not found or load failed.
[   25.457078] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[10177.119205] b43legacy-phy0 debug: Suspending...
[10177.119213] b43legacy-phy0 debug: Device suspended.
[10177.131231] b43-pci-bridge 0000:02:03.0: PCI INT A disabled
[10177.412063] b43-pci-bridge 0000:02:03.0: BAR 0: set to [mem 0xfafee000-0xfafeffff] (PCI address [0xfafee000-0xfafeffff]
[10177.412102] b43-pci-bridge 0000:02:03.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[10178.271324] b43-pci-bridge 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[10178.797814] b43legacy-phy0 debug: Resuming...
[10178.797821] b43legacy-phy0 debug: Device resumed.
[10180.418992] b43legacy-phy0 ERROR: Firmware file "b43legacy/pcm4.fw" not found or load failed.
[10180.419008] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
```



what is the purpose of dmesg | grep b43?

---

### Post by chili555 on 2011-03-07
We're getting closer; we're just not quite there. Hopefully, this will fix it. Download the attached zip file to your desktop. Right-click it and select 'Extract Here.' Then, in a terminal, do:```
sudo cp Desktop/b43legacy/*  /lib/firmware/b43legacy
```If you are asked if you wish to over-write existing files, say Yes. 

Now do:```
sudo rmmod -f b43legacy
sudo modprobe b43legacy
iwconfig
```If your wireless doesn't come to life, again post:```
dmesg | grep b43
```dmesg is a log file that captures the more significant kernel messages. The simple command dmesg reads out all of them since you last booted. However, that's long and hard to pick out the lines we are interested in. Therefore, we ask for only the messages with b43 in them: dmesg | grep b43.

---

### Post by slomo5793 on 2011-03-07
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!


what kind of magic did you do!!??!?!?

THANK YOU SOOO MUCH BROOOOOOOO

---

### Post by slomo5793 on 2011-03-07
thanks alot for all ur time and effort, it really helped me out

2 things i wanna know though

1.  do i need the files u instructed me to download

2.  could you help me with another problem i have?  :D
(nobody replied on my post yet and its been up for a while)
of course, its totally up to you if u want to or not, u've been such a big help
heres the link:  
[http://ubuntuforums.org/showthread.php?t=1700363]("http://ubuntuforums.org/showthread.php?t=1700363")

---

### Post by chili555 on 2011-03-07
> 1. do i need the files u instructed me to downloadDo you mean do you need to leave them on your desktop? If you copied them to the /lib/firmware/b43legacy file and your wireless is working (Awesome, slomo!!!) then you can delete them from your desktop.

I am sorry, I know next to nothing about X-server issues. I wish I could help.

Glad the wireless is working. Have fun.

---

### Post by irishluck4u2 on 2011-04-25
This cured my wireless problem. I finally found the cure here for my BCM4309 card. I was about to get a wireless adapter. Thank you!

---

### Post by Gavin Fowler on 2011-06-08
This also solved my issue after reinstalling Ubuntu 11.04, where after re-install the syslog was reporting: 

```

ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).

```

which is also related to the following error, when the package fails to install using package manager (where there's a known bug)

```

dpkg: error processing firmware-b43legacy-installer (--configure)
 subprocess installed post-installation script returned error exit status 1

```

The resolve was in post #30, so many thanks to chili555 - I simply followed his instructions and downloaded the attached/extracted zip file (in post #30), created a local /lib/firmware/b43legacy/ folder and copied the contents using "sudo" ie: 

```

sudo mkdir /lib/firmware/b43legacy
sudo cp ~/Download/b43legacy/* /lib/firmware/b43legacy/

```

Many thanks guys, happy camper :)

---

### Post by c.lisco on 2012-08-24
Hi everyone. First of all please forgive my not-so-good english. 

I've got the same problem on my Acer TravalMate2600. Can't get the wireless. I've a BCM4306 rev3. I tried to follow the instructions above but I couldn't fix my problem. 

Would you be so kind to help me? 
Thanks..

---

### Post by chili555 on 2012-08-24
> **c.lisco said:**
> Hi everyone. First of all please forgive my not-so-good english. 

I've got the same problem on my Acer TravalMate2600. Can't get the wireless. I've a BCM4306 rev3. I tried to follow the instructions above but I couldn't fix my problem. 

Would you be so kind to help me? 
Thanks..Yes, but since you don't have the same device, you need a different solution. Please start a new thread and include:```
lspci -nn | grep 0280
```

---

