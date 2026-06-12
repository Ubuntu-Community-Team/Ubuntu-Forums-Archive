---
title: "SSHing into a Virtual Machine with a Static IP address?"
date: 2010-01-11
forum: Networking &amp; Wireless
---

### Post by StanleyKodak on 2010-01-11
So far, I have VirtualBox set up (hosting on windows 7) with a very minimalistic setup, only having the core, irssi, and ssh (not even a gui), which is configured to run through a bridged connection via the VM software, and Putty, for my client.

I can use Putty to SSH to the virtual machine (from the host machine) and that's working all nicely, but I'm not sure how to SSH to the machine from other machines, since I've been referring to the internal IP address ( 192.168.1.8 ).

How would I go about referring to it from non-host computers?  I heard a friend of mine mention something about 'port forwarding.'

Also, on another, related note, at one place that I would SSH from, port 22 is blocked.  Is there any (somewhat easy) way to get around this fact.  I'm using Portable Putty at this place as well.

Thank you very much for you time,
Stanley Kodak.

---

### Post by johnson.d on 2010-01-12
you can use these two links for port forwarding in virtual box

[http://tombuntu.com/index.php/2008/12/17/configure-port-forwarding-to-a-virtualbox-guest-os/](http://tombuntu.com/index.php/2008/12/17/configure-port-forwarding-to-a-virtualbox-guest-os/)

[http://www.virtualbox.org/manual/UserManual.html#natforward](http://www.virtualbox.org/manual/UserManual.html#natforward)

---

### Post by StanleyKodak on 2010-01-13
> **johnson.d said:**
> you can use these two links for port forwarding in virtual box

[http://tombuntu.com/index.php/2008/12/17/configure-port-forwarding-to-a-virtualbox-guest-os/](http://tombuntu.com/index.php/2008/12/17/configure-port-forwarding-to-a-virtualbox-guest-os/)

[http://www.virtualbox.org/manual/UserManual.html#natforward](http://www.virtualbox.org/manual/UserManual.html#natforward)

those seem to all assume that you have Linux as your host OS. I'm using windows 7 as my host.

---

### Post by johnson.d on 2010-01-18
'vboxmanage.exe' is generally in c:\Program Files\Sun\VirtualBox on Windows installations. You can either add this directory to the windows path or alternatively cd into that directory and run the command.

1) For running the commands you can go to the sun virtual box directory by using the command

  cd \Program Files\Sun\VirtualBox

2) After changing the directory try the commands given in the procedure

---

