---
title: "Vuze will not download files"
date: 2010-06-13
forum: Multimedia Software
---

### Post by WilhelmGGW on 2010-06-13
On Lucid with Sun Java installed (and open source cousins removed), I've installed Vuze and opened the incoming port in my firewall. All the configuration and tests run fine, except..
*The links on Getting Started page don't work.
*Search doesn't work.
*Even from the Vuze HD Network tab, I can click to download and nothing happens.

I have Vuze installed on a Windows machine wired to the same router and the application there worked fine, right from the start.  What more do I need to do to make it work on Lucid?

---

### Post by WilhelmGGW on 2010-06-13
I got this reply on the Vuze Community Forum:
> Those part of Vuze's functionality (Getting started, Search, HD network) use your internet browser components to display the results. In Windows PCs Vuze defaults to using IE, but I think that in Linux PCs it wants to use Mozilla firefox components.

You may have to teach it, where Mozilla Firefox/XULrunner can be found in your PC.
Check the Interface options --> Display subpage, where is an option for that.
[http://wiki.vuze.com/w/UG_Options#Display](http://wiki.vuze.com/w/UG_Options#Display)

The actual bittorent downloading should work normally, as it does not need browser components.

In order to try this out, I need to fill in this field:
"Specify XulRunner / Firefox path manually"

_Can someone tell me what is that path on Lucid?_ How should I fill in that required field?  I don't know how to discover this on my own.  Thanks.

---

### Post by WilhelmGGW on 2010-06-15
Or... Any fresh ideas about what I need to do to get Vuze set up? Thanks.

---

### Post by cchhrriiss121212 on 2010-06-15
Firefox path will be /usr/bin/firefox. You could of course use another torrent client like transmission.

---

### Post by WilhelmGGW on 2010-06-15
Thanks, but I tried this and it still didn't work. Maybe a fresh idea based only on my problem from the first post?  Thanks.

---

### Post by erlitzki on 2010-06-20
Maybe this will help: [http://www.detector-pro.com/2010/05/install-vuze-on-ubuntu-10-04.html](http://www.detector-pro.com/2010/05/install-vuze-on-ubuntu-10-04.html).

---

