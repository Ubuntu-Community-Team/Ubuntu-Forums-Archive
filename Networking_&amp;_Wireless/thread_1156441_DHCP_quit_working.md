---
title: "DHCP quit working"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by Iowan on 2009-05-11
I know there's a similar thread nearby, but rather than hijack it ...
Dual-boot HP laptop was working fine wired/wireless.  After wifi-ing in the restaurant yesterday, I took machine home and plugged back into wired network. No DHCP address (although lights on switches blink).  Tried setting up static lease - no go.  
  Static address works! A manual DNS entry in /etc/resolv.conf got it back on internet, but what happened to DHCP? The Windows side still works via DHCP. This machine uses r8169 driver. Any glitches for this driver?
   Is there something I could run on the DHCP server (Breezy) or another machine to monitor packets to see if valid DHCP requests are being sent? 
I'm thankful that it will still access network/internet... and equally thankful that the problem wasn't the wireless side (my weakest area), but I'd still *like* to have it work like it did last Friday...

Problem is similar to bottom of [this]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/368709") bug report.

---

### Post by Iowan on 2009-05-13
Update: I commented out my changes in /etc/network/interfaces and /etc/resolv.conf - just to see if it'd play nice today... still not playing nice.
 Disabled wireless, unplugged machine and rebooted, no network (although wireless re-enabled itself... the checkbox, anyway). Plugged in the cable, globes spin, no connection.
Built "manual connection" through the applet. First it tried "auto eth0", then succeeded with manual connection. Deleted "auto eth0", rebooted, and built another "auto eth0". Reboot again - same thing. Failure via DHCP (auto eth0), success via manual connection.
Still curious why DHCP has failed.

---

### Post by Iowan on 2009-05-14
[Updated update] Per a suggestion in another [thread]("http://ubuntuforums.org/showpost.php?p=7276275&postcount=8"), I tried commenting out the "option rfc3442" line and removing the reference in the "request" line - rebooted, and got a DHCP address.  (Thanks Peter09) We'll see if the "fix" stays fixed...

It should be noted that the actual path is /etc/dhcp3/dhclient.conf. That got edited a couple of posts later than the one I linked.

---

### Post by xAirrick on 2009-07-25
You are the man IOWAN.

Commenting out that line in /etc/dhcp3/dhclient.conf also fixed my DHCP problems :D

---

### Post by no_angst on 2009-08-11
No doubt!  You rock!  Thanks!

---

### Post by Lutin on 2009-08-12
Thanks for that. Managed to get my Dell D400 back onto wireless thanks to this.

---

### Post by shredder12 on 2009-08-12
btw.. what's the issue with this line containing options rfc3442..??

---

### Post by Iowan on 2009-08-12
Apparently rfc3442 is for classless static routes. There's a bug report [here]("https://lists.ubuntu.com/archives/ubuntu-server-bugs/2009-February/009768.html"). One would like to think that a DHCP server that didn't understand it would ignore it, but some (my Breezy server for one) just give up, and don't process the request - meaning no DHCP address... at least that's my interpretation - so far.

---

### Post by wjamoore on 2009-08-22
Hi

This didn't help me.  Same issue here.  Laptop sees the network (full signal) but fails to connect.

I am using a netgear wrn2000 wirless router with no security for now

in iwconfig it has the essid OK but is not associated

also scanning for network gives wlan0 no scan results.

Interestingly I can connect without problem at hotspots, but I may still have an issue there as I couldn't get on the web yesterday

So what is different about wireless hotspots versus wireless routers???

Having trawled the forums for days now I can see that:

1.  this is a common problem
2. it is not associated directly with the hardware because I see it on multiple hardware platforms and therefore a global solution should be found.  I notice on the forums that the same issue is split mutiple times for computer and wifi card 

I think it is a DHCP isue, and for me I think network management is doing something strange.  i tried nm & wicd.. same... I tried madwifi... same

any help appreciated

Aaron

---

### Post by wjamoore on 2009-08-22
and another interestinbg point.

What's Samba up to here?

	 	 Reconfiguring network interfaces...                                          Internet Systems Consortium DHCP Client V3.1.1  
 Copyright 2004-2008 Internet Systems Consortium.  
 All rights reserved.  
 For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)  
 

 Listening on LPF/wlan0/00:19:7e:84:7e:44  
 Sending on   LPF/wlan0/00:19:7e:84:7e:44  
 Sending on   Socket/fallback  
 DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6  
 DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13  
 DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15  
 DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16  
 DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11  
 No DHCPOFFERS received.  
 No working leases in persistent database - sleeping.  
  * Reloading /etc/samba/smb.conf smbd only  
    ...done.  
 

Is this relevant or not?

thanks

aaron

---

