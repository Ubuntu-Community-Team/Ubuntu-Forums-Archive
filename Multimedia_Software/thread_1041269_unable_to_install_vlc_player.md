---
title: "unable to install vlc player"
date: 2009-01-16
forum: Multimedia Software
---

### Post by umkatakam on 2009-01-16
Hi 

When I try to install vlc player I am getting this error:

## sudo apt-get install vlc

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: vlc-nox (= 0.9.8a+x264snapshot20080928+faad2.6.1+2-1~ppa1) but it is not going to be installed
       Depends: vlc-plugin-pulse but it is not going to be installed
E: Broken packages

Please help.

---

### Post by wolfen69 on 2009-01-16
first, go to system>administration>software sources and make sure to check off all repos. close window and reload when asked.

then open terminal and:
```
sudo apt-get install -f
```

try to install vlc now.

---

### Post by mc4man on 2009-01-16
The other thing you can do is open synaptic and under the edit tab use 'fix broken packages" followed by 'apply'
Or to manually fix just search vlc and mark the vlc-plugin-pulse for upgrade.

Your trying to use the korn repo to upgrade vlc and while it will work it doesn't handle the pulse plugin properly.

After upgrading the pulse plugin you should be fine. (to the extent vlc 0.9.x is 'fine'

---

### Post by umkatakam on 2009-01-18
I tried all the above none of it worked... I keep getin the same problem ... what do I do  ..?

---

