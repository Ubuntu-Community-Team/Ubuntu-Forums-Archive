---
title: "Wireless Printing to HP C4500"
date: 2009-04-10
forum: Networking &amp; Wireless
---

### Post by CarlWalters on 2009-04-10
Hi, I've just purchased an HP Photosmart C4500 and have connected it to my main Dasktop - running Ubuntu 8.04. I can print OK from the desktop having installed hplib. My Laptop also runs Ubuntu 8.04 and I can print from the Laptop OK via CUPS. However I can only do this when the Desktop is powered on as well. 

What I would like to be able to do is print wirelessly from the Laptop if the Desktop isn't powered up. In the list of available networks I can "see" the HP Printer which is showing as "hpsetup" as well as my usal wireless access point. 

Does anyone have any idea how I would go about connecting an printing from my Laptop wirelessly? The manuals only give instructions for Windows and Mac :(

Any help much appreciated :)

Carl

---

### Post by chili555 on 2009-04-11
> What I would like to be able to do is print wirelessly from the Laptop if the Desktop isn't powered up.I almost never say this, but, under your present setup: impossible. The data that's going to be printed on paper leaves your laptop, travels wirelessly through your router and heads for your desktop machine. If the desktop is turned off, there is no way for the desktop to pass the data out to the printer port, typically USB. The printing job dies on the vine, so to speak.

Now, you could invest in a wireless print server, which is itself a small single purpose computer, and which needs to be turned on at all times you wish to print. You should balance this against the cost of leaving your desktop machine turned on 24/7.

