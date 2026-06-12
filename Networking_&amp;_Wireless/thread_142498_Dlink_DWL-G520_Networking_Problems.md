---
title: "Dlink DWL-G520 Networking Problems"
date: 2006-03-10
forum: Networking &amp; Wireless
---

### Post by KaridaSerious on 2006-03-10
I posted the last thread in wrong part of the forum so this is the second try :)

I've installed Ubuntu a while ago and everything else works fine but my wireless isn't working.I have tried to look around the forums but none of the instructions have worked for me :(. I've followed the instructions in [http://wiki.ubuntu.com/WPAHowto](http://wiki.ubuntu.com/WPAHowto) but no use. The wireless card interacts with the router correctly but the problem is that the card doesn't receive a IP address from DHCP. When I read my routers connection log there is a mark that says my computer had connected with wireless device. I use WPA encryption. When I link my computer with RJ45 it receives IP just right. Here's some output:

ifconfig ath0:
ath0 Link encap:Ethernet HWaddr 00:11:95:91:6E:01
inet6 addr: fe80::211:95ff:fe91:6e01/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:72 errors:413 dropped:0 overruns:0 frame:413
TX packets:456 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:200
RX bytes:9488 (9.2 KiB) TX bytes:138393 (135.1 KiB)
Interrupt:16 Memory:f8d20000-f8d30000

iwconfig:
ath0 IEEE 802.11g ESSID:"xxxxx" Nickname:"xxxxxx"
Mode:Managed Frequency:2.437 GHz
Access Point: 00:13:46:AC:C5:FA
Bit Rate:36 Mb/s Tx-Power:18 dBm Sensitivity=0/3
Retry:off RTS thr:off Fragment thr:off
Power Management:off
Link Quality=34/94 Signal level=-61 dBm Noise level=-95 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

sudo lspci:
0000:00:0c.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

sudo dhclient ath0:

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/ath0/00:11:95:91:6e:01
Sending on LPF/ath0/00:11:95:91:6e:01
Sending on Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

... can you help me :)

---

### Post by Sendervictorius on 2006-03-11
My G520 works just fine with WEP and DHCP - but I haven't bothered with WPA. 

I suspect your WPA security may be the problem: your card connects to the access point, but fails the encryption - so the DHCP never runs.

If DHCP was working, in your ifconfig  you would see a line like 
inet addr:192.168.0.145  Bcast:192.168.0.255  Mask:255.255.255.0

One suggestion which might not be that helpful, but would narrow down the problem: If you can change your access point and card to WEP, (or no encryption), and it works then that suggests WPA is at fault. I have noticed quite a lot of noise about WPA - and have therefore been reluctant to try. I'll wait till Dapper comes out.

---

### Post by KaridaSerious on 2006-03-11
Hi!

I dont think that WPA is the problem because I have this computer setup for dual boot. So every time I boot into Windows it connects to the router succesfully and I'm able to surf the internet. I tried WEP encryption but It didn't work. What could be the problem?

-KaridaSerious

---

### Post by Sendervictorius on 2006-03-12
My instinct is that there is something simple that you are overlooking. But to find it requires a logical process. I would suggest getting it working with no encryption at all and with hard-wired ip addresses. Then once you have it in a working state, advance logically, one step at a time until it breaks - then you will know where the problem is. Doing anything else is the random scatter-gun approach to problem solving. Sometimes you stumble upon the solution, but that is more luck than good management.

Steps I would suggest:
1. see if your card can see your access point. Type "iwlist scan". But iwconfig is picking up the ESSID, so it should be fine.
2. set access point to no encryption, and hard-wire an ip address. Make sure your AP will let you through - no firewall restrictions, or MAC address restrictions. You should be able to have it working at this stage.
3. swap client over from fixed IP to DHCP, and make sure it still works.
4. set AP back to WEP, and configure WEP in your PC.
5. Once WEP is going, then replace WEP with WPA. 

If you can't get it working at step 2, then there is something more fundamental wrong - but I don't think so because your iwconfigs suggest that the card is working and connecting with the access point - confirmed by iwlist.

I'm not surprised WPA works with windows. The Dlink drivers supplied on the CD that came with the card were written specifically.

---

### Post by KaridaSerious on 2006-03-25
Hello!

I removed all encryption from the router and disabled DHCP. I configured the wireless device using a static IP and tried to ping the router. It only says "Operation not permitted" over and over again. I tried with sudo ping <router> and again, "Operation not permitted". I don't know what is the problem. I'm starting to lose it :D. Hey, do you know why Firestarter sais about my ath0 that it is a "unknown device"?. Thanks

KaridaSerious

EDIT1: Founded out that Firestarter blocked ath0 from sending any data to anywhere afterall. I configured firestarter to allow ath0 to send data and now everything works fine. Im so happy :D. Now, i have to configure my router because my wireless link disconnects every 6 minutes. =) thanks for help. Ubuntu Roks <3

---

