---
title: "Signal 100% (_L__) Partial Lock Ceton USB Ubuntu 13.10"
date: 2014-01-12
forum: Mythbuntu
---

### Post by parallaxview on 2014-01-12
[COLOR=#000000][FONT=Verdana]Hey all. Just got my Ceton infinity4 USB apparently working in ubuntu 13.10 [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]on myth .27 [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I say apparently as I am only getting a 100% (*L_*) partial lock on tv. I [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]am on fios and it works fine in windows. 

[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]I have installed the driver from Ceton with no issues. [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]usb0 is assigned to 192.168.180.3 [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]The web interface is accessible [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I have set myth-setup with the cars as 192.168.180.1-RTP.0 to RTP.3 [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I have run the usbd deamon [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]The daemon is reporting that there is a connection: [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]rtp setup 0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]rtp destroy 0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]rtp setup 0 [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]rtp destroy 0 

I have found nothing on google and the Myth docs on signal are a bit light...[/FONT][/COLOR]

---

### Post by tuat2 on 2014-01-12
I have no idea about this certain piece of hardware, but did you check the syslog (or use "dmesg")? I had similar issues with another card, and the log stated, that the firmware was missing. The syslog was full of "firmware upload failed" messages.

---

### Post by parallaxview on 2014-01-12
Here is the output from backend, infinitv_usbd, and dmesg:

infinitv_usbd:
found infinitv (/sys/devices/pci0000:00/0000:00:13.2/usb2/2-2)
rtp setup 0
rtp destroy 0
rtp setup 0
rtp destroy 0


dmesg:
parallax@foodcourtia:~$ dmesg | grep "usb 2-2"
[93585.742859] usb 2-2: new high-speed USB device number 4 using ehci-pci
[93585.877142] usb 2-2: config 1 interface 0 altsetting 0 has an invalid endpoint with address 0x80, skipping
[93585.877155] usb 2-2: config 1 interface 0 altsetting 0 has an invalid endpoint with address 0x80, skipping
[93585.877164] usb 2-2: config 1 interface 0 altsetting 0 has 6 endpoint descriptors, different from the interface descriptor's value: 4
[93585.878864] usb 2-2: New USB device found, idVendor=2432, idProduct=0aa2
[93585.878874] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[93585.878882] usb 2-2: Product: Ceton InfiniTV USB
[93585.878888] usb 2-2: Manufacturer: Ceton Corporation

backend:
2014-01-12 20:42:45.995616 I  adding: foodcourtia as a client (events: 0)
2014-01-12 20:42:46.010223 I  TVRec[1]: Changing from None to WatchingLiveTV
2014-01-12 20:42:46.015777 I  TVRec[1]: HW Tuner: 1->1
2014-01-12 20:42:46.156918 I  MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2014-01-12 20:42:46.159392 I  Using protocol version 77
2014-01-12 20:42:46.161520 I  MainServer::ANN Monitor
2014-01-12 20:42:46.161553 I  adding: foodcourtia as a client (events: 0)
2014-01-12 20:42:46.731479 I  IPTVSH(::-1): run()
2014-01-12 20:42:46.753405 N  Connecting to master server: 127.0.0.1:6543
2014-01-12 20:42:46.754134 N  Connected successfully
2014-01-12 20:42:46.772064 I  CetonRTSP: Transport: RTP/AVP;unicast;client_port=33260-41971
2014-01-12 20:42:48.810954 E  RecBase[1](192.168.180.1-RTP.0): SetStrOption(...recordingtype): Option not in profile.
2014-01-12 20:42:48.812203 I  IPTVSH(::-1): run()
2014-01-12 20:42:48.849296 I  CetonRTSP: Transport: RTP/AVP;unicast;client_port=42601-40081
2014-01-12 20:43:16.756416 E  MythSocket(8535088:67): ReadStringList: Error, timed out after 30000 ms.
2014-01-12 20:43:16.756581 W  MainServer: Unknown socket closing MythSocket(0x8535088)
2014-01-12 20:43:16.756729 E  MythSocket(8535088:-1): No response.
2014-01-12 20:43:16.756764 E  MainServer: Failed to open master server socket, timeout

---

### Post by aelfric55 on 2014-01-13
Some DVB tuners get swamped and refuse to lock when the received signal is too strong. I don't know whether your tuner is one of these, but the idea can be readily be tested by inserting an el cheapo $2 two-way or four-way splitter between your signal source and the tuner. For my over-sensitive DVB tuners this was generally enough of a signal attenuator to get the job done.

---

### Post by parallaxview on 2014-01-13
I have some attenuators I can throw on tonight to give it a go. If that turns out to be the case I will be gob-smacked as it worked fine in windows :-P

---

### Post by tuat2 on 2014-01-13
Ok, thanks for the logs. But can you use: dmesg | grep firmware

:)

---

### Post by parallaxview on 2014-01-14
> **tuat2 said:**
> Ok, thanks for the logs. But can you use: dmesg | grep firmware

:)


No results

---

