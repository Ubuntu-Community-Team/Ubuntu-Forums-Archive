---
title: "Network problem"
date: 2010-06-07
forum: Networking &amp; Wireless
---

### Post by rakz on 2010-06-07
I am a first time Ubuntu user. I installed ubuntu 10.04 using wubi-within windows 7. During 1st boot everything was fin...my internet worked properly...didn't even ask for username or password. But from the 2nd boot onwards it shows 'Wired Network Disconnected'. My internet works fine in Windows 7. pls help..i am not understanding even a bit. I tried reading many forums...but didn't understand. I use to connect via pppoe dialer in windows. Its not a wireless.

---

### Post by dineshs on 2010-06-07
Can you post the output of
```
cat /etc/network/interfaces
```

---

### Post by varunendra on 2010-06-07
Additionaly, log into windows, open command prompt **(Start Menu>All Programs>Accessories>Command Prompt)** and type following command:```
ipconfig /all >%userprofile%\desktop\ip.txt
```(you can copy the above command & paste it on the command prompt by mouse right-click>paste)
This will create ip.txt named file on your desktop. Post here the contents of that file (copy-paste, or simply attach the file itself).

---

### Post by rakz on 2010-06-07
Hey thanks for the support. Yes i am gonna do all tat u both told me. Good to see a Indian helping the other. Lol...

---

### Post by varunendra on 2010-06-07
Call me ignorant if u wish, but I noticed we all are Indians only after reading ur post.:)

But what's that "lol" for? After all, we're almost 1/3 of the whole world's population!! So ideally, every third person answering you should be an Indian!!!!:P:P

---

### Post by Iowan on 2010-06-07
As a non-Indian, I may be out of place...
Just-in-case... right-click Network Manager applet and verify that networking is enabled - some threads suggest that updates sometimes "turn off" networking.

---

### Post by rakz on 2010-06-08
```

Windows IP Configuration

   Host Name . . . . . . . . . . . . : Macsoft-PC
   Primary Dns Suffix  . . . . . . . : 
   Node Type . . . . . . . . . . . . : Mixed
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No

PPP adapter nivyahbroadband:

   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : nivyahbroadband
   Physical Address. . . . . . . . . : 
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv4 Address. . . . . . . . . . . : 183.87.42.199(Preferred) 
   Subnet Mask . . . . . . . . . . . : 255.255.255.255
   Default Gateway . . . . . . . . . : 0.0.0.0
   DNS Servers . . . . . . . . . . . : 111.125.255.2
                                       111.125.255.6
   NetBIOS over Tcpip. . . . . . . . : Disabled

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Realtek RTL8168C(P)/8111C(P) Family PCI-E Gigabit Ethernet NIC (NDIS 6.20)
   Physical Address. . . . . . . . . : 00-00-11-91-22-F6
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::74c4:18ae:8d82:5c09%11(Preferred) 
   IPv4 Address. . . . . . . . . . . : 192.168.18.250(Preferred) 
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : fe80::998b:c59:7582:1047%11
                                       192.168.18.1
   DHCPv6 IAID . . . . . . . . . . . : 234938445
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-13-9C-BA-F7-00-E0-4D-C2-30-7E
   DNS Servers . . . . . . . . . . . : fec0:0:0:ffff::1%1
                                       fec0:0:0:ffff::2%1
                                       fec0:0:0:ffff::3%1
   NetBIOS over Tcpip. . . . . . . . : Enabled

Tunnel adapter 6TO4 Adapter:

   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Microsoft 6to4 Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2002:b757:2ac7::b757:2ac7(Preferred) 
   Default Gateway . . . . . . . . . : 2002:c058:6301::c058:6301
   DNS Servers . . . . . . . . . . . : 111.125.255.2
                                       111.125.255.6
   NetBIOS over Tcpip. . . . . . . . : Disabled

Tunnel adapter isatap.{09867DAC-9E02-41F1-A2CA-02F5FEBC4413}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #2
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Teredo Tunneling Pseudo-Interface:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter isatap.{B6AE0B0D-A518-414C-B763-F839F8880D81}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

```

---

### Post by rakz on 2010-06-08
> **dineshs said:**
> Can you post the output of
```
cat /etc/network/interfaces
```

auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual

---

### Post by rakz on 2010-06-08
> **Iowan said:**
> As a non-Indian, I may be out of place...
Just-in-case... right-click Network Manager applet and verify that networking is enabled - some threads suggest that updates sometimes "turn off" networking.

Is it same as the netwok connection..the one located in preferences or Administration ???

---

