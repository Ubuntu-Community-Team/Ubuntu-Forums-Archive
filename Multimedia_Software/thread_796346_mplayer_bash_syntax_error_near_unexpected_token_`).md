---
title: "mplayer bash: syntax error near unexpected token `)'"
date: 2008-05-16
forum: Multimedia Software
---

### Post by yopnono on 2008-05-16
Hi. If using Mplayer or Totem plugins in Firefox it will not play the content. 

So can someone please tell me why I get this when using Mplayer or totem gstream in the shell. But if using the xine-plugin in Firefox it works just fine

```
mplayer http://anytime.tv4.se/webtv/metafile.asx?MSG=tT)2GSWzqR7xXzL0x0IA3nDtDrQGzMEeQhe502esVg23AqX2yO7Aofmj(mgix1c9C9x8VdJRjpL2dxMTTofSwvAe)EgfPYY(ZNcQLGFRuFk! bash: syntax error near unexpected token `)'
```

---

### Post by squaregoldfish on 2008-05-16
Try putting the URL in quotes, or escaping the ) i.e. ) becomes \)

It's all to do with the shell interpreting the ) characters before it gets anywhere near mplayer.

Steve.

---

### Post by yopnono on 2008-05-16
> **squaregoldfish said:**
> Try putting the URL in quotes, or escaping the ) i.e. ) becomes \)

It's all to do with the shell interpreting the ) characters before it gets anywhere near mplayer.

Steve.

Have tried the put it in "" but noting. Anyhow the player should be able to read and understand the URI like xine or any windows player do. or is this some non standard URI format?

---

### Post by squaregoldfish on 2008-05-16
Well, I've tried accessing that URI in mplayer, xine and VLC, and none of them want to play it.

Escaping the ( and ) characters managed to get the URI into mplayer, but that didn't like it either.

I'm a bit stumped now. Do you have the URL of the web page where you found this video so I can take a look at it from there?

---

### Post by Gunman1982 on 2008-05-16
If I try that link I get a "404 page not found" error 
and use ' ' instead of " "

---

### Post by yopnono on 2008-05-17
> **squaregoldfish said:**
> Well, I've tried accessing that URI in mplayer, xine and VLC, and none of them want to play it.

Escaping the ( and ) characters managed to get the URI into mplayer, but that didn't like it either.

I'm a bit stumped now. Do you have the URL of the web page where you found this video so I can take a look at it from there?

[http://anytime.tv4.se/webtv/?treeId=90512](http://anytime.tv4.se/webtv/?treeId=90512) just pick any of the episodes

[http://anytime.tv4.se/webtv/?treeId=901](http://anytime.tv4.se/webtv/?treeId=901)

---

### Post by squaregoldfish on 2008-05-17
Unfortunately, "Due to rights limitations, this video cant be offered in the country or region where you are located."

Looks like I can't help any further :(

---

### Post by yopnono on 2008-05-17
> **squaregoldfish said:**
> Unfortunately, "Due to rights limitations, this video cant be offered in the country or region where you are located."

Looks like I can't help any further :(

well thanks anyway.

---

