---
title: "Dell Latitude D500 wireless issue."
date: 2011-05-20
forum: Networking &amp; Wireless
---

### Post by Pontster on 2011-05-20
Hello
I've only recently started using ubuntu (10.10) and running it on a relatively old laptop. It's been working fine up until the last update when the wireless has stopped connecting. When booting up normally it connected automatically but after the update it tries a few minutes and then says it can't connect. When I look at available networks I select mine enter my key and then after a few minutes it says it can't connect. The key is correct as everything else connects fine.

I've had a look at some of the other posts where people have had similar problems but none to do with this dell model which makes me reluctant to run any of the other solutions.

I've run the lspci -v | grep -i Network command and this is what comes back.
Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04).

Can anyone help or have a solution specific to this model please?

Cheers

---

### Post by chili555 on 2011-05-20
Let's do some diagnostics. Please open a terminal and run and post:```
sudo iwlist eth1 scan
dmesg | grep -e eth -e ipw
iwconfig
```Thanks.

---

### Post by Pontster on 2011-05-20
Chilli
Laptop is at home and will run it when I finish work, and then post.
Cheers

---

### Post by Pontster on 2011-05-21
Chilli here is what the commands came back with (note the dmesg l  grep -e eth -e  ipw command said invalid option - - 'e')

eth1      Scan completed : 
          Cell 01 - Address: 02:23:4E:CB:BA:CD 
                    ESSID:"BTFON" 
                    Protocol:IEEE 802.11bg 
                    Mode:Master 
                    Frequency:2.412 GHz (Channel 1) 
                    Encryption key:off 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s 
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Quality:72  Signal level:0  Noise level:0 
                    Extra: Last beacon: 252ms ago 
          Cell 02 - Address: 00:23:4E:CB:BA:CB 
                    ESSID:"BTHomeHub2-J4SS" 
                    Protocol:IEEE 802.11bg 
                    Mode:Master 
                    Frequency:2.412 GHz (Channel 1) 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s 
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Quality:71  Signal level:0  Noise level:0 
                    IE: WPA Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK 
                    Extra: Last beacon: 248ms ago 
          Cell 03 - Address: 02:23:4E:CB:BA:CC 
                    ESSID:"BTOpenzone" 
                    Protocol:IEEE 802.11bg 
                    Mode:Master 
                    Frequency:2.412 GHz (Channel 1) 
                    Encryption key:off 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s 
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Quality:65  Signal level:0  Noise level:0 
                    Extra: Last beacon: 240ms ago 

lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
eth1      IEEE 802.11b  ESSID:"BTOpenzone"  Nickname:"ipw2100" 
          Mode:Managed  Frequency:2.462 GHz  Access Point: 06:8B:5D:9C:FB:62    
          Bit Rate=11 Mb/s   Tx-Power:16 dBm    
          Retry short limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality=100/100  Signal level=-37 dBm   
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Pontster on 2011-05-21
Typo when putting in dmesg command so here is the output.

ponty@Latitude-D500:~$ dmesg | grep -e eth -e ipw
[    1.746119] e100 0000:01:08.0: eth0: addr 0xfcffe000, irq 11, MAC addr 00:0d:56:72:2e:91
[   24.493858] libipw: 802.11 data/management/control stack, git-1.1.13
[   24.493862] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   24.719264] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[   24.719271] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[   24.736105] ipw2100 0000:01:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   24.736817] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[   25.824566] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   25.865934] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1128.745618] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 1139.568260] eth1: no IPv6 routers present
[ 1527.412075] ipw2100: exit - failed to send CARD_DISABLE command
[ 1532.064080] ipw2100: exit - failed to send CARD_DISABLE command

---

### Post by chili555 on 2011-05-21
> eth1 IEEE 802.11b ESSID:"BTOpenzone" Nickname:"ipw2100"
Mode:Managed Frequency:2.462 GHz Access Point: 06:8B:5D:9C:FB:62
Bit Rate=11 Mb/s Tx-Power:16 dBm
Retry short limit:7 RTS thrff Fragment thrff
Power Managementff
Link Quality=100/100 Signal level=-37 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0It looks like it's connected to me. Do you have an IP address?```
ifconfig
```Can you reach the internet?```
ping -c3 www.google.com
```

---

### Post by Pontster on 2011-05-21
It's connected via a different network but the one I want it to connect to it doesn't this is what I can't understand.  Output below when trying to connect to my network.

udo iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 02:23:4E:CB:BA:CD
                    ESSID:"BTFON"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:72  Signal level:0  Noise level:0
                    Extra: Last beacon: 164ms ago
          Cell 02 - Address: 00:23:4E:CB:BA:CB
                    ESSID:"BTHomeHub2-J4SS"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:71  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 160ms ago
          Cell 03 - Address: 02:23:4E:CB:BA:CC
                    ESSID:"BTOpenzone"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:65  Signal level:0  Noise level:0
                    Extra: Last beacon: 168ms ago
          Cell 04 - Address: 00:8B:5D:9C:FB:62
                    ESSID:"TryAgainCA48"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:86  Signal level:0  Noise level:0
                    Extra: Last beacon: 172ms ago
          Cell 05 - Address: C0:D0:44:42:4E:61
                    ESSID:"SKY20064"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:37  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 160ms ago

ponty@Latitude-D500:~$ dmesg | grep -e eth -e ipw
[    1.746119] e100 0000:01:08.0: eth0: addr 0xfcffe000, irq 11, MAC addr 00:0d:56:72:2e:91
[   24.493858] libipw: 802.11 data/management/control stack, git-1.1.13
[   24.493862] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   24.719264] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[   24.719271] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[   24.736105] ipw2100 0000:01:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   24.736817] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[   25.824566] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   25.865934] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1128.745618] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 1139.568260] eth1: no IPv6 routers present
[ 1527.412075] ipw2100: exit - failed to send CARD_DISABLE command
[ 1532.064080] ipw2100: exit - failed to send CARD_DISABLE command
[ 2054.004185] e100 0000:01:08.0: eth0: NIC Link is Up 100 Mbps Full Duplex
[ 2054.004450] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2056.004339] e100 0000:01:08.0: eth0: NIC Link is Down
[ 2064.920045] eth0: no IPv6 routers present
ponty@Latitude-D500:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"TryAgainCA48"  Nickname:"ipw2100"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:8B:5D:9C:FB:62   
          Bit Rate=11 Mb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=99/100  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:2

---

### Post by chili555 on 2011-05-21
> eth1 IEEE 802.11b ESSID:"TryAgainCA48" Nickname:"ipw2100"
Mode:Managed Frequency:2.462 GHz Access Point: 00:8B:5D:9C:FB:62
Bit Rate=11 Mb/s Tx-Power:16 dBm
Retry short limit:7 RTS thr:off Fragment thr:off
Power Management:on
Link Quality=99/100 Signal level=-53 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:2It still looks like you are connected. Are you saying that TryAgainCA48 is not your network?

---

### Post by Pontster on 2011-05-21
Yeah that's the one.

---

### Post by chili555 on 2011-05-21
Meaning what? That you are connected and all is well with the world?

---

### Post by Pontster on 2011-05-21
Apologies chilli, after reading your previous reply again I see the word not!!!!
TryAgainCA48 is my network. Sorry.

---

### Post by Pontster on 2011-05-23
Hi Chilli
I've just reinstalled ubuntu and I still can't connect to my network.
Have you got any ideas.
Cheers

---

### Post by Pontster on 2011-05-23
Chilli I found another thread to do with a Dell D500 and ran the commands you said to run in that, output below:

ponty@ponty-Latitude-D500:~$ sudo modprobe ipw2100
[sudo] password for ponty: 
ponty@ponty-Latitude-D500:~$ sudo ifconfig eth1 up
ponty@ponty-Latitude-D500:~$ sudo cat /var/log/messages | grep ipw
May 23 20:24:54 ponty-Latitude-D500 kernel: [    8.935374] libipw: 802.11 data/management/control stack, git-1.1.13
May 23 20:24:54 ponty-Latitude-D500 kernel: [    8.935381] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
May 23 20:24:54 ponty-Latitude-D500 kernel: [    9.308232] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
May 23 20:24:54 ponty-Latitude-D500 kernel: [    9.308240] ipw2100: Copyright(c) 2003-2006 Intel Corporation
May 23 20:24:54 ponty-Latitude-D500 kernel: [    9.319261] ipw2100 0000:01:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
May 23 20:24:54 ponty-Latitude-D500 kernel: [    9.319957] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection

---

### Post by chili555 on 2011-05-23
So far, your readings look perfect. Does it try to connect? Do you see networks when you click the Network Manager icon?

---

### Post by Pontster on 2011-05-23
Yeah it tries to connect automatically when i switch on then after a few minutes a window pops up asking for the network key. This already filled in and if I click the show key box it shows that the key is correct.

---

### Post by chili555 on 2011-05-23
Let's try a temporary fix; if it works, we'll need to write one file to make it permanent:```
sudo ifconfig eth1 down
sudo rmmod -f ipw2100
sudo modprobe ipw2100 associate=1
sudo ifconfig eth1 up
```Is it any better?

---

### Post by Pontster on 2011-05-23
Unfortunately not.

---

### Post by chili555 on 2011-05-23
Is this your network?> Cell 04 - Address: 00:8B:5D:9C:FB:62
ESSID:"TryAgainCA48"
Protocol:IEEE 802.11bg
Mode:Master
Frequency:2.462 GHz (Channel 11)
Encryption key:on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
48 Mb/s; 54 Mb/s
Quality:86 Signal level:0 Noise level:0
Extra: Last beacon: 172ms ago
Cell 05 - Address: C0:D0:44:42:4E:61It looks like it has WEP encryption. Is that correct? How many characters are in your key? 5, 13, 10 or 26?

---

### Post by Pontster on 2011-05-23
Yes that's correct and it's 10

---

### Post by chili555 on 2011-05-23
Please run and post:```
iwconfig
sudo tail -n15 /var/log/syslog
```We are looking for what NM is doing as you try to connect. If the second command produces little or no output, please try:```
sudo tail -n15 /var/log/syslog.1
```

---

### Post by Pontster on 2011-05-23
ponty@ponty-Latitude-D500:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ponty@ponty-Latitude-D500:~$ sudo tail -n15 /var/log/syslog
[sudo] password for ponty: 
May 23 21:50:54 ponty-Latitude-D500 kernel: [ 1912.748082] usb 2-2: device descriptor read/64, error -71
May 23 21:50:54 ponty-Latitude-D500 kernel: [ 1912.964062] usb 2-2: new full speed USB device using uhci_hcd and address 12
May 23 21:50:54 ponty-Latitude-D500 kernel: [ 1913.084085] usb 2-2: device descriptor read/64, error -71
May 23 21:50:54 ponty-Latitude-D500 kernel: [ 1913.308111] usb 2-2: device descriptor read/64, error -71
May 23 21:50:54 ponty-Latitude-D500 kernel: [ 1913.524096] usb 2-2: new full speed USB device using uhci_hcd and address 13
May 23 21:50:55 ponty-Latitude-D500 kernel: [ 1913.932074] usb 2-2: device not accepting address 13, error -71
May 23 21:50:55 ponty-Latitude-D500 kernel: [ 1914.044072] usb 2-2: new full speed USB device using uhci_hcd and address 14
May 23 21:50:55 ponty-Latitude-D500 kernel: [ 1914.452072] usb 2-2: device not accepting address 14, error -71
May 23 21:50:55 ponty-Latitude-D500 kernel: [ 1914.452100] hub 2-0:1.0: unable to enumerate USB device on port 2
May 23 21:50:56 ponty-Latitude-D500 kernel: [ 1915.384078] usb 2-2: new full speed USB device using uhci_hcd and address 15
May 23 21:50:56 ponty-Latitude-D500 bluetoothd[1802]: HCI dev 0 registered
May 23 21:50:57 ponty-Latitude-D500 bluetoothd[1802]: HCI dev 0 up
May 23 21:50:57 ponty-Latitude-D500 bluetoothd[1802]: Starting security manager 0
May 23 21:50:57 ponty-Latitude-D500 bluetoothd[1802]: ioctl(HCIUNBLOCKADDR): Invalid argument (22)
May 23 21:50:57 ponty-Latitude-D500 bluetoothd[1802]: Adapter /org/bluez/1801/hci0 has been enabled

---

### Post by chili555 on 2011-05-23
Oops! We missed the attempt to connect. Please be sure any ethernet cable is detached, try to connect and then run:```
sudo cat /var/log/syslog | grep Network | tail -n15
```

---

### Post by Pontster on 2011-05-23
ponty@ponty-Latitude-D500:~$ sudo cat /var/log/syslog | grep Network | tail -n15May 23 21:58:42 ponty-Latitude-D500 NetworkManager[769]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
May 23 21:58:42 ponty-Latitude-D500 NetworkManager[769]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
May 23 21:58:42 ponty-Latitude-D500 NetworkManager[769]: <info> (eth1): device state change: 5 -> 7 (reason 0)
May 23 21:58:42 ponty-Latitude-D500 NetworkManager[769]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
May 23 21:58:42 ponty-Latitude-D500 NetworkManager[769]: <info> dhclient started with pid 2031
May 23 21:58:42 ponty-Latitude-D500 NetworkManager[769]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
May 23 21:58:42 ponty-Latitude-D500 NetworkManager[769]: <info> (eth1): DHCPv4 state changed nbi -> preinit
May 23 21:59:28 ponty-Latitude-D500 NetworkManager[769]: <warn> (eth1): DHCPv4 request timed out.
May 23 21:59:28 ponty-Latitude-D500 NetworkManager[769]: <info> (eth1): canceled DHCP transaction, DHCP client pid 2031
May 23 21:59:28 ponty-Latitude-D500 NetworkManager[769]: <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
May 23 21:59:28 ponty-Latitude-D500 NetworkManager[769]: <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout) started...
May 23 21:59:28 ponty-Latitude-D500 NetworkManager[769]: <warn> Activation (eth1/wireless): could not get IP configuration for connection 'Auto TryAgainCA48'.
May 23 21:59:28 ponty-Latitude-D500 NetworkManager[769]: <info> (eth1): device state change: 7 -> 6 (reason 0)
May 23 21:59:28 ponty-Latitude-D500 NetworkManager[769]: <info> Activation (eth1/wireless): asking for new secrets
May 23 21:59:28 ponty-Latitude-D500 NetworkManager[769]: <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout) complete.

---

### Post by chili555 on 2011-05-23
I'm googling a couple of things. While I look, is your laptop plugged in to the wall or not? If not, will you plug it in and try to connect?

---

### Post by Pontster on 2011-05-23
I'm plugged in at the moment and have tried unplugged.

---

### Post by chili555 on 2011-05-23
This is from your *dmesg*:> [ 25.865934] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1128.745618] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 1139.568260] eth1: no IPv6 routers present
[ 1527.412075] [COLOR="Red"]ipw2100: exit - failed to send CARD_DISABLE command[/COLOR]
[ 1532.064080] [COLOR="Red"]ipw2100: exit - failed to send CARD_DISABLE command[/COLOR]This is what I am worried about now and I'm Googling. But first a bit of supper and a few tranquilizers! I'll be back later. You might Google, too.

---

### Post by Pontster on 2011-05-23
Ok cheers Chilli, getting late over here so i'm of for a sleep and be back tomorrow to see what you managed to find. All I found when googling what you posted was this thread.
Cheers.

---

### Post by chili555 on 2011-05-23
My favorite kind of problem: everything looks perfect except it just doesn't work.

Since NM times out trying for a DHCP lease, we might try a static IP address. Do you know your gateway? You can learn these details from another computer on the network. Click the NM icon and Edit Connections. Select Wireless and click Edit. Change Automatic to Manual and fill in the details as I've suggested attached. Of course, substitute details appropriate for your network. Then click on your network and try to connect.

---

### Post by Pontster on 2011-05-24
Hi Chilli tried that and still won't connect..

Edit: Just tried connecting again and it has established a connection to the router.  Only issue now is that it can't find any websites.

---

### Post by chili555 on 2011-05-24
Let's see:```
cat /etc/resolv.conf
ping -c3 74.125.47.106
```Thanks.

---

### Post by Pontster on 2011-05-24
ponty@ponty-Latitude-D500:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 62.6.40.170
ponty@ponty-Latitude-D500:~$ ping -c3 74.125.47.106
PING 74.125.47.106 (74.125.47.106) 56(84) bytes of data.
From 86.159.191.114 icmp_seq=2 Destination Host Unreachable
From 86.159.191.114 icmp_seq=3 Destination Host Unreachable

--- 74.125.47.106 ping statistics ---
3 packets transmitted, 0 received, +2 errors, 100% packet loss, time 1999ms
pipe 2

---

### Post by Pontster on 2011-05-24
Chilli, sussed it.
Connected via the wired connection and copied all the info from there and now its working.
Should I try pinging again.

---

### Post by Pontster on 2011-05-24
ponty@ponty-Latitude-D500:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.1.254
ponty@ponty-Latitude-D500:~$ ping -c3 74.125.47.106
PING 74.125.47.106 (74.125.47.106) 56(84) bytes of data.
64 bytes from 74.125.47.106: icmp_req=1 ttl=49 time=120 ms
64 bytes from 74.125.47.106: icmp_req=2 ttl=49 time=121 ms
64 bytes from 74.125.47.106: icmp_req=3 ttl=49 time=118 ms

--- 74.125.47.106 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 118.501/119.960/121.022/1.139 ms
ponty@ponty-Latitude-D500:~$

---

### Post by chili555 on 2011-05-24
Looks awesome so far. Now can you reach webpages?

---

### Post by Pontster on 2011-05-24
Yeah I can, there's life in the old dog yet, just need some more ram now to make it a bit more zippy..

---

### Post by Pontster on 2011-05-24
Hey Chilli thanks so much for all your help over the last few days.
Cheers

---

### Post by chili555 on 2011-05-24
Glad to help. Call on us again if we can help further.

---

