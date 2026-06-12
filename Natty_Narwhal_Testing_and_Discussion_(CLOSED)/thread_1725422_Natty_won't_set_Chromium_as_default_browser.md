---
title: "Natty won't set Chromium as default browser?"
date: 2011-04-09
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by moore.bryan on 2011-04-09
My clean install of Natty won't let me register Chromium as the default browser, even though that's what's set in Preferred Applications. Any ideas, oh wise community?

---

### Post by techunit on 2011-04-09
Your posting in the wrong category for problems with natty. You should post in the Development Natty category. Most of the General Help guys aren't going to know how to help.

Best of luck to you.

---

### Post by moore.bryan on 2011-04-09
Thanks, techunit... good point. I'm just coming-back to Ubuntu after a foray into some other distros and forgot Natty wasn't the scheduled release yet.

To any admin who works their way around to this thread: could you please move it? Thanks, in-advance!

---

### Post by techunit on 2011-04-09
Good luck fixing the issue. You may find the setting under preferred applications. Sorry I didn't suggest this earlier but I was on my way out the door.

---

### Post by mc4man on 2011-04-09
What happens if you go 
```
sudo update-alternatives --config gnome-www-browser
```
and type the # for  /usr/bin/chromium-browser

---

### Post by VMC on 2011-04-09
I'm not sure about Chromium but every time I install Chrome and run it for the first time, that's the first question Chrome it asks and from then on its Chrome only.

Also under Chrome: "Preferences > Basics > Default Browser" option there's a selection.

---

### Post by ktp on 2011-04-09
> **moore.bryan said:**
> My clean install of Natty won't let me register Chromium as the default browser, even though that's what's set in Preferred Applications. Any ideas, oh wise community?

Are you using daily builds?  If so then there was bug/regression introduced few days ago.

---

### Post by moore.bryan on 2011-04-10
> **mc4man said:**
> What happens if you go 
```
sudo update-alternatives --config gnome-www-browser
```
and type the # for  /usr/bin/chromium-browser
No dice.

> **ktp said:**
> Are you using daily builds?  If so then there was bug/regression introduced few days ago.
Ah, this may be the problem... I *am* using the daily build. ktp, do you happen to know the link to the bug report?

---

### Post by KegHead on 2011-04-10
Hi!

I found chromium with just a google search.

Agree to a few itews and download.

KegHead

---

### Post by frankbooth on 2011-04-10
Had the same problem, ended up removing firefox :roll:.
A proper fix would be nice though.

---

