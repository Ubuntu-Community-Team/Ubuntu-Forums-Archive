---
title: "Total Newb: Unable to connect with Broadcom wifi card"
date: 2012-08-10
forum: Networking &amp; Wireless
---

### Post by Dea ex Machina on 2012-08-10
Hey, folks! Bouncing baby Ubuntu 12.04 user here. I'm living in Japan, and English windows costs the moon here, so I decided to take the plunge and install Ubuntu on my new Acer Aspire One D270 laptop. Unfortunately, it seems Ubuntu and the wifi card have... personality conflicts. 

I can see the available connections, but when I select my home internet connection and enter my password, it tries to connect for a couple of minutes then asks for my password again. And KEEPS asking, every few minutes, even if I hit cancel. I have to disable wireless to get it to stop asking for my wireless password, but if I do that, sometimes it won't turn back on, or when it does, my home wifi is missing from the list of available connections. Wired connection works fine.

I've tried a few solutions from this forum and elsewhere, because this seems to be a common problem, but I'm worried I did it wrong, or used the wrong solution, because a couple of them made the problem worse (wifi wouldn't enable, connections won't appear). SO! I have done a clean install of Ubuntu 12.04 from the live USB again. We are starting from scratch, so that I know that the only issues are the one it came with, not one I created with noobish muddling.

My wifi card is a Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller. Additional Drivers are checked and installed. 

Small words, step by step instructions, and as much hand-holding as possible, please. Linux is new and scary.

---

### Post by chili555 on 2012-08-11
Welcome to the party! We have a lot of fun here.

If it's the card I think it is, there are two ways to get it going and only one is correct. Unfortunately, 'Additional Drivers' usually installs the wrong conflicting method! Let's verify what driver and card you have. Open a terminal and run and post:```
lspci -nn | grep 0280
lsmod | grep -e wl -e brcm -e b43
rfkill list all
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by Dea ex Machina on 2012-08-11
Thanks so much for the reply!


Okay, ran the terminal tests, copypasted below (username and computername changed to protect the guilty) :P



me@mycomputer:~$ lspci -nn | grep 280 
 00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2) 
 02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01) 
 me@mycomputer:~$ lsmod | grep -e wl -e bcrm -e b43 
 wl                   2646601  0  
 lib80211               14040  1 wl 
 me@mycomputer:~$ rfkill list all 
 0: acer-wireless: Wireless LAN 
 	Soft blocked: no 
 	Hard blocked: no 
 1: acer-bluetooth: Bluetooth 
 	Soft blocked: no 
 	Hard blocked: no 
 2: phy0: Wireless LAN 
 	Soft blocked: no 
 	Hard blocked: no

---

### Post by chili555 on 2012-08-11
>  Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [[COLOR="Red"]14e4:4727[/COLOR]] (rev 01) Ah, haaa! I believe the driver *wl* is incorrect and some anecdotal evidence is here:> when I select my home internet connection and enter my password, it tries to connect for a couple of minutes then asks for my password again. And KEEPS asking, every few minutes, even if I hit cancel. I have to disable wireless to get it to stop asking for my wireless password, but if I do that, sometimes it won't turn back on, or when it does, my home wifi is missing from the list of available connections.I believe the driver brcmsmac is correct. Let's temporarily unload wl and load brcmsmac and see if things improve. If so, we'll do some minor surgery and fix it for good.```
sudo modprobe -r wl
sudo modprobe brcmsmac
```Any change?

---

### Post by Dea ex Machina on 2012-08-11
Nope, no noticeable change (possibly it may be churning slightly longer before it asks for my password again, but it's hard to tell)

(Should there have been any kind of text message in terminal after entering the sudo modprobe commands? There wasn't, and I'm used to getting some kind of "yes I have done that" note from machines, but maybe linux is the strong silent type)

---

### Post by chili555 on 2012-08-11
> (Should there have been any kind of text message in terminal after entering the sudo modprobe commands? There wasn't, and I'm used to getting some kind of "yes I have done that" note from machines, but maybe linux is the strong silent type)Nope, Linux reports, generally on exceptions or errors only. Silence usually means, approximately: command executed as ordered, sir, and I have no warnings or errors to report. In many cases, you can ask for the details by asking for the command to be executed verbosely:```
sudo modprobe -r[COLOR="Red"]v[/COLOR] wl
```Let's see if there are any interesting messages here:```
dmesg | grep -e wlan -e brcm
```Some Linux drivers, I'm sad to say, are troubled by mixed mode WPA and WPA2 encryption and prefer WPA2 only. Which is yours?```
sudo iwlist wlan0 scan
```Of course, obscure any private details, MAC addresses, et al.

---

### Post by Dea ex Machina on 2012-08-11
Hoo boy, this is long... All mac addresses asterisked out and all ESSIDs altered:

                          ```
