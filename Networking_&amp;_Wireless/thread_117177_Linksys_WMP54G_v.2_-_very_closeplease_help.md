---
title: "Linksys WMP54G v.2 - very close/please help"
date: 2006-01-14
forum: Networking &amp; Wireless
---

### Post by boomerian on 2006-01-14
I have tried raising this on the Beginners' forum, but I need some help from the "heavy-hitters," please.
I think I'm close here, but...
After a successful install and much reading of these various forums, I am stuck without successful internet access via Linksys WMP54G v.2 wireless adapter with Broadcomm chipset. Can someone look at the following and assist?

ian@ubu:~$ sudo modprobe ndiswrapper
ian@ubu:~$ sudo iwlist wlan0 scan
wlan0 Scan completed :
Cell 01 - Address: 00:13:46:16:12:30
ESSID:"default"
Protocol:IEEE 802.11b
Mode:Managed
Frequency:2.437 GHz (Channel 6)
Quality:0/100 Signal level:-36 dBm Noise level:-256 dBm
Encryption keyn
Bit Rate:1 Mb/s
Bit Rate:2 Mb/s
Bit Rate:5.5 Mb/s
Bit Rate:11 Mb/s
Bit Rate:6 Mb/s
Bit Rate:12 Mb/s
Bit Rate:24 Mb/s
Bit Rate:36 Mb/s
Bit Rate:9 Mb/s
Bit Rate:18 Mb/s
Bit Rate:48 Mb/s
Bit Rate:54 Mb/s
Extra:bcn_int=100
Extra:atim=0
Cell 02 - Address: 00:14:6C:13:6C:40
ESSID:"NETGEAR"
Protocol:IEEE 802.11b
Mode:Managed
Frequency:2.462 GHz (Channel 11)
Quality:0/100 Signal level:-78 dBm Noise level:-256 dBm
Encryption keyff
Bit Rate:1 Mb/s
Bit Rate:2 Mb/s
Bit Rate:5.5 Mb/s
Bit Rate:11 Mb/s
Bit Rate:18 Mb/s
Bit Rate:24 Mb/s
Bit Rate:36 Mb/s
Bit Rate:54 Mb/s
Bit Rate:6 Mb/s
Bit Rate:9 Mb/s
Bit Rate:12 Mb/s
Bit Rate:48 Mb/s
Extra:bcn_int=100
Extra:atim=0
Cell 03 - Address: 00:11:24:08:0A:31
ESSID:"harry's network"
Protocol:IEEE 802.11b
Mode:Managed
Frequency:2.412 GHz (Channel 1)
Quality:0/100 Signal level:-78 dBm Noise level:-256 dBm
Encryption keyff
Bit Rate:1 Mb/s
Bit Rate:2 Mb/s
Bit Rate:5.5 Mb/s
Bit Rate:11 Mb/s
Bit Rate:6 Mb/s
Bit Rate:9 Mb/s
Bit Rate:12 Mb/s
Bit Rate:18 Mb/s
Bit Rate:24 Mb/s
Bit Rate:36 Mb/s
Bit Rate:48 Mb/s
Bit Rate:54 Mb/s
Extra:bcn_int=100
Extra:atim=0

ian@ubu:~$ sudo ifup wlan0
ifup: interface wlan0 already configured
ian@ubu:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5 driver present, hardware present
ian@ubu:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wlan0 IEEE 802.11g ESSIDff/any
Mode:Managed Frequency:2.462 GHz Access Point: 00:00:00:00:00:00
Bit Rate:54 Mb/s Tx-Power:16 dBm
RTS thr:2347 B Fragment thr:2346 B
Power Managementff
Link Quality:100/100 Signal level:-10 dBm Noise level:-256 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:145215 Missed beacon:0

sit0 no wireless extensions.

ian@ubu:~$ ifconfig
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:751102 errors:0 dropped:0 overruns:0 frame:0
TX packets:751102 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:61640644 (58.7 MiB) TX bytes:61640644 (58.7 MiB)

wlan0 Link encap:Ethernet HWaddr 00:0F:66:6E:51:7C
inet6 addr: fe80::20f:66ff:fe6e:517c/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Memory:febfc000-febfdfff

ian@ubu:~$


I want to continue learning bash commands in Terminal, and to this point have been using a combination of Synaptic and Terminal.
Working with an old machine, on which I want to learn...
Assistance is greatly appreciated!

---

### Post by Lambert on 2006-01-14
Depending on which signal you want to connect to use this command

```
sudo iwconfig wlan0 essid ___ channel __ ap __:__:__:__:__:__ key ____
```

Read the man page for iwconfig for different options such as entering key as you may need to give more information such as restricted or if ascii key use s: in front of the key.

scan results can be wrong on the protocol field but both show using 802.11b and iwconfig shows your card is using 802.11g protocol. If the scan is correct you might need to change your card with this command. (it's supposed to be auto but sometimes it doesn't automatically change)

