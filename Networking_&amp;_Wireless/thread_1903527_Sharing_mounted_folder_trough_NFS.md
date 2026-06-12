---
title: "Sharing mounted folder trough NFS"
date: 2012-01-02
forum: Networking &amp; Wireless
---

### Post by StevenStip on 2012-01-02
Hi,

I have this 150 gb ubuntu 10.04 partition and I have shared my video's folder in my home directory to access it somewhere else trough nfs.
Basically I did:
```
sudo apt-get install nfs-kernel-server

```then
```
sudo vim /etc/exports
```
Added:
/home/user/Videos *(ro)
then restarted the service and I can access the folder trough nfs on a Boxee, problem now is... there is only 150 gb and I need MOAR.
so... another disk 1 tb this time, with a ntfs(yeah yeah I know) so I added 
/media/Backup/movies *(ro)
to the file.
But this folder isn't browsable by the other devices now. It is advertised on the server tho. Does anyone know what I'm doing wrong and how to fix it?

kind regards,
Steven

---

