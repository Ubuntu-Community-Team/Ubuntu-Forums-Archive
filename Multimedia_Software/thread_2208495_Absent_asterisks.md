---
title: "Absent asterisks"
date: 2014-02-28
forum: Multimedia Software
---

### Post by Langstracht on 2014-02-28
I have long used this command:

```
mkdir temp && for f in *.wav; do lame --vbr-new -V 3 "$f" ./temp/"${f%.wav}.mp3"; done
```

to convert .wav files to .mp3.

And successfully.  I believe.

Running the script results in the display of dynamic histograms - populated by asterisks.  But not always.  Sometimes there are percentage (%) symbols, ranging from one to perhaps a dozen, instead.

Does anyone know why that happens.  What that means. And what, if anything, should I be doing about it ...

TIA

---

### Post by Yellow Pasque on 2014-02-28
[http://forum.doom9.org/showthread.php?t=19499](http://forum.doom9.org/showthread.php?t=19499)

---

### Post by andrew.46 on 2014-04-09
It is the smallest and most pedantic point but I believe that the option *--vbr-new* is only required if you are using lame 3.97 and earlier (although not all earlier versions had access to this option). For lame 3.98 and above the 'new' vbr method is the default. Version can be seen:

```

andrew@ilium~$ **[COLOR="#FF0000"]lame --version | head -n 1[/COLOR]**
LAME 64bits version 3.99.5 (http://lame.sf.net)

```

Now if only there were an award on these Forums for being pedantically correct.....

---

### Post by Langstracht on 2014-04-12
So!  The correct command is:

```
mkdir temp && for f in *.wav; do lame -V 3 "$f" ./temp/"${f%.wav}.mp3"; done
```

??

that said, does that have anything to do with my '%' "problem"?

---

### Post by Yellow Pasque on 2014-04-12
Did you read the link in my previous post? I thought that answered it, which is why you gave no response..

---

### Post by andrew.46 on 2014-04-12
> **Langstracht said:**
> that said, does that have anything to do with my '%' "problem"?

Absolutely nothing :). I suspect that Temujin has given you the best answer for this issue...

---

### Post by Langstracht on 2014-04-13
Yes I read the link.

Not that I was any the wiser.

Not sure why the post was a 'personal guess' as opposed to a 'fact'.

And, my reading of it was that any one file would produce either '%' OR '*'.  That is not what I had.

Consequently I continue to wonder whether I have a problem or not.

---

### Post by andrew.46 on 2014-04-13
> **Langstracht said:**
> Not sure why the post was a 'personal guess' as opposed to a 'fact'.

Probably because the documentation is not all that comprehensive and sure knowledge of the fine details of mp3 encoding is not held by that many people. I could find no further mention of the use of these symbols via Google and a grep through the source was not helpful as the symbols are very common.

> Consequently I continue to wonder whether I have a problem or not.

I suspect not unless you have noticed anything particularly odd with the resulting file. As suggested in Temujin's link you could experiment a little with lame's* mode *setting but I suspect the existing sane defaults are your best friend with lame...

---

### Post by Langstracht on 2014-04-14
> Probably because the documentation is not all that comprehensive and sure knowledge of the fine details of mp3 encoding is not held by that many people. I could find no further mention of the use of these symbols via Google and a grep through the source was not helpful as the symbols are very common.

The paucity of information was what prompted me to post to the forum ...

If this %age thing IS causing a problem then I haven't identified it.  So I guess I'll just keep calm and carry on.  Regardless one might say.  And tag this thread solved.

Thanks for taking the time.

---

