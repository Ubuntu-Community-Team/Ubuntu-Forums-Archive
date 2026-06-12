---
title: "wireless on jaunty jackalope not working"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by rbkhanna on 2009-04-30
I upgraded to jaunty jackalope. Everything is working but my wireless WLAN is showing disconnected on the network connections. I have a wireless modem which is being detected. How can I connect the WLAN? It is enabled. I am a novice. Can someone help, please?

Ravi

---

### Post by pro003 on 2009-04-30
type in terminal:

```
ifconfig -a
```

If you see on the output ath0 you should do in terminal:

```
ifconfig ath0 up
```

and then

```
ifconfig ath0
```

see on the output is there any changes in bytes where is TX or RX.. If there is than your wlan is working.
Also you can install some wlan managers from synaptic and that you can find in System > Administration > Synaptic Package Manager... do the search by entering wlan or wireless and it will give you something for sure, but thats on you...

---

### Post by t0mppa on 2009-04-30
Of course ath0 only appears, if you're using an Atheros chip and MadWifi drivers. The wireless logical name could be a wide variety of other things like wlan0, wifi0, wmaster0, ra0, etc. depending on what drivers are being used. Much easier to find out when you run ```
iwconfig
```

---

### Post by agentbuzz on 2009-05-02
I, too, have just upgraded to Jaunty Jackalope. I had a problem with my AR5416-based NIC.

Try running a command such as this:
```
user@server:~$ lspci -v | grep Atheros -A 6
03:05.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
	Subsystem: D-Link System Inc Device 3a6d
	Flags: bus master, 66MHz, medium devsel, latency 168, IRQ 20
	Memory at fdef0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

```

Your object is to find the information about the wireless NIC. In my case, the card is a D-Link DWA547. Look the the kernel module that is loaded for your card. For example, I am using ath9k, the driver for the AR5008 family of Atheros chipsets.

Using the name of your own driver, instead of "ath9k", try the following commands:

```
:~$ sudo modprobe -r ath9k
:~$ sudo modprobe ath9k

```

Run the "dmesg" command. You should see a line like this at the end of the output from that command:

```
[142347.654793] wlan0: associated
```

Your logical device name might be something other than "wlan0", but your NIC should have associated with an access point if you have a wireless configuration.

If you do not have a properly configured wireless LAN, then you should use a tool such as the Network Manager that comes with Ubuntu or Wicd ( [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)) to configure your card, as pro003 has stated.

---

### Post by calicogeko on 2009-05-06
What happens if 

ath0: ERROR while getting interface flags: No such device
megar@megar-laptop:~$ 

I can't get any WiFi networks to show up at all. I'm an extreme novice and any help is appreciated.
Thanks.

---

### Post by pro003 on 2009-05-07
> **calicogeko said:**
> What happens if 

ath0: ERROR while getting interface flags: No such device
megar@megar-laptop:~$ 

I can't get any WiFi networks to show up at all. I'm an extreme novice and any help is appreciated.
Thanks.

type in terminal 

```
iwconfig 
```

and post the output.

---

### Post by Kainwolf on 2009-06-28
Hi, I have a quite different situation and I can't find something similar. I had just installed Kubuntu Jaunty Jackalope on my laptop over a Gutsy Gibbon installation where the wireless connection was working fine. Now, however, my wireless connection works fine, as long as I show the network SSID. However, as soon as I hide the SSID, the wireless network connection fails. Any ideas? Or points to a forum that I haven't yet found?
Thanks!

---

### Post by pro003 on 2009-06-28
I think that there should be an option for creating / connecting to a hidden network in kubuntu, I was using it few months ago. I am sure there is in ubuntu an option from the menu if you click on the nm applet, there is a 'connect to hidden wireless network' option.

---

### Post by Ruthless on 2009-07-01
> **pro003 said:**
> type in terminal 

```
iwconfig 
```

and post the output.



Since I'm having the same problem, I'll go ahead and post my output: (I use a Starling [System 76] netbook with Jaunty)

```
netbook:~$ iwconfig
      lo       no wireless extensions.
      eth0     no wireless extensions.
      pan0     no wireless extensions.
      wmaster0 no wireless extensions.
      wlan0    IEEE  802.11bg    ESSID:"mmmk"
           Mode:Managed Frequency:2.437 GHz Access Point:Not-Associated           
           Tx-Power=27 dBm
           Retry min limit:7 RTS thr:off Fragment thr=2352 B
           Power Management:off
           Link quality:0 Signal level:0 Noise level:0
           Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
           Tx excessive retries:0 Invalid misc:0 Missed beacon:0


