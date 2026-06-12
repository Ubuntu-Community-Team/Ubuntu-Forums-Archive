---
title: "Can I Haz Networking?"
date: 2012-04-29
forum: Networking &amp; Wireless
---

### Post by derpishi on 2012-04-29
I am having issues with networking after installing 12.04. I dual boot Vista, and it works there. I reset my router, so it is not there. Here are some outputs from 

lspci -nn | grep 0280
lsusb
arch
iwconfig

> mvyvoda@Vyvoda-Laptock:~$ lspci -nn | grep 0208
mvyvoda@Vyvoda-Laptock:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
mvyvoda@Vyvoda-Laptock:~$ arch
i686
mvyvoda@Vyvoda-Laptock:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"VyvodaView"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 4C:E6:76:3E:C3:20   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:14   Missed beacon:0

eth0      no wireless extensions.

Thanks for the suggestions...

---

### Post by chili555 on 2012-04-29
I asked for:> lspci -nn | grep 0[COLOR="Red"]280[/COLOR]...but you ran:> mvyvoda@Vyvoda-Laptock:~$ lspci -nn | grep 0[COLOR="Red"]208[/COLOR]Also, I see:> wlan0 IEEE 802.11abg [COLOR="Red"]ESSID:"VyvodaView"[/COLOR]
Mode:Managed Frequency:2.437 GHz [COLOR="Red"]Access Point: 4C:E6:76:3E:C3:20[/COLOR]
[COLOR="Red"]Bit Rate=54 Mb/s[/COLOR] Tx-Power=15 dBm
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management:off
Link Quality=49/70 Signal level=-61 dBm It looks like you are connected perfectly well. What is your problem?

---

### Post by derpishi on 2012-04-29
> **chili555 said:**
> I asked for:...but you ran:Also, I see:It looks like you are connected perfectly well. What is your problem?

lspci -nn | 0280 returns:

> 06:00.0 Network Controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02) 

I can not get on the internet, and it says that it is disconnected in the gui network manager...

---

### Post by derpishi on 2012-04-29
> **chili555 said:**
> I asked for:...but you ran:Also, I see:It looks like you are connected perfectly well. What is your problem?

Now iwconfig says:

> mvyvoda@Vyvoda-Laptock:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.



---

### Post by chili555 on 2012-04-29
Please let us see:```
rfkill list all
dmesg | grep iwl
```Thanks.

---

### Post by derpishi on 2012-04-29
> **chili555 said:**
> Please let us see:```
rfkill list all
dmesg | grep iwl
```Thanks.

here you are sir:

> mvyvoda@Vyvoda-Laptock:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
mvyvoda@Vyvoda-Laptock:~$ dmesg | grep iwl
[   27.006127] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   27.006131] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   27.006204] iwl3945 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   27.006220] iwl3945 0000:06:00.0: setting latency timer to 64
[   27.077789] iwl3945 0000:06:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   27.077795] iwl3945 0000:06:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   27.077966] iwl3945 0000:06:00.0: irq 44 for MSI/MSI-X
[   27.179503] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   27.742167] iwl3945 0000:06:00.0: loaded firmware version 15.32.2.9



---

