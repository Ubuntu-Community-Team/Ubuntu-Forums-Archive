---
title: "e173 T-Mobile - any chance??"
date: 2011-03-11
forum: Networking &amp; Wireless
---

### Post by faz. on 2011-03-11
I got an E173 today, it works great in Windows but I am having real problems getting it to work in Ubuntu.

I have tried most of the modeswitch settings and added various lines to files, to no avail. I tried adding it as a mobile broadband, nope. I tried the Vodafone software, which pops up with some settings which no one on the net seems to understand. I am stuck. I really want to get this working!

Treat me as a complete idiot, give me full lines of code to type into the terminal as I am still learning the basics. Just for reference the device is the T-Mobile 615, and I am trying to run it on an EEE PC 900.

I really am stuck so any help would be appreciated.... I can't think of anything I haven't tried. And I can't think of anything I have tried which I have fully understood, either! :)

Cheers

---

### Post by Davaross on 2011-03-11
Try this

First type  sudo apt-get install usb-modeswitch into the terminal.

Then create a new entry  12d1:1c0b in the /etc/usb_modeswitch.d directory  by doing sudo vi /etc/usb_modeswitch.d/12d1:1c0b. The contents of the  file should be: ########################################################
# Huawei E173s
 DefaultVendor= 0x12d1
DefaultProduct= 0x1c0b
 TargetVendor= 0x12d1
TargetProduct= 0x1c05
 CheckSuccess=20
 MessageEndpoint= 0x0f
MessageContent= "55534243123456780000000000000011062000000100000000000000000000"
 save the file and do a sudo usb-modeswitch -c  /etc/usb_modeswitch.d/12d1:1c0b and then sudo modprobe usbserial vendor  0x2d1 product 0x1c05
 Your device should now be working and visible in network manager


Hope this helps!

---

### Post by faz. on 2011-03-11
Tried that, here are the issues:

