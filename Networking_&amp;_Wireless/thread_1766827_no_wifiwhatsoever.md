---
title: "no wifiwhatsoever"
date: 2011-05-24
forum: Networking &amp; Wireless
---

### Post by geoffy on 2011-05-24
hello all, if i am in the incorrect thread i apologise.
im new to linux having been a long time windows user and its a bit daunting to me. For the most part the transition on my eeepc 1001pxd was very easy. the only problem i have started as spotty wifi connection. it would drop connection after about an hour and would not be able to connect until a restart. ive tried several different solutions to this that i found on the web but that only made it worse as i now have no wifi connection. i figured i should get specific answers for this before i make matters worse. any help on this would be greatly appreciated.

---

### Post by IWantFroyo on 2011-05-24
```
sudo iwconfig wlan0 power off
```

```
sudo iwconfig wlan0 rate 54M
```

Hope that fixes it!

---

### Post by geoffy on 2011-05-25
it says that there is no such device as wlan0, also it says that my network is "UNCLAIMED"

---

