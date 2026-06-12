---
title: "Ubuntu Studio hangs on restart/shut down"
date: 2018-09-01
forum: Multimedia Software
---

### Post by elisabethi on 2018-09-01
Hello! 

  I have installed Ubuntu Studio Bionic Beaver 18.04 64bit on my laptop  (HP Pavilion 17-ab440ng Notebook i5-8300H Full HD SSD GTX1050Ti) and  would like it to use it for audio & videoproduction. 

It boots very fast, but it hangs on restart/shut down. When I push shut down the screen turns black but it is still running and if I push restartit freezes with the Ubuntu Studio logo. 

I have tried already: sudo update-grub but it did not change. But the  command ( - journalctl -b -1 -n45) gave me more information about the  problem, as an attachment the log file  [ATTACH]280937[/ATTACH] 

I do not know, what to do.  Can anyone help me? 

Kind regards, 

  Elisabethi

---

### Post by elisabethi on 2018-09-03
I got an helpful advice from another user, the problem was aswell the NVIDIA® GTX™ graphic card.  For the installation I looked up in: [https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-ubuntu-18-04-bionic-beaver-linux]("https://deref-gmx.net/mail/client/TnZXBIYrQi4/dereferrer/?redirectUrl=https%3A%2F%2Flinuxconfig.org%2Fhow-to-install-the-nvidia-drivers-on-ubuntu-18-04-bionic-beaver-linux")

   First I detect the model of my nvidia graphic card and the recommended driver.

    $ ubuntu-drivers devices

and then I made the installation: 
 $ sudo apt install nvidia-396  

And now restart and shut down is working like it should :-)

---

