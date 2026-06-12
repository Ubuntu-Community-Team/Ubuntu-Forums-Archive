---
title: "How to get Wireless working on Samsung N130"
date: 2010-10-04
forum: Networking &amp; Wireless
---

### Post by graeme2912 on 2010-10-04
First download the file at this link 

[http://www.megaupload.com/?d=9XR33G1X](http://www.megaupload.com/?d=9XR33G1X)

In Terminal run the following commands

cd Downloads

tar -zxvf rtl819Xe.tar.gz

                                 cd Downloads/rtl819Xe


                                  sudo su


                                  ./install.sh


----------------------------------------------------------------------------------------



If the wireless isn't working on boot


Run in terminal the following commands


                                  
sudo rmmod r8192_pci


sudo modprobe r8192_pci

---

### Post by graeme2912 on 2010-10-04
its my first post so tell me if i missed anything

---

