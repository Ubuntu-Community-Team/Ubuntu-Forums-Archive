---
title: "Whats wrong?"
date: 2009-10-14
forum: Networking &amp; Wireless
---

### Post by lynx93 on 2009-10-14
I just reinstalled my whole ubuntu to 9.04 Jaunty verison, comletly resinstalled everything. And now I have a little problem with wireless connections. Ok, wired ones are perfectly working, but the wireless internet... They connect very slowly and they are fast as a bad modem. Whats the problem? Do I need to install some plugin or something or do I have problem with my laptop? Its a Toshiba N100 netbook and it had Ubuntu on it when it was new too.
 
Please help!

---

### Post by Baelus on 2009-10-14
Not sure about the slow connect time, but try this for the speed issue:

```
sudo iwconfig
```

You'll see a part that gives you the bitrate as xMb/s. If it's 1Mb/s or just way too low then try this:

```
sudo iwconfig wlan0 rate 54Mb/s
```

Replace wlan0 with ath0, eth1 or whatever your wireless card is listed as. Also play with the bitrates to see if something else works better.

Hope that helps.

---

### Post by lynx93 on 2009-10-14
it didnt really work :(

---

### Post by Iowan on 2009-10-14
You might also check MTU... though I haven't a clue what it *should* be for wireless.

---

