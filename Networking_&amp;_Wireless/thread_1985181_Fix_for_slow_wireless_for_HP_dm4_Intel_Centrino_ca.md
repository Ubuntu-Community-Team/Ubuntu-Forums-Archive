---
title: "Fix for slow wireless for HP dm4 Intel Centrino card in 12.04 Wubi"
date: 2012-05-23
forum: Networking &amp; Wireless
---

### Post by amoxicillin on 2012-05-23
I am using an HP dm4t (dm4x) and the wireless fix I used for 11.10 did not work in 12.04 LTS.  I didn't figure this out myself but found this online on a different forum and wanted to post it up here because this is what finally worked for me.  It may already be somewhere else but it never hurts to put it up for the noobs.

Open the terminal and type the following two lines:

sudo rmmod iwlwifi
sudo modprobe iwlwifi 11n_disable=1

If it works make it permanent by typing the following line in the terminal:

gksudo gedit /etc/modprobe.d/iwlwifi-disable11n.conf

A file will be opened. At the end of the file, paste the following line then save:

options iwlwifi 11n_disable=1

Then save and quit and you should be good to go.  The notes the person had posted said "at the end of the file" but my file didn't have any script to paste this at the end of.  I just pasted it their by itself and it seemed to work anyway.

---

### Post by SinkingRocket on 2012-08-11
thanks so much!! i just installed ubuntu 12.04 through wubi and the wifi connection was so slow but with the script u shared it was all running perfect.. thanks!

---

