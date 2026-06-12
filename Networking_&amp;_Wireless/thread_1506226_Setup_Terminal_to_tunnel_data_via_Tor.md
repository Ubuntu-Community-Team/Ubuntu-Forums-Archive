---
title: "Setup Terminal to tunnel data via Tor"
date: 2010-06-10
forum: Networking &amp; Wireless
---

### Post by N3RVE on 2010-06-10
I have just installed Tor from torproject.org and installed Polipo, as well as Vidalia (GUI to manage Tor). Everything is working as it should and I can connect to the internet with Tor.

I've just installed Ubuntu Tweak and they are a couple of applications I want to install. Although, when I attempt to download the apps, it makes a direct connection seeing that I've not been able to configure it to use the proxy address / port ( 127.0.0.1:8118 ) I setup with Tor. I need atleast, The Ubuntu Software Center, Terminal, Synaptics Package Manager, or UbuntuTweak to connect using Tor. Does anyone have a way around this? Any help is appreciated.

-[n3rve]

---

### Post by N3RVE on 2010-06-10
Sorry for the bump, I just need to know how to configure the aforementioned applications to connect via a proxy. I'm sure they are already people using Proxies with their setups.

-[n3rve]

---

### Post by N3RVE on 2010-06-11
Bump!

---

### Post by N3RVE on 2010-06-11
Too bad, I should try somewhere else.

---

### Post by N3RVE_deact on 2010-12-24
I realise the tread is old but just incase someone needs this. You can apply your proxy settings system wide by going to System -> Preferences -> Network Proxy.

---

### Post by ottosykora on 2010-12-26
OK, and then you fill then the socks proxy field there? This should give you the function permanantly, but do you use then same port for all sevices?

---

### Post by N3RVE_deact on 2011-01-11
> **ottosykora said:**
> OK, and then you fill then the socks proxy field there? This should give you the function permanantly, but do you use then same port for all sevices?

The "Network Proxy Preferences" dialogue has fields for other protocols, Secure HTTP, SOCKS and FTP. If an application attempts to connect using either of the other protocols, say "SOCKS", I'll expect it to connect with the port defined there.

---

### Post by HtmlGifted on 2012-03-29
any one know how to set all services for a proxy through tor.. in kubuntu.? thanks

---

