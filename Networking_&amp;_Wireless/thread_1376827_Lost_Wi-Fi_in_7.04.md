---
title: "Lost Wi-Fi in 7.04"
date: 2010-01-09
forum: Networking &amp; Wireless
---

### Post by intricate on 2010-01-09
Lost all wi-fi on my Toshiba laptop that has worked for 4 years.
Cant find available networks and no network icon appears. 
Can anyone walk me step by step to regain my home wi-fi signal using 7.04? Thanks from this beginner Gentlemen.

---

### Post by %hMa@?b&lt;C on 2010-01-09
7.04 is a very old release.  what do you have for a wireless card?

run this in the terminal
```
sudo lshw -C network 
```

---

### Post by hansdown on 2010-01-09
Hi intricate.

7.04 has reached end of life.

Have you considered installing a newer version?

---

### Post by intricate on 2010-01-14
> **hansdown said:**
> Hi intricate.

7.04 has reached end of life.

Have you considered installing a newer version?
Id like to upgrade but don't know how without losing my data and getting the wifi to operate on this toshiba laptop was a bear and reqd lots of forum help. Its a Toshiba A135, about 4 years old. Its a dual partition with XP Pro on 60 gb and 7.04 on 60 Gb.

---

### Post by coffeecat on 2010-01-14
> **intricate said:**
> Id like to upgrade but don't know how without losing my data and getting the wifi to operate on this toshiba laptop was a bear and reqd lots of forum help. Its a Toshiba A135, about 4 years old. Its a dual partition with XP Pro on 60 gb and 7.04 on 60 Gb.

Without the output of the command that jeffc313 posted, no one is going to be able to give you any constructive help regarding your wireless issue. "Lost Wi-Fi in 7.04" doesn't really tell us much.

But here's a thought for you. Download and burn to CD the desktop ISO for 9.10 Karmic. Run it live - that won't touch your HD unless you mount a partition. See if the wireless works. It's quite possible that a wireless chipset that was a "bear" in Feisty is a fluffy kitten in Karmic. :wink: Test your other hardware while you're about it. If everything (most things) work then consider backing up your data and doing a fresh install of Karmic.

---

### Post by bkratz on 2010-01-14
> **intricate said:**
> Id like to upgrade but don't know how without losing my data and getting the wifi to operate on this toshiba laptop was a bear and reqd lots of forum help. Its a Toshiba A135, about 4 years old. Its a dual partition with XP Pro on 60 gb and 7.04 on 60 Gb.

This may be a solution--creating a separate home folder after installation.  

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

