---
title: "Wireless wont accept password on Ubuntu Netbook Remix"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by Mindrage on 2009-04-26
Hello, I got some problems with my Wireless connection on my Ubuntu Netbook Remix 9.04

I can get to the scanned networks, but it wont allow the password I've written in.
It just edits the password to a bunch of letters and numbers (think its remade to Hexadecimal) after clicking "Okey".

I've tried to manually write in a new connection but it wont work.
I have a Kubuntu 9.04 to compare with with on the same network.

Is there any solution for this problem?
I used WPA & WPA2 Personal.

@offtopic
I've heard bad critics with Ubuntu Netbook Remix, But what is the actuall problem with it?

---

### Post by duffydack on 2009-04-30
I had same problems, i fixed mine by upgrading my router giving it WPA2 functions, not just WPA.. Seems thats what network manager wanted... take a look here
[http://ubuntuforums.org/showthread.php?t=1137981](http://ubuntuforums.org/showthread.php?t=1137981)

---

### Post by strophy on 2009-04-30
I just resolved this exact same problem under Ubuntu 9.04 Netbook trying to connect to a German T-Com Speedport W 502V router. Ubuntu could not authenticate when the router was configured to use WPA & WPA2 pre-shared keys, however both of the MacOS computers I have here did so easily. When wireless security was off it was no problem at all. The solution was to set the router to WPA2 pre-shared key only. Seeing as more and more routers are configured to use WPA and WPA2 simultaneously, fixing this sounds like a good idea... Does anybody have similar experiences?

Leon

---

### Post by conorturton on 2009-04-30
The problem comes down to the fact that network manager expects anything using WPA2 to use AES as the encryption. 

Many routers that offer a combined WPA+WPA2 option use TKIP as the encryption protocol which gives backwards compatibility. 

Windows has no issue working with TKIP on WPA2 but Ubuntu network manager does. So as it doesn't recognise the handshaking, it assumes the password you've entered is incorrect and asks for it again.

---

### Post by strophy on 2009-04-30
Sooo.... isn't this a bug-worthy problem? If 'many' routers use this, often as their default option, and Ubuntu can't connect to any of them without reconfiguring the router (often impossible in cafes or something) then there is literally no solution? Not ideal, particularly on a netbook which connects by wireless when on the road so much.

What is the problem exactly with Network Manager, TKIP and WPA2?

---

### Post by laytek on 2009-10-02
Thanks conorturton for the solution and explanation. I had my Linksys wrt54gl router with tomato software set to TKIP/AES. Switching to AES only allowed my MSI Wind U100 (with 9.04 UNR) to connect.

Some of the assumptions and decisions from the developers make life in the Ubuntu world difficult. Listen to your users and fix these problems.

LayTek

---

### Post by rainbowmagik on 2009-10-03
Hello,
I am having similar trouble with my linksys WAG160N, I am unable to connect using wpa-2 because there is no option in the router to force AES and also there is no telnet access, I hope that in the near future an option is added to the connection dialogue, to choose either AES or TKIP when connecting to a wpa-2 network.

Is there any method at all to force one or the other in ubuntu 9.04?

or maybe an alternative client that can handle both aes/tkip where non is specified?

thanks.

---

### Post by MADinMelbourne on 2009-10-14
I'm having similar problem... not with the laptop... with my mobile, it can't connect to wireless internet because my mobile password won't stick on WPA WPA2 set up.  Just keeps coming back to an alphabet of letters mixed with numbers.  Is there a solution, if so, what is it?

I've got Linksys WAG54G2, HTC dream mobile.

---

### Post by alabasterjones on 2010-01-22
So, has anybody solved this problem without having to change their router settings?

---

### Post by monarchheels on 2010-02-04
Hey, thanks for all the good comments on this...I'm about to take a new MSI U210 with UNR (karmic) on international travels. I'm currently having some wireless issues and am following several threads trying to solve it. This thread is also going on my list of resources...

---

### Post by monarchheels on 2010-02-04
:P
I'm on!
Here's what I did to get the MSI-U210 with a RalinkRT3090 to connect to a            NETGEAR WPN824 IEEE 802.11b/g RangeMax Wireless Router.

1. Followed omniuni's excellent instructions here [http://ubuntuforums.org/showpost.php?p=8521493&postcount=57](http://ubuntuforums.org/showpost.php?p=8521493&postcount=57)
 
2. rebooted, then followed omniuni's further instructions here [http://ubuntuforums.org/showpost.php?p=8774617&postcount=67](http://ubuntuforums.org/showpost.php?p=8774617&postcount=67)

3. logged into my router ([www.routerlogin.com](www.routerlogin.com)), looked at its settings, and saw that it was using WPA-PSK [TKIP]
Based on people's comments above, I changed it to WPA-PSK [TKIP] + WPA2-PSK [AES]. I also gave it a new password just so I was sure I was using the right one. Clicked "Apply" & waited for changes to take effect

4. MSI U210 with UNR now recognizes my router, along with all my neighbors!! Next up...getting it to work in the office where we'd probably use the MAC address...I'm also wondering if my old Powerbook G4 with OS 10.4 will still connect now. But, that's not an issue for these forums. ;)

Thanks everybody! I suddenly feel smarter.

---

### Post by omniuni on 2010-02-04
To get your mac address:
```
ifconfig ra0 | grep HW
``` (**HWaddr** is the mac address)

---

### Post by monarchheels on 2010-02-04
Worked with MAC address method, too!

Yay!

---

### Post by monarchheels on 2010-03-14
Update:
I'm now on the road with this MSI w/ URN and can't keep a connection. Yesterday it worked with a yesss ([http://www.yesss.at](http://www.yesss.at)) set up (SIM card & Huawei E220) but now after turning the computer off last night and starting it this morning, it sees the network yet won't accept the WEP key. I don't have access to the router settings since it's not my router.
I've tried killing and restarting Network Manager, disabling and re-enabling the wireless, restarting...but no luck.
Writing this message from an old PowerBook G4 without problems.

---