### Post by bab1 on 2009-08-22
> **wjamoore said:**
> and another interestinbg point.

What's Samba up to here?

	 	 Reconfiguring network interfaces...                                          Internet Systems Consortium DHCP Client V3.1.1  
 Copyright 2004-2008 Internet Systems Consortium.  
 All rights reserved.  
 For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)  
 

 Listening on LPF/wlan0/00:19:7e:84:7e:44  
 Sending on   LPF/wlan0/00:19:7e:84:7e:44  
 Sending on   Socket/fallback  
 DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6  
 DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13  
 DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15  
 DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16  
 DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11  
 No DHCPOFFERS received.  
 No working leases in persistent database - sleeping.  
  * Reloading /etc/samba/smb.conf smbd only  
    ...done.  
 

Is this relevant or not?

thanks

aaron

Aaron,

It sure is.  The host is looking for a DHCP server. When the host finds no servers i.e. No DHCPOFFERS received.  The host looks for a previously issued leases.  It finds none and ends its work.  

The Samba daemon will reload anytime the IP address changes. In this case it appears to anticipate the change.  This is handled by a script in dhcp-hooks I believe.

This problem could be that the DHCP server and the DHCP client are referring to non compatible RFC directives.  This appears to be the case with Iowan's setup.

In any event the log you have shown indicates the DHCP server is not responding to the clients request and the Samba server is grumping about it.

---

### Post by wjamoore on 2009-08-22
Thanks for the reply... Ok so we're closing in on this I think

Looking at the NM for wireless and in I have it set up for auto DHCP but the DHCP Client ID remains open for editing.

I put in the providers ADSL modem IP there and it still doesn't work, but I get a pile of things going on with wlan0 and wlan master that didn't happen before.  

i'd paste it in but I've switched off the laptop due to lack of interest for the day... and vino rosso is calling 

So do you know what should go there??  I'll see if there is any relevant how to on NM.

thanks

Aaron

---

### Post by wjamoore on 2009-08-23
OK so I think the problem is my wireless N router and my ath5K driver.

i read that ath9K does wireless N.  Does anyone know if this is true and if yes do I face any problems??

I wonder how many people are screwing up their systems when they really need to know the wireless frequency compatibility.  This is not mentioned of course on the router documentation.

Is it any wonder I stick to vinyl and tubes for music? 

thanks in advance

Aaron

---

### Post by wjamoore on 2009-08-23
and a bit more info.

wlan0 is scanning....  iwlist scan

wlan0     Scan completed :
          Cell 01 - Address: D6:6A:86:F7:56:7F
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:off
                    ESSID:"NETGEAR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000011fa1bb99a
                    Extra: Last beacon: 1352ms ago
                    IE: Unknown: 00074E455447454152
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401080800000000000000000000000000000000000000
                    IE: Unknown: 3D1601080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: DD820050F204104A000110104400010210570001001041000100103B00010310470010565AA94967C14C0EAA8FF349E6F593111021000D4E6574676561722C20496E632E10230007574E523230303010240007574E523230303010420004353637381054000800060050F204000110110007574E5232303030100800020084103C000103
          Cell 02 - Address: 00:1F:33:F2:54:E8
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:off
                    ESSID:"NETGEAR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000011fa1ca180
                    Extra: Last beacon: 1368ms ago
                    IE: Unknown: 00074E455447454152
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401080800000000000000000000000000000000000000
                    IE: Unknown: 3D1601080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: DD2C0050F204104A0001101044000102105700010010470010565AA94967C14C0EAA8FF349E6F59311103C000103

but there seems to be a lot of gibberish there.

Aaron

---

### Post by wjamoore on 2009-08-23
and now it's not scanning....

Aaron

---

### Post by mackerman on 2009-08-27
I solved my issue by removing network-manager from Synaptic.
I then downloaded wicd .deb (on a Windows XP machine) and installed it.

I rebooted, it didn't work, then I ran:
```
sudo dhclient eth0
```

As it was trying the DHCPDISCOVER commands, I unplugged my ethernet cable from the router and plugged it back in.  It then resolved an IP via DHCP.

Not sure why I had to do this pretty annoying gesture, but it worked.

---

### Post by DevinMcElheran on 2009-09-09
I have had very similar problems. I installed samba to access windows shares at school, then all of a sudden, no DHCP. I use Wicd, not sure which version. I'm using a school computer right now. I can't connect in any way, I even talked to the school IT guy, but he sayed "you get what you pay for with those machines", I'm using an Eeepc, and Ubuntu, how much better can it get? But any ways, no internet. I tried to comment out that line but still nothing. So I'm going to try reinstalling the Wicd.deb and see where that gets me.

---

### Post by Puzzled Guy on 2009-11-17
It worked! Thanks a lot! You rock :guitar: Now I can sleep at night.
I'll keep a backup of the file though, just in case...

