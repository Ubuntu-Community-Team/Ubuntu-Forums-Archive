---
title: "can not install rubygems1.9.1 on  Maverick Meerkat rc"
date: 2010-10-01
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by d6rkaiz on 2010-10-01
Can not install rubuygems1.9.1

here there is rubygems1.9.1
[https://launchpad.net/ubuntu/maverick/+package/rubygems1.9.1](https://launchpad.net/ubuntu/maverick/+package/rubygems1.9.1)

but..
# apt-cache search rubygems
libruby-extras - a bundle of additional libraries for Ruby
libruby1.8-extras - a bundle of additional libraries for Ruby 1.8
ruby1.9.1 - Interpreter of object-oriented scripting language Ruby 1.9.2
rubygems - package management framework for Ruby libraries/applications
rubygems-doc - package management framework for Ruby libraries/applications
rubygems1.8 - package management framework for Ruby libraries/applications

# apt-get install rubygems1.9.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'ruby1.9.1' instead of 'rubygems1.9.1'
ruby1.9.1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

# dpkg -l rubygems1.9.1
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  rubygems1.9.1  <none>         (no description available)

---

### Post by cariboo on 2010-10-01
i'd suggest creating a bug. Press Alt-F2 and type:

```
ubuntu-bug rubygems
```

Add the output you're are getting when trying to install the package.

---

### Post by d6rkaiz on 2010-10-01
Thanks for reply

I've reported.
[https://bugs.launchpad.net/ubuntu/+source/libgems-ruby/+bug/653142](https://bugs.launchpad.net/ubuntu/+source/libgems-ruby/+bug/653142)

---

### Post by SevenMachines on 2010-10-01
rubygems1.9.1 is a purely virtual package, it doesnt really exist. Its actually provided by the ruby1.9.1 'real' package. In short, rubygems is now part of the main ruby library rather than a seperate package. So when you do..

$ apt-get install rubygems1.9.1

The packaging systems knows to really install the ruby1.9.1 which provides it

"Note, selecting 'ruby1.9.1' instead of 'rubygems1.9.1'"

---

### Post by d6rkaiz on 2010-10-01
Thanks for reply.

sorry, i get the rubygems1.9.1 in the ruby1.9.1 package.
this is changes from 10.04.

10.04:
# dpkg -L ruby1.9.1
/.
/usr
/usr/bin
/usr/bin/ruby1.9.1
/usr/bin/erb1.9.1
/usr/bin/testrb1.9.1
/usr/bin/rake1.9.1
...

10.10:
# dpkg -L ruby1.9.1
/.
/usr
/usr/bin
/usr/bin/ruby1.9.1
/usr/bin/erb1.9.1
/usr/bin/testrb1.9.1
/usr/bin/rake1.9.1
/usr/bin/rdoc1.9.1
/usr/bin/irb1.9.1
/usr/bin/gem1.9.1
...

Thanks for letting me.

---

### Post by SevenMachines on 2010-10-02
Yes, i noticed that its a recent change, the virtual package is there to make the transition seamless (hopefully) but it can lead to confusion

---

