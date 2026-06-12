---
title: "nmcli added to network-manager 0.8.1"
date: 2010-08-29
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by plun on 2010-08-29
> * Also install the new nmcli utility so some command-line control of NM is available. (LP: #623385)
    - update debian/network-manager.install

[https://lists.ubuntu.com/archives/maverick-changes/2010-August/006497.html](https://lists.ubuntu.com/archives/maverick-changes/2010-August/006497.html)



New functionality to NM....

Basics:
```
plun@plun-laptop:~$ nmcli
Usage: nmcli [OPTIONS] OBJECT { COMMAND | help }

OPTIONS
  -t[erse]                                   terse output
  -p[retty]                                  pretty output
  -m[ode] tabular|multiline                  output mode
  -f[ields] <field1,field2,...>|all|common   specify fields to output
  -e[scape] yes|no                           escape columns separators in values
  -v[ersion]                                 show program version
  -h[elp]                                    print this help

OBJECT
  nm          NetworkManager status
  con         NetworkManager connections
  dev         devices managed by NetworkManager

plun@plun-laptop:~$ nmcli nm
RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN      
running         connected       enabled         enabled    enabled         enabled   
plun@plun-laptop:~$ nmcli con
NAME                      UUID                                   TYPE              SCOPE    TIMESTAMP-REAL                    
Auto eth0                 926f120d-bcf0-48fbd758c4fec   802-3-ethernet    system   never                             
NAME                      UUID                                   TYPE              SCOPE    TIMESTAMP-REAL                    
Auto Hemma                e424c8a2-af37-   802-11-wireless   user     Fri 27 Aug 2010 03:59:46 PM CEST  
Auto Android               c1fc2577-9366d1a2ab7b   802-11-wireless   user     Tue 20 Jul 2010 09:31:46 AM CEST  
Telenor Mobilt Internet   3a595c87-25e8--d0e685c329aa   gsm               user     Sun 29 Aug 2010 12:23:16 PM CEST  
plun@plun-laptop:~$ nmcli dev
DEVICE     TYPE              STATE       
wlan0      802-11-wireless   disconnected
eth0       802-3-ethernet    unavailable 
hso0       gsm               connected   

```


man nmcli is rather heavy......   any "dummie"-tutorials out there...  ???



--

---

### Post by jared_c on 2010-08-30
See:

[http://docs.fedoraproject.org/en-US/Fedora/13/html/User_Guide/sect-User_Guide-Connecting_to_the_Internet-NM_CLI.html](http://docs.fedoraproject.org/en-US/Fedora/13/html/User_Guide/sect-User_Guide-Connecting_to_the_Internet-NM_CLI.html)

where they give the example 

> 
So, running 
```
nmcli nm status
``` 
we have:
```

NM running:               running
NM state:                 connected
NM wireless hardware:     enabled
NM wireless:              enabled
NM WWAN hardware:         enabled
NM WWAN:                  enabled

```

Apparently nmcli is a nested command, where there are three things you need to write, as in "nmcli nm status" or "nmcli con help".  It looks like it's not going to be an easy command to use/remember...

---

### Post by slakkie on 2010-08-31
Wow, it is worth considering using NM now.. Looks like a cool tool. Too bad I'm not running Maverick, hopefully they'll backport this to Lucid..

---

