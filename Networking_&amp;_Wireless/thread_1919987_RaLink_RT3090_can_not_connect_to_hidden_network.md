---
title: "RaLink RT3090 can not connect to hidden network"
date: 2012-02-03
forum: Networking &amp; Wireless
---

### Post by nowifi on 2012-02-03
Does anyone know a fix for Ubuntu so a wireless RaLink RT3090 will connect  to a "hidden" router? This has not been a problem with other wireless  hardware. The RT3090 will connect successfully to routers with hidden SSID's when using the embedded OEM's Linux derivative, SpalshTop, from DeviceVM.

Ubuntu can not connect routers that do not broadcast  SSID's with a
```

[COLOR=Navy]**lspci**[/COLOR]
...
   Network controller: RaLink RT3090 Wireless
...
```that requires:

```

[COLOR=Navy][B]sudo su
mkdir -p /etc/Wireless/RT2860STA/
touch /etc/Wireless/RT2860STA/RT2860STA.dat
service network-manager restart
exit[/B][/COLOR]
```in order to function.  ( ref:[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620/comments/21](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620/comments/21) )

Trying to connect with NetworkManager Applet 0.8 to [COLOR=Red]**whiffle**[/COLOR] fails:
 ```

[COLOR=Navy]**iwconfig**[/COLOR]
lo        no wireless extensions.

eth0    no wireless extensions.

wlan0  RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: [COLOR=Red]**Not-Associated**[/COLOR]   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=70/100  Signal level:0 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0   no wireless extensions.

```even though the router ([COLOR=Red]**00:00:**[/COLOR][COLOR=Red]**5A:**[/COLOR][COLOR=Red]**3D:33:8D**[/COLOR])  is seen with SSID [COLOR=Red]**whiffle**[/COLOR] "hidden" ...

```
[COLOR=Red]
**[COLOR=Navy]iwlist wlan0 scan[/COLOR]**[/COLOR]
wlan0     Scan completed :
...
          Cell 02 - Address: [COLOR=Red]**00:00:**[/COLOR][COLOR=Red]**5A:**[/COLOR][COLOR=Red]**3D:33:8D**[/COLOR]
                    Protocol:802.11b/g
                    ESSID:""
                    Mode:Managed
                    Channel:1
                    Quality:100/100  Signal level:-37 dBm  Noise  level:-115 dBm
                    Encryption key:off
                    Bit Rates:36 Mb/s
...

```The router is configured as follows (w/o no security for simpler testing):

```

LAN
            MAC    Address        **[COLOR=Red]00:00:5A:3D:33:8D[/COLOR]**
            IP    Address         192.168.0.1
            Subnet    Mask        255.255.255.0
            DHCP    Server        Enabled

Wireless  802.11g
             SSID           whiffle
             Channel        1
             Encryption     Disabled
         SSID Broadcast     Disabled

```

---

### Post by nowifi on 2012-02-04
This appears to be a systemic problem as no solutions exist for the following references:

