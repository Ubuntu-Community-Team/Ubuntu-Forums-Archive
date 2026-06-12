---
title: "Lost internet connection HELP !!!"
date: 2011-08-02
forum: Networking &amp; Wireless
---

### Post by Bruv on 2011-08-02
I am a new convert to Ubuntu and was amazed when installing, how it does so much automatically such as connecting to the internet.
Now for some unknown reason I have lost that connection.
I have researched but cannot seem to work out what I am doing wrong.
I did a system test and found the results to tell me 
Intel Corp 82562 EZ 10/100
Ethernet Controller (rev.02)
Then the ominous
 Error:root; Could not find def Gateway info/proc
and
 Error:root; Could not find def Gateway by running route.

I have tried to manual edit my connection, but there are too many choices left empty.

Any help would be appreciated.

---

### Post by dineshs on 2011-08-03
Please post the results of the following terminal commands(applications-accessories-terminal) ```
sudo lshw -C network
ping 4.2.2.1 -c3
cat /etc/network/interfaces
```

---

### Post by Bruv on 2011-08-03
I am obviously unable to copy and paste and the two PC's are separated by a flight of stairs, but the output doesn't look relevant to me.....but I don't know anything.

Here it is....

Hardware Lister (lshw)-B.02.15
usage:lshw[-format][-options...]
lshw-version

-version  print program version (B.02.15)

format can be
- html    output hardware tree as html
-xml      output hardware tree a xml
-short     output hardware paths
-businfo   output bus information

And it goes on in a similar way.

---

### Post by Bruv on 2011-08-05
Just to clear everything up for anybody else with the same sort of problem, I moved the 2 PCs so I could work off the internet while fixing the problem on the faulty PC, and it turned out that it worked with no problem.


So the lesson is to check and double check your connections, because that is the only thing that could have been wrong

---

