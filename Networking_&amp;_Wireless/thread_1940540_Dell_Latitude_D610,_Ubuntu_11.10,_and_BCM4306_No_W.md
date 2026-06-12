---
title: "Dell Latitude D610, Ubuntu 11.10, and BCM4306 No Wireless"
date: 2012-03-13
forum: Networking &amp; Wireless
---

### Post by jbruckner on 2012-03-13
Hello Everyone,

I am really hoping to find some solid help here. I have 27 Dell Latitude D610 with BCM4306 ver 3 wireless cards installed. I have to get the wireless up and running so the students at the school I work at can use these computers.

I am an Ubuntu newbie and let me apologize upfront if I seem to not have a clue because I pretty much don't right now.

I have been reading a lot of these forums and doing what they said and was able to get the wireless to work for about 2 minutes, but can not get it back now and have no idea what I did to get it to work. Basically I have done a lot already and probably start by undoing everything I have done but do not know how to do that.

I want to thank everyone for the help up front. Tell me what to do and I will.

---

### Post by chili555 on 2012-03-14
Just 27 laptops? That's all??

All kidding aside, that sounds like an awesome project. First, let's see exactly what you have. Please open a terminal and run and post:```
lspci -nn | grep 0280
rfkill list all
lsmod | grep dell
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

I envision, when we figure out what's missing, we burn a CD and apply the same fix to all 27 laptops. Is that what you'd like?

Please see Private Messages at the top.

---

### Post by sidzen on 2012-03-14
Realisticlly  . . .

"Latitude D610 problems

Some Dell Latitude D610 units with a dedicated ATI x300 graphics card seem to have problems with the audio-out jack. Symptoms of this problem include a noise or whine when an audio device is connected to the audio-out jack. Up to this date Dell does not have a clear solution to this problem.[1][2][3][4]

A number of Dell Latitude D610 units will develop microscopic fractures of the motherboard. Symptoms of this problem may include inability to turn on the computer, unexpected shut down within 30 seconds of being turned on, or visible screen artifacts while in operation. This problem also frequently contributes to the blue screen of death (BSOD) in Windows.

The Dell Latitude D610 was intended to have a 3-4 year life. After this period, some known issues include deterioration of CPU and other issues causing poor performance, especially with newer software."