[http://ubuntuforums.org/showthread.php?t=1817624](http://ubuntuforums.org/showthread.php?t=1817624)
[http://ubuntuforums.org/showthread.php?p=11664194](http://ubuntuforums.org/showthread.php?p=11664194)
[http://ubuntuforums.org/showthread.php?t=1659866](http://ubuntuforums.org/showthread.php?t=1659866)
[http://ubuntuforums.org/showpost.php?p=9434771&postcount=8](http://ubuntuforums.org/showpost.php?p=9434771&postcount=8)
[http://ubuntuforums.org/showthread.php?t=1839215](http://ubuntuforums.org/showthread.php?t=1839215)
[http://ubuntuforums.org/showthread.php?t=1045345](http://ubuntuforums.org/showthread.php?t=1045345)

---

### Post by philinux on 2012-02-06
[http://www.howtogeek.com/howto/28653/debunking-myths-is-hiding-your-wireless-ssid-really-more-secure/](http://www.howtogeek.com/howto/28653/debunking-myths-is-hiding-your-wireless-ssid-really-more-secure/)

Does anyone disagree with this?

---

### Post by nowifi on 2012-02-06
There are many systems which DO NOT broadcast SSID's and NOT for reasons  of security - as such it IS necessary to connect to "hidden" networks.

(```
**[COLOR=Navy]iwlist scan[/COLOR]**
``` within a high saturation WiFi zone often shows ESSID's that are "", meaning the SSID's are not broadcast and indicating that it is a ubiquitous practice and ... obviously not totally invisible because they ARE listed. If one really wants to "justify" a non-security rationale for exercising this option none is simpler than avoiding added clutter to the list of WiFi's that DO broadcast their SSID's using "normal" connectivity tools like Network Manager.)

The fact that ALL wireless routers have intrinsic options to disable broadcasting the  SSID (it is an industry wide defined specification), indicates that it is quite a viable exercise to disable the SSID broadcast,  otherwise no such capability to do this would exist in a router's  configuration ...

... and  which is why THERE IS a "Connect to Hidden Wireless Network  ..." menu option in NetworkManager.

If broadcasting SSID's were NOT meant to be turned off then wireless routers and Network Manager in particular would NOT have such functionality.

It is completely  reasonable to expect this to work and it does so for many other OS & hardware configurations. 

It is quite evident that the interfacing for the RT3090 hardware is faulty and broken in Ubuntu which is indicative of poor programming and implementation. If this is not programmed correctly it casts doubt on the integrity and reliability for the code where it does seem to "work" - such as only for those environments where an SSID is broadcast.

Reiterating: Has anyone had success connecting Ubuntu with a wireless RaLink RT3090 to a router that does not broadcast it's SSID?

---

### Post by vhradice on 2012-02-06
Is it a protected hidden network that you cannot connect to?  I have a problem connecting to my hidden protected network.  If I remove the protection, then I can connect.  What is it about Ubuntu and protected networks?  If I broadcast the SSID and have protection on, I cannot connect.  Again, if I turn protection off, I get in.  I have found some posts where people are getting onto protected hidden networks with no problem.

It looks to me like there is 'Something wrong here in River City' to quote an old movie.

---

### Post by nowifi on 2012-02-06
The scenario presented has no encryption protocols activated in order to expedite and simplify testing.

Suffice to say that a variety of OS's other than Ubuntu (SplashTop and other Linux derivatives, Windoze) and wireless hardware (Orinoco PCMCIA, BroadCom etc.) DO fully and reliably implement ALL possible network configurations, with and without SSID broadcasting.

The RaLink RT3090 in other OS environments (especially the embedded SplashTOP Linux derivative supplied with the OEM netbook in which the RT3090 is installed) DOES fully implement all wireless configurations including non-broadcast SSID.

Ubuntu has severe limitations with wireless networking hardware.

The lack of any concrete evidence to resolve this issue has established the precedent that this is now, in fact another bug.

(The statement >  What is it about Ubuntu and protected networks?which I would paraphrase as >  What is it about Ubuntu and wireless networks?reinforces a previous archaic observation:  that Ubuntu 8.04 Hardy Heron could not interface with the wireless hardware in an HP NX6110 - and shows that this is generally a chronic problem with Ubuntu - simply by observing the volume of anecdotal wireless issues that people are having. This is totally anathema to the essence of computer automation which is to REDUCE human manually labour intensive operations - NOT increase them. Corollary - after spending an hour or 2 on trying to solve this issue at a billing rate of $150/hr it is cheaper to go and buy  a machine that works for $300 rather than waste any more breath on this issue.)

Network-Manager can be coerced to make an RT3090 wireless connection to a router that does not broadcast its SSID (**[COLOR=Blue]whiffle[/COLOR]**) by typing the following in a terminal window while the attempt to connect is in progress:

```
[COLOR=Blue]**sudo iwconfig wlan0 essid whiffle**[/COLOR]
```While this "works", it is not consistent with the conventional intended use of Network Manager to establish a wireless connection to a router, irregardless of its SSID broadcast state.

If a password such as "**[COLOR=Blue]whiffill[/COLOR]**" is required, the command also needs to include it as well with the [COLOR=Blue]**key**[/COLOR] or **[COLOR=Blue]enc[/COLOR]** attribute ([COLOR=Blue]**s:**[/COLOR] is used to specify a string or ASCII letter sequence as opposed to a numeric pass code):

```
[COLOR=Blue]**sudo iwconfig wlan0 essid whiffle key s:**[/COLOR]**[COLOR=Blue]whiffill[/COLOR]**
```(an aside: the inclusion of such passwords does not need to be qualified by the appropriate protocol WEP, WAP TKIP AES ... There are several postings which would benefit by using this incantation for specifying passwords to coerce a Network Manager connection. PS. it helps to toggle NM's **Enable Wireless** first. ref: *[Re: Ralink rt2860 running ubuntu netbook remix 10.04]("http://ubuntuforums.org/showthread.php?p=11686477#post11686477")* )

It is disappointing that in the 21st century the caliber of software and  hardware engineering succumbs to such idiosyncratic failures.

---

### Post by nowifi on 2012-02-10
A quick site survey
(for brevity wireless services with SSID's are not included and as well  the entires are pruned to remove text information like ```

                    Mode:Managed
                    Encryption key:on
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

                    Quality:73/100  Signal level:-61 dBm  Noise  level:-83 dBm

``` )

by ```
[COLOR=Blue]**sudo iwlist scan**[/COLOR]
``` of wireless services in a  commercial/corporate environ produced 7 services that do not broadcast their SSID in a total list of 14 (a significant ratio of 50%):

```

...
          Cell 03 - Address: 78:CD:8E:CA:09:72
                    Protocol:802.11b/g/n
                    **[COLOR=Red]ESSID:""[/COLOR]**
                    Channel:1
                    Bit Rates:300 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
          Cell 04 - Address: 00:15:70:00:88:90
                    Protocol:802.11b/g
                    **[COLOR=Red]ESSID:""[/COLOR]**
                    Channel:1
                    Bit Rates:18 Mb/s
                    IE: WPA Version 1
                    IE: IEEE 802.11i/WPA2 Version 1
          Cell 05 - Address: 00:15:70:92:1E:D8
                    Protocol:802.11b/g
                    **[COLOR=Red]ESSID:""[/COLOR]**
                    Channel:1
                    Bit Rates:18 Mb/s
                    IE: WPA Version 1
...
          Cell 07 - Address: 00:15:70:00:88:91
                    Protocol:802.11b/g
                    **[COLOR=Red]ESSID:""[/COLOR]**
                    Channel:1
                    Bit Rates:18 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
          Cell 08 - Address: 00:15:70:92:1E:D9
                    Protocol:802.11b/g
                    **[COLOR=Red]ESSID:""[/COLOR]**
                    Channel:1
                    Bit Rates:18 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
          Cell 09 - Address: 00:15:70:92:1E:DA
                    Protocol:802.11b/g
                    **[COLOR=Red]ESSID:""[/COLOR]**
                    Channel:1
                    Bit Rates:18 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
...
          Cell 13 - Address: 00:11:88:A0:63:60
                    Protocol:802.11b
                    **[COLOR=Red]ESSID:""[/COLOR]**
                    Channel:11
                    Bit Rates:11 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
...

```**Observations**:

While a null SSID of "" is possible, it is highly unlikely since it is  very difficult to set an SSID to an empty string using a router's  configuration interface and is generally disallowed (however it can be  done by custom flashing of the firmware). Consequently a null ESSID of  "" usually manifests because the SSID is not broadcast.

The fact that 50% of the ESSID's are "" indicates that the practice of not broadcasting an SSID is popular, very common AND conventional irregardless of any "security" concerns.

Obviously the actual wireless services themselves are not hidden since they are listed   here even though their SSID's are not broadcast.

Network addresses 
00:15:70:92:1E: DA
00:15:70:92:1E: D9
00:15:70:92:1E: D8
00:15:70:00:88:90
00:15:70:00:88:91 
are highly correlated.
(By industry convention the address enumeration allocation assignment is  matched to manufacturer, models, etc.)

---

