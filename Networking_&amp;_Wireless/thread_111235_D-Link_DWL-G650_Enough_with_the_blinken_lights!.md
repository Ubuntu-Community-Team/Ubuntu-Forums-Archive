---
title: "D-Link DWL-G650 Enough with the blinken lights!"
date: 2006-01-01
forum: Networking &amp; Wireless
---

### Post by glug101 on 2006-01-01
OK,
   After reading the hardware specifications, I went to the store and purchased a D-Link DWL-G650 wireless Cardbus Networking card for my aging IBM laptop.  However, there are some problems with it.  The lights blink and I am unable to pull an ip address from my 802.11b router.  

Here are the symptoms:

lspci shows teh card with and Atheros AR5212 chipset

iwconfig shows ath0 device, but no ip address. 

ifconfig shows ath0 also, and shows an inet6 address in hex and a /64 subnet mask (is that even a valid subnet?).

At first when I plugged it in, the card showed a single, steady light. (this shows power, I think).  When I activated the card with the network-admin util the two lights blink alternately.  When I set the wireless channel manually, the lights blink in synch.  D-Link is mum as to what this means, preferring to give extensive description of what the lights mean when the card is working properly. (Thanx to D-Link for incomplete documentation :( )

Whew!  I hope somebody out there can give me some good advice cause I'm quickly running out of options in my own mind.

Thanx a bunch!

---

### Post by Lambert on 2006-01-01
Post the output of these commands

sudo iwlist ath0 scan

iwconfig

ifconfig

What kind of network signal are you broadcasting? open or wep or wpa?

---

### Post by glug101 on 2006-01-01
[QUOTE=Lambert]Post the output of these commands

sudo iwlist ath0 scan

iwconfig

ifconfig

What kind of network signal are you broadcasting? open or wep or wpa?[/QUOTE]

Lambert:  Hello old friend;)  Have you recieved a medal for helping folks like me out with wireless network troubles?  I think that every thread that I've seen on the subject has you in it someplace:)

Anywho:

sudo iwlist auto scan:
```
ath0      Failed to read scan data : Resource temporarily unavailable
```

iwconfig:
```
lo        no wireless extensions.

ath0      IEEE 802.11  ESSID:"TheShire"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

ifconfig:
```
ath0      Link encap:Ethernet  HWaddr 00:13:46:18:5F:F3
          inet6 addr: fe80::213:46ff:fe18:5ff3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Memory:c6a20000-c6a30000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7724 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7724 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:454554 (443.9 KiB)  TX bytes:454554 (443.9 KiB)
```

What type of network am I broadcasting?  It's an open network right now.  Just till I get the net working.  I'm really not fond of running an open wireless network and normally I have some pretty tight security on it.  ;)

Thanx in advance!

---

### Post by Lambert on 2006-01-01
Try this

```
sudo -s
``` then enter your password

make sure device is up

```
ifconfig ath0 down
ifconfig ath0 up
``` 
set to protocol 802.11b

```
iwpriv ath0 mode 2
``` 
set network info from command line. fill in blanks.

```
iwconfig ath0 essid ___ channel ___ mode managed commit
``` 
then

```
dhclient ath0
``` 
re run iwconfig and ifconfig. What I want to see is association to router. (where it says Access point: in iwconfig it shouldn't be all 0's) and an ip address (where it says inet addr when running ifconfig)

then to get out of root privledge
```
exit
```

If this doesn't work we'll move on to trying a static ip.

---

### Post by glug101 on 2006-01-02
Greetings,
    Here are the results:
```

root@Legolas:~# iwconfig ath0 essid TheShire channel 11 mode managed commit
Error for wireless request "Commit changes" (8B00) :
    SET failed on device ath0 ; Operation not supported.
root@Legolas:~# iwconfig
lo        no wireless extensions.

sit0      no wireless extensions.

ath0      IEEE 802.11b  ESSID:"TheShire"
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@Legolas:~# ifconfig
ath0      Link encap:Ethernet  HWaddr 00:13:46:18:5F:F3
          inet6 addr: fe80::213:46ff:fe18:5ff3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Memory:c6a20000-c6a30000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:201714 errors:0 dropped:0 overruns:0 frame:0
          TX packets:201714 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:18152434 (17.3 MiB)  TX bytes:18152434 (17.3 MiB)

