---
title: "Upgraded to 0.28"
date: 2016-05-18
forum: Mythbuntu
---

### Post by gga96 on 2016-05-18
I am upgrading my systems from 0.27 to 0.28 and would appreciate any advice  you can offer.
  
 There are two BE MythTV boxes.
  
 The first box is for “Active” MythTV which also has a remote FE, this  system has been upgraded from Mythbuntu 0.27 to 0.28 but Ubuntu remains at  14.04.
  
 The second box is set up as an “R&D” machine with a clean Mythbuntu  0.28 ISO install and with Ubuntu 16.04. I have used ansible to provide the  dependencies, downloaded source, clean compiled and installed MythTV. All very  clean. Well done to those responsible!
  
 I would like to upgrade the “Active” system to Ubuntu 16.04  and [http://www.omgubuntu.co.uk/2016/04/how-to-upgrade-ubuntu-14-04-to-ubuntu-16-04-lts](http://www.omgubuntu.co.uk/2016/04/how-to-upgrade-ubuntu-14-04-to-ubuntu-16-04-lts) explains  how to do the upgrade, but I am not sure what will happen!
     Q 1: Will I lose the attractive and simple Mythbuntu Menu GUI?
     Q 2: Will “Active” and “R&D” be the same from a coding, technical  point of view?
     Q 3: if Q 2 is negative can I avoid a complete ISO install of “Active”  and the required post install procedures? 
     Q 4: Will a DB backup of “Active” restore to a new install of ISO 0.28  on “Active”?
  
 Thank you for your interest.
  
 Regards
 Glen

---

### Post by blm-ubunet on 2016-05-19
When the first point release of 16.04 is made then 16.04-LTS upgrade will be offered to 14.04-LTS users (who have selected to stay on LTS).

I fairly sure mythbuntu has 16.04 & mythtv 0.28 & master builds in their repo.
[https://launchpad.net/~mythbuntu/+archive/ubuntu/0.28?field.series_filter=xenial](https://launchpad.net/~mythbuntu/+archive/ubuntu/0.28?field.series_filter=xenial)

There is a simple command to upgrade release (if avail) : "do-release-upgrade -c"
You can force this to upgrade before LTS-upgrade is signalled.. but what's the rush?

My BE was still running 10.04 a year ago (albeit with lots of manually upgraded packages)..

---

### Post by gga96 on 2016-05-19
Thanks blm-ubunet.

I would like to bring the "Active" machine to the same development state as "R&D".

As things stand at the moment ansible versions vary on "R&D" it is 2.0.0.2-2 and on "Active" it is 1.5.4, this difference appears to be due to ubuntu version. 

The "dnf" bug fix recommended by searches is to comment out the 'dnf' references, I tried that but it still fails. Ansible is brilliant and I want it to satisfy the dependencies required.  

I am still curious about the answers to the 4 questions asked in the previous post, any thoughts?

Regards
Glen

---

### Post by blm-ubunet on 2016-05-19
The latest released 0.28 MythTV can directly upgrade the database schema from version 0.22 or higher.

You're just transferring a database between to separate systems of the same version so should be fine.
I'd make sure the "recipient" is exactly same or higher schema level than the donor.

Are you building 0.28 from source on both your production & development machines ?
When you build your own code for other machines have be careful to support the required arch & libc versions etc.

Do you want to make a deb package that can then be installed on the other machine(s)?

Active has a remote FE to what exactly?

---

### Post by gga96 on 2016-05-20
Thanks again blm-ubunet.

> Are you building 0.28 from source on both your production & development machines ?
No. I wish to create an app that works with myth.  I installed with an ISO .28 on "R&D", it is used as a scratch pad to translate code from my developments on Windows to Qt in the Myth environment. I compiled .28 to get the object and .so library files because mythdb, mythplayer and possibly other libraries are required for the interface to myth data. When this stage of development is sound I then intend to take the code to "Active" and test and debug against myth. That is why I want the two systems to have the same status. The app is relatively simple but Qt and Linux are new environments for me, I need to keep it simple.
"Active" has existed since 2013 and upgraded to it's current state, I am not going to build from source, only compile to get the required .so libraries I need.

> Do you want to make a deb package that can then be installed on the other machine(s)?
If the app is as successful as I think it can be, that will be the time to go to open source and make a deb package.

> Active has a remote FE to what exactly?
This system is the original 2013 installation.  BE + local FE in the study and Ethernet cable to FE in the lounge. Has worked very well.

I will wait until "do-release-upgrade -c" comes up with a change before I do anything with "Active".

---

### Post by blm-ubunet on 2016-05-20
Just my POV & could be wrong..
Linking your code to the binary ABI is a bad idea, unless your code becomes part of mythtv.
You need to link to a public documented stable ABI.
You could use the services API or language bindings (perl/python).
I think the developers are willing to accept ideas for services enhancements if required.

Qt is a great thing.. I cooked up a simple browser, just as a test, with about 10 lines of code. Amazing.

---

### Post by gga96 on 2016-05-20
I am very pleased to get your POV thank you  blm-ubunet, I need  it.

The combination of Linux and Qt leaves me feeling like a fish out of  water. It is vital to create the correct development environment from the  start.
> You could use the services API or language bindings  (perl/python).
The recent Silence release prompted my current  endeavors. Having studied the code I thought the libraries lacked the  functionality I required.
 Like Silence my code also requires tweaking to  best deal with local Free To Air TV. A small data set held in CSV text files  stores persistent data about the channel icons and the associated RGB signature  and techniques to be applied. A GUI manages the acquisition and maintenance of  icon data, whilst a Data Module deals with the Myth interface, CSV files and  code to achieve a flagged outcome. I expected to use libraries in the &#8216;libs&#8217;  directory of the build tree. The functionality involved is: Array of video index, Random  access to indexed video frames and SQL via  mythdb.
 I am happy to become part of Mythtv. I  thought the code could be inserted into the build tree as a child of the  &#8216;programs&#8217; directory, this is my first choice for development and  testing. Later the Data Module code could become a child of &#8216;mythcommflag&#8217; but  the need for random user GUI maintenance must be  serviced.

Should we move this topic to mythtv-dev?

Regards
Glen

---

