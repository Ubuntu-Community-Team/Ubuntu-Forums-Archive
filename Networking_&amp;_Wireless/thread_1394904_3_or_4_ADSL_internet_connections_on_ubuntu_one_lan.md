---
title: "3 or 4 ADSL internet connections on ubuntu one lan"
date: 2010-01-31
forum: Networking &amp; Wireless
---

### Post by jritas on 2010-01-31
Hello
I have the following situation

I      isp1 (192.168.1.1) ---------- eth0  |-------------------|                    internal Lan 
N                                                      |                        |                     
T      isp2 (192.168.2.1)----------  eth1 |                        |                      ------10.1.1.2
E                                                      | ubuntu PC         |-- eth4 10.1.1.1
R      isp3 (192.168.3.1)---------- eth2  |                        |                       -----10.1.1.3
E                                                      | 4 nics               |    
T      isp4  (192.168.4.1)---------- eth3 |-------------------|

I want to connect my internal lan pc's (about 30-40 of them) via my ubuntu router (4 network cards) and to be able to bond - aggregate - manage the 3 or 4 internet connections. The ip's 192.168.1.1, 2.1, 3.1, 4.1 are from the ADSL routers witch are the gateways for internet connection.
I have done the router with 1 internet connection.....
I have read the following guides with no success .....
  [http://www.netlife.co.za/content/view/12/34/](http://www.netlife.co.za/content/view/12/34/)
[http://www.linux.com/archive/feature/113988](http://www.linux.com/archive/feature/113988)
[http://www.michaelbrumm.com/how-to-aggregate-bandwidth.html](http://www.michaelbrumm.com/how-to-aggregate-bandwidth.html)
[http://minez-inspirate.blogspot.com/2009/07/create-load-balancing-router-using.html](http://minez-inspirate.blogspot.com/2009/07/create-load-balancing-router-using.html)
[http://www.linuxquestions.org/linux/answers/Networking/Spanning_Multiple_DSLs](http://www.linuxquestions.org/linux/answers/Networking/Spanning_Multiple_DSLs)
[http://chris.olstrom.com/blog/howto/setup-dual-wan/](http://chris.olstrom.com/blog/howto/setup-dual-wan/)
Please help .....

---

