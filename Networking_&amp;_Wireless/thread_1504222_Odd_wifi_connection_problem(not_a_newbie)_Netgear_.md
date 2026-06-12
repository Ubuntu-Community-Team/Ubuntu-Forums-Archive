---
title: "Odd wifi connection problem(not a newbie) Netgear WNDR3700"
date: 2010-06-07
forum: Networking &amp; Wireless
---

### Post by sderrick on 2010-06-07
Lucid i386
Dell inspiron 1525 with 4695agn, iwlagn driver

Just installed a new router, Netgear WNDR3700

Old inspiron laptop with Hardy installed connects fine to G wireless
An Acer with Vista connects fine to G wireless

My Inspiron with Lucid connected fine until I enabled WPA on the routers 5Ghz band.  At that point I couldn't connect on any, 2.4 Ghz no enc, or the wired connection.  The Windoze pc was connecting fine. Fired up the old Hardy laptop and it connected fine. 

Now here's the weirdness!!
As long as I had the Hardy laptop connected either wired or wireless, I could connect to the router with the Lucid laptop to unsecured wireless or wired. Soon as I turned off the old Hardy laptop, my Lucid machine could not connect? 

WTF???

I then disabled security on the router and I could connect with my Lucid machine??? 

any clues?

Scott

---

### Post by sderrick on 2010-06-08
from the kernel log

Jun  5 12:56:02 scotts-laptop kernel: [  265.180540] wlan0: direct probe to AP c0:3f:0e:7a:6a:55 (try 1)
Jun  5 12:56:02 scotts-laptop kernel: [  265.185299] wlan0: direct probe responded
Jun  5 12:56:02 scotts-laptop kernel: [  265.185309] wlan0: authenticate with AP c0:3f:0e:7a:6a:55 (try 1)
Jun  5 12:56:02 scotts-laptop kernel: [  265.187155] wlan0: authenticated
Jun  5 12:56:02 scotts-laptop kernel: [  265.187200] wlan0: associate with AP c0:3f:0e:7a:6a:55 (try 1)
Jun  5 12:56:02 scotts-laptop kernel: [  265.190881] wlan0: RX AssocResp from c0:3f:0e:7a:6a:55 (capab=0x421 status=0 aid=1)
Jun  5 12:56:02 scotts-laptop kernel: [  265.190889] wlan0: associated
Jun  5 12:56:47 scotts-laptop kernel: [  310.220083] wlan0: deauthenticating from c0:3f:0e:7a:6a:55 by local choice (reason=3)

---

### Post by sderrick on 2010-06-09
:guitar:
I might have fixed the problem, it was intermittent so not sure, but have successfully connected 5 times and it connects really fast now!

I think  it was actually two different problems.

1.) dhclient was not getting a lease on a ip address and network manager would time out.  That was the reason for this message

Jun 5 12:56:47 scotts-laptop kernel: [ 310.220083] wlan0: deauthenticating from c0:3f:0e:7a:6a:55 by local choice (reason=3) 

This was fixed by upgrading the bios on this 1525 laptop. I was running A16 and Dell released A17 6 months ago. I should have looked to see if I had the latest but didn't until now.  Once that was installed it started getting a dhcp address right away on an open network. 

2.) The WPA snafu of not being able to connect if I enabled WPA2 encryption on the router, I think is a wpa_supplicant problem. I found this fix for upgrading wpa_supplicant from deb repository

[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/572777/comments/35](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/572777/comments/35)

I was immediately able to log in using WPA2!  :popcorn:

We'll see.  If I have no problems over the next couple days I will change this to Solved!

---

### Post by sderrick on 2010-06-13
Yep not a problem in over 2 dyas.

The bios upgrade released 12/09 fixed the dhclient timeout

Upgrading wpa_supplicant to 0.6.10-2 through the debian repositories fixed using wpa2 login problem. This required upgrading to libssl0.9.8 and libpcsclite1 also

Scott

---

### Post by sderrick on 2010-06-15
](*,)

I was wrong about the dhclient not getting an address and network manager timing out with a reason=3.

Its still happening!  Its intermittent, can go for a couple days, then it will happen a couple time in one day. 

very frustrating.

And it still has the oddity of, if I turn on another linux box that gets a dhcp address it will then acquire one immediately?

Scott

---

