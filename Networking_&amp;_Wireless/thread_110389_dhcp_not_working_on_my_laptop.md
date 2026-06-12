---
title: "dhcp not working on my laptop"
date: 2005-12-30
forum: Networking &amp; Wireless
---

### Post by Sonique on 2005-12-30
I have a Sony Vaio C1VE, ive had numerous problems in the past but this one should be quite easy to solve if someone has had the same problem.

Since the laptop on has on pcmia port [i think thats what it is called], when installing ubuntu, i could not put my wired network card in the laptop becuase the post was occupied by the external cd drive. Therefore it thinks i do not have a network peripheral.

So once inside ubuntu after installation, i disconnect my external cd drive and plug in my wired network card that is connected to my router. System>administration>networking does realise because it shows eth0 when before it didnt. Since my router is dhcp, i put the option dhcp and activate. It looks like it is activating with a window with a bar going left and right, that disappears after about 30 seconds. At this point im thinking "way hey", "no problemo", however, it doesnt work because i can surf the net.

I put a ubuntu live cd on my desktop computer, in the loading it says it is connecting onto then network on dhcp, and when im in the live ubuntu, it works fine, i can surf the net immediately. The difference between my desktop and my laptop is that the desktop had a network card connected when instalising.

So if anyone has any ideas, it would be gladly appreciated !
thanks

---

### Post by darth_vector on 2005-12-30
look at the file /etc/network/interfaces. are there a pair of lines like:

auto eth0
iface eth0 inet dhcp

if not, add them (you will have to edit the file as root: sudo gedit /etc/network/interfaces) and then do a

sudo /etc/init.d/network restart


EDIT: it may be that you havent set up dns properly. can you ping stuff on the internet by ip? try pinging 72.14.207.99 and see if you get a reply.

---

### Post by Sonique on 2005-12-31
I added "auto eth0" to the file and restarted the network. No change.

When pinging ip address i just recieve:

```
connect: Network is unreachable
```

I get it if i ping within the network and if i do 72.14.207.99.

I assume i havent set up my dns properly, how'd you do that?

---

