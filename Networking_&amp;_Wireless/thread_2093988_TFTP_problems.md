---
title: "TFTP problems"
date: 2012-12-12
forum: Networking &amp; Wireless
---

### Post by Breixo L Garcia on 2012-12-12
Hi,
 
I am beginner with TFTP protocol in Linux. I have been trying to connect a AM335x EVM Board with my Host to make boot. but first I will like to test my TFTP server.
 
The configuration is the next:
# cat /etc/xinetd.d/tftp
 
service tftp
{
protocol = udp
port = 69
socket_type = dgram
wait = yes
user = nobody
server = /usr/sbin/in.tftpd
server_args = /tftpboot
disable = no
}
 
# cat /etc/default/tftpd-hpa
 
# /etc/default/tftpd-hpa
TFTP_USERNAME="tftp"
TFTP_DIRECTORY="/tftpboot"
TFTP_ADDRESS="0.0.0.0:69"
TFTP_OPTIONS="--secure"
RUN_DAEMON="yes"
 
the /tftboot has this files:
 
# ls -l /tftpboot/
insgesamt 3096
-rwxrwxrwx 1 nobody root 174 Dez 4 14:50 test
-rwxrwxrwx 1 nobody root 3163680 Dez 7 08:59 uImage-am335x-evm.bin
 
However when I like getting locally some file in /tftpboot over TFTP protocol, I obtain that:
 
# tftp localhost
tftp> get uImage-am335x-evm.bin
Error code 1: File not found
tftp> quit
 
Then I make that I see the /var/log/syslog and it shows:
 
Dec 12 15:29:46 sst-virtual-machine tftpd[6987]: tftpd: trying to get file: uImage-am335x-evm.bin
Dec 12 15:29:46 sst-virtual-machine tftpd[6987]: tftpd: serving file from **[SIZE=4][COLOR=black]/srv/tftp[/COLOR][/SIZE]**
 
I am sure that I miss something out, because my configuration I thing that is good. But the files in TFTP protocol is looked in the /svr/tftp. Why can it be happening that? 
Because tftp configuration shows [SIZE=4][COLOR=black]server_args = /tftpboot. [SIZE=2]I think that the TFTP protocol should search the files in that directory /tftpboot, doesn't it? [/SIZE][/COLOR][/SIZE]

[SIZE=2]I have not more idea what  wrong is, any help would be greatly appreciated.[/SIZE]

[SIZE=2]-Regards[/SIZE]

---

### Post by Breixo L Garcia on 2012-12-12
Hi,
 
I think that I have found the mistake. There is a file /etc/xinetd.d/tftpd with this configuration that overread the tftp configuration I suppose, but I am not sure. 
 
# cat /etc/xinetd.d/tftpd
service tftp
{
    socket_type = dgram
    wait = yes
    user = root
    server = /usr/sbin/in.tftpd
    server_args = -s /srv/tftp
}
 
Why can I do to solve this? Can I erase this file without problems or it is better to reconfigurated that like /etc/xinetd.d/tftp
 
 
service tftp
{
protocol = udp
port = 69
socket_type = dgram
wait = yes
user = nobody
server = /usr/sbin/in.tftpd
server_args = /tftpboot
disable = no
}

sorry for this question and the time that We lost in there.
 
-Regards

---