me@mycomputer:~$ dmesg | grep -e wlan -e brcm 
 [   14.812472] brcmsmac 0000:02:00.0: bus 2 slot 0 func 0 irq 10 
 [   14.812511] brcmsmac 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
 [   14.812530] brcmsmac 0000:02:00.0: setting latency timer to 64 
 [   16.141792] ieee80211 phy0: brcms_ops_config: change monitor mode: false (implement) 
 [   16.141804] ieee80211 phy0: brcms_ops_config: change power-save mode: false (implement) 
 [   16.142918] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement) 
 [   16.143439] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
 [   16.144637] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
 [   19.867291] wlan0: authenticate with **:**:**:**:**:**:** (try 1) 
 [   20.065067] wlan0: authenticate with **:**:**:**:**:**:** (try 2) 
 [   20.264892] wlan0: authenticate with **:**:**:**:**:**:** (try 3) 
 [   20.464727] wlan0: authentication with **:**:**:**:**:**:** timed out 
 [   26.306182] wlan0: authenticate with **:**:**:**:**:**:** ry 1) 
 [   26.503081] wlan0: authenticate with **:**:**:**:**:**:** (try 2) 
 [   26.702862] wlan0: authenticate with **:**:**:**:**:**:** (try 3) 
 [   26.902629] wlan0: authentication with **:**:**:**:**:**:** timed out 
 [   32.769265] wlan0: authenticate with **:**:**:**:**:**:** (try 1) 
 [   32.966702] wlan0: authenticate with **:**:**:**:**:**:** (try 2) 
 [   33.166425] wlan0: authenticate with **:**:**:**:**:**:** (try 3) 
 [   33.366186] wlan0: authentication with **:**:**:**:**:**:** timed out 
 [   39.239914] wlan0: authenticate with **:**:**:**:**:**:** (try 1) 
 [   39.437426] wlan0: authenticate with **:**:**:**:**:**:** (try 2) 
 [   39.637127] wlan0: authenticate with **:**:**:**:**:**:** (try 3) 
 [   39.836814] wlan0: authentication with **:**:**:**:**:**:** timed out 
 [   45.698627] wlan0: authenticate with **:**:**:**:**:**:** (try 1) 
 [   45.896072] wlan0: authenticate with **:**:**:**:**:**:** (try 2) 
 [   46.095812] wlan0: authenticate with **:**:**:**:**:**:** (try 3) 
 [   46.295501] wlan0: authentication with **:**:**:**:**:**:** timed out 
 [   52.145322] wlan0: authenticate with **:**:**:**:**:**:** (try 1) 
 [   52.342725] wlan0: authenticate with **:**:**:**:**:**:** (try 2) 
 [   52.542558] wlan0: authenticate with **:**:**:**:**:**:** (try 3) 
 [   52.742498] wlan0: authentication with **:**:**:**:**:**:** timed out 
 [   58.576037] wlan0: direct probe to **:**:**:**:**:**:** (try 1/3) 
 [   58.773509] wlan0: direct probe to **:**:**:**:**:**:** (try 2/3) 
 [   58.973213] wlan0: direct probe to **:**:**:**:**:**:** (try 3/3) 
 [   59.172996] wlan0: direct probe to **:**:**:**:**:**:** timed out 
 [   65.046745] wlan0: authenticate with **:**:**:**:**:**:** (try 1) 
 [   65.244213] wlan0: authenticate with **:**:**:**:**:**:** (try 2) 
 [   65.444087] wlan0: authenticate with **:**:**:**:**:**:** (try 3) 
 [   65.643615] wlan0: authentication with **:**:**:**:**:**:** timed out 
 [   71.521404] wlan0: authenticate with **:**:**:**:**:**:** (try 1) 
 [   71.718840] wlan0: authenticate with **:**:**:**:**:**:** (try 2) 
 [   71.918563] wlan0: authenticate with **:**:**:**:**:**:** (try 3) 
 [   72.118268] wlan0: authentication with **:**:**:**:**:**:** timed out 
 [   77.948728] wlan0: authenticate with **:**:**:**:**:**:** (try 1) 
 [   78.145552] wlan0: authenticate with **:**:**:**:**:**:** (try 2) 
 [   78.345309] wlan0: authenticate with **:**:**:**:**:**:** (try 3) 
 [   78.544958] wlan0: authentication with **:**:**:**:**:**:** timed out
