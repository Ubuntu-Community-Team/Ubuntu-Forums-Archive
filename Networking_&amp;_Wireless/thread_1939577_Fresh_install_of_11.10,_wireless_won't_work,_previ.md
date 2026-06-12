---
title: "Fresh install of 11.10, wireless won't work, previous solutions don't either"
date: 2012-03-11
forum: Networking &amp; Wireless
---

### Post by Athena's Owl on 2012-03-11
My old laptop died a few days ago, and I got a loaner from a friend. this computer was destined for the recycler. When I turned it on it had windows XP and working wireless. I installed Ubuntu 11.10 by CD, formatting windows completely off the computer to be a pure linux machine, just like my old laptop.

But this computer is an old Acer Ferrari 4000 with ... you guessed it, a broadcom wireless controller. I know this is a common problem, I've read a dozen help threads trying to figure out my problem.

I know that you like to get information about the hardware in the computer, so here's the first bit:

chelsea@Data:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 (RS480/RS482/RX480/RX482) Chipset - Host bridge (rev 01)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
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
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 11)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller

Now I read a bunch of stuff and discovered that this version of linux doesn't have the Synaptic Package manager. I have that loaded on my machine and I tried the fix that was stickied at the top of the networking forum to load the package for b43 broadcom cards. When that didn't work, I tried another solution, which was to install all the packages. 

I thought that worked, because the computer suddenly wasn't at "firmware required" but it wouldn't display any wireless networks, and I couldn't figure out how to ask it to show me any. So I rebooted and then suddenly I don't have any indication that I have any sort of wireless technology in my computer at all!

I tried looking for another help guide but that's not helping because I can't get past the first step, which is make sure your wireless switch is on. I don't know how to be able to tell if it's on or not. the bluetooth button lights up blue, but the button right next to it never lights up.

I really don't know what to do. I feel incredibly stupid for having to ask for help. I can usually figure this stuff out by following someone else's support request, but that's not working for this problem and as much as I hate to do it I need to ask for personalized help.

I don't mind if I only get to do one trouble shooting step once per day. I have another computer running windows that works just fine, and I don't need this computer to travel away from home for the next week. Just tell me what command to run in terminal and I will report back dutifully.

Thank you!

---

### Post by kurt18947 on 2012-03-12
disclaimer: I am not broadcom knowledgeable.  Having said that, do you have a way to connect an ethernet cable?  If you're able to establish a wired connection, you can check 'additional drivers' to see if there's anything broadcom related available to activate.  My personal preference when faced with your situation is to use a USB device that is recognized 'out of the box'.  I have used an old but still-recognized adapter to download software/firmware/whatever for other faster network adapters then shut down and remove the older slower device.

---

### Post by Athena's Owl on 2012-03-12
Oh I'm sorry, I should have said that wired connection does work, that's how I was able to get the synaptic package installer (as well as the updates to 11.10)

When I checked "additional Drivers" the only thing it had is the internal modem (lol modem) and so I have that driver installed even though I doubt I will need it. it's just the wireless so far that's giving me fits.

---

### Post by chili555 on 2012-03-12
How about letting me see:```
lspci -nn | grep 0280
lsmod | grep -e wl -e b43
dmesg | grep -i firm
```Thanks.

---

### Post by praseodym on 2012-03-12
Download the firmware from here:

[http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz) 

and unpack it via

> sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 

---

### Post by Athena's Owl on 2012-03-12
chili555: here's what resulted of those two command strings. 

chelsea@Data:~$ lspci -nn | grep 0280
06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)


chelsea@Data:~$ lsmod | grep -e wl -e b43
chelsea@Data:~$ 

chelsea@Data:~$ dmesg | grep -i firm
chelsea@Data:~$ 

Yes the last two commands gave no response, not even an error message.

praseodym, I downloaded the firmware and used that command. Here's the result:

chelsea@Data:~$ sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/
[sudo] password for chelsea: 
tar: 2480236-Broadcom_Firmware.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now


so i'm guessing that error was about not having my file download in the correct directory?

---

### Post by kurt18947 on 2012-03-12
> **Athena's Owl said:**
> chili555: here's what resulted of those two command strings. 

chelsea@Data:~$ lspci -nn | grep 0280
06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)


chelsea@Data:~$ lsmod | grep -e wl -e b43
chelsea@Data:~$ 

