---
title: "ubuntu update problem : 407 Unauthorized"
date: 2010-09-12
forum: Networking &amp; Wireless
---

### Post by rastar101 on 2010-09-12
hi
i just connected to a proxy network which needed username and password.i configure firefox proxy settings and i can access to net and everything is working well!
and i did configure **System->Prefrences->Network Proxy** to manual and **set all protocols to use the same proxy** , then i enter my username and password by clicking on "**details**"
but when i try to update ubuntu via update manager or ```
sudo apt-get update
``` i got this error :
```
Failed to fetch http://ir.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz  407  Unauthorized

```
when i asked from network manager to remove authorization ,everything was OK.
could anyone help me,plz?

---

### Post by tiosus on 2010-09-12
i have got this problem too plz help!!!

---

### Post by MaindotC on 2010-09-12
The ip address of the proxy server is probably banned for malicious use.  This happens very frequently, especially with the [Tor project]("http://tor.org").  Remove the proxy settings, run your updates, then you can put it back on for whatever else you need.

---

### Post by rastar101 on 2010-09-12
> **strAlan said:**
> The ip address of the proxy server is probably banned for malicious use.  This happens very frequently, especially with the [Tor project]("http://tor.org").  Remove the proxy settings, run your updates, then you can put it back on for whatever else you need.

i cant remove the proxy setting xhenever i want.its a network!!

---

### Post by MaindotC on 2010-09-12
Why can't you?  You entered the proxy information, why can't you just remove it?

---

### Post by rastar101 on 2010-09-13
> **strAlan said:**
> Why can't you?  You entered the proxy information, why can't you just remove it?

tnx for replying!
I enter the proxy information which is given to me by network administrator.I cant change them or remove the authorization requests.I'm not the networks admin!!

---

### Post by BkkBonanza on 2010-09-13
This is probably just apt-get being rejected when not using the proxy.
apt-get will not use the system proxy set from the GUI.
You need to either export the environment variable HTTP_PROXY=...
or add a configure line in /etc/apt.conf
See **man apt.conf** for details on how to configure that option.

[noparse]HTTP http://[[user][:pass]@]host[:port]/[/noparse]

Most command line tools won't use a proxy unless the env variable is set, and some won't use one anyway. tsocks can help with those cases. But, in this case apt.conf should help you.

---

### Post by rastar101 on 2010-09-13
> **BkkBonaza said:**
> 
You need to either export the environment variable HTTP_PROXY=...
or add a configure line in /etc/apt.conf
See **man apt.conf** for details on how to configure that option.

[noparse]HTTP http://[[user][:pass]@]host[:port]/[/noparse]


tnx for helping;
i did try to set proxy by a command like this :
```
export http_proxy=http://username:pass@proxyserver:port/
```
but it didn't work...

---

### Post by BkkBonanza on 2010-09-13
It should work, see this thread for a few other ideas.
Special chars in user/pwd need escapes...
[http://ubuntuforums.org/showthread.php?t=1575](http://ubuntuforums.org/showthread.php?t=1575)
it may require changing apt.conf as well.

Also it would need to be for the root login env since apt-get will be run as sudo. So that's likely why apt.conf is better.

---

### Post by rastar101 on 2010-09-14
@[BkkBonaza]("http://ubuntuforums.org/member.php?u=550406")
tnx very much
it worked!!!:p

---

