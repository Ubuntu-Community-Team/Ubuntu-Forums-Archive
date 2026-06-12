---
title: "convert a png into jpg"
date: 2008-06-11
forum: Multimedia Software
---

### Post by fidaros on 2008-06-11
Well, 

I tried to convert some .png images to .jpg but, unfortunately I was not
able neither to use the command nor to install it with the commands:

[COLOR="RoyalBlue"]sudo apt-get install imagemagick[/COLOR]  and,
[COLOR="RoyalBlue"]sudo apt-get install graphicsmagick-imagemagick-compat[/COLOR]
both want a [sudo] password
:mad::mad::mad::mad::mad:

I want some help there,
Thanks.

---

### Post by KingTermite on 2008-06-11
Just google search...tons of examples there.
[http://www.google.com/search?source=ig&hl=en&rlz=&=&q=linux+imagemagick+convert&btnG=Google+Search](http://www.google.com/search?source=ig&hl=en&rlz=&=&q=linux+imagemagick+convert&btnG=Google+Search)

---

### Post by fidaros on 2008-06-11
And what is that sudo password?

---

### Post by wolfen69 on 2008-06-11
GIMP will convert for you.

---

### Post by TenPlus1 on 2008-06-11
The standard image viewer will let you Save As JPG already...

---

### Post by bigken on 2008-06-11
just use gimp

the sudo password is your password

---

### Post by dschaller on 2008-06-11
> **fidaros said:**
> And what is that sudo password?

If you have a basic installation with a single user, it's probably the password you use when you first log into your system.

Once you have imagemagick installed, it's easy to convert from one format to another. From the command line, just do:

```
convert filename.png filename.jpg
```

---

