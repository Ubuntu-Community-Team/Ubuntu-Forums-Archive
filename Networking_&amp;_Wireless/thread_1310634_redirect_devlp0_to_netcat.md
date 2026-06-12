---
title: "redirect /dev/lp0 to netcat"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by shameerck on 2009-11-02
Hi,

I have connected my printer to a linksys wps54g print server. The print server ip is 192.168.1.22.
When I try the following command, it works fine.
> cat test.txt | nc 192.168.1.22 9100

I have an application which directly pumps print data to /dev/lp0. Now I want to redirect the data from /dev/lp0 to the print server.
Please help me to do this, or make your suggestions to achieve this.

Thanks,
Shameer.

---

### Post by shameerck on 2009-11-02
Issue Solved using the following method.

- Create a device
$ mknod /dev/netcatprint p

- Give access to everyone
$ chmod 666 /dev/netcatprint

- Create a script for redirection
$ nano test.sh

while true
do
cat /dev/netcatprint | /bin/nc.openbsd 192.168.1.22 9100
done

- Run this script in background
$ sh ./test.sh &

Now print anything to /dev/netcatprint. That will get printed on the network printer.

---

