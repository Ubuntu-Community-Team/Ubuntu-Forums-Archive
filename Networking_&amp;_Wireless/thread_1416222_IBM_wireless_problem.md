---
title: "IBM wireless problem"
date: 2010-02-25
forum: Networking &amp; Wireless
---

### Post by NCSU-Cohiba on 2010-02-25
I've dug through the forums listed but can't find an answer for my particular problem.  If anyone out there can help I would appreciate it.

I have an IBM ThinkPad T30 with 512MB RAM and the newest Ubuntu installed on it.  I can see my wireless network come up and given the option to connect.  Here is where my problems start.

My network, named Stuckey has security on it but I don't know what?  How can I find this out and what I need to type it to let me access my network.  I know my network password but that's about it.  Sorry if this is a repeat question.

Thanks.

---

### Post by chili555 on 2010-02-25
Usually, when you select your network and ask it to connect, you will get a prompt for the password. Just fill it in and connect. Is it not working as I described?

If you are curious, you can do:```
sudo iwlist wlan0 scan
```Substitute your wireless interface, if it's not wlan0. The encryption will show as 'Encryption key:on' if it's WEP and WPA and a lot of details if it's WPA.

Usually, Network Manager figures that out for you.

---

### Post by NCSU-Cohiba on 2010-02-25
When I try to connect it asks me for a password.  My options for security type are . . . 

WEP 128-bit Passphrase

WEP 40/128-bit Key

LEAP

Dynamic WEP (802.1x)

I really don't know what I have.  I know my password I use on my other Dell laptop so I assume it will work on this computer.

How would I find this out?

---

### Post by 2hot6ft2 on 2010-02-25
You could just try them 1 at a time with your password.

---

