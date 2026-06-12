---
title: "Samba network activity monitor?"
date: 2009-04-22
forum: Networking &amp; Wireless
---

### Post by dbsoundman on 2009-04-22
I'm looking for a command that I can run in the terminal which will allow me to monitor activity on my samba shares, i.e. users reading/writing information, things like that. I want to use this command inside of a little desktop screenlet I have which automatically runs and shows the output of a command. Anyone know what I can run to show this info?

Thanks,
Dan

---

### Post by Keneo on 2009-09-29
try

sudo watch smbstatus

there is even a 'watch' screenlet already, 
but you might want to parse the output of the command first, since it's a bit long...

---

### Post by cybercity@localhost on 2011-03-24
> **Keneo said:**
> try

sudo watch smbstatus

there is even a 'watch' screenlet already, 
but you might want to parse the output of the command first, since it's a bit long...

how can we kick users?

---

