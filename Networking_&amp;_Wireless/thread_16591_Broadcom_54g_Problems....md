---
title: "Broadcom 54g Problems..."
date: 2005-02-22
forum: Networking &amp; Wireless
---

### Post by acascianelli on 2005-02-22
I have Ubuntu 5.04 installed on my Emachines M5310.  Everything is running great on it except for the wireless.  I *think* i have it working with the NDISWrapper ok.  It is recognized when i do a iwconfig and its identified as wlan0.  However, i am unable to assign it a ESSID using either the gnome network configurator or the command line.  it will not take some settings I try to give it, mainly the ESSID.  

Please help me if you can, getting my wireless networking working is the last thing that is preventing me from leaving Windows all together and going completely Linux.

---

### Post by alastair on 2005-02-22
You need to give some detail - to at least reassure that the device is present i.e. output of

ifconfig -a

and

iwconfig

If we assume your connection is present, some wireless things depend on whether the ESSID is broadcast or cloaked etc.

I sometimes have problems, but manually set the "ap" (access point), ESSID and key i.e. something like :

iwconfig eth1 ap <ap MAC>
iwconfig eth1 key restricted <key>

Does this help?

---

### Post by yatesco on 2005-02-23
I have the same problem.  I heard from the great google somewhere (can't find it again) that there are problems setting the essid if you are connecting to a restricted ap.

Kind of chicken and egg problem.

Sorry not to be any more help, but rest assured you are not alone :)

The same problem on Fedora, SuSE, gentoo etc...

---

### Post by acascianelli on 2005-02-23
[QUOTE=ifconfig -a]eth0      Link encap:Ethernet  HWaddr 00:03:25:08:5D:5D
          inet addr:192.168.71.77  Bcast:192.168.71.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe08:5d5d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5483 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8062 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4400765 (4.1 MiB)  TX bytes:651957 (636.6 KiB)
          Interrupt:11

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22607 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22607 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2504165 (2.3 MiB)  TX bytes:2504165 (2.3 MiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:90:96:5B:ED:C1
          inet6 addr: fe80::290:96ff:fe5b:edc1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Memory:d0004000-d0005fff[/QUOTE]

Obviously wlan0 is my wireless device.

[QUOTE=iwconfig]lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.[/QUOTE]

As you can see the ESSID is set to off/any.  even if i do a iwconfig wlan0 essid "asdf", the value will not change.

[QUOTE=ndiswrapper -l]Installed ndis drivers:
bcmwl5  driver present, hardware present[/QUOTE]

This shows that the ndiswrapper is detecting the card correctly, i think.  The wireless network im trying to connect to is NOT restricted or secured in any manner.  the ESSID is "LTU Wireless Network", it is my schools network.

---

### Post by alastair on 2005-02-23
Is the ESSID broadcast?

Do you know the ap's MAC? Try :

iwconfig wlan0 ap <ap MAC>
iwconfig wlan0 key open
iwconfig wlan0 essid "LTU Wireless Network"

---

### Post by acascianelli on 2005-02-23
[QUOTE=alastair]Is the ESSID broadcast?

Do you know the ap's MAC? Try :

iwconfig wlan0 ap <ap MAC>
iwconfig wlan0 key open
iwconfig wlan0 essid "LTU Wireless Network"[/QUOTE]
 the essid IS being broadcasted.  it is a roaming network that spans the entire campus.  the 3rd compand you said does nothing, it just stays on off/any.

---

### Post by alastair on 2005-02-23
See if you can see the wireless network if you scan for it e.g.

iwlist wlan0 scanning

---

### Post by acascianelli on 2005-02-23
[QUOTE=alastair]See if you can see the wireless network if you scan for it e.g.

iwlist wlan0 scanning[/QUOTE]
 iwlist wlan0 scanning returns nothing, and i know for a fact that it should be see the LTU Wireless Network ssid...

---

### Post by alastair on 2005-02-23
If you can then, I'd want to verify the thing works at all i.e. can connect to some/any wireless. You might  know that Broadcom is not famous for Linux support and, secondly, ndiswrapper is a bit of a hack around this. IF nothing works (and note that I have sometimes had to persevere myself, even with the centrino ipw2100), then you might need to :

a) wait for ndiswrapper to work (check their website)
b) buy an alternative, cheap wireless solution

This is just a guess though - and perhaps wrong. I'd look on the ndiswrapper lists, and do some google research. Maybe "scanning" is known not to work, but you can still get connected.

---

### Post by acascianelli on 2005-02-24
i know that other people have gotten this wireless card to work with the ndiswrapper.  some people even used the same notebook and reported it working.