---

### Post by luomo on 2009-12-01
[SIZE=3]My issue is not resolved by doing the given steps. My os is ubuntu 9.10. please help me.
Result after iwconfig:





cyber@cyber-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"UTStarcom"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:57:F4:F7:EF   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  Noise level=-70 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

cyber@cyber-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
cyber@cyber-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  Mode:Managed  Frequency:2.462 GHz  
          Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



[/SIZE]

---

### Post by phazer on 2009-12-02
Having similar problems, my network stopped working for some reason (connected via wifi), rebooted, and now nothing. I see the network with a iwconfig wlan0 scan, and authenticate fine againts it but I just don't get a IP, tried on my window box to see if it might be a dhcp server side issue, but it work perfectly in windows. Any ideads? I have tried the rfc3442 setting already

---

### Post by bedhead75 on 2010-01-07
I've had a similar issue where I couldn't access the internet through my own network via wireless, despite network manager listing it as connected.  This problem sometimes happens to me in Ubuntu 9.10 after a hard reboot, due to resume from suspend problems.  Unplugging my USB wireless adapter and plugging it back in always fixes the issue for me.

---

### Post by Iowan on 2010-01-07
Dunno if it's a Jaunty thing, laptop thing, 64-bit thing, etc., but the machine I set up with Karmic has the default settings for rfc3442, and works fine on DHCP.

---

### Post by IceCap on 2010-01-11
I have the same problem but intermittently (doesn't work most of the time).

  I have TrendNet wireless-n PCI card TEW-643PI using a RealTek rtl8190 chip.  Using ndiswrapper and associated driver (net8190p.inf/.sys).  Card is recognized using the driver in 9.10.  See the network.  Worked fine the first time I tried connecting.  Since then, it has been intermittent, mostly not being able to connect.  I'm using Airport Extreme from Apple set to WAP2 security (some reports indicate that disabling security "fixes" the issue).  I have exactly the same reports from iwconfig as someone listed here above.

  On my previous setup I had a Level One wireless-g PCI card using RealTek rtl8185 chip and a TrendNet wireless-g router.  It worked fine for months (using 8.04 and ndiswrapper) but then it started acting up in this same manner (not sure what triggered it, maybe I ran an update, which I guess you should never do on a MythTV system that works).

  Is it possible that there are some log files that need to be deleted for the DHCP IP lease to work correctly?  Or some files that if they are not there, they are automatically generated from some sort of a default setting but changed later on and that is what is causing the communication not to work (clearly I'm not an expert on this).

  I'm not sure how SMB comes into this, but does it help disabling it?

  IC

---

### Post by nathanieldouglas on 2010-01-16
Anyone care to fill me in how to comment out?  Quick step by step anyone?  Please?

Thank you!

---

### Post by Iowan on 2010-01-17
Open the file - system files probably require **sudo**:
```
sudo nano /etc/dhcp3/dhclient.conf
``` or for graphical editor ```
gksudo gedit /etc/dhcp3/dhclient.conf
```To comment out a line add a **#** at the beginning of the line - some programs also use a semicolon as comment indicator. That'll turn everything on the line into a comment. If you only want to "comment out" part of the line, the rest would need to be added back in - I usually put it on the following line.

---

### Post by Iowan on 2010-01-21
Although [this]("https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/94359") shouldn't be necessary - just in case. In brief, it tells the DHCP server that the machine is a M$:> 
Bee said on 2009-12-26:

Well thanks to everyone, but problem was actually solved by editing dhconfig.conf file: i added a string

send vendor-class-identifier "MSFT 5.0";

That solved the problem, and now my linux is masking under windows when log in.


---

### Post by leonlauncher on 2010-03-03
i had some problems with my DHCP too, im using WICD to connect to my home wireless router with WEP , i keep getting "cannot obtain ip address" error after validation , after adding the send vendor-class-identifier "MSFT 5.0";
 to the post-connection script on wicd, the wireless works fine.
Thanks Iowan.

---

### Post by Iowan on 2010-03-03
Still seems like a "cheat" but whatever works... if there's a better way, you can look for it at your leisure - Congrats!!!

---

### Post by Yairr on 2011-08-27
thanks!!!
i just installed ubuntu 11.04, dual boot with windows 7.
imy pc is connected to a Linksys with dd wrt (wired)

i had intermittent internet connectivity, after resetting my router i had no internet connection at all...

**editing /etc/dhcp/dhclient.conf. (without the "3") solved the issue**

thanks a lot!

---

### Post by ruivieira on 2012-10-25
This is brilliant.

Fixed my DHCP problem too.

Many thanks!

---

### Post by wildmanne39 on 2012-10-25
Old thread closed.

---

