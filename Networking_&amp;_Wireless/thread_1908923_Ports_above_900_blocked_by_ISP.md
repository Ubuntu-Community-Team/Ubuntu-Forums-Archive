---
title: "Ports above 900 blocked by ISP"
date: 2012-01-14
forum: Networking &amp; Wireless
---

### Post by sakishrist on 2012-01-14
Hello,

I am in need of your help. The problem I have is that my ISP blocks all listening ports that are above 900. This is pretty bad in my case because I use ubuntu and it does not generally allow me to listen on a port below 1024. So I was wondering whether there is some kind of trick to either let programs listen on ports below 1024 or to let a specific program listen on a given port.

Configuring my router to map the local port to different external is not an option. The thing is that I am using a torrent client and the client needs to report the port it is using. 

I use ubuntu 11.10 (x64) which has the 3.* kernel, I think. 

Thanks in advance!

Sakis

---

### Post by sakishrist on 2012-01-16
Any help please? :)

---

### Post by Fertech on 2012-01-16
who do you have service with, let me know what do you have between your computer and your internet service?

what kind of router do you have?

keep in mind that some modem have a firewall.

If you know for sure your isp is blocking above 900 then you need to call your isp

---

### Post by sakishrist on 2012-01-17
I have already talked with the ISP customer service and they told me that the "home package" includes that limit on the ports.

So, my only option could be to somehow allow applications to open ports below 900.

---

### Post by SeijiSensei on 2012-01-17
Only applications running with root privileges can open ports below 1024.  You might be able to dodge this restriction by using "sudo appname" to start the application with root privileges.

---

### Post by pricetech on 2012-01-17
Can you move up to a level of service where they don't block those ports ??

---

