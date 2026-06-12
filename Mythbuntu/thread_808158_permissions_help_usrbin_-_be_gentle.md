---
title: "permissions help /usr/bin - be gentle"
date: 2008-05-26
forum: Mythbuntu
---

### Post by docjay on 2008-05-26
Okay guys - I'm a bit of newb with linux, been using myth for about 7-8 months & this is the first I've had to mess with permissions...& I just don't want to make anything worse than what it already is.  I've did some searching but from what I've tried, it seems that I'm digging myself into a hole so I'm gonna ask for some help. Let me explain, & sorry for the novel, just want to make sure I didn't miss any points.

I installed the XM integration script [here]("http://www.mythtv.org/wiki/index.php/Integrate_XM"), the install went fine, I could listen to XM channels through command line okay, but the menus in Myth wouldn't do anything for me so I though I would ask the author later - but later that day I wanted to listen to XM through myth with the command line again and I ran 'xamp 48' and it told me that my user didn't have read permissions to /usr/bin, which is where xamp was installed.  So, I did a CHOWN /usr/bin/xamp and now when I run xamp it always wants to look @ /usr/bin/xamp even though I've deleted the relevent files there and reinstalled the script to /home/myusername/, which installed just fine.  

So, now when I run 'xamp 48' it comes back with:  bash: /usr/bin/xamp: No such file or directory.  Is there anyway to tell ubuntu not to look in /usr/bin for xamp anymore?

Docjay

---

### Post by majoridiot on 2008-06-02
> **docjay said:**
> Okay guys - I'm a bit of newb with linux, been using myth for about 7-8 months & this is the first I've had to mess with permissions...& I just don't want to make anything worse than what it already is.  I've did some searching but from what I've tried, it seems that I'm digging myself into a hole so I'm gonna ask for some help. Let me explain, & sorry for the novel, just want to make sure I didn't miss any points.

I installed the XM integration script [here]("http://www.mythtv.org/wiki/index.php/Integrate_XM"), the install went fine, I could listen to XM channels through command line okay, but the menus in Myth wouldn't do anything for me so I though I would ask the author later - but later that day I wanted to listen to XM through myth with the command line again and I ran 'xamp 48' and it told me that my user didn't have read permissions to /usr/bin, which is where xamp was installed.  So, I did a CHOWN /usr/bin/xamp and now when I run xamp it always wants to look @ /usr/bin/xamp even though I've deleted the relevent files there and reinstalled the script to /home/myusername/, which installed just fine.  

So, now when I run 'xamp 48' it comes back with:  bash: /usr/bin/xamp: No such file or directory.  Is there anyway to tell ubuntu not to look in /usr/bin for xamp anymore?

Docjay

if all else fails, make a symlink that points to the location of the proper executable. e.g.:

if there is an existing /usr/bin/xamp you should delete it first:

```
$ sudo rm /usr/bin/xamp
```

then make the link:

```
$ sudo ln -s /location/of/executable /usr/bin/xamp
```

```
$ man ln
``` for more info

---

