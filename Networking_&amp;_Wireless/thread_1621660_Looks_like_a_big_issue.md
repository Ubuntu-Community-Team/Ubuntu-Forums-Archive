---
title: "Looks like a big issue?"
date: 2010-11-14
forum: Networking &amp; Wireless
---

### Post by ArtlessIntent on 2010-11-14
I've got no access to my wireless either, and after looking through screeds of forum posts it seems that alot of people are having the same issue, especially with 10.10.  I am wondering if this will be taken seriously by ubunut technicians etc and will there be an update fix in the near future? Ubuntu rules - i am just so keen to get my computer loose from the wire! matt

---

### Post by chili555 on 2010-11-14
Have you posted a thread so some of us ubunut technicians etc can help?

---

### Post by ArtlessIntent on 2010-11-14
Hi Chilli, no i didn't, Im a real newbie to ubuntu and linux, ive a totally different world! Basically, I use a hp 6730b laptop , im running ubuntu 10.10, and i can't access my wireless internet network for some reason. i can get to it wired, not wireless. I
Im new to 'terminals' and the linux code , its fascinating stuff but a bit over my head . But if you want me to do anything with terminal let me know, ill try and post results here.

---

### Post by chili555 on 2010-11-14
You have come to the right place: Dr. Chili, also known as Mr. Terminal.

Please open Applications > Accessories > Terminal and we will ask your computer for some diagnostic information. First, we will ask it what kind of wireless card it has. Then we will try to get a driver installed and configured. I believe your wireless card is built-in, so please run and post:```
lspci -nn
```Feel free to strip away everything that is clearly not your wireless. I suspect it's a Broadcom that simply wants some firmware.

If so, can you get a wired connection and go to System > Administration > Additional Drivers and see if you can activate your Broadcom?

---

### Post by ArtlessIntent on 2010-11-14
from the code request i got: 
crude@Artless1:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection [8086:4237]
85:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
86:02.0 FireWire (IEEE 1394) [0c00]: Agere Systems FW322/323 [11c1:5811] (rev 70)
crude@Artless1:~$


PS , when seachibg for drivers i was told 'no proprietary drivers are on this system'

---