[I]^[[Auser@ubuntu
user@ubuntu:~$ usb_modeswitch -c /etc/usb_modeswitch.d/12d1:1c0b
Error: Could not find file /etc/usb_modeswitch.d/12d1:1c0b

user@ubuntu:~$ sudo modprobe usbserial vendor = 0x12d1 product = 0x1c05
FATAL: Error inserting usbserial (/lib/modules/2.6.35-22-generic/kernel/drivers/usb/serial/usbserial.ko): Invalid argument
user@ubuntu:~$ 
[/I]

But the file does exist, and contains the correct contents!!!! Very, very frustrating! Just spend 2 hours on Windows trying to install Kaspersky, it is SO SLOW on windows....... I will return the dongle if I don't get it working soon as I feel it unfair that they advertise it as compatible with Ubuntu.

Thanks for your help, annoyed it didn't work :(

---

### Post by llawwehttam on 2011-03-11
> **faz. said:**
> Tried that, here are the issues:

[I]^[[Auser@ubuntu
user@ubuntu:~$ usb_modeswitch -c /etc/usb_modeswitch.d/12d1:1c0b
Error: Could not find file /etc/usb_modeswitch.d/12d1:1c0b

user@ubuntu:~$ sudo modprobe usbserial vendor = 0x12d1 product = 0x1c05
FATAL: Error inserting usbserial (/lib/modules/2.6.35-22-generic/kernel/drivers/usb/serial/usbserial.ko): Invalid argument
user@ubuntu:~$ 
[/I]

But the file does exist, and contains the correct contents!!!! Very, very frustrating! Just spend 2 hours on Windows trying to install Kaspersky, it is SO SLOW on windows....... I will return the dongle if I don't get it working soon as I feel it unfair that they advertise it as compatible with Ubuntu.

Thanks for your help, annoyed it didn't work :(
Could you post the output of :


```
ls* /etc/usb_modeswitch.d/*
```Could be something as small as a typo.

---

### Post by faz. on 2011-03-12
Ok here goes. I did it with the stick in, but it doesn't seem to show on the list, maybe it shouldn't.

Thanks

```
user@ubuntu:~$ ls /etc/usb_modeswitch.d/
0421:060c              0af0:7011  0af0:d033  12d1:101e    19d2:0103
0421:0610              0af0:7031  0af0:d035  12d1:1031    19d2:0115
0471:1210              0af0:7051  0af0:d055  12d1:1414    19d2:1001
0471:1237              0af0:7071  0af0:d057  12d1:1446    19d2:1007
0482:024d              0af0:7111  0af0:d058  12d1:14ad    19d2:1009
04e8:689a              0af0:7211  0af0:d155  12d1:14c1    19d2:1013
04e8:f000              0af0:7251  0af0:d157  12d1:1520    19d2:2000
057c:84ff              0af0:7271  0af0:d255  12d1:1521    19d2:fff5
05c6:1000:sVe=Option   0af0:7301  0af0:d257  12d1:1523    19d2:fff6
05c6:1000:uMa=AnyDATA  0af0:7311  0af0:d357  12d1:1557    1a8d:1000
05c6:1000:uMa=Option   0af0:7361  0b3c:c700  12d1.1c0b    1a8d:1000:uPr=5G
05c6:1000:uMa=SAMSUNG  0af0:7381  0b3c:f000  1410:5010    1ab7:5700
05c6:1000:uMa=Vertex   0af0:7401  0cf3:20ff  1410:5020    1b7d:0700
05c6:2001              0af0:7501  0fce:d0cf  1410:5030    1bbb:f000
05c6:f000              0af0:7601  0fce:d0e1  1410:5031    1c9e:1001
072f:100d              0af0:7701  0fce:d103  1410:5041    1c9e:9200
0930:0d46              0af0:7801  1004:1000  148f:2578    1c9e:9e00
0ace:2011              0af0:7901  1004:607f  16d8:6803    1c9e:f000
0ace:20ff              0af0:8200  1004:613a  16d8:6803:?  1dd6:1000
0af0:6711              0af0:8201  1004:613f  16d8:700a    1e0e:f000
0af0:6731              0af0:8300  1033:0035  16d8:f000    1ee8:0009
0af0:6751              0af0:8302  106c:3b03  198f:bccd    1ee8:0013
0af0:6771              0af0:8304  106c:3b06  19d2:0003    1f28:0021
0af0:6791              0af0:8400  1076:7f40  19d2:0026    1fac:0130
0af0:6811              0af0:c031  1199:0fff  19d2:0040
0af0:6911              0af0:c100  1266:1000  19d2:0053
0af0:6951              0af0:d013  12d1:1001  19d2:0083
0af0:6971              0af0:d031  12d1:1003  19d2:0101
user@ubuntu:~$
```

---

### Post by graysonc on 2011-03-12
> **faz. said:**
> I got an E173 today, it works great in Windows but I am having real problems getting it to work in Ubuntu.

I have tried most of the modeswitch settings and added various lines to files, to no avail. I tried adding it as a mobile broadband, nope. I tried the Vodafone software, which pops up with some settings which no one on the net seems to understand. I am stuck. I really want to get this working!

Treat me as a complete idiot, give me full lines of code to type into the terminal as I am still learning the basics. Just for reference the device is the T-Mobile 615, and I am trying to run it on an EEE PC 900.

I really am stuck so any help would be appreciated.... I can't think of anything I haven't tried. And I can't think of anything I have tried which I have fully understood, either! :)

Cheers
I have and E173 working in Kubuntu 10.10 and 10.04. The instructions I followed are [here]("http://sussexcomputerworks.co.uk/computer-services-and-web-design/tech-stuff/43-linux/76-kubuntu-1004-and-the-t-mobile-broadband-615-usb-device.html")

---

### Post by llawwehttam on 2011-03-12
> **faz. said:**
> Ok here goes. I did it with the stick in, but it doesn't seem to show on the list, maybe it shouldn't.

Thanks

```
user@ubuntu:~$ ls /etc/usb_modeswitch.d/
0421:060c              0af0:7011  0af0:d033  12d1:101e    19d2:0103
0421:0610              0af0:7031  0af0:d035  12d1:1031    19d2:0115
0471:1210              0af0:7051  0af0:d055  12d1:1414    19d2:1001
0471:1237              0af0:7071  0af0:d057  12d1:1446    19d2:1007
0482:024d              0af0:7111  0af0:d058  12d1:14ad    19d2:1009
04e8:689a              0af0:7211  0af0:d155  12d1:14c1    19d2:1013
04e8:f000              0af0:7251  0af0:d157  12d1:1520    19d2:2000
057c:84ff              0af0:7271  0af0:d255  12d1:1521    19d2:fff5
05c6:1000:sVe=Option   0af0:7301  0af0:d257  12d1:1523    19d2:fff6
05c6:1000:uMa=AnyDATA  0af0:7311  0af0:d357  12d1:1557    1a8d:1000
05c6:1000:uMa=Option   0af0:7361  0b3c:c700  12d1.1c0b    1a8d:1000:uPr=5G
05c6:1000:uMa=SAMSUNG  0af0:7381  0b3c:f000  1410:5010    1ab7:5700
05c6:1000:uMa=Vertex   0af0:7401  0cf3:20ff  1410:5020    1b7d:0700
05c6:2001              0af0:7501  0fce:d0cf  1410:5030    1bbb:f000
05c6:f000              0af0:7601  0fce:d0e1  1410:5031    1c9e:1001
072f:100d              0af0:7701  0fce:d103  1410:5041    1c9e:9200
0930:0d46              0af0:7801  1004:1000  148f:2578    1c9e:9e00
0ace:2011              0af0:7901  1004:607f  16d8:6803    1c9e:f000
0ace:20ff              0af0:8200  1004:613a  16d8:6803:?  1dd6:1000
0af0:6711              0af0:8201  1004:613f  16d8:700a    1e0e:f000
0af0:6731              0af0:8300  1033:0035  16d8:f000    1ee8:0009
0af0:6751              0af0:8302  106c:3b03  198f:bccd    1ee8:0013
0af0:6771              0af0:8304  106c:3b06  19d2:0003    1f28:0021
0af0:6791              0af0:8400  1076:7f40  19d2:0026    1fac:0130
0af0:6811              0af0:c031  1199:0fff  19d2:0040
0af0:6911              0af0:c100  1266:1000  19d2:0053
0af0:6951              0af0:d013  12d1:1001  19d2:0083
0af0:6971              0af0:d031  12d1:1003  19d2:0101
user@ubuntu:~$
```

Looks like the file you tried to create is still not there. No idea why though.

---

### Post by faz. on 2011-03-12
Hmmm I will have a go with the instructions again then. 

Will take it back if I can't get it working, my netbook is SO slow with XP!

Cheers

---

### Post by faz. on 2011-03-12
Ok uninstalled both of the modeswitch things...... maybe this is the source of the problem????

```
faz@ubuntu:~$ sudo apt-get usb-modeswitch
[sudo] password for faz: 
E: Invalid operation usb-modeswitch
faz@ubuntu:~$ 

```

---

### Post by faz. on 2011-03-13
Bump, and I found this:

[http://translate.google.com/translate?js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&sl=auto&tl=en&u=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D1634458&act=url](http://translate.google.com/translate?js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&sl=auto&tl=en&u=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D1634458&act=url)

This SHOULD work, as it's the exact modem, but I get this:

```
faz@ubuntu:~$ sudo usb_modeswitch-c / etc/usb_modeswitch.d/E173s
[sudo] password for faz: 
sudo: usb_modeswitch-c: command not found
faz@ubuntu:~$ 

```

Both USB_Modeswitch thingys are installed, but just don't appear as a command. I am getting to the end of my tether, I have spent my whole weekend trying to get this to work and quite frankly it is boring. I am downloading ubuntu netbook edition and I will reinstall it. Then I will try again. I would not be surprised if I can't reinstall it....... So annoyed.

---

### Post by alexfish on 2011-03-13
> **faz. said:**
> Bump, and I found this:

[http://translate.google.com/translate?js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&sl=auto&tl=en&u=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D1634458&act=url](http://translate.google.com/translate?js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&sl=auto&tl=en&u=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D1634458&act=url)

This SHOULD work, as it's the exact modem, but I get this:

```
faz@ubuntu:~$ sudo usb_modeswitch-c / etc/usb_modeswitch.d/E173s
[sudo] password for faz: 
sudo: usb_modeswitch-c: command not found
faz@ubuntu:~$ 

```Both USB_Modeswitch thingys are installed, but just don't appear as a command. I am getting to the end of my tether, I have spent my whole weekend trying to get this to work and quite frankly it is boring. I am downloading ubuntu netbook edition and I will reinstall it. Then I will try again. I would not be surprised if I can't reinstall it....... So annoyed.

Hi

there are spacing errors in the code

```
sudo usb_modeswitch -c /etc/usb_modeswitch.d/E173s
```

---

### Post by faz. on 2011-03-13
Ok will give that a try, I don't hold out much hope though.

I had a smashing idea to try the whole dongle thing on my desktop editon of Ubuntu, to see if I had mucked it up on my netbook, but I got a large error on startup. I reinstalled Ubuntu and it still had the same error. I got bored and gave up. I just spent 2 hours updating kaspersky on my netbook (the read/write on the SSD is too slow).

I will boot into Ubuntu and try it.

Is there any way I can reset all the packages to default, effectively returning Ubuntu to factory defaults (stock settings)? I think I have mucked up the whole 'usb-modeswitch' stuff somehow.

---

### Post by faz. on 2011-03-13
OK I may have made some progress.

I got it to work....... sort of. Followed the translated instructions to the end, got all the right messages, restarted, and my device is now assigned 12d1:1c05 as opposed to 1c0b, but it will not show in the network drop down thing.......... why the heck not!?

Do you think the problem may lie in that it is auto connecting to my home wifi?? It's extremely annoying though! nothing should be stopping it now!!!!!!!!!!!!!!


hmmm and when I unplugged it and plugged it back in, it reverted to the old type....... damn thing

---

### Post by alexfish on 2011-03-13
hi

can try and modprobe serial driver

```
sudo modprobe usbserial vendor=0x12d1 product=0x1c05
```

if this works then will post details of how to do udev rules

this will save having to use the command line

---

### Post by faz. on 2011-03-13
YES!!!!!!!!

Perfect!

When I plug in the device, I did:

usb-modeswitch XXXXXXXXXXXXXXXXXXXXXXXX

then

modprobe

then it appears top right corner "connected: t-mobile UK"!!!

I am so pleased, this has made all the work worth it. Will never have to use slow, slow XP again!!!

thankyou so much for your help, though I do wonder if there is a way of automating the connection when I plug in the usb stick? I don't fancy having to do terminal every time I connect.

thanks again very much, so pleased.

looking at the files again, it should be in this file that the modeswitch is automated: 40-usb_modeswitch.rules - I will check later. I must do some work !

---

### Post by alexfish on 2011-03-13
hi can try these rules

add to 40-usb_modeswitch.rules
```
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1c0b", RUN+="usb_modeswitch '%b/%k'"
```not sure if have to rename the /etc/usb_modeswitch.d/file to 12d1:1c0b
but try first

then 
```
sudo gedit /etc/udev/rules.d/huawie_usb_serial.rules
```add the line to empty file
```
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1c05", RUN+="/sbin/modprobe usbserial vendor=0x12d1 product=0x1c05"
```

save and exit

alexfish

---

### Post by faz. on 2011-03-13
Hmm yeah that didn't seem to work either, not to worry, I am happy enough just going to terminal and I can easily just press UP and do the last command, I don't really use it for anything else.

Thanks again for your help

Actually I have an idea, could I make a file which is like a windows batch file, which would enter the two lines into the terminal and execute them automatically???? This way I could put this on the desktop and call it "connect" or something.

---

### Post by alexfish on 2011-03-13
can post contents of the 40-usb_modeswitch.rules

need to see where the new lines have been placed. also did you rename the file as suggested

do usb-serial driver load after modeswitching

Can also post which version of Ubuntu been used

can also try loading the option driver with this command , disable the modprobe rule ,place a # at front of line , switch the device then try this command
```
echo "12d1 1c05" >/sys/bus/usb-serial/drivers/option1/new_id
```


alexfish

---

### Post by faz. on 2011-03-13
Unbelievable you are!!

I had an empty file: 12d1:1c0b, so I copied the contents of the E173s file into it, popped in the flash drive for a quick test, and hey presto, it worked!!!!!!

Will post the contents of the 40 file anyway, just incase you want to have a look! So now it is all fully automated!!!!!!!!!! perfect. Couldn't be happier!

Thanks very much for your help once again

---

### Post by faz. on 2011-03-13
```
# Part of usb-modeswitch-data, version 20100825
#
# This file is intended for USB_ModeSwitch version >= 1.1.4
# but will not break anything if used with versions >= 1.0.3
#

ACTION!="add", GOTO="modeswitch_rules_end"

# This adds a symlink "gsmmodem[n]" to ttyUSB ports with interrupt transfer;
# will work only with wrapper from 1.1.4 and above (otherwise ignored)
KERNEL=="ttyUSB*", DRIVERS=="option1|usbserial", PROGRAM="/usr/sbin/usb_modeswitch_dispatcher --symlink-name %p", SYMLINK="%c"


SUBSYSTEM!="usb", GOTO="modeswitch_rules_end"

# This adds the device ID to the "option" driver after a warm boot
# in cases when the device is yet unknown to the driver
ATTR{bInterfaceClass}=="ff", ATTR{bInterfaceNumber}=="00", RUN+="usb_modeswitch --driver-bind %p %s{idVendor} %s{idProduct} %E{PRODUCT}"

# Most known install partitions are on interface 0, one on 5, one on 9
ATTRS{bInterfaceNumber}!="0[059]", GOTO="modeswitch_rules_end"

# only storage class devices are handled; negative
# filtering here would exclude some quirky devices
ATTRS{bDeviceClass}=="08", GOTO="modeswitch_rules_begin"
ATTRS{bInterfaceClass}=="08", GOTO="modeswitch_rules_begin"
GOTO="modeswitch_rules_end"


LABEL="modeswitch_rules_begin"

# Nokia CS-10
ATTRS{idVendor}=="0421", ATTRS{idProduct}=="060c", RUN+="usb_modeswitch '%b/%k'"

# Nokia CS-15
ATTRS{idVendor}=="0421", ATTRS{idProduct}=="0610", RUN+="usb_modeswitch '%b/%k'"

# Vodafone MD950 (Wisue Technology)
ATTRS{idVendor}=="0471", ATTRS{idProduct}=="1210", RUN+="usb_modeswitch '%b/%k'"

# Philips TalkTalk (NXP Semiconductors "Dragonfly")
ATTRS{idVendor}=="0471", ATTRS{idProduct}=="1237", RUN+="usb_modeswitch '%b/%k'"

# Kyocera W06K CDMA modem
ATTRS{idVendor}=="0482", ATTRS{idProduct}=="024d", ATTRS{bConfigurationValue}=="1", RUN+="usb_modeswitch '%b/%k'"

# Samsung GT-B3730
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="689a", RUN+="usb_modeswitch '%b/%k'"

# Samsung U209
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="f000", RUN+="usb_modeswitch '%b/%k'"

# AVM Fritz!Wlan USB Stick N
ATTRS{idVendor}=="057c", ATTRS{idProduct}=="84ff", RUN+="usb_modeswitch '%b/%k'"

# Samsung SGH-Z810, Older Option devices, Vertex Wireless 100 Series, AnyDATA devices
ATTRS{idVendor}=="05c6", ATTRS{idProduct}=="1000", RUN+="usb_modeswitch '%b/%k'"

# D-Link DWM-162-U5, Micromax MMX 300c
ATTRS{idVendor}=="05c6", ATTRS{idProduct}=="2001", RUN+="usb_modeswitch '%b/%k'"

# Siptune LM-75 ("LinuxModem")
ATTRS{idVendor}=="05c6", ATTRS{idProduct}=="f000", RUN+="usb_modeswitch '%b/%k'"

# InfoCert Business Key (SmartCard/Reader emulation)
ATTRS{idVendor}=="072f", ATTRS{idProduct}=="100d", RUN+="usb_modeswitch '%b/%k'"

# Toshiba G450
ATTRS{idVendor}=="0930", ATTRS{idProduct}=="0d46", RUN+="usb_modeswitch '%b/%k'"

# Zydas ZD1211RW WLAN USB, Sphairon HomeLink 1202 (Variant 1)
ATTRS{idVendor}=="0ace", ATTRS{idProduct}=="2011", RUN+="usb_modeswitch '%b/%k'"

# Zydas ZD1211RW WLAN USB, Sphairon HomeLink 1202 (Variant 2)
ATTRS{idVendor}=="0ace", ATTRS{idProduct}=="20ff", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="6711", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="6731", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="6751", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="6771", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="6791", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="6811", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="6911", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="6951", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="6971", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="7011", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="7031", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="7051", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="7071", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="7111", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="7211", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="7251", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="7271", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="7301", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="7311", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="7361", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="7381", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="7401", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="7501", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="7601", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="7701", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="7801", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="7901", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="8200", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="8201", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="8300", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="8302", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="8304", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="8400", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="c031", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="c100", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="d013", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="d031", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="d033", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="d035", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="d055", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="d057", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="d058", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="d155", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="d157", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="d255", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="d257", RUN+="usb_modeswitch '%b/%k'"

# Option HSO device
ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="d357", RUN+="usb_modeswitch '%b/%k'"

# Olivetti Olicard 100 and others
ATTRS{idVendor}=="0b3c", ATTRS{idProduct}=="c700", RUN+="usb_modeswitch '%b/%k'"

# Olivetti Olicard 145
ATTRS{idVendor}=="0b3c", ATTRS{idProduct}=="f000", RUN+="usb_modeswitch '%b/%k'"

# Atheros Wireless / Netgear WNDA3200
ATTRS{idVendor}=="0cf3", ATTRS{idProduct}=="20ff", RUN+="usb_modeswitch '%b/%k'"

# Sony Ericsson MD300
ATTRS{idVendor}=="0fce", ATTRS{idProduct}=="d0cf", RUN+="usb_modeswitch '%b/%k'"

# Sony Ericsson MD400
ATTRS{idVendor}=="0fce", ATTRS{idProduct}=="d0e1", RUN+="usb_modeswitch '%b/%k'"

# Rogers Rocket Stick (a Sony Ericsson device)
ATTRS{idVendor}=="0fce", ATTRS{idProduct}=="d103", RUN+="usb_modeswitch '%b/%k'"

# LG LDU-1900D EV-DO (Rev. A)
ATTRS{idVendor}=="1004", ATTRS{idProduct}=="1000", RUN+="usb_modeswitch '%b/%k'"

# LG HDM-2100 (EVDO Rev.A USB modem)
ATTRS{idVendor}=="1004", ATTRS{idProduct}=="607f", RUN+="usb_modeswitch '%b/%k'"

# LG L-05A
ATTRS{idVendor}=="1004", ATTRS{idProduct}=="613a", RUN+="usb_modeswitch '%b/%k'"

# LG LUU-2100TI (aka AT&T USBConnect Turbo)
ATTRS{idVendor}=="1004", ATTRS{idProduct}=="613f", RUN+="usb_modeswitch '%b/%k'"

# Huawei E630
ATTRS{idVendor}=="1033", ATTRS{idProduct}=="0035", RUN+="usb_modeswitch '%b/%k'"

# UTStarcom UM175 (distributor "Alltel")
ATTRS{idVendor}=="106c", ATTRS{idProduct}=="3b03", RUN+="usb_modeswitch '%b/%k'"

# UTStarcom UM185E (distributor "Alltel")
ATTRS{idVendor}=="106c", ATTRS{idProduct}=="3b06", RUN+="usb_modeswitch '%b/%k'"

# Sagem F@ST 9520-35-GLR
ATTRS{idVendor}=="1076", ATTRS{idProduct}=="7f40", RUN+="usb_modeswitch '%b/%k'"

# Sierra devices (specific driver)
ATTRS{idVendor}=="1199", ATTRS{idProduct}=="0fff", RUN+="usb_modeswitch '%b/%k'"

# Digicom 8E4455 (and all Pirelli devices - EXPERIMENTAL)
ATTRS{idVendor}=="1266", ATTRS{idProduct}=="1000", RUN+="usb_modeswitch '%b/%k'"

# Huawei E169
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1001", RUN+="usb_modeswitch '%b/%k'"

# Huawei E220, E230, E270, E870
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1003", RUN+="usb_modeswitch '%b/%k'"

# Huawei U7510 / U7517
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="101e", RUN+="usb_modeswitch '%b/%k'"

# Huawei U8110 (Android smartphone)
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1031", RUN+="usb_modeswitch '%b/%k'"

# Huawei E180
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1414", RUN+="usb_modeswitch '%b/%k'"

# Huawei, newer modems
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1446", RUN+="usb_modeswitch '%b/%k'"

# Vodafone (Huawei) K3806
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="14ad", RUN+="usb_modeswitch '%b/%k'"

# Vodafone (Huawei) K4605
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="14c1", RUN+="usb_modeswitch '%b/%k'"

# Huawei K3765
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1520", RUN+="usb_modeswitch '%b/%k'"

# Huawei K4505
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1521", RUN+="usb_modeswitch '%b/%k'"

# Huawei R201
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1523", RUN+="usb_modeswitch '%b/%k'"

# Huawei E173
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1557", RUN+="usb_modeswitch '%b/%k'"

# Huawei E173s
ATTRS{idVendor}=="12d1", ATTRS{idProduct}=="1c0b", RUN+="usb_modeswitch '%b/%k'"

# Novatel Wireless devices
ATTRS{idVendor}=="1410", ATTRS{idProduct}=="5010", RUN+="usb_modeswitch '%b/%k'"

# Novatel MC990D
ATTRS{idVendor}=="1410", ATTRS{idProduct}=="5020", RUN+="usb_modeswitch '%b/%k'"

# Novatel U760
ATTRS{idVendor}=="1410", ATTRS{idProduct}=="5030", RUN+="usb_modeswitch '%b/%k'"

# Novatel MC760 3G
ATTRS{idVendor}=="1410", ATTRS{idProduct}=="5031", RUN+="usb_modeswitch '%b/%k'"

# Novatel Generic MiFi 2352 / Vodafone MiFi 2352
ATTRS{idVendor}=="1410", ATTRS{idProduct}=="5041", RUN+="usb_modeswitch '%b/%k'"

# Motorola 802.11 bg WLAN (TER/GUSB3-E)
ATTRS{idVendor}=="148f", ATTRS{idProduct}=="2578", RUN+="usb_modeswitch '%b/%k'"

# C-motech D-50 (aka "CDU-680"), C-motech D-50 (aka "CDU-680")
ATTRS{idVendor}=="16d8", ATTRS{idProduct}=="6803", RUN+="usb_modeswitch '%b/%k'"

# C-motech CHU-629S
ATTRS{idVendor}=="16d8", ATTRS{idProduct}=="700a", RUN+="usb_modeswitch '%b/%k'"

# C-motech CGU-628 (aka "Franklin Wireless CGU-628A" aka "4G Systems XS Stick W12")
ATTRS{idVendor}=="16d8", ATTRS{idProduct}=="f000", RUN+="usb_modeswitch '%b/%k'"

# Beceem BCSM250
ATTRS{idVendor}=="198f", ATTRS{idProduct}=="bccd", RUN+="usb_modeswitch '%b/%k'"

# ZTE MU351
ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="0003", RUN+="usb_modeswitch '%b/%k'"

# ZTE AC581
ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="0026", RUN+="usb_modeswitch '%b/%k'"

# Vodafone (ZTE) K2525
ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="0040", RUN+="usb_modeswitch '%b/%k'"

# ZTE MF110 (Variant)
ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="0053", RUN+="usb_modeswitch '%b/%k'"

# ZTE MF110 (Variant)
ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="0083", RUN+="usb_modeswitch '%b/%k'"

# Vodafone (ZTE) K4505-Z
ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="0101", RUN+="usb_modeswitch '%b/%k'"

# ZTE MF112
ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="0103", RUN+="usb_modeswitch '%b/%k'"

# ZTE MF651
ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="0115", RUN+="usb_modeswitch '%b/%k'"

# Vodafone (ZTE) K3805-Z
ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="1001", RUN+="usb_modeswitch '%b/%k'"

# Vodafone (ZTE) K3570-Z
ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="1007", RUN+="usb_modeswitch '%b/%k'"

# Vodafone (ZTE) K3571-Z
ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="1009", RUN+="usb_modeswitch '%b/%k'"

# Vodafone (ZTE) K3806-Z
ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="1013", RUN+="usb_modeswitch '%b/%k'"

# ZTE devices
ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="2000", RUN+="usb_modeswitch '%b/%k'"

# ZTE "fff" devices 1
ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="fff5", RUN+="usb_modeswitch '%b/%k'"

# ZTE "fff" devices 2
ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="fff6", RUN+="usb_modeswitch '%b/%k'"

# BandRich BandLuxe C170, BandLuxe C270, BandLuxe C120
ATTRS{idVendor}=="1a8d", ATTRS{idProduct}=="1000", RUN+="usb_modeswitch '%b/%k'"

# Hummer DTM5731 
ATTRS{idVendor}=="1ab7", ATTRS{idProduct}=="5700", RUN+="usb_modeswitch '%b/%k'"

# EpiValley SEC-7089 (featured by Alegro and Starcomms / iZAP)
ATTRS{idVendor}=="1b7d", ATTRS{idProduct}=="0700", RUN+="usb_modeswitch '%b/%k'"

# Alcatel X200/X060S
ATTRS{idVendor}=="1bbb", ATTRS{idProduct}=="f000", RUN+="usb_modeswitch '%b/%k'"

# Alcatel One Touch X020
ATTRS{idVendor}=="1c9e", ATTRS{idProduct}=="1001", RUN+="usb_modeswitch '%b/%k'"

# MyWave SW006 Sport Phone/Modem Combination
ATTRS{idVendor}=="1c9e", ATTRS{idProduct}=="9200", RUN+="usb_modeswitch '%b/%k'"

# BSNL Capitel
ATTRS{idVendor}=="1c9e", ATTRS{idProduct}=="9e00", RUN+="usb_modeswitch '%b/%k'"

# MobiData MBD-200HU and others
ATTRS{idVendor}=="1c9e", ATTRS{idProduct}=="f000", RUN+="usb_modeswitch '%b/%k'"

# Solomon S3Gm-660
ATTRS{idVendor}=="1dd6", ATTRS{idProduct}=="1000", RUN+="usb_modeswitch '%b/%k'"

# Option iCON 210, PROLiNK PHS100, Hyundai MB-810, A-Link 3GU
ATTRS{idVendor}=="1e0e", ATTRS{idProduct}=="f000", RUN+="usb_modeswitch '%b/%k'"

# Onda MW833UP
ATTRS{idVendor}=="1ee8", ATTRS{idProduct}=="0009", RUN+="usb_modeswitch '%b/%k'"

# Onda MW833UP
ATTRS{idVendor}=="1ee8", ATTRS{idProduct}=="0013", RUN+="usb_modeswitch '%b/%k'"

# Cricket A600
ATTRS{idVendor}=="1f28", ATTRS{idProduct}=="0021", RUN+="usb_modeswitch '%b/%k'"

# Franklin Wireless U210
ATTRS{idVendor}=="1fac", ATTRS{idProduct}=="0130", RUN+="usb_modeswitch '%b/%k'"

LABEL="modeswitch_rules_end"
```

---

### Post by faz. on 2011-03-13
Marked as solved

Final message for those who found this after hours of frustrated searching (as I did for other threads)

Follow this to the letter (but watch the spacing between modeswitch and the -c, as well as the /usb not / SPACE usb):

[http://translate.google.com/translate?js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&sl=auto&tl=en&u=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D1634458&act=url](http://translate.google.com/translate?js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&sl=auto&tl=en&u=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D1634458&act=url)

I am fairly confident I understand it a lot better now, so could fix any problems and maybe even install another :o

Thanks again for all the help

---

