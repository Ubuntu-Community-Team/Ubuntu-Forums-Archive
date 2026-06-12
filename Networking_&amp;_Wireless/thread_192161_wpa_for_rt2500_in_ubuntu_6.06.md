---
title: "wpa for rt2500 in ubuntu 6.06"
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by anuski on 2006-06-08
Hi everybody,

For a few days now, i have been trying to make my wireless PCMCIA card work with no success, so i have decided to cry out for help. I have ubuntu 6.06 installed in a compaq Evo N1100. The card is Conceptronic, with ralink rt2500 chipset and i need to use wpa (i think this is the big issue). I have tried the suggestions of about every howto available, but i cant make it work(and i actually find it very confusing they vary quite a bit form one to another). My knowledge about computers in general and linux in particular is very, very little. This means a number a things: any input will be very much appreciated (and probably of a lot of help), i have loads of questions, and i will probably say things out of my ignorance that will make many of you revolt, so i excuse myself in advance.

Ubuntu has always seen my card, since the first time i plucked it in. I actually started with ubuntu breezy, then upgraded it to 6.06. The only difference is that now it is identified as eth1 rather than ra0 (eth0, wired connection worked ok straight away).

Now, about the drivers issue. I think they are working alright and that my only trouble is wpa encrytation, but i don know if i have enough evidence. I can't change the net's security so i can't just remove security to see if that way it will work. But when i do a iwconfig eth1 i get:

	eth1      RT2500 Wireless  ESSID:""
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:1 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Once i make the card active with ifconfig eth1 up, scanning for wireless nets with iwlist i get:

	eth1      Scan completed :
          Cell 01 - Address: 00:16:38:C4:FF:58
                    Mode:Managed
                    ESSID:"myessid"
                    Encryption key:on
                    Channel:12
                    Quality:0/100  Signal level:-19 dBm  Noise level:-192 dBm

which is the net i want to get connected to. Using graphic tools such as wifi-radar or wireless assistant, i can also detect it alright and show a perfect quality signal.

So, from this information, can i be sure the card+drivers are working correctly and my only trouble is to configure WPA?

So now, about the wpa. I have read rt2500 drivers natively support wpa, so i don need to use wpa-replicant. I have checked and i do have it installed though. Can this be interfering in way and causing the problem? If so, what should i do about it? 

If drivers are ok and wpa-replicant is not a problem, then the only thing left is configuring wpa options in /etc/network/interfaces. Am i right? Now this part i have been changing all the time to try all the different suggestions, and nothing has worked. Right now it reads:

	iface eth1 inet dhcp
pre-up iwconfig eth1 essid "myessid"
pre-up iwconfig eth1 mode Managed
pre-up iwpriv eth1 set AuthMode=WPAPSK
pre-up iwpriv eth1 set EncrypType=AES
pre-up iwpriv eth1 set WPAPSK="password"
pre-up ifconfig eth1 up


Any suggestions?


Finally, is there a way to do this in graphic mode? I know gnome network manager doesn't support WPA. I have seen though wifi-radar does. Is this only through wpa-replicant? Should i give it a try? It asks for a driver, what should go there in my case?

Sorry for the long post, but i wanted to make myself clear. Any help, advice, suggestions, documentation will be very much appreciated.

---

### Post by ComplexNumber on 2006-06-08
> 
So now, about the wpa. I have read rt2500 drivers natively support wpa, so i don need to use wpa-replicant. go to services in your menu and switch it OFF. also, don't have it run at boot time. it stops the internet conenction from working. i switched it of and it immedsiately asked for my password to connect.
> 

It asks for a driver, what should go there in my case? the driver is rt2500.


i'm not even sure that any of whats put it wifi-radar makes any difference. it seems to be netowrk-manager thats doing the bulk of the work in getting a successful connection. incidently, i haven't typed anything into the network manager gui.

---

### Post by polo_step on 2006-06-08
[QUOTE=anuski]
If drivers are ok and wpa-replicant is not a problem, then the only thing left is configuring wpa options in /etc/network/interfaces. Am i right? Now this part i have been changing all the time to try all the different suggestions, and nothing has worked. Right now it reads:

iface eth1 inet dhcp
pre-up iwconfig eth1 essid "myessid"
pre-up iwconfig eth1 mode Managed
pre-up iwpriv eth1 set AuthMode=WPAPSK
pre-up iwpriv eth1 set EncrypType=AES
pre-up iwpriv eth1 set WPAPSK="password"
pre-up ifconfig eth1 up


Any suggestions?
[/QUOTE]
[FONT="Courier New"]No, but I'm following this careully.

I have a MiniPCI RT2500 (which is seen as ra0) and get the same results as you mentioned from the first two.  I'm running in "Live" mode, so I can't write anything to a file to be read at boot.