```
sudo iwpriv wlan0 network_type b
```

then run iwconfig again, you should see the essid and ap mac address in the output. If you're associated then run this command

```
sudo dhclient wlan
```

Now see if you're connected.

---

### Post by boomerian on 2006-01-14
*Tried this:*

```
sudo iwconfig wlan0 essid ___ channel __ ap __:__:__:__:__:__ key ____
```
[I]
Returned[/I] ian@ubu:/$  *which is a good thing, right?*

Read the man page for iwconfig for different options such as entering key as you may need to give more information such as restricted or if ascii key use s: in front of the key.

scan results can be wrong on the protocol field but both show using 802.11b and iwconfig shows your card is using 802.11g protocol. If the scan is correct you might need to change your card with this command. (it's supposed to be auto but sometimes it doesn't automatically change)

*When I tried this:*
```
sudo iwpriv wlan0 network_type b
```

*I got this response:*
Interface doesn't accept private ioctl...
network type (8BF2): Invalid argument

then run iwconfig again, you should see the essid and ap mac address in the output. If you're associated then run this command

```
sudo dhclient wlan
```

Now see if you're connected.[/QUOTE]
*Still not connected...alas*

---

### Post by boomerian on 2006-01-15
*bump*  Someone please help?

---

### Post by boomerian on 2006-01-15
*bump* again-sorry, but I'm stuck here.
Is there additional information I should provide?
Can someone please walk me through this?

---

### Post by boomerian on 2006-01-16
*Another bump*  Can someone read through this and help me?
It' s a helpless feeling, and I've read about every thread that describes wireless problems...

---

### Post by jago25_98 on 2006-01-16
Useful info. Will try for my situation. *bump!*

---

### Post by jago25_98 on 2006-01-16
I got it for me. The key was `restricted after "key and before the actual key` Maybe it will work for you:

```

iwconfig ra0 key restricted 16-digitWEPKeyAKA128BIT essid MYESSID rate auto mode managed nick HOSTNAME

```

---

### Post by boomerian on 2006-01-16
Thanks so much, jago25_98, for responding.

I tried the terminal entry you provided and received this:

Error : unrecognised wireless request 'WEPKey042377face'

Any other suggestions? Help is greatly appreciated...

---

### Post by boomerian on 2006-01-17
*Bump for Lambert et al (who might be able to help).
I'm at work right now, so won't be able to make further attempts until tonight (10-12 hours from now). Thanks in advance,

---

### Post by Lambert on 2006-01-17
I've been watching but don't know if I can offer anything.

Your router is not letting you associate with it.

You should be able to run this command and associate with the router. And I'm picking the second router in the scan.

```
sudo iwconfig wlan0 essid NETGEAR ap 00:14:6C:13:6C:40 freq 2.462
```

If it's another router then you just need to put in correct data and if encrypted add the key information. But as you said previously, you tried this and nothing happened.

Now I notice if you're using Harry's network then the problem might be the space in the essid as that sometimes causes problems.

So here is what I can say currently. pick the router you want to connect to and try the command again, then run just

```
iwconfig 
``` 
and post the output here.

If it's the router with encryption then post back here the detail about the encryption and I'll try to give the exact command syntax to enter.

hex or ascii key?
shared or restricted?

1st step that needs to be taken is router association. 

1. It is possible a router reboot might help but it has been known to completely reset all settings which could cause a temporary problem for other pcs that are connected.
2. If you have encryption on then we need to turn it off just to test connection.

---

### Post by boomerian on 2006-01-17
Thanks, Lambert.
I did not recognize the NETGEAR and Harry's network, which must be local in the neighborhood. (I'm pretty sure mine was the "default" - it is a D-Link router). I think it is wise to back up a bit and walk through (as you are asking me to do). Does it make sense to disable the WEP, at least until I/we can get it (successful wireless access) working?
Question: In order to more easily 'cut and paste' the terminal responses, should I plug in the cable from the router (eth0) which I had de-activated and unconfigured so as not to 'confuse' the situation?
My wife is getting tired of my having the old machine, books, etc. cluttering up our small extra bedroom/study with my old dog (so I can stay connected via the newer XP machine). Once I get the wireless access, I will be 'deported' to the quiet workspace of the basement! 
Cheers,

---

### Post by Lambert on 2006-01-17
If you can turn off encryption I would highly suggest that. This just helps simplify troubleshooting and rules out any hardware or other problem that's happening. If you can connect here then it's just configuring and set up encryption properly so router let's you associate.

so with encryption off you should be able to run this command and associate.

sudo iwconfig wlan0 essid default ap  00:13:46:16:12:30 freq 2.437

run just sudo iwconfig now and notice second line where it says ap: should have the mac address of your router.

