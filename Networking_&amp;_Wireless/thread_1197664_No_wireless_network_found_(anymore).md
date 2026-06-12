---
title: "No wireless network found (anymore)"
date: 2009-06-26
forum: Networking &amp; Wireless
---

### Post by erdalronahi on 2009-06-26
We have two identical laptops, both of which have been running Ubuntu for 1,5 years without any trouble. Now one of them cannot see any wireless networks anymore. 

The laptop and its user are abroad, so I cannot do direct troubleshooting. But what I understood over the phone was:

- A driver problem is unlikely, it's an Intel chipset, no propietary drivers used
- Replacing NetworkManager with WICD did not help, wicd also does not see any networks.
- 'sudo ifconfig' shows an active WLAN0, but no connection

What can be possible reasons for the problem and how can we resolve this? Any hint will be appreciated.

---

### Post by terazen on 2009-06-26
Some laptops have a button to disable the wireless card that can accidentally get pressed.  On my dell it's Fn+F2, though I've seen some that are just 1 key or a button that you slide up and down.  The key usually has some sort of wireless looking logo on it.

---

### Post by terazen on 2009-06-26
FYI, I just tested this on mine and the NetworkManager program needed to be stopped and started for the wireless to come back.  Just pressing the Fn+F2 to reenable wireless didn't do it for some reason.

---

### Post by Rob.I on 2009-06-26
> **terazen said:**
> FYI, I just tested this on mine and the NetworkManager program needed to be stopped and started for the wireless to come back.  Just pressing the Fn+F2 to reenable wireless didn't do it for some reason.
I'm going go try this when my Ubuntu gets re-installed...I'm having the same issue with my Inspiron 6000.

---

### Post by erdalronahi on 2009-06-26
Right, this was my first idea, too. But this is not the case, there is no such switch or key combination. Any other ideas?

---

### Post by superprash2003 on 2009-06-27
what does the following 2 commands give
1)iwconfig
2)sudo iwlist scanning

---

### Post by nmaster on 2009-06-27
it could be a hardware issue.  wireless cards don't fail often, but it isn't impossible.  more likely than failure tho is that it became unseated.  try popping it out and then putting it back in.

---

### Post by kixome on 2009-06-27
actually wireless cards burn out quite alot, especially when reaching the 5 year use mark. I have seen as many wireless (laptop especially) cards burn out as i have ethernet cards/chipsets.

---

### Post by nmaster on 2009-06-27
> **kixome said:**
> actually wireless cards burn out quite alot, especially when reaching the 5 year use mark. I have seen as many wireless (laptop especially) cards burn out as i have ethernet cards/chipsets.

i didn't know that.  i guess i've never kept a laptop long enough to find out lol.  actually the laptop i have know is having some wireless card problems.  its under warranty so i'm getting a new card.  i suppose the tech suppport guy meant that it was not common for it to break so quickly.  i guess i shouldn't believe everything i hear from those guys.

---

### Post by erdalronahi on 2009-06-28
> **superprash2003 said:**
> what does the following 2 commands give
1)iwconfig
2)sudo iwlist scanning

Meanwhile I got a hint to the problem. The dmesg output is:
```

[   31.759063] iwl3945 0000:02:00.0: firmware: requesting iwlwifi-3945-1.ucode
[   31.813429] iwl3945: iwlwifi-3945-1.ucode firmware file req failed: Reason -2
[   31.813434] iwl3945: Could not read microcode: -2

```

So I got bug #185470 [https://bugs.edge.launchpad.net/bugs/185470](https://bugs.edge.launchpad.net/bugs/185470)

---

