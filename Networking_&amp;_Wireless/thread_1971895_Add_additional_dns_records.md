---
title: "Add additional dns records"
date: 2012-05-03
forum: Networking &amp; Wireless
---

### Post by sonicb00m on 2012-05-03
I am using a company network which uses an internal DNS server to provide subdomain records. My resolv.conf points to 127.0.0.1.

I would like to use google DNS [noparse](8.8.8.8)[/noparse] but adding this to resolv.conf results in the internal subdomains not working.

Is it possible to run them concurrently? It also means I cannot use my VPN since the internal subdomains won't work.

---

### Post by newbie-user on 2012-05-03
127.0.0.1 is your loopback address. Unless you're actually working from the DNS server itself, you are not actually doing DNS resolution. So when you add Google's DNS to resolv.conf, Google's DNS starts serving DNS requests, and Google doesn't know of your internal network.

So you should add your company's DNS server to your resolv.conf before Google's server, that way your DNS request goes to the local DNS first before going out to Google's DNS.

---

### Post by Sergius14 on 2012-05-03
You can't mix DNS servers.

You have to choose one DNS type. Internal or External.

Secondary DNS only will be used when primary fails.

A domain not found from Primary it is a very valid, good and realiable response.

A server timed out it is a failure and because of that, your OS is going to asked to the secondary (and so on).

---

### Post by newbie-user on 2012-05-03
In my dhcpd.conf, I specify first my internal DNS server, then list the OpenDNS servers afterwards:

```
option domain-name-servers 172.25.3.242, 208.67.222.222, 208.67.220.220;
```

So when the internal DNS can't resolve a FQDN, the client goes to the OpenDNS servers for name resolution.

---

### Post by Sergius14 on 2012-05-04
> **newbie-user said:**
> In my dhcpd.conf, I specify first my internal DNS server, then list the OpenDNS servers afterwards:

```
option domain-name-servers 172.25.3.242, 208.67.222.222, 208.67.220.220;
```So when the internal DNS can't resolve a FQDN, the client goes to the OpenDNS servers for name resolution.

This is not correct.

When internal DNS can't resolve a FQDN it will reply with a "Non-existent domain".

"Non-existent domain" is a valid response -> why bother to the secondary if the asked domain doesn't exists?

This is why you can't mix.


Confusion starts when some servers gives a time out response instead of non-existant domain for non-local domains (instead of forwarding) and then OS asks to the secondary (public) DNS for that particulary FQDN.

---

### Post by newbie-user on 2012-05-04
> **Sergius14 said:**
> This is not correct.

When internal DNS can't resolve a FQDN it will reply with a "Non-existent domain".

"Non-existent domain" is a valid response -> why bother to the secondary if the asked domain doesn't exists?

This is why you can't mix.


Confusion starts when some servers gives a time out response instead of non-existant domain for non-local domains (instead of forwarding) and then OS asks to the secondary (public) DNS for that particulary FQDN.

Okay, maybe I'm wording my responses incorrectly. Yes, you are correct that a "non-existent domain" response from an internal DNS server should really mean that the domain does not exist at all.

What I'm trying to say to the OP is that you can list both internal and external DNS servers in the network config so that the OP can still resolve internal hosts. However, only the first DNS listed is the primary, so it doesn't make sense to use Google's DNS as anything other than a backup in case the internal DNS fails.

---

### Post by sonicb00m on 2012-05-06
Sorry for the lateness in replying. I was off sick two days last week and had forgotten I left this question.

I guess the only solution for me then is to use google DNS and create a list of subdomains in my host file? Only problem with that is there are so damn many of them hehe.

---

