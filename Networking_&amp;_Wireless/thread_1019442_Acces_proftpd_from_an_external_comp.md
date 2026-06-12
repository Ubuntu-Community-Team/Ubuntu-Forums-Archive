---
title: "Acces proftpd from an external comp"
date: 2008-12-23
forum: Networking &amp; Wireless
---

### Post by teodormircea on 2008-12-23
Hello 

I'm not quite an expert on Linux, but I'm persistent.
OK, i installed proftpd, i have everything OK, is working in my LAN , but i would like to access it my ftp server from an other computer from exterior.
I mention that i can access my computer remotely via ssh and vnc so my router it's configured for my ip.

Thanks:lolflag:

---

### Post by albinootje on 2008-12-23
> **teodormircea said:**
> 
I'm not quite an expert on Linux, but I'm persistent.
OK, i installed proftpd, i have everything OK, is working in my LAN , but i would like to access it my ftp server from an other computer from exterior.
I mention that i can access my computer remotely via ssh and vnc so my router it's configured for my ip.

FTP is an ancient (fast but by default unencrypted) protocol, which can cause headaches when trying to make it available through certain firewall-setups.

You have ssh enabled, so you also have sftp and scp ready to use, which is encrypted, and has nice GUI apps like cyberduck for MacOSX, and winscp for Windows.

[http://cyberduck.ch/](http://cyberduck.ch/)
[http://winscp.net/eng/index.php](http://winscp.net/eng/index.php)

If you really want to have ftp publically accessible (which can also cause a major security headache, be careful with public uploads and permissions!), you should tell some more about your firewall setup.
Are you using a DSL-router, or are you using iptables on a Linux-box ?

And if you decide to use ssh/scp/sftp for other users, you can look at scponly (available in the Ubuntu repositories) to restrict access :
[http://sublimation.org/scponly/wiki/index.php/Main_Page](http://sublimation.org/scponly/wiki/index.php/Main_Page)

And if you're feeling bored, try this :
[http://www.howtoforge.com/chroot_ssh_sftp_debian_etch](http://www.howtoforge.com/chroot_ssh_sftp_debian_etch)
:-)

---

### Post by teodormircea on 2008-12-23
For the admin part of proftpd i use gproftpd, is quite easy to use , i have quite a lot of settings on this gui.I can even see the config file of my server.
So for the user rights i can make it from this gui.
For my open ports after an nmap
 PORT     STATE SERVICE
21/tcp   open  ftp
22/tcp   open  ssh
5900/tcp open  vnc
I can access my from exterior  i use ssh and vnc , but when i use my ip adress (not my LAN ip)to connect to my ftp server is not working.

---

### Post by albinootje on 2008-12-23
> **teodormircea said:**
> For the admin part of proftpd i use gproftpd, is quite easy to use , i have quite a lot of settings on this gui.I can even see the config file of my server.
So for the user rights i can make it from this gui.

Cool. 
> 
For my open ports after an nmap
 PORT     STATE SERVICE
21/tcp   open  ftp
22/tcp   open  ssh
5900/tcp open  vnc
I can access my from exterior  i use ssh and vnc , but when i use my ip adress (not my LAN ip)to connect to my ftp server is not working.

If you really want to test ftp through a firewall, I recommend testing with a range of different ftp-clients (gftp,filezilla,ncftp,lftp,aftp,cftp for example), and test both active and passive ftp in those clients.
And, as I wrote before, prepare for headaches or long hours of struggling with ftp + firewall.

---

### Post by teodormircea on 2008-12-23
I found some documentation on proftpd site to setup the NAT, but is using ipchains
[HTML]irst we need to enable NAT for our FTP server. As root user:

  echo "1">/proc/sys/net/ipv4/ip_forward
  ipchains -P forward DENY
  ipchains -I forward -s 192.168.1.2 -j MASQ

Now we load the autofw kernel module and forward ports 20 and 21 to the FTP server:

  insmod ip_masq_autofw
  ipmasqadm autofw -A -r tcp 20 21 -h 192.168.1.2

Then we forward ports for Passive FTP. In our etc/proftpd.conf file we restriced passive ports to 60000-65535, so that's what we'll use here:

  ipmasqadm autofw -A -r tcp 60000 65535 -h 192.168.1.2

Now you can try to login to your FTP server from a computer on the Internet![/HTML]
well now is iptables

---

### Post by albinootje on 2008-12-23
> **teodormircea said:**
> I found some documentation on proftpd site to setup the NAT, but is using ipchains
-- cut --
well now is iptables

This might be useful :
[http://www.cyberciti.biz/faq/iptables-open-ftp-port-21/](http://www.cyberciti.biz/faq/iptables-open-ftp-port-21/)
[http://www.linuxquestions.org/questions/linux-security-4/iptables-rules-for-active-ftp-22127/](http://www.linuxquestions.org/questions/linux-security-4/iptables-rules-for-active-ftp-22127/)

---

