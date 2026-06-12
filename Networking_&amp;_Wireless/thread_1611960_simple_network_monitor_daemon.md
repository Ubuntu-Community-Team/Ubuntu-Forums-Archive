---
title: "simple network monitor daemon"
date: 2010-11-02
forum: Networking &amp; Wireless
---

### Post by BcRich on 2010-11-02
hi 
i have been looking for a simple network monitor daemon for ubuntu, for some time but have not found anything that suits my requirements and from what i've been reading online there seems to be quite alot of other people out there that are looking for the same thing.
this [http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html) page seems to have the most comprehensive list of similar products but if you read through all of them they don't seem to be what i'd imagine most home users need.
here's a list of what i had in mind, if any one uses something that has these features or knows of something that might meet these requirements please let us know!
1)a small lightweight daemon that can be accessed via the panel on gnome
2)has thee ability to monitor eth or ppp (particularly internet traffic)
3)can represent this data in a human readable format ie using megabytes and gigabytes
4)can store a history of how much data is being sent and received over long periods of time (like several months)
something like this would be very useful for home users accessing the internet via dialup that have a cap on their data.
any help would be greatly appreciated.

---

### Post by sedawk on 2010-11-02
I think that data is available from the command line.

You can have a look at
[CODE]
netstat -i
#or
ethtool -S eth0
#or
sar -n DEV eth0
[CODE]

There might be graphical frontends (especially for the sar stuff).

If you are using a DSL router it also might collect that
data for you and show it on some internal web page.
Many ISPs who have a limit also provide a web page to show
the current counters. Reading that data might require some
scripting and usage of curl or wget.

---

### Post by BcRich on 2010-11-04
Hi sedawk
Thanks for your suggestions. gave them a try, not to sound harsh or ungrateful, but I cannot say that I particularly liked any of them, sorry :)
nonetheless, thanks very much for your help

---

