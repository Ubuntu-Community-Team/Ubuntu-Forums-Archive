---
title: "Proxy Exclude Not Working for Apt-get"
date: 2012-12-12
forum: Networking &amp; Wireless
---

### Post by hackaxle on 2012-12-12
Hello, I am currently trying to configure my Ubuntu 12.04 system to be able to install from both an internal repository behind the firewall as well as Canonical's. I setup my firewall auth using cntlm using NTLMv2 and it is working successfully. I am now able to use apt-get through the firewall. However, as soon as I turn on the proxy settings I can no longer install from the internal repository. I used dconf Editor and edited ignore-hosts in system > proxy using *.domain.com, logged out and back in and still I cannot install using apt-get from internal repos. If I turn off proxy in network settings I can then install internally but not externally. Does anyone know how I can setup for both?

---

