---
title: "Host names?"
date: 2006-05-05
forum: Networking &amp; Wireless
---

### Post by monomaniacpat on 2006-05-05
Since I have DHCP enabled, it would be useful if I could set up my printers using the computer names, rather than the IP addresses. Can anyone tell me how I find out the names (or whatever it is I need instead of an IP) of the computers on my network?

Thank you,

mono.

---

### Post by neouser99 on 2006-05-05
are you looking for full fledged dns?

---

### Post by monomaniacpat on 2006-05-06
Well,, when looking at printer sharing through samba on many websites, they advise you to put the computer name instead of the IP. E.g on the SettingUpSamba wiki page someone put:

```
DeviceURI smb://GUEST@WARRIOR/R300
```

I don't know how this relates to DNS.

---

### Post by neouser99 on 2006-05-06
warrior needs to be translated somehow, thats through dns. i don't think that a dhcp server will translate it for you, without some soft of module or something or other... its not its job techincally. your best and easiest way to do things at the moment if you only have a couple of computers is to setup their /etc/hosts files... or windows/system32/drivers/etc/hosts depending on the machine. say warrior is at 192.168.0.103, your hosts file will look like this
```
192.168.0.103                warrior.localdomain warrior
```

let me know if that helps

-neo

---

### Post by neouser99 on 2006-05-06
warrior needs to be translated somehow, thats through dns. i don't think that a dhcp server will translate it for you, without some soft of module or something or other... its not its job techincally. your best and easiest way to do things at the moment if you only have a couple of computers is to setup their /etc/hosts files... or windows/system32/drivers/etc/hosts depending on the machine. say warrior is at 192.168.0.103, your hosts file will look like this
```
192.168.0.103                warrior.localdomain warrior
```

let me know if that helps

-neo

---

### Post by monomaniacpat on 2006-05-07
That doesn't work as the hosts list works on the assumption of static IP's. However, a quick google was sufficient to turn up the answer. I simply had to go to system properties on Windows and look under the 'Computer Name' tab. Entering the 'Full Name' into /etc/cups/printers.conf. allowed me to connect successfully.

Thanks though.

---

