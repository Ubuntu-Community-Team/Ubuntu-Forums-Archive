---
title: "Mapping Drive for sharing"
date: 2009-12-02
forum: Networking &amp; Wireless
---

### Post by Plasma_Snake on 2009-12-02
I know this is one of the most commonly asked n00b question of all times but here it comes once again. How can I map my NTFS partition like a Network drive like in Windows for sharing purposes? It has been configured to be auto-mount at startup so will using the sharing option in the /media/<NTFS Partition> will do the trick? Current situation is this that when I switch my laptop to Ubuntu from Windows 7, the network places under my Vista desktop shows no other machine connected at all, I mean the laptop is not shown at all. How to rectify this situation? :confused:
When I try to do that sharing thing under the /media, I get this error message
> 'net usershare' returned error 255:net usershare add:cannot share path /media/Torrents as we are restricted to only sharing directories we own.
Ask the administrator to add the line "usershare owner only=false" to the [global]section of the smb.conf to allow this
Neva mind folks, got it running! But u can tell me the other methods to do the same, especially the NFS one.

---

