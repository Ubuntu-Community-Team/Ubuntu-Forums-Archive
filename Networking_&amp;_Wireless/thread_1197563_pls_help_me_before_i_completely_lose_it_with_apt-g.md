---
title: "pls help me before i completely lose it with apt-get"
date: 2009-06-26
forum: Networking &amp; Wireless
---

### Post by fourtyseven on 2009-06-26
I am so frustrated right now I could just crap! For the past week I have been trying to setup a repository server for some of my students (I teach IT). However, I have encountered a problem which I have not been able to solve and I dont know why.
Firstly I made a fresh installation of 8.10. We connect to the internet through a wired lan via a proxy. When I type sudo apt-get install apt-cacher-ng, I get the following error:
> reading package lists... Done
building dependency tree
reading state information... done
E: couldn't find package apt-cacher-ng

No matter what I do I cannot download anything using apt-get or even aptitude. I can however browse the internet using Mozilla.
Can somebody please tell me what Im doing wrong. The funny thing is that my computer in my office on the same network behind the same proxy can do it without a problem.
Im seriously considering shooting someone over this. Help me!

---

### Post by fourtyseven on 2009-06-26
PS I also cannot update Synaptics Package Manager as it tells me it failed to fetch the necessary archives. I have checked the sources.list and everything seems fine. My IP address is fine and I have used the relevant proxy settings.

---

### Post by Sef on 2009-06-26
> Quote:
                                                 reading package lists... Done
building dependency tree
reading state information... done
E: couldn't find package apt-cacher-ng                      Synaptic > Settings > Repositories:

Is Community-maintained Open Source software (universe) enabled?

> PS I also cannot update Synaptics Package Manager as it tells me it failed to fetch the necessary archives. I have checked the sources.list and everything seems fine. My IP address is fine and I have used the relevant proxy settings.

System > Administration > Software Sources > Ubuntu Software:

Change Download From to a different server.

---

### Post by statistic on 2009-06-26
This could be the issue:

"apt: Not possible to use an @ (at sign) in username or password of a proxy"
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=500560](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=500560)

Edit: This issue appears to have been resolved though.

---

### Post by jimv on 2009-06-26
Can you post the output of "sudo apt-get update"?

---

