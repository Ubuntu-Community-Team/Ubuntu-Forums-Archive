---
title: "picasa problem"
date: 2010-07-20
forum: Multimedia Software
---

### Post by skarosg3 on 2010-07-20
Hi all,
I have a problem that i just cant figure out (actually i cant even understand it)

I am trying to install Picasa, so i go to the google website, download the deb file and run it. When finished everything seems to be fine. there is a new menu for picasa and everything. when i try to run picasa, nothing happens. I restart and then the picasa menu is gone, but is consider to be installed when i see the package manager.

any ideas? thanks.

ps, sorry if this is not the right place for such a thread, but could not find any other more appropriate.

ilias

---

### Post by alfh on 2010-07-30
I have the same problem, though with a version found through synaptic (2.7.3736-15)

When I look up the google faq it says I need glibc 2.3.2 or newer, but I don't even find a package called glibc through synaptic.

I tried this command: 
```
aptitude search glibc
```

and the result is here:
> p   eglibc-source                   - Embedded GNU C Library: sources           
v   glibc-2.10-1                    -                                           
p   glibc-doc                       - Embedded GNU C Library: Documentation     
v   glibc-doc-reference             -                                           
v   glibc-pic                       -


So it looks like glibc should be updated, but since I can't find the package, how?

I see mentioned here and there that Picasa requires WINE, but there is no mention of that on the [picasa website]("http://picasa.google.com/linux/") and installing through synaptic doesn't indicate Wine either.

Very thankful for any input!

---

### Post by alfh on 2010-07-30
Following this guide at [www.webupd8.org]("http://www.webupd8.org/2010/04/how-to-install-picasa-36-in-ubuntu.html") I successfully got Picasa 3 working.

Didn't try to get 3.6, but expect that would work, too.

---

### Post by skarosg3 on 2010-07-31
For some strange reason, after many attempts, picasa 3 worked just fine!
who knows!?

---

