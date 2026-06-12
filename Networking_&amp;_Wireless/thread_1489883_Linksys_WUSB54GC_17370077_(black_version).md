---
title: "Linksys WUSB54GC 1737:0077 (black version)"
date: 2010-05-21
forum: Networking &amp; Wireless
---

### Post by 10.04LinuxDan on 2010-05-21
Hi I recently saved an old desktop with Ubuntu 10.04. It will now have a new home at my new desk. However I cannot get the above usb wifi adapter working and have no idea what to do . What exactly should i do to get this wireless card working? If this involves command line please do a step by step. Thanks very much.
Long Live Linux

---

### Post by chili555 on 2010-05-21
Please open a terminal and let's get our geek on! Please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```The text editor gedit will pop open and we will add three lines at the end:```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread carefully. Save and close gedit. Reboot.

Click the Network Manager icon, see your network and connect. Use your working wireless connection to post back and report your success.

---

### Post by b k on 2010-05-21
> **chili555 said:**
> Please open a terminal and let's get our geek on! Please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```The text editor gedit will pop open and we will add three lines at the end:```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread carefully. Save and close gedit. Reboot.

Click the Network Manager icon, see your network and connect. Use your working wireless connection to post back and report your success.

Apologies to 10.04LinuxDan for butting in.

I have a fresh install of Ubuntu 10.04 LTS and use the same Linksys wusb54gc v3 adapter.
My wireless network is 'hidden' with authmode : wpa2-psk and encryption : AES

I can confirm that chili555's solution works very well.
The only problem is that I have to re-enter my network password every time I want to connect.
I did not enter any Keyring password but just pressed cancel.
Poking around within network connections, I noticed that the password cannot be saved.

