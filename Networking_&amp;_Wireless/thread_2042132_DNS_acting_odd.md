---
title: "DNS acting odd"
date: 2012-08-14
forum: Networking &amp; Wireless
---

### Post by chuuk on 2012-08-14
Hi,

I've been having some fairly major problems with my DNS for the last two years or so. I previously solved them by simply connecting my Ubuntu machine to an ethernet port, which worked fine, but I have moved house and can't do this at my new address.

For those who live in the UK, by internet is provided by BT. A few years ago, Ubuntu would connect to the BT Home Hub (then v2, now v3) but when I tried to load any pages in Chrome, I would be met by: 'The server at [www.example.co.uk](www.example.co.uk) can't be found because the DNS look-up failed'. 

I looked around for a solution to this error, and simply switched my DNS to Google's ( 8.8.8.8 ) in /etc/resolv.conf. This worked fine on wired ethernet.

Since I moved house, my laptop connects to the wireless and displays the same DNS message. I changed the DNS settings to point to Google, which works fine for a few minutes and then fails. 

I thought that /etc/resolv.conf might be getting overwritten, but this is not the case.

The problem was then (and still can be) fixed (for five more minutes) by simply restarting the network again:
sudo /etc/init.d/networking restart

I have toyed with the idea of writing a cron job to simply restart my network interfaces every few minutes, but this is messy and inefficient and I would rather have a proper solution.

Does anyone have any ideas about the situation?

---

### Post by hawkmage on 2012-08-14
There are a couple ways of fixing this depending on what version of Ubuntu you are using and what services are runing.  

Are you using Ubuntu Desktop 12.04?  If you run the nslookup to look up a name is the server localhost or 172.0.0.1?  If so Network Manger is running an instance of DNSMasq that is getting in the way of switching to the DNS servers other than what you get via DHCP.  TO fix this you will need to edit the /etc/NetworkManager/NetworkManager.conf file and comment/remove the line "dns=dnsmasq".   From here you can either install the full dnsmasq and add lines to the /etc/dnsmasq.d/dnsmasq.conf like "server=8.8.8.8" to make it use Google's DNS.  Or don't install dnsmasq and configure the resovconf service template files to include the DNS servers you want.  You would edit the /etc/resolvconf/resolv.conf.d/base file and add the lines like you would in the /etc/resolv.conf.  

Prior to Ubuntu 12.04 you would likely have had issues with your resolv.conf being overwritten and you would have had to edit your /etc/dhcp/dhclient.conf file to add something like "supersede domain-name-servers 8.8.8.8;"

---

### Post by chuuk on 2012-08-14
I am currently on 11.10 (this issue has been with me since 10.04).

I have been checking, and as far as I can see /etc/resolv.conf does not get overwritten. Just in case, I added "supersede domain-name-servers 8.8.8.8;" to /etc/dhcp/dhclient.conf, but this did not help in any way.

Could there be any other approach?

---

### Post by papibe on 2012-08-14
Hi chuuk.

The 'supersede' method works pretty good for servers (no GUI). It is much easier to setup your machine with a static DNS using [this]("http://ubuntuguide.net/google-public-dns-setting-up-an-alternative-to-current-dns-provider-in-ubuntu") method (using network connections).

Let us know how it goes.
Regards.

---

### Post by chuuk on 2012-08-15
Unfortunately, no dice. I suspect there *may* be something in my router's software preventing me from using Google's DNS. 

Could this be done? How would I check if this was happening if I did want to know?

Or does anyone have any other possible solutions?

---

### Post by SeijiSensei on 2012-08-15
Some providers "hijack" DNS requests and force them through their own servers.  I don't know if BT is one of them, though in the past they've been known for some other [dicey activities]("http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-DNS-hijack-for-mistyped-or-invalid-URLs/td-p/45082").  In order for them to implement this "service" they need to see every DNS query.  Did you opt-out of this service after you moved?

---

### Post by joober on 2012-08-15
Just chiming in here, but what is the output of the nslookup command when you query google.com, for instance? I am curious which DNS server (if any) is doing the resolving.

```
# nslookup www.google.com
```

---

### Post by chuuk on 2012-08-15
When /etc/resolv.conf is set and /etc/init.d/networking restart is run, the result of nslookup is (as expected):

Server:		8.8.8.8
Address:	8.8.8.8#53

A few minutes later (not having touched anything and with /etc/resolv.conf as before):

timed out; no servers could be reached

Something appears to be blocking that traffic at a very basic level.

---

### Post by papibe on 2012-08-15
If you follow the instructions on post #4, it may actually be working, but you are seeing the effects of the dnsmasq plugin.

If when it changes, it goes to 127.0.0.1, it could be OK.

Please post the results of these commands, after you experience a change:
```
grep dnsmasq /etc/NetworkManager/NetworkManager.conf

cat /var/run/nm-dns-dnsmasq.conf
```
Regards/

---

### Post by chuuk on 2012-08-15
grep dnsmasq /etc/NetworkManager/NetworkManager.conf

returns nothing

cat /var/run/nm-dns-dnsmasq.conf

returns 'No such file or directory'

As I mentioned earlier, I am on 11.10 and I think someone mentioned that dnsmasq was only deployed in 12.04, so this is not too surprising.

---

### Post by abhopkins on 2012-10-10
Thank you for your help. I am using Ubuntu 12.04 and had similar problems (I could load one webpage, one time, and then the DNS server look-up failed error would appear). Installing dnsmasq, creating the config file /etc/dnsmasq.d/dnsmasq.conf and putting "server=8.8.8.8" in there, then rebooting, appears to have completely solved my problem.
 
> **hawkmage said:**
> There are a couple ways of fixing this depending on what version of Ubuntu you are using and what services are runing. 
 
Are you using Ubuntu Desktop 12.04? If you run the nslookup to look up a name is the server localhost or 172.0.0.1? If so Network Manger is running an instance of DNSMasq that is getting in the way of switching to the DNS servers other than what you get via DHCP. TO fix this you will need to edit the /etc/NetworkManager/NetworkManager.conf file and comment/remove the line "dns=dnsmasq". From here you can either install the full dnsmasq and add lines to the /etc/dnsmasq.d/dnsmasq.conf like "server=8.8.8.8" to make it use Google's DNS. Or don't install dnsmasq and configure the resovconf service template files to include the DNS servers you want. You would edit the /etc/resolvconf/resolv.conf.d/base file and add the lines like you would in the /etc/resolv.conf. 
 
Prior to Ubuntu 12.04 you would likely have had issues with your resolv.conf being overwritten and you would have had to edit your /etc/dhcp/dhclient.conf file to add something like "supersede domain-name-servers 8.8.8.8;"

---

