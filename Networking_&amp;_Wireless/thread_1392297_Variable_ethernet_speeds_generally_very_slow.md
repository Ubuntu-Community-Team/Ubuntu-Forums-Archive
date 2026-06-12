---
title: "Variable ethernet speeds generally very slow"
date: 2010-01-27
forum: Networking &amp; Wireless
---

### Post by daveuu on 2010-01-27
Hi

Transferring files between 2 ubuntu boxes starts moderately fast but slows to a crawl.

Machines: Ubuntu 9.10 AthlonX2 5800+ 4GB RAM SATA 3Gb/s 1Gbps nVidia Corporation MCP77 Ethernet wired, RaLink RT2561/RT61 802.11g wireless to AthlonX2 4800+ 4GB RAM SATA 3Gb/s Realtek 1Gbps (2 interfaces, can't remember chipsets off hand).

Over the wire (direct link): starts ~20-40MB/s for several GB then slows to 400 kB/s for several hours then may pick up again to ~20MB/s then fluctuates but stays low for long periods.

Wireless from first box to Buffalo openWRT router then wired to box B: follows a similar pattern to above but starts ~1.5 MB/s and drops to 40 kB/s.

I think the hardware is up to it as acceptable speeds are reached but strangely, regardless of interfaces, with/without router, for long periods, it crawls at 40 or 400 kB/s (wireless, wired respectively) Coincidence that there's a x10 difference?

I'd like sustained speeds at 20+MB/s over gigabit LAN and 1.5++ MB/s over wireless (should this be higher anyway?). But I'm stumped as to what is throttling it. Suggestions very welcome. Thanks

daveuu

---