### Post by chili555 on 2010-11-14
> Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection [8086:4237]This beauty ought to work perfectly. Let's load the module explicitly and see if there is another problem:```
sudo modprobe iwlagn
dmesg | grep iwl
iwconfig
sudo iwlist wlan0 scan
```Thanks.

---

### Post by ArtlessIntent on 2010-11-14
real sorry there mr chilli but i have a problem with my terminal, when it asks for my password after entering the command i cant type anything - it wont budge....is there anyway out of that scenario? (sorry bout this!)

---

### Post by ArtlessIntent on 2010-11-14
got this far: 
crude@Artless1:~$ modprobe iwlagn 
crude@Artless1:~$ dmesg | grep iwl 
[   13.726534] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   13.726537] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   13.726589] iwlagn 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.726598] iwlagn 0000:02:00.0: setting latency timer to 64
[   13.726623] iwlagn 0000:02:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   13.773210] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   13.773334] iwlagn 0000:02:00.0: irq 46 for MSI/MSI-X
[   13.833410] iwlagn 0000:02:00.0: loaded firmware version 8.24.2.12
[   13.841383] phy0: Selected rate control algorithm 'iwl-agn-rs'
crude@Artless1:~$

---

### Post by ArtlessIntent on 2010-11-14
So for some reason i cant type sudo in without being asked for my password - which i cant type in .
but i can type everything but sudo. with these commands do you enter the whole lot in at once (pasted in) or is it line at a time?

---

### Post by ArtlessIntent on 2010-11-14
crude@Artless1:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
crude@Artless1:~$ iwlist wlan0 scan 
wlan0     No scan results

(didnt type in 'sudo' )

---

### Post by bkratz on 2010-11-14
Sudo requires your password. When you type it in, it will not show on the screen. Just press enter when done:  with what Mr. Terminal! wants.

---

### Post by chili555 on 2010-11-14
When you type in sudo, your password is accepted but, for security reasons, is not echoed back in the terminal. Not even **** is printed so eavesdroppers can't even see how many characters it contains. It is being accepted nonetheless. Let's try it now. Please run and post:```
sudo rfkill list all
```All your other listings look really very healthy.

---

### Post by ArtlessIntent on 2010-11-14
ok, thanks! 
crude@Artless1:~$ sudo rfkill list all 
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
crude@Artless1:~$

---

### Post by chili555 on 2010-11-14
Looks very good. Please detach the ethernet cable and click the Network Manager icon and see if you see your network. Click it and try to connect and tell me of any errors or messages.

---

### Post by ArtlessIntent on 2010-11-14
......well, it lists the name of my wireless network, and i click connect, the lil' icon spins for minutes , and dose'nt stop or connect. My passphrase ./ wep key is all correct, although, i don't have the option to enter both the password and wep key - maybe thats the problem? my sons eeepc had ububntu on it asnd picked up/connected to our wireless network no trouble at all. hey thx alot for your patience and help with this ! matt, new zealand

---

### Post by chili555 on 2010-11-14
> although, i don't have the option to enter both the password and wep key - maybe thats the problem? I don't understand. When you click your network, it should prompt you for the encryption key; in your case, the WEP hex key.

Is yours a DSL modem which often requires a user name and password? Those are set up by right-clicking the Network Manager icon, selecting 'Edit Connections' and selecting the DSL tab. Fill in your details there. If you are using a router, it's usually easier to set up the username and password there. 
Be sure to check the 'Connect Automatically' box.

---

### Post by ArtlessIntent on 2010-11-14
...yeah sorry, i might be going off on a tangent. what happens , after ive entered the key etc, the icon spins unti i get a notiofication saying 'wireless networks' disconnected' .I'll try it again

---

### Post by ArtlessIntent on 2010-11-14
Hi, yeah no, it just dosent want to connect. No matter what i try. Its all set up to go, it recognizes the network name etc but just wont connect. Anyway, i give up, hopefully ill receive an update with a fix or the next version of ubuntu will have this sorted! thanks for your help there mr terminal. matt ps - it isnt DSL either...ne'er mind!

---

### Post by chili555 on 2010-11-14
Let's see what kind of network you have:```
sudo iwlist wlan0 scan
```> Anyway, i give up,I almost never give up. Let's sleep on it and give it a fresh start tomorrow.

---

### Post by ArtlessIntent on 2010-11-14
Ha Ha i like that attitude. Ok 
 Cell 01 - Address: 00:17:3F:BD:D9:22
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-17 dBm  
                    Encryption key:on
                    ESSID:"belkin54g"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000124ea54177
                    Extra: Last beacon: 3208ms ago
                    IE: Unknown: 000962656C6B696E353467
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 0406000200000000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C

---

### Post by chili555 on 2010-11-14
It looks like a straight-ahead WEP network. Let's continue tomorrow. I need a nap!

---

### Post by chili555 on 2010-11-15
I've had my coffee and I'm ready to crack this case! How many characters does your WEP key have? Does it work seamlessly with other computers in the house? Have you tried both upper and lower-case if there are any letters in the key? We can get some clues about what's going on with:```
sudo cat /var/log/syslog | grep -i network | tail -n20
```If there is no or very little output, try:```
sudo cat /var/log/syslog.1 | grep -i network | tail -n20
```

---

### Post by ArtlessIntent on 2010-11-15
Hi there, yeah we got a bit of a time difference! it 10.29 am next day here, 4.29 where yr at. lets start on this? ill answer yr last post now.

---

### Post by ArtlessIntent on 2010-11-15
ok heres the data for the first question: 
crude@artless1:~$ sudo cat /var/log/syslog | grep -i network | tail -n20 
[sudo] password for crude: 
Nov 16 10:24:52 artless1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Nov 16 10:24:52 artless1 NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Nov 16 10:24:53 artless1 NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
Nov 16 10:24:53 artless1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Nov 16 10:24:53 artless1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Nov 16 10:24:53 artless1 NetworkManager: <info>    address 192.168.2.2
Nov 16 10:24:53 artless1 NetworkManager: <info>    prefix 24 (255.255.255.0)
Nov 16 10:24:53 artless1 NetworkManager: <info>    gateway 192.168.2.1
Nov 16 10:24:53 artless1 NetworkManager: <info>    nameserver '192.168.2.1'
Nov 16 10:24:53 artless1 NetworkManager: <info>    nameserver '192.168.1.1'
Nov 16 10:24:53 artless1 NetworkManager: <info>    domain name 'Belkin'
Nov 16 10:24:53 artless1 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Nov 16 10:24:53 artless1 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Nov 16 10:24:53 artless1 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Nov 16 10:24:54 artless1 NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Nov 16 10:24:54 artless1 NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Nov 16 10:24:54 artless1 NetworkManager: <info>  Activation (eth0) successful, device activated.
Nov 16 10:24:54 artless1 NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Nov 16 10:30:25 artless1 NetworkManager: <info>  (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Nov 16 10:30:27 artless1 NetworkManager: <info>  (eth0): carrier now ON (device state 8)


....so this looks like the info for my wired connection, eth0 , which is what im connected to now. 
ps - my WEP code is 8 characters long. Ill try the wep key in uppercase. it works on the other computers.

---

### Post by chili555 on 2010-11-15
> NetworkManager: <info> Activation ([COLOR="Red"]eth0[/COLOR]) successful, device activated.You are trying to activate your wired ethernet connection. Network Manager will disable your wireless when the wired ethernet is connected.

[https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has been managed for themPlease disconnect the ethernet cable, wait a few moments for NM to notice the change in state and try clicking the NM icon to see if you can connect. Run the test above and leave the terminal open and reconnect the ethernet cable so you can post the result.> it 10.29 am next day here, 4.29 where yr at.Yes; let's get this fixed in time for supper!

---

### Post by chili555 on 2010-11-15
> ps - my WEP code is 8 characters long.Hmmm...eight, you say?

[http://www.smallbusinesscomputing.com/webmaster/article.php/3556296/Understanding-WEP-Encryption-Bit-by-Bit.htm](http://www.smallbusinesscomputing.com/webmaster/article.php/3556296/Understanding-WEP-Encryption-Bit-by-Bit.htm)> # 40-or 64-bit ASCII WEP code has five characters
# 40- or 64-bit HEX WEP code has 10 characters
# 128-bit ASCII WEP code has 13 characters
# 128-bit HEX WEP code has 26 characters Are you sure it's WEP? We can ask the router what it is:```
sudo iwlist wlan0 scan
```

---

### Post by ArtlessIntent on 2010-11-15
result:

crude@artless1:~$ sudo cat /var/log/syslog | grep -i netowrk | tail -n20 
crude@artless1:~$ sudo cat /var/log/syslog | grep -i network | tail -n20 
Nov 16 10:50:37 artless1 NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Nov 16 10:50:37 artless1 NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Nov 16 10:50:37 artless1 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 16 10:50:37 artless1 NetworkManager: <info>  Config: set interface ap_scan to 1
Nov 16 10:50:37 artless1 NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Nov 16 10:50:37 artless1 NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Nov 16 10:50:40 artless1 NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Nov 16 10:50:40 artless1 NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Nov 16 10:50:40 artless1 NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed
Nov 16 10:50:40 artless1 NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'belkin54g'.
Nov 16 10:50:40 artless1 NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Nov 16 10:50:40 artless1 NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Nov 16 10:50:40 artless1 NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Nov 16 10:50:40 artless1 NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Nov 16 10:50:40 artless1 NetworkManager: <info>  dhclient started with pid 5426
Nov 16 10:50:40 artless1 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Nov 16 10:50:40 artless1 NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Nov 16 10:50:40 artless1 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Nov 16 10:50:40 artless1 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Nov 16 10:50:40 artless1 NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
crude@artless1:~$

---

### Post by ArtlessIntent on 2010-11-15
i got another computer in the house and tried the wep key again and for some reason it didnt work either. but it truly is the correct key. i dunnow. i wish there was a way i could check the original setting of the  key on windows (after my manual entry it resorted back to the saved wep entry) . But anyway, does it look limke it could be the key? maybe im typing it wrong or smthing.

---

### Post by ArtlessIntent on 2010-11-15
Scan completed :
          Cell 01 - Address: 00:17:3F:BD:D9:22
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-17 dBm  
                    Encryption key:on
                    ESSID:"belkin54g"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002fbc2ce7b
                    Extra: Last beacon: 3220ms ago
                    IE: Unknown: 000962656C6B696E353467
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 0406000200000000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C

---

### Post by chili555 on 2010-11-15
If one of your computers has a hard-wired connection to the router, even this one, you can go into the administration pages of the router. In the address box of Firefox, type:```
http://192.168.2.1
```You should be able to see the WEP key there.

You *do* remember the administrator's password, right? If not, we can find the manual on the web; we need to know the exact model of your Belkin.

My wife just asked when I would prefer supper be served; I said, "Very soon."

---

### Post by chili555 on 2010-11-15
Deleted.

---

### Post by ArtlessIntent on 2010-11-15
hiya!!! suppose yr eating now. ..anyways...yep got that info!! my wep key was wrong. . so close now. i have to merge the security type though, my wep is a 64bit.

---

### Post by ArtlessIntent on 2010-11-15
Hi there, WE DID IT. but man.....it so SLOW. but nevermind. thanks so much.

---

### Post by ArtlessIntent on 2010-11-15
Oh yeah, im going to delete this thread, because its got too many details about my network on it etc. that ok with you>

---

### Post by chili555 on 2010-11-15
It's Ok with me. I am not sure you can delete. You certainly can edit the posts, however.

Glad it's working!

---

### Post by grahammechanical on 2010-11-15
Well done chili555!

---

