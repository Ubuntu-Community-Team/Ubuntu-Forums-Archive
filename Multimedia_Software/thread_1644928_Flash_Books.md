---
title: "Flash Books"
date: 2010-12-13
forum: Multimedia Software
---

### Post by zgembo on 2010-12-13
Hi, I have a question about flash books. 
Here is one example of that kind of books:

[http://www.page-flip.com/new-demos/03-kitchen-gorenje-2008/index.html]("http://www.page-flip.com/new-demos/03-kitchen-gorenje-2008/index.html")

This is really cool because it looks like real reading, you can flip pages and hear that flipping sound.

My question is if it is possible to save these books on hard drive for reading offline since I don't have wireless internet for my laptop.
Thanks in advance.

---

### Post by misskimberly on 2010-12-14
From what i see on the site it looks pretty simple to save offline.  However i notice that it dynamically downloads the pages when you go to flip them.    For example you can save the [swf file]("http://www.page-flip.com/new-demos/03-kitchen-gorenje-2008/FlippingBook.swf")

It seems the pages are numbered like this: [http://www.page-flip.com/new-demos/03-kitchen-gorenje-2008/pages/page-](http://www.page-flip.com/new-demos/03-kitchen-gorenje-2008/pages/page-)**001**.jpeg ... page-**002**.jpeg and so on

So you'd have to download each image page and place them in the same folder as the swf.
I'd say use something like wget but it does not know what the swf is doing internally (dloading image pages dynamically).

---

### Post by zgembo on 2010-12-14
Thanks, I will try.

---