```
I decided to abridge that, because it goes on identically for a few more pages: tries to authenticate three times, times out. Presumeably it's showing every single time it's pestered me for my password.


And the next one, also abridged, I cut out all my neighbours' wifi signals and just kept the info for the two signals my own wifi router gives off (it sends an extra one called "gameuser", intended to be used with game consoles and such, I gather). If you want the full and complete list, let me know.

                          ```
me@mycomputer:~$ sudo iwlist wlan0 scan 
 [sudo] password for me:  
 wlan0     Scan completed : 



*(snip)*



                     Cell 09 - Address: **:**:**:**:**:** 
                     Channel:12 
                     Frequency:2.467 GHz (Channel 12) 
                     Quality=48/70  Signal level=-62 dBm   
                     Encryption key:on 
                     ESSID:"mygameuserconnection" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                               9 Mb/s; 12 Mb/s; 18 Mb/s 
                     Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s 
                     Mode:Master 
                     Extra:tsf=000000e41031217f 
                     Extra: Last beacon: 92ms ago 
                     IE: Unknown: 000F6C6F676974656367616D6575736572 
                     IE: Unknown: 010882848B960C121824 
                     IE: Unknown: 03010C 
                     IE: Unknown: 2A0100 
                     IE: Unknown: 32043048606C 
                     IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00 
                     IE: Unknown: DD0600E04C020160 


*(snip)*

      
Cell 12 - Address: **:**:**:**:**:** 
                     Channel:12 
                     Frequency:2.467 GHz (Channel 12) 
                     Quality=53/70  Signal level=-57 dBm   
                     Encryption key:on 
                     ESSID:"myregularuserconnection" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                               9 Mb/s; 12 Mb/s; 18 Mb/s 
                     Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s 
                     Mode:Master 
                     Extra:tsf=000000e41032b17f 
                     Extra: Last beacon: 40ms ago 
                     IE: Unknown: 000B6C6F676974656375736572 
                     IE: Unknown: 010882848B960C121824 
                     IE: Unknown: 03010C 
                     IE: Unknown: 2A0100 
                     IE: Unknown: 32043048606C 
                     IE: Unknown: 2D1A2C181EFFFF000000000000000000000000000000000000000000 
                     IE: Unknown: 3D160C000000000000000000000000000000000000000000 
                     IE: WPA Version 1 
                         Group Cipher : TKIP 
                         Pairwise Ciphers (1) : TKIP 
                         Authentication Suites (1) : PSK 
                     IE: IEEE 802.11i/WPA2 Version 1 
                         Group Cipher : TKIP 
                         Pairwise Ciphers (1) : CCMP 
                         Authentication Suites (1) : PSK 
                     IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00 
                     IE: Unknown: DD9E0050F204104A0001101044000102103B000103104700106304125310192006122800018EEA63421021001B5265616C74656B2053656D69636F6E647563746F7220436F72702E1023000752544C387878781024000D45562D323030392D30322D30361042000F3132333435363738393031323334371054000800060050F2040001101100135265616C74656B20576972656C657373204150100800020086 
                     IE: Unknown: DD1E00904C332C181EFFFF000000000000000000000000000000000000000000 
                     IE: Unknown: DD1A00904C340C000000000000000000000000000000000000000000 
                     IE: Unknown: DD0600E04C020160 

