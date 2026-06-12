---
title: "Update Ubuntu via proxy"
date: 2011-02-25
forum: Networking &amp; Wireless
---

### Post by Ema0404 on 2011-02-25
Hi all, from a few days I stay at my uncle's home preparing some exams for the University and I can connect to Internet with the w-ifi of the shop of my uncle that's in the same building, but for do that I need to connect via proxy at the server which manges the users.
So I go to System->Preference->Proxy and I add a new profile and configure manually the protocols adding the domain's IP (xxx.yyy.1.3), the port (8080) and in details user name (my_user_name) and password (password),

After that, if I open Firefox, it asks me to insert "domain\my_user_name" and "password" and then I can navigate on Internet, and up to here it's all right. But, if I want to update my system I receive the following error:
```

407  Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

```What's the problem?

I've all ready tried to modify the /etc/apt/apt.conf adding ```
Acquire::http::proxy "http://username:password@ipdomain:port/";
``` but it doesn't work.

Please, help me.

---

