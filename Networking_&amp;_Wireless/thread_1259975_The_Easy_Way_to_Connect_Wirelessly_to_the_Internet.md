---
title: "The Easy Way to Connect Wirelessly to the Internet -- Use the Command Line
(CLI)!"
date: 2009-09-07
forum: Networking &amp; Wireless
---

### Post by RHorse on 2009-09-07
The Easy Way to Connect Wirelessly to the Internet -- Use the Command Line
(CLI)! 
by Rockinghorse Winner

I hear a lot of chatter on the internet -- on irc, forums, newsnet --
everywhere! -- about problems people are having connecting wirelessly to the
internet.

I guess I was just lucky, cuz, though I've had my problems with wireless,
they were usually pretty easily resolved. That's not to say it didn't cost a
couple of tenners and a weekend to get resolved, but that the solution was
fairly straight forward, once you determined what it was.

I don't like to remain with one problem for too long. So if 20.00 for a new
card is going to save me a weekend away from my girlfriend, I'm more
inclined to bite the bullet rather than wrack my brains cuz I'm too cheap to
buy a new card, fer cryin' out loud.

I have seen, and I'm sure you've seen, people on the internet who will spend
4 bloody weekends getting their card to work with ndiswrapper, when for 15
bucks and some fresh air, they could have walked down to the store and
gotten one that worked out of the box. But that's human nature, and who am I
to judge -- but it sounds crazy to me.

So my prefatory remarks include this admonition: if these commands don't
work for you, don't sweat it! Get a card that works ootb (there are many -
google it), and save yourself some aggravation. Unless of course you like
living in a cave by the light of your computer screen 24/7!

Getting a wireless card to connect to the internet is not really that hard.
Once you know what the commands are you have to type, you just make a little
script and put it in your path. So for instance, I have a little script
called connect that I call from my home directory, by typing ~/connect.

The first thing to do when getting a card to work with your system is
determine what device the card is associated with -- usually ath0, ath1,
eth0, eth1, or wlan0. I've never had one that wasn't one of these five
(well, mebbe one time it was eth2 or something, but, never mind, you get the
idea). The way to determine this is to type ifconfig and/or iwconfig at the
command line. This is what I get when I type iwconfig on my machine


~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Ghosteye4"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:22:A4:45:AB:89   
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=46/94  Signal level=-48 dBm  Noise level=-94 dBm
          Rx invalid nwid:2340317  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
          
You can see this device is associated with the hardware layer, ath0. Now if
I type ifconfig, I get the following:

:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:13:46:17:FF:70  
          inet addr:192.168.1.162  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:216435 errors:0 dropped:0 overruns:0 frame:0
          TX packets:154714 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:139470090 (133.0 MiB)  TX bytes:29403946 (28.0 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11227 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11227 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1951489 (1.8 MiB)  TX bytes:1951489 (1.8 MiB)

wifi0     Link encap:UNSPEC  HWaddr 
00-13-46-17-FF-70-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3464475 errors:0 dropped:0 overruns:0 frame:1843877
          TX packets:162785 errors:46 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:498704767 (475.6 MiB)  TX bytes:34433124 (32.8 MiB)
          Interrupt:11 

As you can see, ath0 again. 

If you don't see any devices or only the lo ones, don't despair. I
will come back to you unlucky fellows (and gals) later. For now lets assume
that your device is listed as ath0. That, my friends, is valuable
information. You can use this information to get your wireless going.




The WEP Way


iwconfig, the command used to get the wireless device name, is also the
command used to connect to the device, when the wireless router is *open* or
WEP encrypted. For WPA encryption, stay tuned.


OK, now to connect to an *open* (unencrypted router) like the one your dopey
neighbor broadcasts to the world, or a WEP encrypted router, you would take
the following steps:

1. Determine which of the wireless routers in range of your card you want to
connect to.

Type iwlist ath0 scanning|less. This is assuming ath0 is the device. You may
have to use ath1, eth0, etc, depending on what you found out in the step
above. If you have a scrolling terminal you don't have to use |less. This
will run down all the channels that are emitting a signal within range of
your wireless card, along with some information about them.

2. Choose which router you want to connect to. The ESSID is the *name* of
that router. If the name is listed as "", that means the ESSID is *hidden*
and you'll have to already *know* what the essid is before you can connect
to it.

Here is the first part of what iwlist ath0 scanning produces on my terminal

~$ iwlist ath0 scanning
ath0      Scan completed :
          Cell 01 - Address: 00:22:A4:45:AB:89
                    ESSID:" "
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/94  Signal level=-47 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:22:A4:45:AB:89
                    ESSID:""
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/94  Signal level=-47 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:13:46:F1:7B:C0
                    ESSID:"crown"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/94  Signal level=-47 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:ath_ie=dd0900037f010100100000
         
          Cell 05 - Address: 00:1A:C4:DE:F4:81
                    ESSID:"2WIRE796"
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Quality=13/94  Signal level=-82 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101020003a4000027a4000042435e0062322f00
                    
As you can see, cells 1, 2, 3, and 5 appear to be WEP encryption. Although
it doesn't say WEP encryption, it says Encryption key:on and since it
doesn't say something about WPA, we may assume it is WEP (the weaker
encryption standard). As you can see Cells 1 and 2 are *hidden.* The essid's
are not broadcast so we can't use them to connect unless we know the essid.
But the third Cell has an essid of "crown." The fourth is wpa encrypted and
the 5th is WEP encrypted.
                    
