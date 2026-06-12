---
title: "HP Pavilion dv6000 BCM4311 Wired Driver Problem"
date: 2012-05-25
forum: Networking &amp; Wireless
---

### Post by motocollage on 2012-05-25
Heya, another noob here. I've been trying, but a little out of my depth here.  I apologize if this is not the appropriate thread/post/way to obtain tech assistance and moderators feel free to move this thread or reprimand me if need be.

I just acquired an old HP Pavilion dv6000 with no operating system and no USB boot options from BIOS, just cd boot. I popped in my Ubuntu 10.04 Live CD and successfully installed, HOWEVER I have run into the persistent problem of a) not being able to obtain a wired connection and thus b) not being able to install necessary drivers for, say, wireless networking.

FIrst off, I have been running 11.04 on my Acer D250 netbook and have very little experience so far with Ubuntu.

On the HP, I followed this thread: [http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)
which seemed to be helpful. I tried to install the appropriate STA driver from the CD. In Synaptic, i have marked bcmwl-kernel-source for installation, which should support my BCM4311 driver. Maybe I'm missing something here, but it seems as if it only pertains to my wireless driver, not my wired networking ability. Anyhoo, when I apply changes i receive this message:

W: Failed to fetch cdrom:[Ubuntu 10.04 LTS_Lucid Lynx_ - Release i386 (20100429)]/pool/restricked/b/bcmwl-kernel-source__5.60.48.36+bdcom-0ubuntu3_i386.deb
 Hash Sum mismatch

Of course, when I try to reboot the drivers are not applied. However, when I look for Proprietary Drivers, now i have several options: NVIDIA, B43 wireless driver, STA driver, etc.  When I try to activate, I am returned the above error.

My other obstacle is that I am currently without a home internet connection. I house sitting currently, but I would like to get this problem fixed on my own before this gig is up (and without having someone else fix it for me). Eventually, I want to upgrade to at least 11.04 and Unity, but can't do much without connecting to a network.  

Please have mercy on me, I have been trying. Any help would be appreciated. Thanks!

---

### Post by chili555 on 2012-05-25
I'm confused. Are you trying to get your wired going or wireless? Please open a terminal and run and post:```
lspci -nn | grep -e 0200 -e 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

PS - I will be away from the forum for a while. If it is wireless you want and the pci.id is indeed 14e4:4311, then check here: [http://ubuntuforums.org/showpost.php?p=11413327&postcount=11](http://ubuntuforums.org/showpost.php?p=11413327&postcount=11)

---

### Post by motocollage on 2012-05-26
Yeah, I'm confused, too! Actually, trying to get the wired network up first although the driver issue I seem to be having seems to apply to the Broadcom wireless drivers. FIrst wired, then wireless. Here you go:

```
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN 
[14e4:4311] (rev 01)
```

Thanks for the prompt response!

---

### Post by chili555 on 2012-05-26
> **motocollage said:**
> Yeah, I'm confused, too! Actually, trying to get the wired network up first although the driver issue I seem to be having seems to apply to the Broadcom wireless drivers. FIrst wired, then wireless. Here you go:

```
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN 
[14e4:4311] (rev 01)
```

Thanks for the prompt response!Very good. Just follow the procedure here: [http://ubuntuforums.org/showpost.php?p=11413327&postcount=11](http://ubuntuforums.org/showpost.php?p=11413327&postcount=11)

Once the wireless is working we'll tackle the wired.

---

### Post by motocollage on 2012-05-26
Cool, looks like wireless is up and running, though I can't test it out from this location (house sitting for someone with a wired network. will try as soon as I can at a known public wifi hotspot). For some reason, I was mistakenly under the impression that I would have to enable wired before I could tackle wireless.

As far as the commands go, ```
mkdir
``` created a new folder for the .zip file, which I copied to, right? Then with ```
 rmmod -f
``` did I remove a module from the kernel that wasn't intended to be removed? What was ssb? Was I essentially deleting old (packaged with the LIVE disc) firmware and replacing it with new?

I looked at the MAN for the commands, and I want to understand a) what the exact problem was and b) how I corrected it.

OK, what's next?

---

### Post by chili555 on 2012-05-26
> As far as the commands go,
Code:

mkdir

created a new folder for the .zip file, which I copied to, right?Exactly.> Then with
Code:

 rmmod -f

