---
title: "Another Digital Picture Frame - though with a twist"
date: 2010-07-17
forum: Multimedia Software
---

### Post by dushuahuja on 2010-07-17
I had an old Dell Inspiron 6400 lying around at home and decided to install Linux on it – had been dabbling with Linux for many years – but as it was never the only operating system on the computer – didn’t really get ahead with it. Also the plan was to make a multimedia center that I could control with my mobile. I had been doing this on my mac using Salling Clicker, but had no idea what I would do with the Dell – so, as is usual in such cases – Google came to my help.

The feature-set I had planned includes:

[LIST=1]
[*]Digital Photo Frame – slideshow starts as soon as the computer boots
[*]Media Centre (controlled via Bluetooth mobile):
[*]Control wi-fi router through Bluetooth mobile
[*]E-book server - Serve e-books to the nook over wi-fi
[*]Remote access via ssh and vnc
[*]Sync music, videos and photos from usb HDD (to-do)
[*]Send commands via email – e.g start slideshow, suspend, start/ stop torrents, etc. (to-do)
[*]Act as a wireless server for my macbook time machine (to-do)
[*]Display clock while in slideshow mode (to-do)
[/LIST]

Detailed instructions can be found at:
[http://controlyourproject.com/blog/2010/07/diy-digital-picture-frame/](http://controlyourproject.com/blog/2010/07/diy-digital-picture-frame/)

The one thing I'm unable to do is get a clock in the slideshow mode - preferably something discreet - semi-transparent digital clock. Any help would be appreciated.

Also comments and suggestions are welcome. :-)

---

### Post by dushuahuja on 2010-07-20
Found a way to get the clock - osd_clock

-- only problem - still can't figure out how to configure it to get a larger clock. Specifically the fully qualified font name - any ideas ?

---

### Post by dushuahuja on 2010-07-30
Figured it out - used xfontsel 
([http://manpages.ubuntu.com/manpages/intrepid/man1/xfontsel.1.html](http://manpages.ubuntu.com/manpages/intrepid/man1/xfontsel.1.html))

to get the fully qualified font name - now have my system running as I wanted it.

---