chelsea@Data:~$ dmesg | grep -i firm
chelsea@Data:~$ 

Yes the last two commands gave no response, not even an error message.

praseodym, I downloaded the firmware and used that command. Here's the result:

chelsea@Data:~$ sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/
[sudo] password for chelsea: 
tar: 2480236-Broadcom_Firmware.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now


so i'm guessing that error was about not having my file download in the correct directory?

I've seen the "no such file or directory" message a time or two :oops:.  I enter the command "dir" and see what directories/files are shown.  For me, downloaded files default to "Downloads" so I need to 'cd Downloads' then 'dir' and the downloaded file is usually there.  Then execute the desired command.

---

### Post by Athena's Owl on 2012-03-12
Taking a wild guess; is the desired command

sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/

with /lib/firmware now /downloads?

---

### Post by chili555 on 2012-03-13
Please try this. When you download things, where do they go? To your folder called Downloads? Let's check:```
cd Downloads
ls
```Do you now see the tar.gz? If so, proceed:```
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```If things get downloaded to your desktop, then it's the same but with Desktop in place of Downloads.

Afterwards, reboot and tell us how it's working.

---

### Post by Athena's Owl on 2012-03-13
All right I looked around and found the file, and used that command:

chelsea@Data:~$ cd Downloads
chelsea@Data:~/Downloads$ ls
2480236-Broadcom_Firmware.tar.gz  google-chrome-stable_current_i386.deb
chelsea@Data:~/Downloads$ sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware
[sudo] password for chelsea: 
b43/
b43legacy/
b43/b0g0initvals5.fw
b43/b0g0bsinitvals5.fw
b43/a0g0initvals5.fw
b43/a0g1initvals5.fw
b43/a0g0bsinitvals5.fw
b43/a0g1bsinitvals5.fw
b43/b0g0initvals9.fw
b43/b0g0bsinitvals9.fw
b43/a0g0initvals9.fw
b43/a0g1initvals9.fw
b43/a0g0bsinitvals9.fw
b43/a0g1bsinitvals9.fw
b43/n0initvals11.fw
b43/n0bsinitvals11.fw
b43/n0absinitvals11.fw
b43/lp0initvals13.fw
b43/lp0bsinitvals13.fw
b43/b0g0initvals13.fw
b43/b0g0bsinitvals13.fw
b43/a0g1initvals13.fw
b43/a0g1bsinitvals13.fw
b43/lp0initvals14.fw
b43/lp0bsinitvals14.fw
b43/lp0initvals15.fw
b43/lp0bsinitvals15.fw
b43/ucode5.fw
b43/ucode9.fw
b43/ucode11.fw
b43/ucode13.fw
b43/ucode14.fw
b43/ucode15.fw
b43/pcm5.fw
b43legacy/a0g0bsinitvals5.fw
b43legacy/b0g0initvals2.fw
b43legacy/b0g0initvals5.fw
b43legacy/b0g0bsinitvals2.fw
b43legacy/a0g1initvals5.fw
b43legacy/a0g0initvals2.fw
b43legacy/a0g1bsinitvals5.fw
b43legacy/a0g0initvals5.fw
b43legacy/b0g0bsinitvals5.fw
b43legacy/a0g0bsinitvals2.fw
b43legacy/pcm5.fw
b43legacy/pcm4.fw
b43legacy/ucode11.fw
b43legacy/ucode5.fw
b43legacy/ucode4.fw
b43legacy/ucode2.fw
chelsea@Data:~/Downloads$ 


That looked terribly positive so I restarted with the ethernet out.

When I restarted, there was no indication that I had a wireless network. SO I guess that didn't work.

I remembered the first reply asked me for a couple of commands that returned no response. here they are again:

chelsea@Data:~$ lsmod |grep -e wl -e b43
chelsea@Data:~$ dmesg |grep -i firm
chelsea@Data:~$ 

Once again, no response to those two commands, not even an error message.

---

### Post by chili555 on 2012-03-13
Let's see if the firmware installation went well:```
ls /lib/firmware/b43
```You don't have to post the whole thing; it either got nothing or it got many. Just tell us which.

Now let's load up b43 and see what happens:```
sudo modprobe b43
iwconfig
```Now do you have a wireless interface wlan0? If not, let's check the message files and see why not:```
dmesg | grep -e b43 -e irmware
```If loading b43 manually does the trick, then do:```
sudo su
echo b43 >> /etc/modules
exit
```

---

### Post by Athena's Owl on 2012-03-13
the first command, ls /lib/firmware...

I got a bunch of entries.

then I went to sudo modprobe b43 and then iwconfig and nothing happened in the terminal, but suddenly my wireless card power light came on and it's showing me a list of available networks, so I tried connecting to my router on WPA2 security, but it wouldn't connect. I even unsecured my router and restarted, still won't connect.

Then I decided that I just got too eager and ran sudo modprobe b43, and got this result:

```
chelsea@Data:~$ sudo modprobe b43
[sudo] password for chelsea:
chelsea@Data:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
         Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
         Retry  long limit:7   RTS thr:off   Fragment thr:off
         Power Management:off
         
