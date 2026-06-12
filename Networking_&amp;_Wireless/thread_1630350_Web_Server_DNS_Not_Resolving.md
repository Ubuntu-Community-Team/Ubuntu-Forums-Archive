---
title: "Web Server DNS Not Resolving"
date: 2010-11-25
forum: Networking &amp; Wireless
---

### Post by own3mall on 2010-11-25
I've installed a web server on my server, and it works great; however, DNS will not resolve for any domains I add to the web server.

For example, I've created custom ns records at GoDaddy.com to point

ns1.mydomain.com to 24.8.45.105
ns2.mydomain.com to 24.8.45.105

Thus, my clients should set their name servers to ns1.mydomain.com and ns2.mydomain.com and have them be routed to 24.8.45.105

24.8.45.105 is my server's external IP
192.168.x.119 is my server's local IP address

These entries are not resolving even though they have been setup properly in the GoDaddy control panel.

Connecting via direct IP does resolve however:

[http://24.8.45.105/](http://24.8.45.105/)

Ports are all unblocked including 53.

Here's how my network is setup:
[B]
Internet Settings[/B]
```


Gateway MAC Address     00:22:2D:96:68:FE
WAN MAC Address     00:22:2D:96:69:02
WAN DHCP IP Address     24.8.45.105
WAN DHCP Subnet Mask     0.0.0.0
WAN DHCP Default Gateway     0.0.0.0
WAN Internet IP Address     24.8.45.105
DNS (primary)     68.87.85.102
DNS (secondary)     68.87.69.150
DHCP Time Remaining     68h:02m:55s
Date     NOV-25-2010
Static IP Block     [20.20.20.1/24]("http://20.20.20.1/24")
Local Settings
Gateway IP Address     10.1.10.1
Subnet Mask     255.255.255.0
DHCP Server     Enabled
IP Range (start)     10.1.10.10
IP Range (end)     10.1.10.15

```**Router 1 Settings:**
```

Local Settings
Gateway IP Address     10.1.10.1
Subnet Mask     255.255.255.0
DHCP Server     Enabled
IP Range (start)     10.1.10.10
IP Range (end)     10.1.10.15


```
**Router 2 Settings:**
```

IP Address :     192.168.x.43
Subnet Mask :     255.255.255.0
Default Gateway :     10.1.10.1
Primary DNS Server :     10.1.10.1
Secondary DNS Server :     0.0.0.0


```Ports are forwarded for 10.1.10.13 (Router 2) and then ports are forwarded on (Router 2) to the server's IP address of 192.168.x.119

**The following files contain the below entries:**

resolv.conf:

192.168.x.43

dhclient.conf under dhcp3:

#prepend domain-name-servers 127.0.0.1
prepend domain-name-servers 10.1.10.1
prepend domain-name-servers 68.87.85.102
prepend domain-name-servers 68.87.69.150

The DNS Template on the server is:

```

 $TTL    86400
@       IN      SOA     ns1.{domainname}. {dnsemail} (
                        {serial}     ; Serial
                        10800   ; Refresh
                        1200     ; Retry
                        86400  ; Expire
                        86400 ) ; Minimum
 ns1.{domainname}.           IN NS   ns1.{domainname}.
ns2.{domainname}.           IN NS   ns2.{domainname}.
ns.{domainname}.        IN A    {dnsip}
ns1.{domainname}.       IN A    {dnsip}
ns2.{domainname}.       IN A    {dnsip}
dns.{domainname}.       IN A    {dnsip}
dns1.{domainname}.       IN A    {dnsip}
dns2.{domainname}.       IN A    {dnsip}
{domainname}.           IN A    {webip}
mail.{domainname}.      IN A    {mailip}
smtp.{domainname}.   IN A    {webip}
webmail.{domainname}.   IN A    {webip}
ftp.{domainname}.       IN CNAME        {domainname}.
www.{domainname}.       IN CNAME        {domainname}.
{domainname}.           IN MX  10 mail.{domainname}.
{domainname}.           IN TXT "v=spf1 a mx"
 {customdns}
 *                       IN A    {webip}
 
``` My IP address is:  24.8.45.105
 I set NS1.mydomain.com to resolve to 24.8.45.105
I set NS2.mydomain.com to resolve to 24.8.45.105


Any ideas what's wrong?  Why won't ns1.mydomain.com resolve for clients or myself?

---

### Post by surfer on 2010-11-25
what does
```
$ ping ns1.mydomain.com
```
say?

---

### Post by SeijiSensei on 2010-11-25
You have to be running a nameserver if you point the NS records to that address.  Are you running BIND? 

There really isn't a good reason to run a nameserver yourself if you're just trying to provide external DNS services.  Just point the NS records to the GoDaddy servers and set up the records there.

---

### Post by own3mall on 2010-11-25
I'm currently at a Windows machine, and here's what it says when I ping:

ping ns1.webehostin.com
Ping request could not find host ns1.webehostin.com. Please check the name and t
ry again.

I have setup the entries at GoDaddy correctly.

[B]Host Summary Entries

[/B]ns1.mydomain.com** --- **24.8.45.105
ns2.mydomain.com     --- 24.8.45.105

Adding the entries used to work fine standalone until ICANN changed the rules.  Now, the server at 24.8.45.105 must also have the correct DNS entries and be setup for use with that host summary.

Is there anything else network side that I need to setup for DNS?  What am I missing?

---

### Post by own3mall on 2010-11-27
Anyone?

---

### Post by SeijiSensei on 2010-11-27
You need an A record at GoDaddy that points [www.yourdomain.com](www.yourdomain.com) to your server's IP address.

---