```

I know the internet is working (because I'm using the same wireless signal (mmmk) on another laptop. I've already done a few different things, trying to resolve the problem for the Starling, but none have worked so far. This was the link that I posted yesterday before I found this post: [Wireless in Starling]("http://ubuntuforums.org/showthread.php?t=1200995")


Thanks for any help!

---

### Post by Crafty Kisses on 2009-07-01
> **rbkhanna said:**
> I upgraded to jaunty jackalope. Everything is working but my wireless WLAN is showing disconnected on the network connections. I have a wireless modem which is being detected. How can I connect the WLAN? It is enabled. I am a novice. Can someone help, please?

Ravi

I would like some more information. You didn't state what wireless card you have, in the Terminal run these following commands:
```
lspci
lsusb
iwconfig
ifconfig
lshw -C network
```
I also wouldn't mind seeing the following command as well:
```
route
```

---

### Post by pro003 on 2009-07-01
***Access Point:Not-Associated***  means what it means, there should be instead a MAC address for example 00:11:22:33:44:55 and then it should mean it's connected or associated.

try this in terminal:

```
sudo iwconfig wlan0 down 
sudo iwconfig wlan mode monitor
sudo iwconfig wlan0 up
```

or it may be **ath0** which you can see in the output of command

```
 sudo ifconfig -a
```

btw, do you have encryption enabled likw WEP or WPA?

---

### Post by Ruthless on 2009-07-01
Here is what I did and what it printed out. 

No, there is no encryption enabled. Also (and this might matter a whole bunch), I don't have a LAN cable handy nor do I have any way to connect via cable. It's all wireless here.

```
reh@system76-netbook:~$ sudo ifconfig wlan0 down 
reh@system76-netbook:~$ sudo iwconfig wlan0 mode monitor 
reh@system76-netbook:~$ sudo ifconfig wlan0 up 
reh@system76-netbook:~$ sudo ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 00:23:8b:aa:ff:50  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:253 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:104 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:7892 (7.8 KB)  TX bytes:7892 (7.8 KB) 

pan0      Link encap:Ethernet  HWaddr 4a:ce:86:c1:6f:8e  
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

wlan0     Link encap:UNSPEC  HWaddr 00-17-C4-76-A9-12-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:871 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:57675 (57.6 KB)  TX bytes:0 (0.0 B) 

wmaster0  Link encap:UNSPEC  HWaddr 00-17-C4-76-A9-12-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
```

---

### Post by pro003 on 2009-07-03
You see your wlan0 interface is ok, you just need to connect it to your a.p.
Do this in terminal:

```

sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "nameofyouraccesspointyouwishtoconnectto"
sudo iwconfig wlan0 mode managed
sudo iwconfig wlan0 enc off
sudo iwconfig wlan0 key off
sudo iwconfig wlan0 bit auto
sudo iwconfig wlan0 txpower auto

```

then you just type 

```
sudo iwconfig
```

and see if there is a line like 

```

wlan0     IEEE 802.11bg  ESSID:"nameofyouraccesspointyouwishtoconnectto"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:15:6D:53:7B:85   
          Bit Rate=11 Mb/s   Tx-Power=9 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality=77/100  Signal level:-68 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

of cource you dont need quotes "" in terminal.

Hope it will help you a bit.

---

### Post by Ruthless on 2009-07-05
I ended up finding a wireless connection that was at 100% signal so I could connect. As soon as I did that, I installed the newest driver for System76 then changed my network manager to wicd. 

So far, it seems to keep me connected regardless of signal strength. So maybe that's all I needed to do. We'll see.

---

