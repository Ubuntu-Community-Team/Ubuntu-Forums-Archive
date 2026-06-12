---
title: "Redirect internal traffic to webpage"
date: 2011-11-29
forum: Networking &amp; Wireless
---

### Post by LANrover on 2011-11-29
Hey, LANrover here.

Just set up my general-purpose home server today, and I plan on using it as a Media Server, Web Server (intranet only), and I plan on setting up a VPN so I can use my laptop to access my server while I'm at school.

I plan on running a File-Collaboration website over my intranet to be able to always have access to my school files/keep track of my assignments easier while I'm at school/work/wherever I have my laptop.

At work, I'm assuming they have a large scale VPN set up, and if  you type "intra" into your web browser, you're brought to my companies internal homepage.  How exactly would one go about setting this up?  I assume it can't be too hard, and I'm just guessing that it's something that I have to set up on each client station to be able to do this.  Is it something set with the VPN client, or would it be a setting I would enter into a browser config or something?

An explanation or a link to a tutorial would be greatly appreciated.

Thanks guys, rock on! :guitar:

LANrover

---

### Post by LANrover on 2011-11-29
Nevermind, I just figured it out.

For anybody looking to do the same thing, all you have to do is edit your hosts file to say something like this:

```
192.168.1.x     intra
```
Correcting this to solved for my own stupidity.

---