did I remove a module from the kernel that wasn't intended to be removed?You removed b43 which was crippled because it didn't have the firmware. Once you installed the firmware, you reloaded b43 which grabbed the shiny new firmware and created a usable wireless interface, as you've seen.> OK, what's next? Let's identify the wired ethernet card. We'll **L**i**S**t all the **PCI** cards and specify only the ethernet card. Please run and post:```
lspci -nn | grep 0200
```Once we know what it is (tg3??) we'll fix it up.

---

### Post by motocollage on 2012-05-27
did you mean 0280? First command returned nothing:

```
lspci -nn | grep 0200
lspci -nn | grep 0280
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

```

---

### Post by chili555 on 2012-05-27
Nope. I meant 0200, the identifier for ethernet. From my system:> chili@LAPTOP60:~$ lspci -nn | grep  0200
00:19.0 ***Ethernet*** controller [[COLOR="Red"]0200[/COLOR]]: Intel Corporation 82577LM Gigabit Network Connection [8086:10ea] (rev 06)Please run:```
lspci -nn
```Find the line that you think is the ethernet card and post it here.

---

### Post by motocollage on 2012-05-27
Ah, it looks like ```
00:14.0  Bridge [0680]:  nVidia Corporation MCP51 Ethernet 
Controller [10de:0269] (rev a3)
```

Does that help? Or should I post the entire output from **lspci -nn** so you can see? (sorry, back and forth between houses and w/o a flash drive this second...). I show no [0200] anywhere.

---

### Post by chili555 on 2012-05-27
That helps.

