---
title: "Network Card not detected"
date: 2010-04-04
forum: Networking &amp; Wireless
---

### Post by artemKas on 2010-04-04
Hello all !
I'm new in this community of Ubuntu users :)
I have bought a new laptop with W7 installed. And I installed dual boot with Ubuntu 9.10 on it.

I tried to connect my laptop to Internet by Ethernet port. It works with W7, but Ubuntu doesn't detect my Network card :(.
After some research on Internet, I suppose that it's a problem of drivers for this card.

Here some parameters I could get :
   
>ifconfig :

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:4 erreurs:0 :0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:240 (240.0 B) Octets transmis:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 2c:81:58:f8:9a:7c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 2C-81-58-F8-9A-7C-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)



>lspci -vvnn

04:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Device [11ab:4381] (rev 11)
      Subsystem: Sony Corporation Device [104d:9071]
      Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
      Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
      Latency: 0, Cache Line Size: 64 bytes
      Interrupt: pin A routed to IRQ 4
      Region 0: Memory at f2220000 (64-bit, non-prefetchable) [size=16K]
      Region 2: I/O ports at a000 [size=256]
      Expansion ROM at f2200000 [disabled] [size=128K]
      Capabilities: <access denied>

  
So my network card is a Marvell, model : 88E8059 (got it with W7).
I searched here : [http://www.marvell.com/support.html](http://www.marvell.com/support.html)
But the only drivers are for Linux 2.6 - Fedora.
And it doesn't work with my release, already tried. :(

Is there any other way to get the drivers for it ? Should I wait for possible release by Marwell or can i do something by myself ?
Thank you for your help :)

---

### Post by Iowan on 2010-04-04
[This]("http://ubuntuforums.org/showthread.php?t=1416385") thread (at least post #6) reports success...

---

### Post by artemKas on 2010-04-05
Thank you for your response, but they talk about wireless network.

It seems that mtinman have the same ethernet card than me and have the same problem :
> **mtinman said:**
> I did try this, and the installer shell program  provided by Marvell (which, btw, is written for Fedora, with the 2.6  kernel) ends up in an error. Also, my HP Mini 5102 (Product:  FN100UT#ABA) uses the 88E8059 driver, according to my Windows XP device  manager. Hope this helps.
I did the same and it ended up in an error too :(

---

### Post by artemKas on 2010-04-05
I tried to install the driver.

that's what I did :

unpack the driver : tar xfvj sk98lin.tar.bz2
here is the list of all files unpacked :
[http://img52.imageshack.us/img52/120/capture1ho.png](http://img52.imageshack.us/img52/120/capture1ho.png)
[http://img64.imageshack.us/i/capture2u.png/](http://img64.imageshack.us/i/capture2u.png/)
[http://img708.imageshack.us/i/capture3op.png/](http://img708.imageshack.us/i/capture3op.png/)

and when I try to launch ./install.sh
i get this : 
[http://img717.imageshack.us/img717/6135/capture4pb.png](http://img717.imageshack.us/img717/6135/capture4pb.png)

May be I did something wrong ?

I used the drivers for Linux 2.6 - Fedora from [http://www.marvell.com/support.html](http://www.marvell.com/support.html)

Have any idea ?

---

### Post by artemKas on 2010-04-08
still don't know what to do, can someone help me please ?

---