```The snips are where the other, not mine, wifi signals went. Let me know if you need to see them.

---

### Post by chili555 on 2012-08-12
> Copy/pasting into/out of libroffice added some weird extraneous text Sorry about that. For any future posts, you might try the text editor gedit which you can install if it's not already there:```
sudo apt-get install gedit
```You can shoot your dmesg into a text document:```
dmesg | grep -e wlan -e brcm > newb.txt
```Then open it with gedit:```
gedit newb.txt
```Then use the find and replace tool to overwrite all the MAC addresses, etc. at once. 

It's certainly your choice, but I'd think a MAC address like this is sufficiently obscure if it saves you effort: xx:13:10:62:8D:xx.

Then save the gedit changes and, again, if it saves effort, post it as an attachment using the paperclip tool at the top of the reply box.

As I said previously, some Linux drivers are troubled by mixed mode WPA and WPA2 encryption and prefer WPA2 only. Your primary network is mixed mode:> Cell 12 - Address: **:**:**:**:**:** 
                     Channel:12 
                     Frequency:2.467 GHz (Channel 12) 
                     Quality=53/70  Signal level=-57 dBm   
                     Encryption key:on 
                     ESSID:"myregularuserconnection" 
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                               9 Mb/s; 12 Mb/s; 18 Mb/s 
                     Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s 
                     Mode:Master 
                     <snip>
                     IE: [COLOR="Red"]WPA Version 1 [/COLOR]
                         Group Cipher : TKIP 
                         Pairwise Ciphers (1) : TKIP 
                         Authentication Suites (1) : PSK 
                     IE: IEEE 802.11i/[COLOR="Red"]WPA2 Version 1[/COLOR] Can you please try WPA2 only?

---

### Post by Dea ex Machina on 2012-08-12
Oof. That was harder than it should have been. Darn Japanese routers with their Japanese manuals and Japanese control panel pages... All right, after messing with settings and powercycling the router, it LOOKS like my connection is now WPA2 encrypted only...

```
          Cell 14 - Address: xx:01:8E:EA:63:xx
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"myregularuserconnection"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000015bf317f
                    Extra: Last beacon: 64ms ago
                    IE: Unknown: 000B6C6F676974656375736572
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010D
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A2C181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160D000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C332C181EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340D000000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
                    IE: Unknown: DD0E0050F204104A0001101044000102
