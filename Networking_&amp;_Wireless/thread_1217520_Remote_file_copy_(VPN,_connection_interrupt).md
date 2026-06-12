---
title: "Remote file copy (VPN, connection interrupt)"
date: 2009-07-19
forum: Networking &amp; Wireless
---

### Post by ear9mrn on 2009-07-19
I have two machines connected via OpenVPN and regularly copy large files (>300mb) via ftp. Unfortunately the connection drops occasionally and the copy fails. When the connection comes back OpenVPN reconnects but I have to repeat the copy of the file if it did not complete. I am looking for a way to copy files that could resume after reconnection. I have NFS drives shared across OpenVPN as well if that would help, I tried a couple of times just doing a "CP" but that seemed very slow and unreliable. I thought of using a torrent a approach but that seems a bit of overkill.   

I thought of SCP, RSYNC but neither of these offer resume functions as far as I am aware either.

Thanks,

Pete.

---

