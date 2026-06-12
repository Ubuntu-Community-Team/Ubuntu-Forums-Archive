---
title: "Wired connection intermittent with AR8152"
date: 2010-11-08
forum: Networking &amp; Wireless
---

### Post by glilco on 2010-11-08
I have a Dell Inspiron n4030 notebook and I am connecting in a wired network in my office using the Atheros Network AR8152, running Ubuntu 10.10 Maverick.

After 20 minutes aproximately, the connections stops to respond, but the status is still "connected". I can't ping the machines in my network or reach internet. The cable and the IP I am using are the same I was using in my old workstation and works fine.

If I try to send an e-mail through gmail with attached file, the connection allways reaches this scenario above.

It works fine with Windows 7.

nm-tool:
```
NetworkManager Tool

State: connected

- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        C0:CB:38:13:A4:3E

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    MULTILASER:      Infra, 00:1D:0F:A9:98:6A, Freq 2437 MHz, Rate 0 Mb/s, Strength 20 WEP


- Device: eth0  [Labtime] ------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        F0:4D:A2:D5:D6:80

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.0.218.23
    Prefix:          16 (255.255.0.0)
    Gateway:         10.0.11.11

    DNS:             200.137.221.70
```


```
ifconfig
eth0      Link encap:Ethernet  Endereço de HW f0:4d:a2:d5:d6:80  
          inet end.: 10.0.3.3  Bcast:10.0.255.255  Masc:255.255.0.0
          endereço inet6: fe80::f24d:a2ff:fed5:d680/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:587 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:587 erros:0 descartados:0 excesso:0 portadora:1
          colisões:0 txqueuelen:1000 
          RX bytes:430381 (430.3 KB) TX bytes:134786 (134.7 KB)
          IRQ:47 

eth1      Link encap:Ethernet  Endereço de HW c0:cb:38:13:a4:3e  
          endereço inet6: fe80::c2cb:38ff:fe13:a43e/64 Escopo:Link
          UP BROADCAST MULTICAST  MTU:1500  Métrica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
          IRQ:17 

lo        Link encap:Loopback Local  
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:16436  Métrica:1
          pacotes RX:354 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:354 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0 
          RX bytes:87893 (87.8 KB) TX bytes:87893 (87.8 KB)
```

```
lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
12:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)
13:00.0 Ethernet controller: Atheros Communications AR8152 v2.0 Fast Ethernet (rev c1)
```

---

### Post by uncaspi on 2010-11-08
Please post the output of sudo /sbin/iwlist scan

---

### Post by glilco on 2010-11-09
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1D:0F:A9:98:6A
                    ESSID:"MULTILASER"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:2/5  Signal level:-75 dBm  Noise level:-87 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

```

The problem is with the wired connection and not with the wireless.

---

### Post by glilco on 2010-11-10
Anybody?

---

### Post by glilco on 2010-11-10
It seems the problem occurs when I try to do any file upload. When the file is very small, the connection continues to live, but if the file is not very small, it dies.

I think it is a driver issue. How can I be certain of it and how can I report this?

---

### Post by julio prada on 2010-11-26
Hi glilco, did you solve your problem?
I want to buy a new PC but unluckily it has the AR8152

---

### Post by glilco on 2010-11-26
No, I didn't. And I have a friend who also bought a Dell n4030 and the wired connection is also intermittent. I had no more answers from this forum. :(

---

### Post by MooPi on 2010-11-26
Can you please give us the output of your ```
/etc/network/interfaces
```
While I wait I'll look into why your wireless shows as a wired connection

---

### Post by glilco on 2010-11-27
/etc/network/interfaces
```
auto lo
iface lo inet loopback

