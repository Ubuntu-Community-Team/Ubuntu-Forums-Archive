---
title: "Strange, LAN slower than 1Mbps Internet !!!"
date: 2013-02-02
forum: Networking &amp; Wireless
---

### Post by ninadpchaudhari on 2013-02-02
Hi,
I am seriously confused !

 I have a Ubuntu Server running in my Home and a macbook Pro (both with 5400Rpm HDDs) 
the strange thing is, when i download a file from Internet over my Internet connection (in either my LAN connected Server or Router to WLAN connected MBP ), it requires same time as to Download from the internet ( I have a Barely 1Mbps(~120KBps) connection here) and to transfer .... 
How is that possible ! also some times when i get 2Mbps connection (~200KBps) from my ISP as per my I.Net plan , i can still access internet with that speed !

I mean , if my network can transfer the data with 2Mbps from Internet then why should i experience slow Connection with my Computers !

Btw, I have been using, 802.11n for MBP and router & Wired (Cat6 ,100Mbps) LAN to my Server ...
and the same stuff happens if i transfer my files from one WLAN PC to other as well !

---

### Post by alexii on 2013-02-03
Can't help without info. 

What kind of server (FTP/SFTP/CIFS/...)?


How are you connecting from inside (what client, what settings or commands)?


Possible that you are connecting to the server's external address from inside, when you should use the internal address from inside...

---

### Post by ninadpchaudhari on 2013-02-04
Oops forgot to mention .... It is Samba , and ya i am referring the internal address only !

As for client i am using the Native Finder connect ! also  same stuff with Windows machines as well :o

Tried FTP once via cyberduck , but did not really like FTP , as same problem and i have transfer the full file at a time !

---

### Post by CharlesA on 2013-02-04
Check the actual speeds with iperf:

[http://linuxaria.com/article/tool-command-line-bandwidth-linux?lang=en](http://linuxaria.com/article/tool-command-line-bandwidth-linux?lang=en)

---

