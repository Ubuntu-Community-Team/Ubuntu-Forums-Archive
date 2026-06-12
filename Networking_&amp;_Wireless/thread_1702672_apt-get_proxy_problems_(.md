---
title: "apt-get proxy problems :("
date: 2011-03-08
forum: Networking &amp; Wireless
---

### Post by grim340 on 2011-03-08
i put this in /etc/bash.bashrc
```

#proxy
export http_proxy=http://..the user..:localhost:8080/
export ftp_proxy=http://..the user..:localhost:8080/

```

The above proxy does not require a passworld. I don't know
if thats a problem ??

I put this in /etc/wgetrc
```

# You can set the default proxies for Wget to use for http and ftp.
# They will override the value in the environment.
http_proxy = http://localhost:8080/
ftp_proxy = http://localhost:8080/

# If you do not want to use proxy at all, set this to off.
use_proxy = on

```

Again the proxy does not require a password.
And of course i set my proxy settings in Gnome-Control-Center(System-Wide)
and after all this, it still does not work(using apt-get) !!! :confused::confused:

Here is an error i get when using apt-get update
```

Could not resolve '..the user..:localhost'

```

---

### Post by grim340 on 2011-03-08
i really need a this proxy problem fixed.
i have these problems when running Synaptic update:
```

W: GPG error: http://download.virtualbox.org karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 54422A4B98AB5139
W: GPG error: http://deb.opera.com lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A2019EA84E7532C8
W: GPG error: http://packages.medibuntu.org karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0DA7581859566E92
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 43BB102C405A15CB
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2ED6BB6042C24D89
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A6DCF7707EBC211F
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 638ABCA0FA3A1271
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7FB8BEE0A1F196A8
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0CC1223EE2314809
W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7889D725DA6DEEAA
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 28A8205077558DD0
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D79F61BE8D31A30
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DE
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2A8E3034D018A4CE
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC6D7D9D009ED615
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F104610CF0876AC9
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 978228591BD3A65C
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4FEC45DD06899068
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6298AD34413576CB
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg  Connection failed [IP: 127.0.0.1 8080]

W: Failed to fetch http://linux.getdropbox.com/ubuntu/dists/karmic/Release.gpg  Connection failed [IP: 127.0.0.1 8080]

W: Failed to fetch http://le-web.org/repository/dists/stable/main/binary-i386/Packages.gz  404  Not Found [IP: 127.0.0.1 8080]

W: Failed to fetch http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found [IP: 127.0.0.1 8080]

W: Some index files failed to download, they have been ignored, or old ones used instead.


```

---

### Post by grim340 on 2011-03-08
I had to set my proxy settings:
bash.bashrc
```

export http_proxy=http://localhost:8080/
export ftp_proxy=http://localhost:8080/

```
wgetrc
```

http_proxy = http://localhost:8080/
ftp_proxy = http://localhost:8080/

use_proxy = on

``` 
duhh, :lolflag:

---

