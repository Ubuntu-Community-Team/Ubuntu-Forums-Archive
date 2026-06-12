---
title: "Flash support in Linux - noob alert  please help !!!"
date: 2006-10-16
forum: Multimedia &amp; Video
---

### Post by Powerwing on 2006-10-16
Okay, I've read lots of stuff on Flash support (and general driver support) in Ubuntu Linux. From what I understand, Linux runs best on a combination of Intel and nVidia (if I'm talking nonsense just stop me).
Suppose I get a laptop from, say HP or Acer with an Intel Core(2) Duo and an nVidia card, will everything run ?  I suppose built-in webcams and stuff like that will require some tweaking, but the main things will run, right ? And more importantly, will I be able to view every web page that uses Flash, like for example You Tube, Disney ... ? :-k

---

### Post by epennings on 2006-10-16
Flash sould work fine, including YouTube.
However, the latest version of Flash for Linux is 7. 
Some flash movies require Flash 9, which is only possible using wine

For a guide on howto install flash and make it work for YouTube go [[COLOR="RoyalBlue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=275947") (shameless self-promotion :p )

For a guide on howto install Internet Explorer with Flash 9 go [[COLOR="RoyalBlue"]here[/COLOR]]("http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu")

---

### Post by TheWizzard on 2006-10-16
> Some flash movies require Flash 9,
often they don't really require flash 9. it's sufficient to let the website think you use flash 9 :mrgreen: 
try the following: 


Open the file ~/.mozilla/firefox/pluginreg.dat ( or ~/.mozilla/pluginreg.dat )
change
Shockwave Flash 7.0 r63:$
to
Shockwave Flash 9.0 r63:$
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

