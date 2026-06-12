---
title: "usb_modeswitch not installing"
date: 2011-05-08
forum: Networking &amp; Wireless
---

### Post by frank_n on 2011-05-08
This machine used to have a DSL connection, it has currently
mobile broadband only. The surf stick works well under
Windows XP on same hardware. It is not even *recognized*
under ubuntu 10.4 LTS although it is a Huawei E1550 which
has a good ubuntu reputation. Lengthy search suggests that
the packages

usb-modeswitch-data
usb-modeswitch

have to be installed (in this order). I got them from the
10.4 repository using Windows and tried to install them in
ubuntu.

Failure with 'sudo apt-get install' although I'm acting as
superuser and permissions to the two deb-files are set to
666.

More precisely, installing usb-modeswitch-data seems to
succeed but installing usb-modeswitch fails. Reason given
is that usb-modeswitch-data is not installed.

Any suggestions what's going wrong and what could be done
about it?

---

### Post by SLIREAND on 2011-05-09
Please forgive my approach, frank_n, but we appear to have the same problem.

May i refer you to my post entitled "Huawei Mobile Broadband on 10.4 LTS" of six days ago.

Regards, Slireand

---

### Post by alexfish on 2011-05-09
Link

[Huawei Mobile Broadband on 10.4 LTS]("http://ubuntuforums.org/showthread.php?t=1747175")

can suggest looking at the debian (sid) links at the above , see what happens

alexfish

---

### Post by chili555 on 2011-05-09
apt-get install means go out on the internet and download and install these things. You already have them on your computer; what you want is:```
sudo dpkg -i usb*.deb
```dpkg -i means install the debs I already have.

---

### Post by frank_n on 2011-05-11
Good point and thank you very much, chilli555. Here is the follow-up.

I tried to install my two deb files with dpkg and was immediately deep in dependencies hell. Would I reboot into Windows and download the dependencies to get more dependencies again in the next iteration?

No. I just recalled sakis3g ([www.sakis3g.org](www.sakis3g.org)), a strange bash script with usb_modeswitch embedded in it as binary. It did the trick but I also had to remove NetworkManager that was bombarding me with error messages. 

And here we go again: when, oh when, are we going to get a decent network manager?

---

