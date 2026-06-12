---
title: "Wireless Card Help"
date: 2006-06-28
forum: Networking &amp; Wireless
---

### Post by boxxxx117 on 2006-06-28
so i got my driver installed with ndiswrapper

```
Installed ndis drivers:
rt2500          driver present
```

do i have to do anything more to "activate" the card?

i still have this 

```
justin@Walter:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
```

and there is nothing in my System->Administration->Networking for a wireless card

---

### Post by boxxxx117 on 2006-06-28
i now have
```
justin@Walter:~$ ndiswrapper -l
Installed ndis drivers:
rt2500          driver present, hardware present
```

but nothing in my Networking option for wireless

---

### Post by mpvano on 2006-06-29
That just installs the information about your card into the ndiswrapper program. To use ndiswrapper you need to make sure it's loaded (it's an optional driver for your system).

Many people load it by adding it's name to the end of the driver module list in /etc/modules. You need to have root priveleges to edit this file. The easiest way to do this is to open a terminal window and give the command:

sudo gedit

Give it your own password when it asks for a password and you should then be able to use the open menu to open /etc/modules and add the line

ndiswrapper

to the end of that file and save it.

Now when you restart the machine, ndiswrapper will be present and ready for use when your card is plugged in.

From here on in, you still have some things to get working - you should have a working network adapter, but you still need to configure it for use. That's done just like any other non-ndiswrapper based card. Refer to hundreds of other threads here and the information in the wiki for all the various options you have open to do this.

Before you go any farther though, make sure the card's available by opening a terminal window and typing:

iwconfig

And seeing if it shows up in the list of adapters present. Ndiswrapper usually gives the card the device name of wlan0.

At this point, one simple way to use the card (but only for simpler networks) is  to use the  "Networking" Tool in the "System" menu under the "Administration" section.

Hope this gets you started.

Mario

---

### Post by stupidkid on 2006-06-29
Uh just run modprobe ndiswrapper. If it works, then you can add it to /etc/modules or whatever that file is.

---

### Post by patrickfromspain on 2006-06-30
mmm I think you're going the wrong way :S

Do you have a rt2500 based card? If so, it should work right out of the box. I have one, and there's no need on Ndiswrapper. 

Anyway, if you want to try ndiswrapper because it doesn't work or whatever you must first blacklist the driver. sudo gedit /etc/modprobe.d/blacklist and there add rt2500, save and exit.

Now, ndiswrapper. Once ndiswrapper -l says hard present, driver present, you must first do: sudo ndiswrapper -m and the sudo modprobe ndiswrapper to load the module. Now the card should be there.

---

### Post by boxxxx117 on 2006-07-01
ok. you are right it wasnt rt2500 and i have since found the correct driver. 
Now my card is detected in System->Admin->Network  i have a wlan0
i did the ndiswrapper -m command

now my card detects networks but i cannot connect to them. Any ideas why I cant connect?

Im using NetworkManager

---

### Post by boxxxx117 on 2006-07-01
I found this today in lsmod. My wireless card is PCMCIA. 


```
usbcore 130692 3 ndiswrapper,uhci_hcd
```


and under the PCMCIA line i get this

```

pcmcia_core 42640 3 pcmcia,yenta_socket,rsrc_nonstatic

```

should ndiswrapper be in pcmcia_core and not usbcore. if so how do i do this?
thanx

---

### Post by mpvano on 2006-07-01
Network manager is not ready for prime time yet. If you're not sure if you have things working right you should try sticking to the built in tool in the System:Administration:Network menu until you get a working connection.

The right part of the lsmod line shows other drivers that depend on using services from the driver in the left column. The line you saw means ndiswrapper reserves services from the core USB driver in case in needs to talk to a USB network adapter. It's useful information when you are unloading drivers because a driver "reserved" this way by another driver can't be unloaded. These cross uses are called "dependencies" in general...

The mere fact that the ndiswrapper driver is loaded is good, because it means it's available for your card. The fact that the card shows up in network tools or in the output from the following commands is even better. That means that the card is "hooked up" to the linux networking system.

Try these commands and show us the results:

sudo iwconfig

sudo ifconfig

sudo iwlist scan

