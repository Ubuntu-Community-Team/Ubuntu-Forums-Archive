---
title: "Windows Network browsing not workiing"
date: 2009-05-24
forum: Networking &amp; Wireless
---

### Post by kaelistus on 2009-05-24
Hi everyone

I just installed Ubuntu 9.04 after years of using Gentoo. It's really nice, but I'm having some networking issues that I can't solve by myself.

When I select browse the network I get the icon for "Windows Network" but when I select that, no workgroup shows up. I also cannot browse through a computer's share by selecting connect through server.

However, If I actually pick a windows shared folder by using connect through server, I can browse through my files just fine - I just can't see what shared folders/computers are available. When I type in smbtree I correctly get the full list of workgroups computers and shares.

On the windows side of things, I can see my Ubuntu machine, it's shares, as well as the other windows computers as expected.

Does anyone have an idea why this would happen?

---

### Post by Iowan on 2009-05-24
You can try editing the "workgroup=" line in */etc/samba/smb.conf*, then restarting Samba.  I haven't stayed current as Samba evolves, so it may not help.  I back up the config file before I make any edits... just in case.

---

### Post by kaelistus on 2009-05-24
I did. The Workgroup line in smb.conf has the correct workgroup. I can see all the computers through the command line (smbtree), I just don't see them through the Nautilus file browser.

---

