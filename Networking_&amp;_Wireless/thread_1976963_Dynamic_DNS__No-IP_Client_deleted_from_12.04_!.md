---
title: "Dynamic DNS / No-IP Client deleted from 12.04 ?!?"
date: 2012-05-09
forum: Networking &amp; Wireless
---

### Post by Groodles on 2012-05-09
I've been using Ubuntu for my home server for a few years now (since Jaunty).

My home internet IP is dynamic, so to get around it I've always used no-ip.com and their dynamic dns service.

That was, until I updated to 12.04 and tried to install the no-ip update client (noip2) and I find it's not in the repos.

Is there another client, service which I can use instead?

---

### Post by Groodles on 2012-05-09
I'm such a numpty.

No-IP have the source available.  Quick compile, sorted.

---

### Post by se7en983 on 2012-09-24
hi, i'm really new to the linux os and i was having the same problem with with no-ip on ubuntu server 12.4
after a bit of digging i found a solution.


you need to install the gcc and g++ compilers, This will also install GNU make.
$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get install build-essential
$ gcc -v
$ make -v

to install No-IP Linux Dynamic Update Client Ubuntu 12.04 

    cd /usr/local/src/
    wget [http://www.no-ip.com/client/linux/noip-duc-linux.tar.gz](http://www.no-ip.com/client/linux/noip-duc-linux.tar.gz)
    tar xf noip-duc-linux.tar.gz
    cd noip-2.1.9-1/
    sudo make install

    you should get asked for your email add and password

    just enter them and bobs your teapot

    this worked for me and i'm up and running;)

---

