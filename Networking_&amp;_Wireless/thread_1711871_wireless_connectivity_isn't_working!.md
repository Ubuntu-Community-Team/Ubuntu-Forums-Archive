---
title: "wireless connectivity isn't working!"
date: 2011-03-21
forum: Networking &amp; Wireless
---

### Post by breemiller on 2011-03-21
okay so I installed ubuntu 10.10 almost a week ago and the the wireless has yet to work from my home router. I've searched this forum and a number of other sources looking for a way to fix this.. obviously to no avail :P 

I am running 10.10 on a Compaq Presario CQ60 using a 
Realtek Semi conductor Co. Ltd. RTL8101E/ RTL8102E PCI
Express Fast Ethernet controller (rev 02)
Atheros Communication Inc. Ar5001 Wireless Network Adapter (rev 01)

the laptop is now recognizing my network but still cannot connect to the internet, update or download any software. When I attempt to update or open a browser page appears to load for few seconds before informing me that I have no available connections. --> a direct connection to the router doesn't fix this.

I'm reasonably sure the wireless driver is at least part of the problem.. and i've tried updating the driver by downloading driver to another device and installing driver on laptop from flashdrive but not sure how to go about this.. as i'm a fairly new linux user.

as mentioned before I've spent a pretty good chunk of time working on this and would greatly appreciate any and all help forum can offer.. b/c i'm beginning to miss my little compaq :(

---

### Post by conneco on 2011-03-22
If the laptop connects to the wireless then a good place to start is whats the output of

ifconfig

?

---

### Post by breemiller on 2011-03-22
took screenshot and saved it as I am obviously using another machine for internet use atm.

[http://i1219.photobucket.com/albums/dd436/breemiller1/ifconfigterminalcommand.jpg](http://i1219.photobucket.com/albums/dd436/breemiller1/ifconfigterminalcommand.jpg)

---

### Post by grahammechanical on 2011-03-22
From the screen shot the machine is not connected to the router even by ethernet cable. You should see RUNNING after BROADCAST. There should also be a inet addr: as the second line. This would have the router/modem's IP address. Something like 192.168.1.64. Underneath there should be a inet6 addr:

So, I question your comment

> the laptop is now recognizing my network The best that I can offer right now is this link

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Regards.

P.S. Try entering rfkill list  If you see soft blocked = yes, then the wireless adapter is turned off in software. It is not switched on in Network Manager. If you see hard blocked = yes. Then the wireless adapter is switched off by hardware. Is there a keyboard key that you need to press.

---

### Post by breemiller on 2011-03-23
yes it is weird.. but the network signal is there... it's just unusable from the laptop.. and when connection is attempted it boots the other devices off... i'm not sure where to go from here... 

below is the link to the screenshot for 'rfkill' 
[http://i1219.photobucket.com/albums/dd436/breemiller1/rfkill.png](http://i1219.photobucket.com/albums/dd436/breemiller1/rfkill.png)

---

### Post by conneco on 2011-03-23
By the look of your ifconfig the wireless card isnt up, 

try in a terminal 

iwconfig

this should list your wireless cards name like this

steve@mcr-pc-29334:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"f2\x0D\xB71X\xA3Z%]\x05\x17X\xE9^\xD4\xAB\xB2\xCD\xC6\x9B\xB4T\x11\x0E\x82tA!=\xDC\x87"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
vboxnet0  no wireless extensions.

you can see that my wireless card is wlan0

then once you know your wireless card name then type in terminal replacing wlan0 with your wifi card name(it may be wlan0 or ath0)

sudo ifconfig wlan0 up

then repost the output of ifconfig and see if it shows

EDIT***

To anyone who knows how do you wrap terminal output in this forum to keep it formated correctly? thanks

---

### Post by breemiller on 2011-03-23
okay posted result of ifconfig after other commands.. haven't checked to see if theres a difference yet 

also just thought of this but I did everything in the same terminal screen... do i need to reboot or anything for changes to take effect???

here is my results:
[http://i1219.photobucket.com/albums/dd436/breemiller1/ifconfigX2.png](http://i1219.photobucket.com/albums/dd436/breemiller1/ifconfigX2.png)

---

### Post by conneco on 2011-03-23
theres no ip showing in the ifconfig for wlan0, is you wifi connected in the network manager top right of your screen, if not and you can get it to show connected then give the ifconfig output to me that would be great, else what actually happens when you try to connect using the connection manager

---

### Post by breemiller on 2011-03-23
okay so when connected to network signal , when "sudo ifconfig walan up" command given in the terminal an error message followed saying "error when getting interface flags

heres the screen shot:
[http://i1219.photobucket.com/albums/dd436/breemiller1/scrnsht.png](http://i1219.photobucket.com/albums/dd436/breemiller1/scrnsht.png)

---

### Post by conneco on 2011-03-24
Okay so when you connect via the network manager you are getting an ip address so this is a good sign, what happens when you try and ping your router, If you don't know your routers IP the default is usually at the start or then end of the range so yours would be either 192.168.1.1 or 192.168.1.254 

try

```
ping 192.168.1.1
```

or 

```
ping 192.168.1.254
```

if one of them succeeds try pinging google

```
ping www.google.c.uk
```

and give us the output thanks

---

### Post by darkknight19820629 on 2011-03-24
I'm having a similar problem with the exception that I do have access via eth0.  However my wireless button was greyed out before I uninstalled Network Manager.  I used rfkill unblock all with mixed results, edited networkmanager.state so that wireless enabled would equal true. I have also reinstalled with no success. I am beginning to think I have a hardware issue with my wireless switch because I recently discovered that I could not toggle it; it is constantly glowing blue.  The whole thing started after I ended a process and had to do a hard shutdown; when I rebooted my wireless option in network manager was greyed out.  I also installed a different net manager which would actually scan for networks, but not pick any up.  I have also disabled the security for my wireless router, reenabled ssid broadcast, and removed MAC filtering...so I have effectively eliminated my router and network as the issue coupled with the glaringly obvious fact that I can connect to it with other computers, I just wanted to make sure though. I am using the Atheros 5001 adapter on a compaq (model number eludes me at the moment) I think it is close or is the Cq60-something, I can find out after my last class and repost.
ifconfig and iwconfig show that the card is there, but not working...not associated to an AP nor does it state that it is running....any help guys? I woudl really appreciate it, I haven't even listed ALL of the other things I have tried; let's just say I have logged about 13 hours trying to repair this issue...

---

### Post by conneco on 2011-03-24
@DarkKnight

you tried using wpa_supplicant to test if it can connect atall without the use of the network manager?

---

### Post by breemiller on 2011-03-24
okay so tried pinging the IP addresses you found and it ran what I think was a requesting process so I tried locating my router's IP with "route -n " anyways what both screens looked like are posted below... additionally during the ping of the 192.`68.1.1 (i think that was the first address u gave me) my wifi indicator light was blinking... I let this go on for over 2 hours and rebooted everything appears to be the same.. but I think were are on the right track!.. what now??

oh also one of the ping attempts i made asked me if i wanted to "broadcast" i allowed it to and terminal when into same requesting process? should just let this run? plz help... not sure what to do now...:P

n route output: [http://i1219.photobucket.com/albums/dd436/breemiller1/routencommand.png](http://i1219.photobucket.com/albums/dd436/breemiller1/routencommand.png)

ping 192.168.1.1: [http://i1219.photobucket.com/albums/dd436/breemiller1/ping19216811.png](http://i1219.photobucket.com/albums/dd436/breemiller1/ping19216811.png)

ping -b 192.168.1.0 : [http://i1219.photobucket.com/albums/dd436/breemiller1/ping-b19216810.png](http://i1219.photobucket.com/albums/dd436/breemiller1/ping-b19216810.png)

---

### Post by conneco on 2011-03-25
Yeah so your wifi card is up and running and you can communicate with your router so your almost there, what happens if you try

```
ping www.google.co.uk
```

---

### Post by darkknight19820629 on 2011-03-25
I am about to see what the result of wpa_supplicant is, but in the mean time, this is what I'm working with...

ben@Infiltrator:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSIDoff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thrff   Fragment thr:off
          Power Managementoff
          
ben@Infiltrator:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr xxxxxxx  
          inet addrx.xx1.11.253  Bcast:65.191.11.255  Mask:255.255.252.0
          inet6 addr: fe80:xfxxx:fe6d:6fac/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1097 errors:0 dropped:0 overruns:0 frame:0
          TX packets:118 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:87275 (87.2 KB)  TX bytes:18307 (18.3 KB)
          Interrupt:42 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

and every time I reboot it undoes the changes that I have made to /var/NetworkManager/NetworkManager.state
I have also reinstalled once again, this time without updates and my enable wireless button is still greyed out...
standby for more info, thanks for your help and patience

---

### Post by darkknight19820629 on 2011-03-25
This is what I got when I used the wpa_supplicant command...not sure if I used it properly, I'm new to Ubuntu and I had to reference the manual and help to use it...

ben@Infiltrator:~$ wpa_supplicant -c/etc/wpa_supplicant.conf -iwlan0 -d
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'default' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Failed to read or parse configuration '/etc/wpa_supplicant.conf'.
Failed to add interface wlan0
Cancelling scan request
Cancelling authentication timeout
ben@Infiltrator:~$

---

### Post by conneco on 2011-03-25
Yeah that means your conf file is bad, check it for typos or post it here obviously obscure your info

---

### Post by darkknight19820629 on 2011-03-25
there is a wpa_supplicant dir that contains the files "action_wpa.sh", "functions.sh", "ifupdown"  is that correct and if so do you want to see the output of all of them?

---

### Post by conneco on 2011-03-25
in the /etc/wpa_supplicant folder you need to create a file called wpa_supplicant.conf to be honest you can call it anything you want but as long as you refrence it in terminal when running wpa_supplicant,

the conf file should look like this

```
network={
	ssid="example"
	proto=WPA
	key_mgmt=WPA-PSK
	pairwise=TKIP
	group=TKIP
	psk="not so secure passphrase"
	wpa_ptk_rekey=600
}
```

obviously change the info to match yours

---

### Post by darkknight19820629 on 2011-03-25
im currently hardlined through eth0, and I have security currently disabled on my wifi, so should i still proceed as directed above?

---

### Post by conneco on 2011-03-25
you should put security on straight away at least WPA, very very dangerous running with no security. SET WPA security with TKIP encryption on your router and then you can pretty much use that conf bar the psk and ssid

NEVER USE WEP.... ever

---

### Post by darkknight19820629 on 2011-03-25
I previously had ssid broadcast disabled, MAC filtering enabled, I still have wpa2-personal enabled....these are the results of wpa_supplicant with a new conf file

ben@Infiltrator:/etc$ sudo wpa_supplicant -c/etc/wpa_supplicant.conf -iwlan0 -d
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'default' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Priority group 0
   id=0 ssid='******t'
Initializing interface (2) 'wlan0'
WEXT: cfg80211-based driver detected
SIOCSIFFLAGS: Operation not possible due to RF-kill
Could not set interface 'wlan0' UP
SIOCGIWRANGE: WE(compiled)=22 WE(source)=21 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: xx:xx:xx:xx:xx:xx
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
WPS: UUID based on MAC address - hexdump(len=16): xx xx xx xx xx xx xx xx xx xx xx xx xx xx xx xx
WPS: Build Beacon and Probe Response IEs
WPS:  * Version
WPS:  * Wi-Fi Protected Setup State (0)
WPS:  * Version
WPS:  * Wi-Fi Protected Setup State (0)
WPS:  * Response Type (2)
WPS:  * UUID-E
WPS:  * Manufacturer
WPS:  * Model Name
WPS:  * Model Number
WPS:  * Serial Number
WPS:  * Primary Device Type
WPS:  * Device Name
WPS:  * Config Methods (0)
WPS:  * RF Bands (3)
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x1002 ()
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1002 ()
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b1a len=8
l2_packet_receive - recvfrom: Network is down
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
ioctl[SIOCGIWSCAN]: Network is down
Failed to get scan results
Failed to get scan results - try scanning again
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
ioctl[SIOCSIWSCAN]: Network is down
Scan requested (ret=-1) - scan timeout 5 seconds
Failed to initiate AP scan.
Setting scan request: 10 sec 0 usec
EAPOL: disable timer tick
Scan timeout - try to get results
ioctl[SIOCGIWSCAN]: Network is down
Failed to get scan results
Failed to get scan results - try scanning again
Setting scan request: 1 sec 0 usec
Starting AP scan (broadcast SSID)
ioctl[SIOCSIWSCAN]: Network is down
Scan requested (ret=-1) - scan timeout 5 seconds
Failed to initiate AP scan.
Setting scan request: 10 sec 0 usec
Scan timeout - try to get results
ioctl[SIOCGIWSCAN]: Network is down
Failed to get scan results
Failed to get scan results - try scanning again
Setting scan request: 1 sec 0 usec
Starting AP scan (broadcast SSID)
ioctl[SIOCSIWSCAN]: Network is down
Scan requested (ret=-1) - scan timeout 5 seconds
Failed to initiate AP scan.
 I also just noticed something, so I'm going to sudo rfkill unblock all real quick and run the wpa_supplicant command again....

---

### Post by darkknight19820629 on 2011-03-25
ben@Infiltrator:/etc$ sudo rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
ben@Infiltrator:/etc$ 
 
this is after i rfkill unblock all, and run wpa_supplicant....

this is after i rfkill unblock all again.....well its the same as above

---

### Post by darkknight19820629 on 2011-03-25
I also just checked the additional drivers utility and it only displays an alternate nvidia graphics card driver....nothing else.

---

### Post by darkknight19820629 on 2011-03-25
ben@Infiltrator:/etc$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
ben@Infiltrator:/etc$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Operation not possible due to RF-kill
ben@Infiltrator:/etc$ sudo rfkill unblock all
ben@Infiltrator:/etc$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Operation not possible due to RF-kill
ben@Infiltrator:/etc$

---

### Post by conneco on 2011-03-26
Is your wifi switch on your laptop in the onnposition, and FYI even with ssid disabled and mac filtering on with a wifi sniffer like aircrack a person could be on your network with one glance at the screen

---

### Post by breemiller on 2011-03-26
hey, 

okay so sorry for the delay...

    So when I tried to ping google.co.uk  for a few seconds it looked like nothing happened and then message in terminal popped up that said-->     "ping: unknown host www.google.co.uk" ... also just to note I'm in the US so i tried ping [www.google.com](www.google.com) and nadda... the result was exactly the same...

 Anymore ideas??, thanks

---

### Post by conneco on 2011-03-27
try ping 8.8.8.8 (its google public dns server so if your computer is struggling resolving names then ping an IP can test if theres any net there atall)

that will see if it its a DNS problemo

edit 

Sorry just seen that your wifi card is reporting as hardware blocked, so in theory you shouldnt be able to connect to a network atall, 

Double check that your laptops WIFI switch is in the on pos, you may also have a key combo switch or both, sometimes its the FN key plus one of the F keys eg FN+f8, or there will be a rocker switch somewhere on the laptop to physically disab;le the wifi radio.

---

### Post by breemiller on 2011-03-27
okay so did double check wireless switch and it is activated b/c when i push it wireless network becomes disabled and invisible altogether.

I tried a wired connection to the router and ping 8.8.8.8 and the terminal when into the same process as ping 192.168.1.1 ... so hopefully that's a sign of hope? but google in browser is still a no go.
				 				 					 						[Forgotten Your Password?]("http://ubuntuforums.org/login.php?do=lostpw") 						
				 				 					 						[Forgotten Your Password?]("http://ubuntuforums.org/login.php?do=lostpw")

---

### Post by conneco on 2011-03-28
if you can ping 8.8.8.8 succesfully then you should be able to browse the net with ips instead of names

try opening firefox and instead of typing [www.google.co.uk](www.google.co.uk) try putting 74.125.230.112

---

### Post by breemiller on 2011-03-28
firefox doesn't open :(

---

### Post by conneco on 2011-03-28
Firefox doesnt launch or u get page cannot be displayed?

---

### Post by breemiller on 2011-03-28
firefox wont lauch... when I try launching it from desktop little applet thingy on bottom says 'starting firefox' and then it just stops....

also tried 'firefox' in terminal and got error message:
[http://i1219.photobucket.com/albums/dd436/breemiller1/firefox.png](http://i1219.photobucket.com/albums/dd436/breemiller1/firefox.png)

---

### Post by conneco on 2011-03-29
wow your not having much luck 


try unistalling and reinstalling firefox

```
sudo apt-get remove firefox
```

then

```
sudo apt-get install firefox
```

---

