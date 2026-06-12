---
title: "ASUS N13 on Inspiron 1150"
date: 2011-01-04
forum: Networking &amp; Wireless
---

### Post by mysteryd on 2011-01-04
Running Ubuntu 10.04
Unable to get Ubuntu to find the ASUS USB Wireless to connect for network. I got the Broadcom to work using ndiswrapper but the range on it is unbearable meaning I have to be in the same room as the router. Hoping this has a much better range.

Any other information you need I will be happy to provide.

lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0b05:1784 ASUSTek Computer, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

ifconfig

eth0      Link encap:Ethernet  HWaddr 00:11:43:62:73:3a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:7 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:320 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24464 (24.4 KB)  TX bytes:24464 (24.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0b:7d:0f:cf:5b  
          inet addr:192.168.2.103  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:7dff:fe0f:cf5b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1948 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1958 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1513489 (1.5 MB)  TX bytes:345016 (345.0 KB)
          Interrupt:11 Memory:fcffc000-fcffe000 

iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"AndroidTether"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 90:21:55:08:DE:43   
          Bit Rate=18 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:92/100  Signal level:-37 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

---

### Post by chili555 on 2011-01-04
> I got the Broadcom to work using ndiswrapperHow is it's range with the native driver and firmware?

---

### Post by mysteryd on 2011-01-04
> **chili555 said:**
> How is it's range with the native driver and firmware?

If this makes any sense I installed wicd and the range actually reached my living room... it is still sketchy but it is working.

I was unable to get the native driver installed if memory recalls. I installed the bcmwl5.inf through ndiswrapper.

---

### Post by chili555 on 2011-01-04
I asked because ndiswrapper is a compromise in order to use the Windows driver. I don't hear many complaints about range with the native driver. If you'd like to try it again, I'll be happy to help.

---

### Post by mysteryd on 2011-01-04
> **chili555 said:**
> I asked because ndiswrapper is a compromise in order to use the Windows driver. I don't hear many complaints about range with the native driver. If you'd like to try it again, I'll be happy to help.

I would love to try. As long as I have the ndiswrapper option in reserve to get back online that would be awesome. 

Going to be around for a while and subscribed to this thread so my replies will be rather fast.

---

### Post by chili555 on 2011-01-04
Please open a terminal and post:```
lspci -nn | grep -i 14e4
```We can unload ndiswrapper, grab the firmware and temporarily load the native driver. If it works, as I suspect it will, we can make it permanent but reversible.

---

### Post by mysteryd on 2011-01-04
```
02:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

```

---

### Post by chili555 on 2011-01-04
Your device uses the driver b43 and its trusted companion ssb. ssb may be interfering with ndiswrapper because it's also required by your ethernet driver. Let's do some diagnostics. Please do:```
sudo ifconfig wlan0 down
sudo rmmod -f ndiswrapper
sudo modprobe b43
dmesg | grep b43
```dmesg will tell us what firmware is needed and missing. When you are done, you can simply reload ndiswrapper:```
sudo modprobe ndiswrapper
```

---

### Post by mysteryd on 2011-01-04
dmesg | grep b43
[    1.908188] b43-pci-bridge 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   21.644241] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   21.883700] Registered led device: b43-phy0::tx
[   21.883751] Registered led device: b43-phy0::rx
[   21.883798] Registered led device: b43-phy0::radio
[   27.021593] b43-pci-bridge 0000:02:02.0: PCI INT A disabled

---

### Post by chili555 on 2011-01-04
> b43-pci-bridge 0000:02:02.0: PCI INT A [COLOR="Red"]disabled[/COLOR]The plot thickens! Let's have a peek at:```
rfkill list all
```I notice that b43 loads on boot and would, if it were not somehow disabled, interfere with ndiswrapper.

---

### Post by mysteryd on 2011-01-04
```
:~$ rfkill list all
:~$
```

---

### Post by chili555 on 2011-01-04
Please try this:```
sudo rmmod -f dell-laptop
dmesg | grep b43
```We are looking for messages after the ones you already posted; that is, after [ 27.021593].

---

### Post by mysteryd on 2011-01-04
```
:~$ sudo rmmod -f dell-laptop
ERROR: Removing 'dell_laptop': No such file or directory
:~$ dmesg | grep b43
[    1.908188] b43-pci-bridge 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   21.644241] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   21.883700] Registered led device: b43-phy0::tx
[   21.883751] Registered led device: b43-phy0::rx
[   21.883798] Registered led device: b43-phy0::radio
[   27.021593] b43-pci-bridge 0000:02:02.0: PCI INT A disabled
```

am I doing something incorrect. I am not getting anything after the 27.021593

---

### Post by chili555 on 2011-01-04
When you installed ndiswrapper, did you blacklist b43?```
cat /etc/modprobe.d/blacklist | grep b43
cat /etc/modprobe.d/blacklist.conf | grep b43
```Is there a wireless switch on your Inspiron? Are you sure the wireless is switched on?

---

### Post by mysteryd on 2011-01-04
It was months ago... I might have.

```
:~$ cat /etc/modprobe.d/blacklist | grep b43
:~$ cat /etc/modprobe.d/blacklist.conf | grep b43
# replaced by b43 and ssb.
```

No switch.

---

### Post by chili555 on 2011-01-04
Please do:```
sudo ifconfig wlan0 down
sudo rmmod -f ndiswrapper
dmesg > myst.txt
lsmod >> myst.txt
sudo lshw -C network >> myst.txt
zip myst.zip myst.txt
```In your user directory, you will find a zip file called myst.zip. Please attach it to your reply.

I'm on a short schedule; we have to crack this case soon!

---

### Post by mysteryd on 2011-01-04
Attached.

---

### Post by chili555 on 2011-01-04
> ndiswrapper (iw_set_auth:1602): invalid cmd 12A well known bug that I thought was fixed.> [ 6778.040550] ndiswrapper: device wlan0 removed
[ 6778.040588] ndiswrapper 0000:02:02.0: PCI INT A disabled
[ 6778.043189] usbcore: deregistering interface driver ndiswrapper
[ 6778.237326] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)As you can see, it stayed unloaded for about 1/4 second. Not much use in debugging.> Module                  Size  Used by
ndiswrapper           184677  0 
b43                   163524  0 
mac80211              205402  1 b43
cfg80211              126528  2 b43,mac80211
led_class               2864  1 b43So ndiswrapper and b43 are loading; that can't be good. As I implied earlier, it's tough to knock out b43 and ssb without knocking out your ethernet. Let's try a few reversible tricks. I assume if you get the wireless sorted that the ethernet is unimportant. Please do:```
sudo su
echo "blacklist b43" >> /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and give me your report. Is ndiswrapper working better now?

---