```

No network conection yet:(  I also tried setting the ip address manually through the network-admin util, but this is still a no-go:(

---

### Post by glug101 on 2006-01-02
Ok, did some more research....

My card is version b5.  'What?' you say,'There is no version b5 listed on D-Link's website.'  Well, you would be quite correct.  D-Link doesn't seem to think it exists.  Fortunately, the madwifi site knows better.  On the off hunch that the compiled drivers that came with Ubuntu are crap, I'm trying to compile them for myself....

Got as far as ```
./configure
``` and I have allready hit a show stopping snag.  I'm getting a message telling me 'no acceptable C compiler found in $PATH'  And, I've exhausted the supply of gcc compilers on the install cd...

Started to swear softly at this card that is marked as working 'out of the box'.

**bump**

---

### Post by glug101 on 2006-01-02
Oh, right, I should ask a question:)  Any pointers on how to compile these from scratch?

---

### Post by Lambert on 2006-01-02
This first link is a howto with the madwifi-old driver.

[http://www.ubuntuforums.org/showthread.php?t=75451&highlight=madwifi](http://www.ubuntuforums.org/showthread.php?t=75451&highlight=madwifi)

This next link is a howto for the madwifi-ng driver.

[http://www.ubuntuforums.org/showthread.php?t=105437&highlight=madwifi](http://www.ubuntuforums.org/showthread.php?t=105437&highlight=madwifi)

Breezy comes with madwifi-old but the first link will update it with a few bug fixes.

Depending what the madwifi site says and if this is really new you may want to consider the madwifi-ng howto.

---

### Post by glug101 on 2006-01-02
Sadly, both of those solutions rely on installing sharutils.  My box is balking on compiling this with compiler errors.  As a former gentoo user, I'm not used to items not compiling because of missing dependencies.  (Everything else, but not missing dependancies ;) )  Ah well, thanx for the help so far.  This is getting far enough away from what I started with.  I'm going to start looking at more extreme changes to get it working and start a new thread if those don't work.

Take it easy and keep helping guys with annoying network problems like mine ;)

Cheers!

---

### Post by Rob2687 on 2006-01-02
What if you try **ifconfig ath0 up** after doing
iwconfig ath0 essid ___ channel ___ mode managed commit
then do dhclient ath0

My atheros card won't try to associate unless I do that after setting the essid and stuff.

---

### Post by glug101 on 2006-01-03
[QUOTE=Rob2687]What if you try **ifconfig ath0 up** after doing
iwconfig ath0 essid ___ channel ___ mode managed commit
then do dhclient ath0

My atheros card won't try to associate unless I do that after setting the essid and stuff.[/QUOTE]
Thanx for the help Rob2687:)  Unfortunately, if you read my ealier posts, you'll see that I recieve an error message at the iwconfig command that sets the channel and essid:(  

I think that right now I'm going to try installing gentoo with their GRP install (all binary).  I'm hoping that this will give me the tools I need to compile the latest madwifi drivers (since compiling most things on that distro are trivial).  I'm hoping that I'll be able to diagnose the problem with Ubuntu's drivers this way and use the compiled kernel to fix Ubuntu.  

I would prefer Ubuntu on this box because it's a PII 233 and a distro that compiles everything from source would be a pain.  Wish me luck, and thanx for the continued support;)

---

### Post by jafenske on 2006-01-03
I've got the same d-link card...  Have you tried going from IPv6 to IPv4.  THis made a difference for me.

---

### Post by Rob2687 on 2006-01-03
Try without the 'commit' command.
So just 
iwconfig ath0 essid TheShire channel 11 mode Managed

---

### Post by glug101 on 2006-01-03
[QUOTE=jafenske]I've got the same d-link card...  Have you tried going from IPv6 to IPv4.  THis made a difference for me.[/QUOTE]

Sadly, the iwconfig command didn't help. :(  However, I have a question about how to switch to IPv4?  I think this might be the case, but I'm not sure how to do this.

Thanx :)

---

### Post by gangalee on 2006-01-03
I had some problems connecting to my AP at first w/ my DWL-650+ but it works fine now. You might want to try being close to the AP, even better if you can see the dhcp logs on the AP.

---

### Post by jafenske on 2006-01-03
Here is a link that describes the process

[http://www.ubuntuforums.org/showthread.php?t=87798&highlight=disabling+IPv6](http://www.ubuntuforums.org/showthread.php?t=87798&highlight=disabling+IPv6)

Good luck

---

### Post by glug101 on 2006-01-04
Gangalee:  From where the computer is sitting I can reach over and touch the antenna. (close enough? :) )  The logs on the router show zilch.  The router is not seeing the card and the card is not seeing the router.  The activity light on the router doesn't even blink when the card gets power or tries to connect.  

Jafenski:  I tried the ipv4 trick, but it didn't work.  From reading about it, ipv6 shouldn't cause a problem with connection, just a performance downgrade when the program you are using tries to access ipv6 first. 

I'm going to go ahead with the gentoo install.  I think it's a driver issue and I would like to try fixing it in a distro that I feel more in control with.

Thanx for the help:)

---