chelsea@Data:~$
```

So i went on to root and did echo b43 etc and restarted. no good. my wireless light comes on, the computer will attempt to connect to my (unsecured) network, but it won’t actually connect.

But I have a wireless card that’s aware of its existence now, so that is good.

---

### Post by chili555 on 2012-03-13
Is the ethernet cable **de**tached? It should be.

Let's see what Network Manager is doing and what your network looks like:```
sudo cat /var/log/syslog | grep etwork | tail -n15
dmesg | grep -e wlan -e b43
sudo iwlist wlan0 scan
```Thanks.

---

### Post by Athena's Owl on 2012-03-14
Yes it was with the ethernet cable detached. when I run all these commands I don't have the ethernet in, I just plug it in so I can copy-paste the results from the terminal. And speaking of that...

These commands produced a lot of stuff:

```
chelsea@Data:~$ sudo cat /var/log/syslog | grep etwork | tail -n15
[sudo] password for chelsea: 
Mar 13 22:16:50 Data NetworkManager[690]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Mar 13 22:16:50 Data NetworkManager[690]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 13 22:16:50 Data NetworkManager[690]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 13 22:16:50 Data NetworkManager[690]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 13 22:16:50 Data NetworkManager[690]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 13 22:16:50 Data NetworkManager[690]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 13 22:16:50 Data NetworkManager[690]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Mar 13 22:16:50 Data NetworkManager[690]: <info> Activation (wlan0/wireless): connection 'Xanadu' requires no security.  No secrets needed.
Mar 13 22:16:50 Data NetworkManager[690]: <info> Config: added 'ssid' value 'Xanadu'
Mar 13 22:16:50 Data NetworkManager[690]: <info> Config: added 'scan_ssid' value '1'
Mar 13 22:16:50 Data NetworkManager[690]: <info> Config: added 'key_mgmt' value 'NONE'
Mar 13 22:16:50 Data NetworkManager[690]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 13 22:16:50 Data NetworkManager[690]: <info> Config: set interface ap_scan to 1
Mar 13 22:16:50 Data NetworkManager[690]: <info> (wlan0): supplicant interface state: inactive -> scanning
Mar 13 22:16:51 Data NetworkManager[690]: <info> (wlan0): supplicant interface state: scanning -> authenticating
chelsea@Data:~$ 
```


```
chelsea@Data:~$ dmesg | grep -e wlan -e b43
[   22.445079] b43-pci-bridge 0000:06:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 9
[   22.532447] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   22.644609] Registered led device: b43-phy0::tx
[   22.644631] Registered led device: b43-phy0::rx
[   22.644652] Registered led device: b43-phy0::radio
[   25.229225] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   25.301409] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5849.056289] wlan0: authenticate with 00:23:69:8d:f2:38 (try 1)
[ 5849.057873] wlan0: 00:23:69:8d:f2:38 denied authentication (status 1)
[ 5912.328904] wlan0: authenticate with 00:23:69:8d:f2:38 (try 1)
[ 5912.330464] wlan0: 00:23:69:8d:f2:38 denied authentication (status 1)
[ 5975.328879] wlan0: authenticate with 00:23:69:8d:f2:38 (try 1)
[ 5975.330524] wlan0: 00:23:69:8d:f2:38 denied authentication (status 1)
chelsea@Data:~$ 
```

I assumed you only needed the information from my (temporarily!) unsecured router, and not the other dozen or so in the area:

```
chelsea@Data:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 02 - Address: 00:23:69:8D:F2:38
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-37 dBm  
                    Encryption key:off
                    ESSID:"Xanadu"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000005ef5c4ef1
                    Extra: Last beacon: 632ms ago
                    IE: Unknown: 000658616E616475
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7E0050F204104A0001101044000102103B00010310470010138140001DD211B29FFFC67E816B4BFB102100074C696E6B73797310230006526F7574657210240007575254353447321042000C43535630314A3345383135351054000800060050F204000110110011576972656C6573732D4720526F75746572100800020084
                    IE: Unknown: DD090010180200F4000000
