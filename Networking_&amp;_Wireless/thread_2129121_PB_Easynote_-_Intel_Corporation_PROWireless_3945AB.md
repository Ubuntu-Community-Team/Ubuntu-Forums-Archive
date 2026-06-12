---
title: "PB Easynote - Intel Corporation PRO/Wireless 3945ABG (Golan] Netwo - Wireless Problem"
date: 2013-03-25
forum: Networking &amp; Wireless
---

### Post by ajm91 on 2013-03-25
Hi.

I'm really new to Linux -these green users... what would we make without them... :D -.


I have installed Ubuntu 12.10 (not the version beta) to my laptop, which is:
Packard Bell Easynote MX65-203
whose Network Controler is:
Intel Corporation PRO/Wireless 3945ABG (Golan] Netwo rk conection (rev 02)


My problem is that my laptop detect some wifi networks, including mine, of course. But when I'm trying to connect it, it ask me for the password over and over (and don't connect).
It was the case, a day, I was watching a movie at the TV with the computer on. When the movie finished, I had near 40 windows asking me the password (I don't matter, even with my shock finding that, but it's an anecdote about my beginings in Linux ;) )

I have been looking how to fix it in many forums, but couldn't find the exact problem, and finally i have to ask for direct help in this forum. Excuse my ignorancy even to that level. The internet card has similar problems, but can't find about the laptop.
Reading these forums, now I know that Ubuntu 12.10 has had some problems with internet, but if I could, I'd continue using this version. I have read that the problem could be the network controler, or the driver, but don't know how to fix it.

But (now I'm sure it has no relation at all) I have no problems with the wired connection from the same router. I have tried to install these "additional controllers", but didn't work.

I'm writing this in the partition of windows xp I have in the same laptop (don't look so bad to me, i need some programs -and games ;)- which are exclusive to windows :()
I'm not sure what information is necessary to fix it, so i'll be active to answer for any data required. 

And thank you all so much, I've already sensed the famous care among Linux users, and I'm really happy to have entered in this community.

---

### Post by ajm91 on 2013-03-30
ok, it had past 5 days since I wrote that looking for help.
I wonder now if my doubt are too much hard for this forum, maybe I can get 1 level up this doubt.

Or renew my question, because a 5 day-old post is almost on the page 15 of this Absolute Beginners Section, so it's hard to get an answer now.

Any suggestion?

---

### Post by DuckHook on 2013-03-30
Hi and welcome to the forums, and to Linux in general.

This is a community forum run and serviced by volunteers. Unlike lock-in vendor sites, it is not supported by big profits, so it cannot be treated like paid support and therefore relies on people who have the time and the right expertise to catch your request as it is posted. It is perfectly acceptable to bump your thread after 24 hrs if no response.

Re: your request for help.

You will get much better responses by supplying the right info in your request, as per [this]("http://ubuntuforums.org/showthread.php?t=1422475") sticky on the first page of the forum. Otherwise, those trying to help have nothing to go on. Please do the following:

1. Attach your laptop to your router via ethernet cable so that you can do what follows:

2. Invoke a terminal either from dash or by <Ctrl>+<Alt>+<t>

3. Do:```
sudo lshw -C network
``````
sudo lspci -vk | grep -iA13 net
``````
ifconfig
``````
iwconfig
``````
cat /etc/modules
``````
grep blacklist /etc/modprobe.d/blacklist.conf
```
4. Post output of these commands back to this thread, but enclose each set in code marks (the hash button "#") found at top of the posting box.

---

### Post by ajm91 on 2013-03-31
Sorry, I didn't want to be unpolite, I just wanted to express my disappointment because I turned on "panic mode" when my message was 5 day without answer and making way to other threads (and I didn't know that my post would be "refresh" on the first position of the forum on each new message). I really appreciate your work to help everyone.

I didn't want to put the results of some of these commands on the first message, because I didn't want to saturate the thread including information I don't know if it was necessary.

