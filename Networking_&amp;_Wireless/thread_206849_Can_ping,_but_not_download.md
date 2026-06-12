---
title: "Can ping, but not download?"
date: 2006-06-30
forum: Networking &amp; Wireless
---

### Post by Picatta on 2006-06-30
OK, I just installed ubuntu 6.06, and it works like a charm, finding all hardware.  Anyway, after I installed it, there was a bubble saying updates were available, and so I downloaded them.  This made me think that I had internet, so I pinged google.  I got a responce, lilke 200 ms.  I was then shure I had internet.  So I fired up firefox and tried to open google.com, but it didn't work.  It sat for a while and gave a timeout error.

I thought it was a problem with firefox, so I tried wget google.com.  It pinged successfully, but then hung when download the page.  

What is going on?

Oh, the network is dhcp, all the info is correct, and I can connect to my router and to other computers on the network.

---

### Post by invalid on 2006-06-30
[QUOTE=Picatta]OK, I just installed ubuntu 6.06, and it works like a charm, finding all hardware.  Anyway, after I installed it, there was a bubble saying updates were available, and so I downloaded them.  This made me think that I had internet, so I pinged google.  I got a responce, lilke 200 ms.  I was then shure I had internet.  So I fired up firefox and tried to open google.com, but it didn't work.  It sat for a while and gave a timeout error.

I thought it was a problem with firefox, so I tried wget google.com.  It pinged successfully, but then hung when download the page.  

What is going on?

Oh, the network is dhcp, all the info is correct, and I can connect to my router and to other computers on the network.[/QUOTE]
Ping usually first resolves the canonical name into an IP. What happens if you try to visit a website using the IP ( example for google.com would be [http://64.233.167.99/](http://64.233.167.99/) )

You may be having problems resolving into the actual address.

---

### Post by eholly on 2006-07-01
I have had problems with connecting to google with Dapper.  It seems to be intermittent.  Sometimes re-booting or waiting a day seems to correct the problem.  Disableing ipv6 in two places has cured this.  Some of the advice in other threads say that doing so will speed up firefox and epiphany and not harm anything on a desktop instalation.  Note: some other sites load fine.  Evidently google (and others) use ipv6 and may change their use frequently.

To disable ipv6 in firefox and epiphany,
          clear the address bar
          Type in "about:config" enter>
          Type in "ipv"  in the filter window
                     "network.dns.disableIPv6   default   boolean   false" 
                            should appear in the window below.
            Double click on it and it should change to 
                          "network.dns.disableIPv6    user set    boolean   true"
                             should appear in the window.
           go to your google bookmark.




To disable ipv6 in /etc/modporbe.d/aliases file, using sudo privieges,
                       # the "alias net-pf-10 ipv6" line and add
                        "alias net-pf-10 ipv6 off
                         alias net-pf-10 off
                         alias ipv6 off"         

so that it looks like.

                        #alias net-pf-10 ipv6
                        alias net-pf-10 ipv6 off
                        alias net-pf-10 off
                        alias ipv6 off

I haven't had problems accessing any of my bookmarks with a browser since doing the above and the browsers seem to load much faster.

                   E Holly

---

### Post by genreviam on 2006-07-02
Thanks EHolley. That was my exact problem and your suggestion fixed it.

---

