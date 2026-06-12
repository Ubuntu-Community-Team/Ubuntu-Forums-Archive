---
title: "Midori Browser"
date: 2014-12-30
forum: Multimedia Software
---

### Post by Stob on 2014-12-30
I have used Firefox for years. However, I see a browser offered Midori with Ubuntu. How does it compare to FF and is it secure to use? Does it have an Ad Blocker feature?

I don't do gaming,just general web surfing.

---

### Post by Yellow Pasque on 2014-12-30
The version found in the default Debian/Ubuntu repos is somewhat old. You probably want to use Midori's PPA: [https://launchpad.net/~midori/+archive/ubuntu/ppa](https://launchpad.net/~midori/+archive/ubuntu/ppa)
Yes, it has an Ad blocker. I don't know about security, but it's based on Webkit, so you may want to look at how secure that is.
The only thing I don't like about it is that you're forced to install zeitgeist unless you build it yourself or find a pcakge where that's been removed.

---

### Post by Stob on 2014-12-30
What is zeitgeist?

---

### Post by Yellow Pasque on 2014-12-30
Google is your friend.
[http://en.wikipedia.org/wiki/Zeitgeist_%28free_software%29](http://en.wikipedia.org/wiki/Zeitgeist_%28free_software%29)

---

### Post by Holger_Gehrke on 2014-12-30
> **Stob said:**
> What is zeitgeist?

A central storage backend for all kinds history data - used files, visited urls etc. Instead of each program keeping it's own history, you have one history for everything, which can make working with the same data in several programs quicker. Example: You draw a picture in Inkscape, export it, work on it in gimp and import it into LibreOffice. At the second and third step you wouldn't have to browse through the file system, you could just go to "recently used files" and get the first item. 

A nice idea with some problems in implementation. There are some problems with privacy since the tools to edit or selectively erase history are not quite there yet. Also it's kind of a tempting target for people trying to built profiles.

---

### Post by Stob on 2014-12-30
Never mind then, I don't want my history saved. Sounds like a "cloud". Nothing secure about a cloud.

---

### Post by vasa1 on 2014-12-30
> **Temüjin said:**
> ...
The only thing I don't like about it is that you're forced to install zeitgeist ...
Wow. The (old) one in the software center doesn't list any zeitgeist-like dependency. But [this page]("http://www.twotoasts.de/index.php/midori/") lists it as optional.

---

### Post by Yellow Pasque on 2014-12-30
Upon closer investigation, the Midori PPA explicitly disables zeitgeist support, so feel free to try Midori without worrying about it. Sorry for false alarm.

---

### Post by kerry_s on 2014-12-30
i actually like midori, don't have any other browser installed. i use the 1 from the repo cause it works the best with flash. don't use the adblocker cause it messes up forum formats, but it is a very good adblocker just no whitelist. it does have privacy settings.

---

