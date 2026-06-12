---
title: "Infiniband ubuntu-server 10.04 QLogic IBA7332"
date: 2011-07-14
forum: Networking &amp; Wireless
---

### Post by platinummonkey on 2011-07-14
I thought I would share this, since after search high and low and coming across many dead ends I found the solution by mere luck mostly.

I was attempting to configure infiniband to work on ubuntu server 10.04 with stock kernel, without using the OFED package, but the packages available from the ubuntu repos using QLogic IBA7332 HCA cards in Dell T7500's.

You'll need to follow this guide mostly:
[http://davidhunt.ie/wp/?tag=infiniband](http://davidhunt.ie/wp/?tag=infiniband)

However, these QLogic cards use Mellanox chipsets, so you'll need to install the mellanox infiniband drivers available from the repository. And also add *all* the modules to /etc/modules found in /lib/modules/`uname -r`/kernel/drivers/infiniband/

I also for safe measure added /lib/modules/`uname -r`/kernel/drivers/net/mlx4/* and /lib/modules/`uname -r`/kernel/drivers/net/ifb
These may not be needed, I haven't looked into it much further.

Items you'll also need for troubleshooting and configuring infiniband:
[https://launchpad.net/~ast/+archive/srp/+build/1758231](https://launchpad.net/~ast/+archive/srp/+build/1758231)
[https://launchpad.net/~ast/+archive/test3/+build/1719463](https://launchpad.net/~ast/+archive/test3/+build/1719463)

---

