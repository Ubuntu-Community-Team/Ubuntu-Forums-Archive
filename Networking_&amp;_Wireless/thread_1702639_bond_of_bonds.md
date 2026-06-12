---
title: "bond of bonds"
date: 2011-03-08
forum: Networking &amp; Wireless
---

### Post by koszta on 2011-03-08
Hi,
this is a little more theoretical. I read the bonding driver doc but there is nothing said bout bonding 2 bonds into one bond... 

It would look like something like this:
1. bond0 and bond1 are bonded in mode 0 (round robin)
2. bond2 bonds bond0 and bond1 as slaves in mode 1 (active-backup)




         +----------+                                          +----------+
          |          |                                          |          |
          | switch A |                                          | switch B |
          |          |                                          |          |
          |          |                                          |          |
          +----++----+                                          +-----++---+
          port1||port2                 Server                    port1||port2
               ||             +-----------------------+               ||
               |+-------------+                       +---------------+|
               |         eth0 |BOND0<---BOND2--->BOND1| eth1           |
               +--------------+                       +----------------+
                         eth2 +-----------------------+ eth3  


BOND0(aggregate)
+------+
| eth0 |
| eth2 |
+------+

BOND1(aggregate)
+------+
| eth1 |
| eth3 |
+------+

BOND2(active/backup)
+-------+
| bond0 |
| bond1 |
+-------+  

(credits to Dustin Kamper for the picture)

Could this be done? Is it even possible

---

### Post by dkamper on 2011-04-28
[FONT=Courier New][COLOR=#000000][COLOR=#0000bb][FONT=Verdana]Hey,  thanks for re-posting this....I totally forgot about this (ie, I gave up and went with a simpler bonding solution because nobody replied to my original post in the Novell forums regarding doing this in SLES 10.2).

I have re-formatted the image you credited me with as it came out looking horrible without a fixed width font.  Thanks for crediting me, btw.

If I can get an answer to this, I would still like to configure the server this way for faster throughput and high availability.[/FONT]


     [/COLOR][/COLOR][/FONT]```

     +----------+                                          +----------+
     |          |                                          |          |
     | switch A |                                          | switch B |
     |          |                                          |          |
     |          |                                          |          |
     +----++----+                                          +----++----+
     port1||port2                 Server                   port1||port2
          ||             +-----------------------+              ||
          |+-------------+                       +--------------+|
          |         eth0 |BOND0<---BOND2--->BOND1| eth1          |
          +--------------+                       +---------------+
                    eth2 +-----------------------+ eth3  


BOND0(aggregate)
+------+
| eth0 |
| eth2 |
+------+

BOND1(aggregate)
+------+
| eth1 |
| eth3 |
+------+

BOND2(active/backup)
+-------+
| bond0 |
| bond1 |
+-------+  
```

---

