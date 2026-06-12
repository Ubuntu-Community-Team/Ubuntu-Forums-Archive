---
title: "[SOLVED] Live frontend can't connect to the master backend"
date: 2007-10-29
forum: Mythbuntu
---

### Post by lfuzzy on 2007-10-29
I am trying Mythbuntu Live CD frontend on a different machine. The test was sucessful connecting to MySQL in the setup program. But when I click Watch TV, I got,

"Could not connect to the master backend server -- is it running? Is the IP address set for it in the setup program correct?"

---

### Post by superm1 on 2007-10-29
> **lfuzzy said:**
> I am trying Mythbuntu Live CD frontend on a different machine. The test was sucessful connecting to MySQL in the setup program. But when I click Watch TV, I got,

"Could not connect to the master backend server -- is it running? Is the IP address set for it in the setup program correct?"
Your backend is not configured for remote access properly,.  Go into mythtv-setup on that backend and be sure to put in an IP address in both boxes of general that is not a loopback address.

---

### Post by lfuzzy on 2007-10-30
> **superm1 said:**
> Your backend is not configured for remote access properly,.  Go into mythtv-setup on that backend and be sure to put in an IP address in both boxes of general that is not a loopback address.

Thanks. It connects now.

---

