---
title: "problem  of GRE tunnel between two PCs in a private network"
date: 2010-02-24
forum: Networking &amp; Wireless
---

### Post by feelagain on 2010-02-24
Here is my network:
                                                                hostd
                                                                   |
hosta---------------router1 --------------------router3-----------hostc
                              |                                      |
                              |                                      |
                              |______________________|
                                                    |
                                                  router2------------------------hostb

When hostc want to send data to hostb, the defaul route is through router 3 and router2. Now I am trying to tunnel it through hosta, i.e. hostc ->router3->router1->hosta->router2->hostb. I was configuring the hostc and hosta as two endpoints of a gre tunnel. any data sent by hosta will be routed to router2 by default. But the tunnel wouldn't work. actually, data piped into the tunnel never leave the end host. Is it possible to setup the hosts to do this or I have to setup tunnel between router3 and router 1? Any links? Many thanks.:(:confused:

---

