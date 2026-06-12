---
title: "SSH via Internet"
date: 2010-01-28
forum: Networking &amp; Wireless
---

### Post by den_elze on 2010-01-28
hi,

I would like to setup an ssh connection to my laptop at home which runs ubuntu 9.10

what I did was:

- install openssh-server
- configure my router to port-forward external port 22 to internal static ip of the laptop with the same port.

but when I try to ssh to the public ip, there is a timeout. Can someone give me some tips?

- is there a fw installed in the default 9.10 installation of ubuntu?

thx,

Koen

---

### Post by dmizer on 2010-01-28
> **den_elze said:**
> hi,

I would like to setup an ssh connection to my laptop at home which runs ubuntu 9.10

what I did was:

- install openssh-server
- configure my router to port-forward external port 22 to internal static ip of the laptop with the same port.

but when I try to ssh to the public ip, there is a timeout. Can someone give me some tips?

- is there a fw installed in the default 9.10 installation of ubuntu?

thx,

Koen

When you tested, did you test from a remote network, or did you test from within your LAN? Most retail (low end) routers are not capable of loop back, so you'll have to test from another location.

---

### Post by den_elze on 2010-01-29
I am able to ssh to the internal and external ip of the laptop, from the laptop itself. I don't have another machine at home to test from. But I can't seem to connect from work

---

### Post by dmizer on 2010-01-29
> **den_elze said:**
> I am able to ssh to the internal and external ip of the laptop, from the laptop itself. I don't have another machine at home to test from. But I can't seem to connect from work

Do you have a firewall enabled on the laptop? Assuming your external IP is dynamic rather than static, do you have a dynamic host like [dyndns]("http://www.dyndns.com/") configured? If not, how are you determining that you're hitting the correct external IP from work?

If you are positive you're hitting the correct external IP address, then your work may be blocking port 22 outbound. You should probably discuss the issue with your office network administrator if that's the case.

---

### Post by Skaperen on 2010-01-29
> **dmizer said:**
> If you are positive you're hitting the correct external IP address, then your work may be blocking port 22 outbound. You should probably discuss the issue with your office network administrator if that's the case.Another option is to change the port to a different number. Be sure it is changed at all places as appropriate. Not all port numbers are equal, either. For example, your work may be allowing port 80 out for web access, but your ISP may be blocking port 80 in to prevent running web servers (even though you could run an ssh server there if a web server were not running).

Also, be sure your activity is compliant with your work policy. If the policy is to disallow all ssh connections, just because they only enforce it at port 22 could still leave you in violation by doing it at another port. It's your responsibility to comply with all applicable work rules, policies, laws, etc.

---

### Post by SecretCode on 2010-01-29
For testing reasons, and for avoiding restrictions imposed by companies (as a consultant I've seen lots of different levels of restriction), I always recommend getting a 3G mobile service.

den_elze, I don't know what country you're in and whether 3G is available and economic there, but for me a 3G card - with prepaid bandwidth that doesn't expire - is perfect. I can test how my home firewall appears from the internet without leaving home. And I don't have to go through the hassle of working through corporate networks (which can be pretty congested even if the policy allows it).

Meanwhile ... how is your home router connected to the internet? ADSL? If you just have an external ADSL modem device, is that set up as a router or a bridge?

Is your public IP address (for your home router) always the same?

---

### Post by doas777 on 2010-01-29
when you get home, from the laptop go to [http://www.canyouseeme.org/](http://www.canyouseeme.org/) and make sure they can see prt 22.

---

