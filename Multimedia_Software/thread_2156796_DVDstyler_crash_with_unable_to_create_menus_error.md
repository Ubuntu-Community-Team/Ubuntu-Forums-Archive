---
title: "DVDstyler crash with unable to create menus error"
date: 2013-06-23
forum: Multimedia Software
---

### Post by Ghost_Mazal on 2013-06-23
Hi everyone , I use ubuntu 13.04 64bit with all updates uo to today.

I have used DVDstyler to create DVD's from mpg files for a number of years without problems.
But now , in 13.04 , it just crashes with the error "unable to create menus".

I have searched but couldn't find the solution.

Can anyone help please ?

Thank you

---

### Post by ka1ssr on 2013-09-30
I was having the same problem. Then I discovered that dvdstyler was complaining that it couldn't find an AC3 codec. Encoding the audio on MP2 got the program to work.

Are the AC3 codecs available? What's the package name?

I hope this helps.

Bill

---

### Post by Ghost_Mazal on 2013-10-01
Hmm , I went back to 12.04 where DvDstyler still works so can't check if mine is the same problem. But surely there must be a way to install the AC3 codec manually ?

---

### Post by Yellow Pasque on 2013-10-01
dvdstyler uses libavcodec for codec support, so it should be capable of encoding AC3.

I packaged dvdstyler 2.4.3 for Raring in my PPA: [https://launchpad.net/~dtl131/+archive/mediahacks](https://launchpad.net/~dtl131/+archive/mediahacks) Maybe that will fix the error.

---

