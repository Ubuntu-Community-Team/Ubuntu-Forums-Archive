---
title: "Low signal strength"
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by brandonhon on 2008-12-15
I just installed Intrepid and noticed that my wireless signal is really poor. My antenna is within a foot of the accesspoint. I have an Asus P5W DH Deluxe with on-board wlan. Any suggestions? New driver maybe?

---

### Post by andreasis on 2008-12-15
hi brandonhon,

please post what wireless card/driver you are using. You should be able to find that information in:

lspci
lsmod

---

### Post by brandonhon on 2008-12-16
ok so i attached my lsmod and lspci because i don't see my wireless card

---

### Post by joebeasley on 2008-12-17
I have the same issue. Only shows up to 10% with one bar, but my connection works fine.  AP is 6 feet away behind a wall.  This is a fresh 64bit Ibex install on an AMD with 2Gigs ram.  

Please post if you find a solution.  

7.10 showed a 80-98% connection.

---

### Post by brandonhon on 2008-12-18
I have a feeling it is the default driver. I just don't know which one to change it to or try. I am also kind of a newbie at this.

---

### Post by brandonhon on 2008-12-19
ok, so i just tried the livecd of mint based on Hardy and i am now getting full signal strength through my wifi. does anyone know if the driver for Hardy is a different version then the one for intrepid? if not how would i find out?

by the way it is the rtl8187 driver i am referring too.

---

### Post by almikul on 2008-12-20
I have the same issue with Intrepid. Hardy indeed uses a different version of rtl8187. My router is 2-3 metres from the laptop, but the link strength is about ~20%. Hardy's rtl8187 (from 2.6.24-19) showed a more reasonable link strength of about 90%, but it had its own problems with keeping the connection up. Now, i am wondering whether the card really sees a poor signal or it just reports the signal strength incorrectly. Frankly, I did not notice any degradation in download speed compared to Vista.

---

### Post by Baldrick_NZ on 2008-12-20
Thank goodness for this thread!

I was thinking my new wireless card was faulty!

I'm using an acer aspire 3000 lappy with a asus wl-107 network card (ralink) with intrepid and xp on dual boot. 

I've found xp gets excellent coverage where as intrepid gets between 8-74% strength. To get 50-74% I need to be a max of 3m away from the access point, but at about 7m away i get 9-50%. Although, right now I'm about 7m away and it claims 70%.

I've noticed when it transfers traffic the signal drops by 20-30% as well.

The signal drops using xp too, but maybe by only 10%. I still get excellent signal when using xp @ 7m.

The wireless drops out regularly using intrepid (due to signal loss I guess), and seldom using xp.

Sounds like bad drivers in intrepid. any ideas for a simple fix guys? I too am a relative newbie to linux, and can work synaptic fine but not so hot on coding.

Any help would be greatly appreciated. 

By the way it seems to make no difference if I use network manager or wicd.

Cheers,

Baldrick.

---

### Post by jongkind on 2008-12-20
I had the same. Then I installed wicd, which is an alternative for Ubuntu's network-manager), and the signal strength increased from 50-60% to 90%.

