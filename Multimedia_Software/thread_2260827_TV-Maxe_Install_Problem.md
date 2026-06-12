---
title: "TV-Maxe Install Problem"
date: 2015-01-14
forum: Multimedia Software
---

### Post by Rick St. George on 2015-01-14
Attempting to install TV-MAXE, using these commands;

> 
sudo add-apt-repository ppa:venerix/pkg
sudo apt-get update
sudo apt-get install tv-maxe

 and get the following ...


> 
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 tv-maxe : Depends: sp-auth:any
           Depends: python-virtkey but it is not installable
           Recommends: rtmpdump but it is not installable
E: Unable to correct problems, you have held broken packages.


Anyone have any idea how to resolve?
Running Latest UbuntuStudio LTS 14+
Thanks!
Rick
:popcorn:

---