```

The problem just occurs with wired connection. Wireless works fine.

---

### Post by MooPi on 2010-11-27
Lets try something simple first. ```
gksudo gedit /etc/network/interfaces
```
 Add this to the end of the file, proof read, save and close.
```
# The primary network interface
auto eth0
iface eth0 inet dhcp
```
You may want to do a system update. I have the same network adapter and it is squirrely to say the least. Works fine after I updated my 10.10 system just after initial install.

---

### Post by Sindegra on 2010-11-29
Glilco, I have that Ethernet card as well and I just updated to the 3.6.36.1 and I so far haven't had any dropouts, (although I really only updated a few minutes ago, so who knows). I used kernelcheck to update to this kernel since it isn't in the package lists yet. ([http://kcheck.sourceforge.net/](http://kcheck.sourceforge.net/)).
It is useful for dummies like me who don't know the first thing about compiling kernels.

---

### Post by glilco on 2010-12-03
MooPi, it doesn't work because we are not using dhcp here. If I make this setup, the Network Manager is disabled?

My system is up to date and a friend bought the same notebook (Dell Inspiron n4030) and is having the same trouble in Ubuntu 10.10

---

### Post by glilco on 2010-12-03
Sindegra, I recompiled the kernel and aparently... it works! thank you guys! problem solved!

---

### Post by wijit on 2011-01-12
Hi, guys!
Sorry to say that I'm stuck with the problem. My Ubuntu does things abnormally. Here is the result of an ifconfig command:
tingit@tidellit:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr c0:cb:38:0f:85:50  
          inet addr:172.16.13.136  Bcast:172.16.15.255  Mask:255.255.248.0
          inet6 addr: fe80::c2cb:38ff:fe0f:8550/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:71170 errors:0 dropped:0 overruns:0 frame:53371
          TX packets:36760 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:74530986 (74.5 MB)  TX bytes:3756392 (3.7 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

But when looking through Edit Connection dialog I saw nothing in the "Wired" tab. And I remembered that an internet address shown in "eth0" above was broadcasted by a known wireless access point. MooPi, have you got any idea?

---

### Post by adari1 on 2011-01-13
Just wanted to say thank you so much.

I've got an Asus 1215n with the AR8152 card.. upgraded to 10.10 which broke the ethernet, and your solution worked fine!  You really made my week!

---

### Post by mascip on 2011-01-14
Hello, there, i had the same intermittent ethernet connection problem on a 1215N Asus, and a friend a mine told me to install the "compat-wireless" package. I worked perfectly: i don't have the same problem anymore.

He said the problem comes from the network chipset which sucks with Linux, and  which is strange, too: both internet and wireless use the same "wireless" driver,  which is unusual...and seem to not always work.

He said "compat-wireless" has the latest wireless driver or something like that...i don't understand everything, but it works.

Hope it can be usefull !

---

### Post by wijit on 2011-01-15
hi Sindegra and glilco.
i don't know why i'm not lucky as you were. following your path caused my system crash. it said kernel-panic and something like it could not create block on some address. however, following pytheas22 @ [http://ubuntuforums.org/showthread.php?t=1505697](http://ubuntuforums.org/showthread.php?t=1505697) solved my problem. all network interfaces are up now. my system is dell inspiron n4030.

---

### Post by wijit on 2011-01-15
hi Sindegra and glilco.
i don't know why i'm not lucky as you were. following your path caused my system crash. it said kernel-panic and something like it could not create block on some address. however, following pytheas22 @ [http://ubuntuforums.org/showthread.php?t=1505697](http://ubuntuforums.org/showthread.php?t=1505697) solved my problem. all network interfaces are up now. my system is dell inspiron n4030. however, i did not mean to say yours is no good. in fact it was because at least you solved your problems. it was me that might did something wrong. keep on doing good things. cheers!

---

### Post by wijit on 2011-01-15
hi Sindegra and glilco.
i don't know why i'm not lucky as you were. following your path caused my system crash. it said kernel-panic and something like it could not create block on some address. however, following pytheas22 @ [http://ubuntuforums.org/showthread.php?t=1505697](http://ubuntuforums.org/showthread.php?t=1505697) solved my problem. all network interfaces are up now. my system is dell inspiron n4030. however, i did not mean to say yours is no good. in fact it was because at least you solved your problems. it was me that might did something wrong. keep on doing good things. cheers!

---

### Post by sudden8 on 2012-02-11
I had the same problem - intermittent wired ethernet connection using AR8152 and linux kernel 2.6.32.  Solution provided by pytheas22 at [http://ubuntuforums.org/showthread.php?t=15056797](http://ubuntuforums.org/showthread.php?t=15056797) fixed it!
Kudos to pytheas22.

---