It can be downloaded from here:
[http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

---

### Post by Baldrick_NZ on 2008-12-20
> **jongkind said:**
> I had the same. Then I installed wicd, which is an alternative for Ubuntu's network-manager), and the signal strength increased from 50-60% to 90%.

It can be downloaded from here:
[http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

Didn't work for me. Only created more issues...

---

### Post by jongkind on 2008-12-20
> **Baldrick_NZ said:**
> Didn't work for me. Only created more issues...

I would help if you indicate what these 'more issues' are....

---

### Post by brandonhon on 2008-12-20
i tried wicd and it did nothing for me, same issue with low signal strength and dropped connection. i tried the livecd based on hardy and kabang, great signal strength. so i decided to just install the hardy version. now my signal strength is great but my connection just drops in the middle of surfing.

any suggestions on this issue?

---

### Post by almikul on 2008-12-20
> **brandonhon said:**
> i tried the livecd based on hardy and kabang, great signal strength. so i decided to just install the hardy version. now my signal strength is great but my connection just drops in the middle of surfing.

any suggestions on this issue?
Try this [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/258344](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/258344). For some reason, I could never compile these drivers provided by Realtek, but it may work for you. My connection on Intrepid, however weak it is, never drops, so I just switched back to Intrepid.

---

### Post by Argard on 2008-12-20
> **andreasis said:**
> hi brandonhon,

please post what wireless card/driver you are using. You should be able to find that information in:

lspci
lsmod

try lsusb, this asus card uses usb wireless card

---

### Post by Baldrick_NZ on 2008-12-20
> **jongkind said:**
> I would help if you indicate what these 'more issues' are....

Thanks for the reply Jongkind.

Mainly drops out and doesn't reconnect with wicd. Seems to me that it drops out when you move the PC and loose signal, then when you are back in signal range it won't detect that AP at all, even after a refresh, unless you re-boot.
Network manager not only detects the network but reconnects to that network after a drop out. 

Would really like to solve the signal issue though, tired of using xp for surfing the internet while I've got this orsum os doing nothing.

---

### Post by brandonhon on 2008-12-20
here is my lsub results.

by the way thanks for everyones help

---

### Post by Argard on 2008-12-21
> **brandonhon said:**
> here is my lsub results.

by the way thanks for everyones help

see,

yours: 
```
Bus 005 Device 006: ID 0bda:8187 Realtek Semiconductor Corp. 
```

Your card, like mine

mine : 
```
Bus 007 Device 002: ID 0bda:8187 Realtek Semiconductor Corp.
```

I was using ubuntu standard driver, but don't work, then I removed it, and installed the win98 driver using ndiswrapper, but I connect but the problem in the link happens.

[http://ubuntuforums.org/showthread.php?t=1016859]("http://ubuntuforums.org/showthread.php?t=1016859")

Then, tired,I bring the access point to my room and I am using a eth0.:(

---

### Post by brandonhon on 2008-12-28
my fix:

1. look for cat5 cable
2. cable found
3. plug in and disable wireless
4. everything works great :)

i hope this thread will eventually help someone with the same issue i was having. being kinda new to the *nix environment i just decided to go with what works.

good luck

---

### Post by AlexBellisBrown on 2009-01-01
Its defo a driver issue, hopefully launchpad knows about this, ill have a look to see if they do. My RTL8187 has never worked well, not on Hardy, nor Intrepid. In hardy i had fine signal strength but the dropping connections, but now on Intrepid, the signal is so weak its not worth bothering. On XP it works perfect, But the driver issue exists with ubuntu.

---

### Post by AlexBellisBrown on 2009-01-01
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/293946](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/293946)

Launchpad bug report, can everyone effected please post something there? The more evidence of a problem, the faster itll be fixed. Thanks :)

---

### Post by tymek666 on 2009-01-03
I have similar problem with newest kernel 2.6.27-11 and Intel wireless (ASmobile S96-jm laptop). The signal is very low when this kernel is used. With older one, 2.6.27-9 (official) works fine.

---

### Post by brandonhon on 2009-01-03
i visited launchpad yesterday and left a comment. thanks for the help. i hope this issue gets resolved.

thanks again

---

### Post by tymek666 on 2009-01-04
Well, today's linux-restricted update fixed my issue. Now I have good signal on 2.6.27-11 kernel.

---

### Post by Pitou on 2009-01-07
tymek666,

Can you tell me how you did upgrade your kernel to 2.6.27-11?

I'm at 2.6.27-9 and when I do a sudo apt-get update/upgrade, it tells me that there is no update available.

I have a Realtek 8187 on a Asus P5K-E

Thank you.

Pitou!

---

### Post by brandonhon on 2009-01-07
i believe if you just go to system -> administration -> update manager you will see those updates.

i don't see some of the system updates when i use apt-get. hope that helps.

---

### Post by Bourne_Identity on 2009-02-09
> **jongkind said:**
> I had the same. Then I installed wicd, which is an alternative for Ubuntu's network-manager), and the signal strength increased from 50-60% to 90%.

It can be downloaded from here:
[http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

So when I go to the Sourceforge link above and follow the instructions for downloading wicd I get an error. They say go to synaptics package manager and enable a repository which is fine. Then the next instruction is to open a terminal and enter:


wget -q [http://apt.wicd.net/wicd.gpg](http://apt.wicd.net/wicd.gpg) -O- | sudo apt-key add -

But I get an error returned through bad usage of the apt-key arguements. So what is wrong with the above line please ?

Thanks in adavance

---

### Post by zstein on 2009-02-10
I'm very new to Linux. Recently, I bought myself a new laptop, and decided to install Ubuntu 8.1 on my old one to play around with, try and teach myself a bit about Linux. (The laptop with Linux is a IBM A20m, pentium 3).

I plugged a Netgear WG111v2 USB wireless adapter in, and was quite pleased to see that it didn't need configuring...it immediately picked up my router in the next room and asked me for the WEP key.  I was able to connect right away, surf, get email.  But....

The signal strength is never more than 1 bar, and seems to vacillate between 14%-17%.  I have a Windows XP laptop in the same room and it has a full signal with 5 bars.

Also, when I am on for a little while, I cease to be able to surf or get email...it just stops until I reboot.  But it shows me still connected to the same IP.

Any advice for this newbie on:
A. Improving signal strength
B. Ending whatever causes the system to stop communication with the internet yet stay connected to the router?

Here is the ifconfig -a while I'm connected:

zane@zane-laptop:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:89 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8116 (8.1 KB)  TX bytes:8116 (8.1 KB)

pan0      Link encap:Ethernet  HWaddr a2:7b:7a:80:65:67  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:18:4d:c3:d4:e6  
          inet addr:10.0.0.3  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::218:4dff:fec3:d4e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32466 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2529 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13301295 (13.3 MB)  TX bytes:645841 (645.8 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-4D-C3-D4-E6-34-65-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Here is the iwconfig:

zane@zane-laptop:~$ iwconfig
lo        no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"ZANE"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1F:33:34:28:06   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=15/100  Signal level:65/65  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and running lspci:
zane@zane-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:02.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:02.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:03.0 Communication controller: Agere Systems WinModem 56k (rev 01)
00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)

Any advice, aside from moving to a newer laptop?

Zane

---

### Post by Juggercat on 2009-02-10
Ive been having exactly the same problems recently... before my internet used to download at speeds of 100-300 kbs... now its downloading at 40kbs with down them all!

Internet surfing is fine... and it doesnt drop at all... but i have between 1 and 2 bars...

With WICD it doesnt even connect to the wifi...

:S

---

### Post by pwp7669 on 2010-02-20
I recently replaced a Ubuntu 9.10 fully updated system with a clean install of Xubuntu 9.10 (also fully updated as of yesterday).  The signal strength of my wireless connection dropped from ~90% an the older system to ~40% with the newer install.  No changes to my PC, wireless card (IBM 802 CAG), wireless access point, or physical location.  Any ideas on how to restore the higher performance?

Peter

---

### Post by pwp7669 on 2010-02-21
Problem Solved.  I applied latest Ubuntu updates (32 files as of 23:30 yesterday) and rebooted my system.  Wireless connection now reported by Wicd at 100% strength.  Ah sweet mysteries of applying updates! 

:grin:
Peter

---

