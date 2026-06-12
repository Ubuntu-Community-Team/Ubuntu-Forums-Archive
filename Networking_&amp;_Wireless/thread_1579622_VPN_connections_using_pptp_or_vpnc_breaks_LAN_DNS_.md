---
title: "VPN connections using pptp or vpnc breaks LAN DNS lookups"
date: 2010-09-22
forum: Networking &amp; Wireless
---

### Post by rod40cool on 2010-09-22
I use my laptop 10.04 LTS 64bit at my work to VPN to client networks and visa versa when at client sites I VPN back to the office. I use Network-Manager PPTP and VPNC type connections.

The problem I have is that whenever I'm VPN connected I lose the ability to connect to LAN devices by their DNS name so I have to connect to any local LAN device by it's IP address. What seems to be happening is the VPN connection DNS takes over any local LAN DNS lookup and I was wondering if there is any solution to this. 

For example, if am at customer A connected on their LAN I am able to ping and connect to any local server by name, eg ```
ping sfs01.othercompany.internal
``` and it is resolved ok. However, if I now want to VPN back to my office to access a server there the PPTP connection works fine and I can now ping server.mycompany.internal but now I can no longer ping sfs01.othercompany.internal.
```
rod@rods-t400:~$ ping sfs01.othercompany.internal
ping: unknown host sfs01.othercompany.internal
```

There is nothing wrong with routing as I can still ping the othercompany server by IP address and this works. 

I have tried searching for answers to this but I (a) don't know what exactly to call this problem and (b) therefore I am probably unable to accurately describe what's going on to see if a solution exists.

Given I've had this problem ever since I started using Ubuntu as my work laptop and I've just been living with the fact that with a VPN connection established I must use the IP address to connect to any LAN device, this must be a common problem with linux VPN connections. I know Windows PPTP connections still allow you to access LAN devices using the DNS name. (How and what do you call what Windows does - is it split VPN? or is it using a local cached DNS?)

My laptop is a Lenovo T400 with Ubuntu 10.04 LTS 64 bit, no firestarter or UFW is loaded or enabled.

Can anyone help me with this?

---

### Post by marcovanbeek on 2010-09-27
Hi,

I would say it is because when you connect via PPtP you get a new set of DNS servers added to resolv.conf, and the list is prioritized to use the remote DNS servers first, which answers (so your laptop does not roll over to the local DNS servers on the list). As the remote DNS server does not know who/ you are talking about, it forwards the request on to the next DNS server up the line (probably your ISP), which also does not understand what you are talking about.

There are a couple of possible solutions. The simplest would be to put an entry in your own office DNS server that points any requests to the client's internal domain back to their DNS server (called an NS record). Alternatively you could use the host file on your own laptop to resolve the most common entries, or you could even set up DNS on your own laptop and host NS entries yourself.

Marco

---

### Post by rod40cool on 2010-09-27
> **marcovanbeek said:**
> I would say it is because when you connect via PPtP you get a new set of DNS servers added to resolv.conf, and the list is prioritized to use the remote DNS servers first, which answers (so your laptop does not roll over to the local DNS servers on the list). Marco

Yes I've seen evidence of this. So what you're saying is that because the remote DNS on the VPN connection replies the 2nd or 3rd nameserver entries in resolv.conf are never used. For some reason I was thinking that if any DNS query fails on the 1st nameserver entry it would check the #2 nameserver entry. Am I confused at how nameserver and hence DNS queries get resolved?

I have been getting by by simply using IP addresses for accessing any local lan devices when I'm VPN connected or entries in the /etc/hosts file as you suggested.

Hmm... A DNS server on my laptop with NS records... I hadn't thought of that, but what about using the prepend option of dhclient.conf? I was looking also into this too. Would this accomplish a similar thing in forcing a particular DNS server to be used 1st?

How would you see having a DNS server with NS records helping? Is that so I can specify the order of DNS servers, and hence how DNS queries should proceed if a query fails on the first NS then move to the next?

---

### Post by SeijiSensei on 2010-09-27
> **rod40cool said:**
> Hmm... A DNS server on my laptop with NS records... I hadn't thought of that, but what about using the prepend option of dhclient.conf? I was looking also into this too. Would this accomplish a similar thing in forcing a particular DNS server to be used 1st?

Unfortunately having multiple "nameserver" lines in resolv.conf isn't going to help.  The resolver only uses the second entry if the first entry times out.  In your case, the server in your office is available, so it gets used for all requests, and returns an NXDOMAIN reply when it finds no entries for your client's internal hosts.

Running a DNS server on your laptop is a clever solution to this.  I'd use the "forward" directive in named.conf myself like this:

```
zone "mycompany.com" {
     forward-only;
     forwarders { 10.1.2.3; 10.1.2.4;};
};

zone "anothercompany.com" {
     forward-only;
     forwarders { 10.2.2.3; 10.2.2.4;};
};

```
where the 10.x IP addresses are replaced by the nameserver address(es) at the various locations.  Then you can make 127.0.0.1 be the nameserver in resolv.conf and have it handle all the queries.

As you mentioned you'll need to use a "prepend domain-name-servers 127.0.0.1" directive in dhclient.conf.

---

