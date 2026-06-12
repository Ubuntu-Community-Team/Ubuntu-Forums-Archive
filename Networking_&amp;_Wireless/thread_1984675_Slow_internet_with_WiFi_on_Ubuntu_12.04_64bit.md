---
title: "Slow internet with WiFi on Ubuntu 12.04 64bit"
date: 2012-05-22
forum: Networking &amp; Wireless
---

### Post by harsh2209 on 2012-05-22
Hi,

I have Ubuntu 12.04 LTS installed on my HP dv41120us laptop. 
Intel core 2 duo, 8 gb ram and 250 gb hard drive.

Have tried reinstalling, restarting etc.. but it stays the same... Any help would be much appreciated!!

I have attached the result of following herewith.

cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod

---

### Post by harsh2209 on 2012-05-22
I have updated the attachment with formatting for clear viewing. Apologize for the earlier version, it wasn't formatted at all!

---

### Post by harsh2209 on 2012-05-23
Hi All, could any one please help answer my issue..? I would highly appreciate that!

---

### Post by Loan_Refi on 2012-05-29
Hi there, I have Asus Zenbook UX31-DH52 + Ubuntu 12.04 LTS 64bit

I used these instructions to improve my wireless internet. I believe it might help you too;

[http://ubuntuforums.org/showthread.php?p=11765924](http://ubuntuforums.org/showthread.php?p=11765924)

Let me know if it helps!

---

### Post by dnukumamras on 2012-12-20
[B]Open a terminal (alt+ctrl+t)
type
 sudo rmmod -f iwlwifi

then
[/B] [B]sudo modprobe iwlwifi 11n_disable=1

now check if the speeds have improved. if yes lets make it permanent

type
[/B][B]gksudo gedit /etc/modprobe.d/iwlwifi_disable11n.conf

add the line

[/B]**options iwlwifi 11n_disable=1**

[B]to the end of the file.save and quit!!!:D


in-case you get an error like

ERROR: Removing 'iwlwifi': No such file or directory

replace iwlwifi with iwlagn in the above commands and try again.

[/B]

---

### Post by dnukumamras on 2012-12-20
[B]In case you are experiencing slow internet with Wifi on Ubuntu 12.04 try this:

[/B][B]Open a terminal (alt+ctrl+t)
type
 sudo rmmod -f iwlwifi

then
[/B] [B]sudo modprobe iwlwifi 11n_disable=1

now check if the speeds have improved. if yes lets make it permanent

type
[/B][B]gksudo gedit /etc/modprobe.d/iwlwifi_disable11n.conf

add the line

[/B]**options iwlwifi 11n_disable=1**

[B]to the end of the file.save and quit!!!:grin:


in-case you get an error like

ERROR: Removing 'iwlwifi': No such file or directory

replace iwlwifi with iwlagn in the above commands and try again.[/B]

---

