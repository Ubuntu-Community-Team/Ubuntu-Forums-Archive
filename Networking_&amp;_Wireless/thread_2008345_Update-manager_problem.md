---
title: "Update-manager problem"
date: 2012-06-22
forum: Networking &amp; Wireless
---

### Post by guimadog on 2012-06-22
I can not update, i get this message

Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-input-synaptics/xserver-xorg-input-synaptics_1.5.99.902-0ubuntu5.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-input-synaptics/xserver-xorg-input-synaptics_1.5.99.902-0ubuntu5.1_amd64.deb) 404  Not Found [IP: 91.189.88.28 80]

I am also having problems with my wireless network. Right now I am connected by cable (live)

thanks for any help.

---

### Post by wildmanne39 on 2012-06-22
Hi, well the 404 issue is because either the server where the package is stored is down or it has been removed and this is the wrong place for that question.

As for wireless issues we need more information, what kind of problems are you having?

Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod

```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

