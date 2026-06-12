---
title: "Problem sending photo from phone via Bluetooth"
date: 2009-09-06
forum: Networking &amp; Wireless
---

### Post by alexeix on 2009-09-06
Hi,

Using Jaunty 32bit, when attempting to send a photo to my PC from my mobile phone (Nokia N70), the message "sending failed" is displayed.

Both the the PC and phone have Bluetooth enabled, the devices have been correctly paired and they are visible.
The phone is set as a trusted device in Ubuntu and the PC is set as authorised in the phone. Automatic connection is allowed too.

I've tried the default Bluetooth manager, but without success, so I subsequently installed Blueman, however, the same problem occurs.

In Blueman, I've checked the available services for the phone and made sure that 'File Receiving (Object Push)' is set to Enabled=Yes and 'Accept Files From Trusted Devices'=Yes.

I cannot think what else could be causing this problem, but have found a lot of people reporting issues with Bluetooth.

Any suggestions?

---

### Post by walmis on 2009-09-07
try running these commands to get a debug log:
```

$ killall obex-data-server
$ obex-data-server -ng

```Then try to send a file, after it fails, copy everything from the terminal and post here.

---

### Post by alexeix on 2009-09-07
Thanks for that suggestion.

I logged on to do what you suggested and thought I'd try sending a file one more time.
Hey presto, it worked!  I have no idea why.

Maybe the phone or PC needed to be re-booted for something to take effect?!?
I can only guess, but I hadn't changed the Bluetooth settings since the last time I tested.

Anyway, all sorted now.
Thanks again!

---

