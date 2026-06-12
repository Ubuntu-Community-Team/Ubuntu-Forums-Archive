---
title: "Network disconnected. You are now offline."
date: 2010-11-19
forum: Networking &amp; Wireless
---

### Post by wi0 on 2010-11-19
Hello all,

The title message appears when I log in.
Neither wired nor wireless network adapters show in ifconfig output.
Network manager shows a simple networking disabled greyed out message.
Both adapters work in live cd boot.
Everything was working properly before; I'm not sure what happened.

Thanks!

---

### Post by wi0 on 2010-11-20
I like how google shows this post as the third result for this particular error message. Hopefully a solution can be added here so that those running the search wouldn't be disappointed (and so that I can stop booting from a live cd). ;)

---

### Post by spiky001 on 2010-11-20
Did network only work onlive cd? or have you had it working when installed

---

### Post by wi0 on 2010-11-20
Everything was working before and now it's OK again. Thanks for wanting to help.

Here's what worked for me:

Like I said, the error message appears on boot with no adapter showing in ifconfig.

Left clicking network manager doesn't help, but right clicking the icon brings up a menu where "enable networking" can be chosen.

Once that option is enabled the error message appears again. This is misleading because it makes one think that nothing happened, but **now ifconfig does show the adapters**.

A quick sudo ifconfig wlan0 up, and everything is working again.

---

