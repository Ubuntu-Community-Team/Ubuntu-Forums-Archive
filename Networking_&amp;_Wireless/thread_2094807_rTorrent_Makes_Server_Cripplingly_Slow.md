---
title: "rTorrent Makes Server Cripplingly Slow"
date: 2012-12-14
forum: Networking &amp; Wireless
---

### Post by snowman4839 on 2012-12-14
I've set up my home desktop to run as a VNC/FTP server using tightvnc and filezilla for torrents on Windows XP and everything was super fast and worked great but I wanted to switch everything to linux

Installed Mint 14 (I know not ubuntu but I like this forum and it's debian based anyway) desktop and made it a SSH/FTP box instead. Used sshd and ftpd. Those work pretty well. I've been trying to find a good CLI torrent interface and finally went with rTorrent for it's easy use with magnet files. But it causes major problems.

When I start up rTorrent (or even transmission), it CRIPPLES network connectivity. I makes ftp connection time out and ssh connections have like 5 second lag. I've run top and it's only using like 2% of the CPU and it's got plenty of RAM left. It's not even close to maxing out the wireless G 54Mb/s card downloading at like 100kB/s. What is wrong with this?? 




Also anyone want to tell me why the logins for FTP and SSH have a log lag during the login? Everything after the login is smooth but it's just odd that there's a long delay after username and after password inputs.

EDIT: I actually tried pinging a few other computer on the network and when this computer torrents, it slows everything. Some computer even become unreachable.

---

### Post by snowman4839 on 2012-12-15
Well since nobody answered me, I just installed Ubuntu Server 12.04 over Mint 14 and installed SSH and FTP servers and hooked it up directly with ethernet rather than using the wireless card. Now basic settings in rTorrent with DHT turned off and use UDP trackers get me 2MB/s (yes megaBYTE) downloads and everything is how it should be.

One problem I think I was having was the wireless card was slowing down everything because not only were the torrents limited to 100KB/s on the mint 14/wireless setup but so were the FTP transfers so it might have been an NIC problem.

Whatever, now the server is set up like a server.

---

### Post by chadk5utc on 2012-12-15
something to remember about wifi is that for all devices computers connected it shares that bandwidth. Theoretically 2 each would get half 3 each a third Etc etc if memory serves me right. Oh plus the overhead of any apps running through the same connection as well VNC

---