### Post by bkratz on 2011-01-04
@Dr Chili

I think you will have to have the op also blacklist b44 temporarily, I believe b44 will load ssb anyway, but I could be wrong--sometimes!

---

### Post by mysteryd on 2011-01-04
range is about the same...

---

### Post by chili555 on 2011-01-04
Please see bkratz' comments above. Please run and post:```
lsmod | grep -e b4 -e ssb
ndiswrapper -l
ls /lib/firmware/b43
```Thanks.

---

### Post by mysteryd on 2011-01-04
```
lsmod | grep -e b4 -e ss
b44                    25574  0 
ssb                    38902  1 b44
mii                     4381  1 b44
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_oss            26722  0 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54180  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
```

```
ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)
```

```
ls /lib/firmware/b43
ls: cannot access /lib/firmware/b43: No such file or directory
```

---

### Post by chili555 on 2011-01-04
Please do:```
sudo su
echo "blacklist b44" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and bkratz will take over or I'll check back later. G'nite.

---

### Post by bkratz on 2011-01-04
Actually, it is sleepy time for me too, these old bones can't stay up as long as they used to!

---

### Post by mysteryd on 2011-01-05
Did the blacklist b44 and rebooting now. Since I am using my EVO to tether the range probably wont be noticeable until I get home around 5:30pm est.

Can you guys give me a run through on what we are doing... I can cut and paste commands all day long but if I dont know why or what they are for I probably wont learn much =)

---

### Post by bkratz on 2011-01-05
> **mysteryd said:**
> Did the blacklist b44 and rebooting now. Since I am using my EVO to tether the range probably wont be noticeable until I get home around 5:30pm est.

Can you guys give me a run through on what we are doing... I can cut and paste commands all day long but if I dont know why or what they are for I probably wont learn much =)

Well in the first half of the thread, Dr. Chili was trying to determine the best approach keeping in mind your needs.  He tried a couple of "quick fixes" and did not have much luck, so returned to ndiswrapper and right now is blacklisting some modules to prevent them from loading and interfering with the desired software. Right now we are attempting to get the wireless working at the temporary expense of the wired connection.  I was one of the ones caught by the " ndiswrapper (iw_set_auth:1602): invalid cmd 12" nightmare and ended up building my own ndiswrapper version, but that was over a year ago. I thought that was fixed already too in the latest versions, but I also thought that 1.56 was the latest (yours says 1.55) I will try to "dig-out" the old thread for your informational purposes.

---

### Post by chili555 on 2011-01-05
Hey! We're both back! The native driver for the wireless card is a combination: b43 and ssb. The driver for your ethernet card is b44 and ssb. The system was loading both ndiswrapper and b43 and ssb and they conflicted. It was not enough to blacklist, or block out b43 and ssb, because your ethernet card loaded b44 and dragged ssb along with it and ssb commenced to conflict with ndiswrapper anyway! We are temporarily blacklisting b43, ssb and b44. We hope that ndiswrapper will work correctly and you'll be another satisfied client. However, your wired ethernet will not work unless you load b44 and ssb.

You do not currently have the needed firmware for your wireless card. Of course, we could install it and go back to b43, b44 and ssb and remove ndiswrapper entirely. 

I suspect your exact problem is pretty widespread.

Do you have the Windows .inf file in a safe spot in your user directory in case we want to experiment?

---

### Post by bkratz on 2011-01-05
I guess it was actually 1 1/2[COLOR="Red"][/COLOR] years ago, another age problem! Just for reference when bored, no need to study right now.