If you are associated then run the sudo dhclient wlan0 command to see if you get an ip address. This is checked with the ifconfig command. Second line should say inet addr xxx.xxx.x.x

---

### Post by boomerian on 2006-01-17
If I didn't need the $$ I'd rush home now to try what you've suggested, Lambert - thanks again.
I am keen on getting this hooked up and really getting into the nuts and bolts of Ubuntu!:) :cool:

---

### Post by boomerian on 2006-01-18
So here is the latest...following your direction, Lambert

(Lambert)So here is what I can say currently. pick the router you want to connect to and try the command again, 

*Response was:*

Error : unrecognised wireless request "2.462" 

(Lambert)then run just

Code:
iwconfig 
and post the output here.

*Response was:*

l0       no wireless extensions

eth0   no wireless extensions

wlan0 IEEE 802.11g ESSID:off/any
         Mode:Managed Frequency:2.462 Access Point:00:00:00:00:00:00
         Bit Rate:54 Mb/s Tx-Power:14 dBm
         RTS thr:2347 B Fragment thr:2345 B
         Encryption key:0423-77FA-CE Security mode:restricted
         Power management:off
         Link Quality 100/100 Signal level:10 dBm Noise level:256 dBm
         Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
         Tx excessive retries:0 Invalid misc:601699 Missed beacon:0

*Note: this has been transcribed, since I don't have internet access yet (obviously), so I've had to write it down and use another box to record it. The formatting does not come through, as you may recognize the indentation is missing for the response from the iwconfig entry...*

I'm again at work, so won't be able to try again until late this evening, if then.
I'm not giving up until I/we get this figured out! I've got to believe we're close
Cheers,

---

### Post by Lambert on 2006-01-18
```
 sudo iwconfig wlan0 essid default ap  00:13:46:16:12:30 freq 2.437
```

this should be the correct command to connect to the first router in the scan w/ encryption off.

If you get the invalid 2.437 error, try it with out the [I]freq 2.437
[/I]
```
sudo iwconfig wlan0 essid default ap 00:13:46:16:12:30
```

also make sure the interface is up

```
sudo ifconfig wlan0 up
```

---

### Post by boomerian on 2006-01-19
Lambert, my friend,
The error was returned on the first command (i.e., with <freq 2.437>).

The second two commands were accepted (i.e., no error, cursor returned), but still no internet access.

What now? Thanks for your patience...

---

### Post by Lambert on 2006-01-19
My last couple posts won't have you with internet access. We're just trying to get association with the router.

So if you run iwconfig now do you get a line saying ap: ab:cd:ef:hj

instead of 00:00:00:

---

### Post by boomerian on 2006-01-20
Nope. All zeros

wlan0     IEEE 802.11g  ESSID:off/any
            Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00

etc.,

---

### Post by boomerian on 2006-01-20
Off to bed now...will check early a.m.
Thanks, amigo.

---

### Post by Lambert on 2006-01-20
I have to say I'm at a loss. Your router just won't let you associate with it.

1. check your firmware on the router and see if there is a newer version and update it.
2. follow these steps to test your tcp/ip stack on the pc

```
ifconfig wlan0 192.168.0.10 up
```
```
ping -C 4 127.0.0.1
```
```
ping -C 4 192.168.0.10
```

Results?

---

### Post by boomerian on 2006-01-20
Here's what happened:
Code:
ifconfig wlan0 192.168.0.10 up

*Response:*
SIOCSIFADDR:  Permission denied
SIOCSIFFLAGS:  Permission denied
SIOCSIFFLAGS:  Permission denied

Code:
ping -C 4 127.0.0.1

*Response:*

ping: invalid option  - C
Usage:  ping (etc., description of available ping arguments)

Code:
ping -C 4 192.168.0.10

*Response:* (same as for above)

