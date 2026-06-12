---
title: "question regarding ssh tunnel &amp; http"
date: 2012-09-16
forum: Networking &amp; Wireless
---

### Post by flyingsliverfin on 2012-09-16
I'm trying to figure out how (conceptually) it would work if I wanted to tunnel http traffic from my laptop to my ssh server to the destination.

So for example, if I'm at school using the wifi (that I don't trust) with my laptop, I want to connect to my home server via ssh, which then forwards internet traffic to the destination.

If i wanted to do this, would it look like this? (if i have my home ssh server set up with port 4000)
```
ssh -p 4000 j@myserver -L 4500:localhost:80
```

I like to picture stuff so i tried to draw it out in the attached picture. Does it seem accurate?

Also, if I set up the command right, is the syntax after the -L equivalent to: <local exit port>:<ssh server>:<exit port for ssh server>?

---

### Post by beboylips on 2012-09-17
You can setup a proxy on your home computer. Use either PPTP or OpenVPN. PPTP is easy to setup but it has its limitations (such as it is easier to detect that it's being used). OpenVPN is harder to setup but its pretty much full-proof.

Also you can setup a web php proxy on your home computer and host it on an SSL (HTTPS) connection with apache.

That's how I would do it.

---