Can you somehow manually enter the above WPA-related strings in terminal and get a WPA connection with your AP? [/FONT]

---

### Post by phace on 2006-06-08
Well guys... Why dont you try the wpa supplicant program ? Download it "sudo apt-get install wpasupplicant". After downloading do this:
wpa_passphrase xxxxx yyyyyyyyyyyyyy
where xxxxx is essid and yyyyyyyyyyyyy is the encryption key. After that import everything that it outputted in an file (for example /etc/wpa_supplicant/wpa.conf). After putting it configure it with the needs of your access point. I am using WPA2 encryption (pre-shared key only) and TKIP and my config looks like:

ctrl_interface=/var/run/wpa_supplicant

network={
        key_mgmt=WPA-PSK
        proto=WPA2
        pairwise=TKIP
        ssid="ssid"
        #psk="somekey"
        psk=an key... really long key
}

so the first line has to stay there... the ctrl_interface
after i mentioned TKIP as an pairwise option i putted it there. WPA-PSK stands for WPA Pre-Shared-Key. WPA2 is an protocol version of WPA.
that's all. For more information read the man pages

---

### Post by ComplexNumber on 2006-06-08
> Why dont you try the wpa supplicant program ? i already have. when i had the service running, i couldn't connect. when i switched it off, it connected to the internet immediately (after asking for my password). i'm running a belkin F5D7000 with rt2500 driver.

---

### Post by anuski on 2006-06-09
I am sorry if i make really dumb questions but i just can't figure out how to disable wpasupplicant. What services in which menu? And what should i do to avoid it from running on reboot? 

I installed network-manager-gnome because i read it supported wpa. A new network icon did appear on reboot (i guess that is NM, but don't know if it is a wrong guess). When i click on it and change it to wireless, it does recognise the net right away and prompts me for password, but still only allows wep.

Well, at least this is being a learning experience:)

---

### Post by ComplexNumber on 2006-06-09
> I am sorry if i make really dumb questions but i just can't figure out how to disable wpasupplicant. What services in which menu?
in the admin menu(there are 3 menus - applications, places, system. you want the 3rd one). then go into admin. you will see services. click on that and give your password. look down the list until you see wpa_supplicant. highlight it, then click it OFF if it isn't already. if it currently running, then click the 'stop' button.

---

