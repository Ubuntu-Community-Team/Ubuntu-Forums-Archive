---
title: "MythTV Unmet Dependencies"
date: 2012-09-03
forum: Multimedia Software
---

### Post by ksanger on 2012-09-03
I have ubuntu 12.04 64-bit and am trying to install MythTV to watch an HDHomeRun Tuner.  Trying to install from the Software Package Manager I get a Package Dependencies Can Not Be Resolved Error.  Details states that the following packages have unmet dependencies.  MythTV.

I get the same error for the MythTV Front End and the Back End.

If I follow examples from some forum entries and use a terminal I get:

sudo apt-get install mythtv
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 mythtv : Depends: mythtv-database but it is not going to be installed
          Depends: mythtv-frontend but it is not going to be installed
          Depends: mythtv-backend but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

