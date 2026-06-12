---
title: "Wireless not functioning correctly"
date: 2009-09-20
forum: Networking &amp; Wireless
---

### Post by Petarrrr on 2009-09-20
I just installed Ubuntu Desktop Edition 9.04 on my pc and dual booting windows 7.
Everything works absolutely perfect except my wireless card, a netgear wg311v3
I've spent countless hours googling answers, and have got so close to it working.
Installed ndiswrapper and got the drivers working, ubuntu recognizes my card and it comes up in iwconfig in the terminal. It even picks up my wireless access point.
The problem is when i try to connect, it just keeps trying until it eventually gives up.
it has connected a couple of times, and i disconnected my ethernet to see if it worked, but no success.
This is my last hope to get this working.
Thanks for reading, and if you can help i'd greatly appreciate it :D

Cheers.

---

### Post by drpjkurian on 2009-09-20
Hi Petarr

Please visit this URL. [https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3) .It may solve your problem. Give it a try

With regards
Dr Kurian:P

---

### Post by Petarrrr on 2009-09-20
Thanks for your help and your super quick reply [drpjkurian]("http://ubuntuforums.org/member.php?u=805294"), unfortunately i have already been through that article!
according to that article it is installed correctly.
The problem is it wont connect to my wireless access point properly and when it does, i seem to have no internet connection
My wireless has WPA2 encryption, would this affect it?

---

### Post by louigi600 on 2009-09-20
After connects gives up can you show me tha last 20 lines of your /var/log/messages  and 
the output of:
dmesg |tail -20

---

### Post by Petarrrr on 2009-09-20
> **louigi600 said:**
> After connects gives up can you show me tha last 20 lines of your /var/log/messages  and 
the output of:
dmesg |tail -20
Hey louigi600

Here it is as you requested:

  	 	 	 	 	 	  /var/log/messages
 Sep 20 18:59:51 petar-desktop kernel: [   11.660863] ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 Sep 20 18:59:52 petar-desktop kernel: [   12.812724] scsi 4:0:0:0: Direct-Access     USB2.0   CardReader CF    0100 PQ: 0 ANSI: 0  
 Sep 20 18:59:52 petar-desktop kernel: [   12.813090] scsi 4:0:0:1: Direct-Access     USB2.0   CardReader SM XD 0100 PQ: 0 ANSI: 0  
 Sep 20 18:59:52 petar-desktop kernel: [   12.813464] scsi 4:0:0:2: Direct-Access     USB2.0   CardReader MS    0100 PQ: 0 ANSI: 0  
 Sep 20 18:59:52 petar-desktop kernel: [   12.813838] scsi 4:0:0:3: Direct-Access     USB2.0   CardReader SD    0100 PQ: 0 ANSI: 0  
 Sep 20 18:59:52 petar-desktop kernel: [   12.815568] sd 4:0:0:0: [sdc] Attached SCSI removable disk  
 Sep 20 18:59:52 petar-desktop kernel: [   12.816597] sd 4:0:0:0: Attached scsi generic sg3 type 0  
 Sep 20 18:59:52 petar-desktop kernel: [   12.820631] sd 4:0:0:1: [sdd] Attached SCSI removable disk  
 Sep 20 18:59:52 petar-desktop kernel: [   12.820729] sd 4:0:0:1: Attached scsi generic sg4 type 0  
 Sep 20 18:59:52 petar-desktop kernel: [   12.860194] sd 4:0:0:2: [sde] Attached SCSI removable disk  
 Sep 20 18:59:52 petar-desktop kernel: [   12.860298] sd 4:0:0:2: Attached scsi generic sg5 type 0  
 Sep 20 18:59:52 petar-desktop kernel: [   12.861705] sd 4:0:0:3: [sdf] Attached SCSI removable disk  
 Sep 20 18:59:52 petar-desktop kernel: [   12.861790] sd 4:0:0:3: Attached scsi generic sg6 type 0  
 Sep 20 18:59:58 petar-desktop kernel: [   19.068095] Bluetooth: BNEP (Ethernet Emulation) ver 1.3  
 Sep 20 18:59:58 petar-desktop kernel: [   19.068099] Bluetooth: BNEP filters: protocol multicast  
 Sep 20 18:59:58 petar-desktop kernel: [   19.080456] Bridge firewalling registered  
 Sep 20 19:00:03 petar-desktop kernel: [   23.775878] r8169: eth0: link down  
 Sep 20 19:00:03 petar-desktop kernel: [   23.776047] ADDRCONF(NETDEV_UP): eth0: link is not ready  
 Sep 20 19:00:05 petar-desktop pulseaudio[3720]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.  
 Sep 20 19:00:17 petar-desktop kernel: [   38.005062] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
 

 

 dmesg |tail -20
 [   12.812224] usb-storage: device scan complete  
 [   12.812724] scsi 4:0:0:0: Direct-Access     USB2.0   CardReader CF    0100 PQ: 0 ANSI: 0  
 [   12.813090] scsi 4:0:0:1: Direct-Access     USB2.0   CardReader SM XD 0100 PQ: 0 ANSI: 0  
 [   12.813464] scsi 4:0:0:2: Direct-Access     USB2.0   CardReader MS    0100 PQ: 0 ANSI: 0  
 [   12.813838] scsi 4:0:0:3: Direct-Access     USB2.0   CardReader SD    0100 PQ: 0 ANSI: 0  
 [   12.815568] sd 4:0:0:0: [sdc] Attached SCSI removable disk  
 [   12.816597] sd 4:0:0:0: Attached scsi generic sg3 type 0  
 [   12.820631] sd 4:0:0:1: [sdd] Attached SCSI removable disk  
 [   12.820729] sd 4:0:0:1: Attached scsi generic sg4 type 0  
 [   12.860194] sd 4:0:0:2: [sde] Attached SCSI removable disk  
 [   12.860298] sd 4:0:0:2: Attached scsi generic sg5 type 0  
 [   12.861705] sd 4:0:0:3: [sdf] Attached SCSI removable disk  
 [   12.861790] sd 4:0:0:3: Attached scsi generic sg6 type 0  
 [   19.068095] Bluetooth: BNEP (Ethernet Emulation) ver 1.3  
 [   19.068099] Bluetooth: BNEP filters: protocol multicast  
 [   19.080456] Bridge firewalling registered  
 [   23.775878] r8169: eth0: link down  
 [   23.776047] ADDRCONF(NETDEV_UP): eth0: link is not ready  
 [   38.005062] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready  
 [   48.756010] wlan0: no IPv6 routers present  
 

