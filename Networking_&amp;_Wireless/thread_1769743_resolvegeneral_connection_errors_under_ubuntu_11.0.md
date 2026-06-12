---
title: "resolve/general connection errors under ubuntu 11.04"
date: 2011-05-28
forum: Networking &amp; Wireless
---

### Post by pythonscript on 2011-05-28
I have a Lenovo Thinkpad SL510, with a "Realtek RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)" wireless adapter, on Ubuntu 11.04 x64. When I run updates, I get many resolve errors "Something wicked happened resolving us.archive.ubuntu.com," and other errors like that. Also, the internet connection runs incredibly slowly, and a lot of my downloads through firefox freeze and fail. I'm wondering if all of these problems are connected. Here are the contents of /etc/resolv.conf
```
domain gateway.2wire.net
search gateway.2wire.net
nameserver 192.168.1.254
```I'm in the States now on an ATT network, if that helps. Also, could this be a problem with my source list? Here are the contents of that too. 
```

#deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty universe
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security main restricted
deb http://security.ubuntu.com/ubuntu natty-security universe
deb-src http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse
deb-src http://security.ubuntu.com/ubuntu natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main


```EDIT: I was able to download the newest Realtek drivers from [http://tinyurl.com/yefqho5](http://tinyurl.com/yefqho5), actually; my connection problems were holding me up. It looks like I have to compile them from source, though, so I think I'll hold off on that until I make sure there isn't any other problem. 

Does anyone have any ideas for what I can do to fix this? The connection here is a 1.5 Mbps, which should be plenty for checking email, downloading updates, etc. but it's practically unusable when ~2/3 of the downloads fail or the connections don't resolve. 

Thank you!

EDIT: Error message:
> 
Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)


---

### Post by pythonscript on 2011-05-30
EDIT: My wireless card's model is Realtek RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01). The booting problem was solved in this thread: [http://ubuntuforums.org/showthread.php?p=10881817](http://ubuntuforums.org/showthread.php?p=10881817). Once I get the wireless up I'll see if that fixes the connection errors in any way.

---

