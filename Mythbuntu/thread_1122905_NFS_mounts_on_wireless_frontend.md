---
title: "NFS mounts on wireless frontend?"
date: 2009-04-11
forum: Mythbuntu
---

### Post by rubrboots on 2009-04-11
Hello, I have a backend that serves 2 wired frontends. For wired frontends I edit the /etc/fstab file so that the videos and music folders on the backend are mounted in the corresponding folders on the frontend. This allows me to access music and videos as if they were actually on the frontend.

I have recently made a frontend out of an old laptop which connects to the local network via wifi. The wireless frontend works prefectly for watching recorded shows, but not for videos and music. During boot the NFS mount fails because the network manager has not yet connected to the wireless router.

Is there a way to mount these shares after a connection has been established? Or to instruct the frontend to mount without verifying the connection? Or a better method of achieving the same goal?

---

### Post by nickrout on 2009-04-11
> **rubrboots said:**
> Hello, I have a backend that serves 2 wired frontends. For wired frontends I edit the /etc/fstab file so that the videos and music folders on the backend are mounted in the corresponding folders on the frontend. This allows me to access music and videos as if they were actually on the frontend.

I have recently made a frontend out of an old laptop which connects to the local network via wifi. The wireless frontend works prefectly for watching recorded shows, but not for videos and music. During boot the NFS mount fails because the network manager has not yet connected to the wireless router.

Is there a way to mount these shares after a connection has been established? Or to instruct the frontend to mount without verifying the connection? Or a better method of achieving the same goal?

in /etc/rc.local add a line

```
mount -a
```

it will be executed after all other startup scripts.

---

### Post by oobe-feisty on 2009-04-12
change your /etc/fstab mounts

so each nfs share mount contains the line noauto

the do what the nickrout said that will work ok.

---

### Post by rubrboots on 2009-04-12
Great! that worked thank you.

---

