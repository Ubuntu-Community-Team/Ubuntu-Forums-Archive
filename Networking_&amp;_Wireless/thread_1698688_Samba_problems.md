---
title: "Samba problems"
date: 2011-03-02
forum: Networking &amp; Wireless
---

### Post by Z.K. on 2011-03-02
I had my Samba server working or I thought I did.  I could see the server in Windows, but using CloneZilla on a USB drive or from Ubuntu work station, I cannot see the server or its file shares.  So, I decided to start over and replaced the smb.conf file with the default one.

To my surprise Windows can still see and access the file share.  Why is that.  I thought that was what Samba was for to let Windows see Linux file shares.  Yet it seems Windows does not need it.

My other question is how do I get another Linux station to see the file shares on the Linux Server?  Do I need to install nfs or can I use Samba?

I am thinking I need to use nfs, but I have seen some references to only using Samba.


:(

---

### Post by Z.K. on 2011-03-26
> **Z.K. said:**
> I had my Samba server working or I thought I did.  I could see the server in Windows, but using CloneZilla on a USB drive or from Ubuntu work station, I cannot see the server or its file shares.  So, I decided to start over and replaced the smb.conf file with the default one.

To my surprise Windows can still see and access the file share.  Why is that.  I thought that was what Samba was for to let Windows see Linux file shares.  Yet it seems Windows does not need it.

My other question is how do I get another Linux station to see the file shares on the Linux Server?  Do I need to install nfs or can I use Samba?

I am thinking I need to use nfs, but I have seen some references to only using Samba.


:(


I got samba working finally.  It ended up being that samba was not starting up automatically at boot.  So, put the command "restart nmbd" and restart "smbd" in the rc.local file and now it works fine.  Eventually, I will look into why it does not start up, but for now it is working.

:)

---