[http://ubuntuforums.org/showthread.php?t=1343847&highlight=(iw_set_auth:1602](http://ubuntuforums.org/showthread.php?t=1343847&highlight=(iw_set_auth:1602))

---

### Post by mysteryd on 2011-01-05
> **bkratz said:**
> Well in the first half of the thread, Dr. Chili was trying to determine the best approach keeping in mind your needs.  He tried a couple of "quick fixes" and did not have much luck, so returned to ndiswrapper and right now is blacklisting some modules to prevent them from loading and interfering with the desired software. Right now we are attempting to get the wireless working at the temporary expense of the wired connection.  I was one of the ones caught by the " ndiswrapper (iw_set_auth:1602): invalid cmd 12" nightmare and ended up building my own ndiswrapper version, but that was over a year ago. I thought that was fixed already too in the latest versions, but I also thought that 1.56 was the latest (yours says 1.55) I will try to "dig-out" the old thread for your informational purposes.

Excellent... thank you. So I guess using the native driver wont work (which I believe was Chilli's thought to improve the range on the card). I seriously sit in a room next to the router and catch issues with 50% or below connection. Now before Wicd I couldnt get signal in the living room but now am able to log in as long as I stay in a certain part of the living room.

I figured the ASUS would be a solve to the problem by getting more speed and a newer card would have more range, which was the original idea.

I really appreciate the help guys. I enjoy playing with this laptop and this is the longest I havent messed up linux (going on a year and some change) on a machine yet and am getting things closer to the way I like it, and playing with newer things in the meantime.

---

### Post by chili555 on 2011-01-05
> So I guess using the native driver wont workWhy? I don't believe anyone said that or thinks that. After you blacklisted all three and rebooted, does ndiswrapper work better? Are you ready to get the native driver going instead?

---

### Post by mysteryd on 2011-01-05
> **chili555 said:**
> Why? I don't believe anyone said that or thinks that. After you blacklisted all three and rebooted, does ndiswrapper work better? Are you ready to get the native driver going instead?

Haha... sorry Chili, assumptions kill me sometimes.

I am definitely ready. I am at work so it will be touch and go so my replies and updates will be slower but ready when you are. Downloaded the ucode5.fw.zip... =)

---

### Post by chili555 on 2011-01-05
Sorry for the delay; had to step away for an appointment. Our first step is to remove ndiswrapper from effectiveness. Before you proceed, be sure you have the Windows .inf and .sys files safely in your home directory. That way, we can reactivate ndiswrapper if things go wrong. Please do:```
sudo ndiswrapper -e bcmwl5
```Now, let's remove the blacklist lines so that b43, ssb and b44 load:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Remove the lines:```
blacklist b43
blacklist ssb
blacklist b44
```Proofread, save and close gedit. Now, we'll get the firmware file in the right spot. May I assume you downloaded the ucode file to your desktop? Right-click it and select 'Extract Here.' It will extract a file called ucode5.fw. We'll but in in the correct place so the driver can find it.```
sudo mkdir /lib/firmware/b43
```Now, we'll move the file:```
sudo cp Desktop/ucode5.fw /lib/firmware/b43
```Now, let's be sure ndiswrapper is not being explicitly called:```
sudo gedit /etc/modules
```If ndiswrapper is listed, remove it; save and close gedit. Now reboot and run:```
dmesg | grep b43
```Is your wireless working or are there errors or warnings to report?

---

### Post by mysteryd on 2011-01-05
There are errors... wireless card seems to be inactive and is not locating the wireless tether I had set up from my phone.
 
Currently using work internet to post this reply.
 
```
 
b43-phy0 ERROR: Firmware file "b43/b0g0initvals5.fw" not found
b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instuctions on this website.

```
 
I get that about 3 times in the dmesg | grep b43 > dmesg.txt (thanks for that... learned how to create text file error logs yesterday)

---

### Post by chili555 on 2011-01-05
> There are errors... wireless card seems to be inactiveWe need to know what they are. Can you copy and paste from the terminal to a text document and transfer the text on a USB key to another computer so you can post it?

---

### Post by mysteryd on 2011-01-05
> **chili555 said:**
> We need to know what they are. Can you copy and paste from the terminal to a text document and transfer the text on a USB key to another computer so you can post it?
 
Figured you would want to see the errors. Attempting to secure a thumb drive to bring over the text file. Put the errors on the post above

---

### Post by mysteryd on 2011-01-05
Office full of engineers and non more technilogically advanced than a calculator. Will have to wait till this afternoon when I get home I guess.

---

### Post by chili555 on 2011-01-05
Work? Work is a four letter word. I'll look forward to a kwik fix tonight.

---

### Post by mysteryd on 2011-01-05
```
[    1.928606] b43-pci-bridge 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   21.862095] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   22.026437] Registered led device: b43-phy0::tx
[   22.026484] Registered led device: b43-phy0::rx
[   22.026546] Registered led device: b43-phy0::radio
[   26.828128] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   27.292961] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   27.306135] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   27.318841] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   27.339287] b43-phy0 ERROR: Firmware file "b43/b0g0initvals5.fw" not found
[   27.339296] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   27.339301] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   27.607662] b43-pci-bridge 0000:02:02.0: PCI INT A disabled
[   28.098430] b43-pci-bridge 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   28.568878] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   28.716513] Registered led device: b43-phy0::tx
[   28.716556] Registered led device: b43-phy0::rx
[   28.716599] Registered led device: b43-phy0::radio
[   35.532146] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   35.545428] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   35.575125] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   35.594732] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   35.620596] b43-phy0 ERROR: Firmware file "b43/b0g0initvals5.fw" not found
[   35.620605] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   35.620611] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   38.083963] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   38.089799] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   38.101507] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   38.112782] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   38.123772] b43-phy0 ERROR: Firmware file "b43/b0g0initvals5.fw" not found
[   38.123781] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   38.123786] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   43.093069] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   43.098887] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   43.110129] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   43.121341] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   43.132621] b43-phy0 ERROR: Firmware file "b43/b0g0initvals5.fw" not found
[   43.132631] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   43.132636] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   48.079373] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   48.085325] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   48.096520] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   48.107696] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   48.118853] b43-phy0 ERROR: Firmware file "b43/b0g0initvals5.fw" not found
[   48.118863] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   48.118867] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   87.939985] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   87.945548] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   87.956474] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   87.967340] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   87.978419] b43-phy0 ERROR: Firmware file "b43/b0g0initvals5.fw" not found
[   87.978428] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   87.978432] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   91.943349] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   91.949376] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   91.960548] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   91.971489] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   91.982417] b43-phy0 ERROR: Firmware file "b43/b0g0initvals5.fw" not found
[   91.982427] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   91.982432] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  105.627252] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[  105.636637] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[  105.649961] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[  105.665577] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[  105.681828] b43-phy0 ERROR: Firmware file "b43/b0g0initvals5.fw" not found
[  105.681859] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[  105.681864] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  252.084151] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[  252.089257] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[  252.101405] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[  252.109958] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[  252.123571] b43-phy0 ERROR: Firmware file "b43/b0g0initvals5.fw" not found
[  252.123581] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[  252.123586] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  314.983751] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[  314.996948] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[  315.011844] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[  315.030026] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[  315.050348] b43-phy0 ERROR: Firmware file "b43/b0g0initvals5.fw" not found
[  315.050358] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[  315.050363] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  455.125844] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[  455.134764] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[  455.146391] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[  455.158890] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[  455.180717] b43-phy0 ERROR: Firmware file "b43/b0g0initvals5.fw" not found
[  455.180727] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[  455.180732] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  660.099279] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[  660.105253] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[  660.117068] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[  660.131239] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[  660.142153] b43-phy0 ERROR: Firmware file "b43/b0g0initvals5.fw" not found
[  660.142163] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[  660.142167] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
```

---

### Post by chili555 on 2011-01-05
Do you have an ethernet connection at home? Do you have b43-fwcutter installed? Can you do this?```
export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo ../../b43-fwcutter-013/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta_mimo.o

