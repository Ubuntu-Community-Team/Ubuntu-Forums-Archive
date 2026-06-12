---
title: "Nothing works (ATi Radeon 9250)"
date: 2006-08-13
forum: Multimedia &amp; Video
---

### Post by Martin A on 2006-08-13
Hi,

I've searched the forums hi and low for a solution, tried EVERY howto I could find and still I have no 3D acceleration ](*,) ](*,) ](*,) . I have an ATi RADEON 9250, and I'm running Ubuntu 6.06. Can someone point me to a howto that works? I will be eternally grateful, I need 3D acceleration for my work and I really don't want to use Windows....

Thanks in Advance,

Martin

---

### Post by Greycloak on 2006-08-13
I used the following and it worked fine for me:

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

Use method 2.

---

### Post by Martin A on 2006-08-13
I've tried that howto 40-50 times, reinstalling Ubuntu on several occasions. It doesn't work.

---

### Post by tseliot on 2006-08-13
did you try this one too?
[http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910)

---

### Post by Martin A on 2006-08-13
Yeah, I tried all the ones mentioned those "Sticky" ATi threads in this forum. I haven't heard of a single user that have gotten this card working in Ubuntu, which isn't exactly encouraging either....

I do appreciate the replies though :) 

Thanks,

Martin

---

### Post by Darth Tux on 2006-08-26
I got my 9250 working with the latest 8.28.8 drivers. In earlier releases I had to used this [guide]("http://www.ubuntuforums.org/showpost.php?p=1108696&postcount=26"). 3D acceleration worked right off the bat with the new drivers and I added [ Option "AGPv3Mask" "0x00000002" ] to my xorg.conf under the "Device" section.I added that to stop random freezing and complete lock-ups I was experiencing in games. Hope this helps.

---

