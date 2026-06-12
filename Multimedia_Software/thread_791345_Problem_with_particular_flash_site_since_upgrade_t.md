---
title: "Problem with particular flash site since upgrade to 8.04"
date: 2008-05-12
forum: Multimedia Software
---

### Post by potatan on 2008-05-12
Hi,

As a student of English and Linguistics, I regularly use the following site in order to check the sounds of the IPA fonts:

[http://www.yorku.ca/earmstro/ipa/consonants.html](http://www.yorku.ca/earmstro/ipa/consonants.html)

What is supposed to happen is that when you click on a symbol you should hear a short sound sample of the symbol you clicked on, in context.

This no longer happens since I switched to Hardy Heron, and I'm not entirely sure why.  Anyone have any ideas?

I'm using Firefox with the following plugin:
Shockwave Flash

    File name: libswfdecmozilla.so
    Shockwave Flash 9.0 r100

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Adobe Flash movie 	swf 	Yes
application/futuresplash 	FutureSplash movie 	spl 	Yes

I have tried using Opera, but cannot even click to activate the control.

Thanks in advance

(oh, and P.S. I have an exam tomorrow!)

---

### Post by gandaran on 2008-05-12
I tried that site and it works all-right,I believe you have the wrong flash installed.
remove swfdec or even gnash if it's installed, and just install the flashplugin-nonfree (adobe flash) package.

---

### Post by xc3RnbFO8P on 2008-05-12
> **potatan said:**
> Hi,

As a student of English and Linguistics, I regularly use the following site in order to check the sounds of the IPA fonts:

[http://www.yorku.ca/earmstro/ipa/consonants.html](http://www.yorku.ca/earmstro/ipa/consonants.html)

What is supposed to happen is that when you click on a symbol you should hear a short sound sample of the symbol you clicked on, in context.

This no longer happens since I switched to Hardy Heron, and I'm not entirely sure why.  Anyone have any ideas?

I'm using Firefox with the following plugin:
Shockwave Flash

    File name: libswfdecmozilla.so
    Shockwave Flash 9.0 r100

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Adobe Flash movie 	swf 	Yes
application/futuresplash 	FutureSplash movie 	spl 	Yes

I have tried using Opera, but cannot even click to activate the control.

Thanks in advance

(oh, and P.S. I have an exam tomorrow!)

I got it working in FF3b and Opera.
I don't have  **libswfdecmozilla.so**
and I got Shockwave Flash 9.0 r124

You could try to rename libswfdecmozilla.so to **libswfdecmozilla.so.backup**
restart FF and try play again.

Or install Opera 9.5 beta if you haven't.
[http://www.opera.com/download/index.dml?platform=linux&ver=9.50b]("http://www.opera.com/download/index.dml?platform=linux&ver=9.50b")

Last option is to try this:
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

