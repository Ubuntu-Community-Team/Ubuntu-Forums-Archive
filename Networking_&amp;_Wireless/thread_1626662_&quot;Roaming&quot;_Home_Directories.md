---
title: "&quot;Roaming&quot; Home Directories"
date: 2010-11-20
forum: Networking &amp; Wireless
---

### Post by Atomic Fusion on 2010-11-20
I have several Ubuntu installs, including one on a flash drive. I also have a server. I want to sync my home directories from all my client installs onto my server.
What I want is really a combination of two things:
Unison, which enables me to work without a network connection.
An SFTP filesystem so that changes are immediatly sent to the server, not JUST at login and logout, which makes login and logout extremely slow.
Is there any combination I could use? Could I make unison sync extremely frequently? Any other suggestions would be appreciated as well!

Thanks,
Stephen

---

### Post by headvampyre@hotmail.co.uk on 2010-11-21
you could probably do this with NFS actaully, by mounting an nfs share to /home after cpoying your data out and then copying it back to the server.

---

### Post by Atomic Fusion on 2010-11-26
Is this unique to NFS, or could I do it with SFTP?

---

