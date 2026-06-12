---
title: "Wireless and packaging troubles"
date: 2006-05-23
forum: Networking &amp; Wireless
---

### Post by EGR on 2006-05-23
ok, here's my situation. I just installed Ubuntu on my laptop and, 
as seems to be common enough, can't connect using my wireless card (Intel Pro 2200). This is the only way it has of connecting, so this means it is offline until I fix the problem.

Now, doing some browing using another computer I found the following
HowTO: ([http://www.ubuntuforums.org/showthread.php?t=26623)](http://www.ubuntuforums.org/showthread.php?t=26623)). 

One person who commented claimed that the problem could be solved 
without installing any new stuff, so I tried that solution first. 
First, I configured the wireless card to connect to my network, and entered
my WEP key. My wireless network (and a bunch beside) gets detected, so
the problem isn't there. 
Where it fails is when comes time to get the IP address. Here's my
terminal transcript:
___
eg@Eg:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 32381
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:0e:35:94:da:bd
Sending on   LPF/eth1/00:0e:35:94:da:bd
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
___

In any case, I decided to try the actual HowTo with firmware download and all. 
I got the files from the other computer and transferred them to the laptop
with USB Stick. Everything seems to be going alright, until the last step, 
where I need to command `make' and `make install'. These are not recognised
as commands. I figured this was because I was lacking packages. Since I can't
get online, though, I can't get them to work. I also tried `sudo apt-get install ndiswrapper' with the install CD in the drive, but same result, this is what I get:

eg@Eg:~$ sudo apt-get install ndiswrapper
Reading package lists... 
Done
Building dependency tree... Done
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http:// [...]
W: You may want to run apt-get update to correct these problems
E: Couldn't find package ndiswrapper
___

[The `couldn't start packagage list (etc) is the same message I get upon opening
Synaptic]

I really don't know what to do. I am a total newbie, and I wouldn't even know
what files exactly to go get from the Ubuntu site to get them manually.

Anybody could help? Thanks already!
EGR

---

### Post by ingo on 2006-05-23
Hi there,

if Ubuntu recognises your card you're home and dry. All you have to do is:

1. type
sudo ifdown sit0
3. type
sudo iwconfig sit0 essid "NETWORK NAME" key s:YOUR WEP KEY PHRASE
4. type
sudo ifup sit0

Right, that should do it.

And in case you're fed up with sudo type

sudo bash

at the start and then you've got a root shell.

Finally, it might be a good idea to write a simple script for this, as you'll probably get fed up typing all that lot every time you want to get into your network. Here is how:

get into the root shell (see above) and change into /usr/local/bin. Type

touch mynetwork (or the name of your network or a nice short name you remember easily)

Now open the file /usr/local/bin/mynetwork with your favourite editor (I use vi, but nano is very user friendly...) and type the following:

#!/bin/bash
#my network

ifdown sit0
iwconfig sit0 essid "YOUR NETWORK NAME" key s:YOUR WEP KEY PHRASE
ifup sit0

#end

Save it and Bob's your uncle. Now every time you want to log into your network just type

sudo sh mynetwork

and you're in.

You might want to do write other scripts for other networks. If in doubt check the man pages for iwconfig (man iwconfig)

HTH

Ingo

---

### Post by EGR on 2006-05-23
Ingo, 

Thanks a lot for your reply. Unfortunately, things don't seem to be working out. 
trying to configure `sit0' gets me a `no wireless extension' message. 
My wireless card is `eth1', so I take it that is what you meant. 
I tried your `key s" ' command in many variations, but got errors 
every time: 
```

root@eg:~# iwconfig eth1 essid "Percy" key s: xxxxxxxxxx
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "s:".
root@eg:~# iwconfig eth1 essid "Percy" key: xxxxxxxxxx
Error : unrecognised wireless request "key:"
root@eg:~# iwconfig eth1 essid "Percy"
root@eg:~# key s: xxxxxxxxxx
bash: eg:: command not found
root@eg:~# iwconfig eth1 key s: xxxxxxxxxx
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "s:".
root@eg:~# iwconfig eth1 key: xxxxxxxxxx
Error : unrecognised wireless request "key:"
root@eg:~# iwconfig eth1 key s xxxxxxxxxx
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "s".

```

The only one that didn't get me such an error was: 
# iwconfig eth1 key xxxxxxxxxx

So, I tried the entire procedure with it, the results below: 

```

eg@eg:~$ sudo bash
Password:
root@eg:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"Percy"
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:09FF-AE6C-A0   Security mode:open
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4   Missed beacon:0

sit0      no wireless extensions.

root@eg:~# ifdown eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 9554
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:0e:35:94:da:bd
Sending on   LPF/eth1/00:0e:35:94:da:bd
Sending on   Socket/fallback

root@eg:~# iwconfig eth1 essid "Percy"
root@eg:~# iwconfig eth1 key xxxxxxxxxx
root@eg:~# ifup eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:0e:35:94:da:bd
Sending on   LPF/eth1/00:0e:35:94:da:bd
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

I also tried with the key in format xxxx-xxxx-xx, and the result was the same. 
Finally, I disabled my WEP key entirely, and made my network open access. 
Even that didn't work: I can detect the network, but I can't get an IP 
from it, as usual. 

Is there anything I am doing wrong? 

In the end, would it do me any good to try and install the firmware and patched for my card? If so, would you happen to know of a quick and efficient way for me to get the `make' and `make install' commands to work? 

Thanks a lot, it's really appreciated.
Eric

---

### Post by ingo on 2006-05-24
Hi Eric,

yes, eth1 it should be, quite right:)

The problem with the "key:" command bit of iwconfig is that there shouldn't be any space after : For further information type

man iwconfig

You can use the man bit in front of any command to display the manual pages. They are a bit cryptic at the best of times to a newbie (incl. me), but the iwconfig is quite understandable;)

Below is the output of my iwconfig. The differences appear to be a) my card gets recognised, but only after I installed the firmware and b) the length of the encryption key (apart from the fact that you are not online:(

root@ibm:~# iwconfig
lo        no wireless extensions.

irda0     no wireless extensions.

ra0       RT2500 Wireless  ESSID:"uslot"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:15:0C:28:15:37
          Bit Rate:54 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xx   Security mode:open
          Link Quality=83/100  Signal level=-61 dBm  Noise level:-205 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


So go with the firmware. In order to get make and make install going you need to install "make". Get it from [http://packages.ubuntu.com/breezy/devel/make]("http://packages.ubuntu.com/breezy/devel/make") and put it on the old stick...
 
 Let us know how you get on!
 
 Ingo
PS.: sorry about all the smilies where there shouldn't be any but I'm not sure how to turn them off...

---

### Post by EGR on 2006-05-24
Hi Ingo,

Well, I'm back online! 
I realised that I had made a stupid mistake last I tried to connect with WEP off (I failed to apply changes from my router settings, dummy me...). So I tried again this morning, and it worked. Then, I turned back access control and the WEP encryption, but this time using OpenKey rather than SharedKey, and voila: I connected no problem. The connection seems to be up to speed (`100% Signal Strength').

I do have a small question still, though. How can I verify that my connection is indeed secured? I do know I lost connection after turning the encryption back on from the router, and only regained it after writing it the key from the laptop. But when I do `iwconfig' I don't get any `Encryption Key ......' line as I used to. It looks like this:
```

eth1      IEEE 802.11b  ESSID:"Percy"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:09:5B:6E:A3:14
          Bit Rate=11 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=95/100  Signal level=-31 dBm  Noise level=-82 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:17  Invalid misc:0   Missed beacon:0


```

Is this normal, given that I am using OpenKey, or something else amiss?

In any case, thank you very much again; I'm very happy to see things work!
Eric

---

### Post by ingo on 2006-05-24
brilliant, glad you made it:)

my encryption is in open mode and it shows - not sure why your's is like that...

But tell me, how do you get this nice little box around your shell readout??? I've got to know :-k

---

