---
title: "Wheres Multiverse and Universe"
date: 2006-06-04
forum: Multimedia &amp; Video
---

### Post by Michiba on 2006-06-04
Hi Guys,

I know all you guys are run off your feet with dapper problems and I don't mean to make your life harder but...... When I used Breezy all multimedia woes went away when I tagged Universe and Multiverse. I can't find it in synaptic in Dapper. 

Ok guys reply when you have a spare thirty seconds.

Apart from that dapper went pretty much without a hitch.

Michiba

---

### Post by s6dalane on 2006-06-04
## Uncomment the following two lines to add software from the 'universe'
## repository.

Find the following paragraph in your sources.list file and add 'multiverse' in both repository lines.
For example, mine looks like this:
> deb [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://ee.archive.ubuntu.com/ubuntu/](http://ee.archive.ubuntu.com/ubuntu/) dapper universe multiverse

---

### Post by Michiba on 2006-06-04
s6dalene,

Bingo, Many thanks

Michiba

---

