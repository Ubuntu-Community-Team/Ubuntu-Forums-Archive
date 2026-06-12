---
title: "DHCP relay &amp; option 82"
date: 2009-02-16
forum: Networking &amp; Wireless
---

### Post by Leebria on 2009-02-16
Can someone please explain to me how the 'match if binary-to-ascii' line for dhcp and option 82 works? I'm running a dhcp3 server on 8.10 and am having a heck of a time trying to get it to match the agent.remote-id. My relay agent is appending the information.

The line in my config file is such:
match if binary-to-ascii(16, 8, ":", option remote.agent-id) = "00:11:22:33:44:55";

I'm running wireshark to verify option 82 information is being properly appended, which it is, and I'm seeing a value in the remote.agent-id field as 001122334455, no colons. Could the ":" delimiter be whats causing it to fail to match?

---

