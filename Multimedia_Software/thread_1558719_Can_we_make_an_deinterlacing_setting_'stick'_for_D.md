---
title: "Can we make an deinterlacing setting 'stick' for DVDs?"
date: 2010-08-22
forum: Multimedia Software
---

### Post by tpprynn on 2010-08-22
I can see there is an option to save a deinterlacing choice in VLC but am assuming from the wording of something I read that this pertains to streamed video or files on the hard drive maybe.  When I watch a film, on an official shop-bought DVD, to get rid of extremely slight but annoying horizontal lines I click Video > Deinterlace > X.  (In fact X may have initially been a random choice from that menu but it seems to work.)

I have to do this each time I watch a film though and wondered if something can be altered so that the X choice stays on.

Latest Synaptic version.

Thanks.

---

### Post by mc4man on 2010-08-22
To set a 'global' option in vlc go Tools -> preferences -> all 
For deinterlacing first go to Video -> filters and enable deinterlacing 

To choose a specific mode continue to -  expand the filters drop down -> Deinterlace and choose a mode

(remember to click 'save'

Edit; this  however will enable deinterlacing for all video, to only use on specific videos(dvd's ?), then it may be better to create an additional 'vlc player' by creating a new .desktop with a slightly different name ('vlc dvd player' for example) and a custom launch command.
Not to hard to do - ask

---

### Post by tpprynn on 2010-08-23
Superb - that worked.  That also put to an end one of my Linux reservations going back two years, that DVD playback hadn't been as good as with Windows and paid for codecs.  If only I'd seen these options then.

Thanks.

---

