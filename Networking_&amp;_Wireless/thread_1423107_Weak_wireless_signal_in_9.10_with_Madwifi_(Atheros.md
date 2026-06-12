---
title: "Weak wireless signal in 9.10 with Madwifi (Atheros ar5001x)"
date: 2010-03-06
forum: Networking &amp; Wireless
---

### Post by gelatinous_cube on 2010-03-06
Hi,

I am among those unfortunate wretches with an Atheros wireless card (ar5001) and I've had problems with it from the day I installed Ubuntu. I've been using Madwifi to connect to the internet, and it's worked fine, until I lately changed my internet connection, got a new modem etc.

Madwifi works still, but the signal is really weak - while not so on Windows Vista. I have found many people complaining about this, but none of the help has been any good. 

I know it's NOT ipv6 related. Do I have to change the connection settings? Is my card outdated or whatever? Am I using inefficient drivers? Should I just not use Madwifi and rather something else instead? 

(Trying to install ndiswrapper and get it to work was a dreadful process, so I won't attempt that again.)

---

### Post by gelatinous_cube on 2010-03-07
Come on! Anybody? Is someone at least able to explain the theory behind this? 

How does Madwifi work? Why cannot it achieve the same performance as the correct driver in Windows?

---

### Post by Easy Limits on 2010-03-07
You say "got a new modem etc.".  Does that mean you got a new router also?

---

### Post by gelatinous_cube on 2010-03-15
> **Easy Limits said:**
> You say "got a new modem etc.".  Does that mean you got a new router also?

Yes. I had to use a manual DNS address for IPv4, the previous connection sorted everything automatically.

---

### Post by sidkat2006 on 2010-04-05
I guess its got to do with the rate adaptation algorithms in the madwifi drivers..Because i hv two wireless cards intel and atheros. The signal quality in intel is much better when i try using both simulataneously

---

