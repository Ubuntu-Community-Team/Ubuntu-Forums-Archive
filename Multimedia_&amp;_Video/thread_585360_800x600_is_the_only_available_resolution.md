---
title: "800x600 is the only available resolution"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by chillpenguin on 2007-10-21
**Edit:** removed this unhelpful message.

---

### Post by prshah on 2007-10-23
Try:

sudo dpkg-reconfigure xserver-xorg

in a Terminal. You can then manually select the resolutions you want. Maybe you should also give some more information, such as Graphics card, Monitor, etc. 

Also if not solved, maybe you could post your /etc/X11/xorg.conf file here.

Cheers,
PRS

---

### Post by Edoaigor on 2008-03-11
Hmm maybe agent Smith in the Matrix was right after all... I must be the wors virus I have ever met. I tried typing the sudo dpkg-reconfigure xserver-xorg command but i must have given some wrong answer in the multiple choice questionnaire I had to face... for some questions i really had not the faintest clue. At one point I tried pressing the good old Esc key to tell the thing I was joking and to go back to the good old values but the thing kept plowing deeper into configuration...
result, I get a funny screen during startup saying my xserver is fried and has wrong values and... at this point I should be able, according to mr command line, to get myself out of this.. hmm think I-ll reinstall the whole thing over
:(
may this serve me as a lesson...
by the way is there an interesting book about ubuntu linux someone could suggest I read.. i saw the classic Dummy series one and others but don t know where to start from.
thanks for any suggestions ... on both items

---

