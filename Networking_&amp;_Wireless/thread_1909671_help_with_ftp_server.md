---
title: "help with ftp server"
date: 2012-01-15
forum: Networking &amp; Wireless
---

### Post by zinzara on 2012-01-15
I have a server running ubuntu desktop 11.04 and I'm trying to set it up so I can acces files remotely. I can't get a static IP so I'm using an online service to do that part. Anyway, I set up the ftp by this guide: [https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html) and I can't get it to work. i've got the port set at 21 in the config file, I have port forwarding set for port 21. I am using WS_FTP to connect through the DDNS on port 21. I can successfully telnet to the server and access my files but every time I try to connect through FTP, it won't connect. If anyone can offer some assistance, it would be great.

Also, I've tried connecting through ftp while on another computer on the server's network and it still won't work so it's not something wrong with the DDNS connection. I can successfully open the server and view files through Windows Networking.

---

### Post by Dangertux on 2012-01-15
> **zinzara said:**
> I have a server running ubuntu desktop 11.04 and I'm trying to set it up so I can acces files remotely. I can't get a static IP so I'm using an online service to do that part. Anyway, I set up the ftp by this guide: [https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/10.04/serverguide/C/ftp-server.html) and I can't get it to work. i've got the port set at 21 in the config file, I have port forwarding set for port 21. I am using WS_FTP to connect through the DDNS on port 21. I can successfully telnet to the server and access my files but every time I try to connect through FTP, it won't connect. If anyone can offer some assistance, it would be great.

Also, I've tried connecting through ftp while on another computer on the server's network and it still won't work so it's not something wrong with the DDNS connection. I can successfully open the server and view files through Windows Networking.

You may also need to open port 20 TCP as FTP requires both a control and a data port.

Hope this helps.

---

### Post by zinzara on 2012-01-15
thanks for the input, I added port 20 to the port forwarding also. It still won't work. I rechecked everything in the config. here is what i have:

listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
rsa_cert_file=/etc/ssl/private/vsftpd.pem
ssl_enable=YES

---

### Post by zinzara on 2012-01-15
Ok, I figured out what was wrong I think. I don't really understand how it works or anything but I commented out the rsa key thing and the ssl_enable. It works now. I would like to use SSL but for now until I understand it more, I'll just not use it. Sorry for troubling you. Maybe someone will get something out of this though.

---

### Post by Dangertux on 2012-01-15
There is no reason to apologize, you were trying to get support, and this is a support forum.

As far as what I think happened and why it happened that way, is whatever client you were using probably wouldn't accept a self-signed SSL cert (security feature) so denied the connection.

Hope that helps some.

---

