---
title: "Can no longer connect to WHS Samba share - please help"
date: 2011-06-01
forum: Networking &amp; Wireless
---

### Post by scylla2 on 2011-06-01
I'm running 10.10 on a pretty fresh install with a brand new system I built especially for Ubuntu.

For some reason, I'm beginning to have trouble with accessing my Samba shares from this computer. I have a Windows Home Server also running on my network and I have to be able to access the files on it.

At first Nautilus showed "SERVER" in the folder tree when I clicked on "Network" and everything was working great. A couple of days ago my WHS "SERVER" suddenly no longer showed up in Nautilus and I had to mount the WHS server manually (via "Connect to Server...").

Now, today, even that doesn't work. When I try to mount manually I get the error "Failed to Retrieve Share List from Server". I can now no longer access the WHS from Ubuntu at all.

Why has my ability to access the Samba shares on my WHS deteriorated over time to the point where I can't access them at all?? Any ideas?

I have other systems on this network (Mac and Windows) and none of the others have any problems at all with the WHS. Re-booting WHS and router has no effect. I've changed nothing in my set-up. Is this update related?

---

### Post by capscrew on 2011-06-01
> **scylla2 said:**
> I'm running 10.10 on a pretty fresh install with a brand new system I built especially for Ubuntu.

For some reason, I'm beginning to have trouble with accessing my Samba shares from this computer. I have a Windows Home Server also running on my network and I have to be able to access the files on it.

At first Nautilus showed "SERVER" in the folder tree when I clicked on "Network" and everything was working great. A couple of days ago my WHS "SERVER" suddenly no longer showed up in Nautilus and I had to mount the WHS server manually (via "Connect to Server...").

Now, today, even that doesn't work. When I try to mount manually I get the error "Failed to Retrieve Share List from Server". I can now no longer access the WHS from Ubuntu at all.

Why has my ability to access the Samba shares on my WHS deteriorated over time to the point where I can't access them at all?? Any ideas?

I have other systems on this network (Mac and Windows) and none of the others have any problems at all with the WHS. Re-booting WHS and router has no effect. I've changed nothing in my set-up. Is this update related?

What happens if you use "Connect to Server" with the server's IP address?

---

