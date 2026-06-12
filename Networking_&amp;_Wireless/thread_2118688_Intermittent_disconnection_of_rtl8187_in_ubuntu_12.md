---
title: "Intermittent disconnection of rtl8187 in ubuntu 12.04 64bit"
date: 2013-02-21
forum: Networking &amp; Wireless
---

### Post by rolandpish on 2013-02-21
Hi, I recently switched from linuxmint debian edition to ubuntu 12.04 and I am experimenting wireless intermittent disconnections.

The amount of time that passes before getting disconnected is very random: sometimes it takes 3-4 hours, sometimes it takes 15-20 minutes, etc.

I was able to look at /var/log/syslog and the following is part of the output of the exact time when the connection drops:

Feb 21 14:45:17 msibox kernel: [28921.840952] rtl8187: wireless radio switch turned off
Feb 21 14:45:17 msibox kernel: [28921.939953] wlan0: deauthenticating from c9:3b:34:48:a5:f0 by local choice (reason=3)
Feb 21 14:45:18 msibox kernel: [28922.424501] cfg80211: All devices are disconnected, going to restore regulatory settings
Feb 21 14:45:18 msibox kernel: [28922.424508] cfg80211: Restoring regulatory settings
Feb 21 14:45:18 msibox kernel: [28922.424525] cfg80211: Calling CRDA to update world regulatory domain
Feb 21 14:45:19 msibox kernel: [28923.514600] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Feb 21 14:45:19 msibox kernel: [28923.514605] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
... (long output)

Is there something I can do for avoiding these intermittent disconnections?

I would really appreciate any help on this issue.

Thanks in advance.

PS: I never had this problem in linuxmint.

---

### Post by arthurborsboom2 on 2013-09-01
I am experiencing the same issues on Lubuntu x64. Did you find a solution?

---

### Post by rolandpish on 2013-09-02
Hi arthurborsboom2. Unfortunately, I wasn't able to solve the problem. I recall trying everything I found in this and other forums, but the problem persisted. I even installed the linux-wireless driver for my usb dongle and I experienced the same.
Since I didn't plan to spend more money buying a usb dongle of another brand (with the probability to experience the same issue) I ended up with a wired connection between my router and the computer.

If you get to solve it, please let me know. I am also dying to know if there is a solution for this problem :)

---

### Post by varunendra on 2013-09-03
> **arthurborsboom2 said:**
> I am experiencing the same issues on Lubuntu x64. Did you find a solution?

Welcome to the Forums arthurborsboom2 !

Are you sure you are using the same driver? You can confirm that with the output of command -
```
lspci -nnk | grep -iA2 net
```

If yours is a different card/driver, please start your own thread and post your question with details of the problem.

@rolandpish,
Did you also try the proprietary driver from realtek?

It may help if we can get more info about your wireless setup. You may generate a detailed diagnostics report by running "wireless_script" (courtesy Wild Man) which you can find in the "Wireless Script" link in my signature.

---

### Post by rolandpish on 2013-09-03
> **varunendra said:**
> 

@rolandpish,
Did you also try the proprietary driver from realtek?

It may help if we can get more info about your wireless setup. You may generate a detailed diagnostics report by running "wireless_script" (courtesy Wild Man) which you can find in the "Wireless Script" link in my signature.

Yes, I also tried with the proprietary driver from realtek and it seemed to work a bit better but I still experienced intermittent disconnection.
Once I get home I will download the Wireless Script and post the diagnostics here.

Thanks a lot!

---

