---
title: "Firefox hijacked (?!?)"
date: 2009-10-25
forum: Networking &amp; Wireless
---

### Post by solemnavalanche on 2009-10-25
Something very strange has happened to me. I searched for a website with google, clicked on the correct link, and was redirected to some other random site. I thought to myself -- weird -- this isn't supposed to happen to Ubuntu/Firefox. I investigated further and discovered something quite alarming. When I search for "foo" in google, enable the status bar, and hover over a link from the list, I see this url:

[http://en.wikipedia.com/wiki/Foobar](http://en.wikipedia.com/wiki/Foobar)

But when I right-click on the same link and select "Copy link location" the url that appears in the clipboard is as follows:

[http://www.google.com/url?sa=t&source=web&ct=res&cd=1&ved=0CAcQFjAA&url=http%3A%2F%2Fen.wikipedia.org%2Fwiki%2FFoobar&ei=t6_kSsSuH9yPtgezkpnGAQ&usg=AFQjCNH1J2pXAETcCKA7T6svhOKIRNyojg&sig2=SIXvKVXqiMwa7TbkpdnDYg](http://www.google.com/url?sa=t&source=web&ct=res&cd=1&ved=0CAcQFjAA&url=http%3A%2F%2Fen.wikipedia.org%2Fwiki%2FFoobar&ei=t6_kSsSuH9yPtgezkpnGAQ&usg=AFQjCNH1J2pXAETcCKA7T6svhOKIRNyojg&sig2=SIXvKVXqiMwa7TbkpdnDYg)

Thereafter, when I hover over said link, I see the long, weird URL in the status bar. 

This doesn't happen to my desktop -- the link is always the same. My desktop also runs Ubuntu, and is connected to the same router. So I can only conclude that my laptop must be the problem.

I find this very unsettling. Any suggestions?

---

### Post by hansdown on 2009-10-25
Hi solemnavalanche.

Both of those links lead to the same web page.

---

### Post by solemnavalanche on 2009-10-25
> **hansdown said:**
> Both of those links lead to the same web page.

I realize that, but if the url were legit, why would the status bar display a fake/wrong url? That's pretty clearly incorrect behavior, even if it seems innocuous. 

Additionally, the long url clearly isn't coming from Google, because on my desktop, the long url never appears. So where's it coming from?

And as I said, in other cases, I've been redirected to a random search site, so it doesn't *always* lead to the correct site.

Update: Ok, mystery solved. Sorry to annoy. See below.

[http://blog.teusink.net/2009/09/greasemonkey-script-to-change-google.html](http://blog.teusink.net/2009/09/greasemonkey-script-to-change-google.html)

---