3. Use iwconfig to configure your card to the router. Type sudo iwconfig
ath0 essid crown key 1234567890 mode managed

The essid will be whatever it is, and the key will be the wep encryption
key. If there is no encryption, then just leave out the key argument.

4. Use dhclient to connect.
.
The command is sudo dhclient ath0.

Give it a chance. It could take 10 or 20 seconds. Don't start twittering -
wait for it to complete it's connection. It'll usually stop *talking* back
and return to a prompt. Then you know it's done all it could and it either
connected successfully or could not connect at all. Test the connection by
pinging my good friends at sonic.net. They're lonely and appreciate the
attention:

ping sonic.net

If you see scrolling text that looks like this:

PING sonic.net (209.204.190.64) 56(84) bytes of data.
64 bytes from [www.sonic.net](www.sonic.net) (209.204.190.64): icmp_seq=1 ttl=242 time=31.4 ms

congratulations, you've connected to the internet! If you haven't, that's
just too bad, now, isn't it? Go back and try it all again, google your
brains out until you figure it out yourself, then send me an email and tell
me how you did it! I'll incorporate your advice in this web page.



The WPA Way


So now onto WPA encryption. For this we need to take the first step of using
iwconfig and ifconfig to determine the wireless device (see above). Then we
use iwlist [device] scanning to find a WPA channel we want to connect to
(get the essid). Then we change course a bit and do the following:

Install wpa_supplicant into your distro with the package manager of your
choice. I just typed sudo apt-get install wpa_supplicant. It's a tiny
program (but oh, so useful!).

wpa_supplicant comes with wpa_passphrase. Here's an Ubuntu guide to get you
started. [http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136) To rephrase what
that article says, you simply type sudo wpa_passphrase essid
psk_passphrase. The essid is the essid of the router as discussed above,
and the psk_passphrase is just the passphrase. This will generate a bunch of
letters and numbers on the terminal screen and will also write a file called
wpa_supplicant.conf to /etc/wpa_supplicant. Here is a copy of my
wpa_supplicant.conf

network={
	ssid="production"
#scan_ssid=1
	proto=WPA
	key_mgmt=WPA-PSK
	psk=453b5f22de0d07c48e814b604a4a3f2c67a66f76249f66ba55a6f5921d8c77c1
}

This works for me on my system. But reading the man pages for
wpa_supplicant.conf, wpa_supplicant and wpa_passphrase is not a bad idea.
They're very informative and *relatively* easy to digest.

By default, wpa_supplicant looks for wpa_supplicant.conf in
/etc/wpa_supplicant, but you can move it to anyplace you want and use -c
argument to specify the location when you start wpa_supplicant.


I start it by typing

sudo wpa_supplicant -Dmadwifi -c/home/me/wpa_supplicant.conf -iath0

The list of drivers available for the -D switch is in the man page. I have
found madwifi or wext to work with my machines. Typed in this fashion, all
errors and feedback will print to screen, so you can see what's happening.
Once you find the command switches that work for you, you can include the -B
switch which makes it a daemon, and forks it to the background.

sudo wpa_supplicant -Dmadwifi -c/home/me/wpa_supplicant.conf -iath0 -B

One more step is necessary, the same as we took with the WEP router: type
sudo dhclient ath0.





One more note about not seeing any wireless extensions when you type
iwconfig or ifconfig. Sometimes rebooting the router and then shutting off
and turning on the puter can shake things up. Sometimes just guessing at the
wireless extension and typing the iwconfig or wpa_supplicant commands will
work and bring the extension alive. I have seen this. Then you type dhclient
as noted above, and you're in business.


sorry about the smilies - it's the way the forums interpret certain characters.


RHorse
[email]rockinghorse@phreaker.net[/email] (Subject: Wireless)

---

### Post by j7%&lt;RmUg on 2009-09-07
Interesting, Iv never had a problem with my wireless, all iv ever had to do on ubuntu is select my network and enter my WPA key, EASY!

---

### Post by RHorse on 2009-09-11
That's assuming you could start X and have access to the Network Manager. For someone who mangled their X configuration it could mean the difference between being able to download and configure applications, browse the web and get help online, and being stranded at a command prompt.

---

