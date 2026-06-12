---
title: "Wireless won't activate after coming out of sleep/lock."
date: 2012-10-26
forum: Networking &amp; Wireless
---

### Post by kenmore on 2012-10-26
I'm running Ubuntu 12.10 with Gnome3 on my Gateway FX-6860 laptop.

Whenever my computer locks, whether manually or because I leave it alone for awhile, I can't connect to my wireless network. If I restart it works again. Any ideas? Thanks.

Edit: Clicking the lock button from the menu doesn't actually do anything. I have to close my laptop to lock it. I also wanted to mention, it's not that I can't connect to wireless, I can't even turn wireless on. If I click the on button it immediately goes back to off. My wireless switch is in the on position and I've tried toggling the function key for wireless. 

It's not an immediate problem because I can just restart but it's rather annoying to have to restart every time my laptop falls asleep.

---

### Post by Gadgetech on 2012-10-27
The following has worked for me on previous versions of Ubuntu and Linux Mint. I haven't loaded 12.10 onto my laptop yet, but it should work.

```
sudo touch /etc/pm/power.d/wireless
```

After that your wifi card should work again when coming out of sleep.

---

### Post by kenmore on 2012-10-27
> **Gadgetech said:**
> The following has worked for me on previous versions of Ubuntu and Linux Mint. I haven't loaded 12.10 onto my laptop yet, but it should work.

```
sudo touch /etc/pm/power.d/wireless
```

After that your wifi card should work again when coming out of sleep.

That seems to have done the trick. Thanks a million.
Any idea *whyyy* that works, though?

---

### Post by Gadgetech on 2012-10-27
I *think* it's telling the power management system to re-initialize the wifi card when you resume from sleep. But that's just my best guess.

---

