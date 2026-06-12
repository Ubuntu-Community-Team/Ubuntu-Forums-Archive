---
title: "japanese text support"
date: 2008-03-02
forum: Multimedia &amp; Video
---

### Post by AJB2K3 on 2008-03-02
Im trying to write some Japanese links but the text is coming out a gibberish on my site but displayed correctly on other sites.

---

### Post by scottro on 2008-03-02
Could you be a bit more specific?  Do you mean you can view Japanese text on other sites (created by that site) but not text that you create?

It sounds like an encoding issue.  There are various encodings--these days, UTF-8 is probably the most common, but Microsoft still uses Shift-JIS.  The old default in Unix was EUC.  

When trying to view it, have you tried going to View=>Encoding (or character encoding or something similar, depending upon your browser) and trying the various options for Japanese text?

Unfortunately, it's not yet standardized--UTF-8 seems to be the direction it's taking--I believe that MS is also planning to make that their standard and I know that Mac already sets it as default encoding on Japanese input.

---

