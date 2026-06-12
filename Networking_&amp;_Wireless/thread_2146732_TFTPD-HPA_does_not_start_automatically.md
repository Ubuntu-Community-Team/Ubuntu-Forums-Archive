---
title: "TFTPD-HPA does not start automatically?"
date: 2013-05-19
forum: Networking &amp; Wireless
---

### Post by jamesaepp on 2013-05-19
I installed server 12.04 amd64

After doing apt-get update && apt-get -y upgrade && reboot as root, I then did this:

(as root) apt-get -y install tftpd-hpa


During installation, the following files were created:

/etc/init/tftpd-hpa.conf
/etc/init.d/tftpd-hpa
/etc/default/tftpd-hpa

However, if I reboot the machine and perform "service --status-all" it shows this:

 [ ? ]  tftpd-hpa

I can only assume it is not meant to run automatically by default, but could someone teach me how to configure this service to run automatically?

Thanks in advance!

(Yeah, I probably made the question more complicated than it needs to be....)

---

