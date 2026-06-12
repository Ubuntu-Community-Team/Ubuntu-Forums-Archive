---
title: "JFFNMS tftp"
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by ipguru99 on 2010-02-23
This always kills me.. and I never remember how to do it.

JFFNMS--getting cisco configs from host

--Ubuntu 8.04 specific (apt-get install jffnms atftpd)--

1. After installing atftpd, it is started, by default, from the openbsd-inet package.  Edit the /etc/inetd.conf file from this:
> tftp		dgram	udp	wait 	nobody /usr/sbin/tcpd /usr/sbin/in.tftpd --tftpd-timeout 300 --retry-timeout 5     --mcast-port 1758 --mcast-addr 239.239.239.0-255 --mcast-ttl 1 --maxthread 100 --verbose=5  [COLOR="Red"]/tftpboot[/COLOR]
to this:
> tftp		dgram	udp	wait 	nobody /usr/sbin/tcpd /usr/sbin/in.tftpd --tftpd-timeout 300 --retry-timeout 5     --mcast-port 1758 --mcast-addr 239.239.239.0-255 --mcast-ttl 1 --maxthread 100 --verbose=5  [COLOR="Red"]/var/lib/jffnms/tftp[/COLOR]
...basically just changing the path where the tftp server works

2. When adding a host to JFFNMS, specify the RW string you put into the device.. specify the tftp server ip (should be JFFNMS IP). 

3. Notice I didn't change the user, I didn't manually create files ahead of time.  I tested this with a command that Craig Small and another gentlemen where mentioning in the forum.  The following command duplicates what will happen when the JFFNMS Cron job runs at night.  You are switching to the directory, then running the command as the JFFNMS user:
```
cd /usr/share/jffnms/engine; su -s /bin/sh -c 'php tftp_get_host_config.php' jffnms
```

If you have one host, it should look like this:
```
root@jffnms:/usr/share/jffnms/engine# php tftp_get_host_config.php 
11:41:08  :  H   4 : 192.168.0.214 : cisco_cc : OK new config id 2 (4257.98 msec)
11:41:08 TIMES 	: Total Time 4269.46 msec.
```

I can't find this anywhere, so I am assuming it gets pushed into mysql

4. Go back into JFFNMS, click on the yellow Administration lock (top), then click on Hosts.  The drop down in front of each host (on the left) name will have an option to View Stored Configurations.

I have done this a dozen times now and I can never remember where this is.

Many, many thanks to Craig Small and others for not letting this die!  I have tried them all and keep coming back to JFFNMS!

---

