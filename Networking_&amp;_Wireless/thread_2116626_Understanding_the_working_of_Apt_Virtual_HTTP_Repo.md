---
title: "Understanding the working of Apt Virtual HTTP Repository"
date: 2013-02-16
forum: Networking &amp; Wireless
---

### Post by cyanide911 on 2013-02-16
*[SIZE="2"](Not exactly an Ubuntu question, but I hope it's not a problem if I ask it here)[/SIZE]*

My university has a virtual HTTP repository which we can access by changing our proxy to 10.1.1.224:3142. Our regular proxy to access the internet is 10.1.8.44:8080. It incredibly speeds up download speed with apt-get update and install commands.

Now sometimes I encounter various issues with my network connectivity when trying to use apt-get update or install with the repository, and I never know how to fix it or even try to figure out whats wrong since I have no understand of how it works.

So for a networking noob, can you explain how such virtual HTTP repository systems work? Do they have a storage of all packages? That seems a bit impossible. Or is it just sort of a gateway to access the Ubuntu repositories at unrestricted speeds? What happens if I change my repository server (in update manager) from say, Main servers to some other server? It still seems to work. And what happens if I add a custom PPA?

Here's a link of a screenshot of the page that appears if I open 10.1.1.224:3142 when behind 10.1.8.44:8080, if it helps you guys to understand what sort of proxy I'm talking about.

[http://i.imgur.com/NTVLV9R.png?1](http://i.imgur.com/NTVLV9R.png?1)

---