Ohhhhh! One of those things! That device is supposed to work with the driver *forcedeth*. Let's load it and see if we have an ethernet interface:```
sudo modprobe forcedeth
ifconfig
```Now do you have an ethernet interface eth0? Can you connect?

If so, let's load it on boot:```
sudo su
echo forcedeth >> /etc/modules
exit
```If not, let's search the message file to see why not:```
dmesg | grep forcedeth
```

---

### Post by motocollage on 2012-05-29
Sorry, I haven't been able to reply until now. No network activity that I can see. Here is what I have: ```
grandpa@grandpa-laptop:~$ sudo modprobe forcedeth
grandpa@grandpa-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:9c:f4:00  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:273376 (273.3 KB)  TX bytes:4990 (4.9 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3992 (3.9 KB)  TX bytes:3992 (3.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:ee:0a:b0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:12030 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5887 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15360200 (15.3 MB)  TX bytes:601258 (601.2 KB)

grandpa@grandpa-laptop:~$ dmesg | grep forcedeth
[    1.262328] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.262634] forcedeth 0000:00:14.0: PCI INT A -> Link[LMAC] -> GSI 19 (level, high) -> IRQ 19
[    1.262639] forcedeth 0000:00:14.0: setting latency timer to 64
[    1.781077] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:16:36:9c:f4:00
[    1.781082] forcedeth 0000:00:14.0: highdma pwrctl lnktim desc-v3
[  455.160361] forcedeth 0000:00:14.0: PCI INT A disabled
[  455.498077] forcedeth 0000:00:14.0: restoring config space at offset 0x1 (was 0xb00003, writing 0xb00007)
[  458.132507] PM: restore of drv:forcedeth dev:0000:00:14.0 complete after 517.087 msecs
[ 2368.777583] forcedeth 0000:00:14.0: restoring config space at offset 0x1 (was 0xb00003, writing 0xb00007)
[ 2371.412523] PM: restore of drv:forcedeth dev:0000:00:14.0 complete after 517.087 msecs
[ 3476.734628] forcedeth 0000:00:14.0: restoring config space at offset 0x1 (was 0xb00003, writing 0xb00007)
[ 3479.376533] PM: restore of drv:forcedeth dev:0000:00:14.0 complete after 517.074 msecs
[ 4581.172522] PM: resume of drv:forcedeth dev:0000:00:14.0 complete after 519.092 msecs
[ 4660.196491] PM: resume of drv:forcedeth dev:0000:00:14.0 complete after 519.069 msecs
[ 5044.480511] PM: resume of drv:forcedeth dev:0000:00:14.0 complete after 519.085 msecs
[ 5160.712511] PM: resume of drv:forcedeth dev:0000:00:14.0 complete after 519.079 msecs
grandpa@grandpa-laptop:~$ 
```

In the meantime, I'll see if I can use my wireless connection to update && upgrade since I haven't been able to do that until now (at a friend's on his wireless for the moment).

---

### Post by chili555 on 2012-05-29
> [    [COLOR="Red"]1.262328[/COLOR]] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.262634] forcedeth 0000:00:14.0: PCI INT A -> Link[LMAC] -> GSI 19 (level, high) -> IRQ 19
[    1.262639] forcedeth 0000:00:14.0: setting latency timer to 64
[    1.781077] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:16:36:9c:f4:00Looking at the timestamp, forcedeth is loading automagically on boot. The next time you boot, boot with the ethernet cable attached and run and post:```
dmesg | grep eth0
nm-tool
```It actually looks pretty solid!

---

### Post by motocollage on 2012-05-29
```
grandpa@grandpa-laptop:~$ dmesg | grep eth0
[    1.789087] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:16:36:9c:f4:00
[   22.152052] eth0: no IPv6 routers present
grandpa@grandpa-laptop:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        00:14:A5:EE:0A:B0

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    ATT944:          Infra, 20:E5:64:B6:95:20, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    2WIRE752:        Infra, B0:E7:54:11:4C:81, Freq 2412 MHz, Rate 54 Mb/s, Strength 61 WEP


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             disconnected
  Default:           no
  HW Address:        00:16:36:9C:F4:00

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

```

Okay, so what is happening here? Forcedeth "reverse engineered"? That sounds cool. Is this a driver that is used for network related issues, or what is it? It sounded as if you had heard of it before, but it was new to you. Is this something specific to Ubuntu or most Linux distros? And when I use **dmesg | grep _command_**, am I showing results (with grep, which I am trying to understand) that pertain to the specific _command_ that I gave? Is the red number in your last post the timestamp? 

LIke I said, out of my element here, but very interested.

---

### Post by chili555 on 2012-05-29
> Is this a driver that is used for network related issues, or what is it?forcedeth is simply Nvidia's N**force** **eth**ernet driver. Somebody reverse engineered the Windows driver evidently to make a Linux driver. It is Linux-wide, not just Ubuntu; most drivers are such. > It sounded as if you had heard of it before, but it was new to you.Google and I have heard of everything on earth. We don't see too many of these on the forum; I assume they mostly just work! The way they connect to the motherboard is a bit unique and we have to dig a bit deeper to identify them.> And when I use dmesg | grep command, am I showing results (with grep, which I am trying to understand) that pertain to the specific command that I gave?Yes. dmesg is the quickly available kernel message file. You can see the whole thing with:```
dmesg
```But we often don't want to see the whole thing, we want to see any lines with a specific thing in them and no others; for example ACPI. So we tell the terminal to read all of dmesg; then print out only the lines with ACPI in them:```
dmesg | grep ACPI
```However, ACPI may also be acpi, so we look **i**nsensitive to case:```
dmesg | grep **-i** acpi
```What we hope for is that we see an error, warning or glitch that we can fix that will help the ethernet or wireless. As a matter of fact, had you done:```
dmesg | grep b43
```...before we installed firmware, the message would have said:> b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
b43-phy0 ERROR: You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the latest firmware (version 4).> Is the red number in your last post the timestamp?
Yes, exactly. 1.26 seconds after boot, it loaded forcedeth.

I suggest you proceed with all updates and then reboot and then let's see:```
dmesg | grep eth0
```> LIke I said, out of my element here, but very interested. You will get *IN* your element if you keep learning and applying what you learn.

---

### Post by motocollage on 2012-05-30
Thanks! Your answers and expertise are extremely helpful! I was already keeping a notebook understanding pertinent terminal commands. I will have rather extensive notes after this problem is solved.

```
[ 1.793107] forcedeth 0000:00:14.0: ifname [COLOR="Red"]eth0[/COLOR], PHY OUI 0x732 @ 1, addr 
00:16:36:9c:f4:00
[ 30.840030] [COLOR="Red"]eth0:[/COLOR] no IPv6 routers present
```

This is after updates and connected to ethernet cable, directly to cable modem.

---

### Post by chili555 on 2012-05-30
> I was already keeping a notebook understanding pertinent terminal commands. I will have rather extensive notes after this problem is solved.Very smart. I kept a README text document in my home directory. When I finally figured out the best and easiest way to do something, I made notes in my README. Over the years, it became shorter as I eliminated things that became obsolete; as I was more familiar with the process, or as I found an even easier way. I copied links to forum posts, tutorials, etc. I have a folder on my desktop called *Forum* that's a brief, slender 2.0 GB! 

Your dmesg readings look pretty solid. We see no errors to fix. Please look at:```
nm-tool
```Does it report that it sees a carrier? A link? I wonder what Network Manager is doing all this time?```
sudo cat /var/log/syslog | grep -e etwork -e eth0 | tail -n20
```^^^ Pretty slick command, eh?

---

### Post by motocollage on 2012-05-30
Yes, nice (pipelining is it called?) commands! I am back at this house, switching cable from their computer to mine, and forgot my flash drive, so I will not return the output fully.

Some notable parts:

[B]State: Disconnected
Default: no

Carrier Detect: yes
Speed:  100Mb/s

Wired Properties
Carrier: on
[/B]
then after your fancy string, about 20 lines of code, stuff like 

[B]"registering new address" 
"no IPv6 routers present"
"DHCP transaction took too long, stoppping, cancelled" 
"Marking connection 'Auto eth0' invalid" 
"Activation failed, deactivating device (reason: 0)"[/B]

and so forth. Does that help any, or should I wait till I can copy/paste and transfer with my flash? What exactly are you looking for?

---

### Post by chili555 on 2012-05-30
> "[COLOR="Red"]DHCP transaction took too long, stopping, cancelled[/COLOR]"
"Marking connection 'Auto eth0' invalid"
"Activation failed, deactivating device (reason: 0)"That's probably enough. We wonder why. Anything as interesting in:```
sudo cat /var/log/syslog | grep -e forcedeth -e msi | tail -n20
```This is my favorite kind of problem; everything looks perfect...except it doesn't work.

---

### Post by motocollage on 2012-05-30
Umm....

[B]"restore of drv: forcedeth dev: 14
"restoring config space at offset 0x1 )was 0xb00003, writing 0xb00007)"
"PCI INT A -> Link[LMAC] -> GSI 20 (level, high) -> IRQ 20"
"PCI INT A disabled"
"setting latency timer to 64"
"highdma pwrctl lnktim desc-v3"[/B]

Any help?

Also, what does **tail -n20 **do and what exactly is the directory **/var/log/syslog** for?

---

### Post by chili555 on 2012-05-30
> Also, what does tail -n20 doThat means we want to read the ending instances; we don't care what happened yesterday; we care what happened last. Also, we want just the last 20 instances; not 500 or thousands.> what exactly is the directory /var/log/syslog for?syslog is a system log. Brief messages are recorded for most significant activities in the whole system, although there are separate, more specific logs kept. You can see what they are with:```
ls /var/log
```You will notice that as the logs fill up, they are transferred to log.1 and the old log.1 is transferred to log.2 and compressed with gzip. Sometimes, you may find no entries in a log; it has been archived and you should check in log.1. > "restore of drv: forcedeth dev: 14
"restoring config space at offset 0x1 )was 0xb00003, writing 0xb00007)"
"PCI INT A -> Link[LMAC] -> GSI 20 (level, high) -> IRQ 20"
"PCI INT A disabled"
"setting latency timer to 64"
"[COLOR="Red"]highdma pwrctl lnktim desc-v3[/COLOR]"I'm interested in the highlighted part; I'm Googling and suggest you do so as well. Off for the night; see you tomorrow.

---

### Post by motocollage on 2012-05-31
UPDATE: output from last few commands


**grandpa@grandpa-laptop:~$ nm-tool**

```
NetworkManager Tool

State: connecting

- Device: wlan0  [Auto 2WIRE752] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             connecting (need authentication)
  Default:           no
  HW Address:        00:14:A5:EE:0A:B0

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    2WIRE752:        Infra, B0:E7:54:11:4C:81, Freq 2412 MHz, Rate 54 Mb/s, Strength 61 WEP
    ATT944:          Infra, 20:E5:64:B6:95:20, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2


- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connecting (getting IP configuration)
  Default:           no
  HW Address:        00:16:36:9C:F4:00

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on
```

**grandpa@grandpa-laptop:~$ sudo cat /var/log/syslog | grep -e etwork -e eth0 | tail -n20**
```

May 30 17:18:23 grandpa-laptop dhclient: Listening on LPF/eth0/00:16:36:9c:f4:00
May 30 17:18:23 grandpa-laptop dhclient: Sending on   LPF/eth0/00:16:36:9c:f4:00
May 30 17:18:23 grandpa-laptop NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
May 30 17:18:24 grandpa-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
May 30 17:18:25 grandpa-laptop avahi-daemon[741]: Registering new address record for fe80::216:36ff:fe9c:f400 on eth0.*.
May 30 17:18:31 grandpa-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
May 30 17:18:34 grandpa-laptop kernel: [ 2134.664069] eth0: no IPv6 routers present
May 30 17:18:43 grandpa-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
May 30 17:18:57 grandpa-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
May 30 17:19:06 grandpa-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
May 30 17:19:09 grandpa-laptop NetworkManager: <info>  (eth0): DHCP transaction took too long, stopping it.
May 30 17:19:09 grandpa-laptop NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 2040
May 30 17:19:09 grandpa-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
May 30 17:19:09 grandpa-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) started...
May 30 17:19:09 grandpa-laptop NetworkManager: <info>  (eth0): device state change: 7 -> 9 (reason 5)
May 30 17:19:09 grandpa-laptop NetworkManager: <info>  Marking connection 'Auto eth0' invalid.
May 30 17:19:09 grandpa-laptop NetworkManager: <info>  Activation (eth0) failed.
May 30 17:19:09 grandpa-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) complete.
May 30 17:19:09 grandpa-laptop NetworkManager: <info>  (eth0): device state change: 9 -> 3 (reason 0)
May 30 17:19:09 grandpa-laptop NetworkManager: <info>  (eth0): deactivating device (reason: 0).