```

I think I did it... Did I do it? My Japanese is shaky, and I've never even changed the encryption settings in *English* before. :lol:

Unfortunately, the change doesn't seem to have had a noticeable effect on the problem; the netbook is still unable to connect, and still asking for my password over and over.

---

### Post by chili555 on 2012-08-12
> I think I did it... Did I do it?Yes, indeed! > My Japanese is shakyI'm shaky in *every* language I've ever been taught, including python!>  the netbook is still unable to connect, and still asking for my password over and over. And you can confirm that brcmsmac *IS* loaded and wl is not?```
lsmod | grep -e wl -e brcm
```I'm starting to have nightmares about 14e4:4727.

---

### Post by Dea ex Machina on 2012-08-12
```
me@mycomputer:~$ lsmod | grep -e wl -e brcm
wl                   2646601  0 
lib80211               14040  1 wl
brcmsmac              540875  0 
mac80211              436455  1 brcmsmac
brcmutil               14675  1 brcmsmac
cfg80211              178679  2 brcmsmac,mac80211
crc8                   12781  1 brcmsmac
cordic                 12487  1 brcmsmac
```

What's it say?

---

### Post by chili555 on 2012-08-12
It says there are two drivers both yanking on the wheel fighting each other. In order to make any meaningful judgment, we have to kick out wl and let brcmsmac do the job. If it doesn't work correctly, we'll kick out brcmsmac and reinstate wl. One of them surely must work right!! Please do:```
sudo su
echo "blacklist wl" >> /etc/modprobe.d/blacklist.conf
exit
```Please reboot and try to connect.

You get that nifty Nissan Skyline GT-R there in Japan. I wouldn't want four hands on the steering wheel of mine!!!

---

### Post by Dea ex Machina on 2012-08-12
Rebooted, and still no change. I hope that just means we threw the designated driver out of the car and kept the drunk one by mistake...

---

### Post by chili555 on 2012-08-12
Let's pick up the hopefully good driver and kick out the drunk:```
sudo gedit /etc/modprobe.d/blacklist.conf
```When the text editor opens, go to the last line that you added (with 'echo') and change from:```
blacklist wl
```To:```
blacklist brcmsmac
blacklist bcma
```Proofread, save and close gedit. Reboot and give us a good report, please.

---

### Post by Dea ex Machina on 2012-08-12
Dang. Well, that did SOMETHING, but what it did was on the first reboot stop displaying available wifi connections or half the network options (the dropdown pretty much showed 'Enable Networking' and 'Enable Wireless,' both checked in the affirmative, but nothing else), and when I rebooted again, started showing about half of them, NOT including mine. 

So that's a step backwards, but is it a *useful* step backwards? Does it tell you anything we can use?

---

### Post by chili555 on 2012-08-12
Let's see if the kernel messages suggest anything.```
dmesg | grep -e wl -e eth1
```If confidential details are disclosed, you'll know from above how to find and replace.

---

### Post by Dea ex Machina on 2012-08-12
```
me@mycomputer:~$ dmesg | grep -e wl -e ethl
[   14.807817] wl: module license 'MIXED/Proprietary' taints kernel.
[   14.900989] wl 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.901009] wl 0000:02:00.0: setting latency timer to 64
```

???

---

### Post by chili555 on 2012-08-12
When you run:```
iwconfig
```Is there a wireless interface? It's usually eth1 with wl. If it's eth2 or eth197 or some such, see what dmesg says:```
dmesg | grep eth?? [COLOR="Red"]<--whatever you found[/COLOR]
```Thanks.

---

### Post by OM55 on 2012-08-12
Hello Dea ex Machina,

I'd like to drop in and offer a few additional suggestions for things you can try to solve the problem, or at least find the reason for the problem.

I have 5 Acer One laptops, all Ubuntu 12.04 (Classic Gnome - no effects) in several sites.
I experienced several times the exact same problem you described. I noticed it happend also with Ubuntu 10.10 and only with the Acer One laptops not with regular size laptops, so I don't think it is specific to Ubuntu 12.04 but more related to the specific compacted wireless hardware of the Acer One.

In my search for solutions I also tried to force the router to WPA2 only but that was not the problem (although helped in another situation), just like you found it is not the problem in your case.

But I was able eventually to solve the problem. Here is what I found:

1. It happens only with encrypted connections. Meaning - if no password is required to access the Wi-Fi, there is no problem and the Acer One re-connects right away.

2. When there are many other neighbouring WiFi routers around, the Acer One has greater difficulty in connecting to its own router with encrypted connection.

3. In some situations a neighbouring router with similar SSID name, and your laptop may be trying to connect to this other router with your password - which of course will not work and will result in the problem you experience.

4. The wireless reception on the Acer One is definitely not as good as with a full size laptop. When the reception is weak or spotty, the Acer One tends to disconnect from the router and than has a problem reconnecting, asking again and again for the password.

The solutions are (respectively):

1. This is normally a moot point, since most of us need/want to have a password and encrypted Wi-Fi connection. However you should CHECK THAT OUT. Since if you are not able to connect even without a password, the problem could be completely different and you are searching in the wrong place.

2. Unfortuantelly there is nothing much you can do about neighbouring routers (short of shielding your condo with a metal cage...). The only thing you can do is:


[LIST]
[*]Select for your router a manual frequency band that no other neighbouring router is using (or is less used than others). To find that out you can use programs like WireShark, WiFi Radar etc.
[*]Increase the output power of your own router and narrow the bandwidth. Most routers will allow you to replace the antennas with an external antenna that will increase the transmission/reception power considerably. An antenna will have optimal reception/transmission when it is in a specific length (related to the frequency it is working at). All router antennas are considerably shorter than the optimal length, but sufficient for most homes.
[*]Get a USB wireless adaptor with an external antenna (check out Hawking Technology) that will allow you better reception on the laptop's side.
[/LIST]

3. You can direct your Acer One to connect ONLY to your own router:

[LIST=1]
[*]Open 'Network Connections' (or just click on the network icon)
[*]Switch to the 'Wireless' tab
[*]Select your wireless network (you should delete any others that you don't use)
[*]Click the 'Edit' button
[*]Type/paste in the BSSID the MAC address of your router and click 'Save'.
[/LIST]
After restart (or logoff/login) this wireless network connection will connect ONLY to this specific router.

4. To test this assumption, just move the Acer One laptop to be near your router. If the connection issue is resolved, than your problem is indeed a reception issue. If the connection issue continues - that we have to keep looking.

My two cents - I think that somehow in the Acer One's compact design, the Wi-Fi antenna is by far not as efficient as in the larger laptops, and as a result it is very sensitive to all kind of interferences, Wi-Fi reception issues and such. Since Wi-Fi frequency is VERY crowded already (from cordless phones, baby monitors, microwaves, concrete walls and of course - the many other wi-fi routers in the vicinity) interference is constant and the Acer One has a much harder time trying to overcome that. Since encrypted Wi-Fi is adding another layer of information on top of the already spotty reception - it is the first to suffer the consequences, hence the password connection issue.

In my case, I solved all those connection issues using the description above and I have no similar problems.

Hope that helps you as well!

---

### Post by Dea ex Machina on 2012-08-12
> When you run: 	Code:
 	iwconfig 
Is there a wireless interface?

```
me@mycomputer:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:233
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.
```

Looks like it is eth1, but ran dmesg anyway, just in case...

```
me@mycomputer:~$ dmesg | grep eth1
[   15.105007] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.100.82.38

