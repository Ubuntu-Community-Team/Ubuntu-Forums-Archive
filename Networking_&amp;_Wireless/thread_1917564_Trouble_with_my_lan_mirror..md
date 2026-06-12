---
title: "Trouble with my lan mirror."
date: 2012-01-30
forum: Networking &amp; Wireless
---

### Post by maminyana on 2012-01-30
I'm tryig to create a mirror inside my LAN, using ubuntu 11.10
I've followed the HOWTOS. I've installed Apache, apt-mirror, made the links with ln, and everything seems to work properly.
The trouble I have is that I can't download new software. It misses dependencies.

Here are the files mirror.list and sources.list.
Please, help me. Do I have to change these files?

# MIRROR.LIST
############# config ##################
#
# set base_path /var/spool/apt-mirror
#
# set mirror_path $base_path/mirror
# set skel_path $base_path/skel
# set var_path $base_path/var
# set cleanscript $var_path/clean.sh
# set defaultarch
# set postmirror_script $var_path/postmirror.sh
# set run_postmirror 0
set nthreads 20
set _tilde 0

#
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) oneiric-updates universe
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main

clean [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu)
clean [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)
clean [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu)
## END MIRROR.LIST

# SOURCES.LIST
deb [http://192.168.0.211/archive-ubuntu/ubuntu/](http://192.168.0.211/archive-ubuntu/ubuntu/) oneiric universe
deb [http://192.168.0.211/archive-ubuntu/ubuntu/](http://192.168.0.211/archive-ubuntu/ubuntu/) oneiric-updates universe
deb [http://192.168.0.211/archive-ubuntu/ubuntu/](http://192.168.0.211/archive-ubuntu/ubuntu/) oneiric multiverse
deb [http://192.168.0.211/archive-ubuntu/ubuntu/](http://192.168.0.211/archive-ubuntu/ubuntu/) oneiric-updates multiverse
deb [http://192.168.0.211/security-ubuntu/ubuntu](http://192.168.0.211/security-ubuntu/ubuntu) oneiric-security universe
deb [http://192.168.0.211/security-ubuntu/ubuntu](http://192.168.0.211/security-ubuntu/ubuntu) oneiric-security multiverse
deb [http://192.168.0.211/extras-ubuntu/ubuntu](http://192.168.0.211/extras-ubuntu/ubuntu) oneiric main
deb [http://192.168.0.211/archive-ubuntu/ubuntu](http://192.168.0.211/archive-ubuntu/ubuntu) oneiric main universe restricted multiverse
#END SOURCES.LIST

---

### Post by maminyana on 2012-02-02
I answer myself after lots of trial and error attempts.

I think the problem is with the symbol: "/"
In **mirror.list**, seems correct:
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) oneiric universe

and is wrong: 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe

In **sources.list** is right
deb [http://192.168.0.211/extras-ubuntu/ubuntu](http://192.168.0.211/extras-ubuntu/ubuntu) oneiric main

and is wrong:
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) oneiric universe

Very tricky, don't you think?

---

