---
title: "Apply system-wide proxy from console"
date: 2010-07-28
forum: Networking &amp; Wireless
---

### Post by Boris_Brodski on 2010-07-28
Hello everyone,


I try to write a BASH-script to switch between different proxy configurations for linux and all applications (firefox/subversion/maven/...). I have trouble setting proxy system wide.

I try following:
```

function set_proxy_gconf {
        gconftool-2 -t boolean -s /system/http_proxy/use_http_proxy 1
        gconftool-2 -t boolean -s /system/http_proxy/use_same_proxy 1

        gconftool-2 -t string -s /system/proxy/mode "manual"
        gconftool-2 -t list --list-type=string -s /system/http_proxy/ignore_hosts "$3"

        gconftool-2 -t string -s /system/http_proxy/host "$1"
        gconftool-2 -t int -s /system/http_proxy/port "$2"

        gconftool-2 -t string -s /system/proxy/secure_host "$1"
        gconftool-2 -t int -s /system/proxy/secure_port "$2"

        gconftool-2 -t string -s /system/proxy/socks_host "$1"
        gconftool-2 -t int -s /system/proxy/socks_port "$2"

        gconftool-2 -t string -s /system/proxy/ftp_host "$1"
        gconftool-2 -t int -s /system/proxy/ftp_port "$2"
}

set_proxy_gconf proxy.host.com 8080 '[127.0.0.1,localhost]'

```under my user and root to set the proxy. Unfortunately this work only for firefox, but not for synaptic and bash, for example:

```

$ sudo su -l user
$ export
...
declare -x ftp_proxy="ftp://old-proxy:1180/"
declare -x http_proxy="http://old-proxy:1180/"
declare -x https_proxy="https://old-proxy:1180/"

$ sudo su -l
# export
...
declare -x ftp_proxy="ftp://old-proxy:1180/"
declare -x http_proxy="http://old-proxy:1180/"
declare -x https_proxy="https://old-proxy:1180/"

```I can rich the appropriate behavior only by opening "Network Proxy Preferences" (gnome-network-properties) and pressing "Apply System-Wide..." button.

My question is: how can I do "Apply System-Wide..." from the console out of my script?

Thank you very much in advance!

Regards,
Boris Brodski

PS
Ubuntu 9.10 32 bit

Linux boris-laptop 2.6.31-22-generic-pae #60-Ubuntu SMP Thu May 27 01:40:15 UTC 2010 i686 GNU/Linux

---

### Post by rasup on 2010-08-25
I've been trying to do the same thing but the environment variables won't change.

I've found out that when I "Apply System-Wide..." it changes the file:
```
/etc/gconf/gconf.xml.defaults/%gconf-tree.xml
```

I can edit that file with e.g.:
```
sudo gconftool --config-source=xml::/etc/gconf/gconf.xml.defaults -t bool -s /system/http_proxy/use_http_proxy false
```

Maybe someone else can figure out how to change the environment variables system-wide.

Edit: I'm using Ubuntu 10.04.

---

