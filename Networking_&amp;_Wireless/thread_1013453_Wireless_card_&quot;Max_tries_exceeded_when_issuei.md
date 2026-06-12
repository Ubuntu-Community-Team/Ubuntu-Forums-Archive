---
title: "Wireless card: &quot;Max tries exceeded when issueing command&quot;"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by antisho on 2008-12-16
At random times when there's no wireless network nearby, a process called 'eth2' starts taking 99% CPU (eth2 is my wireless interface). I checked the kernel log and found:

```
kernel: [ 3452.079641] airo(eth2): Max tries exceeded when issueing command
...
kernel: [ 7920.629645] airo(eth2): Max tries exceeded when issueing command
```

At that point, I removed the Cisco wireless card, and the screen froze, with the caps lock and scroll lock lights blinking. When I restarted, everything was fine.

What causes this? What can I do?

---