theres go to be someone that knows how to do this...

ive come to the conlusion that the ndiswrapper is not communicating correctly with the card, because even if i turn the card off using fn+f2, ndiswrapper still reports that the card is present and working.  im going to try an older version of the driver to see if that makes a difference.

---

### Post by acascianelli on 2005-02-24
ITS WORKING !!!!

This was the problem, i found this posted on ndiswrapper.sourceforge.net...

> Card: Broadcom 802.11a/b/g Mini PCI wlan chipset hand installed in ASUS M6000BNe laptop
Chipset: Broadcom Mini PCI wlan BCM4306
pciid: 14e4:4320 (rev 03)
Driver: Works with driver from ASUS website (see elsewhere on this page) with changes to ndiswrapper conf file.
Other: Using kernel 2.6.10, ndiswrapper 0.12+1.0rc2-1 Debian package. ndiswrapper incorrectly sets RadioState? to 1, when 0 means "enable" and 1 means "disable". The card did not use the default 14E4:4320.conf file; I had to change the ones with longer names. I also set the country code, although this may not matter. For explanations, see the Win98 .inf file, which is plain text and contains brief descriptions of the options. WEP etc. not yet tested.

...sure enough, when i went and changed the radiostates it started working.  im still having a few problem, it freezes the laptop when i try to do a iwlist wlan0 scanning.

I have WPA-PSK enabled on my network at home and it doenst look like its working with that, but i was able to connect to unsecured networks fine.

---

### Post by bcorcoran on 2005-03-06
I have this same chipset (minipci and all) on my compaq r3210us... i've never, ever gotten it to work on any distro of linux... could you tell me how / where you changed the namestates? I am confused! but I would like it to work! Maybe then we can post this in the WIKI for future users of this same hardware?

---

### Post by acascianelli on 2005-03-07
[QUOTE=bcorcoran]I have this same chipset (minipci and all) on my compaq r3210us... i've never, ever gotten it to work on any distro of linux... could you tell me how / where you changed the namestates? I am confused! but I would like it to work! Maybe then we can post this in the WIKI for future users of this same hardware?[/QUOTE]

ok, ill try to explain this a little better...

/etc/ndiswrapper/bcmwl5/

there are a bunch of files in here.  there is a .conf file that is actually a link to another file.  edit the file that the link points to and down the page there is an option that says "RadioState|1", change the 1 to a 0 then save and hopefully youll be good to go.

---

### Post by bcorcoran on 2005-03-07
Thank you so much! It works!

This really is important to me, because I have never gotten my laptop's wireless to work on ANY distro before Ubuntu--truly, this is a breakthrough!

Here's what I did:
```

[THIS MY EXPERIENCE FOR COMPAQ R3210US (R3000 SERIES) LAPTOP WITH INTEGRATED BROADCOM BCM94306 54G MINIPCI WIRELESS ADAPTER]

[MY ADVICE IS THAT YOU USE THE DRIVER OFF OF YOUR DRIVER CD/DVD THAT CAME WITH YOUR LAPTOP/WIRELESS CARD]

[INSTRUCTIONS/COMMENTS ARE IN BRACKETS -- THEY ARE NOT TO BE TYPED IN THE CONSOLE AND THEY DO NOT REPRESENT ACTUAL OUTPUT]


$sudo ndiswrapper -i /media/cdrom0/SWsetup/WLAN/bcmwl5a.inf
[installs without problems -- but if it does: try using bcmwl5.inf]

$sudo ndiswrapper -l
Installed ndis drivers:
bcmwl5a driver present, hardware present


$sudo ndiswrapper -m
ndiswrapper device bcmwl5a added (this just adds ndiswrapper module to modprobe to load on boot)

$cd /etc/ndiswrapper/bcmwl5a/

$ls
14E4:4301:103C:12F3.conf  14E4:4320:0E11:00E7.conf  14E4:4320.conf  bcmwl5.sys
14E4:4301.conf            14E4:4320:103C:12F4.conf  bcmwl5a.inf

$sudo nano [for all .conf files]
[In nano, ^W and search for radiostate. ("^" = CTRL key)]
[replace the Radiostate|0 with Radiostate|1]
[^O, press Enter, ^X]

$sudo reboot

[AFTER REBOOT]
[While booting up, make sure wireless radio light is on (if you have one)]
[If your wireless radio light is not on, it WILL NOT work]

$network-admin

[Click on the wireless, click configure, select your ESSID, and enter your WEP key (if needed)]
[Congrats! you're finished!]
[I hoped this helped!!! Remember, I am a linux noob too!]


```

