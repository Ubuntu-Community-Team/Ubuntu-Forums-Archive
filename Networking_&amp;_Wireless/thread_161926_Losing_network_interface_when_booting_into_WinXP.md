---
title: "Losing network interface when booting into WinXP"
date: 2006-04-18
forum: Networking &amp; Wireless
---

### Post by mjh007 on 2006-04-18
Hi there

I was wondering if anyone had a similar problem. It seems that after booting into windows, I lose my network interface.

I then follow the Sticky about Wired ethernet troubleshooting and eventually get it back with much trial and error.

Some info: I'm using Dapper on an IBM Thinkpad R51 with a wired network - I don't use the wireless at the moment.

It would seem that windows overwrites something when I log in to it and that messes up the network in Ubuntu.

Thanks in advance.

---

### Post by AndrewB on 2006-04-18
My business computer runs XP pro with our apps running over a Novell client network. After running Dapper flight 6 Live. I lost all Novell connectivity, but not basic tcp. The solution was reinstalling Novell's Client.

I'd like to get Ubuntu running at work to avoid the severe proliferation of at work viruses. Can't really afford the time to mess with the client repeatedly.

Andrew

---

### Post by ivansv on 2006-04-18
check which driver is installed and make sure it ends in .inf, otherwise it won't work.
windows wireless setups come with other driver extensions, .sys .cat, but they won't work you need the .inf extension. go to device hardware and check which driver is installed.

---

