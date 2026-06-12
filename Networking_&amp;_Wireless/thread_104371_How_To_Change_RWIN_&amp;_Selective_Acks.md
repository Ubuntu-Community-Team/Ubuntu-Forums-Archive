---
title: "How To Change RWIN &amp; Selective Acks?"
date: 2005-12-16
forum: Networking &amp; Wireless
---

### Post by ephman on 2005-12-16
hi,

i need to change my RWIN setting.  i'm not sure how to make that change.  also, does anybody know how to turn on selective acks?

thanks for the bandwidth,
ephman

---

### Post by ape on 2005-12-16
Take a look at this [http://www.santa-li.com/linuxonbb.html]("http://www.santa-li.com/linuxonbb.html") site.  It has some info on which settings you need to modify in your sysctl.conf file.

---

### Post by ephman on 2005-12-16
hi,

cool thanks, that's a great start.  but now i'm confused as to what files i need to change?  sorry although i'm a longtime linux user, i'm no networking genius.  

thanks for the bandwidth,
ephman

---

### Post by Lambert on 2005-12-16
This is my sysctl.conf file

#increase TCP maximum buffer size
net.core.rmem_max = 16777216
net.core.wmem_max = 16777216

# increase linux autotuning TCP buffer limits
net.ipv4.tcp_rmem = 4096 87380 16777216
net.ipv4.tcp_wmem = 4096 65536 16777216

# don't cache ssthresh from previous connection
 net.ipv4.tcp_no_metrics_save = 1
 # recommended to increase this for 1000 BT or higher
 net.core.netdev_max_backlog = 2500

Once you change these run the command

sudo sysctl -p

A link about this.

[http://dsd.lbl.gov/TCP-tuning/linux.html](http://dsd.lbl.gov/TCP-tuning/linux.html)

A couple others I use

net.ipv4.tcp_timestamps = 0
net.ipv4.tcp_sack =1
net.ipv4.tcp_window_scaling = 1

Another link

[http://www.speedguide.net/read_articles.php?id=121](http://www.speedguide.net/read_articles.php?id=121)

On this link there is a link tcp/ip analyzer. Run this link before you make changes and note the info, then re-run it after you make the changes to see the difference

---

### Post by Galban on 2007-03-24
Thanks...it works. Good to know about this!

---

