---
title: "Connects to wireless network, but won't load any pages"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by telegramsam17 on 2009-01-16
I've got a laptop with a Realtek RTL8187B wireless card that works fine on the windows partition, I've never had a problem connecting with it under vista.

So I installed intrepid ibex on a separate partition because I figured it would run a whole lot faster on my cheap underpowered laptop than vista which it does, significantly.

But there's one problem - it will connect to wireless networks but  it WILL NOT load pages. I've only ever managed to get it to access the internet ONCE when I was in a place where I was practically sitting on top of the router. Every other time even in spots where I have a seemingly strong connection, the browser will sit for about two minutes then give a page not found error. I tried pinging a few sites and nothing at all is getting through. 

In the FWIW department, I could not get this particular wireless card to work under any earlier versions of ubuntu even with ndiswrapper and a million different versions of the windows driver including a few modified ones, so it may just be a crappy one but I'd be thrilled if somebody knew how to make it work.

---

### Post by x22 on 2009-01-16
welcome to the forum

google "Realtek RTL8187B ubunbtu"

this one looked good:

[http://michael-peeters.blogspot.com/2008/12/getting-realtek-rtl8187b-wifi-stable.html](http://michael-peeters.blogspot.com/2008/12/getting-realtek-rtl8187b-wifi-stable.html)

---

### Post by julioipn on 2009-01-18
hi there, I had the same problem whit rtl8187b card, I could surf the web for about 20 minutes and then firefox wouldn't load any page, I couldn't even ping to my router, although network manager said I was connected and with a signal strength of about 90% most of the times,  what I got when I made a ping to my router was a lot of lost packages or even worse "destination host unreachable".  I tried a lot of things, except ndiswrapper, I didn't get so far, until I decided to send a e-mail to realtek because once I read that they send you a linux driver if you ask for it, and the next day I had the driver, I just compiled it:

make

and then installed:

sudo make install

after that I just reboot and everything works perfect since then, if you are interested this is the email address I wrote to: [email]wlanfae@realtek.com[/email]


PS: sorry about my english if there is anything wrong

---