It now works perfectly fine with WEP (128bit -- have not tried unsecure, WPA/WPA-PSK or 64bit, although I am fairly sure it would work)!

This was my last hurdle before switching entirely to Linux for my laptop (as my Windows tower is for gaming only). Now if I can just get wine to work with FlashFXP...  :mrgreen: 

THIS IS BEING POSTED WIRELESSLY!

---

### Post by acascianelli on 2005-03-07
[QUOTE=bcorcoran]...
This was my last hurdle before switching entirely to Linux for my laptop (as my Windows tower is for gaming only). Now if I can just get wine to work with FlashFXP...  :mrgreen: 
...[/QUOTE]

if your having a hard time with wine, try getting a copy crossover office.  i use gftp for my ftp client.

---

### Post by bcorcoran on 2005-03-07
In Linux I use gFTP currently, however my favorite FTP client ever is FlashFXP... [www.flashfxp.com](www.flashfxp.com) -- if you ever use ftp on windows, you should definately try it out ( I even purchased it -- and I dont purchase many programs).

---

### Post by Mlehliw on 2005-03-07
I have an M5310 too unfortunately, anyway does it matter whether you choose the bcmwl5.inf file or the bcmwl5a.inf file?

---

### Post by acascianelli on 2005-03-08
[QUOTE=Mlehliw]I have an M5310 too unfortunately, anyway does it matter whether you choose the bcmwl5.inf file or the bcmwl5a.inf file?[/QUOTE]

i tried the bcmwl5.inf first and it worked, ive never tried the other file.

---

### Post by jonny on 2005-03-08
The radiostate tweak is a real revelation!  The web is littered with questions from frustrated users who can't get these cards to work.  And it works for me, too!

 - Ubuntu 5.04 Hoary
 - Dell Latitude 100L laptop
 - Dell Wireless WLAN 1450 Dual Band mini PCI card (in Windows); Broadcom 1403 (in Linux)
 - Driver file bcmwl5.inf supplied by Dell and installed on PC

Now my card switches on and iwconfig shows me the Access Point.  It's just a shame that I can't get an IP address back... that's tonight's homework!

---

### Post by bcorcoran on 2005-03-09
The difference between bcmwl5 and bcmwl5a is that one file is a compiled driver and the other is a plaintext version. Some cards can not interpret the compiled version, which is why they made a plaintext one.

ALL cards should work with bcmwl5a, however it may be safe to use bcmwl5, if your specific card supports it.

As for your IP address problem, Jonny, I recently had to set up the ndiswrapper config again, and after installing bcmwl5a and changing the radiostate numbers, all I did was:

-Click on the little networking icon up near the time (if thats where your networking icon is), set the device to wlan0 (if it is not listed, type it in)
-Then click configure
-Once network-admin is up, go to the properties of the wireless device, select your SSID, enter the WEP if necessary, make sure its set to DHCP, and click OK.
-Activating wlan0 should take less than 10 seconds. 
**If it doesn't, your router doesnt know what to do with your linux connection -- in short, you're f*cked. The way I have come to this conclusion, is that everything works fine with WEP at my workplace on a Netgear 802.11B/G router. At home, it does NOT work, and my router is a D-Link SuperG router (also 802.11B/G). I have tried turning off the so-called "Super G" and even setting the router to 802.11B/G compatible (by default, it is G only) to no avail. D-Link's SuperG router just can not handle the type of request sent by this card in Linux.**
-Once wlan0 is activated, make sure the Default Gateway Device is set to wlan0, and click OK. The window should disappear rather quickly. If it doesn't, read the bold text above.
-Now you're good to go. In my experience, trying to set everything manually with iwconfig just messes things up, because network-admin handles all internet connections by default, so there should be no need to use ifconfig or iwconfig on any connection (unless, of course, you're doing something that shouldn't be discussed   [-X   but then you're on your own  :-))

I hope this helps... I really should make a wiki for this...

---

### Post by Patrol on 2005-03-11
I had exactly the same problem ( my card is recognized, driver installed, essid :"Off/any"...) but your solution didn't work with me ...
But I just noticed that when I enter *ifconfig* , I see my "wlan0", but if I enter *iwconfig*  I don't see "wlan0" anymore...
I'm fed up with this problem ^^.
Please help me !

---