```

Should I stay on wl, or switch back to brcmsmac and bcma? Since my home connection isn't showing up any more, I don't know if I can even test OM55's suggestions. 

Though for the record, when I briefly started up Japanese windows to check on everything, the wifi DID connect, though it was a bit sluggish. And my old netbook that died of heatstroke was ALSO an Acer Aspire One, albeit a western one running English Windows and an earlier model, and it never had any troubles. Well, other troubles, since it* did* die, but not troubles with the wifi! :P

---

### Post by chili555 on 2012-08-13
> Should I stay on wl, or switch back to brcmsmac and bcma? Since my home connection isn't showing up any more, I don't know if I can even test OM55's suggestions. I think we do need to kiss wl goodbye:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get autoremove
sudo gedit /etc/modprobe.d/blacklist.conf
```Remove the lines:```
blacklist brcmsmac
blacklist bcma
```Proofread, save and close gedit. Reboot, allowing what I think is the correct driver brcmsmac to take over. Let us hear your report.

---

### Post by Dea ex Machina on 2012-08-13
Okay, removed brcmsmac and bcma from the doghouse (and put wl back on the blacklist, though you didn't mention it, hope that's okay?) After rebooting, my home connections are now back on the list of available connections. 

I took a shot at two of OM55's ideas, turned encryption off completely on my wifi and parked the netbook right on top of the router. It didn't ask for a password any more, as there was none to ask for, but it still churned and attempted and ultimately failed to connect repeatedly, same as before. So it doesn't look like a problem with encryption or reception. Even when there's nothing to ask for and the router's right there, it just can't connect.

