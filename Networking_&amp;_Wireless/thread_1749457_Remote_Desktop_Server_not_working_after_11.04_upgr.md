---
title: "Remote Desktop Server not working after 11.04 upgrade with confirmation enabled"
date: 2011-05-04
forum: Networking &amp; Wireless
---

### Post by hotweiss on 2011-05-04
I just remotely updated my uncle's Ubuntu 10.10 desktop to 11.04. My uncle has no computer skills, so it is very important that I troubleshoot his problems using VNC.  After completing the 11.04 upgrade, I was not able to connect to him via VNC.  After some fiddling around I was able to connect by turning off the confirmation option in the Security section.  We are now using the password security option.  The problem is that my uncle does not have any security against my peering eyes.

I tried reinstalling Vinagre, but that didn't help. Is it possible to get the confirmation option working again somehow?

Is there a download link for Vinagre 3.01 (deb)?

---

### Post by julio prada on 2011-05-04
I installed 2 fresh Ubuntu 11.04 laptops.
First I was getting a "connection closed" message.
And there has a "Your desktop is only reachable... using the address *_localhost_*", after pressing "Configure network to automatically accept connections".
**Suddenly this message changed** to the IP address (192.168.9.102)
After this I could connect without problems and the Remote Desktop Viewer on the client PC showed its availability.
I feel it quite slow and screen is not refreshed even after refresh is issued, I wonder if Teamviewer is be better?

---

### Post by hotweiss on 2011-05-04
> **julio prada said:**
> I installed 2 fresh Ubuntu 11.04 laptops.
First I was getting a "connection closed" message.
And there has a "Your desktop is only reachable... using the address *_localhost_*", after pressing "Configure network to automatically accept connections".
**Suddenly this message changed** to the IP address (192.168.9.102)
After this I could connect without problems and the Remote Desktop Viewer on the client PC showed its availability.
I feel it quite slow and screen is not refreshed even after refresh is issued, I wonder if Teamviewer is be better?

Well I find that the speed has improved with Ubuntu 11.04.  Setting "Configure network automatically to accept connections" on didn't change anything.

---

### Post by kin37ik on 2011-05-05
i had the same problem earlier, ive found that if i turned off the option where the user has to allow or refuse connection to the ubuntu box that it worked, but only asking for a password and with always showing the icon

---

