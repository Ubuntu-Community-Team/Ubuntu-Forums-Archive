---
title: "Digital Media Connection (well, lack of)"
date: 2010-01-18
forum: Multimedia Software
---

### Post by Mahngiel on 2010-01-18
I've trolled the forums for about 30 mins or so already looking this up, but can't seem to find any solutions.  Most threads seem to end with either a "report to launchpad" or they just end without resolution.  So in case I've missed a solved thread:

Plugging my Kodak C503 in gives inability to mount due to lock issues, the infamous -60 lockout.  However, I get TWO icons in metacity, neither are mounted/will mount.  Turning the cam off removes both, and I can't get down to only one.  Not sure if this is because it's reading the camera's internal memory + my SD card.

So, I pulled the SD card out, and jacked it into my card reader in my lappy... no dice.  In fact, none of my SD cards work; leading me to believe I need to find drivers for it.

I've scowered the forums and howto's, but... no dice.  Any help will be greatly appreciated.

Notes: (1)It's a Pavillion ZD7000 (2)nothing pops up in fdisk (3)I really don't want to load up windows

---

### Post by cariboo on 2010-01-18
What's the output of dmesg, when you plug your device in? You can view dmesg either in a terminal or by going to System--> Administration-->Log viewer. If you could paste the last ten line in you next post, we may be able to help. In a terminal type:

```
dmesg | tail -n10
```

or copy and paste from the log viewer.

---

### Post by Mahngiel on 2010-01-18
With SD card in reader:
```

king@mahngiel:~$ dmesg | tail -n10
[   50.684221] wlan0: associated
[   50.685589] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   60.991273] wlan0: no IPv6 routers present
[  581.632025] __ratelimit: 3 callbacks suppressed
[  581.632030] ACPI: EC: missing confirmations, switch off interrupt mode.
[  582.132025] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] 20090521 evregion-424
[  582.132046] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPC0.EC0_.PRTH] (Node df83f504), AE_TIME
[  582.132083] ACPI Error (psparse-0537): Method parse/execution failed [\_TZ_.THRM.CHTR] (Node df841af4), AE_TIME
[  582.132109] ACPI Error (psparse-0537): Method parse/execution failed [\_TZ_.THRM.CHTH] (Node df841b08), AE_TIME
[  582.132133] ACPI Error (psparse-0537): Method parse/execution failed [\_TZ_.THRM._TMP] (Node df841b94), AE_TIME

```

With Camera:
```

king@mahngiel:~$ dmesg | tail -n10
[   60.991273] wlan0: no IPv6 routers present
[  581.632025] __ratelimit: 3 callbacks suppressed
[  581.632030] ACPI: EC: missing confirmations, switch off interrupt mode.
[  582.132025] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] 20090521 evregion-424
[  582.132046] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPC0.EC0_.PRTH] (Node df83f504), AE_TIME
[  582.132083] ACPI Error (psparse-0537): Method parse/execution failed [\_TZ_.THRM.CHTR] (Node df841af4), AE_TIME
[  582.132109] ACPI Error (psparse-0537): Method parse/execution failed [\_TZ_.THRM.CHTH] (Node df841b08), AE_TIME
[  582.132133] ACPI Error (psparse-0537): Method parse/execution failed [\_TZ_.THRM._TMP] (Node df841b94), AE_TIME
[ 2696.311046] usb 3-2: new full speed USB device using uhci_hcd and address 2
[ 2696.497201] usb 3-2: configuration #1 chosen from 1 choice

```

---

