---
title: "Ventrilo port 6100 forwarding problem."
date: 2010-09-05
forum: Networking &amp; Wireless
---

### Post by em3raldxiii on 2010-09-05
It seems I am not the only person to have encountered this problem, but I have not been able to resolve it.

Setup:
Ubuntu 10.04 with very few modifications
Ventrilo 3.03 server software running
Router is Asus RT-N16 with DD-WRT recently flashed.

Problem:
Prior to flashing my router with DD-WRT I had the ventrilo server running fine, people could access it from outside my LAN, and I could access it using the internal IP.

After flashing with DD-WRT, I port-forwarded ports 3784 (UDP+TCP) and 6100 (UDP+TCP)

With this setup, Ventrilo is not accessible outside my internal network.  Users can see with the Vent client that the server is available, but attempts to connect are not successful.  I believe they get "synchronising" which hangs.

Upon some troubleshooting, I visited [www.canyouseeme.org](www.canyouseeme.org) and tried my ports.  3784 was successful, but port 6100 was not.  I attempted to use the Port Triggering options, the port-range forwarding option, disabling the firewall, disabling SPI, etc.  In various configurations 3784 was happily open, but 6100 remained closed in every scenario.  Or at least, canyouseeme.org was unsuccessful at communicating on 6100.  Oh and I tried various hardware reboot options, and rebooting the server, etc.

What I have not tried:
-Disconnecting my router and connecting directly.  I am fairly convinced that my ISP did not spontaneously begin blocking port 6100 on the same day that I flashed my router.

Comments:
I realize that this is more likely a dd-wrt problem, but reviewing the forum over there is ... an exercise in frustration.  A lot of misunderstanding, misdirection, and 'dismissal' of the problem.  What I am appealing to here is, hopefully, someone who has actually encountered this specific problem, and has actually committed a *workable* solution.  One of the things that frustrates me is on one of the forums I read the whole thing because it was marked *solved*, it all looked promising!  Then at the bottom, the solution was that someone bought a new computer.  That is not a solution!!  ROFL!

Of course, for the benefit of all readers, any suggestions are welcome!

---

### Post by cariboo on 2010-09-05
Please ask support questions in the support forums. Moved.

---