Ok, these are the answers to that commands:
(I'm sorry I'm from Spain and installed in Spanish, so a little info is in my language. As long as it is -I hope- on the same order, and the words have similar structure, it's not hard to understand)

1) Answer to lshw -C network
```
  *-network               
       descripción: Interfaz inalámbrica
       producto: PRO/Wireless 3945ABG [Golan] Network Connection
       fabricante: Intel Corporation
       id físico: 0
       información del bus: pci@0000:03:00.0
       nombre lógico: wlan0
       versión: 02
       serie: 00:18:de:87:fc:2b
       anchura: 32 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuración: broadcast=yes driver=iwl3945 driverversion=3.5.0-17-generic firmware=15.32.2.9 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       recursos: irq:44 memoria:fe1ff000-fe1fffff
  *-network
       descripción: Ethernet interface
       producto: RTL-8139/8139C/8139C+
       fabricante: Realtek Semiconductor Co., Ltd.
       id físico: 7
       información del bus: pci@0000:06:07.0
       nombre lógico: eth0
       versión: 10
       serie: 00:18:f3:ab:a9:b7
       tamaño: 100Mbit/s
       capacidad: 100Mbit/s
       anchura: 32 bits
       reloj: 33MHz
       capacidades: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuración: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.9 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       recursos: irq:16 ioport:d800(size=256) memoria:feafe400-feafe4ff

```

2) Answer to lspci -vk | grep -iA13 net
```
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
    Subsystem: Intel Corporation PRO/Wireless 3945ABG Network Connection
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at fe1ff000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [c8] Power Management version 2
    Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [e0] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 00-18-de-ff-ff-87-fc-2b
    Kernel driver in use: iwl3945
    Kernel modules: iwl3945

06:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (prog-if 10 [OHCI])
    Subsystem: Packard Bell B.V. Device c022
    Flags: bus master, medium devsel, latency 64, IRQ 17
--
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Packard Bell B.V. Device c022
    Flags: bus master, medium devsel, latency 64, IRQ 16
    I/O ports at d800 [size=256]
    Memory at feafe400 (32-bit, non-prefetchable) [size=256]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp

```

3) Answer to ifconfig
```
eth0      Link encap:Ethernet  direcciónHW 00:18:f3:ab:a9:b7  
          Direc. inet:192.168.1.9  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::218:f3ff:feab:a9b7/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:3277 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:2350 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:3970090 (3.9 MB)  TX bytes:316431 (316.4 KB)

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:116 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:116 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:11003 (11.0 KB)  TX bytes:11003 (11.0 KB)

wlan0     Link encap:Ethernet  direcciónHW 00:18:de:87:fc:2b  
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)

```

4) Answer to iwconfig
```
wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

eth0      no wireless extensions.

```

5) Answer to cat /etc/modules
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp

```

6) Answer to grep blacklist /etc/modprobe.d/blacklist.conf
```
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

```


And again, thanks for all :). Maybe it was that lack of information why some people saw my message and couldn't help, but, as I said, it was because I don't know yet what information is necessary.

P.S: Maybe this new information is also useful - I didn't make any change in the system since the installation (put a program on the blacklist, I mean, actualize the software or something similar). This OS is perfectly new.

---

### Post by wildmanne39 on 2013-03-31
Hi, please try:
```
sudo su
echo options iwl3945 swcrypto=1 >> /etc/modprobe.d/iwl3945.conf

