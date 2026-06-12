---
title: "How To: put mp3 files on your Sony Ericsson cellphone"
date: 2008-03-18
forum: Multimedia &amp; Video
---

### Post by equal on 2008-03-18
Hey everyone, it took me forever to figure this out. Turns out, the problem is NOT with Ubuntu (as usual) but with the phones themselves. They have trouble with something in the ID3v2.4 tags that they can't read. 

Here's my newest fix, which should work even on **Hardy Heron 8.04**

install kid3-qt. (or kid3 if you're a KDE user)
select the files you wish to convert by opening them (Ctrl-A to select all of them), then from the main menu select &#8216;Tools&#8217; -> &#8216;Convert ID3v2.4 to ID3v2.3&#8242;.

It's not a perfect fix, but ID3v2.3 has everything that'll actually show up on your Sony Walkman, so try that out. This should work on all the models, including W200i/W200c/W200a W610i/W610c W660i W580i W700i/W700c  W810i/W810c W880i/W888c  W300i/W300c W710i/W710c, and probably others as well!

---

### Post by jonvel on 2008-03-20
I would just like to say THANK YOU for posting this.  I've been toying around with trying to get lots of things working, ranging from eyeD3 (has the Ubuntu logo in synaptic package manager) to mp3info and none of them worked.  Sure, they'd claim to change the ID3 tag (and they appeared to), but my W580i phone was NOT able to read the tags properly (even when I "converted" them to v2.3 tags.

Anyway, EasyTag seems to have done the trick, so thanks a ton for that tip.

(Edit - I added a thanks to you for that one, by the way!)

---

### Post by equal on 2008-03-26
No problem at all. It took me an eternity to get it working too. I found it in some obscure forum somewhere, not even talking about Linux.

---

### Post by equal on 2008-03-30
Crap, the version of EasyTag in Hardy Heron doesn't have that option... Gonna have to figure this one out again.

---

### Post by equal on 2008-03-31
AHA! I've found something new! **Directions for Hardy Heron (8.04)**

install kid3-qt. (or kid3 if you're a KDE user)
select the files you wish to convert by opening them (Ctrl-A to select all of them), then from the main menu select &#8216;Tools&#8217; -> &#8216;Convert ID3v2.4 to ID3v2.3&#8242;.

TADA!!!

---