```I was hoping that we could cheat up the process with just ucode5.fw, but evidently not.

---

### Post by mysteryd on 2011-01-05
edited for incorrectness.

Its working. Must have been a typo.

---

### Post by bkratz on 2011-01-05
Ignore!------Is your wired connection currently running?


Reason---typed too slowly!

---

### Post by mysteryd on 2011-01-05
I installed the b43-fwcutter which seems to have activated my wireless.

---

### Post by chili555 on 2011-01-05
> **mysteryd said:**
> I installed the b43-fwcutter which seems to have activated my wireless.Meaning what? All fixed? All happy? Or...?

---

### Post by mysteryd on 2011-01-05
> **bkratz said:**
> Ignore!------Is your wired connection currently running?


Reason---typed too slowly!

Yeah... plugged it in and it connected through wicd.

---

### Post by chili555 on 2011-01-05
> **mysteryd said:**
> Yeah... plugged it in and it connected through wicd.Outstanding! How does the range compare with the old ndiswrapper?

---

### Post by mysteryd on 2011-01-05
> **chili555 said:**
> Outstanding! How does the range compare with the old ndiswrapper?

Not half bad... about 20% increase as far as signal strength. Would consider that a success

How do you change the prefix to SOLVED?

---

### Post by bkratz on 2011-01-05
Sure am glad to hear that you got it working!  Oh and just go to the thread tools above to mark as solved (only you can do it!)

---

### Post by mysteryd on 2011-01-05
> **bkratz said:**
> Sure am glad to hear that you got it working!  Oh and just go to the thread tools above to mark as solved (only you can do it!)

Might have spoke to soon.

was surfing the net and ubuntu locked up and wanted to go to low graphics mode so I rebooted it.

When it came back up I have no eth0 or wlan0. I cant connect to the internet at all. Driver is still there but the card seems to be non responding.

---

### Post by chili555 on 2011-01-05
Please let us see:```
dmesg | grep -e b4 -e ndis
```Thanks.

---

### Post by mysteryd on 2011-01-05
```
[    0.447795] usb usb4: configuration #1 chosen from 1 choice
[    1.913951] b43-pci-bridge 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    2.025287] b44 0000:02:01.0: PCI INT A -> Link[LNKB] -> GSI 7 (level, low) -> IRQ 7
[    2.084963] b44.c:v2.0
[   23.006770] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   23.307466] Registered led device: b43-phy0::tx
[   23.307512] Registered led device: b43-phy0::rx
[   23.307559] Registered led device: b43-phy0::radio
[   27.936131] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   28.316363] b44 0000:02:01.0: PCI INT A disabled
[   28.410731] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   28.441746] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   28.462181] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   28.690724] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   29.612742] Modules linked in: fbcon tileblit font bitblit softcursor vga16fb vgastate snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi arc4 snd_seq_midi_event snd_seq pcmcia snd_timer joydev b43(-) snd_seq_device i915 yenta_socket mac80211 rsrc_nonstatic dell_wmi drm_kms_helper cfg80211 pcmcia_core dcdbas snd led_class drm intel_agp psmouse serio_raw soundcore snd_page_alloc shpchp i2c_algo_bit agpgart video output lp parport ssb [last unloaded: mii]
[   29.612935]  [<f8280468>] ? b43_led_brightness_set+0x28/0x30 [b43]
[   29.612975]  [<f8202104>] ? ieee80211_unregister_hw+0xb4/0xe0 [mac80211]
[   29.612995]  [<f8265e08>] ? b43_remove+0xa8/0xb0 [b43]
[   29.613074]  [<f82806da>] ? b43_exit+0x12/0x2c [b43]
[   29.613103] Code: b8 9d a4 12 c0 e9 59 ff ff ff 90 b9 a0 a4 12 c0 b8 a3 a4 12 c0 e9 49 ff ff ff 90 90 90 90 90 90 90 90 90 55 ba 00 01 00 00 89 e5 <3e> 66 0f c1 10 38 f2 74 06 f3 90 8a 10 eb f6 5d c3 8d b4 26 00 
[   29.663142] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
```

---

### Post by chili555 on 2011-01-05
It appears that ndiswrapper is loading as well as the native driver. Please do:```
sudo su
rm /etc/modprobe.d/ndis*
echo "blacklist ndiswrapper" > /etc/modprobe.d/blacklist.conf
exit
```Reboot and let us have your report.

---

### Post by mysteryd on 2011-01-05
> **chili555 said:**
> It appears that ndiswrapper is loading as well as the native driver. Please do:```
sudo su
rm /etc/modprobe.d/ndis*
echo "blacklist ndiswrapper" > /etc/modprobe.d/blacklist.conf
exit
```Reboot and let us have your report.

Saved the report to text so i can upload tomorrow.

---

### Post by mysteryd on 2011-01-06
```
 
[    0.415768] usb usb4: configuration #1 chosen from 1 choice
[    1.882246] b43-pci-bridge 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    2.003079] b44 0000:02:01.0: PCI INT A -> Link[LNKB] -> GSI 7 (level, low) -> IRQ 7
[    2.060373] b44.c:v2.0
[   22.825063] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   23.057483] Registered led device: b43-phy0::tx
[   23.057527] Registered led device: b43-phy0::rx
[   23.057570] Registered led device: b43-phy0::radio
[   27.768134] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   28.148325] b44 0000:02:01.0: PCI INT A disabled
[   28.240165] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   28.271027] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   28.291519] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   28.515956] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   29.436751] Modules linked in: fbcon tileblit font bitblit softcursor vga16fb vgastate snd_intel8x0m snd_intel8x0 snd_pcm_oss snd_ac97_codec ac97_bus snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi arc4 snd_rawmidi snd_seq_midi_event snd_seq pcmcia b43(-) snd_timer joydev snd_seq_device i915 mac80211 snd dell_wmi drm_kms_helper cfg80211 dcdbas yenta_socket rsrc_nonstatic pcspkr drm led_class pcmcia_core psmouse serio_raw soundcore snd_page_alloc intel_agp shpchp i2c_algo_bit agpgart evbug video output lp parport ssb [last unloaded: mii]
[   29.436947]  [<f8280468>] ? b43_led_brightness_set+0x28/0x30 [b43]
[   29.436986]  [<f8325104>] ? ieee80211_unregister_hw+0xb4/0xe0 [mac80211]
[   29.437003]  [<f8265e08>] ? b43_remove+0xa8/0xb0 [b43]
[   29.437081]  [<f82806da>] ? b43_exit+0x12/0x2c [b43]


```

---

### Post by bkratz on 2011-01-06
did it go back to working after removing ndiswrapper?

---

### Post by mysteryd on 2011-01-06
> **bkratz said:**
> did it go back to working after removing ndiswrapper?
 
Nope. I still have no wireless. Or wired for that matter.

---

### Post by chili555 on 2011-01-06
Please let bkratz and me see this as an attachment:```
dmesg > myst2.txt
lsmod >> myst2.txt
sudo cat /var/log/syslog | grep b4 >> myst2.txt
sudo /etc/init.d/networking restart >> myst2.txt
zip myst2.zip myst2.txt
```This is quite perplexing; it ought to start and run perfectly.

---

### Post by mysteryd on 2011-01-06
As requested

---

### Post by bkratz on 2011-01-06
It sure seems that ndiswrapper still has control

[   27.122564] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   27.261765] ndiswrapper: driver bcmwl5 (Broadcom,03/23/2006, 4.40.19.0) loaded
[   27.262268] ndiswrapper 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   27.273026] ndiswrapper: using IRQ 11
[   28.248098] wlan0: ethernet device 00:0b:7d:0f:cf:5b using NDIS driver: bcmwl5, version: 0x4281300, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4320.5.conf
[

configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.55+Broadcom,03/23/2006, 4.40.1

@Chili how about if we remove it rather than blacklisting?

---

### Post by chili555 on 2011-01-06
Here is a problem:> [ 6778.237326] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[ 6778.289697] ndiswrapper: driver bcmwl5 (Broadcom,03/23/2006, 4.40.19.0) loaded
[ 6778.290185] ndiswrapper 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[ 6778.298436] ndiswrapper: using IRQ 11
[ 6778.715994] b44: eth0: powering down PHY
[ 6778.729219] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 6778.839323] wlan0: ethernet device 00:0b:7d:0f:cf:5b using NDIS driver: bcmwl5, version: 0x4281300, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4320.5.conf
[ 6778.839383] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[ 6778.843154] usbcore: registered new interface driver ndiswrapper
[ 6784.968324] ndiswrapper (iw_set_auth:1602): invalid cmd 12We have, still, ndiswrapper conflicting with b43! Let's remove it again:```
sudo ndiswrapper -e bcmwl5
```
Please verify that ndiswrapper is blacklisted:```
cat /etc/modprobe.d/blacklist.conf
```There should be a line in there:```
blacklist ndiswrapper
```If it doesn't appear, add it:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Next, be sure there are no longer any aliases in /etc/modprobe.d:```
ls /etc/modprobe.d | grep ndis
```If there are any such files in there, remove them:```
cd /etc/modprobe.d
sudo rm whateverndisfileyoufound
```Now, be sure ndiswrapper is not being explicitly called:```
cat /etc/modules | grep ndis
```If it is listed there, do:```
sudo gedit /etc/modules
```Remove ndiswrapper.

In all cases, proofread carefully, save and close gedit.

Reboot and give us a good report or a myst.zip.

I wonder if your system is haunted.

---

### Post by mysteryd on 2011-01-06
> **chili555 said:**
> Here is a problem:We have, still, ndiswrapper conflicting with b43! Let's remove it again:```
sudo ndiswrapper -e bcmwl5
```
Please verify that ndiswrapper is blacklisted:```
cat /etc/modprobe.d/blacklist.conf
```There should be a line in there:```
blacklist ndiswrapper
```If it doesn't appear, add it:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Next, be sure there are no longer any aliases in /etc/modprobe.d:```
ls /etc/modprobe.d | grep ndis
```If there are any such files in there, remove them:```
cd /etc/modprobe.d
sudo rm whateverndisfileyoufound
```Now, be sure ndiswrapper is not being explicitly called:```
cat /etc/modules | grep ndis
```If it is listed there, do:```
sudo gedit /etc/modules
```Remove ndiswrapper.
 
In all cases, proofread carefully, save and close gedit.
 
Reboot and give us a good report or a myst.zip.
 
I wonder if your system is haunted.
 
```
 
