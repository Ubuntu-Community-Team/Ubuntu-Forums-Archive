---
title: "Acer Revo 3700 rt3090 wireless speed/stability"
date: 2011-10-16
forum: Networking &amp; Wireless
---

### Post by ltlbkofjim on 2011-10-16
Hi
I was wondering if anybody could help me I have recently purchased an acer revo 3700 which I believe has an RaLink RT3090 802.11n wireless card. 
I have ubuntu 10.04 installed and I have been having difficulty getting wireless up and running. I have finally been able to get it up and running with the help of many existing threads but I am still have the following problems.

I can not connect to wireless n only networks and I can only seem to connect at 54Mb/s when in b/g/n mode.

I am also having issues keeping a stable connection, with random disconnects every 20 mins or so, this seems to have improved a great deal when switching routers but still getting random disconnects.

I would be greatful if anyone would be able to point me in the right direction. 

I have included the following as it seems to be frequently requested

lspci -v
```
02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
        Subsystem: Lite-On Communications Inc Device 6622
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at febf0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: rt3090
        Kernel modules: rt2860sta, rt3090sta

```

iwconfig
```
wlan0     RT2860 Wireless  ESSID:"Media"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:1C:B3:AD:C0:31
          Bit Rate=54 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=61/100  Signal level:-67 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

sudo lshw -C network
```
  *-network
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: d0:df:9a:74:e7:77
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt3090 ip=192.168.0.101 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:18 memory:febf0000-febfffff

```

Thank you

---

### Post by wildmanne39 on 2011-10-16
Hi, try this please and if it helps we will need to make it permanent.
```
sudo rmmod -f rt2860sta
```
```
sudo modprobe rt3090sta
```
Thank you

---

### Post by ltlbkofjim on 2011-10-17
Thanks for that but unfortunately it did not appear to work, all the outputs i posted before seem to be the same and I still can not connect to a wireless n only network and the b/g/n networks I can connect to still only connect at 54Mb/s.
I tried restarting the network, reconnecting, bringing the network up and bringing it down, in all combinations, before running your commands but nothing appears to have changed even though the commands did not produce any errors.
Any more ideas?

---

### Post by ltlbkofjim on 2011-10-17
I forgot to mention, I do not think it is relevant but the ubuntu install I have has no gui and on the recommendation of a different forum i use wicd-curses to connect via wireless.
Like I said it probably isnt relevant but I have been proven wrong many times before

---

### Post by wildmanne39 on 2011-10-17
Hi, the best we can do if we are lucky most likely is to get the disconnects to stop.

Please post the results of:
```
lsmod | grep rt3
```
Thank you

---

### Post by ltlbkofjim on 2011-10-17
lsmod | grep rt3

```
rt3090sta             674216  1

```

that is all that comes up, do you think wireless n is a lost cause then? Still be something if the disconnects would stop

Thanks

James

---

### Post by wildmanne39 on 2011-10-17
Hi, change your router setting n, to b,g,n, or just b,g and see if that helps the disconnects.
Thank you

---

### Post by ltlbkofjim on 2011-10-17
thanks for the reply it is currently set on b/g/n, it will not connect at all on n only and b only is not an option on this router

James

---

### Post by wildmanne39 on 2011-10-17
Hi, there are several different methods that people have used to fix getting disconnected.

First try this please:
```
sudo su
echo "blacklist rt2860sta" >> /etc/modprobe.d/blacklist.conf
exit

