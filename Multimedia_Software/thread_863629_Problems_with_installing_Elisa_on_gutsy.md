---
title: "Problems with installing Elisa on gutsy"
date: 2008-07-18
forum: Multimedia Software
---

### Post by zeezam on 2008-07-18
I got this message:
[Screenshot]("http://static.pici.se/pictures/XYwVXwfWL.gif")

Tried both synaptic and apt-get install.

Any ideas?

Followed this guide without success; [http://elisa.fluendo.com/packages/](http://elisa.fluendo.com/packages/)

Here is what I get in the terminal:

[I]htpc@htpc:~$ sudo apt-get install elisa
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  elisa: Depends: elisa-core but it is not going to be installed
         Depends: elisa-plugins-good but it is not going to be installed
         Depends: elisa-plugins-bad but it is not going to be installed
E: Broken packages
htpc@htpc:~$ [/I]

---