```

---

### Post by chili555 on 2012-03-14
Man, that is wierd! This all looks great!>  <info> Activation (wlan0/wireless): connection 'Xanadu' requires no security.  No secrets needed.
Mar 13 22:16:50 Data NetworkManager[690]: <info> Config: added 'ssid' value 'Xanadu'
Mar 13 22:16:50 Data NetworkManager[690]: <info> Config: added 'scan_ssid' value '1'
Mar 13 22:16:50 Data NetworkManager[690]: <info> Config: added 'key_mgmt' value 'NONE'
Mar 13 22:16:50 Data NetworkManager[690]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 13 22:16:50 Data NetworkManager[690]: <info> Config: set interface ap_scan to 1
Mar 13 22:16:50 Data NetworkManager[690]: <info> (wlan0): supplicant interface state: inactive -> scanning
Mar 13 22:16:51 Data NetworkManager[690]: <info> (wlan0): supplicant interface state: scanning -> authenticatingHowever, over in dmesg, the news is completely different:> [ 5975.328879] wlan0: authenticate with 00:23:69:8d:f2:38 (try 1)
[ 5975.330524] wlan0: 00:23:69:8d:f2:38 [COLOR="Red"]denied authentication[/COLOR] (status 1)Please run:```
iwconfig
```Does it show as Mode: Managed? Next, click the Network Manager icon and select Edit Connections. Are there any settings that you entered trying to get connected? If so, delete them all. If the hardware, driver, NM and wpa_supplicant are doing the job, no human intervention is needed. I am wondering if you set up 'Create New Wireless Network...' which is NM-speak for 'create new ad-hoc computer-to-computer network' which is *NOT* what you want.

You might also try:```
sudo modprobe -rv b43
sudo modprobe b43 nohwcrypt=1
```Any improvement? If so, we can write one quick file and make it persistent.

---

### Post by Athena's Owl on 2012-03-14
I was in Mode: managed, and I deleted all my wireless connections and tried to connect again. 

No good.

the first command kicked up a few lines of response, but the next one, b43 nowcrypt=1 didn't generate any response, and my wireless is still not connecting. (I didn't plug my laptop in my internet because I'm doing something on the desktop that's dependent on my connection staying connected, but I can quote and paste exactly what the commands said in a bit over an hour.

---

### Post by Athena's Owl on 2012-03-15
I'm sorry it took me so long to get back to this, I wound up getting distracted by all sorts of things but here's the results of the commands:

```
chelsea@Data:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

At this point I did remove all the wireless networks (I only had one, the one to Xanadu) and attempted a reconnect. No good.

Here's the results of the superuser commands you suggested:
    
```
chelsea@Data:~$ sudo modprobe -rv b43
[sudo] password for chelsea: 
rmmod /lib/modules/3.0.0-16-generic/kernel/drivers/net/wireless/b43/b43.ko
rmmod /lib/modules/3.0.0-16-generic/kernel/drivers/ssb/ssb.ko
rmmod /lib/modules/3.0.0-16-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.0.0-16-generic/kernel/net/wireless/cfg80211.ko
chelsea@Data:~$ sudo modprobe b43 nohwcrypt=1
chelsea@Data:~$ 
```

the second command didn't do anything, and I still can't connect wirelessly. Is there anything else I can try, or have we exhausted the possibilities? do I need to purchase a different router? Replacing the network card isn't something I can do, this is just supposed to be a holdover until the back to school sales in August.

---

### Post by chili555 on 2012-03-16
> Is there anything else I can try, or have we exhausted the possibilities?One last thing. You might try the backported modules; there is a newer b43 and ssb in there:```
sudo apt-get install linux-backports-modules-cw-3.1-oneiric-generic
```Reboot and let's see if things look better:```
dmesg | grep -e wlan -e b43
```> do I need to purchase a different router?Is yours older? With most store's liberal return policies, it seems worthwhile to buy and try to see if it's actually the router. 

Even if you *could* connect to your current router without WPA2, I wouldn't feel happy or secure.

---

