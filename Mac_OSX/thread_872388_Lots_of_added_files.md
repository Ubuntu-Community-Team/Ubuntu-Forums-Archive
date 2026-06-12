---
title: "Lots of added files"
date: 2008-07-27
forum: Mac OSX
---

### Post by TedPacyga on 2008-07-27
Hey, I just did the software update from 10.5.2 to 10.5.4 and now I have all these new folders added in my main volume but the look like folders from Ubuntu.  There is like etc, var, bin.  Is this supposed to happen, I have been messing around with my mac and ubuntu, so I am just wondering if this was supposed to happen?

---

### Post by coffeecat on 2008-07-28
On your Mac desktop, open a terminal (yes, that's right, a terminal :shock: ) and do the following two commands*:

```
cd /
ls
```A lot of those directories look familiar, don't they? You've got /etc, /var and /bin there, haven't you? Not surprising really, since both Linux and MacOS X are Unix-type OSs.

However - they don't normally appear in the main volume. I guess by this you mean the finder window that opens when you double-click on the HD icon, top-right of the desktop. That's because MacOS deliberately obfuscates the structure of the file-system, partly to prevent users from poking around too much in the system. Which leads me to...

> **TedPacyga said:**
> I have been messing around with my mac and ubuntu

Exactly what was the nature of this messing around? :-s You haven't been copying system files or folders from one OS to the other, have you? :wink: Or have you been using something like Onyx or Tinker Tool?

***Edit:** or you could do one command - 'ls /' - if you're feeling  lazy.

---

### Post by TedPacyga on 2008-07-28
yes they are visible when i double click the hard drive icon on the desktop, i don't no why this is though.  By messing areound I mean just installing and uninstalling ubuntu a lot.  But as you said they shouldn't be visible, but they became visible after I installed the latest updates.

---

### Post by coffeecat on 2008-07-28
> **TedPacyga said:**
> but they became visible after I installed the latest updates.

I'm posting from my Mac atm, and I'm running 10.5.4, but all those directories don't show up in the Finder, only when I 'ls' from a terminal. Odd - I can't explain it.

Might be worth doing a search on [http://discussions.apple.com/index.jspa](http://discussions.apple.com/index.jspa)

Although I should think mention of /etc and /var would frighten the living daylights out of a lot of Mac users. :lol:

---

### Post by DeadSuperHero on 2008-07-29
Try this:

```
defaults write com.apple.finder AppleShowAllFiles NO

```

Try it under both root and user account, it should make all those extra files be invisible to you.

---

