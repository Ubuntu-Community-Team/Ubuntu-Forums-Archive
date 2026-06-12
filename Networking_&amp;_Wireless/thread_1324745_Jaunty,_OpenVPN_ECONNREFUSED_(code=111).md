---
title: "Jaunty, OpenVPN ECONNREFUSED (code=111)"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by sitush on 2009-11-12
Really sorry to have to post this but I cannot seem to find an answer despite hours and hours of searching. Doubtless someone can point me in the right direction and I'll look like an idiot!

I've built a test install using Jaunty/9.04 desktop, fully up to date as of today. I've recently been playing with OpenVPN with the Jaunty box as server and connecting via a Windows XP Pro SP3 system as client (client using OpenVPN GUI). Set up as routed rather than bridged, pretty much using the sample conf files except for change of server names (ie: 10.8.0.0, port 1194, UDP etc are left as provided in the samples).

Worked ok for a few hours and then stopped working. Openvpn.log shows a mis-match between local and remote hashes and "UDPv4 [ECONNREFUSED]: Connection refused (code=111)".Pinging 10.8.0.1 works ok but the GUI on the XP machine now stays in its yellow state rather than turning green and reporting the IP in a bubble.

The ONLY thing that had changed was I uncommented ";crypto=BF-CBC" in the previously working conf files at both server and client. But commenting them out again does not resolve the error which appeared at that point. Still failed after an /etc/init.d/openvpn restart and even after rebooting both server and client machines before trying again. Even with the logging altered to the most verbose ~(9) I cannot make sense of this.

I can provide the conf files and the logs, obviously, and am happy to do so if it would help. I could also start from scratch ... but that rather defeats the point of testing something out as clearly I have hit some sort of problem.

In fact, it is the abundance of postings of logs that has probably created my search problem: the phrases are common but the solutions seem to be irrelevant! Like I said, I'm probably missing the obvious here but I am definitely getting very frustrated!

Any advice would be much appreciated.

---

### Post by sitush on 2009-11-13
Sorted. For reasons unknown, my NICs reversed their settings and this blew away the port forwarding on the firewall. Weird, since they're on static IPs, and even more so that it should happen just when I alter a conf file setting ... but all appears to be ok now & I can resume testing that which I really intend to test.

---

