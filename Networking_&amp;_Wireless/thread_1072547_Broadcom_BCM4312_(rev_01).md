---
title: "Broadcom BCM4312 (rev 01)"
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by DPic on 2009-02-17
So, i hooked up my friend with Ubuntu. Everything goes very smoothly (except for a few hurdles getting Japanese input to work) but then wireless isn't working. Restricted drivers recommends something which i install and nearby networks are found but a connection couldn't be established. So i looked online for help and tried following complicated instuctions to get ndiswrapper working (what a nightmare!) but that failed and seems to have made things worse since there is no longer the option to enable wireless by right-clicking on the network icon. 

SO, if anyone can 
[LIST=1]
[*]Undo the ndiswrapper damage
[*]Get wireless working
[/LIST]
I WILL OWE YOU MY LIFE! 

This might help and please let me know if you have any ideas or need mor info:

```
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
        Subsystem: Dell Device 000b
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at fe7fc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel modules: wl

```

Thanksssssssss! 
.danny

---

### Post by puppywhacker on 2009-02-17
I agree ndiswrappers are a nightmare. I don't know what you did, but maybe you need to unload some drivers with rmmod, but I don't think you did serious damage there.

I have an Broadcom 4306 for which I used these instructions [fw-b43 instructions]("http://linuxwireless.org/en/users/Drivers/b43#fw-b43-new")

I built my own fw-cutter to extract the firmware from the restricted linux drivers and I downloaded and built the module b43 which replacemes b43xx. And I loaded the module with
```
modprobe b43
depmod -a
```
and a small reboot for goodluck :)

I used iwconfig to set the channel and essid. I don't rely only on the network manger applet (the network icon) to find my network.
```
iwconfig wlan0 channel 10
iwconfig wlan0 essid "myaccess"
```

goodluck

---

### Post by DPic on 2009-02-17
Sorry, i'm a complete n00b when it comes to this stuff. Can i get some help figuring out exactly what the problem is and step-by-step instructions on how to fix it?

---

### Post by Plumtreed on 2009-02-17
Doesn't Broadcom provide a proprietary driver for BCM4312. Check the Broadcom site.Usually described as 'wl'.

I have BCM4312 and 8.04 and 8.10 with NetworkManager and it runs 'out of the box'.

---

### Post by DPic on 2009-02-17
Then can i get help reversing the ndiswrapper stuff i described in the first post?

---

### Post by Ayuthia on 2009-02-17
If you are using Intrepid , you can try the following:
```
sudo modprobe -r b43 ssb wl ndiswrapper
sudo modprobe wl
sudo /etc/init.d/networking restart
sudo iwlist scan
```
That will remove the possible wireless modules and load the Broadcom STA module.  If this works, we can create a script to make it permanent.  This will also prevent the ndiswrapper to work so you don't have to uninstall ndiswrapper.

---

### Post by DPic on 2009-02-18
Thanks! That undid the damage but now i still have to figure out how to get wirless working normally. Here's the output if that helps at all...

```
boo@boo-laptop:~$ sudo modprobe -r b43 ssb wl ndiswrapper
boo@boo-laptop:~$ sudo modprobe wl
boo@boo-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
boo@boo-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1E:52:7A:FF:7D
                    ESSID:"Router"
                    Mode:Managed
                    Frequency=2.412 GHz (Channel 1)
                    Quality:1/5  Signal level:-90 dBm  Noise level:-93 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:18:39:D5:8F:EB
                    ESSID:"Boneyard"
                    Mode:Managed
                    Frequency=2.437 GHz (Channel 6)
                    Quality:4/5  Signal level:-63 dBm  Noise level:-91 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:18:01:FE:9E:51
                    ESSID:"scrapheap"
                    Mode:Managed
                    Frequency=2.462 GHz (Channel 11)
                    Quality:5/5  Signal level:-44 dBm  Noise level:-24 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

```

---

### Post by DPic on 2009-02-18
Scratch that, it doesn't save after a reboot. How do i make this permanent?

---

### Post by kevdog on 2009-02-19
echo "blacklist b43" | sudo tee -a /etc/modprobe.d/blacklist
echo "blacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist
echo "wl" | sudo tee -a /etc/modules

Also edit the /etc/modules file as root, and remove the ndiswrapper line.

That should make the config permanent.

---

### Post by DPic on 2009-02-19
Thank you! Although something still seems to be different since i am unable to activate the Restricted Broadcom STA Driver from the restricted drivers manager. 

Also, i have noticed that the wifi light next to other light (like power, HDD activity, etc) is on, but there seems to be a light next to the actual hardware switch for the wifi which is not on. I did not pay attention to this before ubuntu so it might be irrelevant information. 

More symptoms: As i said, available networks are detected, but will not connect. I enter in the passcode and it attempts to connect for a while before asking me for the passphrase again. 

Also, this just in, if i click on the network manager applet, wireless networks are all listed twice. i don't think this has to do with the problem though. 

sorry, i'm just trying to provide as much information as possible to come to a solution. I NEED to get wireless working for my friend...

Thanks for the help everyone!

---

### Post by DPic on 2009-02-21
I just tried wireless from a Intrepid 32-bit live CD and it was able to connect to the available open wireless network but not my protected network (perhaps that's a problem on my end), but i'm running 64 bit. Is this a bug?

---

