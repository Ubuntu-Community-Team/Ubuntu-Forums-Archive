---
title: "setting up a server : port forwarding and...?"
date: 2011-06-09
forum: Networking &amp; Wireless
---

### Post by enimeizoo on 2011-06-09
Hello,
I want to set up a server, but I am behind a router. I did the port forwarding thing but it still doesn't work. Is there any other setting I have to change on the router? 
When trying to access a non-redirected port, I instantly get an error from firefox. 
```

Unable to connect.
Firefox can't establish a connection to the server at xxx.xxx.xxx.xxx:800.

```
I get another error when I try to connect a forwarded port, but firefox actually tries to connect quite a long time before.
```

The connection has timed out
The server at xxx.xxx.xxx.xxx is taking too long to respond.

```
The forwarding I did :
port 9541 to 192.168.1.15:80

I have no problem to connect from the local network, so I think it comes from the router.
Any help will be appreciated!

---

### Post by Cheesehead on 2011-06-09
Well, the first example says it cannot connect to port 800 (instead of 80), so check the router's port forwarding setup for a typo.

When outside the network, are you really looking for url [http://xxx.xxx.xxx.xxx:9541/](http://xxx.xxx.xxx.xxx:9541/) ?

---

### Post by enimeizoo on 2011-06-09
Well, the port 800 is confusing, but that is just to show what happens when I try to access a port that is not forwarded, where the router expects no connection. I geuss that since the error is different from the second error, I did the forwarding right, but I must be missing something.
I'm not sure what you mean, but I'm sure about my url, and I didn't forget the protocol (even thought firefox would have used it by default). 
Would my public address help you to find out what happens?

---

