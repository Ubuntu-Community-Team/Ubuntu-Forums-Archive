---
title: "Hauppauge WinTV-HVR-950 problems"
date: 2009-11-14
forum: Multimedia Software
---

### Post by kcihtred2 on 2009-11-14
ok ive tried to install my tv stick and this is what ive gotten...
> 
andrew@andrew-desktop:~$ su -
Password: 
root@andrew-desktop:~# wget [http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip](http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip)
--2009-11-14 15:20:22--  [http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip](http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip)
Resolving [www.steventoth.net](www.steventoth.net)... 97.74.144.190
Connecting to [www.steventoth.net|97.74.144.190|:80](www.steventoth.net|97.74.144.190|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1545106 (1.5M) [application/zip]
Saving to: `HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip'

100%[======================================>] 1,545,106    643K/s   in 2.3s    

2009-11-14 15:20:25 (643 KB/s) - `HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip' saved [1545106/1545106]

root@andrew-desktop:~# unzip -j HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip Driver85/hcw85bda.sys
Archive:  HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip
  inflating: hcw85bda.sys            
root@andrew-desktop:~# cd /usr/src/linux-headers-2.6.31-14/Documentation/video4linux
root@andrew-desktop:/usr/src/linux-headers-2.6.31-14/Documentation/video4linux# ls
extract_xc3028.pl  Makefile
root@andrew-desktop:/usr/src/linux-headers-2.6.31-14/Documentation/video4linux# chmod +x extract_xc3028.pl
ls
extract_xc3028.pl  Makefile
root@andrew-desktop:/usr/src/linux-headers-2.6.31-14/Documentation/video4linux# ./extract_xc3028.pl
md5sum: hcw85bda.sys: No such file or directory
Hash of extracted file does not match (found , expected 0e44dbf63bb0169d57446aec21881ff2!
root@andrew-desktop:/usr/src/linux-headers-2.6.31-14/Documentation/video4linux#  


the extract_xc3028.pl is green so it is modable
anyone no what im doing wrong?

---

