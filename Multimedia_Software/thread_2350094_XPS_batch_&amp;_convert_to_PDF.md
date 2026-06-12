---
title: "XPS batch &amp; convert to PDF"
date: 2017-01-21
forum: Multimedia Software
---

### Post by Chip88 on 2017-01-21
[COLOR=#000000][FONT=&amp][FONT=arial]Hi there,

I have some **XPS** files, which I used to convert to PDF via the console without any problems with *xpstopdf*. Since the update to Ubuntu 16.04 (Kernel version: 4.4.0-59-generic) there are some converting problemlos, so I tried **mupdf**. The results are much better.

But: Unfortunately, I can't batch XPS files. It doesn't work neither with *xpstopdf* nor with *mupdf* &#8594; *mutool draw -Fpdf*.
Normally, we put an asterisk, but both commands *mutool draw -Fpdf *.xps* or *xpstopdf *.xps* don't convert all the XPS files I have in a folder.

Does anyone have an idea, how I can batch several XPS-files at once?[/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][FONT=arial]Thank you in advance for your help!

Regards,
Chipy[/FONT][/FONT][/COLOR]

---

### Post by nothingspecial on 2017-01-21
does a for loop work?

```
for blah in *.xps; do mutool draw -Fpdf "$blah"; done
```

---

