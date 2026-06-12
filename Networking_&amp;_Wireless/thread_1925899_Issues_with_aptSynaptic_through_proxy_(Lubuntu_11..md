---
title: "Issues with apt/Synaptic through proxy (Lubuntu 11.10)"
date: 2012-02-15
forum: Networking &amp; Wireless
---

### Post by HansRuesch on 2012-02-15
Hi everyone.

I have recently installed Lubuntu 11.10 on an old laptop, and everything seems to be working just fine except from one thing: I cannot manage to make apt, Synaptic, or the Update Manager connect through a Proxy.

So far I have tried the following:

- Entering my settings on Synaptic's own configuration dialog.

- Adding the following, manually, to ~/.bashrc and /etc/bash.bashrc
export http_proxy=http://myserver.net:port/
export ftp_proxy=http://myserver.net:port/

Another solution I came across while Googling is to manually edit /etc/apt/apt.conf, but that particular file doesn't exist on my installation.

I know that my settings are correct, since they work well on other software (Firefox, Chromium). I also assume that there is nothing wrong with my hardware, as there are no issues when connecting to the Internet directly.


Any ideas greatly appreciated

Cheers!

---

### Post by jerrrys on 2012-02-16
What about creating an apt.conf file?

[https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy](https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy)

---

### Post by HansRuesch on 2012-02-21
> **jerrrys said:**
> What about creating an apt.conf file?
[https://help.ubuntu.com/community/Ap...e_a_http-proxy]("https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy")

 
 That actually worked. Thanks!

---

