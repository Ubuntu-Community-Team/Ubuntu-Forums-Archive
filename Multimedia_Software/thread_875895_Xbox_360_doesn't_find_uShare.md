---
title: "Xbox 360 doesn't find uShare"
date: 2008-07-31
forum: Multimedia Software
---

### Post by Xecuter on 2008-07-31
I've been trying for two hours now. Ushare starts fine:
```
$ ushare -x
Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
Listening on telnet port 1337
Initializing UPnP subsystem ...
Starting in XboX 360 compliant profile ...
UPnP MediaServer listening on 192.168.1.1:49152
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /media/disk
Found 501 files and subdirectories.
```

192.168.1.1 is eth0, so it's correct. But the 360 doesn't find anything. 
Can there be a problem since I'm using ICS with the Xbox?

Any solutions?

---

### Post by jlindbergh on 2008-07-31
I just posted about something similar in another forum, and I think it might be related: [http://www.avforums.com/forums/showpost.php?p=7458383&postcount=4](http://www.avforums.com/forums/showpost.php?p=7458383&postcount=4)

I'll try to follow this thread to see if anyone comes with a solution other than haxxing the 360 firmware...

---

### Post by ilrudie on 2008-07-31
generally 192.168.1.1 would be your router/gateway for the 192.168.1.0/24 network.  Is your router serving the ushare content or have you changed the routers IP?  If your router is serving up the ushare content you may have to make a virtual IP for the xbox to connect to and bring ushare up on it.

add a stanza to /etc/network/interfaces as follows:

```

auto eth0:1
iface eth0:1 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1
hwaddress ether <MAC address of your eth0 or other valid MAC>

```

Look in the man page for ushare and see how to bring it up on the virtual interface.  Thats my take on the problem anyway.  Someone else might have a better idea.

---

### Post by Xecuter on 2008-07-31
No eth0 is 192.168.1.1 since I'm using ICS with the Xbox:
Xbox (192.168.1.2) --(cable)--> (192.168.1.1 eth0) Ubuntu (10.0.0.6 wlan0) --(wireless)--> (10.0.0.138) Router

I'm thinking that the static IP or the DNS/DHCP-server has something to do with this.

---

### Post by ilrudie on 2008-07-31
> **Xecuter said:**
> No eth0 is 192.168.1.1 since I'm using ICS with the Xbox:
Xbox (192.168.1.2) --(cable)--> (192.168.1.1 eth0) Ubuntu (10.0.0.6 wlan0) --(wireless)--> (10.0.0.138) Router

I'm thinking that the static IP or the DNS/DHCP-server has something to do with this.

OK so 192.168.1.1 is still a gatway and that is probably what is causing this.  DNS shouldn't have anything to do with this unless you need name resolution for some reason.  I would still suggest trying this with the virtual interface and ushare bound to an ip address that is not acting as a gateway.

The other thing i noticed when using ushare is you can't connect from the 360 to ushare as a media center.  Just choose like video's or music and in there you should see the name or ip of your ushare server if its working.  Select that and you should see the contents of your ushare shared folder.

Hope one of those suggestions helps.  Let us know if they don't.

---

### Post by Xecuter on 2008-08-01
Can't find anything about virtual interface in man ushare.
Can you give me a quick howto?

Is the eth0:1 supposed to show in ifconfig and such? It doesn't.

---

### Post by ilrudie on 2008-08-01
it should show in ifconfig.  you will probably have to run ```
ifup -a
``` to start up all auto interfaces.  Also it should also show up after a reboot if you added it into /etc/network/interfaces properly.

To use this interface change the line in /etc/ushare.conf which says
```
USHARE_IFACE=eth0
```to
```
USHARE_IFACE=eth0:1
```Then run
```
sudo /etc/init.d/ushare restart
```to restart the ushare daemon.

---

### Post by flytripper on 2008-08-01
xbox gateways are 192.168.0.1 as its a microsoft product... if you were using xp ics your eth:0(lan card) would have to be this for it to work.

---

### Post by ilrudie on 2008-08-01
> **flytripper said:**
> xbox gateways are 192.168.0.1 as its a microsoft product... if you were using xp ics your eth:0(lan card) would have to be this for it to work.

I don't think thats strictly true.  I think it will use whatever gateway DHCP tells it to use.  Is the OP also having trouble connecting to Xbox Live?

I will check when I get home but I don't think my Xbox is on a 192.168.0.0/24 network and its working fine with Live and ushare.

---

### Post by flytripper on 2008-08-01
i was just saying, its a microsoft product and ics in windows forces the lan nic to 192.168.0.1. so maybe that would be a good start point for troubleshooting..

---

### Post by Xecuter on 2008-08-02
I get this:
```
SIOCSIFFLAGS: Cannot assign requested address
SIOCSIFHWADDR: Device or resource busy - you may need to down the interface
Failed to bring up eth0:1.
```

I ran ifdown -a first.

---

### Post by ilrudie on 2008-08-02
Post the contents of /etc/network/interfaces please.

---

### Post by Xecuter on 2008-08-03
/etc/network/interfaces
```
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.1.1
netmask 255.255.255.0
gateway 10.0.0.138

auto eth0

auto eth0:1
iface eth0:1 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1
hwaddress ether 00:11:09:1b:7a:d2
```

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:11:09:1b:7a:d2  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:9ff:fe1b:7ad2/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5906 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5299 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:695891 (679.5 KB)  TX bytes:1131525 (1.0 MB)
          Interrupt:19 Base address:0xc800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10133 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10133 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5728079 (5.4 MB)  TX bytes:5728079 (5.4 MB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:e5:2a:20:7a  
          inet addr:10.0.0.6  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:e5ff:fe2a:207a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2529466 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1968639 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2144183521 (1.9 GB)  TX bytes:986044894 (940.3 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1E-E5-2A-20-7A-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by ilrudie on 2008-08-03
Comment out the hwaddress and gateway lines in the virtual interface's stanza.  The error you are getting sounds like its having trouble dealing with the hwaddress line.  I don't think either is stricly necissary anyway.  Let me know how that works.

---

### Post by Xecuter on 2008-08-04
No it doesn't work. Setting up ushare on eth0:1 works fine, but the xbox still doesn't find ushare.

---

### Post by ilrudie on 2008-08-04
OK.  sounds like we are making some progress.  We have an interface thats not a gateway and ushare is listening on it.  Make sure you are using the -x flag when ushare starts.  I had to adjust the rc script to use this flag.  Alternativly you can just kill the ushare process started by the rcscript and run ushare -x.  The xbox compatibily option in the ushare.conf did not seem to work for me.

Take me through what you are doing on the xbox when its failing?  Are you getting errors on the xbox?  Is it timing out or just waiting indefinitly?

Also doing a little research I found that 'SIOCSIFFLAGS: Cannot assign requested address' is always shown when bringing up a virtual interface so it should be working even when you get that message but it seems you already discovered that.  I thought it should be posted in this thread to benefit any others who might be following along.

---

### Post by Xecuter on 2008-08-04
What do you mean do on the Xbox? Ushare is supposed to show automatically when going to videos and pressing X (change source or something). It does so on my computer. It's friend of mine who has the problem if you wonder. ^^, 

And yes i run it with the -x flag.

---

### Post by ilrudie on 2008-08-04
So there is no error; it just doesn't show up?  Earlier in the thread you showed the xbox's ip address as 192.168.1.2.  Is that still the xbox's ip.  You should use a different ip for the xbox, the virtual ip and the xbox.  Are you having any trouble connecting to xbox live?  Try setting up a on the subnet the ubuntu router is serving and verify that you have basic connectivity to the virtual ip.  Ping, traceroute, telnet to the ushare port?  Are they all working?  How is the ICS setup?  Is there a tutorial that your friend followed?

---

### Post by Xecuter on 2008-08-05
No changed the IP on the Xbox to 192.168.1.3. ICS is working fine, used this guide [https://help.ubuntu.com/community/Internet/ConnectionSharing?action=show&redirect=InternetConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing?action=show&redirect=InternetConnectionSharing) .

I didn't use a guide when setting up ushare. 

I'll try checking if eth0:1 is responding.

---

### Post by Xecuter on 2008-08-05
ping 192.168.1.2 works fine.
telnet 192.168.1.2 1337 also works fine.
traceroute 192.168.1.2 works.

So is the problem on the xbox then?

---

### Post by Xecuter on 2008-08-07
Bump!

Anyone?

---

### Post by ilrudie on 2008-08-07
Have you tried hooking up a known good xbox to the ushare in question and/or the xbox in question to a known good ushare in order to pinpoint the issue?

---

### Post by Xecuter on 2008-08-07
No, no one else uses Ubuntu and ushare.

---

### Post by ilrudie on 2008-08-07
> **Xecuter said:**
> What do you mean do on the Xbox? Ushare is supposed to show automatically when going to videos and pressing X (change source or something). It does so on my computer. It's friend of mine who has the problem if you wonder. ^^, 

And yes i run it with the -x flag.

For some reason I thought you had another xbox from reading this.  I guess I got a little confused. 

The only other thing I can think to do right now is try selecting the media center button at the bottom of the media tab to get it to search your network for computers.  You won't be able to complete the setup because its not real windows UPnP but it might force a lan search and maybe it will discover ushare.  I'm very perplexed by the issues you are having because it was super easy for me to setup.  The hardest thing I had to do was modify the init script to force it to use -x when it started ushare as a daemon.

---

### Post by zoroko on 2008-10-31
BUMP...


does anyone have any ideas? I'm having the same problem, Ushare works fine, I did all those tests, but the Xbox can't see it at all.. nothing.. :(

---

### Post by rkrizan on 2010-02-01
You know what's funny, is that I have 2 xboxs. The first is either a Xenon or a Zephyr console. The second is a Falcon, an Elite console. The Elite console works flawlessly with uShare. The first console, the older console, does not. Same identical network and options, both wireless, the works. Very odd.

---

