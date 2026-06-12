---
title: "Ebook Embedded in Flash"
date: 2012-02-06
forum: Multimedia Software
---

### Post by ultramilkman on 2012-02-06
Hello everyone, I have a ebook on a site that uses flash to display its contents. I had no idea when purchasing this ebook that it can be only used on my computer. I had wanted to use it on my iPad. Fortunately, the flash ebook has the ability to be printed. The catch is though, it can only print 20 page at once... I understand it is for anti piracy purposes, but it makes reading the portability of this book very low.

So now I am trying to extract the text or image from the ebook, or in someway emulate printing more than 20 pages so that I can save it as a pdf onto my computer.

I have read the thread here: [ebook flash]("http://ubuntuforums.org/showthread.php?t=1358644")
But the conclusion seems in conclusive.

I have done my own research in this, but now I seem stuck.
I have poked around wireshark, and I have noticed that the request for the next page would be something like:

[CENTER]GET /college/chemistry/chem3_ebook/pages/ch31_0800.swf HTTP/1.1 [/CENTER]

The packets that come in would be:
[CENTER]HTTP/1.1 200 OK  (application/x-shockwave-flash)[/CENTER]

But now I am stuck, because when I try to access the swf, it does not seem to display, as it seems to request the reader to decode its contents. I do not know how to simulate the reader, so I am really not sure what to do next.

---

