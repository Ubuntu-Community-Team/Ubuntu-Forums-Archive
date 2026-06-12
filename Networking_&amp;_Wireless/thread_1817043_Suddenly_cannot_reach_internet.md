---
title: "Suddenly cannot reach internet"
date: 2011-08-02
forum: Networking &amp; Wireless
---

### Post by Odyssey1942 on 2011-08-02
I used my computer this morning before leaving for the office, but when I returned this evening, I am unable to reach the internet. Also the light on the mobo where the ethernet cable is plugged in is steady yellow.

My limited experience would tell me it is a hardware failure, but it seems so strange with nothing happening during the day. How might I best diagnose the problem from within Ubuntu (10.04)?

---

### Post by wildmanne39 on 2011-08-02
Hi, with your light being yellow it looks like a hardware failure, or maybe it got turned of in the bios.

When your computer starts look at the screen and it will tell you which button to hit to enter setup, and then look for your lan and make sure it is set to on.

I am not an expert on network issues so someone might have a better idea.

---

### Post by Odyssey1942 on 2011-08-02
In BIOS, the 'Onboard Devices Configuration' screen shows:

Onboard LAN [Enabled], and
    Onboard LAN Boot ROM  [Disabled]

Is that normal, or should the latter be Enabled?

Thanks

---

### Post by Odyssey1942 on 2011-08-03
When I got up this morning, decided to swap the computer end of my ethernet cable to a known "internet good" computer when I tried pinging the router and got a reply. 

Had restarted the computer twice yesterday and the second time had not restarted my browser, so when the ping worked this morning, I opened the browser and lo, it reached the internet. Very strange. I expect that I now have an intermittent problem, but hopefully that will be a one-time event.

Expect me back, but in the meantime, thanks for all the great help!

---

### Post by dandnsmith on 2011-08-03
> **Odyssey1942 said:**
> In BIOS, the 'Onboard Devices Configuration' screen shows:
    Onboard LAN Boot ROM  [Disabled]
Is that normal, or should the latter be Enabled?

That setting is quite normal - only on if you want to boot from a boot-server machine

That intermittent connection sounds like:
*either* imminent failure of port
*or*  connection problem - cable and port not mating securely.

---