```

**grandpa@grandpa-laptop:~$ sudo cat /var/log/syslog | grep -e forcedeth -e msi | tail -n20**

```
May 30 08:54:07 grandpa-laptop kernel: [ 2469.640534] PM: restore of drv:forcedeth dev:0000:00:14.0 complete after 517.034 msecs
May 30 09:54:57 grandpa-laptop kernel: [ 5886.184412] forcedeth 0000:00:14.0: restoring config space at offset 0x1 (was 0xb00003, writing 0xb00007)
May 30 09:54:57 grandpa-laptop kernel: [ 5888.820520] PM: restore of drv:forcedeth dev:0000:00:14.0 complete after 517.049 msecs
May 30 10:22:58 grandpa-laptop kernel: [    1.268632] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
May 30 10:22:58 grandpa-laptop kernel: [    1.268965] forcedeth 0000:00:14.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, high) -> IRQ 20
May 30 10:22:58 grandpa-laptop kernel: [    1.268970] forcedeth 0000:00:14.0: setting latency timer to 64
May 30 10:22:58 grandpa-laptop kernel: [    1.789097] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:16:36:9c:f4:00
May 30 10:22:58 grandpa-laptop kernel: [    1.789101] forcedeth 0000:00:14.0: highdma pwrctl lnktim desc-v3
May 30 10:23:02 grandpa-laptop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'forcedeth')
May 30 16:38:24 grandpa-laptop kernel: [  189.508363] forcedeth 0000:00:14.0: PCI INT A disabled
May 30 16:38:24 grandpa-laptop kernel: [  189.864011] forcedeth 0000:00:14.0: restoring config space at offset 0x1 (was 0xb00003, writing 0xb00007)
May 30 16:38:24 grandpa-laptop kernel: [  192.496556] PM: restore of drv:forcedeth dev:0000:00:14.0 complete after 517.094 msecs
May 30 16:43:17 grandpa-laptop kernel: [    1.271822] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
May 30 16:43:17 grandpa-laptop kernel: [    1.272173] forcedeth 0000:00:14.0: PCI INT A -> Link[LMAC] -> GSI 19 (level, high) -> IRQ 19
May 30 16:43:17 grandpa-laptop kernel: [    1.272178] forcedeth 0000:00:14.0: setting latency timer to 64
May 30 16:43:17 grandpa-laptop kernel: [    1.793107] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:16:36:9c:f4:00
May 30 16:43:17 grandpa-laptop kernel: [    1.793112] [COLOR="Red"]forcedeth 0000:00:14.0: highdma pwrctl lnktim desc-v3[/COLOR]
May 30 16:43:19 grandpa-laptop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'forcedeth')
May 30 17:52:31 grandpa-laptop kernel: [ 2800.160374] forcedeth 0000:00:14.0: PCI INT A disabled
May 30 17:52:31 grandpa-laptop kernel: [ 2803.172522] PM: resume of drv:forcedeth dev:0000:00:14.0 complete after 519.106 msecs
```

---

### Post by motocollage on 2012-05-31
Google search returned nothing that I could make sense of, however you may be a different story.

Side note: I am at the 'house-sitting' house, plugged in to the same cable, directly from cable modem (no router), only this time with my Acer d250 Netbook running 11.04 and it is having the same problem.....

running **nm-tool**, under eth0

**State: connecting (getting IP configuration)** THEN
**State: disconnected**

However, it still says** yes** for carrier detect at **100 Mb/s**. 

I know this netbook's wired eth0 works. Here in a little while, I might try my HP's wired capability when I run to the university for another errand, but that is a cable that I know works. It may be that the HP connects just fine, and the problem has something to do with how it is connecting directly with the cable modem at the 'house.'

---

