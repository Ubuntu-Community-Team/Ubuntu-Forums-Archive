---
title: "Totem can't play DVD"
date: 2009-04-24
forum: Multimedia Software
---

### Post by ufarmer on 2009-04-24
When I try to play a commercial DVD using Totem I get the following message:

> Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc.

However there is no mention of exactly which plugins are needed.  Googling the message has turned up lots of threads but no solutions.  I have libdvdcss2 installed.  VLC works just fine but has developed some annoying behaviour since the upgrade to 9.04 so I am trying out Totem for the first time.

Any advice is appreciated.

---

### Post by mdpalow on 2009-04-29
See link in my signature below for help.

mdpalow

---

### Post by ufarmer on 2009-04-29
So the "Play DVD Movies On Your Computer" option in QuickStart applies to Totem?

---

### Post by tlabus on 2009-05-01
I found this on another forum and it worked for me.

sudo apt-get install ubuntu-restricted-extras debhelper fakeroot build-essential

---

