---
title: "Can't get my wireless network working"
date: 2013-05-17
forum: Networking &amp; Wireless
---

### Post by Newb13 on 2013-05-17
So I'm trying Ubuntu, dual booted with Windows 7. When I go on my Ubuntu, it shows me the available networks, mine among them, but it can't seem to connect it. It tries to for about a minute or so and then shows a little pop-up saying I'm disconnected. I tried installing some app that its name I can't remember (something disgkt?) which is supposed to enable Windows drivers on Ubuntu, which required me to install 2 other apps. I installed the two, but when I came to the final stage of installing the disgkt app itself, it told me I'm missing another app (something with glade-2), so when I tried to install that one (I downloaded all of the apps on a different computer and then transferred them to my own using a disk on key) it told me I'm missing another one, and then when I tired to install THAT one, I needed another one, and so forth... I've been trying to solve this with no success for the past 2 hours, and I'm really frustrated. Can anyone help?

Thanks in advance.

---

### Post by Newb13 on 2013-05-21
Bump :\

---

### Post by Hadaka on 2013-05-21
Hi, to begin,Ubuntu is not windows and while
it is possible to load windows drivers, it is a last resort
fix. Please open a terminal...ctrl/alt/t  then Copy and
paste these commands..

```
lspci -nn | egrep '0200|0280' 
```

post the output.

please use code tags...like this -> [CODE] paste your out put here [\CODE]

thanks.

---

### Post by richardbond500 on 2013-05-21
What does this do? What / where do you "post the output"?

---

### Post by Hadaka on 2013-05-21
Hi, it puts the "output of the requested commannd" into code brackets..
 thusly..
```
This is the output of a requested command
```
it makes less confusing reading and is also part of the terms
of use for this forum.

```
 manual entry 
```
#you type the word ...CODE...inclosed in brackets ##```
 ##copy and paste your output here 
#then you type the word CODE again in brackets## 
``` ## *note the "/"
this puts data IN CODE TAGS.

---

