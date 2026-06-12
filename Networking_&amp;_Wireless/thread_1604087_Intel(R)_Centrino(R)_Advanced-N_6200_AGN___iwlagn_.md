---
title: "Intel(R) Centrino(R) Advanced-N 6200 AGN  / iwlagn not connecting at N"
date: 2010-10-23
forum: Networking &amp; Wireless
---

### Post by Stolly on 2010-10-23
Hi,

I've got a Dell Studio 15 laptop with a Intel(R) Centrino(R) Advanced-N 6200 AGN wireless module.  Its being run by the iwlagn driver (in the kernel now)....it works, but only at G.  I won't use N.  When I tell my AP to use N only, it won't connect at all.

```
dmesg | grep iwl
[   14.662719] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   14.662723] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   14.662844] iwlagn 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.662885] iwlagn 0000:04:00.0: setting latency timer to 64
[   14.662970] iwlagn 0000:04:00.0: Detected Intel(R) Centrino(R) Advanced-N 6200 AGN, REV=0x74
[   14.680372] iwlagn 0000:04:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   14.680597] iwlagn 0000:04:00.0: irq 48 for MSI/MSI-X
[   14.702680] iwlagn 0000:04:00.0: loaded firmware version 9.221.4.1 build 25532
[   14.709162] phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 2203.946597] iwlagn 0000:04:00.0: ACTIVATE a non DRIVER active station id 0 addr 1c:af:f7:a8:ec:64

```

```
 sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Net2"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 1C:AF:F7:A8:EC:64   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=37/70  Signal level=-73 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Help !

---

### Post by Stolly on 2010-10-24
Anyone got one of these connecting at N speeds ?

---

### Post by joop! on 2010-10-26
> **Stolly said:**
> Anyone got one of these connecting at N speeds ?

I noticed at my computer that for some reason in **/etc/modprobe.d/intel-5300-iwlagn-disable11n.conf** N-speed for the iwlagn driver was disabled. Uncommenting the line and a reboot brought N-speed for me.

---

### Post by Fludizz on 2010-11-07
I also had trouble connecting to Wireless N networks. I have a Netgear WNR3500L running latest Tomato. I completely removed the /etc/modprobe.d/intel-5300-iwlagn-disable11n.conf file (placed it in a backup storage location) and rebooted the system. In lshw -C network it now correctly shows wireless=IEEE 802.11abgn in configuration for the card, however it could only reach the Wireless on B/G speeds...

It turned out you need to configure the WPA2 key to use AES encryption for Wireless N to work... When your AP is set to TKIP or TKIP/AES it fails to do Wireless N.

One thing I do not understand is why the wireless N is disabled by default in Ubuntu for these Intel cards?

---

### Post by allan.jones on 2010-11-08
I have a Lenovo Thinkpad T410 with Advanced-N 6200 AGN and I can't connect at N.

I tried with Ubuntu and Fedora.
My router is configured with WPA2 key and others notebooks with others OS can connect at N.

iwconfig shows wlan0: IEEE 802.11abg**[SIZE=3]n[/SIZE] **

My modprobe.d is ok and doesn't have 11n_disabled turned on.


But I only got 54Mb/s.

---

### Post by allan.jones on 2010-11-08
I found the problem!

Wireless N doesn't work if WMM is disabled.

After I configured my router with WMM enabled, everything worked

[http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2222](http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=2222)



wlan0     IEEE 802.11abgn  ESSID:"rato-fi"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 68:7F:74:1C:E3:00   
          Bit Rate=130 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by hansheijmans on 2010-11-10
I also got a Lenovo T410 with a WiFi Link 6000 Series wireless interface. Indeed enabling WMM in my router's QoS setup did the trick!

However, speeds beyond the 130 Mbps boundary don't seem possible. Could that be a compatibility issue with N-standards? My router is a Netgear WNR834Bv2.

---

### Post by dendy7h on 2010-11-13
Joop! posted:
> I noticed at my computer that for some reason in /etc/modprobe.d/intel-5300-iwlagn-disable11n.conf N-speed for the iwlagn driver was disabled. Uncommenting the line and a reboot brought N-speed for me. 

I had to comment the line and then reboot for mine to work, but I have N speed now..... Thanks Joop!! :)

```

$ cat /etc/modprobe.d/intel-5300-iwlagn-disable11n.conf 
#options iwlagn 11n_disable=1

