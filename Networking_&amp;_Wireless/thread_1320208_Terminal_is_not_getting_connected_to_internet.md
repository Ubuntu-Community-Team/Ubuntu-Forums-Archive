---
title: "Terminal is not getting connected to internet"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by harish4linux on 2009-11-09
Hi every one

I have configured my network connections of eth0 and enabled the connection

i am able to access the internet in mozilla firefox, but when i am trying to run commands in terminal such as

sudo apt-get update

it is generating a error

root@Vasireddy:/usr/src/linux-2.6.31.5# apt-get update
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty Release.gpg
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main Translation-en_IN
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/restricted Translation-en_IN
  Could not resolve 'in.archive.ubuntu.com'

please help me regarding the issue

---

### Post by darshana on 2009-11-09
Are u using a proxy?

---

### Post by dungun on 2009-11-09
[http://ubuntuforums.org/showpost.php?p=3996845&postcount=5](http://ubuntuforums.org/showpost.php?p=3996845&postcount=5)

Your Problem:
DNS resolution via local router DNS relay has proven to be a common failure point in my experience.

Try this...
open a terminal.
run this command 
 	Code:
 	sudo gedit /etc/dhcp3/dhclient.conf 
search for this line... #prepend domain-name-servers 127.0.0.1; insert the following line
after that line. 
 	Code:
 	 prepend domain-name-servers 208.67.222.222,208.67.220.220; 
Save the file, disconnect and reconnect, then retest.

What this does...
It hardsets your machine to use OpenDNS nameservers.. you may swap 208.67.xxx.xxx with the IP's of your chosen nameservers, although I think you'll find the OpenDNS servers to be much more efficient.

So, no matter what DNS is handed to you by DHCP, your machine will always behave and use just the DNS servers you tell it to.


-Mark Williams

---