### Post by jonny on 2005-03-11
OK, I now have wireless networking working reliably with this card.  In addition to the problems outlined in the post above (the need to use ndiswrapper and change the radio state), I found the gui doesn't work for me.  I've started a separate thread ([http://www.ubuntuforums.org/showthread.php?p=91470#post91470](http://www.ubuntuforums.org/showthread.php?p=91470#post91470)) on that issue, as I've found it's not specific to the Broadcom card.

I've also completely failed to get ifconfig to bring up the network (despite having a qualified Unix networking expert to help me!), but I've found that ifup works fine.  Add these lines to /etc/network/interfaces (first remove any straggling lines referring to your interface and back up the file):

```
iface wlan0 inet dhcp
wireless_essid MyNetwork
wireless_key s:MyKey
```

Obviously, you shoul replace the wlan0, MyNetwork and MyKey as appropriate.  If you're not usingWEP, you only need the first line; if you're not using DHCP then you're on your own - sorry.

Once you've saved the file, enter iwconfig to check that your device is up, make sure the LED is lit and then type ifup wlan0 (or whatever your device is called.

Good luck.  These cards *can* be made to work.

---

### Post by Patrol on 2005-03-12
No it doesn't work...

---

### Post by jonny on 2005-03-13
[QUOTE=Patrol]I had exactly the same problem ( my card is recognized, driver installed, essid :"Off/any"...) but your solution didn't work with me ...
But I just noticed that when I enter *ifconfig* , I see my "wlan0", but if I enter *iwconfig*  I don't see "wlan0" anymore...
I'm fed up with this problem ^^.
Please help me ![/QUOTE]
If you can see the card with ifconfig but not iwconfig, are you sure the driver is properly loaded?  I guess your light's not on, either?  I found that the ndiswrapper -m command doesn't work properly for me; I have to use ```
sudo modprobe ndiswrapper
```every time I restart the computer.

Why not start again  from the beginning?  Use ```
sudo ndiswrapper -e bcmwl5.inf
``` to remove the driver, and then follow each of these steps in order (details for each are further up the thread):

1. Install the driver with ndiswrapper (see above)
2. Deal with the radiostate problem (see above)
3. Edit your /etc/network.interfaces file, delete any existing stanza for wlan0, and add these lines:
```
iface wlan0 inet dhcp
wireless_essid MyNetwork
wireless_key s:MyKey
```4. To use your card, enter this code each time you turn on your computer:
```
sudo modprobe ndiswrapper
sudo ifup wlan0
```
I hope this helps.  Let us know how you get on.

---

### Post by Patrol on 2005-03-13
Yeeeeeeeeeepah.
It works now !
jonny : I followed your idea 
The problem was there : "iface wlan0 inet dhcp" I just added linksys after "dhcp" and everything works fine !
Thank you all !

---

### Post by WilliamE on 2005-03-17
Followed the instructions here several times, can't get this to work.  Problem I'm running into is that my wireless light doesn't come on (works fine in windows on same machine).  Laptop is r3310ca.  Any ideas?

---

### Post by jonny on 2005-03-17
If your light doesn't come on, the driver hasn't loaded properly.  The light should come on immediately after typing modprobe ndiswrapper, and it should stay on.  Are you getting any strange error messages when you walk through the steps?  If not, you could try different flavours of the driver - I had to use the one installed on my Windows partition; the downloaded Dell drivers didn't do it for me.

---

### Post by WilliamE on 2005-03-18
No Errors.  tried the bcmwl5 and bcmwl5a drivers from the driver cd (same one that windows is using) no luck.  Going to see if there are any I can download.

---

### Post by jonny on 2005-03-19
One off the wall thought.  On my laptop, a Dell, if I exit Windows with wireless disabled then I can't re-enable it in Linux.  Also, if I press Fn-2 (my keyboard shortcut for disabling wireless) in Ubuntu then my wireless connection gets droppped and I have to return to Windows to switch it back on.

There must be a way around this, of course, but life's too short...

---

### Post by Hidden.Elf on 2005-03-19
jw... should the radiostate be set to 1 or 0??? it says both ways in this thread :? i am using the dell driver on a belkin 54g card

---

### Post by jonny on 2005-03-20
> jw... should the radiostate be set to 1 or 0??? it says both ways in this thread  i am using the dell driver on a belkin 54g card

Hidden.Elf, you're right; one of the replies above is incorrect.  You need to set radiostate to 0 in all of those config files.

---

### Post by Hidden.Elf on 2005-03-20
ok thanks for clarifying that... i didn't try the regular driver with the radiostate... just jumped straight to the dell one.. never did get it to work on the dell... but it worked perfectly on the one from my driver cd :grin: 

also if ```
ifup wlan0
```
doesn't work for you, try```
dhclient wlan0
```this is the only thing that works on mine ](*,)

---