cat /etc/modprobe.d/blacklist.conf
blacklist ndiswrapper

``` 
There is no bcmwl5 file or directory
There is nothing on```
 /etc/modprobe.d | grep ndis
```
There is nothing on ```
cat /etc/modules | grep ndiswrapper
```

---

### Post by chili555 on 2011-01-06
The "haunted" idea is starting to look better! Let's take the strongest steps:```
sudo rm -rf /etc/ndiswrapper/*
```Now reboot and give us a myst.zip.

PS- I am starting to get the creeps. I got an email from Amazon this morning offering a good price on Asus USB-N13 Wireless-N Adapter. Targeted advertising at it worst!

---

### Post by mysteryd on 2011-01-06
> **chili555 said:**
> The "haunted" idea is starting to look better! Let's take the strongest steps:```
sudo rm -rf /etc/ndiswrapper/*
```Now reboot and give us a myst.zip.
 
PS- I am starting to get the creeps. I got an email from Amazon this morning offering a good price on Asus USB-N13 Wireless-N Adapter. Targeted advertising at it worst!
 
Haha! Thats good stuff.
 
There wasnt anything in /etc/ndiswrapper/ but ran the command anyways. Starting to catch on the the command stuff as far as what these things are doing. Rebooted after the rm -rf and here is the myst3.zip

---

### Post by chili555 on 2011-01-06
Do you believe this?> [   28.950477] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)Actually, everything otherwise looks pretty healthy. Do you have an interface?```
iwconfig
sudo iwlist wlan0 scan
```Anything showing when you click the Network Manager icon?

---

### Post by mysteryd on 2011-01-06
> **chili555 said:**
> Do you believe this?Actually, everything otherwise looks pretty healthy. Do you have an interface?```
iwconfig
sudo iwlist wlan0 scan
```Anything showing when you click the Network Manager icon?
 
Its running now. Sorry... had work and couldnt reply (i know... four letter word)
 
What was the deal?

---

### Post by chili555 on 2011-01-06
> Its running now.Meaning what? Meaning the wireless is fixed and you are happy?

---

### Post by mysteryd on 2011-01-06
> **chili555 said:**
> Meaning what? Meaning the wireless is fixed and you are happy?
 
The wireless is fixed. iwconfig returns more than "lo".
 
Stay subscribed to this just incase =) It freaked out last time after about 1.5 hours of surfing.
 
Happy, definitely... learned some stuff and fixed the issue.

---

### Post by chili555 on 2011-01-06
> Stay subscribed to this just incase =) Forever, my friend. Post back any time and my colleagues and I will be happy to help.

---

### Post by mysteryd on 2011-01-06
Its down again with the same symptoms. I will run thru the steps tomorrow. This is frustrating.

---

### Post by bkratz on 2011-01-06
I bet it is. Were you doing anything special when it happened or did it just not boot correctly again?

---

### Post by mysteryd on 2011-01-06
> **bkratz said:**
> I bet it is. Were you doing anything special when it happened or did it just not boot correctly again?

Just tried to boot it. Only showed lo in iwconfig. Tomorrow we try again.

---

### Post by mysteryd on 2011-01-07
Round 4?

---

### Post by chili555 on 2011-01-07
> [   31.330566] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)I will be out for a few hours today. In the meantime, please do:```
sudo apt-get remove --purge ndis*
```I will check in later.

---

### Post by mysteryd on 2011-01-07
> **chili555 said:**
> I will be out for a few hours today. In the meantime, please do:```
sudo apt-get remove --purge ndis*
```I will check in later.
 
Ok this thing is making me think I installed ndiswrapper wrong.
 
```
 
E: Could't find package ndiswrapper-1.56

```
 
when clearly I have 1.55 installed.

---

### Post by bkratz on 2011-01-07
I think the term "haunted" earlier was appropriate! I don't even see the line Chili was referencing " [ 31.330566] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)" in the myst4 file above. Did I miss it? And I thought 1.56 was the actual current version of ndiswrapper! I commented on that earlier. Anyway you guys have me lost! I think I'll just watch, you are in the best hands (Chili) in this group.

---

### Post by chili555 on 2011-01-07
> **bkratz said:**
> I think the term "haunted" earlier was appropriate! I don't even see the line Chili was referencing " [ 31.330566] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)" in the myst4 file above. Did I miss it? And I thought 1.56 was the actual current version of ndiswrapper! I commented on that earlier. Anyway you guys have me lost! I think I'll just watch, you are in the best hands (Chili) in this group.Here is a bigger snip:> [   31.281160] EIP: [<c0163d5a>] insert_work+0x4a/0xb0 SS:ESP 0068:f41fbe14
[   31.281169] CR2: 000000000000f30a
[   31.281175] ---[ end trace a78f150843afac79 ]---
[COLOR="Red"][   31.330566] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)[/COLOR]
[  122.895659] evbug.c: Event. Dev: input4, Type: 4, Code: 4, Value: 30
[  122.895683] evbug.c: Event. Dev: input4, Type: 1, Code: 30, Value: 1
[  122.895694] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  123.017617] evbug.c: Event. Dev: input4, Type: 4, Code: 4, Value: 30By the way, the evbug.c lines are somewhat troubling; I am researching now.

@mysteryd--

You might open System > Administration > Synaptic and search for ndis. Mark every thing that has ndiswrapper in its name as well as ndisgtk if you have it for complete removal including configuration files.

---

### Post by mysteryd on 2011-01-07
> **chili555 said:**
> Here is a bigger snip:By the way, the evbug.c lines are somewhat troubling; I am researching now.
 
@mysteryd--
 
You might open System > Administration > Synaptic and search for ndis. Mark every thing that has ndiswrapper in its name as well as ndisgtk if you have it for complete removal including configuration files.
 
Was ahead of you on that. Already attempted that but it appears my only choise is for installation.
 
Those errors are causing my reboots to hang and requiring hard boots.

---

### Post by chili555 on 2011-01-07
I am currently of the opinion that, if we get rid of ndiswrapper, the evbugs will go away. Let's wait and see.

@bkratz--

Keep chiming in when you need to; you are very helpful!

---

### Post by bkratz on 2011-01-07
Chili, in case you haven't found this one yet there is a really old bug report (updated as late as Dec 2010) that looks familiar. Maybe it is this

[https://bugs.launchpad.net/ubuntu/+source/module-init-tools/+bug/240553](https://bugs.launchpad.net/ubuntu/+source/module-init-tools/+bug/240553)

---

### Post by chili555 on 2011-01-07
Further to evbug, as suggested in the bug report, evbug is generally blacklisted. Here is a snip from my /etc/modprobe.d/blacklist.conf```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug
```Let's add it back and remove the module from those currently loaded:```
sudo su
echo "blacklist evbug" >> /etc/modprobe.d/blacklist.conf
rmmod -f evbug
exit
```

---

### Post by mysteryd on 2011-01-07
> **chili555 said:**
> Further to evbug, as suggested in the bug report, evbug is generally blacklisted. Here is a snip from my /etc/modprobe.d/blacklist.conf```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.
 
# evbug is a debug tool that should be loaded explicitly
blacklist evbug
```Let's add it back and remove the module from those currently loaded:```
sudo su
echo "blacklist evbug" >> /etc/modprobe.d/blacklist.conf
rmmod -f evbug
exit
```
 
Ok... explain why my wireless now works after that if you dont mind.
 
```
 
ERROR: Removing 'evbug' : No such file or directory

```
 
Nevermind... I rebooted to check and it is back down again.

---

### Post by chili555 on 2011-01-07
> I rebooted to check and it is back down again.Did you remove ndiswrapper? Please let us see a myst5.zip and a tranquilizer.

---

### Post by mysteryd on 2011-01-07
> **chili555 said:**
> Did you remove ndiswrapper? Please let us see a myst5.zip and a tranquilizer.
 
ndiswrapper is not installed according to apt-get and synaptic. I dont know how to search to make sure it is not installed any other way.
 
If I had a tranq I would have already put it into this ^%&* laptop.

---

### Post by chili555 on 2011-01-07
> I dont know how to search to make sure it is not installed any other way.```
lsmod | grep ndis
dmesg | grep ndis
ls /usr/sbin | grep ndis
```

---

### Post by mysteryd on 2011-01-07
> **chili555 said:**
> ```
lsmod | grep ndis
dmesg | grep ndis
ls /usr/sbin | grep ndis
```
 
All three had no responses.

---

### Post by mysteryd on 2011-01-07
As requested... a few hours late.

---

### Post by chili555 on 2011-01-07
Here are some sobering messages:> [   28.628733] Oops: 0002 [#1] SMP 
[   28.628737] last sysfs file: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:02.0/ssb0:0/[COLOR="Red"]firmware[/COLOR]/[COLOR="Red"]ssb[/COLOR]0:0/loading
--- snip ---
[   28.628854] Call Trace:
[   28.628865]  [<c012a688>] ? default_spin_lock_flags+0x8/0x10
[   28.628872]  [<c058d9bf>] ? _spin_lock_irqsave+0x2f/0x50
[   28.628878]  [<c016402d>] ? __queue_work+0x2d/0x50
[   28.628883]  [<c01640d0>] ? queue_work_on+0x40/0x60
[   28.628887]  [<c016412a>] ? queue_work+0x1a/0x20
[   28.628915]  [<f8299529>] ? ieee80211_queue_work+0x29/0x40 [mac80211]
[   28.628933]  [<f81f2468>] ? [COLOR="Red"]b43[/COLOR]_led_brightness_set+0x28/0x30 [b43]
[   28.628941]  [<c04ab52f>] ? led_trigger_set+0xbf/0xd0
[   28.628945]  [<c04ab5d9>] ? led_trigger_unregister+0x99/0xa0
[   28.628959]  [<f829a04a>] ? ieee80211_led_exit+0x1a/0x80 [mac80211]
[   28.628970]  [<f8282104>] ? ieee80211_unregister_hw+0xb4/0xe0 [mac80211]
[   28.628976]  [<c016437f>] ? cancel_work_sync+0xf/0x20
[   28.628986]  [<f81d7e08>] ? [COLOR="Red"]b43[/COLOR]_remove+0xa8/0xb0 [b43]
[   28.629000]  [<f8022782>] ? [COLOR="Red"]ssb[/COLOR]_device_remove+0x22/0x40 [[COLOR="Red"]ssb[/COLOR]]
--- snip ---A kernel oops is pretty serious and sometimes, not always, suggests a hardware problem.

[http://kerneltrap.org/mailarchive/linux-kernel/2007/4/26/81930](http://kerneltrap.org/mailarchive/linux-kernel/2007/4/26/81930)

I am Googling and suggest you do the same. I hope bkratz is watching and can lend a hand.

Do you know how to run memtest86 from the GRUB menu in order to test the integrity of your memory and motherboard? It's a thorough test and takes a fair amount of time. I generally run it all night!

---

### Post by bkratz on 2011-01-07
> **chili555 said:**
> Here are some sobering messages:A kernel oops is pretty serious and sometimes, not always, suggests a hardware problem.

[http://kerneltrap.org/mailarchive/linux-kernel/2007/4/26/81930](http://kerneltrap.org/mailarchive/linux-kernel/2007/4/26/81930)

I am Googling and suggest you do the same. I hope bkratz is watching and can lend a hand.

Do you know how to run memtest86 from the GRUB menu in order to test the integrity of your memory and motherboard? It's a thorough test and takes a fair amount of time. I generally run it all night!

I have been "googlubuntu and google-ing" since I looked at the listing and have found just how little I actually know, but it does seem serious. There are several bugs which demonstrate it, but they don't seem related (sometimes intel video-sometimes IR devices) and others. Will continue to look, hopefully learning something in the process. I think the memory test is a good idea.

---

### Post by chili555 on 2011-01-07
Does it kick your wireless to life if you remove and reload the driver?```
sudo rmmod -f ssb
sudo rmmod -f b43
sudo modprobe b43
```Does your system freeze, become unstable, smoke or spark??!!

---

### Post by mysteryd on 2011-01-08
> **chili555 said:**
> Here are some sobering messages:A kernel oops is pretty serious and sometimes, not always, suggests a hardware problem.

[http://kerneltrap.org/mailarchive/linux-kernel/2007/4/26/81930](http://kerneltrap.org/mailarchive/linux-kernel/2007/4/26/81930)

I am Googling and suggest you do the same. I hope bkratz is watching and can lend a hand.

Do you know how to run memtest86 from the GRUB menu in order to test the integrity of your memory and motherboard? It's a thorough test and takes a fair amount of time. I generally run it all night!

Running memtest86 now. So after that I will address the other stuff this weekend.

---

### Post by mysteryd on 2011-01-08
> **chili555 said:**
> Does it kick your wireless to life if you remove and reload the driver?```
sudo rmmod -f ssb
sudo rmmod -f b43
sudo modprobe b43
```Does your system freeze, become unstable, smoke or spark??!!

The system only provides issues during reboot or shut down. Everything else is fine. Smoking and sparking is normal right? =) (which means no it doesnt smoke or spark)

---

### Post by chili555 on 2011-01-08
> The system only provides issues during reboot or shut down.Does that mean if you remove and reinsert b43 and ssb after boot it works well? We could automate that!

I am concerned that either the motherboard or the memory has a perhaps intermittent fault. Rectifying that would pay dividends in stability not only for wireless but probably other systems as well.

---

### Post by mysteryd on 2011-01-08
> **chili555 said:**
> Does that mean if you remove and reinsert b43 and ssb after boot it works well? We could automate that!

I am concerned that either the motherboard or the memory has a perhaps intermittent fault. Rectifying that would pay dividends in stability not only for wireless but probably other systems as well.

ssb wouldnt allow rmmod
b43 wouldnt allow me to rmmod because it was in use

Rebooted and modprobe and still hangs on reboot. I really dont think this is going to end well.

---

### Post by chili555 on 2011-01-08
> ssb wouldnt allow rmmod
b43 wouldnt allow me to rmmod because it was in useYou'd probably have to 'down' wlan0:```
sudo ifconfig wlan0 down
sudo rmmod -f ssb
sudo rmmod -f b43
```How did memtest86 come out? If it's merely a memory problem, you can probably replace the stick easily and inexpensively. If you have two sticks, you'll need to test each alone to isolate the one that's sick. You could also boot with one stick and then the other to see which one causes an oops.

---

### Post by mysteryd on 2011-01-08
> **chili555 said:**
> You'd probably have to 'down' wlan0:```
sudo ifconfig wlan0 down
sudo rmmod -f ssb
sudo rmmod -f b43
```How did memtest86 come out? If it's merely a memory problem, you can probably replace the stick easily and inexpensively. If you have two sticks, you'll need to test each alone to isolate the one that's sick. You could also boot with one stick and then the other to see which one causes an oops.

Memory test passed. No errors.

Attached is what I am getting back on dmesg and the rmmods.

Thank you guys again for the help.

---

### Post by chili555 on 2011-01-09
I see this in your logs:> [   28.628701] BUG: unable to handle kernel NULL pointer dereference at (null)
[   28.628712] IP: [<c0163d5a>] insert_work+0x4a/0xb0
[   28.628729] *pde = 00000000 
[   28.628733] Oops: 0002 [#1] SMP 
[   28.628737] last sysfs file: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:02.0/ssb0:0/firmware/ssb0:0/loadingIt's not exactly an unknown issue:  [http://www.google.com/search?source=ig&hl=en&rlz=&=&q=%22BUG%3A+unable+to+handle+kernel+NULL+pointer+dereference+at+%28null%29%22&btnG=Google+Search&aq=f&oq=#hl=en&expIds=25657,25907,27955&sugexp=ldymls&xhr=t&q=%22BUG%3A+unable+to+handle+kernel+NULL+pointer+dereference+at+%28null%29%22+b43&cp=68&qe=IkJVRzogdW5hYmxlIHRvIGhhbmRsZSBrZXJuZWwgTlVMTCBwb2ludGVyIGRlcmVmZXJlbmNlIGF0IChudWxsKSIgYjQz&qesig=YDCU9x8b8z7N-ixsI9Lj5w&pkc=AFgZ2tmgrapW724ngo2jRw9i_gbsL0NQPykUJFnklBpArHb5Uh30zEC98TmJLJPqovdSwSrj2OT3rO9dLnSQT6Uqz4WjtP8lNg&pf=p&sclient=psy&safe=off&aq=f&aqi=&aql=&oq=%22BUG:+unable+to+handle+kernel+NULL+pointer+dereference+at+%28null%29%22+b43&gs_rfai=&pbx=1&fp=9bef8cda26d1a6ec](http://www.google.com/search?source=ig&hl=en&rlz=&=&q=%22BUG%3A+unable+to+handle+kernel+NULL+pointer+dereference+at+%28null%29%22&btnG=Google+Search&aq=f&oq=#hl=en&expIds=25657,25907,27955&sugexp=ldymls&xhr=t&q=%22BUG%3A+unable+to+handle+kernel+NULL+pointer+dereference+at+%28null%29%22+b43&cp=68&qe=IkJVRzogdW5hYmxlIHRvIGhhbmRsZSBrZXJuZWwgTlVMTCBwb2ludGVyIGRlcmVmZXJlbmNlIGF0IChudWxsKSIgYjQz&qesig=YDCU9x8b8z7N-ixsI9Lj5w&pkc=AFgZ2tmgrapW724ngo2jRw9i_gbsL0NQPykUJFnklBpArHb5Uh30zEC98TmJLJPqovdSwSrj2OT3rO9dLnSQT6Uqz4WjtP8lNg&pf=p&sclient=psy&safe=off&aq=f&aqi=&aql=&oq=%22BUG:+unable+to+handle+kernel+NULL+pointer+dereference+at+%28null%29%22+b43&gs_rfai=&pbx=1&fp=9bef8cda26d1a6ec)

It is (not very) funny that it appears in some, but not all of your logs. One of the suggestions I read when I googled was to update to the latest kernel. Have you done so? The latest is, for a 32-bit Ubuntu 10.10 system, 2.6.35-24-generic. 

Another thing I'm a bit concerned about is that when the system chokes, it's loading the firmware for ssb:> b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   27.440092] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   27.456739] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   27.477128] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fwLet's be sure you have all those files and they're not corrupted:```
ls -al /lib/firmware/b43
```My corresponding entries are:> -rw-r--r--  1 root root   178 2010-11-02 10:36 b0g0bsinitvals5.fw
-rw-r--r--  1 root root  1848 2010-11-02 10:36 b0g0initvals5.fw
-rw-r--r--  1 root root  1320 2010-11-02 10:36 pcm5.fw
-rw-r--r--  1 root root 22264 2010-11-02 10:36 ucode5.fwI will be interested not only in the existence of these files, but their size and permissions.

---

### Post by mysteryd on 2011-01-09
> **chili555 said:**
> I see this in your logs:It's not exactly an unknown issue:  [http://www.google.com/search?source=ig&hl=en&rlz=&=&q=%22BUG%3A+unable+to+handle+kernel+NULL+pointer+dereference+at+%28null%29%22&btnG=Google+Search&aq=f&oq=#hl=en&expIds=25657,25907,27955&sugexp=ldymls&xhr=t&q=%22BUG%3A+unable+to+handle+kernel+NULL+pointer+dereference+at+%28null%29%22+b43&cp=68&qe=IkJVRzogdW5hYmxlIHRvIGhhbmRsZSBrZXJuZWwgTlVMTCBwb2ludGVyIGRlcmVmZXJlbmNlIGF0IChudWxsKSIgYjQz&qesig=YDCU9x8b8z7N-ixsI9Lj5w&pkc=AFgZ2tmgrapW724ngo2jRw9i_gbsL0NQPykUJFnklBpArHb5Uh30zEC98TmJLJPqovdSwSrj2OT3rO9dLnSQT6Uqz4WjtP8lNg&pf=p&sclient=psy&safe=off&aq=f&aqi=&aql=&oq=%22BUG:+unable+to+handle+kernel+NULL+pointer+dereference+at+%28null%29%22+b43&gs_rfai=&pbx=1&fp=9bef8cda26d1a6ec](http://www.google.com/search?source=ig&hl=en&rlz=&=&q=%22BUG%3A+unable+to+handle+kernel+NULL+pointer+dereference+at+%28null%29%22&btnG=Google+Search&aq=f&oq=#hl=en&expIds=25657,25907,27955&sugexp=ldymls&xhr=t&q=%22BUG%3A+unable+to+handle+kernel+NULL+pointer+dereference+at+%28null%29%22+b43&cp=68&qe=IkJVRzogdW5hYmxlIHRvIGhhbmRsZSBrZXJuZWwgTlVMTCBwb2ludGVyIGRlcmVmZXJlbmNlIGF0IChudWxsKSIgYjQz&qesig=YDCU9x8b8z7N-ixsI9Lj5w&pkc=AFgZ2tmgrapW724ngo2jRw9i_gbsL0NQPykUJFnklBpArHb5Uh30zEC98TmJLJPqovdSwSrj2OT3rO9dLnSQT6Uqz4WjtP8lNg&pf=p&sclient=psy&safe=off&aq=f&aqi=&aql=&oq=%22BUG:+unable+to+handle+kernel+NULL+pointer+dereference+at+%28null%29%22+b43&gs_rfai=&pbx=1&fp=9bef8cda26d1a6ec)

It is (not very) funny that it appears in some, but not all of your logs. One of the suggestions I read when I googled was to update to the latest kernel. Have you done so? The latest is, for a 32-bit Ubuntu 10.10 system, 2.6.35-24-generic. 

Another thing I'm a bit concerned about is that when the system chokes, it's loading the firmware for ssb:Let's be sure you have all those files and they're not corrupted:```
ls -al /lib/firmware/b43
```My corresponding entries are:I will be interested not only in the existence of these files, but their size and permissions.

here is mine.

---

### Post by chili555 on 2011-01-10
Nothing we have done has kicked your Broadcom to life except very briefly. I suggest a completely different approach. Get that Asus N13 ready, we're going to work. First, do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add three new lines: ```
blacklist b43
blacklist b44
blacklist ssb
```Proofread, save and close gedit. Reboot.

Now do:```
dmesg | grep -e b4 -e Oops
```Any listings? No? Great! Now insert the Asus and do:```
sudo modprobe rt2870sta
dmesg | grep -i rt2
```Any wireless joy?

---

### Post by mysteryd on 2011-01-10
double

---

### Post by mysteryd on 2011-01-10
> **chili555 said:**
> Nothing we have done has kicked your Broadcom to life except very briefly. I suggest a completely different approach. Get that Asus N13 ready, we're going to work. First, do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add three new lines: ```
blacklist b43
blacklist b44
blacklist ssb
```Proofread, save and close gedit. Reboot.
 
Now do:```
dmesg | grep -e b4 -e Oops
```Any listings? No? Great! Now insert the Asus and do:```
sudo modprobe rt2870sta
dmesg | grep -i rt2
```Any wireless joy?
 
/etc/modprobe.d/blacklist.conf was checked over and reads
```
 
blacklist ndiswrapper
blacklist evbug
blacklist b43
blacklist b44
blacklist ssb

```
 
I ran the commands you asked, rebooted and got this on ```
dmesg | grep -e b4
``` and it pissed me off. Then noticed ifconfig didnt return anything so I ```
dmesg | grep -i rt2
```
 
The light on the asus doesnt turn on so not sure it is being found by the computer. Attached is my text dmesg returns after all of this, and ifconfig and iwconfig.
 
```
 
Bus 001 Device 002: ID 0b05:1784 ASUSTek Computer, Inc.

```
 
So it SEES it... thinking maybe it doesnt know what to do with it?

---

### Post by mysteryd on 2011-01-10
"haunted" is a possibility.

I noticed when I reloaded I didnt get an -e Oops in my dmesg. So I removed the b43, b44 and ssb in the blacklist.conf and have had 10 reboots at work connecting to my EVO and now currently at school on their wifi network.

I think I am going to keep with the press and try my luck at whatever fixed itself and see how this goes. Hopefully its sustained success.

---

### Post by chili555 on 2011-01-10
I have my fingers crossed. I was starting to doubt the power of my grey beard.

---

### Post by bkratz on 2011-01-10
> **chili555 said:**
> I have my fingers crossed. I was starting to doubt the power of my grey beard.



Been out of town for a few days, and it looks like I have missed a lot. 
PS--had no doubt in the "grey" beard!

---

