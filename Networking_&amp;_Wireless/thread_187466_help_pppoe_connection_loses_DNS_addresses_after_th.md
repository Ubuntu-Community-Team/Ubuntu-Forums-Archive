---
title: "help: pppoe connection loses DNS addresses after the first DHCP lease renewal"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by Quark Green on 2006-06-03
How can I configure the system so that the DNS addresses remain in /etc/resolv.conf and don't get removed at the first dhcp lease renewal?
I have this problem in dapper RC. My connection is PPPOE and my ADSL router/gateway/modem is running in bridge mode with NAT.
After setting up "sudo pppoeconf" successfully or running "sudo pon dsl-provider" subsequently, the internet address and DNS server addresses (DNS1 and DNS2) are correctly obtained from my ADSL router/gateway/modem. This is confimed from /var/log/syslog. Then /etc/resolve.conf is updated with the internet address and DNS servers and all is well.
The problem starts when the dhclient first initiates a renewal of the dhcp internet address. In reply to this renewal request, the router/gateway/modem replies with only the internet address. So then when /etc/resolve.conf is updated, the DNS entries disappear. After that I am no longer able to connect to internet sites by name, only by number. How can I fix this so that the DNS addresses remain in /etc/resolv.conf and don't get removed at the first dhcp lease renewal?

---

### Post by Quark Green on 2006-06-04
I have solved the problem in one way which was to increase the dhcp lease time to maximum by changing it on my adsl router/gateway/modem. The max. I could make it was 999999 seconds which is about 11-12 days. This is fine for now since I never keep my connection on that long. So after establising the pppoe connection, the client doesn't ask for a renewal during the time my computer is connected and the DNS addresses remain in the /etc/resolv.conf file.
But I don't think this is an elegant solution because it depends on me having access to change the router configuration. I will continue to look for another way. I have a lead that some settings can be changed in /etc/dhcp3/dhclient.conf that might offer a better solution.

---

### Post by chiok on 2006-06-05
I comment out make_resolv_conf() in /etc/dhcp3/dhclient-script

[http://ubuntuforums.org/showthread.php?t=24093](http://ubuntuforums.org/showthread.php?t=24093)

---

### Post by Quark Green on 2006-06-06
chiok, Thank you for that. I will investigate it. Quark.

---

### Post by eboo on 2006-06-06
Instead of commenting out the make_resolv_conf() in /etc/dhcp3/dhclient-script,

I would recommend editing the following file /etc/dhcp3/ dhclient.conf
find the following line:
#prepend domain-name-servers 127.0.0.1;

as you can see it is usually commented out, uncomment it and replace 127.0.0.1 with your DNS ddressses (commma separated).

It should look something like this
prepend domain-name-servers 195.55.22.33,195.55.22.3;

This works much better I think , your resolv.conf will always be regenerated and it will always place the addresses you specify in the dhclient.conf first.

hopefully this is a more elegant solution

---

### Post by Quark Green on 2006-06-10
eboo, Thank you too for your contribution. I think it is more elegant. The problem that still remains that if you change to another ISP, then you have to find out the DNS and re-hard-code them into dhclient.conf. The ultimate solution would be for dhclient to get the DNS along with the lease renewal everytime. I would like to find out the following: if pppd can get the DNS from the router/gateway/modem when it first sets up the connection after "pon dsl-provider", then why can't dhclient get DNS subsequently?

---

### Post by edwardwang on 2006-06-23
[QUOTE=eboo]Instead of commenting out the make_resolv_conf() in /etc/dhcp3/dhclient-script,

I would recommend editing the following file /etc/dhcp3/ dhclient.conf
find the following line:
#prepend domain-name-servers 127.0.0.1;

as you can see it is usually commented out, uncomment it and replace 127.0.0.1 with your DNS ddressses (commma separated).

It should look something like this
prepend domain-name-servers 195.55.22.33,195.55.22.3;
[/QUOTE]

Two problems here
[LIST]
[*]Activating pppoe when boot doesn't work. I must 'pon dsl-provider' manually.
[*]Losing DNS address. Seems dhclient picks up my ADSL modem's IP address when renewing lease.
[/LIST]

But unfortunately, neither solution above works for me. I end up with:
```

pon dsl-provider
sudo pkill -9 dhclient

```
It is brutal, :p  but at least it works for me.

---

### Post by manusia_aneh on 2007-05-12
Very BIG thank you to edwardwang for the great solutions...!!! I`ve search the entire web only to find the real solution of PPPoE bugs in Ubuntu (even the Ubuntu developer can`t find the solution for this problem, read the Launchpad Bugs section), and I found it`s the REAL answer...!!! :D

The method "sudo pkill -9 dhclient" is really work for me, now I don`t have any problem to connect to internet, and I started to enjoy Ubuntu. Many Thx for you, edwardwang!!!

---

### Post by Adam590 on 2007-05-29
I'd like to echo the thanks to edwardwang - this is also the ONLY thing I have found to resolve my PPPoE problems.

Would I be able to add this pkill line somewhere and have it run at startup automatically?

---

### Post by cnbiz850 on 2008-04-05
> **manusia_aneh said:**
> 
The method "sudo pkill -9 dhclient" is really work for me, now I don`t have any problem to connect to internet, and I started to enjoy Ubuntu. Many Thx for you, edwardwang!!!

I am running Hardy and have this same problem.  Is "sudo pkill -9 dhclient" still the best solution so far?  It seems to work though.

---

### Post by cnbiz850 on 2008-04-08
help please.

---