### Post by rakz on 2010-06-08
Man...u guys are such a pro...Cheers for all u guys der for helping noobs like me. :guitar:

---

### Post by dineshs on 2010-06-08
In aterminal type
```
sudo pon dsl-provider
```
Now try the following commands and post the output
```
ping 4.2.2.1 -c5
```
```
ifconfig -a
```

---

### Post by Iowan on 2010-06-08
> **rakz said:**
> Is it same as the netwok connection..the one located in preferences or Administration ???No, that's the icon in the top right corner that (on my Lucid box) looks like an ethernet socket/connector - sometimes it goes missing...

---

### Post by varunendra on 2010-06-09
> **dineshs said:**
> In aterminal type
```
sudo pon dsl-provider
```Now try the following commands and post the output
```
ping 4.2.2.1 -c5
``````
ifconfig -a
```Would be nice if you can also explain what these commands do. I don't know & am interested.

> **Iowan said:**
> No, that's the icon in the top right corner that (on my Lucid box) looks like an ethernet socket/connector - sometimes it goes missing... He means something like the attached snap (taken from Karmik, not from Lucid).
If you can't find it, right-click on an empty area of the panel, select "Add to Panel", then select "Notification Area" from the list. 'Notification Area' contains this (or the socket-looking) icon along with some other icons.

@Rakesh (aren't you?)
Apparently you are using dsl modem. If it is not already configured for autoconnect, you can set it to automatically connect to broadband as soon as it is powered on. Doing so, you won't need to use a dialer on your pc anymore to connect to the broadband.
Additionally, you can enable dhcp server on it so that you don't need to configure LAN settings manually (I'm assuming it has the dhcp functionality available). Refer to your modem's manual to learn how to configure these (you can ask your Internet Service Provider to do the same for you).

Dialing from Ubuntu is also possible, but only from command line AFAIK. Once connected, the following LAN settings (through Network Manager mentioned above, under IPv4 settings) should do the job for you:

Address: 192.168.18.250
Subnet :  255.255.255.0
Gateway: 192.168.18.1

DNS1: 111.125.255.2
DNS2: 111.125.255.3

I'm sure most of this (if not everything) must have gone above your head, so try whatever you can & ask for help wherever you need!
It'd be really nice to see a noob becoming a pro (I'm not one yet ;)):D:D


Edit: Just realised the existance of "pppoeconf" commandline tool. No time to experiment but looks promising.
```
pppoeconf
```Besides, some GUI tools KPPP, Roaring Penguin, etc. are also out there. (I never needed these as I always configure my adsl modems to connect automatically.)

---