*[COLOR=Blue]Also the wireless adapter is unable to automatically connect to the hidden wireless network upon bootup although I have ticked this option in the network connection setting[/COLOR].*
(for symptoms - refer to post #10).

Would appreciate any guidance to solve the problem.

On behalf of the many newbies here, thank you chili555 for your invaluable contributions to this forum.

Let me know if you need any further info.

Update : 

[COLOR=Blue]Thanks to  mawil1013 at [http://ubuntuforums.org/showthread.php?t=1491965](http://ubuntuforums.org/showthread.php?t=1491965) , I was able to resolve the issue by going to *System, Administration, Login Screen* and **[COLOR=Red]unchecking/untic[/COLOR]**[COLOR=Red]king[/COLOR] Log in as XXXX automatically (this was previously set to auto login on bootup)[/COLOR].

---

### Post by chili555 on 2010-05-22
Thank you very much for your very kind comments. 

If you right-click the Network Manager icon and select Edit Connections, select Wireless, can you highlight your network and click Edit and then check the Connect Automatically box?

I am not really sure as I have not ever worked with hidden ESSIDs.

---

### Post by 10.04LinuxDan on 2010-05-22
Hi everyone thanks for the help. I just thought i Would give more detail. I would like to say that before posting my initial question i had the rt2870 driver installed. That is all that I did. Is that the right thing to do is there anything else i need to do. And in blacklist gedit do i skip a line then add the three lines or just add them right at the end. Also If there is anything else that would be great. When I click on the network icon in the top right I see my wired connection but no wireless section. Did I do anything wrong? Again thanks so much for the help.

---

### Post by chili555 on 2010-05-22
> i had the rt2870 driver installed. That is all that I did. Is that the right thing to doHow? The native driver? Compiled from a downloaded tar.gz? Ndiswrapper?> And in blacklist gedit do i skip a line then add the three lines It makes no difference, but that will work fine.

---

### Post by 10.04LinuxDan on 2010-05-22
I got the rt2870.inf from the disk that came with the adapter. I then used the ndisgtk frontend to intall it and checked on the terminal ndiswrapper -l and saw that the driver was installed using rt2800 as alternate. From here it still doesn't work and I have no idea what to do. By the way i did that blacklist text that you gave me. I haven't noticed anything so far but thank you very much for helping me and being patient with me. Im new to Linux as you can probably see. However I am comfortable with terminal if commands are given for me to use. 
Thanks
10.04LinuxDan

---

### Post by chili555 on 2010-05-22
Let's see what's loading or not:```
lsmod | grep -e rt2 -e ndis
ndiswrapper -l
```Thanks.

---

### Post by 10.04LinuxDan on 2010-05-22
this is what came up after that command
[COLOR=Red]ndis[/COLOR]wrapper                        184677    0

where should i go from here.

---

### Post by b k on 2010-05-22
> **chili555 said:**
> Thank you very much for your very kind comments. 

If you right-click the Network Manager icon and select Edit Connections, select Wireless, can you highlight your network and click Edit and then check the Connect Automatically box?

I am not really sure as I have not ever worked with hidden ESSIDs.

When I did what you suggested, 'unlock login keyring' message appears after I clicked Edit.
After pressing cancel, I noted that Connect Automatically box was already checked previously.

Upon boot up, 'unlock login keyring' message appears.
Canceling this message brings up 'wireless network authentication required'.
Sometimes the  'unlock login keyring' message appears again.
Canceling the keyring message again and entering the wireless network password enables me to establish wireless network connection.

Once the connection is established, it performs near flawlessly as far as I can tell.

Any further suggestions to try and lick the problem?

Thanks

---

### Post by 10.04LinuxDan on 2010-05-22
sorry i forgot the second command now it says that then warning about config files then it says
rt2870 : driver installed
          device (1737:0077) present (alternate driver: rt2800usb)

---

### Post by chili555 on 2010-05-22
> **10.04LinuxDan said:**
> sorry i forgot the second command now it says that then warning about config files then it says
rt2870 : driver installed
          device (1737:0077) present (alternate driver: rt2800usb)Looks good! Now let's look at:```
iwconfig
sudo iwlist wlan0 scan
```

---

### Post by 10.04LinuxDan on 2010-05-22
i get this 

lo no wireless extensions

eth0 no wireless extensions

wlan0 Interface doesn't support scanning

by the way this was the xp driver from the cd i installed i forgot if i mentioned that.

---

### Post by chili555 on 2010-05-22
Did you drag and drop just the .inf file from the CD to your home directory or did you also get the accompanying .sys file? Also, please let us see:```
dmesg | grep ndis
```Thanks.

---

### Post by 10.04LinuxDan on 2010-05-22
no only the inf file what should i do with the sys file? Also when i do that command it tells me the version of ndis loaded which is 1.55 it also says it couldn't prepare or load the rt2870 driver. DOes the sys file have something to do with this?

---

### Post by 10.04LinuxDan on 2010-05-22
sorry i didnt clarify yes i did nothing with the .sys file only the .inf file what should be done about the .sys

---

### Post by 10.04LinuxDan on 2010-05-22
i just checked and it turns out the .sys was installed with the .inf

---

### Post by ip3t on 2010-05-22
adding in the blacklist.conf my wireless adapter works also in monitor mode?...

---

### Post by 10.04LinuxDan on 2010-05-22
What is monitor mode? How did you get yours configured is it the same model?

---

### Post by chili555 on 2010-05-22
> it also says it couldn't prepare or load the rt2870 driver.Does it say anything more informative than that? What about:```
sudo cat /var/log/syslog | grep ndis
```Can you copy the output to a text document and transfer it to another computer on a USB key so we can examine it in detail?> What is monitor mode?It is used to monitor nearby networks to crack WEP keys, among other things. Let's get it working before we do that.

---

### Post by chili555 on 2010-05-22
> **ip3t said:**
> adding in the blacklist.conf my wireless adapter works also in monitor mode?...I don't know; I don't have the device. Why not try it and we'll all find out when you try it and post your report.

---

### Post by ip3t on 2010-05-23
i tried to add the three lines at the end of blacklist.conf , but it seems doesn't work ..
i see wireless connections, but i can't connect to them...

---

### Post by chili555 on 2010-05-23
> **ip3t said:**
> i tried to add the three lines at the end of blacklist.conf , but it seems doesn't work ..
i see wireless connections, but i can't connect to them...If you see networks and it tries to connect, the driver and card are working. What happens? Are you asked for the encryption key? Does it try and fail or what?

---

### Post by ip3t on 2010-05-23
i also insert the encr key.. but nothing appens..
it's tried to connect all the time without succes

---

### Post by chili555 on 2010-05-23
Please try to connect and then run:```
sudo tail -n 25 /var/log/syslog
```Please post the result and let's see why it won't connect.

---

### Post by ip3t on 2010-05-23
```

Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Config: set interface ap_scan to 1
(wlan0): supplicant connection state:  disconnected -> scanning
kernel: [  491.557759] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 404
AptDaemon: INFO: Quiting due to inactivity
AptDaemon: INFO: Shutdown was requested
wpa_supplicant[1479]: Trying to associate with **:**:**:**:**:** (SSID='NETGEAR' freq=2412 MHz)
wpa_supplicant[1479]: Association request to the driver failed
NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
kernel: [  501.568102] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 411
kernel: [  501.568298] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
wpa_supplicant[1479]: Authentication with **:**:**:**:**:** timed out.
NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
kernel: [  511.578767] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 404
kernel: [  521.589195] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 404
kernel: [  531.599584] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 404
NetworkManager: <info>  wlan0: link timed out.
kernel: [  541.610035] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 404
NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
kernel: [  551.620180] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 411


```

---

### Post by chili555 on 2010-05-23
There is nothing very obvious there. Let's troubleshoot the driver. Did you compile the driver from Ralink or what? Let's see:```
lsmod | grep -e rt2 -e ndis
dmesg | grep -e ndis -e rt2
```Thanks.

---

### Post by ip3t on 2010-05-23
```

lsmod | grep -e rt2 -e ndis:
rt2870sta             461811  1

dmesg | grep -e ndis -e rt2:
[    4.588520] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[    4.706040] usbcore: registered new interface driver rt2870
 

```

> 
Did you compile the driver from Ralink or what?


no, i don't...i should do that?

---

### Post by chili555 on 2010-05-23
> no, i don't...i should do that? Not yet. Let's try something else first. Let's try rt2800usb and exclude rt2870sta. Please remove the device and do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Remove the lines you previously added:> blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00libReplace those lines with:```
blacklist rt2870sta
```Proofread carefully, save and close gedit. Re-insert the device and run:```
sudo modprobe rt2800usb
iwconfig
```Do you have a wireless interface? Can you connect?

---

### Post by ip3t on 2010-05-23
doesnt' work as before

---

### Post by 10.04LinuxDan on 2010-05-23
i did this and now see a wireless interface and now wireless is enabled but i cannot connect?

---

### Post by chili555 on 2010-05-23
> but i cannot connect?May I have details, please? Do you see networks when you click the Network Manager icon? Are you asked for the encryption key? Please try to connect and then may I see:```
sudo tail -n 25 /var/log/syslog
```

---

### Post by ip3t on 2010-05-24
is there another way to install the driver?...
can i try to use the rt2800/rt3070 driver on the Ralink web site?

---

### Post by chili555 on 2010-05-24
> **ip3t said:**
> is there another way to install the driver?...
can i try to use the rt2800/rt3070 driver on the Ralink web site?Sure, go ahead. You will need to again blacklist rt2800usb, rt2x00usb and rt2x00lib. Post back if you get stuck.

---

### Post by ip3t on 2010-05-25
in the Win Installation CD i've found the name of two possible drivers:
Win Vista => rt3070
Win XP => rt2870sta

he problem is how can i install..
i should looking for info about "balisting" and modules installation..

---

### Post by chili555 on 2010-05-25
Instructions on blacklisting are a few posts previous in this thread. If you are going to use ndiswrapper, you will need to blacklist all the native drivers: rt2870sta, rt2800usb, rt2x00usb and rt2x00lib.

Next, drag and drop the XP drivers, both the .inf and .sys from the CD to any convenient place, your desktop, for example.

Open System > Administration > Windows Wireless Wireless Drivers and install the driver you dropped on to your desktop.

Post back with any questions or errors.

---

### Post by ip3t on 2010-05-25
i know :)
again thanks
but at first i'd try to install without ndiswrapper drivers..

---

### Post by chili555 on 2010-05-25
> **ip3t said:**
> i know :)
again thanks
but at first i'd try to install without ndiswrapper drivers..That's not what I thought you were doing when you said:```
in the Win Installation CD i've found the name of two possible drivers:
Win Vista => rt3070
Win XP => rt2870sta

he problem is how can i install..
```And when you said:> i'm not unable to install the other drivers..
but i've read many where the driver's issue is causes by 2.6.32.* kernel (ubuntu 10.04 LTS)..
do you suggest me to install 9.10 oe 9.04?I am very happy to help you do whatever you'd like to try, but please tell me what it is you'd like to try first.

We can:

* Troubleshoot why you cannot connect even though you see networks;
* Try the native drivers and see which works better, rt2870sta or rt2800usb;
* Download and install the driver direct from Ralink;
* Or, try ndiswrapper.

Which do you prefer? My preference is to try the first option first. I also prefer that you not ask for help on several different threads. It's hard to find you and try to relate one thread to another.

---

### Post by deadite66 on 2010-05-25
trouble i found with using ndiswrapper is only get 54Mbps support no 802.11n

---

### Post by ip3t on 2010-05-25
> I am very happy to help you do whatever you'd like to try, but please  tell me what it is you'd like to try first.
the problem is my bad english..

however, i said
> We can:

* Troubleshoot why you cannot connect even though you see networks;

i agree with you!

so:
i added in blacklist.conf  only "blacklist rt2800usb";
it scans the network but doesn't connect..
it should depends on the Virtual Machine that i use to run ubuntu?

---

### Post by chili555 on 2010-05-25
Please add to your blacklist.conf:```
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread, save and close gedit. Now reboot and see if you can connect. Do you see your network? Does it try? Does it ask for your encryption key? What kind of encryption is it?

---

### Post by ip3t on 2010-05-25
in this case doesn't work at all.
i've a WPA2 + psk encryption

ps my network is hidden

---

### Post by chili555 on 2010-05-25
When you left-click the Network Manager icon and select Connect to Hidden Network and fill in your details, does it try to connect?

Some routers have a mixed WPA ***and*** WPA2 mode; many wireless drivers have difficulty connecting in mixed mode. Your router ought to be set in WPA2 ***only***. Could you please check that?

---

### Post by ip3t on 2010-05-25
with my router i can only set WPA2-psk encryption method , or wep.
with the last modifiy, the wireless is down, so i can't open a connection.

---

### Post by chili555 on 2010-05-25
Please post:```
dmesg | grep -i rt2
```Thanks.

---

### Post by ip3t on 2010-05-25
```

[    7.808265] Registered led device: rt2800usb-phy0::radio
[    7.808283] Registered led device: rt2800usb-phy0::assoc
[    7.808308] Registered led device: rt2800usb-phy0::quality
[    8.692410] usbcore: registered new interface driver rt2800usb
[    8.697966] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[    8.702837] usbcore: registered new interface driver rt2870
[    9.349694] rt2800usb 1-1:1.0: firmware: requesting rt2870.bin
[   43.692155] phy0 -> rt2800usb_wait_wpdma_ready: Error - WPDMA TX/RX busy, aborting.
[   47.091424] Registered led device: rt2800usb-phy1::radio
[   47.091439] Registered led device: rt2800usb-phy1::assoc
[   47.091452] Registered led device: rt2800usb-phy1::quality
[   47.125813] rt2800usb 1-1:1.0: firmware: requesting rt2870.bin
[  147.692219] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x1700 with error -19.
[  147.764419] phy1 -> rt2800usb_wait_wpdma_ready: Error - WPDMA TX/RX busy, aborting.
[  150.212838] Registered led device: rt2800usb-phy2::radio
[  150.218275] Registered led device: rt2800usb-phy2::assoc
[  150.218352] Registered led device: rt2800usb-phy2::quality
[  152.986088] rt2800usb 1-1:1.0: firmware: requesting rt2870.bin


```

---

### Post by chili555 on 2010-05-25
> rt2800usb 1-1:1.0: firmware: requesting rt2870.bin
It look like you didn't blacklist rt2800usb correctly. May I see:```
cat /etc/modprobe.d/blacklist.conf
```Thanks.

---

### Post by ip3t on 2010-05-25
/etc(modprobe.d/blacklist.conf:
```

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist rt2x00usb
blacklist rt2x00lib

```if I add also blacklist rt2800usb it can scans the network but not connect..
if i change the encryption method does it probably works?

---

### Post by chili555 on 2010-05-25
Is your device the same as the title of the thread?```
lsusb
```Is the usb.id 1737:0077? It ought to work with rt2870sta. If you blacklist rt2800usb and then do:```
sudo modprobe rt2870sta
```Does it work?

Sorry, out for an appointment. I will catch up later.

---

### Post by ip3t on 2010-05-25
it's the same device, i'm sure :)
even after modprobe the situation doesn't change

---

### Post by chili555 on 2010-05-25
May I see:```
sudo modprobe rt2870sta
dmesg | grep -i rt2
```Thanks.

---

### Post by ip3t on 2010-05-26
it's here:
```

[    5.487580] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[    7.868319] usbcore: registered new interface driver rt2870

```

---

### Post by chili555 on 2010-05-27
Please do:```
lsusb > listing.txt
lsmod >> listing.txt
dmesg >> listing.txt
iwconfig >> listing.txt
zip listing.zip listing.txt
```You will find a zip file in your home directory called listing.zip. Please attach it to your reply. Thanks.

---

### Post by ip3t on 2010-05-27
is here

---

### Post by chili555 on 2010-05-27
> [   15.313665] --> Error 2 opening /etc/Wireless/RT3070STA/RT3070STA.datLet's see if we can fix that. Please do:```
sudo su
mkdir -p /etc/Wireless/RT3070STA
touch /etc/Wireless/RT3070STA/RT3070STA.dat
service network-manager restart
exit
```Now are you able to connect?

---

### Post by ip3t on 2010-05-28
no.. i don't.. :(
[COLOR=Black]the user [/COLOR][marianlibrarian]("http://ubuntuforums.org/member.php?u=183963") in this discussion said that he found a solution.
is it right also for me?

---

### Post by chili555 on 2010-05-28
I think Marian is a she. You gave me a link to her profile. Can you give me a link to the solution?

Can you please reboot and give me a new listing.txt as above?

---

### Post by ip3t on 2010-05-28
you're right! :oops: .. i've made a mistake ..
here you are the [link]("http://ubuntuforums.org/showthread.php?t=1479196") of the solution
even if i reboot the situation doesn't change.

---

### Post by chili555 on 2010-05-28
I am not sure what part of her thread you are referring to as a solution. She had available networks immediately and was stuck in an ad-hoc connection with an IP address of 10.42.x.x. As well, I believe her device has a different chipset. She says:> lsusb tells me:
Bus 001 Device 002: ID13bl: Linksys WUSB54GC 802.11g Adapter [ralink rt73]You, however, assured me that you have the same device as the title of this thread: 1737:0077.

What is it that she did are you hoping will work for you?

Just because I am nervous, please post:```
lsusb
```Thanks.

---

### Post by ip3t on 2010-05-28
because she linked to me the solution from [this]("http://ubuntuforums.org/showthread.php?t=1464255&page=2") tread.
i'm sure :) my devide is tha same..
why are you so nervous?

---

### Post by chili555 on 2010-05-28
I'll be sure to send her a Private Message and let her know that you have a different device.

I am nervous because I am afraid you do *not* have the same device 1737:0077 and we have been working on the wrong drivers.

Please post:```
lsusb
```

---

### Post by ip3t on 2010-05-28
```
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1737:0077 Linksys 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

i've been sure.

---

### Post by chili555 on 2010-05-28
If you run:```
dmesg | grep -i RT3
```Are you still getting this error?> --> Error 2 opening /etc/Wireless/RT3070STA/RT3070STA.datAfter all the changes we've made, do you still have a wireless interface?```
iwconfig
```
I am no longer nervous. Thanks.

---

### Post by ip3t on 2010-05-28
when i run dmesg | ... i don't see anything..
the search sesult is "NULL"..

and.. yes. i still have a wireless interface:

```

wlan0     RTxx70 Wireless  ESSID:""  Nickname:"RT3070STA"
          Mode:Auto  Frequency=2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:-69 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by hans egon on 2010-05-29
oh sorry!!

hello
i've got the same problem

I tried all your suggestions, but i cant get a connection (although I can see the networks)

Now I created (with a notebook) a non-encrypted, wep and wpa encrypted network and tried to connect with the pc.
with the non-encrypted and the wep encrypted network it worked without problems
but with the WPA encrypted network i didnt get a connection with the pc (it tried a lond time and then asked again for the password)

---

### Post by ip3t on 2010-05-29
i don't speak your language.. you shoud try to speak english, please.

---

### Post by ip3t on 2010-05-29
i've the same device?
i'll try of sure

---

### Post by hans egon on 2010-05-29
ok
now i tried to change the router configuration (encryption was wpa/wpa2 mixed mode)

no encryption - ok
wep                -  ok
wpa                -  ok
wpa2              -  ok
wpa/wpa2      -  no

so everything except wpa/wpa2 mixed works (for me)

if you have access to your router, maybe try to change the encryption

(yes i have the same device, linksys wusb54gc v3, 1737:0077)

---

### Post by Burnieboy on 2010-06-05
Good morning Mr. Chili!
I got the same problem as anyone here, and I tried everything you just mentionned in the post. 
 
Here is where I am:
In the beginning, I just add the blacklist rt2800usb at the end, and I was able to see the networks. To make a shortcut, because I was always not able to connect to mine, I decided to install the thing wich with it we can install the rt2870.sys or .inf.. don't remember. It stopped working, so i uninstalled it. 
 
Now, if i want to see the networks again, i have to go in the terminal and wrote sudo modprobe rt2870sta. But always not able to connect. However, I think i've found the source of the problem. here it is:
 
[EMAIL="bernard@bernard-desktop:~$"]bernard@bernard-desktop:~$[/EMAIL] sudo tail -n 25 /var/log/syslog
Jun  5 10:45:38 bernard-desktop wpa_supplicant[901]: Authentication with 00:00:00:00:00:00 timed out.
Jun  5 10:45:38 bernard-desktop wpa_supplicant[901]: Trying to associate with SSID 'Max et Jay'
Jun  5 10:45:38 bernard-desktop wpa_supplicant[901]: Association request to the driver failed
Jun  5 10:45:38 bernard-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jun  5 10:45:38 bernard-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jun  5 10:45:38 bernard-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jun  5 10:45:43 bernard-desktop wpa_supplicant[901]: Authentication with 00:00:00:00:00:00 timed out.
Jun  5 10:45:43 bernard-desktop wpa_supplicant[901]: Trying to associate with SSID 'Max et Jay'
Jun  5 10:45:43 bernard-desktop wpa_supplicant[901]: Association request to the driver failed
Jun  5 10:45:43 bernard-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jun  5 10:45:43 bernard-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jun  5 10:45:43 bernard-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jun  5 10:45:48 bernard-desktop wpa_supplicant[901]: Authentication with 00:00:00:00:00:00 timed out.
Jun  5 10:45:48 bernard-desktop wpa_supplicant[901]: Trying to associate with SSID 'Max et Jay'
Jun  5 10:45:48 bernard-desktop wpa_supplicant[901]: Association request to the driver failed
Jun  5 10:45:48 bernard-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jun  5 10:45:48 bernard-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jun  5 10:45:48 bernard-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jun  5 10:45:53 bernard-desktop wpa_supplicant[901]: Authentication with 00:00:00:00:00:00 timed out.
Jun  5 10:45:53 bernard-desktop wpa_supplicant[901]: Trying to associate with SSID 'Max et Jay'
Jun  5 10:45:53 bernard-desktop wpa_supplicant[901]: Association request to the driver failed
Jun  5 10:45:53 bernard-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Jun  5 10:45:53 bernard-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Jun  5 10:45:53 bernard-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jun  5 10:45:54 bernard-desktop NetworkManager: <info>  wlan0: link timed out.
 
I don't think it is supposed to do that..
Thanks for the help!
 
Bernard

---

### Post by chili555 on 2010-06-05
Good morning!

You are right, it's not supposed to time out. This is also suspicious:> Authentication with [COLOR="Red"]00:00:00:00:00:00[/COLOR] timed out.Let's take a look at:```
lsmod | grep rt2
dmesg | grep -i RT2
```Thanks.

---

### Post by Burnieboy on 2010-06-05
HAHA! yeah... this is part of things I understand into all that story :P
 
So for your request:
 
[EMAIL="bernard@bernard-desktop:~$"]bernard@bernard-desktop:~$[/EMAIL] lsmod | grep rt2
[EMAIL="bernard@bernard-desktop:~$"]bernard@bernard-desktop:~$[/EMAIL] dmesg | grep -i RT2
[    9.293827] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[   10.053144] ndiswrapper (load_sys_files:206): couldn't prepare driver 'rt2870'
[   10.053763] ndiswrapper (load_wrap_driver:108): couldn't load driver rt2870; check system log for messages from 'loadndisdriver'
[EMAIL="bernard@bernard-desktop:~$"]bernard@bernard-desktop:~$[/EMAIL] 

The first code just did nothing. The second one, I just don't understand but I'll repost the messages in the system log. Maybe it can help...

---

### Post by Burnieboy on 2010-06-05
Okay! Here's what I just found in the system logs so I hope it will help!
 
Jun  5 08:48:01 bernard-desktop kernel: [  336.355195] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
Jun  5 08:48:01 bernard-desktop kernel: [  336.492025] usb 1-1: reset high speed USB device using ehci_hcd and address 2
Jun  5 08:48:01 bernard-desktop loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver rt2870
Jun  5 08:48:01 bernard-desktop kernel: [  336.637544] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'MmGetSystemRoutineAddress'
Jun  5 08:48:01 bernard-desktop kernel: [  336.637821] ndiswrapper (load_sys_files:206): couldn't prepare driver 'rt2870'
Jun  5 08:48:01 bernard-desktop kernel: [  336.638423] ndiswrapper (load_wrap_driver:108): couldn't load driver rt2870; check system log for messages from 'loadndisdriver'
Jun  5 08:48:01 bernard-desktop kernel: [  336.640475] usbcore: registered new interface driver ndiswrapper
Jun  5 08:48:47 bernard-desktop AptDaemon: INFO: Quiting due to inactivity

---

### Post by chili555 on 2010-06-06
I suspect your card needs not only the .inf file, but also the .sys file(s). Can you look around in /etc/ndiswrapper and see if a .sys file is loaded?

Where did you get the .inf file? Was there a .sys file (or two) with it that you omitted?

---

### Post by Burnieboy on 2010-06-06
I got both the .sys and the .inf on the windows installation cd...

---

### Post by chili555 on 2010-06-06
Please see: [https://bugs.launchpad.net/hundredpapercuts/+bug/388593](https://bugs.launchpad.net/hundredpapercuts/+bug/388593)

Post #9 says:> The problem is people doesn't know that making a wireless connection "Available to all users" means "No need to enter the keyring password".Please edit again and be sure 'Available to all users' is also checked.

---

### Post by Burnieboy on 2010-06-06
Ok then. I've checked the box but the problem remains. The other thing I've just remarked is that the .sys file loaded in the folder is called wusb54gcv3.sys, wich is not the .sys that is coming with the cd (rt2870something.sys)... is that can be the problem?

---

### Post by chili555 on 2010-06-06
> **Burnieboy said:**
> Ok then. I've checked the box but the problem remains. The other thing I've just remarked is that the .sys file loaded in the folder is called wusb54gcv3.sys, wich is not the .sys that is coming with the cd (rt2870something.sys)... is that can be the problem?It absolutely could. I suggest you uninstall the .inf and reinstall the files from the CD. I have never tried all this, so I am a bit unsure if it will work correctly. We can try manual methods if not.

---

### Post by Burnieboy on 2010-06-07
Alright, but we will try the manual methods because I already did the reinstallation of the drivers and it did the same thing...
 
Thanks!

---

### Post by chili555 on 2010-06-07
Let's see what is in the appropriate file:```
ls /etc/ndiswrapper
```What are the names of the .inf and .sys files on the CD?

---

### Post by Burnieboy on 2010-06-07
Here we go:
 
[EMAIL="bernard@bernard-desktop:~$"]bernard@bernard-desktop:~$[/EMAIL] ls /etc/ndiswrapper
rt2870
[EMAIL="bernard@bernard-desktop:~$"]bernard@bernard-desktop:~$[/EMAIL] ls /etc/ndiswrapper/rt2870
1737:0077.F.conf  rt2870.inf  wusb54gcv3.sys

 
And the cd files:
 
rt2870.sys
rt2870.inf
 
Bernard

---

### Post by chili555 on 2010-06-07
I suggest the following. Create a folder on your desktop called rt2870. Drag and drop the files from the CD to this new folder. If there are other files, additional .sys files, .cat files, etc., copy those over, as well.

Next, do:```
sudo ndiswrapper -e rt2870
```Now, let's check again:```
ls /etc/ndiswrapper
```Hopefully, it is now empty. If not, do:```
sudo rm -rf /etc/ndiswrapper/*
```BE VERY CAREFUL! The *rm* command removes files and not just to Trash. Used improperly, it may wreck your system, so proofread carefully, twice, before you press the Enter button.

Now do:```
sudo ndiswrapper -i Desktop/rt2870/rt2870.inf
```If .sys files, etc. are required, they will be imported. Now do:```
sudo rmmod -f ndiswrapper
sudo modprobe ndiswrapper
```

Now does the wireless work better?

---

### Post by Burnieboy on 2010-06-18
So, I did everything, but in fact, the files, that were removed from the folder by the first code line, they are the same as i've found at the end of the procedure. And the network is still not recognized. 
 
I noticed something else; when I go into the modprobe.d folder, there is a ndiswrapper text file in it. If I remove the code line into it, the usb adapter is working then, but always not able to connect to the network. It is always to connect again and again...
 
Sorry for the late answer by the way.
 
If you have any other ideas, fine, i'll try everything I can with your help, but if you think the better way for me to get wireless internet on my desktop is to buy an usb adapter more easily supported, you can say, I won't be angry :)

---

### Post by malcolm.watts on 2010-06-23
Hi, I was looking around to find a solution to this problem - I was getting the wpa_supplicant association timeout message also mentioned elsewhere.

After adding the blacklist lines as mentioned in this or another thread I got the device recognised but then through fiddling found that the only way to get connected was to change the security on the access point(mine is a draytek Vigor2800vg) to "WPA2 only" from "WPA/WPA2 mixed", it has no option for WPA only.

Someone else also mentioned this work around but wanted to mention it again in case it was missed.

So that appears to be a work around and maybe a starting point for driver devs to work from...

Cheers

---

### Post by Tonyr63 on 2010-07-21
Hi

i have tried all the troubleshooting steps here and it appears to me that my USD wireless is dead unless i plug it into a windows machine.  How can it be so hard to get this sucker to work.

This is what i did.

1.) Download the driver  (2009_1110_RT3070_Linux_STA_v2.1.2.0) 
2.) Extracted it to your Desktop
Basically if you double-click on it the Archive Manager will start and you need to choose where to Extract. 
3.) Go to the folder 
code: 
 
Quote: 
cd /home/anthony/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0   
 
4.) code: 
 
Quote: 
sudo make   
  (or anywhere, but I used that one)  
(obviously it will ask for your sudo/administrator password) 
5.) code: 
 
Quote: 
make install   
 
6.) Create two files in the next steps: 
code: 
 
Quote: 
gedit /etc/udev/rules.d/network_drivers.rules   
 
then when the text editor opens up 
copy and paste the followings exactly as it is. case and all, quotes and all: 
 
Quote: 
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1784", RUN+="/sbin/modprobe -qba rt3070sta"   
 
save and close the text editor. 
 
Quote: 
gedit /etc/modprobe.d/network_drivers.conf   
 
the copy and paste as above: 
 
Quote: 
install rt3070sta /sbin/modprobe --ignore-install rt3070sta $CMDLINE_OPTS; /bin/echo "0b05 1784" > /sys/bus/usb/drivers/rt2870/new_id   
 
save and close text editor. 
7.) plug the USB device in (mine wasn't recognized until I restarted...) 
8.) exit terminal window 
9.) restart system 
10.) configure your wireless 

NOTHING WORKS

I tried some stuff from the terminal


anthony@TeleLinux:~$ lsmod | grep -e rt2 -e ndis
anthony@TeleLinux:~$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
anthony@TeleLinux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

anthony@TeleLinux:~$ sudo iwlist wlan0 scan
[sudo] password for anthony: 
wlan0     Interface doesn't support scanning.

anthony@TeleLinux:~$ sudo cat /var/log/syslog | grep ndis
anthony@TeleLinux:~$ sudo tail -n 25 /var/log/syslog
Jul 21 23:18:24 TeleLinux dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Jul 21 23:18:24 TeleLinux dhclient: 
Jul 21 23:18:24 TeleLinux NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Jul 21 23:18:24 TeleLinux dhclient: Listening on LPF/eth0/00:16:41:6a:5b:ce
Jul 21 23:18:24 TeleLinux dhclient: Sending on   LPF/eth0/00:16:41:6a:5b:ce
Jul 21 23:18:24 TeleLinux dhclient: Sending on   Socket/fallback
Jul 21 23:18:28 TeleLinux dhclient: DHCPREQUEST of 10.1.1.7 on eth0 to 255.255.255.255 port 67
Jul 21 23:18:28 TeleLinux dhclient: DHCPACK of 10.1.1.7 from 10.1.1.1
Jul 21 23:18:28 TeleLinux dhclient: bound to 10.1.1.7 -- renewal in 867763539 seconds.
Jul 21 23:18:28 TeleLinux NetworkManager: <info>  DHCP: device eth0 state changed preinit -> reboot
Jul 21 23:18:28 TeleLinux NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jul 21 23:18:28 TeleLinux NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Jul 21 23:18:28 TeleLinux NetworkManager: <info>    address 10.1.1.7
Jul 21 23:18:28 TeleLinux NetworkManager: <info>    prefix 24 (255.255.255.0)
Jul 21 23:18:28 TeleLinux NetworkManager: <info>    gateway 10.1.1.1
Jul 21 23:18:28 TeleLinux NetworkManager: <info>    nameserver '10.1.1.1'
Jul 21 23:18:28 TeleLinux NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jul 21 23:18:28 TeleLinux NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Jul 21 23:18:28 TeleLinux NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Jul 21 23:18:29 TeleLinux NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Jul 21 23:18:29 TeleLinux NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Jul 21 23:18:29 TeleLinux NetworkManager: <info>  Activation (eth0) successful, device activated.
Jul 21 23:18:29 TeleLinux NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Jul 21 23:18:30 TeleLinux ntpdate[1649]: adjust time server 91.189.94.4 offset -0.035467 sec
Jul 21 23:18:35 TeleLinux kernel: [  702.772010] eth0: no IPv6 routers present
anthony@TeleLinux:~$ dmesg | grep -i rt2
[   10.057982] usbcore: registered new interface driver rt2870
anthony@TeleLinux:~$ lsusd
No command 'lsusd' found, did you mean:
 Command 'lsusb' from package 'usbutils' (main)
lsusd: command not found
anthony@TeleLinux:~$ sudo modprobe rt2870sta
FATAL: Error inserting rt2870sta (/lib/modules/2.6.32-21-generic/kernel/drivers/staging/rt2870/rt2870sta.ko): Device or resource busy
anthony@TeleLinux:~$ sudo modprobe rt2870sta
FATAL: Error inserting rt2870sta (/lib/modules/2.6.32-21-generic/kernel/drivers/staging/rt2870/rt2870sta.ko): Device or resource busy
anthony@TeleLinux:~$ sudo modprobe rt2870sta
FATAL: Error inserting rt2870sta (/lib/modules/2.6.32-21-generic/kernel/drivers/staging/rt2870/rt2870sta.ko): Device or resource busy
anthony@TeleLinux:~$ sudo modprobe rt2870sta
FATAL: Error inserting rt2870sta (/lib/modules/2.6.32-21-generic/kernel/drivers/staging/rt2870/rt2870sta.ko): Device or resource busy
anthony@TeleLinux:~$ dmesg | grep -i rt2
[   10.057982] usbcore: registered new interface driver rt2870
[ 1686.188723] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[ 1686.195734] Error: Driver 'rt2870' is already registered, aborting...
[ 1686.195740] usbcore: error -16 registering interface     driver rt2870
[ 1743.779835] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[ 1743.787637] Error: Driver 'rt2870' is already registered, aborting...
[ 1743.787642] usbcore: error -16 registering interface     driver rt2870
[ 1821.036486] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[ 1821.044409] Error: Driver 'rt2870' is already registered, aborting...
[ 1821.044414] usbcore: error -16 registering interface     driver rt2870
[ 1852.200562] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[ 1852.210781] Error: Driver 'rt2870' is already registered, aborting...
[ 1852.210786] usbcore: error -16 registering interface     driver rt2870
anthony@TeleLinux:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0b05:1784 ASUSTek Computer, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
anthony@TeleLinux:~$ dmesg | grep -i RT3
anthony@TeleLinux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
.  
I did not install the NDISwrapper as most advise that this is not required.

What do I do next?

:(

---

### Post by Tonyr63 on 2010-07-22
Hi


I tried reinstalling the newer driverv2.3.0.3_20100422.tgz with completely no different outcome.  Still a completely dead USB card.

anthony@TeleLinux:~/Desktop/Linux$ tar -xvzf DPO_RT3070_LinuxSTA_V2.3.0.2_20100422.tgz
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/iwpriv_usage.txt
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/LICENSE ralink-firmware.txt
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/Makefile
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/README_STA_usb
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/RT2870STA.dat
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/RT2870STACard.dat
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/sta_ate_iwpriv_usage.txt
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/chips/
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/chips/rt3070.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/chips/rt30xx.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/chips/rt3593.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/action.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/ba_action.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/br_ftph.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/client_wds.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/cmm_aes.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/cmm_asic.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/cmm_cfg.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/cmm_cmd.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/cmm_data.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/cmm_data_usb.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/cmm_info.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/cmm_mac_usb.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/cmm_profile.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/cmm_sanity.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/cmm_sync.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/cmm_tkip.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/cmm_wep.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/cmm_wpa.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/crypt_aes.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/crypt_arc4.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/crypt_hmac.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/crypt_md5.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/crypt_sha2.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/dfs.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/eeprom.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/ee_efuse.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/ee_prom.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/mlme.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/mrgtmp0
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/netif_block.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/rt2870.bin
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/rtmp_init.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/rtmp_init_inf.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/rtmp_mcu.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/rtmp_timer.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/rtusb_bulk.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/rtusb_data.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/rtusb_dev_id.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/rtusb_io.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/rt_channel.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/rt_rf.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/spectrum.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/common/vr_ikans.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/action.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/ap.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/cfg80211.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/cfg80211extr.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/chlist.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/client_wds.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/client_wds_cmm.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/crypt_aes.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/crypt_arc4.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/crypt_hmac.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/crypt_md5.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/crypt_sha2.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/dfs.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/dot11i_wpa.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/eeprom.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/firmware.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/link_list.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/mlme.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/netif_block.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/oid.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/rtmp.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/rtmp_chip.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/rtmp_cmd.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/rtmp_def.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/rtmp_dot11.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/rtmp_iface.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/rtmp_mcu.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/rtmp_os.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/rtmp_timer.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/rtmp_type.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/rtusb_io.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/rt_ate.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/rt_config.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/spectrum.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/spectrum_def.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/sta_cfg.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/vr_ikans.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/wpa.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/wpa_cmm.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/os/
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/os/rt_linux.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/iface/
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/iface/rtmp_usb.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/chip/
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/chip/mac_usb.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/chip/rt3070.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/chip/rt30xx.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/chip/rt3593.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/chip/rtmp_mac.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/include/chip/rtmp_phy.h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/cfg80211.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/config.mk
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/Makefile.4
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/Makefile.6
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/modules.order
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/rt_ate.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/rt_linux.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/rt_main_dev.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/rt_profile.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/rt_usb.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/rt_usb_util.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/sta_ioctl.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/usb_main_dev.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/vr_ikans.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/sta/
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/sta/assoc.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/sta/auth.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/sta/auth_rsp.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/sta/connect.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/sta/dls.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/sta/rtmp_ckipmic.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/sta/rtmp_data.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/sta/sanity.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/sta/sta_cfg.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/sta/sync.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/sta/wpa.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/tools/
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/tools/bin2h
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/tools/bin2h.c
DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/tools/Makefile
anthony@TeleLinux:~/Desktop/Linux$ cd DPO_RT3070_LinuxSTA_V2.3.0.2_20100422
anthony@TeleLinux:~/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422$ sudo make
make -C tools
make[1]: Entering directory `/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/tools'
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/tools/bin2h
cp -f os/linux/Makefile.6 /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/Makefile
make -C /lib/modules/2.6.32-21-generic/build SUBDIRS=/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/crypt_md5.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/crypt_aes.o
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/crypt_aes.c: In function ‘AES_GTK_KEY_WRAP’:
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/crypt_aes.c:2265: warning: the frame size of 1100 bytes is larger than 1024 bytes
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/crypt_aes.c: In function ‘WscDecryptData’:
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/crypt_aes.c:1592: warning: the frame size of 1364 bytes is larger than 1024 bytes
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/crypt_aes.c: In function ‘WscEncryptData’:
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/crypt_aes.c:1522: warning: the frame size of 1364 bytes is larger than 1024 bytes
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/mlme.o
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/mlme.c:4683: warning: the frame size of 1720 bytes is larger than 1024 bytes
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_wep.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/action.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_data.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/rtmp_init.o
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/rtmp_init.c: In function ‘NICInitAsicFromEEPROM’:
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/rtmp_init.c:2488: warning: unused variable ‘RFValue’
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_aes.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_sync.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/eeprom.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_info.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/dfs.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/spectrum.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/rt_channel.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_profile.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_asic.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/assoc.o
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/assoc.c: In function ‘MlmeAssocReqAction’:
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/assoc.c:377: warning: unused variable ‘pInfo’
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/assoc.c:374: warning: unused variable ‘infoPos’
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/auth.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/sync.o
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/sync.c:1736: warning: the frame size of 1316 bytes is larger than 1024 bytes
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtJoinAction’:
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/sync.c:1079: warning: the frame size of 1264 bytes is larger than 1024 bytes
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtScanAction’:
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/sync.c:773: warning: the frame size of 1268 bytes is larger than 1024 bytes
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/sync.c: In function ‘MlmeStartReqAction’:
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/sync.c:589: warning: the frame size of 1064 bytes is larger than 1024 bytes
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/sanity.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/connect.o
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/connect.c: In function ‘CntlOidScanProc’:
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/connect.c:351: warning: the frame size of 1748 bytes is larger than 1024 bytes
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/wpa.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../sta/sta_cfg.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/rt_profile.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/sta_ioctl.o
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_siwencode’:
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/sta_ioctl.c:1481: warning: suggest parentheses around operand of ‘!’ or change ‘&’ to ‘&&’ or ‘!’ to ‘~’
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlRF’:
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/sta_ioctl.c:6219: warning: the frame size of 2328 bytes is larger than 1024 bytes
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlE2PROM’:
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/sta_ioctl.c:6035: warning: the frame size of 1348 bytes is larger than 1024 bytes
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlMAC’:
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/sta_ioctl.c:5837: warning: the frame size of 1344 bytes is larger than 1024 bytes
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_iwaplist’:
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/sta_ioctl.c:606: warning: the frame size of 1288 bytes is larger than 1024 bytes
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_siwmlme’:
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/sta_ioctl.c:1979: warning: the frame size of 1588 bytes is larger than 1024 bytes
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/rt_linux.o
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSTaskAttach’:
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/rt_linux.c:1283: warning: passing argument 1 of ‘kthread_create’ from incompatible pointer type
include/linux/kthread.h:7: note: expected ‘int (*)(void *)’ but argument is of type ‘RTMP_OS_TASK_CALLBACK’
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevDetach’:
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/rt_linux.c:1614: warning: initialization discards qualifiers from pointer target type
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/rt_linux.c:1653: warning: initialization discards qualifiers from pointer target type
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/rt_linux.c:1653: warning: ISO C90 forbids mixed declarations and code
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/rt_main_dev.o
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/rt_main_dev.c: In function ‘RtmpOSIRQRequest’:
/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/rt_main_dev.c:951: warning: unused variable ‘net_dev’
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/ba_action.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_mac_usb.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/rtusb_io.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/rtusb_bulk.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/rtusb_data.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_data_usb.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/ee_prom.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/ee_efuse.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/rtmp_mcu.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../chips/rt30xx.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/rt_rf.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../chips/rt3070.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/rtusb_dev_id.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/rt_usb.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/rt_usb_util.o
  CC [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../os/linux/usb_main_dev.o
  LD [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/rt3070sta.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/rt3070sta.mod.o
  LD [M]  /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/rt3070sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
cp -f /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/rt3070sta.ko /tftpboot
anthony@TeleLinux:~/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422$ make install
make -C /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux'
rm -rf /etc/Wireless/RT3070STA
rm: cannot remove `/etc/Wireless/RT3070STA/RT2870STA.dat': Permission denied
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux'
make: *** [install] Error 2
anthony@TeleLinux:~/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422$ sudo gedit os/Linux/Makefile.6
anthony@TeleLinux:~/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422$ sudo gedit os/linux/Makefile.6
anthony@TeleLinux:~/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422$ sudo make install
make -C /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux'
rm -rf /etc/Wireless/RT3070STA
mkdir /etc/Wireless/RT3070STA
cp /home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/RT2870STA.dat /etc/Wireless/RT3070STA/.
install -d /lib/modules/2.6.32-21-generic/kernel/drivers/net/wireless/
install -m 644 -c rt3070sta.ko /lib/modules/2.6.32-21-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.32-21-generic
make[1]: Leaving directory `/home/anthony/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux'
anthony@TeleLinux:~/Desktop/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422$ 

anthony@TeleLinux:~$ dmesg | grep -e rt2 -e rt3
[   10.110703] usbcore: registered new interface driver rt2870
[   11.764775] !!! rt28xx Initialized fail !!!
[   12.479416] !!! rt28xx Initialized fail !!!
[  277.289978] !!! rt28xx Initialized fail !!!
[  277.887150] !!! rt28xx Initialized fail !!!
[  323.392052] !!! rt28xx Initialized fail !!!
[  323.997558] !!! rt28xx Initialized fail !!!
[  333.132888] !!! rt28xx Initialized fail !!!
[  333.730044] !!! rt28xx Initialized fail !!!

anthony@TeleLinux:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0b05:1784 ASUSTek Computer, Inc. 
Bus 001 Device 003: ID 1307:0163 Transcend Information, Inc. 512MB/1GB Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
anthony@TeleLinux:~$ lsmod | grep -e rt2 -e rt3
rt3070sta             571815  0 
anthony@TeleLinux:~$ dmesg | grep -i rt2
[   10.110703] usbcore: registered new interface driver rt2870
[   11.708621] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2870STA/RT2870STA.dat
[   11.708625] Open file "/etc/Wireless/RT2870STA/RT2870STA.dat" failed!
[   11.764775] !!! rt28xx Initialized fail !!!
[   12.415847] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2870STA/RT2870STA.dat
[   12.415851] Open file "/etc/Wireless/RT2870STA/RT2870STA.dat" failed!
[   12.479416] !!! rt28xx Initialized fail !!!
[  277.233860] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2870STA/RT2870STA.dat
[  277.233866] Open file "/etc/Wireless/RT2870STA/RT2870STA.dat" failed!
[  277.289978] !!! rt28xx Initialized fail !!!
[  277.830957] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2870STA/RT2870STA.dat
[  277.830962] Open file "/etc/Wireless/RT2870STA/RT2870STA.dat" failed!
[  277.887150] !!! rt28xx Initialized fail !!!
[  323.335891] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2870STA/RT2870STA.dat
[  323.335897] Open file "/etc/Wireless/RT2870STA/RT2870STA.dat" failed!
[  323.392052] !!! rt28xx Initialized fail !!!
[  323.941416] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2870STA/RT2870STA.dat
[  323.941422] Open file "/etc/Wireless/RT2870STA/RT2870STA.dat" failed!
[  323.997558] !!! rt28xx Initialized fail !!!
[  333.076753] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2870STA/RT2870STA.dat
[  333.076758] Open file "/etc/Wireless/RT2870STA/RT2870STA.dat" failed!
[  333.132888] !!! rt28xx Initialized fail !!!
[  333.673780] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2870STA/RT2870STA.dat
[  333.673785] Open file "/etc/Wireless/RT2870STA/RT2870STA.dat" failed!
[  333.730044] !!! rt28xx Initialized fail !!!
anthony@TeleLinux:~$ 

anthony@TeleLinux:~$ dmesg | grep -e rt3 -e ra0
[  328.412540] RtmpOSNetDevDetach(): RtmpOSNetDeviceDetach(), dev->name=ra0!


I could have installed gigabit cabling in the time I have wasted trying to get Ubuntu 10.04 to recognise my wireless card.

Can I have some assistance?

---

### Post by Tonyr63 on 2010-07-22
Hi

I notice that RtmpOSFileOpen () is looking in /etc/wireless/RT2870STA folder when the actual folder where the RT2870.Dat file is stored is in the /etc/wireless/RT3070STA folder.

I dont know what is cause it to try the incorrect path?

---

### Post by Tonyr63 on 2010-07-22
Hi

I renamed the folder in the /etc/Wireless folder mv RT3070STA to RT2870STA and immediately my USB wireless adapter started to illuminate making me think I had a resolution however I still cannot see the network.  At lease after 4 days of frustration I can see an LED.

anthony@TeleLinux:/etc/Wireless$ dmesg | grep -i rt2
[   10.110703] usbcore: registered new interface driver rt2870
[   11.708621] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2870STA/RT2870STA.dat
[   11.708625] Open file "/etc/Wireless/RT2870STA/RT2870STA.dat" failed!
[   11.764775] !!! rt28xx Initialized fail !!!
[   12.415847] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2870STA/RT2870STA.dat
[   12.415851] Open file "/etc/Wireless/RT2870STA/RT2870STA.dat" failed!
[   12.479416] !!! rt28xx Initialized fail !!!
[  277.233860] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2870STA/RT2870STA.dat
[  277.233866] Open file "/etc/Wireless/RT2870STA/RT2870STA.dat" failed!
[  277.289978] !!! rt28xx Initialized fail !!!
[  277.830957] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2870STA/RT2870STA.dat
[  277.830962] Open file "/etc/Wireless/RT2870STA/RT2870STA.dat" failed!
[  277.887150] !!! rt28xx Initialized fail !!!
[  323.335891] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2870STA/RT2870STA.dat
[  323.335897] Open file "/etc/Wireless/RT2870STA/RT2870STA.dat" failed!
[  323.392052] !!! rt28xx Initialized fail !!!
[  323.941416] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2870STA/RT2870STA.dat
[  323.941422] Open file "/etc/Wireless/RT2870STA/RT2870STA.dat" failed!
[  323.997558] !!! rt28xx Initialized fail !!!
[  333.076753] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2870STA/RT2870STA.dat
[  333.076758] Open file "/etc/Wireless/RT2870STA/RT2870STA.dat" failed!
[  333.132888] !!! rt28xx Initialized fail !!!
[  333.673780] RtmpOSFileOpen(): Error 2 opening /etc/Wireless/RT2870STA/RT2870STA.dat
[  333.673785] Open file "/etc/Wireless/RT2870STA/RT2870STA.dat" failed!
[  333.730044] !!! rt28xx Initialized fail !!!
[ 3428.361441] <==== rt28xx_init, Status=0
[ 3502.039553] <==== rt28xx_init, Status=0

---

### Post by dlindster on 2010-08-29
Worked perfect for me!  Thanks Chili.

-Sincerely, a total Newb

---

### Post by drewciferpike on 2010-10-13
Sweet Jesus on a pogo stick... I am so glad I found this thread! I was scared that I would have to compile code, etc., and because I am completely new to Linux, I was ready to be a wreck, by the time I was done.

Thank you SO much for posting this wonderful information!

** For others who read this after 10-13-2010: I ordered an older version of the WUSB54GC, but received the v.3 model. To make super-sure of everything, I typed " lsusb " in the terminal, looked for anything "Linksys", and made sure the man/dev codes were 1737:0077 (I had MAJOR problems trying to install an HVR-1250 that wasn't matching the codes it was supposed to have, so I'm a little gun-shy). When plugged right in, the adapter didn't work with Ubuntu 10.4 LTS, and I didn't bother to try 10.10 because it just came out. All I did was perform the blacklisting actions posted at the beginning of this thread, and I was good to go...

UPDATE: Because this followed a fresh install, the update manager blew its load and updated everything, once I got connected. After the update reboot, I still connected without a hitch.

---

### Post by hrpr on 2010-10-13
I have a black WUSB54GC, Version 3 and had no problems getting it working with Ubuntu 10.10.

Plugged it in, ran lsusb to see if it was detected...it was.  Configured it as wlan0 and connected to two different wireless access points with no problems.

---

### Post by cccddd on 2010-10-18
Chili,

Thanks so much for your help.  My card was connecting at startup but dropping about as fast as i could open a browser.  Once i did your steps in post #2, everything worked flawlessly.  Youve been a great help, Thanks again!!!


> **chili555 said:**
> Please open a terminal and let's get our geek on! Please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```The text editor gedit will pop open and we will add three lines at the end:```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread carefully. Save and close gedit. Reboot.

Click the Network Manager icon, see your network and connect. Use your working wireless connection to post back and report your success.

---

### Post by olithered on 2010-10-20
> **chili555 said:**
> Please open a terminal and let's get our geek on! Please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```The text editor gedit will pop open and we will add three lines at the end:```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread carefully. Save and close gedit. Reboot.

Click the Network Manager icon, see your network and connect. Use your working wireless connection to post back and report your success.

Worked perfectly for me on 10.04 with a Dlink DWA-140 (07d1:3c09).

---

### Post by Goolie on 2010-12-06
> **chili555 said:**
> Please open a terminal and let's get our geek on! Please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```The text editor gedit will pop open and we will add three lines at the end:```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread carefully. Save and close gedit. Reboot.

Click the Network Manager icon, see your network and connect. Use your working wireless connection to post back and report your success.

chili555

I was searching for an answer to this, and I *finally* got this thread.  I don't know exactly what your voodoo magic done did, but I'm not getting disconnects after 5 seconds.  It's only been up and running for approximately 10 minutes, but full signal strength and running perfectly.  Thank you so much for this contribution, you win 9000 internets.  And cookies if I could bake.

---

### Post by DethKore on 2011-01-31
Chili, I have read through this post multiple times and have followed everything up until about page 7 where you go into ndiswrapper. I have a wlan0 interface that can see my network but whenever I enter the correct password to the WPA encryption, the wireless manager will chug along for 2 minutes or so and ask me for the password again even thought I know I entered the correct one. It never connects to my router. Any Suggestions on what to do next?

---

### Post by edgardvicente on 2011-07-27
> **Tonyr63 said:**
> Hi

i have tried all the troubleshooting steps here and it appears to me that my USD wireless is dead unless i plug it into a windows machine.  How can it be so hard to get this sucker to work.

This is what i did.

1.) Download the driver  (2009_1110_RT3070_Linux_STA_v2.1.2.0) 
2.) Extracted it to your Desktop
Basically if you double-click on it the Archive Manager will start and you need to choose where to Extract. 
3.) Go to the folder 
code: 
 
Quote: 
cd /home/anthony/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0   
 
4.) code: 
 
Quote: 
sudo make   
  (or anywhere, but I used that one)  
(obviously it will ask for your sudo/administrator password) 
5.) code: 
 
Quote: 
make install   
 
6.) Create two files in the next steps: 
code: 
 
Quote: 
gedit /etc/udev/rules.d/network_drivers.rules   
 
then when the text editor opens up 
copy and paste the followings exactly as it is. case and all, quotes and all: 
 
Quote: 
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1784", RUN+="/sbin/modprobe -qba rt3070sta"   
 
save and close the text editor. 
 
Quote: 
gedit /etc/modprobe.d/network_drivers.conf   
 
the copy and paste as above: 
 
Quote: 
install rt3070sta /sbin/modprobe --ignore-install rt3070sta $CMDLINE_OPTS; /bin/echo "0b05 1784" > /sys/bus/usb/drivers/rt2870/new_id   
 
save and close text editor. 
7.) plug the USB device in (mine wasn't recognized until I restarted...) 
8.) exit terminal window 
9.) restart system 
10.) configure your wireless 

NOTHING WORKS

I tried some stuff from the terminal


anthony@TeleLinux:~$ lsmod | grep -e rt2 -e ndis
anthony@TeleLinux:~$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
anthony@TeleLinux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

anthony@TeleLinux:~$ sudo iwlist wlan0 scan
[sudo] password for anthony: 
wlan0     Interface doesn't support scanning.

anthony@TeleLinux:~$ sudo cat /var/log/syslog | grep ndis
anthony@TeleLinux:~$ sudo tail -n 25 /var/log/syslog
Jul 21 23:18:24 TeleLinux dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Jul 21 23:18:24 TeleLinux dhclient: 
Jul 21 23:18:24 TeleLinux NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Jul 21 23:18:24 TeleLinux dhclient: Listening on LPF/eth0/00:16:41:6a:5b:ce
Jul 21 23:18:24 TeleLinux dhclient: Sending on   LPF/eth0/00:16:41:6a:5b:ce
Jul 21 23:18:24 TeleLinux dhclient: Sending on   Socket/fallback
Jul 21 23:18:28 TeleLinux dhclient: DHCPREQUEST of 10.1.1.7 on eth0 to 255.255.255.255 port 67
Jul 21 23:18:28 TeleLinux dhclient: DHCPACK of 10.1.1.7 from 10.1.1.1
Jul 21 23:18:28 TeleLinux dhclient: bound to 10.1.1.7 -- renewal in 867763539 seconds.
Jul 21 23:18:28 TeleLinux NetworkManager: <info>  DHCP: device eth0 state changed preinit -> reboot
Jul 21 23:18:28 TeleLinux NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jul 21 23:18:28 TeleLinux NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Jul 21 23:18:28 TeleLinux NetworkManager: <info>    address 10.1.1.7
Jul 21 23:18:28 TeleLinux NetworkManager: <info>    prefix 24 (255.255.255.0)
Jul 21 23:18:28 TeleLinux NetworkManager: <info>    gateway 10.1.1.1
Jul 21 23:18:28 TeleLinux NetworkManager: <info>    nameserver '10.1.1.1'
Jul 21 23:18:28 TeleLinux NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jul 21 23:18:28 TeleLinux NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Jul 21 23:18:28 TeleLinux NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Jul 21 23:18:29 TeleLinux NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Jul 21 23:18:29 TeleLinux NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Jul 21 23:18:29 TeleLinux NetworkManager: <info>  Activation (eth0) successful, device activated.
Jul 21 23:18:29 TeleLinux NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Jul 21 23:18:30 TeleLinux ntpdate[1649]: adjust time server 91.189.94.4 offset -0.035467 sec
Jul 21 23:18:35 TeleLinux kernel: [  702.772010] eth0: no IPv6 routers present
anthony@TeleLinux:~$ dmesg | grep -i rt2
[   10.057982] usbcore: registered new interface driver rt2870
anthony@TeleLinux:~$ lsusd
No command 'lsusd' found, did you mean:
 Command 'lsusb' from package 'usbutils' (main)
lsusd: command not found
anthony@TeleLinux:~$ sudo modprobe rt2870sta
FATAL: Error inserting rt2870sta (/lib/modules/2.6.32-21-generic/kernel/drivers/staging/rt2870/rt2870sta.ko): Device or resource busy
anthony@TeleLinux:~$ sudo modprobe rt2870sta
FATAL: Error inserting rt2870sta (/lib/modules/2.6.32-21-generic/kernel/drivers/staging/rt2870/rt2870sta.ko): Device or resource busy
anthony@TeleLinux:~$ sudo modprobe rt2870sta
FATAL: Error inserting rt2870sta (/lib/modules/2.6.32-21-generic/kernel/drivers/staging/rt2870/rt2870sta.ko): Device or resource busy
anthony@TeleLinux:~$ sudo modprobe rt2870sta
FATAL: Error inserting rt2870sta (/lib/modules/2.6.32-21-generic/kernel/drivers/staging/rt2870/rt2870sta.ko): Device or resource busy
anthony@TeleLinux:~$ dmesg | grep -i rt2
[   10.057982] usbcore: registered new interface driver rt2870
[ 1686.188723] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[ 1686.195734] Error: Driver 'rt2870' is already registered, aborting...
[ 1686.195740] usbcore: error -16 registering interface     driver rt2870
[ 1743.779835] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[ 1743.787637] Error: Driver 'rt2870' is already registered, aborting...
[ 1743.787642] usbcore: error -16 registering interface     driver rt2870
[ 1821.036486] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[ 1821.044409] Error: Driver 'rt2870' is already registered, aborting...
[ 1821.044414] usbcore: error -16 registering interface     driver rt2870
[ 1852.200562] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[ 1852.210781] Error: Driver 'rt2870' is already registered, aborting...
[ 1852.210786] usbcore: error -16 registering interface     driver rt2870
anthony@TeleLinux:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0b05:1784 ASUSTek Computer, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
anthony@TeleLinux:~$ dmesg | grep -i RT3
anthony@TeleLinux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
.  
I did not install the NDISwrapper as most advise that this is not required.

What do I do next?

:(

Hi People,

I did this procedures and my WUSB54gc was recognized but don't find any wireless network.
What i can do? Please help me
im attaching my listing.zip like another post.

---

