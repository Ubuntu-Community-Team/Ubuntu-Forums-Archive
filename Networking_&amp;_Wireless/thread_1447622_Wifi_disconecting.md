---
title: "Wifi disconecting"
date: 2010-04-05
forum: Networking &amp; Wireless
---

### Post by bgrohe on 2010-04-05
I am running a server in my basement of my wifi network. The problem is that even when the computer is on it is not always connected. Therefore it doesn't accept any requests. and I can't find the problem. It has full signal and it doesn't seen to be disconnected on the desktop.

---

### Post by czarama on 2010-05-05
Hello,

I have similar problem, at the work my wifi get connected but after 2 -5 minutes it stop working, the signal and the ip seems OK, then I turn the wifi off/on and it works again.

The most strange is that at home my wifi works perfect. And at the office another college uses Kubuntu as well and he has no problem.

In 9.10 everything was perfect the issue comes with 10.4.

Any Ideas?

---

### Post by int on 2010-05-05
What pc do you have?

---

### Post by udippel on 2010-05-05
> **czarama said:**
> Hello,

I have similar problem, at the work my wifi get connected but after 2 -5 minutes it stop working, the signal and the ip seems OK, then I turn the wifi off/on and it works again.

The most strange is that at home my wifi works perfect. And at the office another college uses Kubuntu as well and he has no problem.

In 9.10 everything was perfect the issue comes with 10.4.

Any Ideas?

Had you taken to *search* the forum before posting, you would have noticed hundreds, if not thousands of likewise situations.
[/RANT]

Let me take a guess: at home you are about the only power user of the access point?

Uwe

---

### Post by czarama on 2010-05-05
Yes at home is me ho set up the wifi and we are only 2 pc to use the connection.

I already have done lot of search, already updated the drivers to the last drivers on backports still no success.

My computer is an HP elitebook 8530w

---

### Post by udippel on 2010-05-05
> **czarama said:**
> Yes at home is me ho set up the wifi and we are only 2 pc to use the connection.



Yes, that confirms my own observations. When there is low load, it keeps going, to some limits. I can forcefully bring down the link here by just adding a second, high data rate user.

No chance, I guess, we need to use wired and wait for some rectification from Ubuntu.

Uwe  :(

---

### Post by czarama on 2010-05-05
Do you know where we can report this problem?

---

### Post by udippel on 2010-05-05
> **czarama said:**
> Do you know where we can report this problem?

It has been reported, some bug reports filed. As of now, no 'official' reaction.

---

### Post by czarama on 2010-05-12
I saw than the problem is with kernel 2.6.32-22

I switch back to 2.6.32-21 and now is working fine.

---

