---
title: "office windows network: can connect from laptop but NOT desktop. Both have mint"
date: 2021-01-11
forum: MINT
---

### Post by miesnerd on 2021-01-11
As the admittedly long title says, I brought in a new desktop I purchased and installed mint into the office. I had already tried to connect to the network share via a super old laptop that I think is running Mint 19.3... and the desktop is running 20.1. So the laptop can connect, it can browse shares, see files, etc. The the good news is I presume the network setup is fine. What's wrong with my setup that I cannot see the network?

I (and maybe I'm wrong here) assume this comes down to avahi config. In thinking that, I looked at the config files of both computers, and they appear to be the same. 
So now, knowing that mint can successfully connect to the network, I humbly come to ubuntuforums, asking for help.

Thanks!

Because I presume you'll want to see it, here's the avahi.conf file from the laptop:

# This file is part of avahi.
#
# avahi is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as
# published by the Free Software Foundation; either version 2 of the
# License, or (at your option) any later version.
#
# avahi is distributed in the hope that it will be useful, but WITHOUT
# ANY WARRANTY; without even the implied warranty of MERCHANTABILITY
# or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public
# License for more details.
#
# You should have received a copy of the GNU Lesser General Public
# License along with avahi; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

# See avahi-daemon.conf(5) for more information on this configuration
# file!

[server]
#host-name=foo
#domain-name=local
#browse-domains=0pointer.de, zeroconf.org
use-ipv4=yes
use-ipv6=yes
#allow-interfaces=eth0
#deny-interfaces=eth1
#check-response-ttl=no
#use-iff-running=no
#enable-dbus=yes
#disallow-other-stacks=no
#allow-point-to-point=no
#cache-entries-max=4096
#clients-max=4096
#objects-per-client-max=1024
#entries-per-entry-group-max=32
ratelimit-interval-usec=1000000
ratelimit-burst=1000

[wide-area]
enable-wide-area=yes

[publish]
#disable-publishing=no
#disable-user-service-publishing=no
#add-service-cookie=no
#publish-addresses=yes
publish-hinfo=no
publish-workstation=no
#publish-domain=yes
#publish-dns-servers=192.168.50.1, 192.168.50.2
#publish-resolv-conf-dns-servers=yes
#publish-aaaa-on-ipv4=yes
#publish-a-on-ipv6=no

[reflector]
#enable-reflector=no
#reflect-ipv=no

[rlimits]
#rlimit-as=
#rlimit-core=0
#rlimit-data=8388608
#rlimit-fsize=0
#rlimit-nofile=768
#rlimit-stack=8388608
#rlimit-nproc=3

---

### Post by howefield on 2021-01-11
Thread moved to the "*MINT*" forum.

---

### Post by miesnerd on 2021-01-11
To give more detail, when I go to network on the desktop, I currently see Windows Network, but there are no contents listed there. 
I have ensured the avahi-daemon is running, so I'm not sure why it's not populating with the folders.

---

### Post by miesnerd on 2021-01-11
got it to work. I suspect what fixed it was using a code I found for nmap:

sudo nmap -sT -O 192.168.1.0/24 > nmap_output

Not sure if that did it, but it worked right after that.

---

