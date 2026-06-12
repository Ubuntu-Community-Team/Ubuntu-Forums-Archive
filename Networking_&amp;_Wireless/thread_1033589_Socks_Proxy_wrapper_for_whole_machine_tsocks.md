---
title: "Socks Proxy wrapper for whole machine? tsocks?"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by cforrest on 2009-01-07
I currently have a Ubuntu Hardy server install at my work which needs to go through a socks5 proxy to reach the outside world. I have tsocks setup and am using it for things such as apt-get:
```
tsocks apt-get update
```
The problem is that this machine is being used for an intranet apache server which needs to pull down some RSS feeds from the outside world.

The current server is a windows xp box running an application called "[Hummingbird Socks]("http://connectivity.hummingbird.com/products/nc/socks/")" which runs silently in the background and redirects outgoing requests to the proxy. I have successfully transfered all functionality to the Ubuntu box with the exception of being able to pull the RSS feeds.

I am looking for some sort of solution similar to the "[Hummingbird Socks]("http://connectivity.hummingbird.com/products/nc/socks/")" I am currently using on the Windows XP box. I don't want to have to go through the mediawiki and drupal code and edit the php to get it to direct through the proxy.

Any way tsocks can be used to do this? Some other solution?

---

### Post by sullivanjc on 2009-02-15
I'd like to know the same thing.  I too use Hummingbird socks on Windows machines and would like to know how to do the same in Linux.

---

### Post by jeszi on 2009-07-02
I need it too. Can anyone help?

---

### Post by teedubb on 2009-07-06
could you achieve this with [proxy chains]("http://proxychains.sourceforge.net/")?  proxy chains is similar to tsocks but proxy chains seems to be more flexible, you can just "apt-get install proxychains".  also could you not just use tsocks to pull in those rss feeds?

---

