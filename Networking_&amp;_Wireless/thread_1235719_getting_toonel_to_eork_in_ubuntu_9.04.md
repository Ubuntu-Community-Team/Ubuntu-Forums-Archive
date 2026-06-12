---
title: "getting toonel to eork in ubuntu 9.04"
date: 2009-08-09
forum: Networking &amp; Wireless
---

### Post by redzsky on 2009-08-09
hello fellow linux users i`m trying to compress my bandwidth use due to this mobile dongle and am trying to use toonel to use this as this sounds like the best option so what i want to know is  how i get this to work with Ubuntu 9.04(best operating system to date) i have set up the proxies in firefox and in the operating system preferences but am not sure which file i have to add the following to

Add the following to your shell configuration file:

export HTTP_PROXY=127.0.0.1:8080
export HTTPS_PROXY=127.0.0.1:8080
export FTP_PROXY=127.0.0.1:8080

there are many shell configuration files that i don`t know which one to add it to any help would be appreciated ,thanks for your time...

files are located in the etc directory

---

