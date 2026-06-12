---
title: "Run script after dhcpd assigned ip to client"
date: 2009-11-16
forum: Networking &amp; Wireless
---

### Post by oddwareso on 2009-11-16
Hello, 

Does anyone know if there is a way to get dhcpd to run a script on the server side after a client has requested an ip? I would like the script to run a check on the mac address and then depending on what the result is either re-direct the users browser to a page on the server or allow access to internet. the closest thing i can find is along the lines of running tail on the messages log for events. Unfortunately the script will lock up while it waits for tail. Is there any "Event" i can use to invoke the startup of a script on the server side?

---

### Post by capscrew on 2009-11-17
> **oddwareso said:**
> Hello, 

Does anyone know if there is a way to get dhcpd to run a script on the server side after a client has requested an ip? 
  My guess is that dhcpd will not trigger a script directly.  The request, offer, etc. routine for an IP address is unto itself.> 
I would like the script to run a check on the mac address and then depending on what the result is either re-direct the users browser to a page on the server or allow access to internet. 
This is probably best handled with a proxy server such as squid. > 
the closest thing i can find is along the lines of running tail on the messages log for events. Unfortunately the script will lock up while it waits for tail. Is there any "Event" i can use to invoke the startup of a script on the server side?
Squid will limit specific hosts access to the internet.  But you have to configure each client to use the proxy.  The event is the clients HTTP request.

---

### Post by TankEnMate on 2010-02-21
There is a config entry you can put in your dhcpd.conf file that will allow you to run stuff when events occur. In dhcpd 3.1pre there was the ability to exec programs but I'm not sure if that is still around, you'd have to have a look at the source.

---

### Post by TankEnMate on 2010-02-21
Just went away and looked it up, you'll want something like this in your dhcpd.conf file...

```
on commit {
        set ClientIP = binary-to-ascii(10, 8, ".", leased-address);
        set ClientMac = binary-to-ascii(16, 8, ":", substring(hardware, 1, 6));
        log(concat("Commit: IP: ", ClientIP, " Mac: ", ClientMac));
        execute("/usr/sbin/my_script_here", "commit", ClientIP, ClientMac);
}
```

Please note that the script you call is called synchronously, this means if your script takes time to run it will stop your dhcpd server from responding. If your script takes a while to run make sure you fork and get the parent to exit straight away.

---