source -- [https://en.wikipedia.org/wiki/Dell_Latitude#Latitude_D610_problems](https://en.wikipedia.org/wiki/Dell_Latitude#Latitude_D610_problems)

. . . like ubuntu 11.10.

How much RAM is each one maxed out at?  If more than 512, find the good mobos and cpus and match them to maxed RAM machines  Then, you could possibly use lubuntu or peppermint;  if not, antiX is a good choice.

Best wishes from an Old PC junkie!

---

### Post by spikoley on 2012-03-15
I have an Inspiron 6000 with the same BCM4306 wireless card and problem.

lspci
```
Network controller: Broadcom Corporation BCM4306 802.11a/b/g (rev 03)
```

rfkill list all
```

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

lsmod | grep dell
```

dell_laptop            13519  0 
dcdbas                 14098  1 dell_laptop

```

I had this issue before, but when I upgraded to a new version of Ubuntu it started to work.

---

### Post by spikoley on 2012-03-15
I found a solution [here]("http://ubuntuforums.org/showpost.php?p=10796508&postcount=44").

Basically, you download this file [http://www.omattos.com/sites/default...all-fw.tar_.gz](http://www.omattos.com/sites/default...all-fw.tar_.gz).  Then extract it in /lib/firmware/.

---

### Post by jbruckner on 2012-03-15
lspci -nn | grep 0280
03:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

lsmod | grep dell
dell_laptop            13519  0 
dcdbas                 14098  1 dell_laptop

---

### Post by chili555 on 2012-03-15
> Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)Your device is claimed by the usual suspect b43 and ssb. It requires proprietary firmware. Download the attached file to your desktop. Right-click it and select *Extract Here*. Now open a terminal and copy the firmware to the correct location:```
sudo cp Desktop/b43/ /lib/firmware
```Now unload and reload the driver so it grabs the firmware:```
sudo modprobe -r b43
sudo modprobe b43
```Your wireless should now be working.

I'd suggest the folder b43, with its contents, be copied to a CD and the process repeated on the other 26.

Post back if you need further assistance.

---

### Post by jbruckner on 2012-03-15
Chili555,

Followed directions to the letter and still no wireless yet. :(

---

### Post by chili555 on 2012-03-15
Let's do some diagnosis. Please run and post:```
dmesg | grep b43
ls -al /lib/firmware/b43
```Thanks.

---

### Post by jbruckner on 2012-03-15
dmesg | grep b43
[    1.349309] b43-pci-bridge 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   24.459384] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   24.865495] Registered led device: b43-phy0::tx
[   24.865585] Registered led device: b43-phy0::rx
[   24.865661] Registered led device: b43-phy0::radio
[   26.175066] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   26.175072] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   26.175076] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   34.323762] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   34.323767] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   34.323771] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   34.337854] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   34.337860] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   34.337864] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   57.282552] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   57.282558] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   57.282562] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   57.419385] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   57.419390] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   57.419394] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   57.434725] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   57.434731] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   57.434735] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   57.718441] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   57.718446] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   57.718450] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   63.042289] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   63.042295] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   63.042299] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   68.044341] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   68.044347] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   68.044350] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  273.371800] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  273.371810] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[  273.371819] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  273.397554] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  273.397560] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[  273.397564] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  466.264316] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  466.264322] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[  466.264326] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  466.287168] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  466.287174] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[  466.287178] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  467.907623] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  467.907629] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[  467.907633] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  467.930471] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  467.930477] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[  467.930480] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  469.998780] b43-pci-bridge 0000:03:03.0: PCI INT A disabled
[  471.147701] b43-pci-bridge 0000:03:03.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[  471.147721] b43-pci-bridge 0000:03:03.0: restoring config space at offset 0x4 (was 0x0, writing 0xdfcfe000)
[  471.147727] b43-pci-bridge 0000:03:03.0: restoring config space at offset 0x3 (was 0x0, writing 0x4000)
[  471.147734] b43-pci-bridge 0000:03:03.0: restoring config space at offset 0x1 (was 0x0, writing 0x106)
[  471.300071] b43-pci-bridge 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  477.266034] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  477.266040] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[  477.266044] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  477.304915] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  477.304921] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[  477.304925] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.

ls -al /lib/firmware/b43

ls: cannot access /lib/firmware/b43: No such file or directory

---

### Post by chili555 on 2012-03-15
> Now open a terminal and copy the firmware to the correct location:
Code:

sudo cp Desktop/b43/ /lib/firmware

Now unload and reload the driver so it grabs the firmware:
Code:

sudo modprobe -r b43
sudo modprobe b43

I made a mistake and I apologize. Nothing worse than an old newbie!

Please do:```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo modprobe -r b43
sudo modprobe b43
```Be sure that the firmware made it this time:```
ls -al /lib/firmware/b43
```If it went well, you should have wireless and should see many lines like:> -rw-r--r--  1 root root    12 2011-09-16 15:39 ucode32_mimo.fw
-rw-r--r--  1 root root     9 2011-09-16 15:39 ucode33_lcn40.fw
-rw-r--r--  1 root root 21328 2011-09-16 15:39 ucode5.fw
-rw-r--r--  1 root root 23256 2011-09-16 15:39 ucode9.fwYou don't have to post it; just confirm it's there.

---

### Post by jbruckner on 2012-03-17
Ok so everything looks good, but still no wireless. :(

---

### Post by mauleshjani on 2012-03-17
[SIZE=3]dear do this,
 
give this command 1st 

[/SIZE][SIZE=4]sudo lspci -v[/SIZE]
[SIZE=3]

then... give all these commands... u ll succeed...

[SIZE=4]sudo apt-get update[/SIZE][/SIZE][SIZE=4]

sudo apt-get install firmware-b43-installer[/SIZE]


[SIZE=4]sudo apt-get remove bcmwl-kernel-source[/SIZE]


[SIZE=4]sudo reboot[/SIZE]

==================================================  =============================
[SIZE=4]bye  thx[/SIZE]

---

### Post by chili555 on 2012-03-17
> **jbruckner said:**
> Ok so everything looks good, but still no wireless. :(I highly doubt you have bcmwl-kernel-source and it's (non-) removal will not help.

Let's see:```
dmesg | grep b43
rfkill list all
```Thanks.

---

### Post by jbruckner on 2012-03-17
student008@student008-laptop:~$ dmesg | grep b43
[    1.384138] b43-pci-bridge 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   24.759950] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   24.924730] Registered led device: b43-phy0::tx
[   24.924793] Registered led device: b43-phy0::rx
[   24.924844] Registered led device: b43-phy0::radio
[   26.324451] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   26.453553] b43-phy0: Radio hardware status changed to DISABLED
[   26.460101] b43-phy0: Radio turned on by software
[   26.460104] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[  231.462015] b43-pci-bridge 0000:03:03.0: PCI INT A disabled
[  232.632096] b43-pci-bridge 0000:03:03.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[  232.632116] b43-pci-bridge 0000:03:03.0: restoring config space at offset 0x4 (was 0x0, writing 0xdfcfe000)
[  232.632123] b43-pci-bridge 0000:03:03.0: restoring config space at offset 0x3 (was 0x0, writing 0x4000)
[  232.632130] b43-pci-bridge 0000:03:03.0: restoring config space at offset 0x1 (was 0x0, writing 0x106)
[  232.784129] b43-pci-bridge 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
student008@student008-laptop:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

---

### Post by jbruckner on 2012-03-17
[mauleshjani]("http://ubuntuforums.org/member.php?u=1520701"),

Thank you!!! That seems to have worked!  Now only question is how do I find wireless networks? On my mac and my Windows computers it always has something in the top bar and I know there was something on this top bar at one point, but it disappeared while I was trying to get the wireless working.

---

### Post by chili555 on 2012-03-17
> The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.Have you pressed the button?

---

### Post by jbruckner on 2012-03-17
I can toggle the wireless on and off with the function F2, but I am talking about the icon that used to be in the top right corner by the battery and volume icons.

---

### Post by chili555 on 2012-03-17
> **jbruckner said:**
> I can toggle the wireless on and off with the function F2, but I am talking about the icon that used to be in the top right corner by the battery and volume icons.Does it reappear if you do:```
nm-applet &
```If so, can you connect? We can work out how to add the icon back if that does it.

If these are all to be at the same place in the same fixed network, I wonder if you really want Network Manager. Would hard-coding the network details suit better?

---

### Post by jbruckner on 2012-03-17
Wireless still works, but it didn't seem to do anything. This is the read out:

student008@student008-laptop:~$ nm-applet &
[1] 2867
student008@student008-laptop:~$ The program 'nm-applet' can be found in the following packages:
 * network-manager-gnome
 * mythbuntu-diskless-client
Try: sudo apt-get install <selected package>

---

### Post by jbruckner on 2012-03-17
I will be honest with you. Our network is very weak and we are slowly trying to get it to where it should be at. A couple of years ago nothing worked wired so they switched EVERYTHING to wireless and there are many different access points and even more "dead" spots! :( 

Also I have no idea what it means to hard-code something! Sorry

---

### Post by chili555 on 2012-03-17
> **jbruckner said:**
> I will be honest with you. Our network is very weak and we are slowly trying to get it to where it should be at. A couple of years ago nothing worked wired so they switched EVERYTHING to wireless and there are many different access points and even more "dead" spots! :( 

Also I have no idea what it means to hard-code something! SorryIt means you uninstall Network Manager altogether, which would allow users to disconnect, reconnect, roam, etc., and set up two configuration files which specify which network you want and the encryption details and none other.> student008@student008-laptop:~$ nm-applet &
[1] 2867This sort of suggests it's present and running; while this suggests it's not:> $ The program 'nm-applet' can be found in the following packages:
* network-manager-gnome
* mythbuntu-diskless-client
Try: sudo apt-get install <selected package> Wierd! Let us see, please:```
ps aux | grep -e nm -e etwork
```

---

### Post by jbruckner on 2012-03-17
student008@student008-laptop:~$ ps aux | grep -e nm -e etwork
1000      5148  3.6  2.0  84140 21220 ?        Sl   12:52   1:27 /usr/bin/gtk-gnash -u [https://mail.google.com/mail/im/media-api.swf?ver=1.0.2](https://mail.google.com/mail/im/media-api.swf?ver=1.0.2) -U [https://mail.google.com/mail/?ui=2&view=js&name=main,tlist&ver=U2nDw6vlsRE.en.&am=!uO6pQseRvBdZBP0ukMxaQjhuUDLn6jE3Bq03toe4U-D0QAQbityDgxJduGshAtaiGpTP](https://mail.google.com/mail/?ui=2&view=js&name=main,tlist&ver=U2nDw6vlsRE.en.&am=!uO6pQseRvBdZBP0ukMxaQjhuUDLn6jE3Bq03toe4U-D0QAQbityDgxJduGshAtaiGpTP) -x 50333395 -j 1 -k 1 -F 20:21 -P allowfullscreen=true -P allowscriptaccess=sameDomain -P bgcolor=#000000 -P flashvars=dbg=true&ap=previewer&nm=yj_api0&cb=Recv_yj_api0&os=linux&& -P id=flash_yj_api0 -P name=yj_api0 -P pluginspage=http://www.macromedia.com/go/getflashplayer -P quality=high -P seamlesstabbing=false -P src=im/media-api.swf?ver=1.0.2 -P style=width: 100%; height: 100%;  -P type=application/x-shockwave-flash -P wmode=window -
1000      6896  0.0  0.0   4196   748 pts/0    S+   13:32   0:00 grep --color=auto -e nm -e etwork

---

### Post by chili555 on 2012-03-17
Well, I don't see Network Manager running. You evidently don't have the applet because you don't have the underlying application! I'm not sure which Ubuntu 11.10 you can get without it, but let's try the good old manual way. Please run:```
sudo iwlist wlan0 scan
```You needn't post the results, just note the name of your network. Now do:```
sudo iwconfig wlan0 essid yournetwork
```If there is no encryption, then do:```
sudo dhclient wlan0
```If Network Manager is indeed not installed, it ought to get an IP address and be connected.

We can commit the details to a couple of files, or, if it suits your needs better, you can install NM.

---

### Post by homer911 on 2012-05-06
> **chili555 said:**
> I made a mistake and I apologize. Nothing worse than an old newbie!

Please do:```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo modprobe -r b43
sudo modprobe b43
```Be sure that the firmware made it this time:```
ls -al /lib/firmware/b43
```If it went well, you should have wireless and should see many lines like:You don't have to post it; just confirm it's there.

Thank you! I'm a newbie to ubuntu running 12.04 on a D610 - your instructions worked perfectly!  This was doing my head in!

---

### Post by parrbr on 2012-07-28
+1

The instructions found in this thread also worked for 12.04 install on my Dell Precision M70 with BCM4306.

In summary, I had to:
1) extract b43.zip to /lib/firmware/b43. b43.zip is available from various download sites - the copy attached to an earlier post in this thread did not work for me.

2) reinstall firmware-b43-installer to pick up the firmware

---

### Post by thesheckies on 2012-09-30
same issue. followed instructions and wireless connection worked for like a whole five minutes, then stopped working. tried moving closer to router, still only works for 1 minute each time after reboot.  

have dell d600 with ubuntu 12.4(i think). 

Broadcom Corporation BCM4306 802.11a/b/g [14e4:4324] (rev 03)

what should i do? use an older version of Ubuntu? and if so, what is the easiest way to do that?
thanks

---

### Post by chili555 on 2012-10-01
> Broadcom Corporation BCM4306 802.11a/b/g [[COLOR="Red"]14e4:4324[/COLOR]] (rev 03)Please hook up the ethernet temporarily and do:```
sudo apt-get install firmware-b43legacy-installer
sudo modprobe -r b43
sudo modprobe b43
```Any improvement?

---

### Post by Nefarious PhD on 2012-10-01
The solution linked from post #5 worked for me, but not until I followed Chilli's advice in post #7 about unloading and reloading the driver. I had rebooted after following the initial instructions, so I was surprised I still needed to unload and reload the driver to get it picked up.
Oh, and I had to set my router to not hide the SSID (please, no comments about whether that's security); it couldn't find it until I did that, even though I configured the driver with the correct SSID.
Anyway, thanks everyone for taking the time to post these solutions. I'm diving into linux for the first time and I'd not be able to use ubuntu without people like you.

---

### Post by thesheckies on 2012-10-03
thanks for help, but i decided to try linux mint 13 instead. needed to use the MATE version as i believe my d600 has insufficient graphics card.  
 
install b43 (i think) on mint, which i have to say is much easier to install things on than with ubuntu, and after a little playing around, i seem to have the wireless working.
 
may go back to ubuntu or use it on another laptop though, trying to decide still.  hope mint has enough tech support if i need it. will see i guess
thanks

---

### Post by chili555 on 2012-10-03
> **thesheckies said:**
>   hope mint has enough tech support if i need it. will see i guess
thanksA surprising number of posts here are Minty.

---

### Post by unabatedshagie on 2012-10-03
I was going to start a new thread but this is the exact problem I'm having. I've followed these instructions:

> **chili555 said:**
> I made a mistake and I apologize. Nothing worse than an old newbie!

Please do:```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo modprobe -r b43
sudo modprobe b43
```Be sure that the firmware made it this time:```
ls -al /lib/firmware/b43
```If it went well, you should have wireless and should see many lines like:You don't have to post it; just confirm it's there.

However I'm still not getting wifi.

When I run ```
dmesg | grep b43
rfkill list all
```

I get the following: 
```

0: phy0: Wireless LAN
         Soft blocked: no
         Hard blocked: yes
```

I've tried using the fn + F2 key combo to turn on the wifi but that doesn't seem to do anything.

---

### Post by bkratz on 2012-10-03
> **unabatedshagie said:**
> I was going to start a new thread but this is the exact problem I'm having. I've followed these instructions:



However I'm still not getting wifi.

When I run ```
dmesg | grep b43
rfkill list all
```

I get the following: 
```

0: phy0: Wireless LAN
         Soft blocked: no
         Hard blocked: yes
```

I've tried using the fn + F2 key combo to turn on the wifi but that doesn't seem to do anything.

You might post the the outputs of the following commands

lspci -nn | grep 0280

and 
lsmod  

showing the wireless card and the loaded modules, by the way those are little "L's" not ones.

Also, is the a Dell too?

---

### Post by unabatedshagie on 2012-10-03
> **bkratz said:**
> You might post the the outputs of the following commands

lspci -nn | grep 0280

and 
lsmod  

showing the wireless card and the loaded modules, by the way those are little "L's" not ones.

Also, is the a Dell too?

Yes, it's a Dell Latitude D610

**lspci -nn | grep 0280**
```
03:03.0 Network controller [280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
```

**lsmod**
```
Module                  Size  Used by
uas                    17828  0 
usb_storage            39646  2 
b43                   342643  0 
mac80211              436455  1 b43
bcma                   25651  1 b43
ssb                    50691  1 b43
joydev                 17393  0 
snd_intel8x0           33455  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39791  0 
ipw2200               146241  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
libipw                 46701  1 ipw2200
dell_laptop            17767  0 
ppdev                  12849  0 
rfcomm                 38139  0 
cfg80211              178679  4 b43,mac80211,ipw2200,libipw
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
yenta_socket           27465  0 
dcdbas                 14098  1 dell_laptop
psmouse                86486  0 
pcmcia_rsrc            18367  1 yenta_socket
lib80211               14040  2 ipw2200,libipw
snd                    62064  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
i915                  419110  2 
parport_pc             32114  1 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_intel8x0,snd_pcm
serio_raw              13027  0 
mac_hid                13077  0 
drm_kms_helper         45466  1 i915
drm                   197599  3 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
tg3                   141369  0 
```

---

### Post by bkratz on 2012-10-03
[QUOTE=unabatedshagie;12276154]Yes, it's a Dell Latitude D610

**lspci -nn | grep 0280**
```
03:03.0 Network controller [280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
```

Well, we probably will need to end up removing all the b43 module stuff, since b43 in used only for Broadcom devices.  The Intel versions are usually a part of the kernel and work without additional effort.   We probably should wait for Dr. Chili to return and see if he wants to remove the dell-laptop module just to see the effect.   He is the expert and monitors all his old threads, so it will just be a matter of time.  If he does not return, we will probably go ahead, but it would be in your best interest to wait a bit.

---

### Post by chili555 on 2012-10-04
Please do:```
sudo gedit /etc/modules
```If *b43* is in there, remove it. If there are multiple listings, remove all of the *b43*s. Next do:```
sudo modprobe -r dell-laptop
sudo rfkill unblock all
```Does your wireless work now? If so, we'll blacklist dell-laptop.

---

### Post by unabatedshagie on 2012-10-04
[/b]sudo gedit /etc/modules[/b]

Contains some commented out lines of code then the only thing that's uncommented is the letters **lp**

Ran the other two commands but nothing changed.

I should have mentioned (as I didn't realize this was an older thread) it's the latest LTS I'm trying this with (12.4.1)

---

### Post by chili555 on 2012-10-04
Please run:```
sudo rfkill unblock all
rfkill list all
sudo iwlist eth1 scan
```> Contains some commented out lines of code then the only thing that's uncommented is the letters lp
Perfect!

---

### Post by unabatedshagie on 2012-10-04
> **chili555 said:**
> Please run:```
sudo rfkill unblock all
rfkill list all
sudo iwlist eth1 scan
```Perfect!

**rfkill list all**
```
0: phy0: Wireless LAN
             Soft blocked: no
             Hard blocked: yes
```

**sudo iwlist eth1 scan**
```
eth1       No scan results
```

---

### Post by chili555 on 2012-10-05
> 0: phy0: Wireless LAN
             Soft blocked: no
            [COLOR="Red"] Hard blocked: yes[/COLOR]It looks like there is a hardware switch that has your wireless turned off. Can you please find it and switch it on?

---

### Post by unabatedshagie on 2012-10-05
> **chili555 said:**
> It looks like there is a hardware switch that has your wireless turned off. Can you please find it and switch it on?

The only thing I have is a keyboard shortcut (fn + F2) but pressing it doesn't seem to do anything.


Hmmmm, on the off chance I looked in the BIOS, there was a wireless setting which was disabled. I enabled it and restarted. I'm now able to enable/disable the wifi with the Fn + F2 key combo.


Thanks a lot for your help chili555

---

### Post by whizzyfingers on 2012-11-03
> **chili555 said:**
> Your device is claimed by the usual suspect b43 and ssb. It requires proprietary firmware. Download the attached file to your desktop. Right-click it and select *Extract Here*. Now open a terminal and copy the firmware to the correct location:```
sudo cp Desktop/b43/ /lib/firmware
```Now unload and reload the driver so it grabs the firmware:[CODE]sudo modprobe -r b43
......

Thank you,  I've trawled pages and pages of Google results searching for an answer, everything I tried didn't work.
B43-FWcutter, B43 Leagcy drivers. B43 this and that...
..was on the point of giving up and going back to XP when I found your post and B43 zip file..  It worked a treat.  A simple solution in a small paragraph has done what thousands of other advice pages haven't been able to do.. From a  Windows Expert--Linux Newbie
:)

---

### Post by chili555 on 2012-11-03
> **whizzyfingers said:**
> Thank you,  I've trawled pages and pages of Google results searching for an answer, everything I tried didn't work.
B43-FWcutter, B43 Leagcy drivers. B43 this and that...
..was on the point of giving up and going back to XP when I found your post and B43 zip file..  It worked a treat.  A simple solution in a small paragraph has done what thousands of other advice pages haven't been able to do.. From a  Windows Expert--Linux Newbie
:)Happy to help. Your kind comments make all this worthwhile.

We have a great community here and we're happy to help others with problems that we, ourselves struggled with many years and posts ago.

Have fun!

---

