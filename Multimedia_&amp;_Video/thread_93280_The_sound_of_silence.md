---
title: "The sound of silence"
date: 2005-11-21
forum: Multimedia &amp; Video
---

### Post by anortrup on 2005-11-21
I'm having trouble getting my sound to work on my Gateway M320x laptop.  

I've been through all of the sites that I can find and none of the advice seems to work.  

The strange thing is that I don't get any errors when I try and play sounds, I just don't get any sound at all.  Everything appears to be configured properly (although I've never worked with sound in linux before so I'm not completely sure what it should look like).

I've been through all of the steps listed: [http://linux.iuplog.com/default.asp?item=94639](http://linux.iuplog.com/default.asp?item=94639) and recived no change in the situation.  

When I do lspci my sound card is listed as: 
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)

I'm not sure what other information would be useful in debugging this problem.  Any help you can offer is greatly appreciated.

--Andy

---

### Post by teaker1s on 2005-11-21
make sure your app and system are using the same audio sink
 next volume control  
edit- preferences and select all the 'tracks'
there will now be switches on the switches tab you can toggle on or off

---

### Post by anortrup on 2005-11-21
I have checked all that and everything seems to be in order.  I've still got no sound.

thanks for the help,
Andy

---

### Post by Alphonse on 2005-11-24
Maybe I should post to this thread instead of starting a new one, as I have essentially the same problem as anortrupw (Andy). The only difference seems to be that the Gateway laptop I'm using is series 7330GZ.

I too have tried all the steps given so far for resolution and nothing works -- I get no system errors, I just don't hear any audio at all.

An [COLOR=Blue]**aplay -l**[/COLOR] command gives me following output:

```
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
``` 

An **[COLOR=Blue]lspci[/COLOR]** commands outputs this:

```
0000:00:00.0 Host bridge: Intel Corp. 82852/855GM Host Bridge (rev 02)
0000:00:00.1 System peripheral: Intel Corp. 855GM/GME GMCH Memory I/O Control Registers (rev 02)
0000:00:00.3 System peripheral: Intel Corp. 855GM/GME GMCH Configuration Process Registers (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:02.1 Display controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 03)
***0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)***
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
0000:01:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
0000:01:05.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
0000:01:06.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
0000:01:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
``` 
Any further help would be very much appreciated. Great thanks in advance.

---

