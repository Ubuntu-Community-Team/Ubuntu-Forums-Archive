---
title: "USB wifi adapter works but no browsing"
date: 2010-12-19
forum: Networking &amp; Wireless
---

### Post by Len666 on 2010-12-19
HPG62-144DX notebook, Windows 7 and considering Ubuntu. I installed 10.10 and tried to get my wifi running but that wouldn't work. I had a connection only sometimes and it broke up after 5 minutes. Once I got a webpage but annoyingly slooow.  Got the advice to update drivers and stuff. But the wifi connection is the only one I have...
 
Went back to 10.4 32-bit. Booted from CD and will keep it that way until this is sorted out. Now I see my wifi hotspots directly and I have no problem to establish a connection. The icon shows 3 bars quality. Network Tools says: Wlan1 = Realtek, Transmitted bytes xxx Received bytes yyy, no errors, link speed = 1Mbps, State = active. Looks good! 
 
The only minor thing here is that enabling/disabling my internal Atheros antanna also enables/disables my Alfa USB Wifi adapter (based on Realtek 8187) but who cares.
 
A bigger problem is: when I start Firefox it doesn't come up with a webpage. It just keeps on saying: "loading". At the bottom of the screen it keeps saying "Looking up ..." for ages. Nothing further.
 
Any thoughts? I am willing to offer lot's of popcorn for some guidance  here...:popcorn: 
 
Cheers!
Len.

---

### Post by Calimo on 2010-12-19
Hello,
To me it looks like a possible DNS issue.
Can you connect to Google with an IP address rather than by name, such as: [http://74.125.232.116/](http://74.125.232.116/) ?
If yes, what is the content of your "/etc/resolv.conf" file?

---

### Post by Len666 on 2010-12-19
> **Calimo said:**
> Hello,
To me it looks like a possible DNS issue.
Can you connect to Google with an IP address rather than by name, such as: [http://74.125.232.116/](http://74.125.232.116/) ?
If yes, what is the content of your "/etc/resolv.conf" file?
 
 
Thanks for responding!
 
I booted from cd, I chose the wifi hotspot that normally works fine under Windows 7.
I waited 2p seconds and the connection was established. Icon was showing 3 bars of quality.
 
I started Firefox that wanted to connect to the homepage, didn't work, kept saying "connecting", no time out, just nothing.
 
Then I typed the url you gave me. On the bottom it didn't say "Looking for" but "Connecting to:". After say one minute I got the "connection-problem-page" saying Time Out, the webpage is taking too long.
 
So, did this bring any light in the darkness?
 
Hpoe to hear from you.
 
Regards, Len.

---

### Post by Calimo on 2010-12-20
> **Len666 said:**
> Then I typed the url you gave me. On the bottom it didn't say "Looking for" but "Connecting to:". After say one minute I got the "connection-problem-page" saying Time Out, the webpage is taking too long.Firefox says "looking for" when it is trying to resolve the host name (such as [www.myhomepage.com](www.myhomepage.com)) into a server address (216.239.213.2). This is done with DNS queries.
It says "connecting to" when it tries to connect to the remote server (in this case 216.239.213.2).

So it's not a DNS issue if you can't connect to the IP address directly. I'm sorry I won't be able to help here. But I think if you open a console and type in```
ifconfig
``` valid with "enter" and then report the results here, other readers may help ;)

---

### Post by Len666 on 2010-12-20
> **Calimo said:**
> (...) So it's not a DNS issue if you can't connect to the IP address directly. I'm sorry I won't be able to help here. But I think if you open a console and type in```
ifconfig
``` valid with "enter" and then report the results here, other readers may help ;)
 
Thanks Calimo.
I'll do that and post the result here.
 
Len.

---

### Post by Len666 on 2010-12-20
> **Calimo said:**
> So it's not a DNS issue if you can't connect to the IP address directly. I'm sorry I won't be able to help here. But I think if you open a console and type in```
ifconfig
``` valid with "enter" and then report the results here, other readers may help ;)
 
This is the output of ifconfig. I copied it in Windows 7 so the lines lost their word wrap.
Sorry bout that. Anyone who can locate the problem in this output? And better still, know of a solution?
 
Hoping,
Len. 
 
