---
title: "Highly reliable landline &gt;modem &gt; Ubuntu &gt; VOIP &gt;Android  phone switch"
date: 2012-07-17
forum: Networking &amp; Wireless
---

### Post by Kammerbulle on 2012-07-17
Hello, I wonder if there is an easy way to connect  an Ubuntu computer to the landline phone system (preferently with an old modem) and redirect incoming calls to an Android phone? I would prefer via Skype, but it doesent matter as long as an average grandpa can use it on his phone.

I have heard about Asterisk, how reliable is it? Do I need any special hardware to build my telephone switch or will it work with any modem as long as Ubuntu recognizes it? 

There will propably not be any outcalls from the system.

---

### Post by Cheesemill on 2012-07-17
I'm not sure about the Android side of things but you cant use modems with Asterisk.

You need to use an FXO card to interface the computer with an analogue telephone line.
Try searching e-bay for 'X100P' or 'Asterisk FXO' to give you an idea.

Asterisk is probably overkill for what you are trying to achieve, it's not very user friendly to set up and is designed more for businesses with 10s - 100s of phones who need some of the following features:
[http://www.asterisk.org/features](http://www.asterisk.org/features)

You're probably better of with one of the consumer VOIP solutions where you can purchase a landline number that is routed over the internet directly to an application on your smartphone, no need for a PBX system on your computer.

---

