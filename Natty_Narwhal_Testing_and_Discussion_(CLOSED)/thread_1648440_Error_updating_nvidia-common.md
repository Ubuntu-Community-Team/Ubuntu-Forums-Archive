---
title: "Error updating nvidia-common"
date: 2010-12-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Quackers on 2010-12-18
I ran the update and it exited with an error 1 status.
But even after a reboot the system still loads ok and video seems unaffected. I then ran some apport updates and even though nvidia-common wasn't one of those updates the error came back.
So I ran sudo dpkg --configure -a and this is the response - if you can read it :-)  Any suggestions as to what needs to be done, please? Thanks.

---

### Post by cariboo on 2010-12-18
It may have something to do with the removal of nvidia-current-modaliases, there isn't an updated version of it yet.

---

### Post by Quackers on 2010-12-18
Aha! Thanks cariboo907. As it doesn't seem to affect anything I'm quite happy to await further updates :-)

---

### Post by jerrylamos on 2010-12-18
I get the nvidia error code 1 as well - on an IBM Thinkpad T40 with ati radeon graphics....

Jerry

---

### Post by ronacc on 2010-12-18
I think its a python problem from the looks of the error messages I get .

---

### Post by efflandt on 2010-12-18
Yes it looks like it has gone awol:

```
efflandt@natty-ssd:~$ sudo dpkg-query -l nvidia-common nvidia-settings nvidia-common-modaliases
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                        Version                     Description
+++-===========================-===========================-======================================================================
ii  nvidia-common               0.2.24build1                Find obsolete NVIDIA drivers
ii  nvidia-settings             260.19.21-0ubuntu2          Tool of configuring the NVIDIA graphics driver
No packages found matching nvidia-common-modaliases.
```I just reinstalled this morning from a zsync iso last night and top panel and menus were still unresponsive without doing compiz --replace or unity --reset.  But mid-day I rebooted to recovery and selected to fix broken packages, it did some more downloads.  That improved the top panel icons, which were gaudy gray default ones before, and improved the Unity icons.  And I can log in without having to kick compiz or unity.  So everything is working great for me at the moment.

---

### Post by Yellow Pasque on 2010-12-19
> **jerrylamos said:**
> I get the nvidia error code 1 as well - on an IBM Thinkpad T40 with ati radeon graphics....
I recommend removing nvidia-common if you don't have an nvidia card. This isn't the first time it's caused packaging problems and I wish it wouldn't be installed by default.

---

### Post by Harry33 on 2010-12-19
Nvidia-common (nor nvidia-modaliases) are not important packages after all.
You do not need them at all.
If you have a nvidia graphics card, all you have to know is, what driver supports it.
If you do not know, check that from nvidia search engine here:
[http://www.nvidia.co.uk/Download/index.aspx?lang=en-uk](http://www.nvidia.co.uk/Download/index.aspx?lang=en-uk)

For relatively new cards, just install the latest nvidia-current and nvidia-settings packages.
At the moment the latest stable version cannot be found on Natty's official repos.
But it can be found on xorg-edgers PPA.
Just download it from there and and install it with dpkg.

In terminal, run (now in the repos) for 64-bit:
sudo dpkg -i nvidia-current_260.19.29-0ubuntu1~xup1_amd64.deb

or run for 32-bit architecture:
sudo dpkg -i nvidia-current_260.19.29-0ubuntu1~xup1_i386.deb

And and addition here:
I made a bug report for the latest stable:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/692134](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/692134)

---

### Post by MacUntu on 2010-12-19
> **Temüjin said:**
> I recommend removing nvidia-common if you don't have an nvidia card. This isn't the first time it's caused packaging problems and I wish it wouldn't be installed by default.

Yeah, especially with kernel upgrades/removals it tends to be a PITA.

---

### Post by ronacc on 2010-12-19
I just did my morning update , Nvidia-common is back .additional drivers is working again .

---

### Post by Quackers on 2010-12-19
The problem seems to have passed now :-) Thanks all.

---

