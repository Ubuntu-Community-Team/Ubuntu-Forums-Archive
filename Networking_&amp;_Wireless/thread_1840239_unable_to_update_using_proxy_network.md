---
title: "unable to update using proxy network"
date: 2011-09-07
forum: Networking &amp; Wireless
---

### Post by amirmku on 2011-09-07
Hi,
I am newbie to ubuntu but I am enjoying it. But recently I moved to  institution where I have to access Internet through proxy network with  given username and password.

The problem is I am unable to update using update manager, even I am  unable to update using terminal. 

Update manger always return a message "connection refused".

I have changed my browser setting to proxy so I am able to access  internet . but unable to update using update manager and even unable to  access internet using terminal.

Not only this I am unable to use Team viewer and social networking  gwibber on my ubuntu 10.04

Please help me out

---

### Post by gmargo on 2011-09-07
To configure the **apt** system (which includes the update manager) to use a proxy, create (or edit) a file **/etc/apt/apt.conf** (or **/etc/apt/apt.conf.d/02proxy** if you want to get fancy)  with this content, substituting appropriately for the [optional] parts:
```

Acquire::http::Proxy "http://[[user][:pass]@]host[:port]/";

```

---

### Post by amirmku on 2011-09-08
> **gmargo said:**
> To configure the **apt** system (which includes the update manager) to use a proxy, create (or edit) a file **/etc/apt/apt.conf** (or **/etc/apt/apt.conf.d/02proxy** if you want to get fancy)  with this content, substituting appropriately for the [optional] parts:
```

Acquire::http::Proxy "http://[[user][:pass]@]host[:port]/";

```

Hey did that but still unable to add apt-add repository for updating to firefox6.

---

