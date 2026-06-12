---
title: "MythVideo doesn't recognize non-english files"
date: 2010-10-31
forum: Mythbuntu
---

### Post by rk86 on 2010-10-31
In the /var/lib/mythtv/video  I have nfs mounts to my server shares with movies.

The problem is that the MythVideo scanning ignores all files/directories with not english encoding (russian, utf-8 in my case).

These files are displayed properly in the xfce file manager, console, etc.

It was working properly in 9.04, and my guess the problem is related to the metadata parser in Mythbuntu 10.10.

Any advice?

---

### Post by jms-ubuntu-en on 2010-11-01
I had similar problem with .24's MythMusic, it failed to play files with scandinavian ( utf8 ) characters on my frontend. Music archive is mounted as a nfs4 at frontend from backend server. 

I tried to rescan music archive from frontend's ui, but any of the abovesaid files were not included. 
As a workaround I did the scan on my backend server (where the archive is physically located) and after that all the files were included and also playable on frontend.

I can remember that this problem didn't exist at least for a couple of weeks ago (with .24).

---

### Post by rk86 on 2010-11-01
Hi jms-ubuntu-en,

In my case I am doing it on the same machine (frontend + backend) with nfs shares from my Freebsd server.

I don't think the problem has connection to nfs mounts since all english (latin characters)  files are displayed and played fine from the same mount.

Thank you,

Alex

---

### Post by rk86 on 2010-11-07
To answer my own question - the reason and solution is here:

[https://bugs.launchpad.net/mythbuntu/+bug/541042](https://bugs.launchpad.net/mythbuntu/+bug/541042)

---

