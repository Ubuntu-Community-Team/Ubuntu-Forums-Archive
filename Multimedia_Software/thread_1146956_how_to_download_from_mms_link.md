---
title: "how to download from mms link"
date: 2009-05-03
forum: Multimedia Software
---

### Post by sam1948 on 2009-05-03
```
sudo aptitude install mplayer
```
enter sudoer pass and wait for installation to be done.

the following link is from an Israeli news
u just have to put instead the address u wish to download
```
mplayer mms://s3fwm.castup.net/server12/248/481/48150600-61.wmv -dumpstream -dumpfile foo.wmv
```

mplayer will save the file from streaming to the file foo.wmv
it might take some time depending on the video size/duration 

have fun

many thanks to **sutee** in this link
[http://www.howtoforge.com/forums/showthread.php?t=1827](http://www.howtoforge.com/forums/showthread.php?t=1827)

---

### Post by 21jeremy21 on 2009-07-05
Im having an issue with this, and I'd love some help. The particular mms link that I'm interested in has **.../wm/[COLOR="Red"]_![/COLOR]/comedy/...** in its address and the terminal doesn't seem to like it.

I get the following error when I hit enter

```

bash: !/comedy/JDOR/COME-JDOR-101-EP.clip01.wmv: event not found

```

I'm fairly newbish and I can't seem to figure out what it doesn't like or how to fix it.

Any insight would be appreciated muchly!

---

### Post by 21jeremy21 on 2009-07-05
So I've done some more digging and answered my own question.

I found out that
> When you type a word preceeded by an "!", bash thinks you want to recall a previous command or "event". The message indicates no matching event was found in your recent command history. You can suppress the special meaning of ! by quoting it, for example: \!


[I found this here]("http://zotline.com/shownote.zot/NoteNum/3801.html")

Maybe thats basic or common knowledge, but it's news to me

Now to figure out the next error message :guitar:

---