---

### Post by OM55 on 2012-08-13
Hmmm... so that means the problem has nothing to do with WPA/WPA2, reception quality or interference. Did you try to check the logs?

The system log viewer is at: Applications -> System Tools -> Log File Viewer

or in terminal: 
```
gnome-system-log
```To make it easy to find in the logs where you should start looking, leave your laptop idle for a few of minutes (wireless off), and then try to connect to the wireless router. _Right after_ the unsuccessful attempt to connect to the wireless router, launch the Log File Viewer, select 'syslog' and scroll to the very bottom. Start looking at the events with the time stamp of the moment you tried to connect to the wireless connection.

The events you are interested in will start at the last time-stamp jump and have "NetworkManager" at the beginning of the line. So alternatively, a more comfortable option to do the same thing is:
```
cat /var/log/syslog | grep NetworkManager > WirelessLog.txt
```then
```
gedit WirelessLog.txt
```Normally you would see reports on the network SSID it is connecting to, two DNS servers being assigned, IP address being assigned by the DHCP etc.
In your case some of it is not happening and you may be able to see what it is trying to do and cannot, resulting in no-wireless connection.

So this may give us some hints as for what is NOT happening that should, and why.
If you post the WirelessLog.txt file here (only the bottom lines, starting at the last time-stamp jump), we should be able to help you find a clue and identify the problem.

At this point it doesn't matter if the connection is secure with WPA2 or not. But if it is not-secure there will be less things to check, so would be easier to find and focus on the problematic log entries.

---

### Post by Dea ex Machina on 2012-08-14
Okay, weirdness again with connections disappearing from the network menu. When I started up the computer just now, they were gone again, and I was down to a dropdown that said "enable networking"; "enable wireless" (both checked yes); "connection information" (grayed out), and "edit connections". I rebooted, but they did not reappear. However, the available wifi connections and other options DID reappear when I plugged the lan line in. 

The heck?

So, two txt log files, here, one starting from the time I turned the computer on this afternoon, and one starting, I think, from me plugging in the line (I removed the line after the wifi connections re-emerged; they stayed put.)

Oh, I went in and edited the home connection so that "connect automatically" is no longer checked; it no longer re-tries a minute after I hit cancel, or stacks up a dozen password request windows if I ignore it. So that's something, at least!

---

### Post by OM55 on 2012-08-14
Ok, based on the log files you provided, now I think we are on to something.

But first, regarding all the wireless networks disappearing after reboot - I can confirm that this happens on every single of my 5 Acer One laptops with Ubuntu 12.04 once in a while. So this is a specific issue for Acer One with Ubuntu 12.04 (did not happen with 10.10). In my case it takes 1-2 reboots to bring them back, but that is because they are automatically managed by our software. In your case try:
```
sudo restart network-manager

```or
```
sudo restart networking

```It might help bringing back the wireless networks.


Back to the log files you provided. It appears that Network Manager is trying to establish connection, but the wireless driver takes too long (more than the default 25 seconds allowed) and the result is the message:

**Activation (wlan0/wireless): association took too long.**

This is a known bug for Network Manager that happens with some specific drivers on specific hardware and it has been reported before several times. I think there is a patch available for Network Manager but not yet updated in the repositories (you can try and get a newer .deb file to update Network Manager if such file is out there).