### Post by scstanton1337 on 2014-01-14
You mentioned that accessing the Ceton tuner via the embedded IP address works.  Are you able to set up a UDP RTP stream to the Linux host and receive it via VLC?  I think the syntax is rtp://*:8080 or something like that.. check the Ceton web site for the exact URI.  If that works and VLC displays video and audio, your tuner is working.  Next make sure that the streaming is turned off and see if you can use VLC or mplayer to read directly from /dev/ceton/*_mpeg0* devices.  If that works, then MythTV should be able to receive the streams from the tuner.  Of course, make sure you're getting a signal lock for your tuned channel in the Ceton web interface.  If you're not seeing that, there's probably a problem in the CableCard activation or channel map being downloaded to the CableCard.

---

### Post by parallaxview on 2014-01-14
> **scstanton1337 said:**
> You mentioned that accessing the Ceton tuner via the embedded IP address works.  Are you able to set up a UDP RTP stream to the Linux host and receive it via VLC?  I think the syntax is rtp://*:8080 or something like that.. check the Ceton web site for the exact URI.  If that works and VLC displays video and audio, your tuner is working.  Next make sure that the streaming is turned off and see if you can use VLC or mplayer to read directly from /dev/ceton/*_mpeg0* devices.  If that works, then MythTV should be able to receive the streams from the tuner.  Of course, make sure you're getting a signal lock for your tuned channel in the Ceton web interface.  If you're not seeing that, there's probably a problem in the CableCard activation or channel map being downloaded to the CableCard.

I ran the Python client and then opened VLC. I chose a basic channel, no encryption

parallax@foodcourtia:~/infinitv-usbd-0.1.0/infinitv_client_1_2$ python client.py -i 192.168.180.3 -t 0 -c 3
1389751190.951546 client.py:136 Initializing
1389751194.033451 board.py:46 Found: Ceton InfiniTV USB (00-80-44-9f)
1389751195.348556 client.py:27 PCRLock: 1
1389751195.823049 client.py:36 AVTransportURI: rtsp://192.168.180.1:8554/cetonmpeg0
1389751195.823145 client.py:38 PrepareForConnection
1389751196.076576 client.py:45 RTSP setup done
1389751196.162369 client.py:52 SetChannel ChannelNumber=3 SourceID=0
1389751196.311779 client.py:55 MPEG data streaming to 127.0.0.1:8000
1389751196.311867 client.py:56 OOB data streaming to 127.0.0.1:8001



VLC Output worked! Video and sound were present! :)

I tried it again with a cable channel and VLC started spitting out Demux errors...

---

### Post by parallaxview on 2014-01-14
Since I am using the usb RTP service there is no /dev/ device to read from; so I need to get streaming to function.

---

### Post by parallaxview on 2014-01-16
Ok so update on this, it appears there is an rtp issue.

My test using the python script allowed me to point vlc to udp://@127.0.0.1:8000 and get video. Using RTP I was not able to get video, with or without the python script (so in vlc rtp://127.0.0.1:8000)

Also I attempted to use netcat and save the stream to an mpg. The file grew, which gave me hope, but when trying to view the file I got no video the file simply seemed to blip for a second and then close.

---

### Post by scstanton1337 on 2014-01-17
Stupid question but are you setting a channel that you know you receive via the Ceton web interface before trying to view the stream?  Once you tune the channel you should see the channel details like Frequency, Modulation, Carrier Lock, Digital Lock, Signal and S/N levels, and especially the Copy Protection information.  Is all of that coming through ok and with a Copy Information of 00 (Copy Freely)?

---

### Post by parallaxview on 2014-01-17
I am using Channel 164 (food network) in the Ceton WebUI I get:

WMDRM Pairing: Red
Carrier Lock: 1
Digital Lock: 1
Signal Level: -4.5dBmV

Playback: PLAYING
Program Number 172
PIDs: 514,820,6B8,53C,780,D34,12A2,6C2,6AE,578,0,6B9,6C0,6C1,6BA,6BC

CableCARD: Insterted
Channel: 166
Descrambling Status: Unknown

Copy Protection: Copy Control Information: "Copy Free" (00)

If I run both the infinitv_usbd service and the python client client.py, I can open vlc and set the stream to udp://@127.0.0.1:8000 with success.

So I think things are good, but I can not get rtp to work, and myth is stuck with (_L__).

---

### Post by scstanton1337 on 2014-01-30
I can't say what you problem is, but I know with my card MythTV can't access the tuner while it is in PLAYING mode, it has to be STOPPED.  If you still haven't gotten it working, try emailing [email]linux@cetoncorp.com[/email] for help.

---

### Post by parallaxview on 2014-02-01
> **scstanton1337 said:**
> I can't say what you problem is, but I know with my card MythTV can't access the tuner while it is in PLAYING mode, it has to be STOPPED.  If you still haven't gotten it working, try emailing [EMAIL="linux@cetoncorp.com"]linux@cetoncorp.com[/EMAIL] for help.

I will reach out to them now and see if I can get any further. If so I will let you all know how :)

---

