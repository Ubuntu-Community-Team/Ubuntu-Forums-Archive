---
title: "Stop using a proxy"
date: 2009-10-05
forum: Networking &amp; Wireless
---

### Post by dhubbard on 2009-10-05
I installed Bfilter a while ago, and decided that I preferred to stop using it, no problems. I went into the KDE and the Gnome settings and told them to stop using the proxy settings - but it doesn't seem to effect some of the programs I use. Specifically anything to do with using the console and Chromium all try to keep using the proxy to connect to the internet.

Any help would be appreciated, I've searched, but I can't find a solution. 
I'm using Kubuntu 9.10.

---

### Post by dhubbard on 2009-10-05
After some more in-depth searching I have found out a couple of things - but no solution yet.

When I do '$ cat /etc/apt/apt.conf' I get:
```
Acquire::http::proxy "http://127.0.0.1:8080/";
```
I tried uncommenting that, but I still get the same result.

I have tried the 'unset http_proxy' command with no result.

Suddenly Chromium is working, not trying to use the proxy anymore - but I still have zero success when I try to use the console.

---

### Post by tuwe on 2009-10-09
i have exactly the same problem. my temporary solution is to type ```
export http_proxy=""
``` in the terminal every time i log in.

edit: better solution to the problem: uninstall bfilter completely

```
sudo aptitude remove --purge bfilter
```
and reboot

i even managed to reinstall bfilter and use it for my browser only. i use chromium and appended "--proxy-server=127.0.0.1:8080" to CHROMIUM_FLAGS in /etc/chromium-browser/default. Now it looks like this:
```
~$ cat /etc/chromium-browser/default
# Default settings for chromium-browser. This file is sourced by /bin/sh from
# /usr/bin/chromium-browser

# Options to pass to chromium-browser
CHROMIUM_FLAGS="--proxy-server=127.0.0.1:8080 --enable-plugins"

```

---

