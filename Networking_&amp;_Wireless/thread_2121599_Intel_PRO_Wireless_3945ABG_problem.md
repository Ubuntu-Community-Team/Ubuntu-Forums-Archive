---
title: "Intel PRO Wireless 3945ABG problem"
date: 2013-03-02
forum: Networking &amp; Wireless
---

### Post by EnesTesla on 2013-03-02
Hello ! 
Since i have installed Ubuntu, i cant use Wifi in my home, so i use Cable (LAN), at this moment :) 
Well, I can connect on network but Internet doesnt work, or sometimes working about 1-2 mins and stop ! 
I tried much things but nothing helps ! 
LAPTOP MODEL IS : HP nc6400
Maybe the problem is x64 Ubuntu

---

### Post by chili555 on 2013-03-02
I assume the driver is iwl3945; confirm:```
lsmod | grep iwl
```If so, please try:```
sudo modprobe -r iwl3945
sudo modprobe iwl3945 swcrypto=0 
```Now will it stay connected? If it helps, we'll write one quick file and make it persistent.

---

### Post by EnesTesla on 2013-03-02
enes@anon-PC:~$ lsmod | grep iwl
iwl3945                65160  0 
iwlegacy              104518  1 iwl3945
mac80211              540032  2 iwl3945,iwlegacy
cfg80211              206797  3 iwl3945,iwlegacy,mac80211
enes@anon-PC:~$ sudo modprobe -r iwl3945
[sudo] password for enes: 
WARNING: All config files need .conf: /etc/modprobe.d/ipwraw, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/iwl3945, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/iwlwifi.conf,, it will be ignored in a future release.
enes@anon-PC:~$ sudo modprobe iwl3945 swcrypto=0
WARNING: All config files need .conf: /etc/modprobe.d/ipwraw, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/iwl3945, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/iwlwifi.conf,, it will be ignored in a future release.

New in Ubuntu, sorry if I do something wrong :D 

Well, same **** again !

---

### Post by chili555 on 2013-03-02
Let's do some housecleaning. I think it's likely that you have some conflicts going.```
sudo rm /etc/modprobe.d/ipwraw 
sudo rm /etc/modprobe.d/iwl3945
sudo rm  /etc/modprobe.d/iwlwifi.conf
gksudo gedit /etc/modprobe.d/iwl3945.conf 
```Add a single line:```
options iwl3945 swcrypto=0
```Proofread, save and close gedit. Reboot and give us your report. Make sure any ethernet cables and/or USB wireless devices are detached.

After the reboot, does your wireless work better, worse or the same?

---

### Post by EnesTesla on 2013-03-02
Just follow what chili is saying, good job my friend and thanks for help :D ! [Solved] :D ! 

[COLOR=#333333][FONT=lucida grande]lsmod | grep iwl[/FONT][/COLOR]

[COLOR=#333333][FONT=lucida grande]sudo modprobe -r iwl3945[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]sudo modprobe iwl3945 swcrypto=0

(IF you get this WARNINGS like me) ---> 
sudo rm /etc/modprobe.d/ipwraw 
sudo rm /etc/modprobe.d/iwl3945
sudo rm /etc/modprobe.d/iwlwifi.conf

gksudo gedit /etc/modprobe.d/iwl3945.conf  
[/FONT][/COLOR]
alias wlan0 iwl3945
[COLOR=#333333][FONT=lucida grande]options iwl3945 disable_hw_scan=0 (Thats my iwl3945.conf file)[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]
or options iwl3945 swcrypto=0[/FONT][/COLOR]

---

### Post by chili555 on 2013-03-02
Glad it's working! Post back if we can help you in the future.

---

