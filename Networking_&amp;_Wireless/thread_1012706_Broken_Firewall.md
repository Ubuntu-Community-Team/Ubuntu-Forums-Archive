---
title: "Broken Firewall"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by BUNAC on 2008-12-16
Hello,
Can anyone help me getting my firewall up and running? I'm trying to use:

Ubuntu 8.04
Firestarter 1.0.3
Tinyproxy

I've tried following various tutorials but none of them seem to work for me. At the moment if I set firefox to the proxy localhost, port 8080 then it blocks all connections saying "Proxy Server Refused Connection" otherwise it doesn't block anything.

I hopefully want it to block the usual stuff without having to set the proxy up as it will be used as an internet gateway for other PC's.

Can anyone please help?
Thank you.
Tom

---

### Post by khelben1979 on 2008-12-16
Have you tried [the ipchains firewall?]("http://en.wikipedia.org/wiki/Ipchains")

---

### Post by BUNAC on 2008-12-16
Correct me if I'm wrong but IPChains is now IPtables?

If so I was trying to make things a little easier by using Firestarter as my interface for IPtables...

---

### Post by khelben1979 on 2008-12-16
Okay. 

Maybe you should try GUFW instead? [Look here]("http://beginlinux.wordpress.com/2008/11/23/ubuntu-810-uncomplicated-firewall-gui/") for an article on it.

---

### Post by BUNAC on 2008-12-16
Thanks khelben1979,
What would you recommend I use that with to filter web content? Should I just use GUFW instead of Firestarter and still use Tinyproxy?

---

### Post by khelben1979 on 2008-12-16
I think you should start using GUFW instead of the Firestarter program.

I have never tried the program myself.

---

