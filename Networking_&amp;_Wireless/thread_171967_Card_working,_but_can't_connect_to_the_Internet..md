---
title: "Card working, but can't connect to the Internet."
date: 2006-05-07
forum: Networking &amp; Wireless
---

### Post by Durito on 2006-05-07
After a little thread hunting, I got my ADM8211 chipset card up and running using ndiswrapper and the Windows drivers from SMC. It seems to be working flawlessly, and the network connection icon in the upper right registers that it's merrily sending packages to and fro. Unforunately, when I try to go online I'm told that it can't find the site. Do I have something set up wrong? I can ping my Local Loopback, but can't find an IP for the coffeeshop's wireless router. Using the same card in W2K I have no problems. Here is the information returned in the terminal:

iwconfig returns:
lo        no wireless extensions.

eth0      IEEE 802.11b  ESSID:"FremontCoffee.net"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:11:50:2A:79:39
          Bit Rate:11 Mb/s   Tx-Power:38 dBm
          Retry limit:3   RTS thr:off   Fragment thr:off
          Link Quality:38  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:32  Invalid misc:6   Missed beacon:0

sit0      no wireless extensions.

ifconfig returns:
eth0      Link encap:Ethernet  HWaddr 00:04:E2:7F:D1:66
          inet6 addr: fe80::204:e2ff:fe7f:d166/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5054 errors:141 dropped:0 overruns:0 frame:140
          TX packets:1350 errors:33 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:554124 (541.1 KiB)  TX bytes:114351 (111.6 KiB)
          Interrupt:11

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:46033 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46033 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3300511 (3.1 MiB)  TX bytes:3300511 (3.1 MiB)


iwlist returns:
eth0      Scan completed :
          Cell 01 - Address: 00:11:50:2A:79:39
                    ESSID:"FremontCoffee.net"
                    Mode:Master
                    Channel:6
                    Quality:31  Signal level:0  Noise level:0
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
          Cell 02 - Address: 02:E0:2A:BC:D1:50
                    ESSID:"beta"
                    Mode:Ad-Hoc
                    Channel:1
                    Quality:39  Signal level:0  Noise level:0
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s

dhclient returns:
Listening on LPF/eth0/00:04:e2:7f:d1:66
Sending on   LPF/eth0/00:04:e2:7f:d1:66
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Is DHCP not working? I'm running 5.10 on a Thinkpad 600e.

---

### Post by harisund on 2006-05-07
Yes, your DHCP client doesn't know what essid to connect. 
Execute the following and check if it works. 
```

sudo iwconfig eth0 mode managed
sudo iwconfig eth0 essid <enter_name_of_wireless_network_here>
sudo iwconfig eth0 key <enter_wep_key_if_you_have_one>
sudo dhclient eth0
```

Of course, in the second line you will not be entering any of '<' or '.' or anything in between, but rather the actual name of the wireless network. 

And ignore the third line if you are connecting to a network that doesnt' have a wep key in the first place

Your card can, at the place you were writing, see 2 wireless networks, Beta and FreemontCoffee.net. You will have to mention what to connect to, and that is done in the scond line.

---

### Post by Durito on 2006-05-07
[QUOTE=harisund]Yes, your DHCP client doesn't know what essid to connect. 
Execute the following and check if it works. 
```

sudo iwconfig eth0 mode managed
sudo iwconfig eth0 essid <enter_name_of_wireless_network_here>
sudo iwconfig eth0 key <enter_wep_key_if_you_have_one>
sudo dhclient eth0
``` [/QUOTE]

I specified managed mode and ESSID, but I'm still getting the same results from dhclient: no DHCP offers and no working leases in the persistent database.

The wireless at this coffee shop is a little quirky/unstable, but I was able to connect when using SuSE 10.0 a couple months ago. Thanks for the help,

D.

---

### Post by harisund on 2006-05-07
Hmm.. I am sorry I think I am really lost here, and would require the help of someone else now. 

Generally when what you are describing happens to me I switch off my machine and let my pcmcia wireless card cool for a while. Then I make sure the wireless network is working (at home, that is). 

But if you are otherwise able to connect and not using the above mntioned procedure (which is what I use) I am afraid I am not going to be of any help :(

Sorry !

---

### Post by decaturcomp on 2006-05-22
Hi,
I'm really new to this but had the same problem as above. (No DHCP offers) and also saw in the log "no working leases in persistant database"

I tried Harisund's excellent idea above but kept getting "eth0 operation is not supported"

I managed to resolve the situation by going to system/networking/networking and changing the setting at the bottom from default gateway device wlan0 to eth0.
I don't know why that worked but it did. Now I can get online again.

Incidentally, I knew my network was not down because I'm dual booting w/ xp and that is connecting. FWIW, the connection was working when I first installed Dapper flight 7 but broke after getting the updates.

---

### Post by decaturcomp on 2006-05-22
[QUOTE=decaturcomp]Hi,
I'm really new to this but had the same problem as above. (No DHCP offers) and also saw in the log "no working leases in persistant database"

I tried Harrisund's excellent idea above but kept getting "eth0 operation is not supported"

I managed to resolve the situation by going to system/networking/networking and changing the setting at the bottom from default gateway device wlan0 to eth0.
I don't know why that worked but it did. Now I can get online again.

Incidentally, I knew my network was not down because I'm dual booting w/ xp and that is connecting. FWIW, the connection was working when I first installed Dapper flight 7 but broke after getting the updates.[/QUOTE]

corrected above, it was Harrisund's fix I tried.

---

### Post by avirnig on 2006-05-22
one other thing you should check:

do you have both your wired and wireless cards enabled in the network applet? if you do, that could be the problem. i have the same problems with internet not working if i have them both enabled, but when i disable the wired interface (usually eth0) then my wireless magically works, if i re-enable the wired interface again after that, it stops working again. vice-versa is also true. if i have both enabled internet stops working, but if i disable wireless, then the wired works again. 

kinda wierd, but hey what can ya do.

---

### Post by nccsa186 on 2006-05-26
Avirnig,
here's the trick to using two network cards. We'll call them wa0 (wireless) and eth0 (wired) without losing internet connectivity in ubuntu
given that your wireless router's ip is 198.162.1.99:
1. set wa0 to 198.162.1.1
2. set wa0's subnet to 255.255.255.0
3. set wa0's gateway to 198.162.1.99
4. set eth0 to 198.162.2.1 (NOT 1.2)
5. set eth0's subnet to 255.255.255.0
6. set eth0's default gateway to empty string
7. be sure that ra0 is the default gateway device
i am on breezy and did everything in system > administration > network

---