[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] ifconfig
eth0
Link encap:Ethernet  
HWaddr c8:0a:a9:02:ba:bc
UP BROADCAST MULTICAST  
MTU:1500  Metric:1
          
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
Interrupt:31 Base address:0x6000 
lo        
Link encap:Local Loopback  
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:119 errors:0 dropped:0 overruns:0 frame:0
TX packets:119 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:9602 (9.6 KB)  
TX bytes:9602 (9.6 KB)
wlan0     
Link encap:Ethernet  HWaddr c4:17:fe:ae:4a:f8  
UP BROADCAST MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B)  
TX bytes:0 (0.0 B)
wlan1     
Link encap:Ethernet  
HWaddr 00:c0:ca:1a:1b:d1  
inet addr:192.168.99.108  
Bcast:192.168.99.255  Mask:255.255.255.0
inet6 addr: fe80::2c0:caff:fe1a:1bd1/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:48 errors:0 dropped:0 overruns:0 frame:0
TX packets:75 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:11687 (11.6 KB)  
TX bytes:9355 (9.3 KB)
[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL]

---

### Post by TBABill on 2010-12-20
Disable IPV6 in Firefox?

---

### Post by Len666 on 2010-12-20
> **TBABill said:**
> Disable IPV6 in Firefox?
 
I started from cd, got a connection.
Opened firefox and looked for the preferences regarding the network connection.
I can't find a way to disble IPV6 in Firefox.
 
I looked at the configuration details of my adapter, if that is what you mean.
when I look at these details and look under IPV6 I see "Ignore" so I guess it can't be that.
 
When I was "online but unable to browse with firefox" I tried the Ubuntu software centre in the upper left options. It started to download something (no clue what) or wanted to cause it suddenly said "in progress" but after 2 hours of looking at that turning cycle (quite symbolic) I decided I had waited long enough.
 
So, what have I got? Every now and then I have some kind of very short and terribly slow connection cause I actually see the Google.com homepage. 
 
I don't think it's Firefox. The Ubuntu Software centre uses the internet without Firefox, right? So it's something else. Maybe the driver. The icon says I'm online and gives me 3 bars of signal quality but I can't communicate with the hotspot.
 
Is there anybody in this forum who has an idea? Can I email a developer or specialist?
I'm very greatful for the time of other helpful and friendly users but I guess this problem is in another league. When I look at the amount of messages around this subject I feel an ugly sense of confirmation.
 
Otherwise I'll just have to put up with Windows for another year or so....
Would be a pity. 
 
Thanks anyway for your time and for reading my rant.
 
Len.

---

### Post by TBABill on 2010-12-20
To change IPV6 in Firefox, try > 
Make sure your connection settings are correct (e.g., Tools -> Options -> Advanced -> Network / Connection -> Settings). Additionally, disable ipv6 on Firefox Preferences, by setting the network.dns.disableIPv6 preference to true.
Type about:config in the address bar, press Enter.
Find network.dns.disableIPv6 in the list.
Right-click -> Toggle.
Restart Firefox and try again.

---

### Post by Len666 on 2010-12-21
> **TBABill said:**
> To change IPV6 in Firefox, try
 
Thanks Bill, 
 
I clicked on {Tools} in Firefox but there is no {Options}.
I see {Websearch},{Downloads}, Add-Ons}, {Error Console}, {Page Info}, {Start Private Browsing}, Clear Recent History} and {Manage Content Plug-in}.
So I guess I have another Version. I an using Ubuntu 10.4.
 
The about:config trick worked well.
I changed the value of network.dns.disableIPv6 preference in TRUE
Restarted, no difference. I had a very short contact with the start ubuntu website. I saw the page and below it said "Transferring data" but then it already had stopped.
Al the time the icon upper right is indicating I have a connection.
 
For what it's worth I threw in a few commands I read in other threads.

[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan0     IEEE 802.11bg  ESSID:"Blue_wlan"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:03:52:E3:D1:50   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=41/70  Signal level=-69 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] lsusb
Bus 002 Device 004: ID 064e:f203 Suyin Corp. 
Bus 002 Device 003: ID 0951:1603 Kingston Technology DataTraveler 1GB/2GB Pen Drive
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 004: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] 

Can you give me another hint what to try next?
 
Thanks a lot for your time.
Len.

---