### Post by NCSU-Cohiba on 2010-02-25
**  Firmware Version**                                                    		            			1.00.00 (May  5 2007 08:49:16)           		                                            
                                           	   **LAN/WLAN MAC**                     	                                                                  	00:17:3F:C0:4C:EF                       		 		       		                                            	**   Boot Version**                                                                  V0.09                                                                  
                                           	   [**IP Address**]("http://192.168.2.1/lan_main.stm")                                                                  192.168.2.1                       		 		 		                                            **   Hardware**                                                                  	F5D8233-4-v1(01A)                                                                  
                                              [**Subnet Mask**]("http://192.168.2.1/lan_main.stm")                                                                  255.255.255.0                       		 		                                                           **   Serial No.**                                             				12725823351854 			                                            
                         [**DHCP Server **]("http://192.168.2.1/lan_main.stm")  Enabled (7 LAN,  2 WLAN  Clients)   		 		 		 			 			
			 			
			 			
			 			
			 			
                   		  		 		 ** Internet Settings** 
 			
			                      	** Features**                                         	                   	
          		  		 		    [**WAN MAC Address**]("http://192.168.2.1/wan_dhpc_mac.stm")  00:17:3F:C0:4C:F0  		 			 			
			 				 				   [**NAT**]("http://192.168.2.1/system.stm") 			 			 				 				Enabled  				 			 		                                      [**Connection Type**]("http://192.168.2.1/wan_main.stm")  Dynamic  
     [**Firewall Settings**]("http://192.168.2.1/firewall_main_0.stm")  Enabled    			 		 		    [**Subnet Mask**]("http://192.168.2.1/wan_main.stm")  [COLOR=#000000]255.255.248.0[/COLOR]			 			 			
		     [**SSID**]("http://192.168.2.1/wireless_id.stm")[FONT=Verdana][SIZE=1][COLOR=#004263] 	[/COLOR][/SIZE][/FONT]  Stuckey    		  		 		    [**WAN IP**]("http://192.168.2.1/wan_main.stm")  75.189.137.191   		 			 			
		     [**Security**]("http://192.168.2.1/wireless_e.stm")  WPA-Personal ( PSK )    		  		 		    [**Default Gateway**]("http://192.168.2.1/wan_main.stm")  75.189.136.1   		 			 			
				   [**UPnP**]("http://192.168.2.1/system.stm")  Enabled   		 		 		 		    [**DNS Address**]("http://192.168.2.1/setup_dns.stm")  209.18.47.61  			 			
				   [**Remote Management**]("http://192.168.2.1/system.stm")  Disabled 
That popped up when I typed it in.  I have no clue what any of this means.

---

### Post by 2hot6ft2 on 2010-02-25
Or login on to the router on the Dell and see how you have the router set up. The router should be at 192.168.0.1 or 192.168.1.1.

---

### Post by 2hot6ft2 on 2010-02-25
That shows your security as WPA Personal
> Security WPA-Personal ( PSK ) 
I must be getting tired I keep messing up my posts so G'night all.

---

### Post by NCSU-Cohiba on 2010-02-25
That's what I had to do, it's in my last post.  I have almost no clue what any of that means though.

---

### Post by NCSU-Cohiba on 2010-02-25
> **2hot6ft2 said:**
> That shows your security as WPA Personal

I must be getting tired I keep messing up my posts so G'night all.


Yes, and when i chose the wpa 128-bit passphrase option and enter my password nothing happens

---

### Post by chili555 on 2010-02-25
It's not WPA 128-bit that you see, it's WEP. You are looking for an option of WPA-PSK.> Security WPA-Personal ( PSK )Doesn't that pop up when you ask Network Manager to connect to 'Stuckey?'

WEP and WPA are two different things; apples and oranges.

---

### Post by NCSU-Cohiba on 2010-02-25
When prompted for security I have 4 options to chose from and then enter a password or a key.  These four are . . . 

WEP 128-bit Passphrase

WEP 40/128-bit Key

LEAP

Dynamic WEP (802.1x)

Is the option I need not offered and if so why not?

---

### Post by NCSU-Cohiba on 2010-02-25
I've done some more research and I think I might need to download and install the following file . . . 
sudo apt-get install network-manager-gnome

Where would I go to get this?

---

### Post by chili555 on 2010-02-25
We don't know why quite yet. Let's see:```
sudo iwlist wlan0 scan
```Substitute your wireless interface, if it's not wlan0. Find out in:```
iwconfig
```Also, may we see:```
sudo iwlist wlan0 auth
```Also, please search in System -> Admin -> Synaptic and verify that wpa-supplicant is installed. It is installed if the little box is green.

---

### Post by chili555 on 2010-02-25
> I've done some more research and I think I might need to download and install the following file . . .
sudo apt-get install network-manager-gnomeIf you can click an icon, see networks and try to get connected and are prompted for a password, then you already have Network Manager. Do you see something like this?

---

### Post by NCSU-Cohiba on 2010-02-25
> **chili555 said:**
> We don't know why quite yet. Let's see:```
sudo iwlist wlan0 scan
```Substitute your wireless interface, if it's not wlan0. Find out in:```
iwconfig
```Also, may we see:```
sudo iwlist wlan0 auth
```Also, please search in System -> Admin -> Synaptic and verify that wpa-supplicant is installed. It is installed if the little box is green.

Ok, I'm sorry guys but I have no clue what to do with or what the code above means.  I did open the synaptic package manager but didn't see a little green box.  Sorry to be such a hassle but I'm basically a noob with this.  Does this help you to maybe help me more any?  Thanks

---

### Post by NCSU-Cohiba on 2010-02-25
> **chili555 said:**
> If you can click an icon, see networks and try to get connected and are prompted for a password, then you already have Network Manager. Do you see something like this?

Yes I do see this and can click my network.

As for the little green box, the wpasupplicant is installed because the little box is green.

---

### Post by chili555 on 2010-02-25
Open Applications -> Accessories -> Terminal and type in:```
iwconfig
```You will get a result somthing like this:> iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

[COLOR="Blue"]wlan0[/COLOR]     IEEE 802.11abg  ESSID:"mylilrouter"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 99:24:56:2A:D7:99   
          Bit Rate=54 Mb/s   Tx-Power=15 dBmMy wireless interface is the one with all the details. Yours may be eth1 or ra0 or some other. Whatever it is, use it in the terminal again:```
sudo iwlist [COLOR="Blue"]wlan0 [/COLOR]scan
```That means, scan for networks and tell me something about each one. And then:```
sudo iwlist [COLOR="Blue"]wlan0[/COLOR] auth
```That means, tell us what our wireless card is capable of in terms of encryption: WEP, WPA and/or Klingon.

---

### Post by NCSU-Cohiba on 2010-02-25
This is everything from what you told me to search copied and pasted from the IMB with ubuntu laptop running on a plugged in ethernet cable.

bryce@bryce-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  Nickname:"Prism  I"
          Mode:Managed  Access Point: None   Bit Rate:2 Mb/s   
          Sensitivity:1/3  
          Retry short limit:8   RTS thrff   Fragment thrff
          Power Managementff
          Link Quality=0/92  Signal level=-68 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

irda0     no wireless extensions.

bryce@bryce-laptop:~$ sudo iwlist eth1 scan
[sudo] password for bryce: 
fSorry, try again.
[sudo] password for bryce: 
Sorry, try again.
[sudo] password for bryce: 
eth1      Scan completed :
          Cell 01 - Address: 00:25:BC:8A:42:C9
                    ESSID:"Nolan's Network"
                    Mode:Master
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Signal level:20 dBm  Noise level:18 dBm
                    Encryption keyn
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:capab=0x0431
                    Extra: Last beacon: 5252ms ago
          Cell 02 - Address: 00:1A:70:E2:22:E8
                    ESSID:"linksys_ping"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Signal level:29 dBm  Noise level:13 dBm
                    Encryption keyn
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:capab=0x0411
                    Extra: Last beacon: 5252ms ago
          Cell 03 - Address: 00:17:3F:C0:4C:EF
                    ESSID:"Stuckey"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Signal level:56 dBm  Noise level:13 dBm
                    Encryption keyn
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:capab=0x0411
                    Extra: Last beacon: 5252ms ago
          Cell 04 - Address: 00:22:6B:53:81:70
                    ESSID:"tammy-coby"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Signal level:27 dBm  Noise level:12 dBm
                    Encryption keyn
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:capab=0x0411
                    Extra: Last beacon: 16ms ago
          Cell 05 - Address: 00:25:86:CB:89:0A
                    ESSID:"kallipolis"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Signal level:40 dBm  Noise level:12 dBm
                    Encryption keyn
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Extra:bcn_int=100
                    Extra:capab=0x0431
                    Extra: Last beacon: 16ms ago
          Cell 06 - Address: 00:1F:33:22:F3:90
                    ESSID:"NETGEAR"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Signal level:25 dBm  Noise level:13 dBm
                    Encryption keyff
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:capab=0x0421
                    Extra: Last beacon: 5252ms ago
          Cell 07 - Address: 00:13:10:17:DA:07
                    ESSID:"Wenger Network"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Signal level:22 dBm  Noise level:17 dBm
                    Encryption keyn
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:capab=0x0411
                    Extra: Last beacon: 5252ms ago
          Cell 08 - Address: 00:23:69:25:5B:B9
                    ESSID:"white and nordic"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Signal level:47 dBm  Noise level:12 dBm
                    Encryption keyn
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:capab=0x0011
                    Extra: Last beacon: 16ms ago
          Cell 09 - Address: 00:09:5B:85:79:F4
                    ESSID:"wifi"
                    Mode:Master
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Signal level:17 dBm  Noise level:12 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Extra:bcn_int=100
                    Extra:capab=0x0431
                    Extra: Last beacon: 16ms ago
          Cell 10 - Address: 34:EF:44:55:EC:51
                    ESSID:"2WIRE950"
                    Mode:Master
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Signal level:44 dBm  Noise level:18 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:capab=0x0431
                    Extra: Last beacon: 16ms ago
          Cell 11 - Address: 00:23:69:68:0B:30
                    ESSID:"303"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Signal level:25 dBm  Noise level:34 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:capab=0x0411
                    Extra: Last beacon: 16ms ago

bryce@bryce-laptop:~$ sudo iwlist eth1 auth
eth1      unknown authentication information.



bryce@bryce-laptop:~$ sudo wilist eth1 auth
sudo: wilist: command not found
bryce@bryce-laptop:~$ 


Hope this helps.

---

### Post by chili555 on 2010-02-25
Is your password 10 or 26 numbers and letters? If so, please try it in WEP 40/128-bit *Key*.

I am not too sure this is a WPA network, actually:> Cell 03 - Address: 00:17:3F:C0:4C:EF
ESSID:"Stuckey"
Mode:Master
Channel:6
Frequency:2.437 GHz (Channel 6)
Signal level:56 dBm Noise level:13 dBm
[COLOR="Red"]Encryption key:on[/COLOR]
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
18 Mb/s; 36 Mb/s; 54 Mb/s
Extra:bcn_int=100
Extra:capab=0x0411
Extra: Last beacon: 5252ms agoThis is usually a sign of a WEP encrypted network. Moreover, not very many (any??) Prism cards do WPA.> eth1 IEEE 802.11b Nickname:"[COLOR="Blue"]Prism[/COLOR] I"

Is it a PCMCIA card, that is, a card that slides in a slot in your laptop? If so, please post:```
lspcmcia -v
```Thanks.

---

### Post by NCSU-Cohiba on 2010-02-25
Ok, there is no card that slides into the side of the laptop and therefore I assume its internal.  About the 10 or 26 letter password.  The password I use for logging into the wireless on my dell (which has windows xp) its 12 letters (well 10 letters and 2 numbers).  The password is 95h*********, am I missing this 10 or 26 letter code somewhere?  This might be a really stupid misunderstanding on my part.

When I chose WEP 40/128-bit Key it asks for a Key.  I assume this is the 10 or 26 letter code you're talking about.  If it is, where would I find this?

Thanks again

---

### Post by chili555 on 2010-02-25
I suspect your router is set up for WPA but that your wireless card is too old to do WPA, but it is only a suspicion. Let's take a look at, from the terminal:```
lspci -nn
```If you can, feel free to skip all the parts that are clearly not a wireless card.

---

### Post by NCSU-Cohiba on 2010-02-25
Sorry, I did'nt know what to include or not include but it's not as much as last time.

bryce@bryce-laptop:~$ lspci -nm
00:00.0 "0600" "8086" "1a30" -r04 "" ""
00:01.0 "0604" "8086" "1a31" -r04 "" ""
00:1d.0 "0c03" "8086" "2482" -r02 "1014" "0220"
00:1d.1 "0c03" "8086" "2484" -r02 "1014" "0220"
00:1d.2 "0c03" "8086" "2487" -r02 "1014" "0220"
00:1e.0 "0604" "8086" "2448" -r42 "" ""
00:1f.0 "0601" "8086" "248c" -r02 "" ""
00:1f.1 "0101" "8086" "248a" -r02 -p8a "1014" "0220"
00:1f.3 "0c05" "8086" "2483" -r02 "1014" "0220"
00:1f.5 "0401" "8086" "2485" -r02 "1014" "0508"
00:1f.6 "0703" "8086" "2486" -r02 "1014" "0223"
01:00.0 "0300" "1002" "4c57" "1014" "0517"
02:00.0 "0607" "104c" "ac55" -r01 "1014" "0512"
02:00.1 "0607" "104c" "ac55" -r01 "1014" "0512"
02:02.0 "0280" "1260" "3873" -r01 "8086" "2513"
02:08.0 "0200" "8086" "1031" -r42 "1014" "0209"
bryce@bryce-laptop:~$ 

Does this tell you anything?

thanks

---

### Post by chili555 on 2010-02-25
lspci -n[COLOR="Red"]n[/COLOR], please.

---

### Post by NCSU-Cohiba on 2010-02-25
bryce@bryce-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge [8086:1a30] (rev 04)
00:01.0 PCI bridge [0604]: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge [8086:1a31] (rev 04)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #1 [8086:2482] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #2 [8086:2484] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #3 [8086:2487] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 42)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801CAM ISA Bridge (LPC) [8086:248c] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801CAM IDE U100 Controller [8086:248a] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801CA/CAM SMBus Controller [8086:2483] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801CA/CAM AC'97 Audio Controller [8086:2485] (rev 02)
00:1f.6 Modem [0703]: Intel Corporation 82801CA/CAM AC'97 Modem Controller [8086:2486] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] [1002:4c57]
02:00.0 CardBus bridge [0607]: Texas Instruments PCI1520 PC card Cardbus Controller [104c:ac55] (rev 01)
02:00.1 CardBus bridge [0607]: Texas Instruments PCI1520 PC card Cardbus Controller [104c:ac55] (rev 01)
02:02.0 Network controller [0280]: Intersil Corporation Prism 2.5 Wavelan chipset [1260:3873] (rev 01)
02:08.0 Ethernet controller [0200]: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller [8086:1031] (rev 42)
bryce@bryce-laptop:~$

Sorry about that, here it is.

---

### Post by NCSU-Cohiba on 2010-02-25
I don't know if this helps but I can connect to other wireless networks around me that the people have just not locked up, i.e. no security, you can just connect and "steal" internet.  I want to use my internet though.

---

### Post by chili555 on 2010-02-25
Please also post:```
lsmod
```Thanks.

This may be a clue: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/282840](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/282840)

I'll check back tomorrow.

---

### Post by NCSU-Cohiba on 2010-02-25
Oh, that would be a bummer if just this laptop had a problem with this.  Here is the lsmod code.

bryce@bryce-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
pcmcia                 36808  0 
hostap_pci             48652  0 
hostap                103360  1 hostap_pci
lib80211                6432  2 hostap_pci,hostap
joydev                 10240  0 
snd_intel8x0           30168  3 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
iptable_filter          3100  0 
snd_seq_oss            28576  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
orinoco_pci             4700  0 
orinoco                63600  1 orinoco_pci
yenta_socket           24296  2 
rsrc_nonstatic         11644  1 yenta_socket
pcmcia_core            36528  3 pcmcia,yenta_socket,rsrc_nonstatic
ppdev                   6688  0 
psmouse                56500  0 
serio_raw               5280  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
shpchp                 32272  0 
thinkpad_acpi          67108  0 
led_class               4096  1 thinkpad_acpi
nvram                   7528  1 thinkpad_acpi
parport_pc             31940  1 
nsc_ircc               20976  0 
irda                  189564  1 nsc_ircc
crc_ccitt               1852  1 irda
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
e100                   32420  0 
mii                     5212  1 e100
radeon                636000  0 
ttm                    36212  1 radeon
drm                   159584  2 radeon,ttm
i2c_algo_bit            5760  1 radeon
video                  19380  0 
output                  2780  1 video
floppy                 54916  0 
intel_agp              27484  1 
agpgart                34988  3 ttm,drm,intel_agp
bryce@bryce-laptop:~$ 

Thanks for all of your help, I will check back tomorrow after work and maybe you will have a solution.  thanks again.

---

### Post by chili555 on 2010-02-25
> Intersil Corporation Prism 2.5 Wavelan chipset [[COLOR="Blue"]1260:3873[/COLOR]]From the bug report:> Same here with Intersil prism ([COLOR="Blue"]1260:3873[/COLOR]) wlan device on 9.10.
Detailed information:
--- snip ---
To summarize: ***orinoco_pci will not provide WPA*** (at least not for this device) and hostap_pci does not work (anymore!)Ouch!!!> orinoco_pci 4700 0
orinoco 63600 1 orinoco_pci

---