Also, tell us what you are trying to connect to. Is it your network? Is it using any sort of security (WEP 40, WEP 128, WPA, etc). What kind of router it is, whether you have access to it to change the settings for test purposes, etc.

One big problem lately is that many wireless networks are starting to overlap coverage. My favorite coffee shop is covred by 3 networks now, two of which are on the same frequency. My suburban house is covered by 5 networks! There are actually only 3 non-overlapping channels available for 2.4ghz use (channels are 5 channels wide - the in-between channels are secondary channels used where the rest of the signals are weak enough so some overlap can be tolerated).

Equipment with similar signal strength on the same, or overlapping channels (eg. two adjoining networks on channel 6, or one on channel 6 and one on channel 9) can work OK, but can be tricky to connect to because some programs aren't smart enough to not be "captured" by one or the other of the access points, even if they're not available to you for use.

In addition, the scanning capabilities needed to list all access points have become unreliable in some adapters, making it hard to troubleshoot problems like this, or find your network to associate it from a list.

Even the worst of the above situations, however can be dealt with if you manually provide your card with as much information as possible about the network you are trying to connect with.

It is easier to get things going, at least at first, if you know the following about the access point:

- its exact "essid" name
- its channel number
- it's security configuration, key, key type and key number if used
- whether it rejects connections with unknown "MAC" addresses
- whether it's ever worked for you under another OS.
- how it assigns addresses to users of the access point DHCP or STATIC
- if it's static, how it assigns routes and DNS information (DHCP is easier)
- whether it's YOUR access point or belongs to restaurant, coffee shop, etc.

Also, at this point, you should probably do more homework on the wiki and search for other threads. I believe your card is working from what you said, but configuring it to agree with your access point can be a little confusing sometimes.

If your card and access point show up in iwconfig, then stop messsing with the driver - that part is working...

hope this moves you along a little farther....

Mario

---

