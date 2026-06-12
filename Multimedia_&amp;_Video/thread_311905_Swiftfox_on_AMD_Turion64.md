---
title: "Swiftfox on AMD Turion64"
date: 2006-12-03
forum: Multimedia &amp; Video
---

### Post by hakan69 on 2006-12-03
Sorry if I'm in the wrong forum. If so, please redirect me. 
I mailed this to the Automatix Team:
[I]I run Edgy on a AMD Turion 64, and I installed Swiftfox 2.0 and its plugins with Automatix2. Installation seemed OK, but when I tried to run SR Webradio I got message "could not find hxplay or realplay in the system path to use as an embedded player" On the other hand Flash seenmed to work. As Automatix installed Swiftfox and plugins in /opt, the problem was solved by adding ":/opt/realplayer" to /etc/environment.
Perhaps this correction of the system path should be added to the installation script (?)[/I]
The Team Lead answered: *I have no way to test this since I dont have an amd64 machine but if somehow this fix gets confirmed by other users, I will add it to upstream AX2. Can you post this on the ubuntu forums and check if it works for others?*
Thus I post it, and hope for confirmation.

---

### Post by arnieboy on 2006-12-03
just to add: 
:/opt/realplayer needs to be added to "PATH" in /etc/environment

---