But until then, there are a couple of solutions to that bug:

1. You can patch the Network Manager source code to increase the timeout from 25 seconds to 60 seconds (or any other larger value). BUT, Given the title of this thread (NewB) I think this may be not your preferred solution... :)
Anyway, if you want to try here are a few links (although on a different Linux distro, but same solution nonetheless):
[https://bbs.archlinux.org/viewtopic.php?id=139274](https://bbs.archlinux.org/viewtopic.php?id=139274)
[https://bbs.archlinux.org/viewtopic.php?id=139416](https://bbs.archlinux.org/viewtopic.php?id=139416)

2. You can replace Network Manager and use **Wicd** instead ([https://launchpad.net/wicd](https://launchpad.net/wicd)), it is in the Software Center and the Ubuntu repositories. Wicd is a nicer graphical interface for wired/wireless network management that pretty much replaces all the functionality of Network Manager.
The only small risk in doing this exchange - you have to be careful and do things step by step, or might be left without any network connection... Given that in Ubuntu everything is done via the Internet connection, it wont be fun when that happens... (you will need to download the .deb file of Network Manager using a different laptop, transfer to this one and install).

To install Wicd and properly disable Network Manager, follow the instructions in the following link (coincidentally, it was done to solve the exact same problem you have): 
[http://www.techrepublic.com/blog/australia/fixing-fedoras-wi-fi-with-wicd/463](http://www.techrepublic.com/blog/australia/fixing-fedoras-wi-fi-with-wicd/463)

You install Wicd directly from Software Center, or try the latest version from the develper's website

IMPORTANT: It is critical that you will disable Network Manager only after Wicd is working, or will be left without a networking connection.

Hope that the above will finally resolve your wireless hassle!
Let us know if Wicd worked for you.

---

### Post by Dea ex Machina on 2012-08-14
Oh sweet Spock be praised, PROGRESS, albeit weird progress.

Installed wicd, did the commands, tried to connect through wicd's own graphical interface, failed due to it saying that my password was wrong (LIES). Then I tried to connect via the networking dropdown in the top bar again... SUCCESS! I am now wirelessly connected, even though wicd STILL tells me that my password is wrong if I try to go through it directly. Still working after one reboot. 

I guess wicd can just sit there on my sidebar looking pretty and doing.... whatever the hell it's doing?

---

### Post by OM55 on 2012-08-14
Yes, Wicd can stay there doing nothing. If you did not remove or permanently disable Network Manager, it will still be responsible for your wireless connections while Wicd will just show the status.

However, I definitely hear you loud and clear - after all that hassle, once it is working you have no desire to try and find out why but prefers to leave it as is, working...

Well, if the wireless connection misbehaves again, we can always pick up where we left!

Glad I was able to help, and Ejoy Wifi-ing!
(then please mark this thread as SOLVED for others to see...).

---

### Post by YBthebest on 2013-06-06
Hi guys!

I'm having the exact same problem (albeit being on a HP Mini 5103).
But I'm on 12.04, and I can't connect to the wifi no matter what, & the password windows keep poping up too.
In the beginning my network didn't show up AT ALL, but at least now it does.

Problem is: I have my phone, where I'm on right now, and my computer, and my computer has no interner whatsoever so I didn't manage to install wicd for example...

Thanks a lot!

---

### Post by chili555 on 2013-06-07
> **YBthebest said:**
> Hi guys!

I'm having the exact same problem (albeit being on a HP Mini 5103).
But I'm on 12.04, and I can't connect to the wifi no matter what, & the password windows keep poping up too.
In the beginning my network didn't show up AT ALL, but at least now it does.

Problem is: I have my phone, where I'm on right now, and my computer, and my computer has no interner whatsoever so I didn't manage to install wicd for example...

Thanks a lot!Do you have the same device?```
lspci -nn -d 14e4:
```Thanks.

---

