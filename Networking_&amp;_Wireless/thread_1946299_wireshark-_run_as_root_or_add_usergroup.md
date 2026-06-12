---
title: "wireshark- run as root or add usergroup"
date: 2012-03-24
forum: Networking &amp; Wireless
---

### Post by Ms. Daisy on 2012-03-24
I have installed wireshark from the software center.  When I run it, I have no capture options because I'm not root.  When I run it as root, wireshark warns me
```
Running as user "root" and group "root".
This could be dangerous.

If you're running Wireshark this way in order to perform live capture, you may want 
to be aware that there is a better way documented at
/usr/share/doc/wireshark-common/README.Debian
```I read the README file and either the documentation is obtuse or I am.  Here's what that file says:
```
Members of the wireshark group will be able to capture packets on network 
      interfaces. This is the preferred way of installation if Wireshark/Tshark
      will be used for capturing and displaying packets at the same time, since
      that way only the dumpcap process has to be run with elevated privileges 
      thanks to the privilege separation[1].

      Note that no user will be added to group wireshark automatically, the 
      system administrator has to add them manually.

      The additional privileges are provided using the Linux Capabilities
      system where possible or using the set-user-id bit, where the Linux 
      Capabilities are not present (Debian GNU/kFreeBSD, Debian GNU/Hurd).

      Linux kernels provided by Debian support Linux Capabilities, but custom
      built kernels may lack this support. If the support for Linux
      Capabilities is not present at the time of installing wireshark-common
      package, the installer will fall back to set the set-user-id bit to
      allow non-root users to capture packets.

      If installation succeeds with using Linux Capabilities, non-root users
      will not be able to capture packets while running kernels not supporting
      Linux Capabilities.
``` Seriously? Can someone translate the above passage for a mere mortal?  When I tried to follow it, I assume that apparently I need dumpcap?? I tried sudo apt-get install dumpcap and of course got "could not find package" because that would just make too much sense. So I typed dumpcap into the software center and found pcaputils. Why not- I installed that. Then I added a group "wireshark" and I added my user to that group.  But when I restart wireshark, I still don't get any capture options unless I'm running as root (even after I log out & log back in) ](*,)  

I found someone with the exact same problem as me, but the resolution offered seemed to be "just run as root."

[http://ubuntuforums.org/showthread.php?t=1868316](http://ubuntuforums.org/showthread.php?t=1868316)

So is that the only answer?  How can I allow my normal user to run wireshark?

---

### Post by Ms. Daisy on 2012-03-24
Solved this when I found this link:

[https://blog.wireshark.org/2010/02/running-wireshark-as-you/](https://blog.wireshark.org/2010/02/running-wireshark-as-you/)

---

### Post by sdgengineer on 2012-12-24
I had to use this:  But I am definitely a Newbee


[http://askubuntu.com/questions/105521/wireshark-problem-cant-select-default-interface](http://askubuntu.com/questions/105521/wireshark-problem-cant-select-default-interface)

to wit:

sudo chgrp your username /usr/bin/dumpcap 
sudo chmod 750 /usr/bin/dumpcap 
sudo setcap cap_net_raw,cap_net_admin+eip /usr/bin/dumpcap

You still need to run it as root if you want to look at the USB I/Fs

---

