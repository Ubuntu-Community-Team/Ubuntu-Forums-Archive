---
title: "Automatic Proxy not detected"
date: 2009-04-22
forum: Networking &amp; Wireless
---

### Post by charafantah on 2009-04-22
Am using Kubuntu 9.04, i have a proxy at work which i do not know the settings for.

However, when i set firefox to automatically detect proxy settings, it works fine.

But when i choose from System Setting> Network Settings> Automatically detect proxy configuration
I get a notification that: "Could not find a usable proxy configuration script"

Thus rendering all applications with no internet access, except firefox.


Thanks,

---

### Post by suxenexus on 2009-04-23
Got a similar problem.  I placed the necessary proxy settings in system settings>network settings>proxy>manually specify proxy settings>setup dialog but still other kubuntu programs using the internet don't work.  Also I can't update Kubuntu :)

---

### Post by puppywhacker on 2009-04-23
The 2nd option "auto-detect proxy" will try a few methods of finding the proxy script using DHCP, SLP and DNS to find a file with the extension .pac

This automatic proxy-configuration url can also be filled in at the 4th option.

The PAC file looks like this

```
function FindProxyForURL(url, host)
{
      return "PROXY webcache.domain.com:3128" ;
}

```
the statement PROXY is the actual proxy you can use at the manual configuration at the 3rd option, this is also the proxy you can fill the "Proxy Settings"

[http://www.davidpashley.com/articles/automatic-proxy.html](http://www.davidpashley.com/articles/automatic-proxy.html)

---

### Post by charafantah on 2009-04-23
I found out where is my wpad.dat file is located and got it:

```
function FindProxyForURL(url, host) {

// If URL has no dots in host name, send traffic direct.
	if (isPlainHostName(host))
		return "DIRECT";

// If specific URL needs to bypass proxy, send traffic direct.
	if (shExpMatch(url,"*sqs.int*"))           return "DIRECT";

// If own address is part of an UK network, send traffic direct.
	if (isInNet(myIpAddress(), "10.16.0.0", "255.255.0.0")) return "DIRECT";
	if (isInNet(myIpAddress(), "192.168.0.0", "255.255.0.0")) return "DIRECT";
	
// If IP address is internal or hostname resolves to internal IP, send direct.

	var resolved_ip = dnsResolve(host);

	if (isInNet(resolved_ip, "10.0.0.0", "255.0.0.0") ||
		isInNet(resolved_ip, "172.16.0.0",  "255.240.0.0") ||
		isInNet(resolved_ip, "192.168.0.0", "255.255.0.0") ||
		isInNet(resolved_ip, "127.0.0.0", "255.255.255.0"))
		return "DIRECT";
					
// All other traffic uses below proxies, in fail-over order.
	return "PROXY proxy.COMAPNY.int:8080; DIRECT";
	
}
```

I tried to point KDE to the URL and i tried to set the settings manually. 
None worked (Plasmoids now have access to internet, e.g. weather component, but other applications no, e.g. apt, kopete)....although it no longer display the error message stating that the config file cannot be found.

and Firefox is still working fine :) long live FF :)

---

### Post by bubuzzz on 2009-10-16
so...no solution for this problem??? I can surf by Konqueror but cannot update by terminal .... so weird :confused:

---

### Post by AugustinZ on 2010-05-20
In System Settings --> Network & Connectivity --> Network Settings -- > Proxy set the proxy settings to "Connect to the Internet directly" and restart NetworkManager (or perhaps KDE reset would do the job). And also perhaps edit the settings in your browser (chat clients, mail client, etc.) to something like "no proxy" or "connect to the internet directly", etc. Enjoy...

---

