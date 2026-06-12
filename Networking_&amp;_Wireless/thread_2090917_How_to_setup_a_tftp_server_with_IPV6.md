---
title: "How to setup a tftp server with IPV6"
date: 2012-12-03
forum: Networking &amp; Wireless
---

### Post by cxkipq on 2012-12-03
I want to setup a IPV6 PXE server, But I cannot set it successful with the tftp server.
who can tell me how to setup a IPV6 PXE server with under Ubuntu 12.04.

---

### Post by gnusci on 2012-12-03
Here a couple of nice tutorials

[http://www.howtoforge.com/ubuntu_pxe_install_server](http://www.howtoforge.com/ubuntu_pxe_install_server)
[https://linuxlink.timesys.com/docs/linux_tftp](https://linuxlink.timesys.com/docs/linux_tftp)

Let me know more details, I did that several years ago, maybe I can help you.

---

### Post by cxkipq on 2012-12-04
I want to test a server IPV6 net boot function, so I need setup an IPV6 PXE server. please see my configuration:

1. Install Xinetd and tftpd.
    [COLOR=Blue]apt-get install xinetd tftpd
[/COLOR]
2. config tftp server
   vim /etc/xinetd.d/tftp
[COLOR=Blue]service tftp
{
protocol    = udp
socket_type    = dgram
wait        = yes
flags        = IPV6 IPv4
user        = root
server        = /usr/sbin/in.tftpd
server_args    = -s /srv/tftp
disable        = no
}[/COLOR]

3. config DHCP6 server
[COLOR=Blue]option dhcp6.name-servers 2000::1;
option dhcp6.bootfile-url code 59 = string ;

subnet6 2000:0:0:0::/64 {
    option dhcp6.bootfile-url "tftp://[2000::1]/bootx64.efi";
    range6 2000:0:0:0::100 2000:0:0:0::2000;
    range6 2000:0:0:0:: temporary;
        prefix6 2000:0:0:0::   2000:0:0:0:: /64;[/COLOR]
}

4. copy bootx64.efi and to /srv/tftp and config elilo.conf

5. restart the xinetd and dhcpd6 server

[COLOR=Blue]service xinetd restart
server isc-dhcp-server6 restart[/COLOR]

6. clinet test result:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=228203&stc=1&d=1354601104[/IMG]

[COLOR=Red]PS: IPv4 PXE can boot successfully.[/COLOR]

---

