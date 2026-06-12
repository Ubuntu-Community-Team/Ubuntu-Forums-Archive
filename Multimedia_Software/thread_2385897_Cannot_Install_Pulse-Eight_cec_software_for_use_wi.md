---
title: "Cannot Install Pulse-Eight cec software for use with mythtv"
date: 2018-02-26
forum: Multimedia Software
---

### Post by PaulRSte on 2018-02-26
I have a newly rebuilt Ubuntu 16.04.1 64-bit system with myth tv 0.28 installed. I have recently purchased a Pulse-Eight cec adapter and have set up the PPA for the software.  When I try and install the software I get an unmet dependency as follows:-

sudo apt-get install libcec libcec-dev cec-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 libcec-dev : Depends: libcec4 (= 4.0.0.1~xenial) but 4.0.2.1~xenial is to be installed
E: Unable to correct problems, you have held broken packages.

Can anyone help please?

---

### Post by cruzer001 on 2018-02-26
4.0.0.1 was last used in Wily (15.10).

[https://launchpad.net/~pulse-eight/+archive/ubuntu/testing](https://launchpad.net/~pulse-eight/+archive/ubuntu/testing)

You could add it to your sources, but no way of knowing what will happen next.

Is this your download source?

[http://libcec.pulse-eight.com/Downloads](http://libcec.pulse-eight.com/Downloads)

---

### Post by PaulRSte on 2018-02-26
Hope I have the correct info - from "Software & Updates" on th "Other Software" tab:-  [http://ppa.launchpad.net/pulse-eight/libcec/ubuntu](http://ppa.launchpad.net/pulse-eight/libcec/ubuntu)

---

### Post by deadflowr on 2018-02-26
Try installing the libcec4-dev instead of libcec-dev.

---

### Post by PaulRSte on 2018-02-26
Have installed libcec libcec4-dev cec-utils
Have also added user to dialout group. From myth tv front end log:-

Feb 26 18:53:15 PVR-1 mythfrontend.real: mythfrontend[4178]: E CoreContext cecadapter.cpp:150 (Open) CECAdapter: Failed to load libcec.

---

### Post by cruzer001 on 2018-02-26
Usually depends will require a package equal to or greater than ([COLOR="#FF0000"]>=[/COLOR]). 

But in this case
> libcec-dev : Depends: libcec4 ([COLOR="#FF0000"]=[/COLOR] 4.0.0.1~xenial) but 4.0.2.1~xenial is to be installed
its asking for a exact version.  

Thats why I ask about the above download site.  It shows "libcec4_4.0.2" and ARM architecture.  Is this a Raspberry?

---

### Post by PaulRSte on 2018-02-26
ARM architecture is used in the Raspberry Pi, smart phones, and tablets. My system is a quad core AMD FX-4300 with Nvidia graphics card.

Re the version numbers, forcing this by installing libcec4-dev, got the installation done ok, but mythfrontend can't connect (see my previous reply above). I have seen that mythfrontend will only work with libcec-utils version 1 and not later versions. I've tried just installing libcec-dev without the libcec and cec-utils but I get the same error message. Any way that I can amend that dependency on my system just to try it out?

---

### Post by cruzer001 on 2018-02-26
You seem to have chosen to ignore my posts, but thats ok.

):P

---

### Post by PaulRSte on 2018-02-26
Not ignoring your posts at all cruzer001. I wasn't sure what you meant me to do especially as you said you weren't sure what would happen next. I was hoping for another response from you. 
The reply from deadflowr made sense though. I tried to install libcec libcec-dev cec-utils but it tried to install libcec4 and cec-utils4 (or cec4-utils) but not libcec4-dev.  Seemed like t was worth trying.  It did install but as I said above, I've seen that mythfrontend requires libcec-dev.  That's why I wondered if it was possible to amend the dependency on this on my system only. Or does this need passing back to Pulse-Eight?

---

### Post by PaulRSte on 2018-02-27
I have added the PPA for Pulse-Eight testing, unticked the standard PPA, and tried installing libcec-dev and it still returns the same installation error. Not sure what else to try.

---

### Post by cruzer001 on 2018-02-27
Installed from:
[https://launchpad.net/~pulse-eight/+archive/ubuntu/libcec?field.series_filter=xenial](https://launchpad.net/~pulse-eight/+archive/ubuntu/libcec?field.series_filter=xenial)


```
[COLOR="#FF0000"]~$ sudo add-apt-repository ppa:pulse-eight/libcec
[/COLOR]
https://github.com/Pulse-Eight/libcec
more details available at http://libcec.pulse-eight.com/
 More info: https://launchpad.net/~pulse-eight/+archive/ubuntu/libcec
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpolm916cf/secring.gpg' created
gpg: keyring `/tmp/tmpolm916cf/pubring.gpg' created
gpg: requesting key 5F6EB4BE from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpolm916cf/trustdb.gpg: trustdb created
gpg: key 5F6EB4BE: public key "Launchpad PPA for Pulse-Eight" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK

~$ [COLOR="#FF0000"]sudo apt-get update[/COLOR]
             Reading package lists... Done

~$ [COLOR="#FF0000"]sudo apt install libcec[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  libcec4 libp8-platform2
The following NEW packages will be installed:
  libcec libcec4 libp8-platform2
0 upgraded, 3 newly installed, 0 to remove and 46 not upgraded.
Need to get 267 kB of archives.
After this operation, 785 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://ppa.launchpad.net/pulse-eight/libcec/ubuntu xenial/main i386 libp8-platform2 i386 2.1.0.1~xenial [20.1 kB]
Get:2 http://ppa.launchpad.net/pulse-eight/libcec/ubuntu xenial/main i386 libcec4 i386 4.0.2.1~xenial [218 kB]
Get:3 http://ppa.launchpad.net/pulse-eight/libcec/ubuntu xenial/main i386 libcec i386 4.0.2.1~xenial [28.1 kB]
Fetched 267 kB in 4s (56.6 kB/s)
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
Selecting previously unselected package libp8-platform2:i386.
(Reading database ... 170805 files and directories currently installed.)
Preparing to unpack .../libp8-platform2_2.1.0.1~xenial_i386.deb ...
Unpacking libp8-platform2:i386 (2.1.0.1~xenial) ...
Selecting previously unselected package libcec4:i386.
Preparing to unpack .../libcec4_4.0.2.1~xenial_i386.deb ...
Unpacking libcec4:i386 (4.0.2.1~xenial) ...
Selecting previously unselected package libcec.
Preparing to unpack .../libcec_4.0.2.1~xenial_i386.deb ...
Unpacking libcec (4.0.2.1~xenial) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Setting up libp8-platform2:i386 (2.1.0.1~xenial) ...
Setting up libcec4:i386 (4.0.2.1~xenial) ...
Setting up libcec (4.0.2.1~xenial) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...

~$ [COLOR="#FF0000"]apt policy libcec[/COLOR]
libcec:
  Installed: 4.0.2.1~xenial
  Candidate: 4.0.2.1~xenial
  Version table:
 *** 4.0.2.1~xenial 500
        500 http://ppa.launchpad.net/pulse-eight/libcec/ubuntu xenial/main i386 Packages
        100 /var/lib/dpkg/status

~$ [COLOR="#FF0000"]apt policy libcec4[/COLOR]
libcec4:
  Installed: 4.0.2.1~xenial
  Candidate: 4.0.2.1~xenial
  Version table:
 *** 4.0.2.1~xenial 500
        500 http://ppa.launchpad.net/pulse-eight/libcec/ubuntu xenial/main i386 Packages
        100 /var/lib/dpkg/status
```

I only have a 32bit version of 16.04 to play with, but it installed without issue.  Maybe clean everything out, go back to default and try again.

---

### Post by PaulRSte on 2018-02-27
Thanks for your reply cruzer001 but it is libcec-dev that has the dependency issue. I have literally just solved it though, details below. I hadn't seen your reply as it was on the next page which I hadn't noticed. 
 
I have been looking at buying the Pulse Eight CEC adapter for over a year but was waiting until I had rebuilt my system. That done, I bought one in January, applied the PPA, tried installing the required routines and got a dependency error - wrong version on one of the modules. Having got nowhere with this issue I started looking at the myththtv packaging on Git Hub but all it said was libcec-dev as a dependency. So I started wondering if myhthtv 0.29 would be the way to go and I googled "what version mythtv with ubuntu 18.04". Whilst it mentioned libcec-dev, it didn't mention a version, but it was listed as a hyperlink. So I clicked on it and it came up with the package details and it showed as version 4.01. I realised then that it is included in 18.04. So I searched for "what version mythtv with ubuntu 16.04" and it is version 3.01 which is lower than the one on the Pulse Eight PPA, and is available as standard. So

1) Completely Removed the packages libcec4, cec-utils and libcec4-dev using Synaptic Package Manager
2) Unticked the Pulse-Eight PPA on Software & Updates "Other Software" tab and exited, choosing "Reload" to update the software cache 
3) Used Synaptic Package Manager to install libcec, libcec-dev and cec-utils
4) Rebooted and hey presto

I haven't come across anything that says that these routines are available in xenial. Everything I've seen points to using the PPA.. Just have to delete the PPA from Software & Updates

Thanks to all who helped with this. Other input is always useful as it provides food for thought and often helps point you in the right direction

---