```
Thanks

---

### Post by ajm91 on 2013-03-31
[ATTACH=CONFIG]240790[/ATTACH]

Is this what it was supposed to be? There was no answer after 1 minute.
I'm afraid it didn't work, it continues asking me the password again and again, it doesn't finish connecting the network.

But thanks for your try

---

### Post by wildmanne39 on 2013-03-31
It looks like it, did you reboot? 
Please do then copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

### Post by DuckHook on 2013-04-01
> **ajm91 said:**
> Sorry, I didn't want to be unpolite, I just wanted to express my disappointment because I turned on "panic mode" when my message was 5 day without answer and making way to other threads (and I didn't know that my post would be "refresh" on the first position of the forum on each new message). I really appreciate your work to help everyone.

But I thought you were very polite, and especially so compared to some of the demands that we have seen on these forums. I was only trying to inform you that it is very acceptable etiquette for you to bump an unanswered thread after 24 hours, and that you needn't wait 5 days. 

> I didn't want to put the results of some of these commands on the first message, because I didn't want to saturate the thread including information I don't know if it was necessary.

Very understandable. However, on a help forum, generally the more info the better. As long as you use the code  function to box your output, no one will mind.

> (I'm sorry I'm from Spain and installed in Spanish, so a little info is in my language. As long as it is -I hope- on the same order, and the words have similar structure, it's not hard to understand)

I am always awestruck by people who post here with English as their non-native language. I would never venture to post on a Spanish forum, so you have my sincere admiration.

I note that Wild Man has taken up your problem. You now have a genuine certified guru helping you and are in far better hands than mine.

Good luck and Happy Ubuntuing!

---

### Post by ajm91 on 2013-04-01
sorry, I forgot totally about reboot :oops:, it was like no result. I'll try inmediately.

And sorry, DuckHook, because I misunderstood you. Didn't know what bump meant (now I do), and my first lecture of your message sounded to me like reprimanding, something like "non-professional supporters" don't have to answer a post inmediately. And for me, there's no problem asking for help in a language that I have more posibilities to get an answer, as it's more used than mine.

Now I'll try, wish me luck

---

### Post by ajm91 on 2013-04-01
[ATTACH]240816[/ATTACH]

ok, the reboot didn't make it work, so here's, as you asked for, the netinfo.txt
And thank you all so much for helping me, I don't know what would I do myself with this.

---

### Post by wildmanne39 on 2013-04-01
Wow you have a lot of networks showing, which one are you trying to connect too?

Also none of them have a strong enough signal to connect too.
Thanks

---

### Post by ajm91 on 2013-04-01
I was trying to connect to ONO1E3B, it has 87 points of strength, as I was 2 meters from the router. It'd be strange that this happened for that reason

---

### Post by wildmanne39 on 2013-04-01
Please unplug your wired connection before trying to get your wireless working, then set your settings in network manager to match the screenshots then reboot and let us know if it connects.
Thanks

---

### Post by ajm91 on 2013-04-07
Sorry, couldn't use my laptop during the last 4 days.

I tried the last advice, it's not working yet...
How can I be so bad luck? :(

Actually, I've reinstalled this version of Ubuntu (as it was empty anyway) to see if these advices work, they do not.


I was thinking... maybe I'm doing the "sudo su" instruction in the wrong way:
This is a screen capture after doing that command of "sudo su". When I am going to reboot
I don't know if I must close the terminal or not. If I try to close it, that message appears, so I think maybe the process is interrupted. If I reboot inmediately, without closing it, the message don't show up.
[ATTACH=CONFIG]241056[/ATTACH]
It says something as: "Want to close this terminal? ------ There's still a process executing at this terminal. It will close if you continue"
As a result, neither of the two procedures fix the wireless problem.

There's also useful information maybe:
I tried to connect even with a wrong password, and no message about it came out, it continued asking for write the passwork again. So I think it may be about the wireless card, which may detect wireless networks but not communicate with them.


And thanks for all the help. I don't know what must be happening.

---

### Post by wildmanne39 on 2013-04-07
Hi, let's install wicd and remove network manager and it has to be done in that order.

Follow the directons in this link
[https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)
Thanks

---

### Post by ajm91 on 2013-04-07
ok, I did.
At least that worked out... :)

now, what information should I put at these fields? I don't know, I never chose an IP direction or DNS myself.
 [ATTACH=CONFIG]241070[/ATTACH]

I'm so glad that I tried inmediately to write the pass with no more info, but I think it doesn't work, as it is Authenticating for a long time, until it stops itself.
I hope I don't have the same problem again... :(

And thanks for all this help.

---

### Post by wildmanne39 on 2013-04-07
You can leave all that blank and use dhclient setting and it should connect.

You just need to put a check by auto connect.

Do you see your network listed? choose it then save and reboot and see if it connects.
Thanks

---

### Post by ajm91 on 2013-04-13
ok, my network is listed, I picked the auto-connect, write the password in "Properties", and reboot the system.


My laptop (or me) must be stupid, because it continues trying to connect, without finishing the process.
I will explain:
There are some messages at the bottom of the application about what is happening.
By default, it says: "Not connected"  (obviusly)
When I picked the connect button (or open wicd after picked auto-connect), it starts the process:
There are 2 messages passing very fast: "Shutting down active connections" and "Reseting IP address" Both messages (one after the other passed away in about 1 second)
Next message is "Putting interface up", which remain for 2 s.
And the next one is "Validating authentication", it remains for 35 s, after that, the process stops, and finally, it says:
"ONO1E3B: Connection Failed: Bad password"



........................................................ uhhhhh

I don't think so. I've learn the password due to the several times I tried to connect. Even I tried to connect with my cell again to know that the password is still working, and my phone has no problem connecting.
My cell says the security of the network is WPA/WPA2 PSK; wicd says it's WPA2 at channel 11 with a intensity of 82%.
In Properties I don't know which kind of connection I must choose, from:
"WPA 1/2 (HEX), WPA 1/2 (Passphrase), WPA-PEAP, WPA2-LEAP or WPA2-PEAP"

Thanks

---

### Post by claracc on 2013-04-13
I have the same wireless card in my hp compaq 6720s and wicd is the only manager capable of doing it to work. In properties, I have marked WPA 1/2 (Hex [0-9/A-F]), you can try it and then write the password.

---

### Post by wildmanne39 on 2013-04-13
Hi, in your router set encryption to just wpa2 AES if that option is present.

Use channel 1 or 11, my good friend chili555 also suggests we try this parameter.
```
gksudo gedit /etc/modprobe.d/iwl3945.conf
```
add this line:
```
options iwl3945 disable_hw_scan=1
```
remove
```
options iwl3945 swcrypto=1
```
save, close gedit and reboot.
Thanks

---

### Post by ajm91 on 2013-04-14
ok, I must be really stupid if I can't follow these clear instructions...  or my laptop is really bad... :(
I didn't see any change at that process.

It must have a bad configuration yet (I don't know what). Really, I'm not so stupid to put a wrong password.

I did everything chili555 said to you, it was a little strange that
```
options iwl3945 swcrypto=1
```
was written 3 times at that file. Well, I deleted all of them, and write the other line. (Not so hard)

With:
> Hi, in your router set encryption to just wpa2 AES if that option is present.
Do you mean to change the router configuration or at wicd? At wicd it doesn't appear that kind of connection.
It's strange because I can connect with the wii, the cell, Windows at the same laptop... May the change of configuration make some problems with the connection of the other electronics?



I don't know why I have so many problems with that.:confused:

---

### Post by wildmanne39 on 2013-04-14
You change to wpa2 in the router configuration.

You will also make sure in wicd that it is set to wpa/wpa2 not wep.

No it is not likely to cause issues with your other devices.

If it does not connect after you make the changes please remove the netinfo.text file from your home folder and run the wireless script again and post the results.
Thanks

---

### Post by ajm91 on 2013-04-14
1) Well, I change the encryptation system of the router.
2) wicd is still at WPA/WPA2 A-Z 0-9 HEXADECIMAL security system
3) No issues on the other devices
4) I didn't find a netinfo.txt in my home folder, nor looking for it at dash.

5) I don't know what you mean with the wireless script (a terminal command?, a file?)
6) No results at all. It continues saying "Bad password"... It's not really a wrong password, I know it by heart now, for all times I need to write it. Even, as I say, reconnecting the cell to know if there was a change.

I don't know what to do know. It would be better installing other version of ubuntu... I didn't hear other versions have these problems.
I'm getting a little tired :( of fighting and fighting to the network with no result.
What do you recommend me?

Anyway, thanks again for your help, I won't give up until you get bored of me :rolleyes::rolleyes:

---

### Post by wildmanne39 on 2013-04-14
The directions for the script is in post 7 of this thread.
Thanks

---

