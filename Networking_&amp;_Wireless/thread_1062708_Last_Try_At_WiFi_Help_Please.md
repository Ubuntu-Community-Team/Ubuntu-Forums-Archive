---
title: "Last Try At WiFi Help Please"
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by joeyknuccione on 2009-02-07
>Intrepid under Gnome, built in Intel wireless card on HP dv9235nr laptop, always works with windoze
I've been trying to get my Palm to sync and share an internet connection over wifi for a year now, and nothing I've done works. Can anyone please help with a solution? I love Ubuntu, but if I can't get my wifi setup I gotta do something else.
The wifi will work at say a Krystals, or pretty much any other wifi hotspot. My problem is trying to set it up to sync or work with any wifi device I own.

1- Does Kubuntu or other versions have proper wifi support?
2- If no Ubuntu will work, is there any Linux that will?
3- I've tried every wifi/networking package available through the repos, is there anything that will get this wifi to work? I need wifi sync and internet connection sharing from laptop to my Palm TX.
4- Am I doomed to windoze forever with this setup?

---

### Post by joeyknuccione on 2009-02-07
Alright! I finally think I'm closing in. Looks like using wifi-rader, I'm able to get a signal between the two, but it seems to be unable to setup the IP address.

Wifi radar shows a strong blue signal, the Palm seems connected, but with no signal strength. I think this is part of the IP address deal. 

Iwconfig output:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"joe"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

Ifconfig output:
```

eth0      Link encap:Ethernet  HWaddr 00:16:36:db:a2:be  
          inet addr:192.168.254.1  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fedb:a2be/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1857 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1680 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1875026 (1.8 MB)  TX bytes:295701 (295.7 KB)
          Memory:da000000-da020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:680 (680.0 B)  TX bytes:680 (680.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:19:d2:36:fd:88  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-D2-36-FD-88-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Does this help?

---

### Post by issih on 2009-02-07
Just to clarify, what you want to do is take an internet connection recieved via one interface (e.g. hardwire ethernet) and then broadcast that connection via your computer's wireless interface so that other wifi devices can connect to the internet via your computer?

In effect using your computer as a wifi router.

is that correct?

---

### Post by joeyknuccione on 2009-02-07
> **issih said:**
> Just to clarify, what you want to do is take an internet connection recieved via one interface (e.g. hardwire ethernet) and then broadcast that connection via your computer's wireless interface so that other wifi devices can connect to the internet via your computer?

In effect using your computer as a wifi router.

is that correct?

Thank you for your response. I think you've got it right.

1) DSl wired into laptop: Okay

2) Laptop wifi out to Palm: Seems okay

3) Palm would then sync/surf through laptop: not okay

I know it may sound goofy, but it's a setup I need for work purposes

---

### Post by issih on 2009-02-07
Ok, I can't sadly give you a direct link that will make all your pain go away..Essentially though you need to look into the following technologies:

ip masquerading (basically forwarding ip traffic from one interface to the next)

dns forwarding (sending dns requests through to the dns servers)

dhcp servers (automatically assigning the connecting device an ip address)

Googling will give you this:

[http://www.google.co.uk/search?hl=en&client=firefox-a&rls=org.mozilla%3Aen-GB%3Aofficial&hs=I1n&q=ubuntu+internet+connection+sharing&btnG=Search&meta=](http://www.google.co.uk/search?hl=en&client=firefox-a&rls=org.mozilla%3Aen-GB%3Aofficial&hs=I1n&q=ubuntu+internet+connection+sharing&btnG=Search&meta=)

Which as always is a mix of good and bad and outdated advice.

In the past the firestarter program was capable of making much of this work, but it seems to be unpopular in the community for various reasons I am not au fait with, partly I suspect its just outdated.

In the past I used the dnsmasq and ipmasq packages to set up what you want, but masquerading behind a bluetooth interface rather than a wireless one, dnsmasq even includes a little dhcp server. In general though I am not aware of a magic bullet cure here, although hopefully someone else is. At least now you know more about what you want to ask about.

This is also well worth reading

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

If I was you I'd give firestarter a whirl first off, as it will be the least painful by some considerable margin..oh and I'll also note that I believe that making this all a whole boatload easier is something that is being worked on for the jaunty release :)

Hope that helps

---

### Post by joeyknuccione on 2009-02-07
I 'preciate the info. I'll mark this thread as solved, and open up a new one if I get stuck.

---

### Post by issih on 2009-02-07
You're welcome, good luck with it :)

---

