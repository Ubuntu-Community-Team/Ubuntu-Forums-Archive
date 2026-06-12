---
title: "Privoxy is not allowing connection to any website"
date: 2010-05-15
forum: Networking &amp; Wireless
---

### Post by Nakron on 2010-05-15
I am running karmic on a laptop. I recently changed iptables to drop all new incoming packets (not the related or established ones) on all ports. I was not running a proxy, so this worked fine. More recently I got v 3.0.13 of privoxy with apt-get and looked through the config file. I changed the default port in the privoxy config to 8080 and kept the ip at 127.0.0.1. Then I changed the Firefox settings to use a HTTP proxy at 127.0.0.1 with port 8080.  when I try to run privoxy with the command: privoxy /etc/privoxy/config , the terminal outputs no errors. Then when I try to access a webpage through firefox the page will not load, but firefox doesn't display any reason for it. I don't really even know if privoxy is running because when I check the logfile (after having uncommented the logfile line in the privoxy config file) it is blank.  I don't know much about networking, but I was wondering if someone could tell me why this is happening?   Well that was a bit dumb of me. I just had to allow new packages in from localhost.

---

### Post by katakaio on 2010-06-29
I have a similar problem on a slightly different setup: running Lucid with the latest version of Privoxy and Chromium from the Lucid repos. I configured Privoxy correctly via [this page]("https://help.ubuntu.com/community/Privoxy"), making sure to change my file to **listen-address 127.0.0.1:8118** and duplicating that information in Chromium. However, same problem as Nakron: no web page loads. It seems straightforward, but I'm obviously doing something wrong. Any thoughts?

***Edit:** I was a little to hasty - it loaded just fine, if taking 30 s to load the Google search page is fine. Everything was configured correctly, but Chromium's load time was destroyed by the use of Privoxy. Maybe this machine is too low-spec? I will investigate further . . .*

---

### Post by jdunn on 2010-06-30
I was using Privoxy for a while with Chrome.  At times, there was no slowdown.  At other times, my Yahoo webmail became unresponsive and google search results would only display half a page.  This was all with the basic Privoxy 3.0.15 settings on Lucid Lynx on a dual core 2GHz Intel processor with 4 GB of RAM.

---

