---
title: "error in ftp terminal  while uplodaing/downloading"
date: 2013-08-11
forum: Networking &amp; Wireless
---

### Post by Rohit_Karadkar on 2013-08-11
This year in my engineering class We are learning OS and Doing Shell Programming.
I keep a backup of my work on FTP which used to work fine. 
But now I am getting this error, while uploading and download:
```

ftp> dir
500 I won't open a connection to 10.23.28.243 (only to 1.23.149.28)
ftp: bind: Address already in use

&

ftp> put asdf.sh
local: asdf.sh remote: asdf.sh
500 I won't open a connection to 10.23.28.243 (only to 1.23.149.28)
```
-I don't have college server access, please help me with this problem.

---

### Post by matt_symes on 2013-08-11
Hi  

Firewall issue ?  Try connecting in passive mode and see if that helps.  

Kind regards

---

