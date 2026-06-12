---
title: "Add repos by terminal behind proxy"
date: 2011-06-21
forum: Networking &amp; Wireless
---

### Post by srisharan on 2011-06-21
We use an authenticated proxy in my university.I am not able to add repos by 
sudo apt-get-add-repository.I get the following error(for firefox for example)


*Error reading [https://launchpad.net/api/1.0/~mozillateam/+archive/firefox-next:](https://launchpad.net/api/1.0/~mozillateam/+archive/firefox-next:) <urlopen error [Errno 111] Connection refused>*

I have tried ti change the port by this method
[http://www.omgubuntu.co.uk/2011/01/how-to-add-repositories-to-ubuntu-from-behind-a-firewall/]("http://www.omgubuntu.co.uk/2011/01/how-to-add-repositories-to-ubuntu-from-behind-a-firewall/")
But it didn't work out.apt-get update and upgrade work fine.Adding repos worked fine at home.
Kinda new to Ubuntu(really loving it by the way:D),so please give a bit elaborate explanations

---

### Post by srisharan on 2011-06-22
guys,please help

---

### Post by gmargo on 2011-06-22
It's not failing on getting the key (which is what the edits to ppa.py are for).
Instead it's failing to get the key fingerprint via secure http.
Probably because you need to give it a pointer to your proxy.
Did you try adding **http_proxy** and **https_proxy **environment variables?

```

sudo env http_proxy=ProxyInfo https_proxy=ProxyInfo add-apt-repository ppa:mozillateam/ppa

```

---

### Post by srisharan on 2011-06-23
I think this might work but I am not able to work out exactly the format in which my proxy info (authenticated) should be in.Can you please tell me.

I have already tried username: pass@proxy: port

---

### Post by gmargo on 2011-06-23
I think the appropriate format is:
```

http://[[user][:pass]@]host[:port]/

```Don't forget the http:// part.

---

### Post by srisharan on 2011-06-23
Great It worked.Thank you :D

---

