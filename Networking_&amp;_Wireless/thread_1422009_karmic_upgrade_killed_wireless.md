---
title: "karmic upgrade killed wireless"
date: 2010-03-04
forum: Networking &amp; Wireless
---

### Post by Radissthor on 2010-03-04
Hello everyone,

Believe me, I know this is a very common issue and I've spent hours reading different solutions and workarounds to this problem. I even had it myself a while ago and fixed it somehow. 

Well, a friend of mine is trapped at a place with no wired connections and desperately needs wireless to work (we've been talking on the phone). He had jaunty and wireless was working out of the box, then upgraded to karmic and now Network Manager says wireless is "disabled" and the option to enable it is greyed out.

He's using a HP compaq 6910p. here are some outputs he sent me from a cyber-cafe with much effort:

```
    ezergal@puerto:~$ ifconfig

    lo Link encap:Local Loopback

    inet addr:127.0.0.1 Mask:255.0.0.0

    inet6 addr: ::1/128 Scope:Host

    UP LOOPBACK RUNNING MTU:16436 Metric:1

    RX packets:4 errors:0 dropped:0 overruns:0 frame:0

    TX packets:4 errors:0 dropped:0 overruns:0 carrier:0

    collisions:0 txqueuelen:0

    RX bytes:240 (240.0 B) TX bytes:240 (240.0 B)


    ezergal@puerto:~$ iwconfig

    lo no wireless extensions.


    eth0 no wireless extensions.


    wmaster0 no wireless extensions.


    wlan0 IEEE 802.11abgn ESSID:""

    Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated

    Tx-Power=off

    Retry long limit:7 RTS thr:off Fragment thr:off

    Power Management:off

    Link Quality:0 Signal level:0 Noise level:0

    Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0

    Tx excessive retries:0 Invalid misc:0 Missed beacon:0

```


He'll probably be taking care of this thread soon, but I'm posting meanwhile to see if anyone can suggest something. I think his network/interfaces file only has two lines which I don't remember right now.

Ideas, suggestions and responses in general, I'm sure, will be much appreciated. 
PS: My friend is really really new to Linux and Ubuntu, so be gentle please. I'm also a n00b but at least I use forums a lot.

---

### Post by BGRT on 2010-03-05
Being completely new to Linux / Ubuntu I though I had cocked up somewhere so I'm glad I'm not the only one with this sort of problem... 
After an update yesterday, my wireless went completely wonky. Where it worked perfectly after 1st installing Ubuntu last week, the wifi signal shown on the top of the screen now goes up & down like a yoyo, spending more time disconnected than not. Being right next to the router doesn't make the slightest bit of difference. I have another wifi piece of kit connecting through the same router and this is still working fine. Any pointers appreciated as I'd really like to be able to stick to Ubuntu !
PS; my machine is a Dell Insiron 6000 laptop.
 
TIA

---

