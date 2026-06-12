---
title: "Ready to blow this up Broadcom B43"
date: 2010-12-04
forum: Networking &amp; Wireless
---

### Post by bmcgarrahan on 2010-12-04
Until yesterday I had no problems with using the B43 wireless driver set on my laptop since the initial installation of 10.10.  The first fix took mere minutes and have been worry free since.  Yesterday, with only one known change made, which was removing XDVDShrink through the Synaptic Package Manager, something happened giving me serious trouble.

I thought initially I was having a router problem since the connection was dropping and reconnecting, but it was clear when I used another computer the problem was with mine.  It would drop and reconnect,usually having to go through the authentication several times before logging on.  I looked for fixes and everything pointed me back to the initial install, so I removed the appropriate drivers and files and began to reinstall.  [This is the method I followed for B43 drivers using the "not connected to the internet"]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access") ([https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access)) part since I never did get my wired driver to work on 10.10.  

The first time I applied that fix yesterday it worked without a restart.  Everything seemed fine and then I did a restart and it showed all of my firmware was missing again.  I went through the steps again and it worked again.  Then I was forced to do it again, and now again, only this time it did not work and I am left without a wireless card.  All the fixes from various threads seem the same to me and I am left with a computer unable to access the internet.

I am at my wits end with this one after reading threads seemingly as long as *War and Peace*.

---

