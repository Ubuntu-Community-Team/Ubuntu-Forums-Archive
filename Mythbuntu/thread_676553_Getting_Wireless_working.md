---
title: "Getting Wireless working"
date: 2008-01-23
forum: Mythbuntu
---

### Post by Kawayanan on 2008-01-23
Hello,

I have a reasonably new mythbuntu box that is working nicely.  When I got it going though, I did not have a wireless adapter yet (its in a part of my house that doesn't have wires pulled).  I finally got the wireless adapter I ordered and now wanted to get it working.  I had checked the ubuntu wiki, and chose a Netgear WG111V2 usb wireless adapter (its listed as working out of the box).  The question now is what I need to do to get it working on a box thats already set up.

I have a desktop I was using to test mythbuntu, and tried reinstalling everything with the WG111v2 plugged in.  As the wiki said, it worked just fine out of the box.  When I plug it into my setup mythbuntu box however it doesn't. Before I get down and dirty messing with the configuration manually, is there a way to do a "find new hardware" type thing.  On a new install, it clearly finds the wireless adapter and set everything up right, is there a way to get an existing install to run the setup that runs for a new install?  I'd rather not wipe out my nicely working HTPC to do a reinstall but would also like to avoid manually fighting with kernel modules and configuration files.

As I said, I do have a install with it working (on a test PC), but don't know enough to know what config files and such to look at in order to manually fix things on my actual mythbuntu box.  Anyone know the easiest way to get my new wireless adapter on my existing box?

Thanks for the help!

Kawayanan

---

### Post by wieman01 on 2008-01-24
Please insert the adapter and post the last 10 lines of:
> dmesg
Then:
> sudo lshw -C network
> sudo iwlist scan
These are terminal commands by the way. I am sure your adapter is working.

---

### Post by Kawayanan on 2008-01-24
> **wieman01 said:**
> Please insert the adapter and post the last 10 lines of:

Then:


These are terminal commands by the way. I am sure your adapter is working.

Thanks for the reply.  Sorry I couldn't reply earlier.  My daughters use the dvr in the morning, so I couldn't fiddle with it.  I have to work to get time to work on it - no one want it to go down.

I can't read anything on the TV, so I had to connect a monitor.  I can only get one output running at once, so I needed to reboot.  After rebooting, I got a popup that there were updates available.  I looked like I had network access, but only briefly (ifconfig said something like 38 packets).  I tried rebooting again, but didn't seem to get any connection at all.  Here are the output from the commands you suggested:

dmesg:
```
[   38.209248] wlan0: Initial auth_alg=0
[   38.209255] wlan0: authenticate with AP 00:09:5b:3e:0a:b6
[   38.212240] wlan0: RX authentication from 00:09:5b:3e:0a:b6 (alg=0 transaction=2 status=0)
[   38.212246] wlan0: authenticated
[   38.212249] wlan0: associate with AP 00:09:5b:3e:0a:b6
[   38.214854] wlan0: RX AssocResp from 00:09:5b:3e:0a:b6 (capab=0x1 status=0 aid=4)
[   38.214859] wlan0: associated
[   38.265883] NET: Registered protocol family 10
[   38.266044] lo: Disabled Privacy Extensions
[   38.266261] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   41.834533] wlan0: No ProbeResp from current AP 00:09:5b:3e:0a:b6 - assume out of range
[   48.990023] wlan0: no IPv6 routers present
[   73.810825] wlan0: No STA entry for own AP 00:09:5b:3e:0a:b6
[  105.786075] wlan0: No STA entry for own AP 00:09:5b:3e:0a:b6
[  137.761379] wlan0: No STA entry for own AP 00:09:5b:3e:0a:b6
[  169.736923] wlan0: No STA entry for own AP 00:09:5b:3e:0a:b6
[  201.712183] wlan0: No STA entry for own AP 00:09:5b:3e:0a:b6
[  233.687430] wlan0: No STA entry for own AP 00:09:5b:3e:0a:b6
[  253.654694] wlan0: No STA entry for own AP 00:09:5b:3e:0a:b6

```

lshw:
```
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1b:2f:ea:c4:c9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

```
wlan0     Scan completed :
          Cell 01 - Address: 00:11:24:60:A2:3B
                    ESSID:"Shannon's AirPort"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz
                    Quality=3/64  Signal level=7/65  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000077966812d3
          Cell 02 - Address: 00:1C:B3:AB:7F:01
                    ESSID:"Apple Network ab7f01"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz
                    Quality=22/64  Signal level=8/65  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (2) : TKIP WEP-40
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000008cfef74557
          Cell 03 - Address: 00:0D:88:81:D8:75
                    ESSID:"raabe"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz
                    Quality=37/64  Signal level=18/65  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Extra:tsf=00000000ddcc91e0
          Cell 04 - Address: 00:09:5B:3E:0A:B6
                    ESSID:"Wireless"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz
                    Quality=53/64  Signal level=25/65  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:tsf=00000027b7ba6180

```

and for good measure, ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:1B:FC:A0:EF:39  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:131 errors:0 dropped:0 overruns:0 frame:0
          TX packets:131 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9744 (9.5 KB)  TX bytes:9744 (9.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1B:2F:EA:C4:C9  
          inet6 addr: fe80::21b:2fff:feea:c4c9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:4750 (4.6 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-2F-EA-C4-C9-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

My router is "Wireless" running WEP.  I have checked /etc/network/interfaces and it appears to have all the correct stuff (correct essid, correct wep key, dhcp, auto wlan0, etc).

Kawayanan

---

### Post by Kawayanan on 2008-01-24
Well, when I rebooted to switch the output to the tv (instead of monitor), the network came up.  I lasted for about 3-5 minutes.  Enough time to download some updates and ssh in, but while I was connected via ssh it just died.  I can check log files to see if there is a clue to what happened, just not right now.    Mythtv is currently recording and I don't want to reboot it to use the monitor (I can't read anything at the terminal on my tv).  If there are any suggestions of what logs to check, post them and I will check after this show is over.

Kawayanan

---

### Post by wieman01 on 2008-01-25
I cannot tell you what log files will be most suitable right now. I'll try to find out. But your adapter is OK as far as I can tell. No idea why it would die out of a sudden.

---

### Post by Kawayanan on 2008-01-30
I'm still trying to get this working.  My wireless network works sometimes upon reboot, but never for very long before dying.  I have checked my syslog and found a few different kinds of errors.

On reboots where the network never comes up, I get these errors:

```
Jan 30 18:48:24 mythbox kernel: [  205.612547] wlan0: No STA entry for own AP 00:09:5b:3e:0a:b6
```

It never seems to get a DHCP reply or something.

On the reboots when the network does come up, I end up getting these error:

```
Jan 30 20:20:40 mythbox kernel: [  872.007654] WEP decrypt failed (ICV)
Jan 30 20:20:40 mythbox kernel: [  872.007660] wlan0: RX WEP frame, decrypt failed
```

That set of errors get repeated a bunch around the time the network goes down (though they show up when the network is still working I think).

I also posted a question with more of the logs in the Network and Wireless forum hoping maybe they know more about wireless problems. [http://ubuntuforums.org/showthread.php?p=4240227#post4240227]("http://ubuntuforums.org/showthread.php?p=4240227#post4240227")

Anyone here have any ideas?

Thanks,
Kawayanan

---

