---
title: "Firestarter and ip_conntrack (different group same question)"
date: 2013-04-12
forum: Networking &amp; Wireless
---

### Post by hiflyer on 2013-04-12
I am using Ubuntu 12.10 upgrade up to date on a dell D630
I have firestarter installed (over many versions) and it used to show the active connection but no longer does.
If I
sudo firestarter

and then hit the active connections, in the terminal window I get the following error repeatedly until I stop the active connection display.

Error reading /proc/net/ip_conntrack: No such file or directory

I look in /proc/net and there is no such file. Suggestions on the web state that I should
I check that conntrack is installed and appearently should be, to be able to do the modprobe command to get the file. so I do

sudo apt-get install conntrack

which install just fine

then I do

sudo modprobe ip_conntrack
and it does not complain but the is no file ip_conntrack file created.

I have also done sudo modprobe nf_conntrack but with no results.

What am I doing wrong or what is missing.
I can do a
sudo conntrack -L

and get a list of connections.

I posted this under desktops which is probably the wrong group. I no not know the correct way to move to this group which seems to be the correct group. And yes, I know that firestarter is no longer supported.

does anybody here know why/suggest why I cannot get ip_conntrack or nf_conntrack to produce an output?

tia

---

### Post by Doug S on 2013-04-13
I wonder if you don't have a connection tracking table, even with the module loaded, because you don't need it. ?
Are you doing Network Address Translation (NAT)? It needs it, for example.
You can check via the lsmod command, observing the used by column:```
doug@doug-64:~$ [COLOR=#ff0000]lsmod[/COLOR]
Module                  Size  Used by
xt_multiport           12597  2
xt_limit               12711  1
xt_recent              18437  3
ipt_REJECT             12576  3
xt_tcpudp              12603  8
xt_state               12578  10
ipt_LOG                12919  21
iptable_nat            13229  1
nf_nat                 25891  1 iptable_nat
[COLOR=#ff0000]nf_conntrack_ipv4      19[/COLOR]716  13 iptable_nat,nf_nat
[COLOR=#ff0000]nf_conntrack           [/COLOR]81926  4 xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
iptable_filter         12810  1
ip_tables              27473  2 iptable_nat,iptable_filter
x_tables               29891  10 xt_multiport,xt_limit,xt_recent,ipt_REJECT,xt_tcpudp,xt_state,ipt_LOG,iptable_nat,iptable_filter,ip_tables
ext2                   73795  1
psmouse                97485  0
i915                  477748  1
dcdbas                 14490  0
ppdev                  17113  0
serio_raw              13211  0
drm_kms_helper         46978  1 i915
parport_pc             32866  1
drm                   241971  2 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19651  1 i915
mac_hid                13253  0
lp                     17799  0
parport                46562  3 ppdev,parport_pc,lp
floppy                 70207  0
usbhid                 47238  0
via_rhine              32192  0
hid                    99636  1 usbhid
tg3                   152085  0
```Compare that with another computer, where I force loaded ip_conntrack, but it isn't needed and still /proc/net/ip_conntrack does not exist:```
doug@virt64-02:~$ [COLOR=#ff0000]lsmod[/COLOR]
Module                  Size  Used by
[COLOR=#ff0000]nf_conntrack_ipv4      [/COLOR]14531  0
[COLOR=#ff0000]nf_conntrack           83[/COLOR]300  1 nf_conntrack_ipv4
nf_defrag_ipv4         12730  1 nf_conntrack_ipv4
btrfs                 781017  0
zlib_deflate           27140  1 btrfs
libcrc32c              12645  1 btrfs
ufs                    75309  0
qnx4                   13432  0
hfsplus                89053  0
hfs                    54783  0
minix                  36416  0
ntfs                  101959  0
msdos                  17333  0
jfs                   186683  0
xfs                   852661  0
reiserfs              249170  0
kvm_intel             137888  0
lp                     17800  0
psmouse               102075  0
parport                46563  1 lp
virtio_balloon         13268  0
kvm                   422160  1 kvm_intel
i2c_piix4              13302  0
serio_raw              13216  0
microcode              23030  0
mac_hid                13254  0
ext2                   73799  1
floppy                 70245  0
```

---

### Post by hiflyer on 2013-04-13
I tried lsmod | grep conntrack and got:

nf_conntrack_irc       13350  0 
nf_conntrack_ipv6      14055  7 
nf_defrag_ipv6         13203  1 nf_conntrack_ipv6
nf_conntrack_netbios_ns    12666  0 
nf_conntrack_broadcast    12590  1 nf_conntrack_netbios_ns
nf_conntrack_ipv4      14481  9 iptable_nat,nf_nat
nf_defrag_ipv4         12730  1 nf_conntrack_ipv4
nf_conntrack_ftp       13360  1 nf_nat_ftp
nf_conntrack           82634  11 ipt_MASQUERADE,nf_conntrack_irc,iptable_nat,nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
 
if I read this correctly, lots of things are attempting or are using nf_conntrack.

should I be able to do a sudo cat /proc/net/nf_conntrack given above and get something?
I don't thing ip_conntrack exists anymore as the netfilter group renamed it to nf_conntrack or do I miss understand that as well.

---

### Post by Doug S on 2013-04-13
Hmmm... It seems to me that the connection tracking table should be there for you. I do not know why it is not. I do not use IPV6 on my main server, and I don't know if that makes any difference. 

On the ip_conntrack Vs. nf_conntrack stuff: Yes, the name was changed, I was merely doing what you had done, and it seems to have loaded the proper module.

I do seem to have a /proc/net/nf_conntrack table. I used this to see what else might be there (in case of new names or whatever):```
sudo ls -l /proc/net/*
```Note: I do not have a 12.10 computer, just 12.04 and 13.04.

---

### Post by hiflyer on 2013-04-13
I dont use ip6 either. I see it is turned on. Do you know how I turn it off.

---

### Post by Doug S on 2013-04-13
I think there are a few ways to disable IPV6, however I only remember the way I use.
I edit /etc/default/grub and change this line:```
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1"
```Then run this:```
sudo update-grub
```Note: I do get some side effect grief from dovecot, that I have never bothered to figure out.

---

### Post by hiflyer on 2013-04-13
Thanks, that got rid of IP6 but did not fix the conntrack issue.
I appreciate the help. Will keep looking.

---

### Post by Nexcor on 2013-05-17
The same problem in ubuntu 12.04.2

---

### Post by Doug S on 2013-05-17
> **Nexcor said:**
> The same problem in ubuntu 12.04.2Tell us more about your particular situation. I still think my post #2 above is accurate, and there will not be a /proc/net/ip_conntrack file, even if the module is loaded, if it is not needed. Maybe post your iptables rule set.

---

