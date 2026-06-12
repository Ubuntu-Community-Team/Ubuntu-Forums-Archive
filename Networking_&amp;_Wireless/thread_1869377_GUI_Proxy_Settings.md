---
title: "GUI Proxy Settings"
date: 2011-10-25
forum: Networking &amp; Wireless
---

### Post by insecure hyena on 2011-10-25
Hi community a simple question to which I actually didn't find a good answer.
How can I install on Xubuntu 11.04 the GUI to change the proxy settings used until the release 11.04 of Ubuntu?
Here the screenshot of the application I'm talking about.

[IMG]http://taggi.cse.unsw.edu.au/FAQ/Ubuntu/SetNetworkProxy.png[/IMG]

---

### Post by Toz on 2011-10-25
Try creating a file in /etc/profile.d called proxy.sh
```
gksudo mousepad /etc/profile.d/proxy.sh
```
...with the following content:
```
export http_proxy="http://www-proxy.cse.unsw.edu:3128"
export https_proxy="http://www-proxy.cse.unsw.edu:3128"
export ftp_proxy="http://www-proxy.cse.unsw.edu:3128"
```
...(this assumes that your university uses the same http proxy for https and ftp protocols. If not, adjust accordingly).

Make the file executable:
```
sudo chmod +x /etc/profile.d/proxy.sh
```

Then log out and back in again. The proxy settings should take effect. Sorry I can't test it - no access to a proxy.

---

### Post by insecure hyena on 2011-10-26
Thank you for your response and interest!
I assume that actually there's no way to install the front-end I'm referring about in this thread.
However I'll try your suggestion.
Thank you again

P.S: I'll leave this thread open hoping someone has the right solution.

---

