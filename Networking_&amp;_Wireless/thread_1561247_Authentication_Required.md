---
title: "Authentication Required"
date: 2010-08-26
forum: Networking &amp; Wireless
---

### Post by tekybrit on 2010-08-26
Why does this message appear when everything works ok?

[Screenshot.png]("http://ubuntuforums.org/attachment.php?attachmentid=167526&stc=1&d=1282798175")

The number following "localhost:" is not always the same, probably changes each time I restart.

I have a HP Touchsmart 600-1105XT, I can access my email, NAS and other PC's fine.
But when I use Firefox, the message above appears, I just click cancel & Firefox works fine.

It may not be related, but the wireless icon on the top bar is missing, I have to do Alt F2 "nm-applet" to get it to show.

Also in network manager, when I look at my wireless connection it says "Last used 18 days ago", how can that be when I am using it every day?
When I try to Edit the wireless setting I am told I have "Insufficient privileges."

I realize my problems are trivial, but I would like to understand what's going on.

---

### Post by lovinglinux on 2010-08-26
That problem is probably due to bindwood application. Remove *bindwood* and *xul-ext-bindwood* to solve the problem.

Form a terminal:

```
sudo apt-get purge bindwood
sudo apt-get purge xul-ext-bindwood
```

If you need a sync tool for Firefox, use [Firefox Sync]("https://addons.mozilla.org/en-US/firefox/addon/10868/"). It can Sync bookmarks,  passwords, settings, history and tabs. This extension is already a default feature in the latest Firefox 4 Beta.

---

### Post by tekybrit on 2010-08-26
Thanks, that was great to have it solved so quickly.

---

### Post by lovinglinux on 2010-08-26
> **tekybrit said:**
> Thanks, that was great to have it solved so quickly.

You are welcome.

---

### Post by Neobuntu on 2010-09-03
Removing those(and I rebooted), did not stop the pop up, just as pictured, for me.

Ubuntu 10.04 upgraded now, Firefox 3.6.8 Ubuntu.

[www.regions.com](www.regions.com) bank-site still does this.

---

### Post by Iowan on 2010-09-03
> **tekybrit said:**
> Thanks, that was great to have it solved so quickly.
Consider marking the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") :)
@Neobuntu:
 Consider starting a new thread - link to this one...

---