```

---

### Post by Stolly on 2010-12-05
> **joop! said:**
> I noticed at my computer that for some reason in **/etc/modprobe.d/intel-5300-iwlagn-disable11n.conf** N-speed for the iwlagn driver was disabled. Uncommenting the line and a reboot brought N-speed for me.

Good tip, doing that connected me at N speeds but i then couldn't pass any traffic over the Wifi network......

I've got WMM enabled too on the AP....

---

### Post by Toady00 on 2010-12-19
I have an M11x R2 which I instantly replaced the wireless with the Intel Centrino 6200. I was having the same problem. After reading this post, I checked my router, and I do have WMM enabled. I then saw the /etc/modprobe.d/intel-5300-iwlagn-disable11n.conf and tried to comment it out, and my signal speed actually went down. I then tried changing the value from 1 to 0 and that completely solved my problem.

---

### Post by Stolly on 2010-12-31
Hmm interesting i'll try that

---

### Post by HankB on 2010-12-31
> **Fludizz said:**
> ...
One thing I do not understand is why the wireless N is disabled by default in Ubuntu for these Intel cards?
[https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/630748](https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/630748)

Apparently there is (or was) a bug in the Intel firmware that ships with 10.10. Is that the version of Ubuntu you're running?

I'm still running 10.04 on my T500 which is equipped with the Intel 5300 (the poster child for this problem?) I do not have that file. I recently turned on N on my router and my connection has become very unstable. I added that file and WiFi still (tries to) operate at N speeds. At times it works great. At times it loses the connection and cannot reconnect until I disable/reenable WiFi networking.

Information on this problem seems to be scattered through various posts. Is there some central location where I can get the whole story and monitor progress on a fix?

thanks,
hank

---

### Post by theozzlives on 2010-12-31
> **HankB said:**
> [https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/630748](https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/630748)

Apparently there is (or was) a bug in the Intel firmware that ships with 10.10. Is that the version of Ubuntu you're running?

I'm still running 10.04 on my T500 which is equipped with the Intel 5300 (the poster child for this problem?) I do not have that file. I recently turned on N on my router and my connection has become very unstable. I added that file and WiFi still (tries to) operate at N speeds. At times it works great. At times it loses the connection and cannot reconnect until I disable/reenable WiFi networking.

Information on this problem seems to be scattered through various posts. Is there some central location where I can get the whole story and monitor progress on a fix?

thanks,
hank

Launchpad, see if there is a bug report for this. If there is subscribe, if not file one.

---

### Post by Stolly on 2010-12-31
> **Toady00 said:**
> I have an M11x R2 which I instantly replaced the wireless with the Intel Centrino 6200. I was having the same problem. After reading this post, I checked my router, and I do have WMM enabled. I then saw the /etc/modprobe.d/intel-5300-iwlagn-disable11n.conf and tried to comment it out, and my signal speed actually went down. I then tried changing the value from 1 to 0 and that completely solved my problem.

My Hero.  I set it to 0 and now its connecting at N speeds and also passing traffic.

Thanks.

---

### Post by Stolly on 2011-01-09
Well i'm back at G speeds.  Running at N was totally unstable.  Just stopped passing traffic at random times.  Was OK for a while and then just stopped for say a minute at a time.

---

### Post by ubunoob23 on 2011-01-17
I have a Dell Studio 15 with an Intel Advanced-N 6200 AGN wireless card. The "enable wireless" is greyed out. I have tried everything that has been suggested in this thread but I still cant get it to connect to the internet. Can somebody please suggest some steps. I am new to all this and do not understand terminal commands yet.

Thanks.

---

### Post by egemenaydin on 2011-10-10
Yesterday I had to disable N mode of my card to have a stable wireless connection in Ubuntu 11.10. It is said that Kernel 3.0 supports N mode and there shouldn't be any stabilisation problems. However, in my case it is not valid. The strange thing is that I hadn't experienced such problem in 10.10 and 11.04. Therefore, I am suspicious that this is a bug of Gnome 3...

---

### Post by jackashe on 2011-11-16
I am having intermittent disconnects of my Advanced-N 6200 equipped laptop.  I did not find anything in my modprobe about disabled N, but I did find this online in my searches.  Perhaps those with the flag in there to disable followed these steps for 11.04?
[http://vxlabs.com/2011/05/15/ubuntu-11-04-natty-narwhal-annoyances-dell-e6410-with-nvs-3100m-gpu/](http://vxlabs.com/2011/05/15/ubuntu-11-04-natty-narwhal-annoyances-dell-e6410-with-nvs-3100m-gpu/)

I have WMM support enabled on my router.  But 11.10 keeps dropping the connection and sometimes does not connect again.

---

### Post by thinkux on 2012-04-28
I gave up trying to get N working on my machine. I was running 10.10 and in 11.04 and beyond wireless would not connect. I decided to disable the N functionality on my card until  I can resolve this in the future.

Running 12.04 LTS using a Centrino Advanced-N 6200 wireless card on a Thinkpad T410.

```
sudo nano /etc/modprobe.d/iwlwifi.conf
```

```
options iwlwifi 11n_disable=1
```

Save the file and restart. 

Source: [http://askubuntu.com/questions/38826/centrino-wireless-n-1000-poor-performance-on-n-network/126758#126758]("http://askubuntu.com/questions/38826/centrino-wireless-n-1000-poor-performance-on-n-network/126758#126758")

---

