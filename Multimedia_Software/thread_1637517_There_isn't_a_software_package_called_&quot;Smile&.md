---
title: "There isn't a software package called &quot;Smile&quot; in your current software resources"
date: 2010-12-04
forum: Multimedia Software
---

### Post by toolmania1 on 2010-12-04
I tried to install the package "Smile" from getdeb.  I used the link:

[http://www.getdeb.net/app/Smile](http://www.getdeb.net/app/Smile)

I got this error in the Ubuntu Software Center when it opened to try and automatically load the "Smile" package.

There isn't a software package called "Smile" in your current software resources

---

### Post by lykeion on 2010-12-04
You can follow these instructions to install applications from GetDeb (assuming you are using Ubuntu Lucid):
[http://www.getdeb.net/updates/Ubuntu/10.04#how_to_install](http://www.getdeb.net/updates/Ubuntu/10.04#how_to_install)

---

### Post by toolmania1 on 2010-12-04
I am using Ubuntu Meerkat 10.10 I think.

So I clicked on the install get-deb.  I was prompted to install which I did using the Ubuntu Software Center.  Then, I clicked on the Smile Install again and another tab popped up ( I have FIrefox configured to open a new window in a new tab ).

---

### Post by mc4man on 2010-12-04
Well you'd simply switch, as in this page.
[http://www.getdeb.net/updates/Ubuntu/10.10/](http://www.getdeb.net/updates/Ubuntu/10.10/)

I haven't used getdeb in a few years, it appears they now require you to add their repo .
also it seems they've made their sources, builds and changes unavailable, not really ideal for a repo.
I'd suggest getting what you want from them and then disabling their repo in your software sources.

---

### Post by Chronon on 2010-12-05
> **mc4man said:**
> 
also it seems they've made their sources, builds and changes unavailable, not really ideal for a repo.

Isn't it necessary to provide access to the source?

---

### Post by mc4man on 2010-12-05
I guess they still do in a roundabout way  - there is a little changes tab and if you backtrack a bit you can find the packages, diff's, source, ect.
They used to be more upfront.

[http://archive.getdeb.net/ubuntu/rpool/apps/](http://archive.getdeb.net/ubuntu/rpool/apps/)

---

### Post by lykeion on 2010-12-05
Personally I wouldn't add GetDeb to the repositories, and the link to the archive of deb packages of GetDeb which mc4man provided, gives a simple solution for the OP:
* Browse to [http://archive.getdeb.net/ubuntu/rpool/apps/s/smile/](http://archive.getdeb.net/ubuntu/rpool/apps/s/smile/)
* Download the smile deb-file for your system (select i386 if you're uncertain)
* Doubleclick the downloaded deb-file to install

---

### Post by toolmania1 on 2010-12-06
Mc4man and lykeion,

Thanks!  I used the link lykeion provided and I was able to download the program.

---