### Post by frenkel on 2006-06-09
Don't use any graphical tool or wpa_supplicant, because it's not fully supported.
Read this wiki page and use that, it works great:
[https://wiki.ubuntu.com/WifiDocs/RalinkRT2500?action=show&redirect=Rt2500WirelessCardsHowTo](https://wiki.ubuntu.com/WifiDocs/RalinkRT2500?action=show&redirect=Rt2500WirelessCardsHowTo)

---

### Post by polo_step on 2006-06-09
[QUOTE=frenkel]
Read this wiki page and use that, it works great:
[https://wiki.ubuntu.com/WifiDocs/RalinkRT2500?action=show&redirect=Rt2500WirelessCardsHowTo](https://wiki.ubuntu.com/WifiDocs/RalinkRT2500?action=show&redirect=Rt2500WirelessCardsHowTo)[/QUOTE]
[FONT="Courier New"]WHAT "works great"?  :confused: 

The entire page is a welter of contradictions and arguments about what method's required, plus it's for previous versions -- and posts here claim that 6.06 requires entirely different procedures. [/FONT]

---

### Post by anuski on 2006-06-09
Ok, there is no wpa-supplicant in my services, so i guess it is not running and so is definately not the problem. 

I have found out at [http://live.gnome.org/NetworkManagerHardwaren](http://live.gnome.org/NetworkManagerHardwaren) that rt2x00 drivers will only support wep encryption (in accord to what i am getting) as they don't use wpa-supplicant (they support wpa natively). At ubuntu's wiki [https://wiki.ubuntu.com/NetworkManager](https://wiki.ubuntu.com/NetworkManager) they also mentioned this problem in dapper for these type of drivers and suggested using and older version (which i downloaded and installed but couldn't even get working at all--any input on that?).

So complexnumber, i am really curious because you use my very same driver and apparantly (as i found out in another thread) you are using network manager. Is this it? Are you using breezy or dapper? What version of nm?

By the way, a new version of rt2500 has just been released and had network manager in its last version as a dependency. I thought this might be the solution to all my troubles but upgrading had no effect whatsoever. Any info on this?

Frenkel, that was one of the first links i tried without success, but i must confess i was far more ignorant on this subject (still;)) so i am going to give it another try right now to see what happens.

Thanks everybody for comments and support, it is really very appreciated.

---

### Post by ComplexNumber on 2006-06-09
> So complexnumber, i am really curious because you use my very same driver and apparantly (as i found out in another thread) you are using network manager. Is this it? Are you using breezy or dapper? What version of nm? i'm not using ubuntu. i'm using fedora core 5. i am using network manger. HOWEVER, i have not entered any details of my card in there. when i clicked on the wireless connection, then clicked 'next', it just showed ;other wireless card'. there was NO selection for ndiswrapper. plus, when i did select 'other wireless card', i couldn't find raylink (i found raylink, but they're not the same as far as i know). therefore, i didn't sue it. i used wifi-radara....but whether it actually did any good i don't know. i noticed that network manager seemed to have sussed out my routers IP on its own because the file resolv.conf showed something like:
> #GENERATED BY NETWORK MANAGER. DO NOT EDIT!!!

nameserver 192.168.1.1 i'm really not sure if its got that information from wifi-radar, but something tells me that it must have autodetected my routers Ip instead.


> By the way, a new version of rt2500 has just been released and had network manager in its last version as a dependency. I thought this might be the solution to all my troubles but upgrading had no effect whatsoever. Any info on this? no. i'm using version 2.4.5(or 3.4.5).

---

### Post by frenkel on 2006-06-09
> **anuski]Ok, there is no wpa-supplicant in my services, so i guess it is not running and so is definately not the problem. 

I have found out at [http://live.gnome.org/NetworkManagerHardwaren](http://live.gnome.org/NetworkManagerHardwaren) that rt2x00 drivers will only support wep encryption (in accord to what i am getting) as they don't use wpa-supplicant (they support wpa natively). At ubuntu's wiki [https://wiki.ubuntu.com/NetworkManager](https://wiki.ubuntu.com/NetworkManager) they also mentioned this problem in dapper for these type of drivers and suggested using and older version (which i downloaded and installed but couldn't even get working at all--any input on that?).

So complexnumber, i am really curious because you use my very same driver and apparantly (as i found out in another thread) you are using network manager. Is this it? Are you using breezy or dapper? What version of nm?

By the way, a new version of rt2500 has just been released and had network manager in its last version as a dependency. I thought this might be the solution to all my troubles but upgrading had no effect whatsoever. Any info on this?

Frenkel, that was one of the first links i tried without success, but i must confess i was far more ignorant on this subject (still said:**
> 

Make sure you add all the if up and down stuff also, it's very important, doesn't work for me without it.
This is what I use:
[quote]
auto ra0
iface ra0 inet static
        address 192.168.0.3
        netmask 255.255.255.0
        gateway 192.168.0.1
        pre-up ifconfig ra0 down
        pre-up iwconfig ra0 essid <ssid>
        pre-up iwpriv ra0 set AuthMode=WPAPSK
        pre-up iwpriv ra0 set EncrypType=TKIP
        pre-up iwpriv ra0 set WPAPSK=<wpakey>
        pre-up ifconfig ra0 up


---

### Post by anuski on 2006-06-09
Well, definately, none of the different suggestions in [https://wiki.ubuntu.com/WifiDocs/RalinkRT2500?action=show&redirect=Rt2500WirelessCardsHowTo#wpa](https://wiki.ubuntu.com/WifiDocs/RalinkRT2500?action=show&redirect=Rt2500WirelessCardsHowTo#wpa)
worked out for me. Is there something i am missing? Can anyone refer me to a nice tutorial on wireless configuration?

---

### Post by polo_step on 2006-06-09
[QUOTE=anuski] Can anyone refer me to a nice tutorial on wireless configuration?[/QUOTE]
[Crickets chirping]

[FONT="Courier New"]I'm really beginning to think trying to get wireless working **properly** in Linux is just beating a dead horse.  The factory Linux drivers for this Ralink chipset have been out and in "the community" for nearly two years and it was the "Linux Product of the Year," in some print Linux rag, yet no distribution supports it yet in the sense of working transparently with full features the way it does in XP in five minutes.

Freakin' disgusting![-( 
[/FONT]

---

### Post by anuski on 2006-06-12
Now, i have been able to change my wireless net's security settings and i think i am getting very weird results. All wifi-radar, wireless assistant, network manager or iwlist scan detected my net when it was wpa encrypted, that was what made me thought it must be thw wpa causing troubles.

But when i made the net open, no wep or wap, the results were exactly as above. This didn't bother me that much, because surprisingly it wouldn´t connect either with windows xp (which had had no problems when it was wpa).

No the really weird stuff. I change security to wep. Again no problems at all with xp. Now when i change to ubuntu, network manager can no longer detect my net. Wireless assistant will but won´t connect. Wifi radar detects the net but its signal quality will turn on and off. And that is exactly what thw iwlist scan usshows, sometimes it will detect the net, others it won't.

I think i am going to start another thread anyway,now the subject is misleading. But, any idea of what is going on? Any suggestions?

---

### Post by Kenzy on 2006-06-14
[QUOTE=anuski]Now, i have been able to change my wireless net's security settings and i think i am getting very weird results. All wifi-radar, wireless assistant, network manager or iwlist scan detected my net when it was wpa encrypted, that was what made me thought it must be thw wpa causing troubles.

But when i made the net open, no wep or wap, the results were exactly as above. This didn't bother me that much, because surprisingly it wouldn´t connect either with windows xp (which had had no problems when it was wpa).

No the really weird stuff. I change security to wep. Again no problems at all with xp. Now when i change to ubuntu, network manager can no longer detect my net. Wireless assistant will but won´t connect. Wifi radar detects the net but its signal quality will turn on and off. And that is exactly what thw iwlist scan usshows, sometimes it will detect the net, others it won't.

I think i am going to start another thread anyway,now the subject is misleading. But, any idea of what is going on? Any suggestions?[/QUOTE]

Well, I have pretty much experience of WLAN-technology, thanks to Zyxel Prestige 660HW-61, which isn't the best "plug and pray"- router. Although, I have two RT2500-based cards, one in my server (PCI) and one in my laptop (PCMCIA). I'm using Dapper Drake and WPA is working fine. I haven't even tried wpa_supplicant or NetworkManager, because I've read that both of those programs are having problems with this chipset. After I installed my Ubuntus, both of my WLAN-cards were detected as ra0. After that, just sudo pico /etc/network/interfaces -->
```

auto ra0
iface ra0 inet static
        address 192.168.1.35
        gateway 192.168.1.1
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up iwconfig ra0 essid "MyEssidWithoutSpaces"
        pre-up iwconfig ra0 mode Managed
        pre-up iwpriv ra0 set AuthMode=WPAPSK
        pre-up iwpriv ra0 set EncrypType=TKIP
        pre-up iwpriv ra0 set WPAPSK="MySecretPSKWithoutSpaces"
        pre-up ifconfig ra0 up

```
As you can see, I have configured cards with static ip-address, but you can edit them use dchp also, just remove lines before the first ifup-line, and edit the very first ra0-line look like "iface ra0 inet dhcp".

The second thing I noticed was that you're using channel number 12? As far as I've discovered this Ubuntu <--> WLAN-issue, I haven't found channels bigger than 11 working at all in Ubuntu.

EDIT: and of course after that, "sudo /etc/init.d/networking restart" restarts the network connections.

---

### Post by lennox on 2006-06-22
Hey, I also had Problems with WPA since upgrading to dapper (it worked fine in breezy), but it worked after I changed two things:
I stopped using dhcp and started using a static IP configuration. Its better anyway..

In breezy I just entered my psk in ascii like I would enter it in WinXP or in the router, but now I entered the psk output of
wpa_passphrase <ssid> <ascii - psk>
(which is just the hex version of the ascii psk? Or maybe something else as it also needs the ssid).

I don't know which part did the trick, but its working fine now.

---

### Post by queenorych on 2006-06-22
Keep in mind that iwconfig will list the access point it is connected to when connected.  It will say the selected essid as soon as you put in the essid, but it will only show the ap when connected!  

The rt2500 that comes with dapper is an old cvs release you could try the new version, or the new driver series rt2x00.

With the rt2500  you cannot use wpasupplicant!

With the rt2500 and wap its my understanding you have to do a "pre-up ifconfig ra0 down; ifconfig ra0 up" a couple of times before, see the posts, howto guides.  I would make a bash script until you get everthing working write, as you may be running into wpasupplicant, and other configureation scripts laying around.  Make sure wpasupplicant is not listed when you type lsmod.

---

### Post by pcbodger on 2006-06-22
After weeks of messing around I got a long LAN cable for a hard network connection and used

[http://www.ubuntuforums.org/showthread.php?t=185174&highlight=broadcom+dapper]("http://www.ubuntuforums.org/showthread.php?t=185174&highlight=broadcom+dapper")

Took me 20 minutes and I was up and running without a single hitch - no messing with config files at all.

Just remember to turn off the hard lan and turn on the wifi in network manager before any serious surfing.

---

### Post by queenorych on 2006-06-22
I take it you are talking about using your internal broadcom card.  I had a 4301 card, which worked ok, but hubernate would not work.  I also attribute it to a few system hard locks.  The driver was created without any specs and only a mips reference driver, so it has a few issues.

I replaced my broadcom (only 802.11b) mini-pci with an new rt2500 from newegg ($20 ships), hibernate works great.  If your getting a new mini-pci I'd look into getting an intel, as they seem the best supported.

---

### Post by nquinnathome1 on 2006-06-23
Kenzy you just saved my life; adding your string to my interfaces file allowed me to use WPA! Thanks!

---

### Post by johnnyrico on 2007-03-12
A million thank yous Kenzy, your config worked. After trying many, many other variations of it and ndiswrapper etc (only to find it was supported natively) my CWC 854 card is now working with Ubuntu 6.06.


Cheers,

---