### Post by boxxxx117 on 2006-07-01
iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:A0:D1:D5:2B:E5
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:d1ff:fed5:2be5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1447 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1417 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1051715 (1.0 MiB)  TX bytes:226421 (221.1 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:03:6D:20:D9:A6
          inet6 addr: fe80::203:6dff:fe20:d9a6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Memory:26000000-26000800

```

iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:66:04:F3:0F
                    ESSID:"dawes"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-44 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:0F:3D:3A:AF:D8
                    ESSID:"WIFI"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:0/100  Signal level:-68 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

sit0      Interface doesn't support scanning.


```

Im try'n to connect to the "dawes" network, It's my home network. It has no WEP key for the moment. the router is a lynksys wireless-b.

---

### Post by mpvano on 2006-07-01
If I were you, I'd use the admin tools and change your channel from 7 to either 1 or 11. Channel 7 and channel 6 overlap about 80%. The usual way to use the channels is: 6 first, then 1 or 11, then 3 or 9 depending on the relative signal strengths.

That, however, may not be your problem.

It looks like your wireless card is working fine. It's called wlan0. I think you should be able to open the normal networking tools, select wlan0, click on properties and you should find both networks in the essid popup. Select the one you want, pick "dhcp" addressing and click OK.

This should be all you need to do for your network, and the settings should be remembered across boots under Dapper.

It's a little clumsy changing connections this way if you roam, however.

Let us know if you have any luck connecting that way.

If it works, I suggest connecting by a wired system (never try to administer a wireless router via wireless) and selecting channel 1 on the linksys router and restarting. Performance should improve a lot, and it will be easier to associate with it. All the clients should follow the change automatically the next time they're turned on.

If you're STILL not connected, let us know and we can walk you through figuring out what's wrong.

After you're connected using DHCP, the "sudo iwconfig wlan0" command should show the access point MAC address and say you are associated with it along with other appropriate information for that access point.

The ifconfig command should show an IP address on the linksys subnet (assuming you have it's dhcp server turned on). You can check the routing table with the "route -n" command. It should show the linksys (usually at xxx.xxx.xxx.1 as the default route). If you're not sure whether you picked up the correct dns information from the dhcp, you can use the command "cat /etc/resolv.conf" to see what your current DNS servers are.

One last comment that might avoid confusion - When you are messing around with changing configurations that involve DHCP, it's easy to get very confused because the DHCP client implementation in ubuntu takes a VERY long time to shutdown when told to do so. Any changes to network configurations can take 30-40 seconds to occur as a result. If you get impatient, and try to cancel an operation and try it again, you can very easily end up with multiple DHCP clients running at the same time. This will probably confuse both you and the machine and may require a reboot to recover from. Be patient after any changes. You can tell if the client has shut down using the "ps command" or by using the gnome "system monitor" to examine running processes.

I'm sure you're well on your way to getting things working now. Using network manager has it's own special undocumented quirks. If you want to get it working, perhaps someone else can help you - I can't use it here because it's not compatible with some of my networks that use static addressing, so I'm not an authority on it.

Please report back if you get things working.

good luck,

Mario

---

### Post by nomdeguerre on 2006-07-03
Im having a similair problem here, not sure whether to start a new thread or not.

Im using a Netgear MA311, installed driver and hardware recognised, using windows driver and ndiswrapper. Not getting any of this wlan0 showing up, instead im getting eth1 both in network settings and in terminal with the commands iw/if config. iwlist scan brings up my ESSID name and channel and other bits of information.

If i run through the network settings GUI, check the card properties or re-activate it i get an "activating interface "eth1" msg box which lasts for a while and then just dissappears, no conformation.

Running tail /car/log/messages i get the following:

localhostkernel: [ 878.283248] ADDRCONF(NETDEV_UP): eth1: link is not ready
localhostkernel: [ 878.608864] eth1: New link status: Association Failed (0006)

I get those two lines printed twice. 

Runnin iwconfig Acess Point: None

I've been doing this all day and i've kinda dried up now - any suggestions? (first day on linux btw). Thanks for any help!

edit// I saw this somewhere else and changed mine, as i was seeing eth1 and the file had wlan0 in it, but it made no difference:
> When you install ndiswrapper it makes a file named /etc/modprobe.d/ndiswrapper. It probably has a single line which "alias wlan0 ndiswrapper".

If you are seeing your wireless card as eth2 or something else, change the line in the above file to match what the system is calling your wireless card instead of wlan0.

---

### Post by mpvano on 2006-07-04
I have no experience with your card, but it has been my experience that normally the ndiswrapper built into Dapper creates drivers named wlan0. While there are things that may have changed this, I have no idea whether you've done any of them.

Also, there are many ways to "install ndiswrapper" - the term's pretty vague. Adding files to modprobe.d may or may not have been done by your procedure, and it may not be needed.

You may not be using that ndiswrapper driver at all. There are several alternate drivers for some cards, and ndiswrapper is usually considered the last resort.

It's possible to load a driver and have it show up in lsmod, but to not have it be in use. This happens if another driver for that card loads first and "claims" the card.

Depending on the chipset, there may be another driver already available in the linux kernel and that may be what you are actually using. You need to know the chipset and interface type for your card to determine this.

Your card may actually be eth1 (or not, depending on what other interfaces are installed in your machine!). You haven't provided enough information to tell that.

The name of your card doesn't particularly matter, as long is all the software you are trying to use to control it agrees on the name, and that it's always the same every time you startup.

I suggest studying your log files, especially /var/log/messages and /var/log/daemon.log and the output of the dmesg command looking for messages from driver loading. to trouble shoot your problem.

If you ARE in fact using ndiswrapper, you should also make sure that you are using the recommended windows driver. This may NOT be the one shipped with your card or available from the vendors website. Check the ndiswrapper wiki for this information. Some windows drivers do not work.

You've provided no information about your system, Dapper variant, or the network you are trying to connect with., all of which may have a great deal to do with the process as well.

You're also more likely to get help if you start a more specific thread title. This should contain your card name and machine type. You may also have better luck searching first to see if such a thread already exists and joining that one.

This forum works better by shared experience. Most help comes from people who recognize your problem and jump in already knowing the answer, not by finding someone to walk you through all the standard tech-support style troubleshooting steps that have been repeated elsewhere.

Sorry I can't be more help, but at this stage your problem could be almost ANYTHING.

Mario

---

### Post by nomdeguerre on 2006-07-08
Thanks for your reply, i will come back to this with a new thread when i have some time :)

---

