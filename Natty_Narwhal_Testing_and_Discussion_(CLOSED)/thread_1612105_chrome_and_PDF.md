---
title: "chrome and PDF"
date: 2010-11-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ronacc on 2010-11-02
Google chrome ships with a pdf viewer plugin ( you have to type about:plugins in the url bar and enable it ) that is very fast , much faster to load than evince .Why isn't that available in Chromium ?

---

### Post by cariboo on 2010-11-02
Personally with all the problems that Adobe has been having with flash and pdfs, I'd rather they stay as far as possible away from my web browser. [[IMG]http://imgur.com/cP311.png[/IMG]](http://imgur.com/cP311.png)

---

### Post by ronacc on 2010-11-02
while I keep flash switched off in my browser ,I make heavy use of PDF's in my business and it is convenient  to be able to view them directly without having to download and open them in a separate viewer . Google chrome ships with it disabled and you have to enable it , it isn't even an option in chromium .

---

### Post by Mr. Picklesworth on 2010-11-02
> **cariboo907 said:**
> Personally with all the problems that Adobe has been having with flash and pdfs, I'd rather they stay as far as possible away from my web browser. [[IMG]http://imgur.com/cP311.png[/IMG]](http://imgur.com/cP311.png)

The point is it isn't Adobe Reader's PDF plugin, hence the high performance. The PDF format *itself* is just fine.
They talk about it right here: [http://blog.chromium.org/2010/06/bringing-improved-pdf-support-to-google.html](http://blog.chromium.org/2010/06/bringing-improved-pdf-support-to-google.html) :)

As I understand it, the PDF plugin is proprietary for some reason, and therefore limited to Chrome. Hopefully they'll release the code at some point; Google's Chrome team usually seems to understand [&#8220;open source&#8221; is not a verb]("http://yergler.net/blog/2010/09/23/diaspora-community/"), so I'm a little surprised they haven't.

[SIZE="1"]Edit: I guess [this is why]("http://googlesystem.blogspot.com/2010/08/google-chromes-pdf-plugin-uses-foxit.html"). Oh well :([/SIZE]

---

### Post by ronacc on 2010-11-02
@ Mr. Picklesworth  thanks for the links .

---

### Post by VinDSL on 2010-11-02
> **cariboo907 said:**
> Personally with all the problems that Adobe has been having with flash and pdfs, I'd rather they stay as far as possible away from my web browser. [[IMG]http://imgur.com/cP311.png[/IMG]](http://imgur.com/cP311.png)No joke!

SOURCE:  [Adobe's Updated Reader: Thwarting or Tempting Hackers?]("http://www.pcworld.com/article/209413/adobes_updated_reader_thwarting_or_tempting_hackers.html")

> Here's a distinction no software company craves: **For two quarters running, Adobe's popular Acrobat and Reader software have been the favorite target of hackers around the globe**.

According to Symantec's quarterly threat assessment, attacks related to PDF usage accounted for [COLOR="Red"]36 percent[/COLOR] of malicious activity in the most recent quarter and [COLOR="red"]57 percent[/COLOR] in the preceding three months.

Dittos for Flash, Shockwave, and Java (Oracle)...

---

### Post by cariboo on 2010-11-02
I know the vulnerability is in the Adobe reader, but I've never liked opening pdfs in a browser, call it a personal quirk, this is just another excuse for not doing it.

---

### Post by muze4life on 2010-11-03
One must also remember that Google being a big company is involved in the big "geopolitical chess game" for market dominance, thus it can well be not primarily because that will make users more happy, but mostly because Google (under the hood) (could well have) reached a deal with Adobe, there are many reasons for that, for instance Adobe agreed to support WebM which pretty much guarantees that WebM ( VP8 ) will be a success, this is very important for Google, and Google in turn did a favour to Adobe - by bundling their software into Chrome - which is important for Adobe, of course none of them will tell you that in the face because of the rules of the game, so of course anyone can call me a naive conspiracy theorist or so, I don't mind. That means that Chromium has a choice (whether to include the pdf reader etc) and Chrome doesn't unless the rules of the possible agreement are changed.

---

### Post by chrisccoulson on 2010-11-03
> **ronacc said:**
> Google chrome ships with a pdf viewer plugin ( you have to type about:plugins in the url bar and enable it ) that is very fast , much faster to load than evince .Why isn't that available in Chromium ?

Chromium is all the free bits of Chrome. I guess that the PDF viewer plugin is non-free

---

### Post by ronacc on 2010-11-03
couldn't that plugin go in one of the NON-FREE sections of the repos?

---

### Post by chrisccoulson on 2010-11-03
> **ronacc said:**
> couldn't that plugin go in one of the NON-FREE sections of the repos?

No, it's not shipped as a plugin, but appears to be part of Chrome.

---