### Post by dineshs on 2010-06-09
DSL can be connected in 2 ways
_Method-1.Modem in BRIDGE mode_
The user has to either run *sudo pppoeconf* command then connect using *pon dsl-provider* and disconnect using *poff dsl-provider* as explained [here]("https://help.ubuntu.com/community/ADSLPPPoE")
Or
Use Network manager(NM) and configure the connection via the DSL tab .It is always better to configure DSL via NM and tick the option _available to all users_
From the contents of */etc/network/interfaces* I think the OP has tried *pppoeconf* command.
_Method-2 Modem in PPPoE mode_
Here the connection is always ON because the connect/disconnect function is done by the modem .Configuring diffferent BSNL modems in PPPoE  mode is explained here
[http://ernakulam.sancharnet.in/ernakulam/bbservice.html](http://ernakulam.sancharnet.in/ernakulam/bbservice.html) 
What varunendra suggests is the second method(He is right)
If you find difficulty in using NM check nm-system-settings.conf
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```
and set
```
managed=true
```
4.2.2.1 is an open DNS .If there is reply when you ping 4.2.2.1 we can ensure that internet is connected.
To get details of a command and options type man followed by the command.For example
```
man ifconfig
```
[http://ubuntuforums.org/showpost.php?p=9430286&postcount=5](http://ubuntuforums.org/showpost.php?p=9430286&postcount=5)

---

### Post by varunendra on 2010-06-09
> **dineshs said:**
> DSL can be connected in 2 ways....... ............ To get details of a command and options type man followed by the command.For example .........

Wow! Well explained Dinesh. Applause & thanx!
Now this is (& will remain for long-I wish) something really understandable & helpful to anyone who is a non-expert.

Let's wait to hear from Rakesh. :)

---

### Post by rakz on 2010-06-09
Thanks guys for ur help...but its not working...maybe a system glitch...I will uninstall and reinstall it again...no more troubling you...but once its done i will be having more doubts,i am sure u guys will help me.

---

### Post by dineshs on 2010-06-09
Before reinstalling pl try this
```
sudo gedit /etc/network/interfaces
```
let the contents be
```
auto lo
iface lo inet loopback


#auto dsl-provider
#iface dsl-provider inet ppp
#pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
#provider dsl-provider

#auto eth0
#iface eth0 inet manual 
```

Now restart your machine and configure NM via DSL tab

---

### Post by rakz on 2010-06-09
Here is my Top panel screenshot....its showing wifi icon i think. But my net used to work @ the 1st boot.

[ATTACH]159862[/ATTACH]

---

### Post by rakz on 2010-06-09
> **dineshs said:**
> Before reinstalling pl try this
```
sudo gedit /etc/network/interfaces
```
let the contents be

auto lo
iface lo inet loopback


#auto dsl-provider
#iface dsl-provider inet ppp
#pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
#provider dsl-provider

#auto eth0
#iface eth0 inet manual

Now restart your machine and configure NM via DSL tab


Yea i will try this in my next reboot. Thanks

---

### Post by dineshs on 2010-06-10
> **rakz said:**
> Here is my Top panel screenshot....its showing wifi icon i think. But my net used to work @ the 1st boot.

[ATTACH]159862[/ATTACH]
Can you right click that icon and tell what are the options?

---

### Post by rakz on 2010-06-15
i am facing the probs again...i am not understanding anything...pls help ppl....here r the screenshots below...


[ATTACH]160512[/ATTACH]

[ATTACH]160513[/ATTACH]

---

### Post by dineshs on 2010-06-15
Can you post the contenets of
```
cat /etc/NetworkManager/nm-system-settings.conf
```
and
```
cat /etc/network/interfaces
```

---

### Post by rakz on 2010-06-15
The first one it says NO SUCH FILE OR DIRECTORY

2nd
auto lo
iface lo inet loopback

---

### Post by varunendra on 2010-06-15
> **rakz said:**
> The first one it says NO SUCH FILE OR DIRECTORY

2nd
auto lo
iface lo inet loopback

Mind the case of letters (type exactly as he wrote-caps in caps, smalls in smalls)


PS: Right-click on the network icon>Edit Connections. Send the screen shot.

Also, select Auto eth1 in the list, click edit, click on tab- IPv4 Settings. Send screenshot.

---

### Post by rakz on 2010-06-15
Yea i had forgot to write / before etc. But now it says permission denied. ;-(

---

### Post by dineshs on 2010-06-15
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf 
```

---

### Post by rakz on 2010-06-15
A file opened. But its empty.

---

### Post by varunendra on 2010-06-15
> **rakz said:**
> A file opened. But its empty.

r u typing 'N' & 'M' in caps in NetworkManager? (without space between words)

EDIT: copy the code posted by Dinesh & right-click>paste in terminal.

---

### Post by rakz on 2010-06-15
Yea a file opened but its empty.

---

### Post by varunendra on 2010-06-15
Post the screenshots I asked:
> **varunendra said:**
> PS: Right-click on the network icon>Edit Connections. Send the screen shot.

Also, select Auto eth1 in the list, click edit, click on tab- IPv4 Settings. Send screenshot.

Did you succeed earlier to connect? (After the attempts you made a few days earlier)
If yes, how then?

Do you still dial from PC?

---

### Post by dineshs on 2010-06-15
I dont understand why.Anyway try *sudo gedit /etc/NetworkManager/nm-system-settings.conf *
and if the file opens ensure 
```
managed=true
```
Now try to configure your connection via DSL tab in NM
Right click the NM icon and click edit connection
click on DSL
add
enter username and password(serice name say internet)
select the option *available to all users* and apply
Now you can connect or disconnect this DSL connection by clicking on the NM icon
Does this help?
If not pl post the output for
```
ifconfig -a
```

---

### Post by rakz on 2010-06-15
Ok guys i ll do it when i ll login in ubuntu...coz currently i am in windows. Btw how did u learn all this ? U guys know everything.

---

### Post by varunendra on 2010-06-15
> **rakz said:**
> Ok guys i ll do it when i ll login in ubuntu...coz currently i am in windows. Btw how did u learn all this ? U guys know everything.
lol :D

Once you figured it out (your problem) you'll know it "all" (at least what others would think of u, just like u r thinknig of us right now). That's how I know whatever I know (it is called "try & error method") ([Here's me]("http://ubuntuforums.org/showpost.php?p=9408238&postcount=92")). Dinesh may have a different story (He is (apparently) more mature at this after all!)

---