### Post by chili555 on 2010-12-04
Let's do some diagnostics. Please cold-boot your computer and open a terminal and run:```
dmesg | grep b43
ls -al /lib/firmware/b43
ls -al /lib/firmware/b43-open
```You can copy and paste from the terminal into a text document and transfer it on a USB key or similar.

---

### Post by bmcgarrahan on 2010-12-04
Additional information:  With each attempt at repair I had the B43 driver showing under **System/Administration/Additional Drivers**, but now that is gone.  Not sure what I did to it.  Here is the output of the request:
>    
   
  ls -al /lib/firmware/b43
   
  total 292
    drwxr-x---  2 root root  4096 2010-12-04 09:23 .
    drwxr-xr-x 52 root root  4096 2010-12-04 09:23 ..
    -rw-r--r--  1 root root   158 2010-12-04 09:23 a0g0bsinitvals5.fw
    -rw-r--r--  1 root root   158 2010-12-04 09:23 a0g0bsinitvals9.fw
    -rw-r--r--  1 root root  1840 2010-12-04 09:23 a0g0initvals5.fw
    -rw-r--r--  1 root root  2002 2010-12-04 09:23 a0g0initvals9.fw
    -rw-r--r--  1 root root   158 2010-12-04 09:23 a0g1bsinitvals13.fw
    -rw-r--r--  1 root root   158 2010-12-04 09:23 a0g1bsinitvals5.fw
    -rw-r--r--  1 root root   158 2010-12-04 09:23 a0g1bsinitvals9.fw
    -rw-r--r--  1 root root  2080 2010-12-04 09:23 a0g1initvals13.fw
    -rw-r--r--  1 root root  1840 2010-12-04 09:23 a0g1initvals5.fw
    -rw-r--r--  1 root root  2002 2010-12-04 09:23 a0g1initvals9.fw
    -rw-r--r--  1 root root   158 2010-12-04 09:23 b0g0bsinitvals13.fw
    -rw-r--r--  1 root root   158 2010-12-04 09:23 b0g0bsinitvals5.fw
    -rw-r--r--  1 root root   158 2010-12-04 09:23 b0g0bsinitvals9.fw
    -rw-r--r--  1 root root  2080 2010-12-04 09:23 b0g0initvals13.fw
    -rw-r--r--  1 root root  1840 2010-12-04 09:23 b0g0initvals5.fw
    -rw-r--r--  1 root root  2002 2010-12-04 09:23 b0g0initvals9.fw
    -rw-r--r--  1 root root   158 2010-12-04 09:23 lp0bsinitvals13.fw
    -rw-r--r--  1 root root   158 2010-12-04 09:23 lp0bsinitvals14.fw
    -rw-r--r--  1 root root   158 2010-12-04 09:23 lp0bsinitvals15.fw
    -rw-r--r--  1 root root  3618 2010-12-04 09:23 lp0initvals13.fw
    -rw-r--r--  1 root root  2064 2010-12-04 09:23 lp0initvals14.fw
    -rw-r--r--  1 root root  2052 2010-12-04 09:23 lp0initvals15.fw
    -rw-r--r--  1 root root   158 2010-12-04 09:23 n0absinitvals11.fw
    -rw-r--r--  1 root root   158 2010-12-04 09:23 n0bsinitvals11.fw
    -rw-r--r--  1 root root  2100 2010-12-04 09:23 n0initvals11.fw
    -rw-r--r--  1 root root  1320 2010-12-04 09:23 pcm5.fw
    -rw-r--r--  1 root root 29864 2010-12-04 09:23 ucode11.fw
    -rw-r--r--  1 root root 32232 2010-12-04 09:23 ucode13.fw
    -rw-r--r--  1 root root 31384 2010-12-04 09:23 ucode14.fw
    -rw-r--r--  1 root root 30488 2010-12-04 09:23 ucode15.fw
    -rw-r--r--  1 root root 22384 2010-12-04 09:23 ucode5.fw
    -rw-r--r--  1 root root 25160 2010-12-04 09:23 ucode9.fw
     
    ls -al /lib/firmware/b43-open
   
  cannot access /lib/firmware/b43-open: No such file or directory
  

---

### Post by chili555 on 2010-12-04
How about the first command?```
dmesg | grep b43
```

---

### Post by bmcgarrahan on 2010-12-04
That returned nothing at all, not even a response...

---

### Post by chili555 on 2010-12-04
Please do:```
sudo modprobe b43
dmesg | grep b43
iwconfig
```Is your wireless working now? If so, we'll need to do one more step to make it permanent.

If not, post:```
lspci -nn | grep -i 14e4
```

---

### Post by bmcgarrahan on 2010-12-04
About a few seconds after the first command I received a wireless signal and was able to connect.  YAY!  Here is the output:

>   Sudo modprobe b43
  WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
    WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
   
  dmesg | grep b43
    [ 1596.507430] b43-pci-bridge 0000:02:09.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
    [ 1596.580276] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
    [ 1596.693376] Registered led device: b43-phy0::tx
    [ 1596.693404] Registered led device: b43-phy0::rx
    [ 1596.693431] Registered led device: b43-phy0::radio
    [ 1597.068085] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
   
  iwconfig
    lo        no wireless extensions.
     
   
  eth0      no wireless extensions.
     
   
  wlan0     IEEE 802.11bg  ESSID:"BrianNet2"  
              Mode:Managed  Frequency:2.427 GHz  Access Point: 00:22:75:B8:4F:5B   
              Bit Rate=54 Mb/s   Tx-Power=20 dBm   
              Retry  long limit:7   RTS thr:off   Fragment thr:off
              Power Management:off
              Link Quality=70/70  Signal level=-38 dBm  
              Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
              Tx excessive retries:0  Invalid misc:0   Missed beacon:0
     
  lspci -nn | grep -i 14e4
  Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
   
  

---

### Post by chili555 on 2010-12-04
Clearly, b43 is the correct driver module but, evidently it's not loading on boot. Let's try to force it:```
sudo su
echo b43 >> /etc/modules
exit
```You should be all set, but post back if you need more help.

---

### Post by bmcgarrahan on 2010-12-04
Okay, now it has dropped the connection and has requested authentication numerous times.  The B43 driver is still not active...

---

### Post by bmcgarrahan on 2010-12-04
After reboot it just keeps asking to authenticate and never actually connects.

---

### Post by bmcgarrahan on 2010-12-04
I guess I should ask this question.  Should I attempt to activate the driver under System/Administration/Additional Drivers or should I leave it unactivated?  It seems to lose the connection during the attempt to activate and I must restart to get another connection.

---

### Post by bmcgarrahan on 2010-12-04
Nevermind, it drops the connection if I have more than just a single webpage loading at one time....

---

### Post by bmcgarrahan on 2010-12-04
No connection at all now.  Back to the problem that led me to begin trying to fix this.  It almost feels like the problem I had when I first installed 10.10 which was the connection dropping,music skipping, and monitor not being detected.  All the problems were fixed when I upgraded the Intel855 driver.  Why those are all related I did not know, but now I am back to square one except the sound is fine and the monitor is still properly detected.

---

### Post by chili555 on 2010-12-04
> but now I am back to square oneMeaning what? Your wireless works or doesn't work? If it doesn't work, let's see:```
sudo modprobe b43
dmesg | grep b43
```

---

### Post by bmcgarrahan on 2010-12-04
Thanks for your help...
output:
> lowbranch@lowbranch-M320:~$ sudo modprobe b43
[sudo] password for lowbranch: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
lowbranch@lowbranch-M320:~$ dmesg | grep b43
[   24.278449] b43-pci-bridge 0000:02:09.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   25.087570] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   25.727647] Registered led device: b43-phy0::tx
[   25.727672] Registered led device: b43-phy0::rx
[   25.727698] Registered led device: b43-phy0::radio
[   26.809424] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)

---

### Post by bmcgarrahan on 2010-12-04
I have this connected now, but it is really slow.  Pinging results in 50-52% packet loss and I found a problem I did not have when this morning began: USB drives will not mount...

---

### Post by bmcgarrahan on 2010-12-04
Tentatively fixed.  Chili555 thanks for a lot of help...

---

### Post by northd_tech on 2010-12-04
Hi b,

Since the Broadcom 43xx is a whole family of wireless chips, I'm wondering which flavor you specifically have.  I know that many of the Broadcoms work nearly flawlessly with the Broadcom "STA" proprietary hardware driver activated (but the b43 stuff usually needs to be blacklisted and/or deleted on those).  Broadcom is one of the few companies where you can actually download a wireless Linux driver from their website, and it is a pretty painless "build" from what I recall.

Have you posted the output of these terminal commands here yet, or did I miss it above?
```
lspci
lshw -C network
```

I'm wondering if this is one of the newer generation chipsets or a 431x version (which the b43 module was written for as I recall).

---

### Post by chili555 on 2010-12-04
> **northd_tech said:**
> Hi b,

Since the Broadcom 43xx is a whole family of wireless chips, I'm wondering which flavor you specifically have.  I know that many of the Broadcoms work nearly flawlessly with the Broadcom "STA" proprietary hardware driver activated (but the b43 stuff usually needs to be blacklisted and/or deleted on those).  Broadcom is one of the few companies where you can actually download a wireless Linux driver from their website, and it is a pretty painless "build" from what I recall.

Have you posted the output of these terminal commands here yet, or did I miss it above?
```
lspci
lshw -C network
```

I'm wondering if this is one of the newer generation chipsets or a 431x version (which the b43 module was written for as I recall).Please see post #7:> lspci -nn | grep -i 14e4
Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)I believe b43 and ssb are correct for his device.

---

### Post by homeuser1 on 2010-12-04
> **chili555 said:**
> If it doesn't work, let's see:```
sudo modprobe b43
dmesg | grep b43
```

What key do you use to make the vertical line?  I've been screwing around all day trying to get my Broadcom 4306 working.

I found it! duh

---

### Post by homeuser1 on 2010-12-04
So, where can I find the B43 driver for linux to download for a BCM4306 network adpater?

---

### Post by chili555 on 2010-12-04
The module b43 is already built in to the kernel. The required firmware needs to be downloaded and installed. Do you have an ethernet connection? Can you go to System > Administration > Additional drivers and activate your driver?

---

### Post by homeuser1 on 2010-12-04
The driver has been there and activated but disappears after some unknown change.  I'm currently reinstalling 10.10 to see if it comes back.  What a frustrating day.

---

### Post by chili555 on 2010-12-04
You shouldn't have to reinstall. Is the firmware in place?```
ls /lib/firmware/b43
```Is the driver loaded?```
lsmod | grep b43
```We can fix either or both issues without reinstalling.

---

### Post by northd_tech on 2010-12-04
> **homeuser1 said:**
> So, where can I find the B43 driver for linux to download for a BCM4306 network adpater?
Along that line of questioning, looking for the answer here:

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

I noticed this little note:
> This number is read by driver ssb, and the correct choice for your  device is made at that point. Note: If your card is a** BCM4306 Rev 2, or  only has 802.11b capability, it uses b43legacy. All other models use b43**That could be part of the problem (esp. with relatively "really old" hardware in relatively "really newer" Linux kernels), no?

---

### Post by chili555 on 2010-12-04
> That could be part of the problem (esp. with relatively "really old" hardware in relatively "really newer" Linux kernels), no?Absolutely, although I haven't seen a b43legacy in a few years, however, that doesn't mean that homeuser1 doesn't have one. Just to be on the safe side, homeuser1, please let us both see:```
lspci -nn | grep -i 14e4
```We will then check in *modinfo ssb* and be sure it's b43 or b43legacy.

Good catch, northd_tech!

---

### Post by homeuser1 on 2010-12-04
Here's screen shot for you to look at.  This is after a clean install of 10.10. 

dell@dell-Latitude-D600:~$ sudo ls /lib/firmware/b43 
ls: cannot access /lib/firmware/b43: No such file or directory 
dell@dell-Latitude-D600:~$ lsmod | grep b43 
dell@dell-Latitude-D600:~$ lspci -nn | grep -i 14e4 
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

---

### Post by chili555 on 2010-12-04
It appears b43 and ssb are the correct drivers for your device.> modinfo ssb | grep 4320
alias:          pci:v0000[COLOR="Red"]14E4[/COLOR]d0000[COLOR="Red"]4320[/COLOR]sv*sd*bc*sc*i*You do not have the firmware. Can you get an ethernet connection and go to System > Administration > Additional drivers and activate your driver? This downloads and installs the firmware.

---

### Post by homeuser1 on 2010-12-04
> **chili555 said:**
>  Can you get an ethernet connection and go to System > Administration > Additional drivers and activate your driver?

I can't get a connection on the computer I'm trying to install 10.10 on.  I have another laptop with xp running that I can use.

I could install 10.4 and probably have the driver, but I still wouldn't have either a LAN or wireless connection.

---

### Post by chili555 on 2010-12-04
Please run:```
dmesg | grep b43
```Let's see what firmware it wants and maybe we can cheat it up.

---

### Post by homeuser1 on 2010-12-04
Here you go....Thanks for your help!

[    1.600350] b43-pci-bridge 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5 
[   18.289598] b43-phy0: Broadcom 4306 WLAN found (core revision 5) 
[   18.551927] Registered led device: b43-phy0::tx 
[   18.551958] Registered led device: b43-phy0::rx 
[   18.551990] Registered led device: b43-phy0::radio 
[   18.728598] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[   18.728661] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found 
[   18.728716] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.

---

### Post by chili555 on 2010-12-04
Please download the attached to your desktop. Right-click it and select 'Extract here.' Open a terminal and do:```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/ucode5.fw /lib/firmware/b43
sudo chmod 644 /lib/firmware/b43/*
sudo chown root:root /lib/firmware/b43/*
sudo rmmod -f ssb b43
sudo modprobe b43
```Any improvements?

---

### Post by homeuser1 on 2010-12-04
Download and extraction went well,but it doesn't look like it is going to load.  What do you think?  Continue with the command lines?

sudo mkdir /lib/firmware/b43 
mkdir: cannot create directory `/lib/firmware/b43': File exists 
sudo cp desktop/ucode5.fw /lib/firmware/b43 
cp: cannot stat `desktop/ucode5.fw': No such file or directory

---

### Post by pdc on 2010-12-04
chili555 said 

> sudo cp **D**esktop/ucode5.fw

you tell us you have done

> sudo cp **d**esktop/ucode5.fw

in linux, the difference between

> D

and 

> d

means they are not seen as equivalents ...........

I would suggest you **COPY** and **PASTE** the commands chili recommends to you

---

### Post by homeuser1 on 2010-12-05
Hopefully this is correct.  Thanks again. 

sudo cp Desktop/ucode5.fw /lib/firmware/b43 
cp: cannot create regular file `/lib/firmware/b43/ucode5.fw': Permission denied
sudo chmod 644 /lib/firmware/b43/* 
sudo chown root:root /lib/firmware/b43/* 
sudo rmmod -f ssb b43 
ERROR: Removing 'ssb': Resource temporarily unavailable 
sudo modprobe b43

---

### Post by chili555 on 2010-12-05
Let's see if the firmware (magically) got there:```
ls /lib/firmware/b43
```Is ucode5.fw listed?

Is your wireless working now? Reboot and see if it's working.

---

### Post by homeuser1 on 2010-12-05
Well Chili, you may be a magician!  Wired connection worked on restart.  I was also asked to install the broadcom b43 wireless driver, which I did.   

ls /lib/firmware/b43
ucode5.fw

Why doesn't the network manager search for available wireless networks to connect to.  I can't see my home network.

---

### Post by chili555 on 2010-12-05
Is wired connected as you are looking for wireless networks? Network Manager is designed to not allow wireless if wired is available.

[https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has been managed for them

---

### Post by homeuser1 on 2010-12-05
When I disconnected the wired connection, it just lost the connection.  I'm guessing I have to figure out how to find or activate my wireless network.  I know I will have to put in the network key the first time I connect to it.  With windows, I see everyone's wireless network in within range to connect to.

---

### Post by chili555 on 2010-12-05
Is the module loaded?```
lsmod | grep b43
```If not, load it:```
sudo modprobe b43
```Does that bring the wireless to life? If not, let's have a look at:```
dmesg | grep b43
```

---

### Post by homeuser1 on 2010-12-05
Still not seeing any available networks.

lsmod | grep b43 
b43                   168681  0  
mac80211              231541  1 b43 
cfg80211              144470  2 b43,mac80211 
led_class               2633  1 b43 
ssb                    39288  1 b43

---

### Post by chili555 on 2010-12-05
As I already said:> Does that bring the wireless to life? If not, let's have a look at:
```
dmesg | grep b43

```


---

### Post by homeuser1 on 2010-12-05
My bad, sorry! Also, when I unplug the network cord, it doesn't automatically find any wireless networks available.  Do I have to activate it or something in system > administration > network tools or something?

b43-pci-bridge 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
b43-phy0: Broadcom 4306 WLAN found (core revision 5)
Registered led device: b43-phy0::tx
Registered led device: b43-phy0::rx
Registered led device: b43-phy0::radio
b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)

---

### Post by chili555 on 2010-12-05
You probably have to wait a minute or two. Let's look a little deeper:```
sudo cat /var/log/syslog | grep -e b43 -e wlan 
```If there are a lot of repeats, just post the last 20 or so lines. Also, let's see:```
cat /etc/network/interfaces
```Thanks.

---

### Post by homeuser1 on 2010-12-05
I returned from church and the laptop was frozen.  I couldn't login.  After a forced shutdown and restart, the wired connection was dead.  Here's the output from dmesg | grep b43:

b43-pci-bridge 0000:02:03.0: enabling device (0000 -> 0002) 
b43-pci-bridge 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5 
b43-pci-bridge 0000:02:03.0: setting latency timer to 64 
b43-phy0: Broadcom 4306 WLAN found (core revision 5) 
Registered led device: b43-phy0::tx 
Registered led device: b43-phy0::rx 
Registered led device: b43-phy0::radio 
b43-phy0 ERROR: Microcode not responding 
b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website. 
b43-phy0 ERROR: Microcode not responding 
b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.

---

### Post by chili555 on 2010-12-05
Please let me see:```
ls -al /lib/firmware/b43
```I specifically need to see all the little dots and dashes in the result.

This is mighty mysterious.

---

### Post by homeuser1 on 2010-12-05
You're probably getting as tired as I am trying to get this to work.  Is there an easier solution like buying a new network card that would be compatable with my Dell D600?  Thanks for hanging with this one.  

dell@dell-Latitude-D600:~$ ls -al /lib/firmware/b43 
ls: cannot open directory /lib/firmware/b43: Permission denied

---

### Post by chili555 on 2010-12-05
> ls: cannot open directory /lib/firmware/b43: Permission deniedThere's a fundamental problem. If the permissions are not right, the system can't read the file. Please do:```
ls -al /lib/firmware
```We hope the b43 line is:> [COLOR="Red"]drwxr-xr-x[/COLOR]  2 root root    4096 2010-11-02 10:36 b43If not, post back the exact listing and we'll decide how to proceed.

I doubt the issue is the card. I think one of us made an error when we created the file and copied over the firmware. Let's just fix it.

---

### Post by homeuser1 on 2010-12-05
The only line with b43 at the end is this:

drwxr-x--- 2 root root 4096 2010-12-05 08:24 b43

I can send the entire list if you like.

PS: I did redo post 35 again to see if the wired connection would magically come back.  It didn't.  However, the network adapter lights are on but not blinking.  Usually, they are off.

---

### Post by homeuser1 on 2010-12-05
Here's everything:

drwxr-xr-x 51 root root    4096 2010-12-05 08:45 . 
drwxr-xr-x 16 root root   12288 2010-12-05 08:46 .. 
drwxr-xr-x 32 root root    4096 2010-12-05 08:45 2.6.35-22-generic 
drwxr-xr-x 32 root root    4096 2010-12-05 08:45 2.6.35-23-generic 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 3com 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 acenic 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 adaptec 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 advansys 
-rw-r--r--  1 root root   50698 2010-08-16 15:02 agere_ap_fw.bin 
-rw-r--r--  1 root root   65046 2010-08-16 15:02 agere_sta_fw.bin 
-rw-r--r--  1 root root   22622 2010-08-16 15:02 aic94xx-seq.fw 
-rw-r--r--  1 root root   83968 2010-08-16 15:02 ar9170-1.fw 
-rw-r--r--  1 root root    3508 2010-08-16 15:02 ar9170-2.fw 
-rw-r--r--  1 root root   15960 2010-08-16 15:02 ar9170.fw 
-rw-r--r--  1 root root   51280 2010-08-16 15:02 ar9271.fw 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 asihpi 
-rw-r--r--  1 root root  246804 2010-08-16 15:02 ath3k-1.fw 
-rw-r--r--  1 root root  246804 2010-08-16 15:02 ath3k-2.fw 
-rw-r--r--  1 root root   30348 2010-08-16 15:02 atmel_at76c502_3com.bin 
-rw-r--r--  1 root root   31764 2010-08-16 15:02 atmel_at76c502.bin 
-rw-r--r--  1 root root   31764 2010-08-16 15:02 atmel_at76c502d.bin 
-rw-r--r--  1 root root   31776 2010-08-16 15:02 atmel_at76c502e.bin 
-rw-r--r--  1 root root   35180 2010-08-16 15:02 atmel_at76c504_2958.bin 
-rw-r--r--  1 root root   39928 2010-08-16 15:02 atmel_at76c504a_2958.bin 
-rw-r--r--  1 root root   31748 2010-08-16 15:02 atmel_at76c504.bin 
-rw-r--r--  1 root root   31824 2010-08-16 15:02 atmel_at76c506.bin 
-rw-r--r--  1 root root    9726 2010-08-16 15:02 atmsar11.fw 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 av7110 
drwxr-x---  2 root root    4096 2010-12-05 08:24 b43 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 bnx2 
-rw-r--r--  1 root root  165768 2010-08-16 15:02 bnx2x-e1-4.8.53.0.fw 
-rw-r--r--  1 root root  162800 2010-08-16 15:02 bnx2x-e1-5.2.7.0.fw 
-rw-r--r--  1 root root  192400 2010-08-16 15:02 bnx2x-e1h-4.8.53.0.fw 
-rw-r--r--  1 root root  205488 2010-08-16 15:02 bnx2x-e1h-5.2.7.0.fw 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 cis 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 cpia2 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 cxgb3 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 dabusb 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 dsp56k 
-rw-r--r--  1 root root   12401 2010-08-16 15:02 dvb-fe-xc5000-1.6.114.fw 
-rw-r--r--  1 root root   33768 2010-08-16 15:02 dvb-usb-dib0700-1.20.fw 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 e100 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 ea 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 edgeport 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 emi26 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 emi62 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 ess 
-rw-r--r--  1 root root  180760 2010-08-16 15:02 f2255usb.bin 
-rw-r--r--  1 root root   35068 2010-08-16 15:02 GPL-3 
-rw-r--r--  1 root root 1142480 2010-08-16 15:02 i2400m-fw-usb-1.3.sbcf 
-rw-r--r--  1 root root 1251036 2010-08-16 15:02 i2400m-fw-usb-1.4.sbcf 
-rw-r--r--  1 root root   34304 2010-08-16 15:02 intelliport2.bin 
-rw-r--r--  1 root root  209190 2010-08-16 15:02 ipw2100-1.3.fw 
-rw-r--r--  1 root root  201138 2010-08-16 15:02 ipw2100-1.3-i.fw 
-rw-r--r--  1 root root  196458 2010-08-16 15:02 ipw2100-1.3-p.fw 
-rw-r--r--  1 root root  191154 2010-08-16 15:02 ipw2200-bss.fw 
-rw-r--r--  1 root root  185428 2010-08-16 15:02 ipw2200-ibss.fw 
-rw-r--r--  1 root root  187836 2010-08-16 15:02 ipw2200-sniffer.fw 
-rw-r--r--  1 root root  335056 2010-08-16 15:02 iwlwifi-1000-3.ucode 
-rw-r--r--  1 root root  150100 2010-08-16 15:02 iwlwifi-3945-2.ucode 
-rw-r--r--  1 root root  187972 2010-08-16 15:02 iwlwifi-4965-2.ucode 
-rw-r--r--  1 root root  345008 2010-08-16 15:02 iwlwifi-5000-1.ucode 
-rw-r--r--  1 root root  353240 2010-08-16 15:02 iwlwifi-5000-2.ucode 
-rw-r--r--  1 root root  337400 2010-08-16 15:02 iwlwifi-5150-2.ucode 
-rw-r--r--  1 root root  454608 2010-08-16 15:02 iwlwifi-6000-4.ucode 
-rwxr-xr-x  1 root root  463692 2010-08-16 15:02 iwlwifi-6050-4.ucode 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 kaweth 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 keyspan 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 keyspan_pda 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 korg 
-rw-r--r--  1 root root     262 2010-08-16 15:02 lgs8g75.fw 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 libertas 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 matrox 
-rw-r--r--  1 root root   13847 2010-08-16 15:02 mts_cdma.fw 
-rw-r--r--  1 root root   14067 2010-08-16 15:02 mts_edge.fw 
-rw-r--r--  1 root root   13847 2010-08-16 15:02 mts_gsm.fw 
-rw-r--r--  1 root root   13769 2010-08-16 15:02 mts_mt9234mu.fw 
-rw-r--r--  1 root root   13769 2010-08-16 15:02 mts_mt9234zba.fw 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 mwl8k 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 myricom 
-rw-r--r--  1 root root   15664 2010-08-16 15:02 NPE-B 
-rw-r--r--  1 root root   15664 2010-08-16 15:02 NPE-C 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 ositech 
-rw-r--r--  1 root root   76802 2010-08-16 15:02 ql2100_fw.bin 
-rw-r--r--  1 root root   84566 2010-08-16 15:02 ql2200_fw.bin 
-rw-r--r--  1 root root  123170 2010-08-16 15:02 ql2300_fw.bin 
-rw-r--r--  1 root root  132978 2010-08-16 15:02 ql2322_fw.bin 
-rw-r--r--  1 root root  228056 2010-08-16 15:02 ql2400_fw.bin 
-rw-r--r--  1 root root  199776 2010-08-16 15:02 ql2500_fw.bin 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 qlogic 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 r128 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 radeon 
-rw-r--r--  1 root root    8192 2010-08-16 15:02 rt2561.bin 
-rw-r--r--  1 root root    8192 2010-08-16 15:02 rt2561s.bin 
-rw-r--r--  1 root root    8192 2010-08-16 15:02 rt2661.bin 
-rw-r--r--  1 root root    8192 2010-08-16 15:02 rt2860.bin 
-rw-r--r--  1 root root    4096 2010-08-16 15:02 rt2870.bin 
-rw-r--r--  1 root root    4096 2010-08-16 15:02 rt3070.bin 
-rw-r--r--  1 root root    4096 2010-08-16 15:02 rt3071.bin 
-rw-r--r--  1 root root    8192 2010-08-16 15:02 rt3090.bin 
-rw-r--r--  1 root root    2048 2010-08-16 15:02 rt73.bin 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 RTL8192E 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 RTL8192SE 
-rw-r--r--  1 root root    9508 2010-08-16 15:02 s2250.fw 
-rw-r--r--  1 root root    1092 2010-08-16 15:02 s2250_loader.fw 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 sb16 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 scripts 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 slicoss 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 sun 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 sxg 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 tehuti 
-rw-r--r--  1 root root   13765 2010-08-16 15:02 ti_3410.fw 
-rw-r--r--  1 root root   13764 2010-08-16 15:02 ti_5052.fw 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 tigon 
-rw-r--r--  1 root root    7614 2010-08-16 15:02 tr_smctr.bin 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 ttusb-budget 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 ueagle-atm 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 usbdux 
-rw-r--r--  1 root root     999 2010-08-16 15:02 usbduxfast_firmware.bin 
-rw-r--r--  1 root root    1770 2010-08-16 15:02 usbdux_firmware.bin 
-rw-r--r--  1 root root   16382 2010-08-16 15:02 v4l-cx231xx-avcore-01.fw 
-rw-r--r--  1 root root  141200 2010-08-16 15:02 v4l-cx23418-apu.fw 
-rw-r--r--  1 root root  158332 2010-08-16 15:02 v4l-cx23418-cpu.fw 
-rw-r--r--  1 root root   16382 2010-08-16 15:02 v4l-cx23418-dig.fw 
-rw-r--r--  1 root root  262144 2010-08-16 15:02 v4l-cx2341x-dec.fw 
-rw-r--r--  1 root root  376836 2010-08-16 15:02 v4l-cx2341x-enc.fw 
-rw-r--r--  1 root root  155648 2010-08-16 15:02 v4l-cx2341x-init.mpg 
-rw-r--r--  1 root root   16382 2010-08-16 15:02 v4l-cx23885-avcore-01.fw 
-rw-r--r--  1 root root   16382 2010-08-16 15:02 v4l-cx23885-enc.fw 
-rw-r--r--  1 root root   16382 2010-08-16 15:02 v4l-cx25840.fw 
-rw-r--r--  1 root root    8192 2010-08-16 15:02 v4l-pvrusb2-24xxx-01.fw 
-rw-r--r--  1 root root    8192 2010-08-16 15:02 v4l-pvrusb2-29xxx-01.fw 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 vicam 
-rw-r--r--  1 root root   23554 2010-08-16 15:02 whiteheat.fw 
-rw-r--r--  1 root root    5626 2010-08-16 15:02 whiteheat_loader.fw 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 yam 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 yamaha 
-rw-r--r--  1 root root   62484 2010-08-16 15:02 zd1201-ap.fw 
-rw-r--r--  1 root root   70612 2010-08-16 15:02 zd1201.fw 
drwxr-xr-x  2 root root    4096 2010-10-07 12:08 zd1211

---

### Post by chili555 on 2010-12-05
Post #35 has nothing to do with wired; let's work on that next.

These commands will be crucial; do not make a typo or miss a character or a space. Otherwise we will spend another 25-30 posts chasing our tails. Please do:```
sudo su
cd /lib/firmware
chmod 755 b43
chmod 755 b43/*
exit
```Now, reboot and give me your report.> I did redo post 35 again to see if the wired connection would magically come back. It didn't.Please stop. Please do nothing further until we have this fixed, unless I ask for it.

---

### Post by homeuser1 on 2010-12-05
I cut and paste the commands lines you sent.  

dell@dell-Latitude-D600:~$ sudo su 
[sudo] password for dell:  
root@dell-Latitude-D600:/home/dell# cd /lib/firmware 
root@dell-Latitude-D600:/lib/firmware# chmod 755 b43 
root@dell-Latitude-D600:/lib/firmware# chmod 755 b43/* 
root@dell-Latitude-D600:/lib/firmware# exit 
exit 
dell@dell-Latitude-D600:~$  

Upon restart the laptop froze with a bunch of mesage lines.  The cursor was just endlessly blinking.  I forced the shutdown and restarted.  No internet connection on restart.  I'm getting the same message output as in post 43.  What firmware is it trying to load?  

I need to leave for several hours.  I will be back later this evening.  

Thanks again for you help.

PS: if you want to make sure all the changes that have been made are your's, I could do a clean install of 10.10 again.  I did it a lot yesterday before you started helping.

---

### Post by CasparGrigoriNovykh on 2010-12-05
I am having a very similar (if not identical) problem to homeuser.  

```

sudo modprobe -r b43 ssb
sudo modprobe b43

```

These commands used to work, though they both had to be entered upon each boot.  Now, after no conscious changes were made, they fail to activate my wireless.  The icon's message now displays "device not ready (firmware missing)".  

My readout for "ls -al /lib/firmware" differs from homeuser.

drwxr-xr-x  2 root root     4096 2010-12-05 16:37 b43
drwxr-x---   2 root root     4096 2010-12-02 02:06 b43Legacy

Could it be that b43, and b43Legacy are conflicting?  I don't want to hijack this thread, so please continue as normal - if your solutions for homeuser do not apply to me, I will begin a new thread.  Thank you in advance for the help, guys.


Caspar

---

### Post by chili555 on 2010-12-05
> **CasparGrigoriNovykh said:**
> I am having a very similar (if not identical) problem to homeuser.  

```

sudo modprobe -r b43 ssb
sudo modprobe b43

```

These commands used to work, though they both had to be entered upon each boot.  Now, after no conscious changes were made, they fail to activate my wireless.  The icon's message now displays "device not ready (firmware missing)".  

My readout for "ls -al /lib/firmware" differs from homeuser.

drwxr-xr-x  2 root root     4096 2010-12-05 16:37 b43
drwxr-x---   2 root root     4096 2010-12-02 02:06 b43Legacy

Could it be that b43, and b43Legacy are conflicting?  I don't want to hijack this thread, so please continue as normal - if your solutions for homeuser do not apply to me, I will begin a new thread.  Thank you in advance for the help, guys.


CasparIt's a lot easier for me if you start a new thread. PM me if I don't catch it right away. Post:```
lspci -nn | grep -i 14e4
```Thanks.

---

### Post by homeuser1 on 2010-12-05
Hi Chili....here's the output from something you request earlier that did not produce this list.  

dell@dell-Latitude-D600:~$ ls -al /lib/firmware/b43 
total 292 
drwxr-xr-x  2 root root  4096 2010-12-05 08:24 . 
drwxr-xr-x 51 root root  4096 2010-12-05 08:45 .. 
-rwxr-xr-x  1 root root   158 2010-12-05 08:24 a0g0bsinitvals5.fw 
-rwxr-xr-x  1 root root   158 2010-12-05 08:24 a0g0bsinitvals9.fw 
-rwxr-xr-x  1 root root  1840 2010-12-05 08:24 a0g0initvals5.fw 
-rwxr-xr-x  1 root root  2002 2010-12-05 08:24 a0g0initvals9.fw 
-rwxr-xr-x  1 root root   158 2010-12-05 08:24 a0g1bsinitvals13.fw 
-rwxr-xr-x  1 root root   158 2010-12-05 08:24 a0g1bsinitvals5.fw 
-rwxr-xr-x  1 root root   158 2010-12-05 08:24 a0g1bsinitvals9.fw 
-rwxr-xr-x  1 root root  2080 2010-12-05 08:24 a0g1initvals13.fw 
-rwxr-xr-x  1 root root  1840 2010-12-05 08:24 a0g1initvals5.fw 
-rwxr-xr-x  1 root root  2002 2010-12-05 08:24 a0g1initvals9.fw 
-rwxr-xr-x  1 root root   158 2010-12-05 08:24 b0g0bsinitvals13.fw 
-rwxr-xr-x  1 root root   158 2010-12-05 08:24 b0g0bsinitvals5.fw 
-rwxr-xr-x  1 root root   158 2010-12-05 08:24 b0g0bsinitvals9.fw 
-rwxr-xr-x  1 root root  2080 2010-12-05 08:24 b0g0initvals13.fw 
-rwxr-xr-x  1 root root  1840 2010-12-05 08:24 b0g0initvals5.fw 
-rwxr-xr-x  1 root root  2002 2010-12-05 08:24 b0g0initvals9.fw 
-rwxr-xr-x  1 root root   158 2010-12-05 08:24 lp0bsinitvals13.fw 
-rwxr-xr-x  1 root root   158 2010-12-05 08:24 lp0bsinitvals14.fw 
-rwxr-xr-x  1 root root   158 2010-12-05 08:24 lp0bsinitvals15.fw 
-rwxr-xr-x  1 root root  3618 2010-12-05 08:24 lp0initvals13.fw 
-rwxr-xr-x  1 root root  2064 2010-12-05 08:24 lp0initvals14.fw 
-rwxr-xr-x  1 root root  2052 2010-12-05 08:24 lp0initvals15.fw 
-rwxr-xr-x  1 root root   158 2010-12-05 08:24 n0absinitvals11.fw 
-rwxr-xr-x  1 root root   158 2010-12-05 08:24 n0bsinitvals11.fw 
-rwxr-xr-x  1 root root  2100 2010-12-05 08:24 n0initvals11.fw 
-rwxr-xr-x  1 root root  1320 2010-12-05 08:24 pcm5.fw 
-rwxr-xr-x  1 root root 29864 2010-12-05 08:24 ucode11.fw 
-rwxr-xr-x  1 root root 32232 2010-12-05 08:24 ucode13.fw 
-rwxr-xr-x  1 root root 31384 2010-12-05 08:24 ucode14.fw 
-rwxr-xr-x  1 root root 30488 2010-12-05 08:24 ucode15.fw 
-rwxr-xr-x  1 root root 22264 2010-12-05 12:51 ucode5.fw 
-rwxr-xr-x  1 root root 25160 2010-12-05 08:24 ucode9.fw

---

### Post by homeuser1 on 2010-12-05
Hey Chili...even though I wasn't connecting to the internet via the wired connection, I right clicked on the wireless icon on the panel bar and what do you know, I saw my network and the neighbors network showing up.  I entered the my network key and I'm connected! 

So, As long as this lasts, I'm good to go.  Any idea why the wired connection won't work?

---

### Post by chili555 on 2010-12-05
WOO HOO!!! I am super glad it's working.

Please start a new thread and post:```
lspci -nn
```I'll be right there.

---

### Post by Bucic on 2011-02-13
B43 driver listed under Additional Drivers as used and active.

I culdn't even lit my wireless button on my laptop but after executing these commands
```
sudo modprobe b43
dmesg | grep b43
iwconfig
```it lit up!

Unfortunately network manager does not find any connections. Can you guys help me out. After spending literally days dealing with moronic installer that was  trying to access a dead URL I feel I'm close, for the first time. My hardware ID [14e4:4318] is listed as supported on Linux Wireless...


Here's a few commands and returns:

```
lsmod | grep bsudo ls /lib/firmware/b43
a0g0bsinitvals5.fw  a0g1bsinitvals13.fw  a0g1initvals5.fw     b0g0bsinitvals9.fw  lp0bsinitvals13.fw  lp0initvals14.fw      n0initvals11.fw  ucode14.fw
a0g0bsinitvals9.fw  a0g1bsinitvals5.fw     a0g1initvals9.fw     b0g0initvals13.fw   lp0bsinitvals14.fw  lp0initvals15.fw      pcm5.fw       ucode15.fw
a0g0initvals5.fw    a0g1bsinitvals9.fw     b0g0bsinitvals13.fw  b0g0initvals5.fw      lp0bsinitvals15.fw  n0absinitvals11.fw  ucode11.fw       ucode5.fw
a0g0initvals9.fw    a0g1initvals13.fw     b0g0bsinitvals5.fw   b0g0initvals9.fw      lp0initvals13.fw    n0bsinitvals11.fw   ucode13.fw       ucode9.fw
#:~$ lsmod | grep b43
b43                   168681  0 
ssb                    39320  1 b43
mac80211              231959  3 b43,rt2x00usb,rt2x00lib
cfg80211              144694  3 b43,rt2x00lib,mac80211
led_class               2633  3 b43,rt2x00lib,sdhci
__________________________________________________
#:~$ lspci -nn | grep -i 14e4
02:01.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet [14e4:169c] (rev 03)
02:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
__________________________________________________
#:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
02:01.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
02:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
02:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
02:04.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
__________________________________________________
#:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5788 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:0f:b0:74:9e:36
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.110 firmware=5788-v3.26 latency=64 mingnt=64 multicast=yes
       resources: irq:23 memory:d0000000-d000ffff
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:22 memory:d0010000-d0011fff
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:15:bc:32
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-25-generic firmware=N/A multicast=yes wireless=IEEE 802.11bg
__________________________________________________
#:~$ dmesg | grep b43
[ 1848.373307] b43-pci-bridge 0000:02:02.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 1848.447991] b43-phy2: Broadcom 4318 WLAN found (core revision 9)
[ 1848.531003] Registered led device: b43-phy2::radio
[ 1935.260062] b43-phy2: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1979.096070] b43-phy2: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 2024.584069] b43-phy2: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 2071.028080] b43-phy2: Radio hardware status changed to DISABLED
[ 2076.036077] b43-phy2: Radio hardware status changed to ENABLED
[ 2076.276070] b43-phy2: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 2167.396060] b43-phy2: Loading firmware version 410.2160 (2007-05-26 15:32:10)
#:~$ 

```

---

### Post by chili555 on 2011-02-13
> #:~$ lsmod | grep b43
b43                   168681  0 
ssb                    39320  1 b43
mac80211              231959  3 b43,[COLOR="Red"]rt2x00usb,rt2x00lib[/COLOR]
cfg80211              144694  3 b43,[COLOR="Red"]rt2x00lib[/COLOR],mac80211
led_class               2633  3 b43,[COLOR="Red"]rt2x00lib[/COLOR],sdhci
Any idea why these are loaded? Do you also have a USB wireless device? May we see:```
cat /etc/modules
```I love a mystery!

---

### Post by Bucic on 2011-02-13
It returned only description (commented lines, hashes) plus
```
lp
```

Edit:
Maybe it is due to the fact that today I have connected my USB wireless modem for a moment to check if it's detected (wasn't). I have disconnected it but I haven't restarted the machine since.

EDIT 2:
Yup, all the entries marked red by you are gone now! So the only mystery now is that Ubuntu doesn't show/search for any new wireless connections. LAN cable is disconnected, networking enabled, but there's a '!' on the networking icon on the taskbar (or what's that bar called in ubuntu).

---

### Post by chili555 on 2011-02-13
How about we take a gander at:```
rfkill list all
```Thanks.

---

### Post by Bucic on 2011-02-13
```
~$ rfkill list all
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

---

### Post by chili555 on 2011-02-13
Bad news, or good news depending on how you look at it. I really don't see anything wrong that needs fixing. What does this tell us?```
sudo iwlist wlan0 scan
iwconfig
```Let's resume tomorrow after you, the computer and I take a little rest.

---

### Post by Bucic on 2011-02-13
You can imagine me smiling because noob I am I know that wifi detects external networks ;)

OK, till tomorrow. I'm in no position to nag you and I am already grateful for your help.
 
```
~$ sudo iwlist wlan0 scan
[sudo] password for hg1: 
wlan0     Scan completed :
          Cell 01 - Address: 1C:AF:F7:44:5A:B2
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"rt311"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000a6e0f00f17b
                    Extra: Last beacon: 1012ms ago
                    IE: Unknown: 00057274333131
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050100000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706474220010D10
                    IE: Unknown: DD1E00904C33EE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401050100000000000000000000000000000000000000
          Cell 02 - Address: 00:26:F2:60:1B:D8
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Ssspoko"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000eb3ddbd1f2
                    Extra: Last beacon: 1084ms ago
                    IE: Unknown: 0007537373706F6B6F
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: 00:0E:8E:20:D3:1E
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:off
                    ESSID:"M57_securex601217454"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=0000045b25d64db0
                    Extra: Last beacon: 796ms ago
                    IE: Unknown: 00144D35375F73656375726578363031323137343534
                    IE: Unknown: 010482040B16
                    IE: Unknown: 030103
                    IE: Unknown: DD2A000C42000000011E00000000006618030000686F7473706F740000000000000000000000000005027609
          Cell 04 - Address: 00:1C:F0:14:8F:91
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"dlink165"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000018a83d910ef9
                    Extra: Last beacon: 680ms ago
                    IE: Unknown: 0008646C696E6B313635
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 0706474220010D11
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 05 - Address: 00:4F:62:26:95:76
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"silliker_wifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000063dd4683bf1
                    Extra: Last beacon: 412ms ago
                    IE: Unknown: 000D73696C6C696B65725F77696669
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0700E04C01020300
          Cell 06 - Address: 00:22:6B:95:1E:67
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"dark-net"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000eb3decb32a
                    Extra: Last beacon: 548ms ago
                    IE: Unknown: 00086461726B2D6E6574
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 07 - Address: 00:0C:42:05:C9:C1
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"NajtanszyInternet.pl_14"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000fb9184
                    Extra: Last beacon: 604ms ago
                    IE: Unknown: 00174E616A74616E737A79496E7465726E65742E706C5F3134
                    IE: Unknown: 010482040B16
                    IE: Unknown: 030108
                    IE: Unknown: DD2A000C42000000011E00000000006603030000303030433432303543394331000000000000000005028F09
          Cell 08 - Address: 00:1F:33:DC:CD:9A
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"best bitches"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000881b809c4
                    Extra: Last beacon: 744ms ago
                    IE: Unknown: 000C626573742062697463686573
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180202F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 09 - Address: 00:27:19:1D:44:BE
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"asd"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000035d1ff7d40
                    Extra: Last beacon: 756ms ago
                    IE: Unknown: 0003617364
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: 94:0C:6D:AC:52:74
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"KLIK_WIF"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000020b113cb24
                    Extra: Last beacon: 892ms ago
                    IE: Unknown: 00084B4C494B5F574946
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101850003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3404080800000000000000000000000000000000000000
                    IE: Unknown: 3D1604080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010006004000
          Cell 11 - Address: 00:30:4F:37:14:D9
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:off
                    ESSID:"HT-24-merita-internet.pl"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Mode:Master
                    Extra:tsf=00000001d0619b33
                    Extra: Last beacon: 1028ms ago
                    IE: Unknown: 001848542D32342D6D65726974612D696E7465726E65742E706C
                    IE: Unknown: 010582840B162C
                    IE: Unknown: 030102
                    IE: Unknown: DD0408002800
          Cell 12 - Address: 00:27:19:EF:79:1E
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"niewiem"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master

```

---

### Post by bkratz on 2011-02-13
I have problems waiting for sequels--all of the signals seem to have pretty low levels. Is the one you are trying to connect to showing up? There are two on channel 1 with just about the same strength.

---

### Post by Bucic on 2011-02-13
I'm not trying to connect to any specific network. I just wanted to make sure make wireless works before I go abroad with that junk of mine.

---

### Post by Bucic on 2011-02-14
I'll try to use one of the SSIDs to manually set up a wireless connection...


I tried SSID: M57_securex601217454
The NM tells me "connected". I launched Firefox and got a nice welcome screen "Securex HotSpot" with login and password prompt. EDIT: I even got connected after clicking "trial access". Some web pages loaded successfully.

OTher changes:
- NM - Wireless tab - the connection I've set up is visible; every connection I choose from the list (described in the next point) show up there too
- NM - under left-click - there's a list of available wireless networks; under "More networks" i have plenty of connections available.

Please note that after reboot I still have to run the following commands to make my wireless button light up:
```
sudo modprobe b43
dmesg | grep b43
iwconfig
```

---

### Post by chili555 on 2011-02-14
> I still have to run the following commands to make my wireless button light up:Let's try to fix that. Please do:```
sudo su
echo b43 >> /etc/modules
exit
```Now, when you reboot, does it light up?> I even got connected after clicking "trial access". Some web pages loaded successfully.


Everything else looks perfectly fine. I think you are good to go!!

---

### Post by Bucic on 2011-02-14
Not only my wireless correctly activates on boot, it automatically connects to the last used wireless network. Thank you!


One more thing.
Following the standard Ubuntu method of installing the b43 driver/firmware via the "Additional drivers" applet I stumbled upon the most outrageous quirk ever [http://ubuntuforums.org/showthread.php?p=10457627](http://ubuntuforums.org/showthread.php?p=10457627)  (see also my sig). I can safely assume that as a beginner I will have to reinstall Ubuntu rather soon so could you direct me to, in your opinion, the most painless procedures for installing b43 on a fresh system? I mean, some of the procedures require literally TENS of lines to be executed in terminal (sic!). Let's not lie to ourselves - a beginner will hit a wall every few lines.

---

### Post by chili555 on 2011-02-14
The drivers b43 and ssb are installed by default. It is the proprietary firmware that's not installed. Otherwise, the Ubuntu CD wouldn't be free and open source software.

Two approaches come to mind. Obviously, you have the needed firmware in your current install:> lsmod | grep bsudo ls /lib/firmware/b43
a0g0bsinitvals5.fw  a0g1bsinitvals13.fw  a0g1initvals5.fw     b0g0bsinitvals9.fw  lp0bsinitvals13.fw  lp0initvals14.fw      n0initvals11.fw  ucode14.fw
a0g0bsinitvals9.fw  a0g1bsinitvals5.fw     a0g1initvals9.fw     b0g0initvals13.fw   lp0bsinitvals14.fw  lp0initvals15.fw      pcm5.fw       ucode15.fw
a0g0initvals5.fw    a0g1bsinitvals9.fw     b0g0bsinitvals13.fw  b0g0initvals5.fw      lp0bsinitvals15.fw  n0absinitvals11.fw  ucode11.fw       ucode5.fw
a0g0initvals9.fw    a0g1initvals13.fw     b0g0bsinitvals5.fw   b0g0initvals9.fw      lp0initvals13.fw    n0bsinitvals11.fw   ucode13.fw       ucode9.fw
I'd copy it to a CD so that, after a reinstall, you can drag and drop it to your home directory and then copy it to your firmware file:```
sudo mkdir /lib/firmware/b43
sudo cp b43/* /lib/firmware/b43
```Another approach is, when you reinstall, be sure to set up a separate partition for /home. When you have to reinstall, leave the /home partition untouched. The firmware files will remain and can be copied over immediately.

Please post back if you need further clarification.

---

### Post by Bucic on 2011-02-14
So why the Additional drivers applet clearly states "Broadcom B43 wireless driver"? 

Just now I checked the applet and the driver is no longer marked as active. "A different version of this driver is in use". What a mess!!! This is why I'd like to a "from scratch" procedure as making a backup of anything on my current system I would feel like making backup of a mess, non the less.

---

### Post by chili555 on 2011-02-14
> So why the Additional drivers applet clearly states "Broadcom B43 wireless driver"?I suppose it was easier than explaining the whole proprietary vs. GPL thing and naming it, for example, "Install Proprietary Firmware needed to Activate the Broadcom B43 Wireless Driver." I guess you'd have to ask the Ubuntu developers, whoever and wherever they may be.

I am quite confident that, whatever the applet says, you are using b43 and ssb along with firmware downloaded and installed after installation. What does this tell us?```
lsmod | grep -e b43 -e ssb
```The approach above is just about foolproof (that's why even I could figure it out) and doesn't require an internet connection.

Hmmmmm, this would be a fun remastersys project...

[http://en.wikipedia.org/wiki/Remastersys](http://en.wikipedia.org/wiki/Remastersys)

---

### Post by Bucic on 2011-02-14
```
~$ lsmod | grep -e b43 -e ssb
b43                   168681  0 
ssb                    39320  1 b43
mac80211              231959  1 b43
cfg80211              144694  2 b43,mac80211
led_class               2633  2 b43,sdhci

```

Sorry for the delay. I will answear more quickly now. Which still doesn't mean you're obliged to reply immediatelly of course :)

---

### Post by chili555 on 2011-02-14
As I suspected (knew, really), b43 and ssb are driving your device. Copy the firmware to a CD and keep it in the safety deposit box along with your diamond watch, bearer bonds and genuine Jason Bourne fake Swiss passport. As long as there isn't a major redesign of the Broadcom drivers, you're all set.

---

### Post by Bucic on 2011-02-14
Just backed it up
```
#:/home/hg1# cd /lib/firmware/b43
#:/lib/firmware/b43# dir
a0g0bsinitvals5.fw   a0g1initvals5.fw	  lp0bsinitvals13.fw  n0initvals11.fw
a0g0bsinitvals9.fw   a0g1initvals9.fw	  lp0bsinitvals14.fw  pcm5.fw
a0g0initvals5.fw     b0g0bsinitvals13.fw  lp0bsinitvals15.fw  ucode11.fw
a0g0initvals9.fw     b0g0bsinitvals5.fw   lp0initvals13.fw    ucode13.fw
a0g1bsinitvals13.fw  b0g0bsinitvals9.fw   lp0initvals14.fw    ucode14.fw
a0g1bsinitvals5.fw   b0g0initvals13.fw	  lp0initvals15.fw    ucode15.fw
a0g1bsinitvals9.fw   b0g0initvals5.fw	  n0absinitvals11.fw  ucode5.fw
a0g1initvals13.fw    b0g0initvals9.fw	  n0bsinitvals11.fw   ucode9.fw
#:/lib/firmware/b43# mkdir /home/xxx
#:/lib/firmware/b43# cp *.* /home/xxx
#:/lib/firmware/b43# 
```

if needed I'll use e.g.
```
sudo mkdir /lib/firmware/b43
sudo cp /home/xxx/* /lib/firmware/b43
```


I only don't understand that "leave /home/ on separate partition" approach. I've been browsing that location and I see no system relevant files or folders there. There are only Desktop, Documents, Downloads and other insignificant dirs there.


EDIT:
Ah! [IMG]http://forums.eagle.ru/images/smilies/doh.gif[/IMG]
.gconf
.local
. ...

Baobab is a golden tool indeed!


But still during aaaaaaall the troubleshooting I went through for days and days I've never seen a single path that included /home/ in it.

---

### Post by chili555 on 2011-02-14
> I only don't understand that "leave /home/ on separate partition" approach. During a normal install, you are asked if you want to install along side another operating system, such as Windows, or wipe out the drive and install Ubuntu in place of whatever is there. Then, you are asked if you want automatic or guided manual partitioning. Most select automatic and end up with one big partition containing everything: var, lib, etc, dev, home and so forth, as well as a small swap partition. However, it is perfectly possible to create two partitions (plus swap); one for home and one for everything else, usually called /. Here is my scheme:```
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              14G  3.6G  9.8G  27% /
/dev/sda6              41G   21G   18G  54% /home
```There are some other trivial details.

Now, if I need to reinstall, the installation goes on / and /home remains untouched. All my very important mp3s, scanned pictures of my grandparents and jokes I received in email are preserved.

If you have already installed in one big partition, it's too late; however, you can burn your /home to DVD so you'll be able to copy the files over after a new installation. We all should be backing up regularly anyway; DVD is a quick and easy way to do so.

---

### Post by Bucic on 2011-02-14
OK, backing up and partitioning schemes is a subject to another thread I suppose. 

I'd like to **THANK YOU** very much for your assistance, chili! [IMG]http://forums.eagle.ru/images/smilies/drinks_cheers.gif[/IMG]

---

