---
title: "attempt to access a webpage loads internal page instead"
date: 2012-01-09
forum: Networking &amp; Wireless
---

### Post by ahears on 2012-01-09
I am using Ubuntu 10.10 and can access the internet fine however when I call certain webpages my web browser will load a local page that I was using for a web server I was testing. I have completely removed Apache2 and the /var/www and /var/www-ssl locations only to find that this is still a problem. Example: I browse to [http://www.youtube.com](http://www.youtube.com) just fine... but.... [http://netflix.com](http://netflix.com) loads a locally saved webpage I wrote instead. There is no indicator in the website html as to how this happens but I do get the Netflix.com logo in the Firefox tab and the browser claims to be on Netflix.com. Does anyone know what might cause this? I have looked everywhere and must have forgotten something.

---

### Post by jonobr on 2012-01-10
Hello


Please post the result of

```

/etc/resolv.conf
/etc/hosts
/etc/nsswitch.conf
```

What happens when you try

```
nslookup netflix.com
```

or

```
ping netflix.com
```

Finally. Stupid question from me....
Why do you want to go to netflix.com, have they figured out how to make this work?

---

### Post by spacecheck on 2012-01-10
> **ahears said:**
> I am using Ubuntu 10.10 and can access the internet fine however when I call certain webpages my web browser will load a local page that I was using for a web server I was testing. I have completely removed Apache2 and the /var/www and /var/www-ssl locations only to find that this is still a problem. Example: I browse to [http://www.youtube.com](http://www.youtube.com) just fine... but.... [http://netflix.com](http://netflix.com) loads a locally saved webpage I wrote instead. There is no indicator in the website html as to how this happens but I do get the Netflix.com logo in the Firefox tab and the browser claims to be on Netflix.com. Does anyone know what might cause this? I have looked everywhere and must have forgotten something.

Did you go into the browser and clear the caches? If not, try that. If it works, use the thread tools to mark the thread Solved. IF not, report back for further input.

Good luck!

---

### Post by ahears on 2012-01-10
[COLOR=Black]Uggh! I was so flustered with technical settings and stuff I simply forgot to flush the browser cache, and now it works perfectly! Thank you for bringing me back to earth! This thread is SOLVED.[/COLOR]

---