I should mention that the router is "controlled" or governed for settings, by a PC running XP. The router itself is a D-Link model DI-524 AirPlus G High Speed 2.4GHz (802.11g) wireless router. I bought it at CompUSA, whereas the adapter in my old eMachine was purchased at Wal-Mart, and (since it is a version 2 model, is most likely older hardware/technology).  You had pointed out earlier that it might be looking for 802.11b, but as far as I could tell the DI-524 should be able to handle that, (according to what I've read).

Should I concede to hardware limitations, and try the Linuxant DriverLoader? (Would that be considered "giving up?")
Cheers,

---

### Post by Lambert on 2006-01-20
Sorry, was answering on different box so I didn't verify what I was giving and was also answering in sort of a rush this morning.

Add sudo infront of the ifconfig command as root priv is needed.

for the ping commands change it from -C to -c.

so it would be 

ping -c 4 127.0.0.1

Giving up would be walking away, trying linuxant would just be plan B in my opinion. I would agree with anything right now just to get you working.

I wish I was in your area, I'd take the time to come sit down at the pc to help you out.

Do you use IM at all?

---

### Post by boomerian on 2006-01-20
Thanks, Lambert.
I don't really use IM, although my son set up GAIM on the machine he build for my wife and me. He's running Gentoo, exclusively, and works on campus with the university computer systems, so he's learning a great deal. He reluctantly installed Win XP on the new machine, more for his mother's convenience than anything else.
I wondered (as I rushed out the door this a.m.) if I should have added the "sudo" prefix to those entries, but I literally had less than 5 minutes to check this forum and make the tries. I scribble down the responses and posted my reply when I got into the office. Its a bit of a juggling act, to be sure, but I'm game to see it through as long as you remain patient with me.
I found this link 
[http://www.neowin.net/forum/index.php?showtopic=292721](http://www.neowin.net/forum/index.php?showtopic=292721) 
which seems helpful, but I'd rather stay tuned to the Ubuntu if you're willing to guide me through.
Cheers,

---

### Post by boomerian on 2006-01-20
Ah, Lambert - I checked the D-Link website and there do appear to be firmware updates for the router. I've marked the URL, and must determine the "revision" (A,C,D, or E) when I get back home, then download/update as required...then I can try all this again.
Mucho complicated, no?

---

### Post by Lambert on 2006-01-20
hmm, you said di-524

see this post

[http://ubuntuforums.org/showthread.php?t=119260](http://ubuntuforums.org/showthread.php?t=119260)

updating firmware isn't difficult, just follow instructions provided by manufacture and pay attention to any warnings they give.

---

### Post by Lambert on 2006-01-23
Hmmm..... where do we go from here. I need to go back and read the entire thread.....


In the mean time here are some more thoughts.

Let's reset the device.

```
sudo iwconfig wlan0 ndis_reset
```

then try to associate again 

```
sudo iwconfig wlan0 mode managed
sudo iwconfig wlan0 essid default
```

Post back the output of this command

```
sudo modinfo ndiswrapper
```

You did turn encryption off yes?

---

### Post by boomerian on 2006-01-23
Here's what happened, amigo...
[I]
Let's reset the device.

```
sudo iwconfig wlan0 ndis_reset
```[/I]
ian@ubu:~$ sudo iwconfig wlan0 ndis_reset
Password:
Error : unrecognised wireless request "ndis_reset"

[I]then try to associate again 

```
sudo iwconfig wlan0 mode managed
sudo iwconfig wlan0 essid default
```

Post back the output of this command

```
sudo modinfo ndiswrapper
```[/I]
ian@ubu:~$ sudo iwconfig wlan0 mode managed
ian@ubu:~$ sudo iwconfig wlan0 essid default
ian@ubu:~$ sudo modinfo ndiswrapper
filename:       /lib/modules/2.6.12-10-386/kernel/drivers/net/ndiswrapper/ndiswr apper.ko
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
version:        1.1
license:        GPL
vermagic:       2.6.12-10-386 386 gcc-3.4
depends:        usbcore
srcversion:     E21E28A177890611AE46391
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if dri ver is hung. (default: 0) (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (in t)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (in t)
parm:           if_name:Network interface name or template (default: wlan%d) (ch arp)
ian@ubu:~$
[I]
You did turn encryption off yes?[/I][/QUOTE]

Yes, I did turn off encryption.  Anything there give a clue?

---

### Post by boomerian on 2006-01-23
Okay, I tried to post replies a couple of times over the weekend but couldn't hook up due to the database issues.
I upgraded the firmware (revision C on the DI-524) to 3.02, but there is no change. (Access Point still showing all zeroes when I enter "iwconfig")
Where do we go from here? I'm determined, but this sure is frustrating.

---

### Post by RavenOfOdin on 2006-01-24
I have one of these for my hotel access point.
This information might just be something I can print out and run with. :cool:

---

### Post by boomerian on 2006-01-25
*bump* for consideration - can anyone help, please?

---

### Post by boomerian on 2006-01-26
Is this a lost cause? Is there anyone reading this who can or is willing to help?

---

### Post by BenTyreman on 2006-01-26
Have you tried building the latest version of ndiswrapper from source? I have a Linksys WMP54G with the Broadcom chipset and it wouldn't do anything until I used the latest version. I used the drivers provided on the CD-ROM.

---

### Post by boomerian on 2006-01-26
Thanks, Ben. I'll try that, too. (From SourceForge.net, I presume?)
The latest (stable) version appears to be 1.8 (dated 16January2006) - I hope that does it!
Thanks for responding...

---

### Post by boomerian on 2006-02-01
Could the kernel version be preventing (whatever version I have loaded of) ndiswrapper from working?
WMP54G v.2 Broadcomm chipset/driver bcmwl5.inf and bcmwl5.sys loaded
C'mon gang - certainly someone out there can get me up and running????

---

