---
title: "Ethanet Card Troubles"
date: 2006-02-07
forum: Networking &amp; Wireless
---

### Post by peppermint on 2006-02-07
I posted this thread in another catogory, and a member recomended I ask this here. Sorry if im breaking any rules about posting the same thread twice.

I have recently installed ubuntu. The installation went almost smoothly, except for one point. It froze when it said “testing repositories” or something like that. I was able to get past this problem by unplugging the Internet cable from my router and starting the installation again. Now (after the install) I'm having issues with the network. The system will crash when i try to do things with my network card.

Technical info

Processor: Pentium II (333 Mhz)
Ram: 128 MB
HDD: 6 Gb
OS: Ubunto 5.10
Network: zonet zen 1200 PCMCIA card

Thanks

---

### Post by Teroedni on 2006-02-07
Your card is a pcmia card , and after what i know they are poorly supported.

But if you could get some information regarding you card , it may be possible to solve the problem.

Here is what you need to do
[LIST=1]
[*]Open Terminal
[*]Write lshw
[*]try to find the ethernet information and copy that information as accurately as you can, and post it here
[/LIST]

then a search on  [www.google.com/linux](www.google.com/linux) will tell us how other have managed to solve this problem before us:)

---

### Post by mips on 2006-02-07
Is this your card [http://www.zonetusa.com/DispProduct.asp?ProductID=67](http://www.zonetusa.com/DispProduct.asp?ProductID=67)  ?

As far as I know that card is based on Realtek Semiconductor RTL-8139 chipset so you would probably need those modules.

Does your system actually detect the card at all ???

What brand/model laptop are you using ??? It might be that the pcmcia/cardbus slot is not fully operational or you need to disable apci or apic.

---

### Post by peppermint on 2006-02-07
Teroedni : this is the relevant output from the lshw command

```

        *-pcmcia:0
             description: CardBus bridge
             product: OZ6836/6860 CardBus Controller
             vendor: O2 Micro, Inc.
             physical id: 9
             bus info: pci@00:09.0
             version: 62
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:e8000000-e8000fff irq:9
           *-network
                description: 10/100Mbps Ethernet Card
                vendor: CardBus
                physical id: 0
                slot: Socket 0
                resources: irq:9
        *-pcmcia:1
             description: CardBus bridge
             product: OZ6836/6860 CardBus Controller
             vendor: O2 Micro, Inc.
             physical id: 9.1
             bus info: pci@00:09.1
             version: 62
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:e8004000-e8004fff irq:9

     *-network
          description: Ethernet interface
          product: RTL-8139/8139C/8139C+
          vendor: Realtek Semiconductor Co., Ltd.
          physical id: 2
          bus info: pci@02:00.0
          logical name: eth0
          version: 10
          serial: 00:50:22:00:03:62
          size: 100MB/s
          capacity: 100MB/s
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
          configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.1.4 link=yes multicast=yes port=MII speed=100MB/s
          resources: ioport:4400-44ff iomemory:8000000-80001ff irq:9

```

Ive looked for the problem. A person called Martini has sussessfuly got the card to work on a debian system. [Heres a link to the page]("http://www.trenet.ee/~field/woody2.2.20idepciprob.htm"), there silution is half way down the page under "Problem no 3, No support for Zonet Zen1200a-0 PCMCIA ethernet card".

Mips: That is the card. As far as i can tell its being detected. The brand name on the laptop is Pico, but im affrade can't give you any information about the model.

---

### Post by mips on 2006-02-07
Try and follow the Debian guide you found as Ubuntu is a fork of Debian.

Let us know where you get stuck.

---

### Post by peppermint on 2006-02-07
I'm copying this into the thread so I don't need to keep referring to an external source.

[quote=Martini, http://www.trenet.ee/~field/woody2.2.20idepciprob.htm]

First off download all files located [here](http://www.trenet.ee/~field/files.htm) to some folder on your comp. (Since i myself use Debian i recomend /usr/src/modules for compiling reasons).
Then you need to get 2 packages form your distro providing site (in case of Debian visit [www.deiban.org](http://www.deiban.org/) and chose packages): Kernel-headers-KERNELNUMBER and PCMCIA source (suggest using same number of source as the cardmg currently in your system) install / unpack them to /usr/src/ (the headers go to linux folder (make urself) and pcmcia to pcmcia (also make urself)) when that’s done goto /etc/usr/modules and run make config (if error no rule to ... then ignore) , when that’s done run in same folder Makefile it will try to compile the .c files (whitch is the key of it) . In my case it just stopped when it reatched the file called ns820.c so what i did to get past of this point was: i copied one of allready compiled .o files to ns820.o ([COLOR="Red"]USERS WHO NEED THIS MODULE BE WARNED IT IS INCORRECT FILE!!!!!)[/COLOR] and then run the Makefile once more (it chekkes wether the *.o exists and if that’s the case it contiunes to next file). When it’s done run in same folder make install (you need to install make package first if you dont have it yet). 

Now the /etc/pcmcia/config file (not the config.opts as scyld.com tells it is a mistake). 
In there add these two sections:
Add this to the first lline that is not commented...

Device “realtek”
Class “network” module “cb_enabler”, “pci-scan”, “cb_shim”, “rtl8139”
And this one (scroll down to )after  three commented lines and comment ,,Ethernet adapter deffinitions ‘’

card “your cardname eg realtek 8139c” 
manfid 0x0000, 0x024c
bind “realtek”

save the file.

Restart pcmcia cardmgr service /etc/init.d/pcmcia restart and now it should identify and configure your card (makes 2 high beeps).[/quote]

The first problem is that all the links in the above are broken. Secondly, I don't know where to go to download those two packages off Ubuntu. Thirdly, I don't understand half of the terminology.

God, I feel thick.

---

### Post by mips on 2006-02-07
[QUOTE=peppermint]
God, I feel thick.[/QUOTE]

Trust me, you dont feel nearly as thick as I do after 3 bottles of red wine.

I will revisit this thread in in the morning when I'm more copus mentis.

---

### Post by peppermint on 2006-02-08
I typed RTL-8139 into Google and came across this driver

[http://www.szabilinux.hu/rtl8139/](http://www.szabilinux.hu/rtl8139/)

I think thats the right one, I don't know how to use it though.

---

### Post by mips on 2006-02-08
I dont think you have to download that. Think it is already in ubuntu.

---

### Post by mips on 2006-02-08
When your PC boots edit the boot options so **apic=off **or **apci=off**

What is the output of the **lsmod** command ?

Follow this thread and post the output of each step here up to the point where youget stuck. [http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

---

### Post by peppermint on 2006-02-09
I did apci=off and this was the output of the lsmod command...

```

Module                  Size  Used by
nls_cp437               5888  1
isofs                  32824  1
udf                    75524  0
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
pcmcia                 24584  4
apm                    19308  1
ipv6                  217408  6
af_packet              20232  2
floppy                 52692  0
irtty_sir               7808  0
sir_dev                17324  1 irtty_sir
irda                  159804  2 irtty_sir,sir_dev
crc_ccitt               2176  1 irda
pcspkr                  3652  0
rtc                    11832  0
snd_es1968             26368  1
gameport               14472  1 snd_es1968
snd_ac97_codec         72188  1 snd_es1968
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_es1968,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd_page_alloc         10120  2 snd_es1968,snd_pcm
snd_mpu401_uart         6784  1 snd_es1968
snd_rawmidi            22816  1 snd_mpu401_uart
snd_seq_device          8204  1 snd_rawmidi
8139cp                 18432  0
snd                    48644  11 snd_es1968,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
8139too                23552  0
mii                     5248  2 8139cp,8139too
soundcore               9184  1 snd
yenta_socket           22540  3
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_piix4               8336  0
i2c_core               19728  1 i2c_piix4
pci_hotplug            24628  0
intel_agp              21276  1
agpgart                32328  1 intel_agp
dm_mod                 50364  1
tsdev                   7616  0
evdev                   9088  0
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
processor              23100  0
uhci_hcd               28048  0
usbcore               104188  2 uhci_hcd
ide_cd                 36996  1
cdrom                  33952  1 ide_cd
ide_disk               16128  3
ide_generic             1664  0
piix                    9476  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,piix
unix                   24624  658
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon

```

Now for the guide ...

_Physical Layer_

```

robert@picoServer:~$ sudo mii-tool eth0
Password:
eth0: negotiated 100baseTx-FD, link ok

```

_Software Driver_

```

robert@picoServer:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:50:22:00:03:62
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:22ff:fe00:362/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2007 (1.9 KiB)  TX bytes:1719 (1.6 KiB)
          Interrupt:9 Base address:0x4400

```

_Testing the local link_

```

robert@picoServer:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
robert@picoServer:~$ ping 192.168.1.254
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.
64 bytes from  192.168.1.254: icmp_seq=1 ttl=64 time=1.50 ms

```

The system freezes there and I need to reboot. I've done it twice with the same results, apci on and off.

---

### Post by mips on 2006-02-09
```
8139cp                 18432  0
...
8139too                23552  0
mii                    5248   2 8139cp,8139too
```

I might be mistaken but it looks like two modules are being loaded for this card.
I recall seeing a thread about multiple modules being loaded for the same card and someone suggested renaming the one module.

Do a search in these forums for "rtl8139" or "8139" and scan through the posts, it should be within the first two pages of threads.

---

### Post by peppermint on 2006-02-09
I renamed 8139too.ko to 8139too.korenamed and rebooted. Once restarted the system couldnt see the card. So i undid the damage and renamed 8139cp.ko to 8139cp.korenamed. After the reboot the system can see the card but still crashed when I try to ping my router.

---

### Post by mips on 2006-02-09
](*,)   I'll have to get back to you, gonna require some reading & googling.

---

### Post by mips on 2006-02-09
What exactly does that card connect to via UTP cable, brand&model ?

---

### Post by peppermint on 2006-02-09
[QUOTE=mips]](*,)   I'll have to get back to you, gonna require some reading & googling.[/QUOTE]

ok, thanks for the help thus far. I really appreciate it :)

---

### Post by peppermint on 2006-02-09
[QUOTE=mips]What exactly does that card connect to via UTP cable, brand&model ?[/QUOTE]

the card is connected to a Peak router.

PEAK ARM914 Wireless 54Mbps Cable/DSL+4 Port Lan Router

Here is a link to the page I bought it from 
[http://www.spotonuk.com/Srchinfo~Itemcd~1250351~Frm~S~MainCat~Networking~SrchTyp~~Search~router.htm](http://www.spotonuk.com/Srchinfo~Itemcd~1250351~Frm~S~MainCat~Networking~SrchTyp~~Search~router.htm)

---

### Post by peppermint on 2006-02-10
Ive been looking on the router's control panel and Ive found something that might be causing problems. The router has a list of computers that connect to it. The list has the name of the computer, an IP address, how its connected (LAN/WLAN) and weather the IP address is dynamic with DHCP or is fixed. 192.168.1.4 has the name &#8220;unknown&#8221; next to it. although there are other devices with the name unknown. These are PDAs and such. They aren't having problems connecting to the network.

Another interesting (but probably irrelevant) point, the router is registering my duel booting laptop under its Windoze XP name and not its Fedora name under both opperating systems.

---

### Post by peppermint on 2006-02-17
Hi,
	I've tried the card in the same laptop but with fedora installed and got the same results. I also put the card into two other laptops. One running Windows 98 and the other running fedora core 4. The card worked on both computers. So is the PCMCIA slot on this computer broken? If so, can anyone recommend any wired USB ethanet devices that work?

---

### Post by mips on 2006-02-17
Try flashing your the laptop bios to a later version. Do you have windows on the laptop and does the card work under windows.

---

### Post by peppermint on 2006-02-17
The laptop used to have windows on it until around last October. The card did work on windows but the card wasn't used in the laptop at all in 2005.

I'll get back to you when I've finished looking for the bios upgrade. It seems the award website is down right now.

---

