---
title: "Ubuntu computer doesn't show up in Windows Network"
date: 2011-08-18
forum: Networking &amp; Wireless
---

### Post by WikedX on 2011-08-18
I'm on Windows 7 64bit and Ubuntu 11.04 64bit

Windows is on a net book with not so much hard drive space so I want to keep all my music and movies on my hard drive of my Ubuntu desktop. When I try to find my Ubuntu machine I get nothing though

Here is what I've tried
-Manually configuring Samba
-Right clicking folders and hitting the share button
-Using the share tool with "shares-admin"

No matter what though, Win7 simply will not see it on the network. Not even when I run "\\ipadress\"

If anything is there away to delete everything related to Samba and start over?
If not, what else can I do to try and fix this?

---

### Post by kerry_s on 2011-08-18
Uninstall samba & reinstall, you only need to right click share folder, nothing else.

---

### Post by WikedX on 2011-08-18
> **kerry_s said:**
> Uninstall samba & reinstall, you only need to right click share folder, nothing else.

Except I tried that and I'm still getting nothing.

I tried each of those methods separately

---

### Post by pjd99 on 2011-08-18
How is your windows networking set up? Are you using Homegroups (default I think in Win7). These aren't compatible with previous versions of Windows, let alone Ubuntu.

If using legacy networking disregard this post.

---

