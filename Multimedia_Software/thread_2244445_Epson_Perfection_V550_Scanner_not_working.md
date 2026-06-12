---
title: "Epson Perfection V550 Scanner not working"
date: 2014-09-16
forum: Multimedia Software
---

### Post by francis3 on 2014-09-16
I am at my wits end. I bought this scanner a few months ago and managed to make it work. And when I saw work, I had to click on Iscan for a few times before I actually get to scan. 

I recently moved to a new place and the scanner is not working again. 

I have all the linux drivers but I just cannot seem to get it to work again. 

Anyone has any ideas on how to get my Perfection V550 (not supported by SANE) to work?

---

### Post by T.J. on 2014-09-16
That would probably be because the Epson perfection series scanners are not supported in the open version of SANE, and require a binary driver from Epson in order to work at all.  I just searched for Windows and v550 and the Linux driver was also listed.  Their search sucks.  I can't guarantee it will work well, but at least there is a chance.

You may find something helpful here, although I can't be certain: [http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

If you had it working before in your current version of Ubuntu, try making sure that the scanner is hooked up exactly as you had it, much as you would with Windows.  Since the iscan driver is not opensource, the community cannot fix any bugs it has.  Hooking it up exactly as before may be your best chance for a sane recovery.

---

### Post by francis3 on 2014-10-06
Thanks T.J. I've tried everything and googled every possible solution and it still doesn't want to work with me. I really wish someone here will have an alternative.

---

