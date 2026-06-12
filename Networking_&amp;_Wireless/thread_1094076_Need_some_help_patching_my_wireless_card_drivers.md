---
title: "Need some help patching my wireless card drivers"
date: 2009-03-12
forum: Networking &amp; Wireless
---

### Post by humphreybc on 2009-03-12
Hi I am trying to patch my Intel Corporation PRO/Wireless 4965 drivers to allow WEP cracking. I'm using airdriver-ng but can't seem to install the drivers... What should I be doing?

I run sudo airdriver-ng supported and it shows me this:

```

Following stacks are supported:
0. IEEE80211
1. IEEE80211 Softmac
2. mac80211

Following drivers are supported:
0. ACX100/111 - IEEE80211
1. ADMtek 8211 - IEEE80211
2. ADMtek 8211 - mac80211
3. Atmel at76c50x - IEEE80211
4. Atmel at76_usb - IEEE80211
5. Broadcom 4300 - IEEE80211
6. Broadcom 4300 - mac80211
7. Cisco/Aironet 802.11 - IEEE80211 Softmac
8. HostAP - IEEE80211
9. Intel Pro Wireless 2100 B - IEEE80211
10. Intel Pro Wireless 2200 (B/G)/2915 (A/B/G) - IEEE80211
11. Intel Pro Wireless 3945 A/B/G - IEEE80211
12. Intel Pro Wireless 3945 A/B/G - raw mode
13. Intel Pro Wireless 3945 A/B/G - mac80211
14. Intel Pro Wireless 4965 A/B/G/N - mac80211
15. Lucent Hermes and Prism II - IEEE80211
16. Madwifi[-ng] - IEEE80211
17. Prism54 - IEEE80211
18. Prism54 - mac80211
19. Ralink rt2400 (legacy)
20. Ralink rt2400 (rt2x00) - IEEE80211
21. Ralink rt2400 (rt2x00) - mac80211
22. Ralink rt2500 (legacy)
23. Ralink rt2500 (rt2x00) - IEEE80211
24. Ralink rt2500 (rt2x00) - mac80211
25. Ralink rt2570 (legacy)
26. Ralink rt2570 (rt2x00) - IEEE80211
27. Ralink rt2570 (rt2x00) - mac80211
28. Ralink rt61 (legacy)
29. Ralink rt61 (rt2x00) - IEEE80211
30. Ralink rt61 (rt2x00) - mac80211
31. Ralink rt73 (legacy)
32. Ralink rt73 (rt2x00) - IEEE80211
33. Ralink rt73 (rt2x00) - mac80211
34. Realtek rtl8180 - custom
35. Realtek rtl8187 - custom
36. Realtek rtl8187 - mac80211
37. WLAN-NG - IEEE80211
38. Xircom Creditcard Netwave - IEEE80211
39. ZyDAS 1201 - IEEE80211 Softmac
40. ZyDAS 1211 - IEEE80211 Softmac
41. ZyDAS 1211rw - IEEE80211 Softmac
42. ZyDAS 1211rw - mac80211
43. NDIS Wrapper

```

So I choose to install number 14, for my card and type sudo airdriver-ng install 14 and it gives me this:

```
Driver "Intel Pro Wireless 4965 A/B/G/N" specified for installation.
Your current GCC version doesn't match the version your kernel was compiled with.
The build modules will probably not load into the running kernel.
DI_DRIVERPATH1[14] isn't set, you need at least one driver source!
Running "depmod -ae"...
Failed to install the driver.
Look through "/var/log/airdriver" for errors.

```

When I run sudo airdriver-ng kernel it gives me this:

```

Found following stacks in the Kernel:

Found following drivers in the Kernel:

```

And the contents of /var/log/airdriver:

> 
Fri Mar 13 02:06:52 NZDT 2009
Installing "Intel Pro Wireless 4965 A/B/G/N" on 2.6.27-13-generic.
Fri Mar 13 02:12:41 NZDT 2009
Installing "Intel Pro Wireless 4965 A/B/G/N" on 2.6.27-13-generic.


What am I doing wrong?



Help is appreciated :)

---

### Post by ru0n on 2009-05-01
same problem..

---

### Post by otaker on 2009-05-02
I've also stumbled into this. Can't get airdriver to install it either.
Tried to Install airdriver-ng install_stack 1, but it gave me some error message.
```
Stack "IEEE80211 Softmac" specified for installation.
Your current GCC version doesn't match the version your kernel was compiled with.
The build modules will probably not load into the running kernel.
find: `/usr/src/linux/net/': No such file or directory

Your kernel source is neither in "/lib/modules/2.6.27-7-generic/build" nor in "/usr/src/linux".
Trying with vanilla source. (May fail on heavily patched distributions.)
If it fails install your proper kernel source and rerun this script.

1. Getting the source...OK
2. Extracting the source...OK
mv: cannot stat `linux-2.6.27/net/ieee80211/softmac': No such file or directory
Directory "softmac" doesn't exist.
Running "depmod -ae"...
Failed to install the stack.
Look through "/var/log/airdriver" for errors.

```Ideas anyone?

---