[http://www.amazon.com/Linksys-WPS54GU2-Wireless-G-Print-Server/dp/B0000E658Q](http://www.amazon.com/Linksys-WPS54GU2-Wireless-G-Print-Server/dp/B0000E658Q)

---

### Post by CarlWalters on 2009-04-11
Sorry I missed a vital piece of information of my original post. The HP C4500 itself has wireless built in - [http://h10010.www1.hp.com/wwpc/uk/en/ho/WF06a/18972-18972-238444-410635-410635-3575173.html](http://h10010.www1.hp.com/wwpc/uk/en/ho/WF06a/18972-18972-238444-410635-410635-3575173.html) - and when it is powered on and the wireless enabled then I can see it in the Network Manager. It displays as "hpsetup" but the icon next to it is a "monitor" rather then the usual "wireless aerial" than I see next to my wireless access point. This is even if the Desktop is turned off. The printer is connected into the Desktop via USB so I can print to it from there or from the Laptop via CUPS if the Desktop is turned on.

---

### Post by chili555 on 2009-04-11
> The HP C4500 itself has wireless built inThat makes all the difference! I suggest you try adding it as a network printer on your laptop. Go to System -> Administration -> Printing and select New. You should see the option to set up a network printer and I suggest the Internet Printing Protocol, or IPP. Even better, it will probably do 'searching for printers' and figure it out for itself, since the printer is obviously publishing itself as 'hpsetup'. Print a test page and enjoy.

Post back if you get stuck.

---

### Post by CarlWalters on 2009-04-11
Yes - sorry for missing off the vital information. :redface:

If I do a "sudo iwlist scan" then I get a report back which includes the preiinter as below.

Cell 04 - Address: 32:23:7D:AB:19:33
 ESSID:"hpsetup"
 Mode:Ad-Hoc
 Channel:6
 Frequency:2.437 GHz (Channel 6)
 Quality=86/100  Signal level=-48 dBm  Noise level=-68 dBm
 Encryption key:off
 Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
 Extra:tsf=0000000000000000

Then if I do "System -> Administration -> Printing" and select "New Printer" I get "Searching for Printers" and then a list of options none of which looks to be the actual printer itself. I get
 Print into PDF File
 App Socket/HP Jet Direct
 Internet Printing Protococl (ipp)
 LPD or LPR Host or Printer
 Windows Printer via SAMBA
 Other

If I select IPP then I get the form to fill in
  Host  : ????
  Queue : /printers/

and greyed out boxes for "Find Queue" and "Verify". 

And I'm unsure as to what to fill in here.

---

### Post by chili555 on 2009-04-11
The usual format for IPP URI's is:```
ipp://<IPaddress>:631/printers/<printername>
```After glancing at the user guide, I think the address is 192.168.1.101. You can verify this with:```
ping -c3 192.168.1.101
```If you get ping returns, you know the IP address is correct.

Translating all this suggests:```
ipp://192.168.1.101:631/printers/hpsetup
```Please let us know.

I am slightly troubled by the ad-hoc setting in *iwlist.* The user guide suggests ad-hoc is for printers in a setting where there is no wireless router. Also, the guide suggests you use USB ***or*** wireless, but not both.

---

### Post by CarlWalters on 2009-04-11
Many thanks for all the help so far :)

I tried a ping but that doesn't seem hopeful as below

```

carl@carl-laptop:~$ ping -c3 192.168.1.101
PING 192.168.1.101 (192.168.1.101) 56(84) bytes of data.
From 192.168.1.68 icmp_seq=1 Destination Host Unreachable
From 192.168.1.68 icmp_seq=2 Destination Host Unreachable
From 192.168.1.68 icmp_seq=3 Destination Host Unreachable

--- 192.168.1.101 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2009ms
, pipe 3

```

I ran "Wireless Network Test" from the printer front panel and that prints out a page of information

Wireless on :   PASS
Wireless Working : PASS
Network name (SSID) found : FAIL
Security  : PASS
Connected   :NOT RUN
Signal Strength : NOT RUN
Other networks detected matching your Network Name (SSID)  :NOT RUN
Wireless Networks Detected  :4
Downlink Count  :2
Channel  :NOT RUN

Network Name (SSID ) : hpsetup
MAC : 00:23:7d:ab:19:33
IP address : NOT APPLICABLE
Configuration Source : NOT APPLICABLE
Communication Mode : Ad Hoc
Authentication Type : Open System
Encryption : None

---

### Post by chili555 on 2009-04-11
> IP address : NOT APPLICABLEI think that's entirely because the printer is in ad-hoc mode and not infrastructure. I saw this: [http://h30434.www3.hp.com/psg/board/message?board.id=Install&message.id=3994](http://h30434.www3.hp.com/psg/board/message?board.id=Install&message.id=3994)

I wonder if, in order to connect to the printer, which is in ad-hoc mode, you need to put your laptop in ad-hoc mode to continue the process outlined in the link. I suggest:```
sudo ifdown wlan0
sudo iwconfig wlan0 mode Ad-Hoc
```Now can you continue the steps that DexterM outlined? I am quite confident that one necessary step is putting the mode of the printer in infrastructure, or as we call it here in Ubuntu World, Managed.

When you are all done, do:```
sudo iwconfig wlan0 mode Managed
sudo ifup wlan0
```Substitute your interface if it's not wlan0. Please let us know.

---

### Post by CarlWalters on 2009-04-12
I'm not having a lot  of success here I'm afraid :) 

```

carl@carl-laptop:~$ sudo ifdown wlan0
ifdown: interface wlan0 not configured
carl@carl-laptop:~$ sudo iwconfig wlan0 mode Ad-Hoc
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.
carl@carl-laptop:~$ 

```

I don't suppose this is what should happen?

The output of ifconfig is
```

carl@carl-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:23:8b:41:7b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1642 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1642 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:82100 (80.1 KB)  TX bytes:82100 (80.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:26:16:ef:c4  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:26ff:fe16:efc4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16361 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15871 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8578928 (8.1 MB)  TX bytes:2536649 (2.4 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-26-16-EF-C4-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

carl@carl-laptop:~$ 


```

---

### Post by chili555 on 2009-04-12
> Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.
> I don't suppose this is what should happen?No, indeed! However, you must bring the interface down in order to change the mode to ad-hoc. Please also try:```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode Ad-Hoc
```I read the manual for the printer and, unfortunately, I can see no way to change its mode to 'infrastucture' from the front panel. I also downloaded the software package from HP and tried to run it under wine to see if I could figure out what it's doing and, so far, I can't get it to run.

---

### Post by sgrabowski on 2009-05-05
The answer to the problem isn't that this printer doesn't work with Ubuntu - its that you were trying to use it in USB mode AND Wireless mode. This printer can only do one or the other.

Works perfectly with Ubuntu 9.04. Follow these instructions if you need help:

[quote=chilli555]That makes all the difference! I suggest you try adding it as a network printer on your laptop. Go to System -> Administration -> Printing and select New. You should see the option to set up a network printer and I suggest the Internet Printing Protocol, or IPP. Even better, it will probably do 'searching for printers' and figure it out for itself, since the printer is obviously publishing itself as 'hpsetup'. Print a test page and enjoy.[/quote]

The only alteration is that the printer appears straight away under Network Printers.

Hope this helps someone...

---

### Post by rasmus91 on 2010-02-13
> The answer to the problem isn't that this printer doesn't work with Ubuntu - its that you were trying to use it in USB mode AND Wireless mode. This printer can only do one or the other.

Yeah, and this shouldn't be the final comment in this thread, as you're mistaken.

My parents happen to own a hp photosmart c4500 and it's connected to a computer as well as to the network, and it works find this way.

---

### Post by Oxen on 2010-02-26
I have one of these printers & connect via wireless to it 

You have to configure it for wireless using the usb connection first - hplip has the option for the temporary usb. You can continue using usb afterwards though.

I use hplip on all my pcs to connect.

---

