---
title: "Samba Repos Down?"
date: 2009-10-02
forum: Networking &amp; Wireless
---

### Post by DeadlyAura on 2009-10-02
I just tried to share a folder on my Windows network and was prompted that I needed to install Windows network support. When trying to install I got the error:

```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.3.2-1ubuntu3.1_amd64.deb
  404 Not Found [IP: 91.189.88.46 80]


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/libpam-smbpass_3.3.2-1ubuntu3.1_amd64.deb
  404 Not Found [IP: 91.189.88.46 80]
```

So, I tried using terminal doing a:

```
sudo apt-get install samba
```

and got the error:

```
Err http://us.archive.ubuntu.com jaunty-updates/main samba 2:3.3.2-1ubuntu3.1
  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.3.2-1ubuntu3.1_amd64.deb  404 Not Found [IP: 91.189.88.46 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

Does anyone know if the servers are down or what the issue might be?

Also, does anyone know where I can get the package from another reliable source?

---

### Post by DeadlyAura on 2009-10-02
Ah, figured it out, I guess my Samba repo was out of date.

---

