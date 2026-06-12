---
title: "Totem player does not play video"
date: 2005-11-08
forum: Multimedia &amp; Video
---

### Post by kvalis on 2005-11-08
Installed Ubuntu a couple of days ago, I can see why it is popular.  However, playing video is not as straightforward as in Windows.  I tried downloading asf, vmw, mpg, but the player does not play any of them.  What do I have to do????

Sincerely
Tore Kvalheim
Refvik
Norway

---

### Post by nocturn on 2005-11-08
[QUOTE=kvalis]Installed Ubuntu a couple of days ago, I can see why it is popular.  However, playing video is not as straightforward as in Windows.  I tried downloading asf, vmw, mpg, but the player does not play any of them.  What do I have to do????

Sincerely
Tore Kvalheim
Refvik
Norway[/QUOTE]

Though not a full answer.  Those formats are proprietary, you will need to install the codecs to view them (win32codecs), this is documented in the Ubuntu guide.

Distributing these codecs with ubuntu would be illegal, therefore they are not installed by default (and are not in the official repositories).

---

### Post by linbetwin on 2005-11-08
[quote=nocturn]Though not a full answer. Those formats are proprietary, you will need to install the codecs to view them (win32codecs), this is documented in the Ubuntu guide.
 
Distributing these codecs with ubuntu would be illegal, therefore they are not installed by default (and are not in the official repositories).[/quote]
 
Illegal? You're making him think he's installing pirated software. I don't think it would be illegal, but rather noncompliant with the GPL.
 
For codecs check [https://wiki.ubuntu.com/UserDocumentation]("https://wiki.ubuntu.com/UserDocumentation")

---

### Post by markr on 2005-11-08
I think strictly speaking, in order to use the w32codecs you should (although it would be interesting to see in court) have a Windows license; this is usually not a problem as most machines come with Windows and thus the license.

---

### Post by frodon on 2005-11-08
**kvalis** you will solve a lot of your problems intalling the totem-xine package, you could install it really quickly using synaptic.
I give you other links for w32codecs (you will need w32codecs for .wma for example) : [http://www.ubuntuforums.org/showthread.php?t=81577&highlight=w32codecs](http://www.ubuntuforums.org/showthread.php?t=81577&highlight=w32codecs)
[http://www.ubuntuforums.org/showthread.php?t=75278&highlight=w32codecs](http://www.ubuntuforums.org/showthread.php?t=75278&highlight=w32codecs)
[http://www.ubuntuforums.org/showthread.php?t=79449&highlight=w32codecs](http://www.ubuntuforums.org/showthread.php?t=79449&highlight=w32codecs)

---

### Post by kvalis on 2005-11-10
Tried the suggestions you all contributed, but alas, no.

Get the following error:

Totem could not play 'fd://0'.
There were no decoders found to handle the stream, you might need to install the corresponding plugins.

Any suggestions would be welcome.  It is not really a problem for me if I can't watch film clips on my Linux PC, I have a PC with XP, and averything is a lot easier there.  But, if I am going to use Linux more than I do now, it would be nice to get this working.

---

