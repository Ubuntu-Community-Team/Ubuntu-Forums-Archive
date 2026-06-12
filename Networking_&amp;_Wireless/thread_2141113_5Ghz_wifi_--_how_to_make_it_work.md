---
title: "5Ghz wifi -- how to make it work"
date: 2013-05-01
forum: Networking &amp; Wireless
---

### Post by fizikz on 2013-05-01
Intel 5100AGN (dual band, 2.4Ghz & 5Ghz)
iwlwifi driver
Ubuntu 12.04
Asus RT-N53 (dual band, 2.4Ghz & 5Ghz)


I have set up a wifi network with different SSIDs for the different bands. I can see the 2.4Ghz band, but not the 5Ghz band. Using "sudo iwlist scan" shows no 5Ghz entries, but "sudo iwlist wlan0 channel" does indicate that the card is capable of both bands.

What must I do to see the 5Ghz band? 

And please, please, please, no comments on disabling N in the drivers. I see that "solution" plastered all over the internet, and it is totally unacceptable.

---

### Post by ahallubuntu on 2013-05-01
~

---

### Post by fizikz on 2013-05-02
Thanks for your reply, ahallubuntu.

I was mistaken; I meant to say the problem exists with a system running 13.04. 

I have an Asus G1 laptop with an Intel 5100AGN running Ubuntu 12.04, and it sees the 5Ghz band without any problem.

My Acer Aspire One 110, also with an Intel 5100AGN updated to Ubuntu 13.04 does not see the 5Ghz band. Yes, this has been tested in the same room as the wireless access point.

---

### Post by chili555 on 2013-05-02
> **ahallubuntu said:**
> You shouldn't have to do anything.  [B]My 5100 picks up dual band / 5GHZ no problem in 12.04.
[/B]
However, keep in mind that 5GHZ doesn't have the same range that 2.4GHZ has.  If you are only marginally able to pick up your 2.4GHZ signal from one location, you may not be able to pick up 5GHZ at all.  Can we assume you're tried sitting in the same room as the router?Please tell me the make and model of your access point or router for my further research. Thanks.

---