### Post by chili555 on 2012-04-29
I think you have the same issue as this guy and I need the same information, please: [http://ubuntuforums.org/showpost.php?p=11887984&postcount=24](http://ubuntuforums.org/showpost.php?p=11887984&postcount=24)

---

### Post by derpishi on 2012-04-29
> **chili555 said:**
> I think you have the same issue as this guy and I need the same information, please: [http://ubuntuforums.org/showpost.php?p=11887984&postcount=24](http://ubuntuforums.org/showpost.php?p=11887984&postcount=24)

i just changed that settings to "ignore" and restarted. i also disabled that feature on my router. that didn't do the trick. any other suggestions?

here is the output of the commands:

```
mvyvoda@Vyvoda-Laptock:~$ cat /etc/resolvconf/interface-order 
# interface-order(5)
lo.inet*
lo.dnsmasq
lo.pdnsd
lo.!(pdns|pdns-recursor)
lo
tun*
tap*
hso*
em+([0-9])?(_+([0-9]))*
p+([0-9])p+([0-9])?(_+([0-9]))*
eth*
ath*
wlan*
ppp*
*
mvyvoda@Vyvoda-Laptock:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	Vyvoda-Laptock

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
mvyvoda@Vyvoda-Laptock:~$ 


```

---

### Post by oldgeekster on 2012-04-29
> **chili555 said:**
> I think you have the same issue as this guy and I need the same information, please: [http://ubuntuforums.org/showpost.php?p=11887984&postcount=24](http://ubuntuforums.org/showpost.php?p=11887984&postcount=24)
Sometimes its just the simple stuff.  For the first time in a LONG time yesterday I elected to attempt the "online Upgrade" path to 12.04 rather than doing a complete new install. Everything went well, (although slow - got some aging equipment here), until the reboot phase.  After the system came back up I couldn't seem to connect to my old wifi router although I KNEW I was putting in the right password.

Long story short - right clicked on network connections and selected "Edit Connections". Worked my way through Wifi and the specific network name I was attempting to connect to - hit edit - sure enough under the Wireless Security tab, found my key was missing. (Yeah, still running WEP - again my stuff is old).

Guess my point is that I "could" have jumped on the router itself, resetting/etc., but elected to assure the old notebook was properly set up first - and sure enough it wasn't. The WEP key was simply "lost" during the upgrade process.  It wouldn't have happened with a fresh install because I would have had to do that part of the setup anyway. :D

---

### Post by chili555 on 2012-04-29
> **derpishi said:**
> i just changed that settings to "ignore" and restarted. i also disabled that feature on my router. that didn't do the trick. any other suggestions?Yes, please. Same guy here: 
[http://ubuntuforums.org/showpost.php?p=11888119&postcount=29](http://ubuntuforums.org/showpost.php?p=11888119&postcount=29)

Your prior readings look fine so far.

---

### Post by derpishi on 2012-04-30
> **chili555 said:**
> Yes, please. Same guy here: 
[http://ubuntuforums.org/showpost.php?p=11888119&postcount=29](http://ubuntuforums.org/showpost.php?p=11888119&postcount=29)

Your prior readings look fine so far.

Hey Chili, i appreciate your help. I am at a hotel now, and can connect just fine. however, i still can not connect to the home network you have been helping me with. 

i am at a loss now. is it the router settings? i factory-defaulted them. can you help me to confirm it is not my ubuntu machine? why can i connect to vista partition?

thanks again. i appreciate your time and energy.

---

### Post by chili555 on 2012-04-30
When you get back home, please try:```
sudo modprobe -r iwl3945
sudo modprobe iwl3945 swcrypto=0
```If it works and you connect, we can tweak one file to make it persistent.

If not, please let us see:```
sudo iwist wlan0 scan
```Thanks.

---

### Post by derpishi on 2012-05-02
> **chili555 said:**
> When you get back home, please try:```
sudo modprobe -r iwl3945
sudo modprobe iwl3945 swcrypto=0
```If it works and you connect, we can tweak one file to make it persistent.

If not, please let us see:```
sudo iwist wlan0 scan
```Thanks.

I am back and the problem still exists with my computer. here is the code:

```
mvyvoda@Vyvoda-Laptock:~$ sudo modprobe -r iwl3945
[sudo] password for mvyvoda: 
mvyvoda@Vyvoda-Laptock:~$ sudo modprobe iwl3945 swcrypto=0 
```

It did not connect

```
mvyvoda@Vyvoda-Laptock:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Device or resource busy 
mvyvoda@Vyvoda-Laptock:~$
```

Whatcha think?

---

### Post by chili555 on 2012-05-02
> wlan0     Interface doesn't support scanning : [COLOR="Red"]Device or resource busy[/COLOR] Interesting. Let's have another look:```
iwconfig
dmesg | grep iwl
rfkill list all
```Thanks.

---

### Post by derpishi on 2012-05-02
> **chili555 said:**
> Interesting. Let's have another look:```
iwconfig
dmesg | grep iwl
rfkill list all
```Thanks.

I figured it out. It *was* my router settings. In an effort to increase my security (after a hacker breach) I was filtering WAN NAT redirection. This was the cause of my Android phone and Ubuntu laptop not allowing me to connect to DHCP. Apparently Linux and Mac user can not connect with these settings enabled. 

I am using a Buffalo Router (G3000NH) with DD-WRT firmware (build 14998). 

Chili555. You have been so nice to help try to figure out my problem. Thanks so much! Case Closed.

---

