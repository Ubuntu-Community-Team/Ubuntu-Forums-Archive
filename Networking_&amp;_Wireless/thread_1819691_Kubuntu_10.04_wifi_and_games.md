---
title: "Kubuntu 10.04 wifi and games"
date: 2011-08-06
forum: Networking &amp; Wireless
---

### Post by LT72884 on 2011-08-06
Here is a two in one question for yall. First, kubuntu site says that one of the features of kubuntu is all the games. I do not have a games folder listed under apps on my laptop. Did 10.04lts not have games?

Ok, second question. I set up a new network connection named home. Gafve it the ssid and bssid of the linksys router i am using. I tried to scan for available networks using the scan button in the GUI but it didnt find my network. Either because my laptop was on the floor and my router is behind a desktop PC(i know not the best place. and after several reboots, still no signal.. However, the next morning i had the lap top on the table showing it off to my wife how cool the 3d effects are, gotta impress her somehow, i noticed my wifi signal was 88% and it detected my homes wifi. AWESOME right, well almost. i still cant connect to it.

I ran the lshw -C network command and it brings up the properties of the card BUT does not say if it disabled, inabled, connected compiled or anyother indication. I then noticed the maker is atheros. I assume i have to build the wifi somehow? if so, how does one do this and my other question is why does linux have to be so complicted? i mean its 2011, windows 98 was easier than this. not bashing, just venting. I had to install libreoffice last night and i dont get why there is no way to have an installer install it for me like mac or windows does, you know, double click select path and it installs there. SO why did i have to run the dpkg command that is complicated and have to be in the directory? If ubuntu is trying to be user friendly, that needs to be changed in my opinion. I tired to search for it under the kpackage software installer but it found 0 results. maybe i had the wrong reposits selected. I know it sounds like im complaining but im not, im just saying this because i let some average pc users try out ubuntu and they did not like it because they had no idea what a terminal session was and they wanted to install some extra software and it bothered them that they had to basically become bill gates, in there words, to operate the pc. anyway, that is another story my main concern is the games and wifi for the wife. thanks

---

### Post by wildmanne39 on 2011-08-06
Hi, I will try to help you get wireless working, I will let someone else address your other concerns.

Please run these commands in a terminal:
```
sudo lshw -C network
```
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod | grep ath
```
And post the results here.
Thank you

---

### Post by LT72884 on 2011-08-06
> **wildmanne39 said:**
> Hi, I will try to help you get wireless working, I will let someone else address your other concerns.

Please run these commands in a terminal:
```
sudo lshw -C network
```
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod | grep ath
```
And post the results here.
Thank you

thank you for you reply. here is the output from terminal:

> matt@LT72884:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:c0:a8:d4:ec:d5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:c0400000-c040ffff
matt@LT72884:~$ lspci -nn | grep 0280
matt@LT72884:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
matt@LT72884:~$ rfkill list all
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
matt@LT72884:~$ lsmod | grep ath
ath5k                 121632  0 
mac80211              205402  1 ath5k
ath                     7611  1 ath5k
cfg80211              126144  3 ath5k,mac80211,ath
led_class               2864  1 ath5k
matt@LT72884:~$ 

I also searched to see if there were any proprietery drivers for it but the hardware driver utility only found the ones for my nvidea card

---

### Post by wildmanne39 on 2011-08-06
Hi, run these commands one at a time
```
sudo rmmod -f ath5k
sudo rfkill unblock all
sudo modprobe ath5k

```
Then unplug your wired connection ans see if you can connect with your wireless.
Thank you

---

### Post by LT72884 on 2011-08-06
> **wildmanne39 said:**
> Hi, run these commands one at a time
```
sudo rmmod -f ath5k
sudo rfkill unblock all
sudo modprobe ath5k

```
Then unplug your wired connection ans see if you can connect with your wireless.
Thank you

 i will as soon as i can, about 5 minutes or so. Just in the mean time though, what does each command mean and what actions are being performed? Why did you pick these commands and not a set of others? thank you very much my friend

---

### Post by LT72884 on 2011-08-06
ok it still does not work. i click the icon in the sys tray that states that a network is unavailable. It shows my home network with a 91% signal and i watch it go from 88% to 92% so i know that it is reading it in real time. I single click on the home network, nothing. i try double clicking and nothing. i try tripple clicking and nothing. I select connect to another network and i can see my nieghbors wpa network. mine is not listed in that window for some reason. here are some screens:Thanx first image shows network taskbar

---

### Post by wildmanne39 on 2011-08-06
Hi, the first command removed the driver the second unblocked your wireless and the third one adds the driver back. 

The reason I choose those commands because they work a lot of time with this card, and it is a quick way to get your card working.

Please post the results of these commands, I am looking for the problem using these commands.
```
dmesg | grep wlan0
```
```
sudo iwlist scan
```
```
nm-tool
```
```
dmesg | grep ath5k
```
```
modinfo ath5k
```
Thank you

---

### Post by LT72884 on 2011-08-06
> **wildmanne39 said:**
> Hi, the first command removed the driver the second unblocked your wireless and the third one adds the driver back. 

The reason I choose those commands because they work a lot of time with this card, and it is a quick way to get your card working.

Please post the results of these commands, I am looking for the problem using these commands.
```
dmesg | grep wlan0
```
```
sudo iwlist scan
```
```
nm-tool
```
```
dmesg | grep ath5k
```
```
modinfo ath5k
```
Thank you

ok cool thanx for the explanation. I will run those when i get home from work. My shift starts in a few minutes so i will be unavailable to run said commands for about 6 hours. thanx for all the help. Guess its time to start a journal. haha

---

### Post by LT72884 on 2011-08-07
ok here is another wifi question. Once i get this to work, how do i connect to hotspots? i mean, when i created the network connection on my laptop for my home network, it asked for the mac of my wap. Thats all fine and what not because i can access me wap BUT when i go to a hotspot or any other open wifi, how do i connect because i dont have access to some randoms waps mac. haha. 

thanks. I will be trying out your other commands tomorrow. i am at work so i kinda cant. haha

thanks

---

### Post by wildmanne39 on 2011-08-07
Hi, network manager should automatically detect and connect to unsecured hot spots.
Thank you

---

### Post by LT72884 on 2011-08-07
> **wildmanne39 said:**
> Hi, network manager should automatically detect and connect to unsecured hot spots.
Thank you

so with that in mind, i really didnt have to add the mac of my wap to the settings of the new connection i made? Should i start from the very beginning of this task and delete the new connection i made and run those commands, reboot the pc and then see if it connects?

let me know where i should go. Im wondering if creating that network connection messed up something.

i hope you saw the pictures i attached to a previous post?

thanks

---

### Post by wildmanne39 on 2011-08-07
Hi, post the information from the commands I gave you in post #7. It is a process and I need to see the results of those commands so I can determine the next step, that way I am not just guessing.
Thank you

---

### Post by LT72884 on 2011-08-07
> **wildmanne39 said:**
> Hi, post the information from the commands I gave you in post #7. It is a process and I need to see the results of those commands so I can determine the next step, that way I am not just guessing.
Thank you

ok cool. sounds good to me. im at work. thanx for being very patient with me and this issue.

---

### Post by wildmanne39 on 2011-08-07
Hi, your welcome! take all the time you need.

---

