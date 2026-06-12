---
title: "Basic Mythweb setup question"
date: 2009-03-20
forum: Mythbuntu
---

### Post by David Grigor on 2009-03-20
Using mythbuntu 8.10, mythweb works fine internally.

I have mythweb password turned on through mythbuntu-control-centre.

I have port forwarding setup on the router from port 1234 to port 80 of my mythbuntu's internal static IP. 

On the  internet using xxxx.dyndns.org:1234/mythweb/

It prompts for username/password as expected and brings me to the mythweb page just fine. 

However when I go to stream the asx file it coming back with page-not-found because it's sticking :80 in the address. 

Example:  xxxx.dyndns.org:1234[COLOR="Red"]**:80**[/COLOR]/mythweb/pl/stream/1021/1237554000

Not for sure what setting or config file I need to change so that it doesn't try to append the :80 on the address.  

Thanks in advance.

---

### Post by azmyth on 2009-03-21
Backup /includes/utils.php then Line 335 or so change

```
                ? 'http://' . http_host .':'._or($_SESSION['stream']['force_http_port'], '80')
```

to

```
                 ? 'http://' . http_host
```

---

