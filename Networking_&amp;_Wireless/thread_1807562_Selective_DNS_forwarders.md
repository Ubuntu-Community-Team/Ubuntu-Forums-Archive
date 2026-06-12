---
title: "Selective DNS forwarders"
date: 2011-07-19
forum: Networking &amp; Wireless
---

### Post by ocwo92 on 2011-07-19
I have a running name server with a couple of DNS forwarders.

If possible, how do I configure the name server so that for some addresses, the server uses a certain selection of DNS forwarders while for other addresses, it uses the default forwarders?

---

### Post by jmoorse on 2011-07-19
Hello, you should be able to create zones in your bind config with forwarders.

Eg:
```

zone "siteA.com" {
        type forward;
        forwarders {10.10.10.10;};
};
zone "siteB.com" {
        type forward;
        forwarders {172.16.16.16;};
};

```

Remember these forwarders will apply to any subdomains of the defined top level domains.

Hope that helps

---

### Post by ocwo92 on 2011-07-20
> **jmoorse said:**
> Hope that helps
Absolutely. Thanks!

I currently have only a small number of external sites that require a different DNS service, so it is not a big deal to enter the sites individually. Nevertheless, is it possible to enter the domains in list or read them from a file?

---

### Post by SeijiSensei on 2011-07-20
You can always add name/address pairings to /etc/hosts, but they'll be specific to that machine.  If you need to support multiple clients, you'd need to change /etc/hosts on all of them.

---

