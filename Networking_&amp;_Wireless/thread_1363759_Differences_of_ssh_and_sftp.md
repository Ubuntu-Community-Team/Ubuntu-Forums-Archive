---
title: "Differences of ssh and sftp?"
date: 2009-12-24
forum: Networking &amp; Wireless
---

### Post by shade5 on 2009-12-24
Hi,

I am amazed of the possibilities of ssh. Now I wonder what the differences between those two protocols are. sftp is said to be based on ssh. So if I connect to a sshd with nautilus, could I somehow use the binaries through nautilus? Basically I want to know if sftp is just a graphical view of a shell or if it only uses some features of ssh that it can be used for file transfer but nothing more.

And how could I execute scripts or binaries with nautilus on the sshd? 

Many many thanks.

---

### Post by alancop on 2009-12-24
SFTP is just the FTP protocol that is secured with SSH. So all the features of FTP are available but secure.  As far as I know you can not run binary remotely with Nautilus.

---

### Post by shade5 on 2009-12-24
Are there any apps that let you use a graphical file manager + executing binaries?

---

### Post by prshah on 2009-12-24
> **shade5 said:**
> sftp is said to be based on ssh. So if I connect to a sshd with nautilus, could I somehow use the binaries through nautilus? 

sftp is a "subset" of ssh; it runs "on" ssh. While nautilus can display and interact over sftp, it cannot run binaries over sftp.

However, if you ssh to your machine with the -X option (X11 forwarding) you CAN run binaries (including Nautilus and whatever else it may launch). However, my experience of running binaries over SSH has been rather bad, with a lot of unresponsiveness. That may be because I have a (relatively) slow Internet connection.

I suggest that a remote control solution (like VNC) over SSH will be a far better idea for you; unless you have a specific need to use an application remotely (can't think of one, though).

---

### Post by Dennis N on 2009-12-25
**Running Remote Applications**:

Here is an article on how to run remote applications with SSH:

[http://linuxplanet.com/linuxplanet/tutorials/6874/1/](http://linuxplanet.com/linuxplanet/tutorials/6874/1/)

see the section "**Running Remote Applications**" on the second page.

---

