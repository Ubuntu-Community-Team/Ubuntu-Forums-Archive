---
title: "Can't install vlc after upgrade to 14.10"
date: 2014-10-26
forum: Multimedia Software
---

### Post by Michael_Astashkevi on 2014-10-26
Hello, I'm getting erros while trying to install vlc on my xubuntu 14.10:
apt-get install vlc
 vlc : Depends: libgles1-mesa (>= 7.8.1) but it won't be installed or libgles1

apt-get install libgles1-mesa
 libgles1-mesa : Depends: libglapi-mesa (= 10.3.0-0ubuntu3) but 10.4.0~git20141006.ca824e69-0ubuntu0ricotz~trusty will be installed

apt-get install libglapi-mesa=10.3.0-0ubuntu3
 libgl1-mesa-glx : Depends: libglapi-mesa (= 10.4.0~git20141006.ca824e69-0ubuntu0ricotz~trusty) but 10.3.0-0ubuntu3 will be installed
 nvidia-current-updates : Depends: nvidia-304-updates but it won't be installed

How can I install vlc?

---

### Post by kc1di on 2014-10-26
Hi Michael_Astashkevi and welcome to Ubuntu,

Did you reboot after upgradeing?

Did you do an update before trying to install VLC?
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install vlc
```

Give that a try see if it works.

---

### Post by Michael_Astashkevi on 2014-10-26
Yes, I rebooted and upgraded system after upgrade and still get this error

---

### Post by broomie on 2014-10-26
Same here -restarted , updated the works...

---

### Post by yancek on 2014-10-26
Was vlc not working for you on 14.04?  I'm curious as to why you would upgrade to 14.10 when its support will end April, 2015 and 14.04 has support until April, 2019.

---

### Post by mc4man on 2014-10-26
You appear to have mesa packages from a ppa installed for **trusty**. You'll need to resolve that in some manner..
> libgles1-mesa : Depends: libglapi-mesa (= 10.3.0-0ubuntu3) **but 10.4.0~git20141006.ca824e69-0ubuntu0ricotz~trusty will be installed**
will be installed generally means already is installed

---

### Post by geomcd1949 on 2014-10-26
mc4man

Thanks! How do we fix the problem: **y[COLOR=#000000]ou appear to have mesa packages from a ppa installed for [/COLOR]****[B]trusty****. You'll need to resolve that in some manner..**
[/B][B]
Appreciate it!

~George[/B]****

---

### Post by mc4man on 2014-10-26
> **geomcd1949 said:**
> mc4man

Thanks! How do we fix the problem: **y[COLOR=#000000]ou appear to have mesa packages from a ppa installed for [/COLOR]****[B]trusty****. You'll need to resolve that in some manner..**
[/B][B]
Appreciate it!

~George[/B]****
Well I'd think this is a bit of an issue. It would of been best to use ppa-purge of the xorg-edgers ppa before upgrading. I've no clue if it'll work now..
So your current trusty mesa packages are @ 10.4.x & mesa in 14.10 is @ 10.3.x

If it was me I'd go ahead & add back the ppa, update your sources & do a dist-upgrade
(though I'd also probably copy out any files of importance

ppa here - 
[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa)

If you do go ahead with adding the ppa then simulate the dist-upgrade before really doing so, ie.,
```
sudo apt-get [COLOR="#0000CD"]-s [/COLOR]dist-upgrade
```

just to check first about *some* of what may be  installed -  (both should be from ppa for trusty
```
apt-cache policy libgl1-mesa-glx libglapi-mesa

```

---

### Post by Michael_Astashkevi on 2014-10-27
Indeed, I misread "~trusty" at the end of package name.
After adding xorg-edgers ppa and upgrading I was able to install vlc. Thanks a lot!

---

### Post by hhweise on 2014-11-20
> **mc4man said:**
> Well I'd think this is a bit of an issue. It would of been best to use ppa-purge of the xorg-edgers ppa before upgrading. I've no clue if it'll work now..
So your current trusty mesa packages are @ 10.4.x & mesa in 14.10 is @ 10.3.x

If it was me I'd go ahead & add back the ppa, update your sources & do a dist-upgrade
(though I'd also probably copy out any files of importance

ppa here - 
[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa)

If you do go ahead with adding the ppa then simulate the dist-upgrade before really doing so, ie.,
```
sudo apt-get [COLOR=#0000CD]-s [/COLOR]dist-upgrade
```

just to check first about *some* of what may be  installed -  (both should be from ppa for trusty
```
apt-cache policy libgl1-mesa-glx libglapi-mesa

```


Thanks this worked for me as well.

---

### Post by diego-giglio on 2015-08-01
It's worked to me. Tks!

---

### Post by pickarooney on 2015-10-29
Any help for this same issue on Vivid? The PPA doesn't have the necessary packages

---

