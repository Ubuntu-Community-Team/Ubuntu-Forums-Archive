---
title: "wireshark interface issues in ubuntu"
date: 2009-03-27
forum: Networking &amp; Wireless
---

### Post by squeabs on 2009-03-27
I downloaded Wireshark from the repositories. When I fired it up and looked for interfaces to capture from, I found none. When I typed in the interface I'm using, I got an error message saying that I may not have the privileges to do so. Anyone know what's going on or how to give Wireshark the privileges to do this?

---

### Post by redmk2 on 2009-03-27
> **squeabs said:**
> I downloaded Wireshark from the repositories. When I fired it up and looked for interfaces to capture from, I found none. When I typed in the interface I'm using, I got an error message saying that I may not have the privileges to do so. Anyone know what's going on or how to give Wireshark the privileges to do this?

You have to run Wireshark as root.  To do that you can do Alt+F2 then type **gksudo wireshark ** in the box.  I made a launcher under Applications >> System Tools for Wireshark as root.

---

### Post by squeabs on 2009-03-27
Thanks.

---

