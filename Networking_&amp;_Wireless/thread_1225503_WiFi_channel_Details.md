---
title: "WiFi channel Details"
date: 2009-07-28
forum: Networking &amp; Wireless
---

### Post by Geffers on 2009-07-28
I know Linux historically can supply plenty of network details but I have tried to search for Linux programs similar to netstumbler and airsnare.

The former gives details of surrounding access points and the latter warns of any attempts to join your network.

Any suggestions appreciated.

Geffers

---

### Post by rocksockdoc on 2011-07-19
> **Geffers said:**
> I have tried to search for Linux programs similar to netstumbler and airsnare

How do we install airsnare on Ubuntu?

It's not in the "Ubuntu Software Center".

The home page appears to be: [http://home.comcast.net/~jay.deboer/airsnare/](http://home.comcast.net/~jay.deboer/airsnare/)

Is that web site the right way to install airsnare?

What I'm worried about is this:
[http://www.wired.com/images_blogs/threatlevel/2011/07/ardolffedssentencingmemo.pdf](http://www.wired.com/images_blogs/threatlevel/2011/07/ardolffedssentencingmemo.pdf)

---

### Post by rocksockdoc on 2011-07-20
Googling more, I realize now that airsnare is NOT an Ubuntu program.

So, I [enabled arpwatch]("http://aimlinux.com/blog/?p=56") instead:

> **Arpwatch  keeps  track  for  ethernet/ip  address  pairings.  It syslogs activity and reports certain changes via email.  Arpwatch  uses  pcap(3) to listen for arp packets on a local ethernet interface.** *Note: you must have exim4 or postfix setup with SMTP, be it local  or external if you wish to send out &#8220;alerts&#8221; to external email address.*
 [Click Here ]("http://techgurulive.com/2009/01/09/how-to-install-and-configure-exim4-in-ubuntu/")to find out how to setup exim4 on Debian based systems.
 Run the following commands from terminal.
```
sudo apt-get install arpwatch
Create empty file for storing host information:
sudo touch /var/lib/arpwatch/arp.dat
Edit the config file:
sudo nano /etc/arpwatch.conf
insert line like this:
eth0 -a -n 192.168.1.0/24 -m [EMAIL="youremail@mydomain.com"]youremail@mydomain.com[/EMAIL]
Restart arpwatch:
sudo /etc/init.d/arpwatch restart
Check if the process is running:
ps &#8211;ef | grep arpwatch
root 218 1 0 11:38 ? 00:00:00 /usr/sbin/arpwatch ...
```


---

### Post by Geffers on 2011-07-20
> **rocksockdoc said:**
> Googling more, I realize now that airsnare is NOT an Ubuntu program.

So, I [enabled arpwatch]("http://aimlinux.com/blog/?p=56") instead:

Wow, I had forgotten about that post, the Ubuntu forum shows I posted it on July 28th, 2009 - nearly two years ago :razz:

Thanks for taking the time to reply, I know Linux has numerous command line network tools but the two windows programs I mentioned both have sound alerts so you don't have to keep monitoring to check.

Geffers

---