Hope this helps :)

---

### Post by louigi600 on 2009-09-20
Are the chunks you gave me relevant to the interval starting from when the link goes down to when the link comes back up ? 
If so it looks like you temporarely disassociated.
what's iwconfig telling you ?

Anyway is you computer in a much different place with respect to the others that work fine ?
I've seen this happen a lot in 2 circumstances:
1) the is another access point in range that is less the 5channels away from yours
2)the pc is in a position non faivorable to reception hence the wifi card goes automatically to full power .... and ma overheat and temporarily do a thermal shutdown untill it cools then functions again.

Does anything change if you go tight close to your AP ?
Can you scan wireles networks to seeif there are any other AP in range that might be disturbing you ?

---

### Post by Petarrrr on 2009-09-21
I doubt it a lot, there is absolutely no other wireless access points around, and i have a PCI fan card underneath my wireless adapter.
It continues to connect several times now, and it connects ofr a bit but the internet doesnt work, then it drops out and tries to connect again.

iwconfig output:
  	 	 	 	 	 	  lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 wlan0     IEEE 802.11g  ESSID:off/any   
           Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated    
           Bit Rate:54 Mb/s   Sensitivity=-200 dBm   
           RTS thr=2346 B   Fragment thr=2346 B    
           Power Management:off  
           Link Quality:0  Signal level:0  Noise level:0  
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0  
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0  
 

 pan0      no wireless extensions.

---

### Post by louigi600 on 2009-09-21
> Link Quality:0  Signal level:0  Noise level:0
Does not look good

I've a wireless child care unit that when turned on does the following things:
a) makes my wifi voip unusable
b) makes my esprimo disassociate untill I reconnect
c) does nothing to all my other wifi stuff

Not having any other AP around is not sufficient to totally exclude interferance.\

Another thing that can happen:
Some drivers let you turn on and off specific antennas in the wifi card ... make sure that the default enables the antenna you are using or fiddle with the module options to turn it on.

Never had the wifi card you are using .... but some do require firmware do be loaded prior to functioning correctly.
Can change channel ? "sudo iwconfig wlan0 channel 9"

Can you do this for me:
remove the modules for your wifi card,
run "sudo dmesg -c"
reload the wifi modules
capture the whole output that dmesg produces now

---

### Post by Petarrrr on 2009-09-22
No errors came up while trying to change the channel, so I assume that worked accordingly.

On my windows drivers they never had any option to disable or enable the aerial. 
I uninstalled the modules and re-installed as you requested

Here is the output:
                                 [ 3480.404816] ndiswrapper: device wlan0 removed  
 [ 3480.404839] ndiswrapper 0000:04:01.0: PCI INT A disabled  
 [ 3480.404938] usbcore: deregistering interface driver ndiswrapper  
 [ 3480.419108] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)  
 [ 3480.437340] ndiswrapper: driver wg311v3 (NETGEAR,02/22/2005,3.1.1.7) loaded  
 [ 3480.437627] ndiswrapper 0000:04:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22  
 [ 3480.437644] ndiswrapper 0000:04:01.0: setting latency timer to 64  
 [ 3480.439080] ndiswrapper: using IRQ 22  
 [ 3480.697267] wlan0: ethernet device 00:1b:2f:bf:32:43 using NDIS driver: wg311v3, version: 0x3000036, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 11AB:1FAA.5.conf 
 [ 3480.697289] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK  
 [ 3480.725593] usbcore: registered new interface driver ndiswrapper  
 [ 3482.496810] ADDRCONF(NETDEV_UP): wlan0: link is not ready  
 [ 3492.364649] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready  
 

Thanks very much for your support btw :)

---

### Post by louigi600 on 2009-09-22
Sorry ... you are using ndiswrapper (which means using windows drivers in linux environment) ... if I were your PC I'd do the same :-D 
I think that it might be no longer necessary to use ndiswrapper for your wifi card (I'm using native iwlagn on my 4965 and it's working fine) .... and if it is I've no experience with doing that ... sorry.

---

### Post by Petarrrr on 2009-09-22
Oh i see, I think I might do a re-format and start from scratch cause I just can't seem to get it working. I might disable WPA on my router too and just used WEP and mac filtering. Where I am located i doubt it would get hacked anyway.
Thanks for your help louigi :)

---