```
Then restart your computer and see if that helps.

If not install wicd and remove network manager completely, but not until you have installed wicd first.
Thank you

---

### Post by ltlbkofjim on 2011-10-18
Thanks for that, given it a go and seems ok so far, will keep an eye out to see if keeps the disconnects at bay over the next 24 hours.

With regards to the speed, someone mentioned to me about updating to the latest rt3090 from ralink website may enable the n speeds for me, however I didnt want to end up in a situation with no network access at all, do you know if there is a way of backing up the current version incase i cant get the updated version to work?

Thanks for all your help

James

---

### Post by wildmanne39 on 2011-10-18
Hi, the only way that I know of is to use clonezilla to clone your ubuntu system.

I believe if it does not work you just do make clean in the directory of the driver you installed then reinstall the previous driver, how did you install the driver you are using now?

An updated driver may help but I am not sure of that, so I did not want to put you through the trouble of installing a new driver from an outside source.
Thank you

---

### Post by ltlbkofjim on 2011-10-19
It was the one that was already loaded in the system which modinfo rt3090sta reveals to be version 2.1.0.0, the version on the ralink website states version 2.4.0.4.

---

### Post by wildmanne39 on 2011-10-19
Hi, alright if you compile and install the newer version you should not have any problem with it not working, and there is a chance it will give you stability and increased speed, at this point you have nothing to lose.
Thank you

---

### Post by ltlbkofjim on 2011-10-21
Well I attempted to compile the latest driver from the ralink website which is listed as 2.4.0.4, which seemed to work well but for some reason modinfo now lists it as 2.3.1.4.

```
media@XBMCLive:~$ sudo modinfo rt3090sta
filename:       /lib/modules/2.6.32-29-generic/updates/dkms/rt3090sta.ko
version:        2.3.1.4
srcversion:     48483558B9B75D793F07D19
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
depends:
vermagic:       2.6.32-29-generic SMP mod_unload modversions 586
parm:           mac:rt28xx: wireless mac addr (charp)

```

I remember I did previously try to follow a forum post relating to 2.3.1.4 but had no luck getting it working, not quite sure what I have managed to do now to get this one to load and not 2.4.0.4.
However seeing as it was loading I thought I would give it go for a day or so, it appears there are no more disconnects, however although it allows me to connect to 802.11n only networks the speed is awful on both g and n connections (worse than before) I have shown this below by running iperf on the network, I ensured the server and the client were the only two machines on the network and there were no processes running which should have a huge impact on bandwidth.
```
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.0.101 port 5001 connected with 192.168.0.11 port 49224
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-60.0 sec  39.3 MBytes  5.49 Mbits/sec
[  5] local 192.168.0.101 port 5001 connected with 192.168.0.11 port 49256
[  5]  0.0-60.1 sec  40.1 MBytes  5.61 Mbits/sec
[  4] local 192.168.0.101 port 5001 connected with 192.168.0.11 port 49284
[  4]  0.0-10.0 sec  6.90 MBytes  5.78 Mbits/sec
[  5] local 192.168.0.101 port 5001 connected with 192.168.0.11 port 49290
[  5]  0.0-10.0 sec  5.88 MBytes  4.91 Mbits/sec
[  4] local 192.168.0.101 port 5001 connected with 192.168.0.11 port 49314
[  4]  0.0-10.0 sec  6.17 MBytes  5.15 Mbits/sec
------------------------------------------------------------
Client connecting to 192.168.0.11, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  4] local 192.168.0.101 port 44699 connected with 192.168.0.11 port 5001
Waiting for server threads to complete. Interrupt again to force quit.
[  4]  0.0-10.0 sec  15.1 MBytes  12.6 Mbits/sec
media@XBMCLive:~$ iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.0.101 port 5001 connected with 192.168.0.11 port 49351
------------------------------------------------------------
Client connecting to 192.168.0.11, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  6] local 192.168.0.101 port 58025 connected with 192.168.0.11 port 5001
Waiting for server threads to complete. Interrupt again to force quit.
[ ID] Interval       Transfer     Bandwidth
[  6]  0.0-10.0 sec  5.19 MBytes  4.35 Mbits/sec
[  4]  0.0-10.1 sec  3.98 MBytes  3.31 Mbits/sec

```

After the network was this slow i found a spare netgear WNA3100 usb adapter and tried to load this with ndiswrapper, the device and driver loaded successfully and was listed in wicd and iwconfig, however would not maintain a stable connection (I presume something to do with the usb adapter competing with the internal one).

At this stage I am really unsure where to go with this I do need some form of stability, and some speed (not necessarily blazingly fast) in order to be able to stream video and music wirelessly. I know I should be using a wired connection for this but due to hardware and location constraints this is just not possible, and I have previously had a similar system running on a system with a 54mbps connection streaming a 720p video file flawlessly, so I know it should be possible.

Does anyone have any suggestions where I can go from here, with either wireless adapter??

---

### Post by ltlbkofjim on 2011-10-22
Nobody got any ideas?

---

### Post by wildmanne39 on 2011-10-23
Hi, I am out of ideas if you disabled n speed in your route to see if that would help.
Thank you

---

