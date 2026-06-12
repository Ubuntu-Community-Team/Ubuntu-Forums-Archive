---
title: "How to setup global proxy?"
date: 2010-10-11
forum: Networking &amp; Wireless
---

### Post by guimenez on 2010-10-11
Please, how do i set up the global proxy in Kubuntu 10.10

i need to use internet and install software packages. But when i run sudo apt-get update it can't connect

thanks

---

### Post by ankith13 on 2010-10-11
just try 

$export http_proxy="your proxy:port number"

let me know if it works

---

### Post by guimenez on 2010-10-11
Thanks for replying. I've try that but doesn't work with packages install :( 
just for internet

Thanks

---

### Post by Gone fishing on 2010-10-11
try ```
sudo -i
``` 

then

```
export http_proxy=http://192.168.1.1:3128
```

worked for me however, as an Ubuntu user I have to say having to use the commandline to do something as basic as setting up the proxy is a bit crap

---

### Post by Gone fishing on 2010-10-11
OK that works with apt-get but kpackagekit still doesn't work

---

### Post by guimenez on 2010-10-12
Thanks, it works, but just for the root user :(

i will back to Ubuntu, its not so complicated to configure :D

thanks once again

---

### Post by Gone fishing on 2010-10-12
Yes got apt to work but have failed to get kpackagekit to work. I've even tried enabling the root account and graphical login setting everything up from root but kpackagekit **will** not use the proxy settings - hence hardware drivers wont work etc.

Seems to me that Kubuntu is fundamentally broken

---

