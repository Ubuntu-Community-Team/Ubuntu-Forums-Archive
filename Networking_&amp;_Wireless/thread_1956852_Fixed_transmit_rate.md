---
title: "Fixed transmit rate"
date: 2012-04-11
forum: Networking &amp; Wireless
---

### Post by 00145217 on 2012-04-11
Hello, I am in a situation where I need my wireless card to transmit at low rate (1Mbps or 2Mbps).
I set my Router which is DD_WRT to 2Mbps rate.
However when I tried to connect my wireless card to the router it and do iwconfig the rate changed up to 11Mbps by it self.
I tried to sudo iwconfig wlan1 rate 1M, which doesn't help.
I'm using ath9k_htc driver and I am guessing there is some rate control in the driver that cause this.
Is there any way I can tell my wireless card to only transmit at fixed rate of either 1Mbps or 2Mbps?

Thank you.

---

### Post by iponeverything on 2012-04-11
tc can do rate limiting for you.

---

### Post by 00145217 on 2012-04-11
Hello,
Thank you for your reply, I read through the tc documentation.  However, I did not find the option to limit the rate.
I am also wondering the situation I need is that I need the transmitted packet to have PLCP header that have the rate field as 1Mbps so I am wondering if tc will be able to do that.
If you could point me to the option that I can use tc to limit the rate that would be a great help.
Thank you

---

### Post by iponeverything on 2012-04-12
> **00145217 said:**
> Hello,
Thank you for your reply, I read through the tc documentation.  However, I did not find the option to limit the rate.
I am also wondering the situation I need is that I need the transmitted packet to have PLCP header that have the rate field as 1Mbps so I am wondering if tc will be able to do that.
If you could point me to the option that I can use tc to limit the rate that would be a great help.
Thank you

tc is the same mechanism used by dd-wrt for QOS -- it operates at a lower level than 802.11 - so no, it does not affect the 802.11 encapsulation.

I was under the impression that goal was the control of the data transmission rate -- not the same, but only though 802.11.

is this homework?

---

### Post by 00145217 on 2012-04-12
Thank you for your reply.
I'm sorry for my misunderstanding.
First I somehow thought that tc is referred to the Ubuntu's tc command, but it was my mistake.
This is for a project that I have to log low level 802.11b packet with USRP2.  So I am trying to use the BBN80211 code that could decode 1Mbps and 2Mbps packet, and I will not have time to implement the CCK for 5Mbps and 11Mbps so I thought of having all the transmission at 1Mbps so I could just log them.

---

### Post by iponeverything on 2012-04-12
802.11 is implemented device's firmware -- so I think your best bet would be to set your AP to 802.11b and turn the TX power down to 2 dBm. 

you said that the AP was dd-wrt -- it should not be problem.

that should keep your transmission rate low.

btw- tc on dd-wrt and ubuntu are same utility.

---

### Post by 00145217 on 2012-04-16
Thank you for your suggestion,
I will try that out.

---

