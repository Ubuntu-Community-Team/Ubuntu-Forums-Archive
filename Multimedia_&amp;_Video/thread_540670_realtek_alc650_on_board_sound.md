---
title: "realtek alc650 on board sound"
date: 2007-09-01
forum: Multimedia &amp; Video
---

### Post by jimerickso on 2007-09-01
i am using an msi k7n2 motherboard with realtek alc650 on board sound with feisty. unfortunately ubuntu will not detect this chipset. does anyone have any suggestions for getting it detected. i can take it from there. thanks

---

### Post by Jest3r on 2007-09-01
> **jimerickso said:**
> i am using an msi k7n2 motherboard with realtek alc650 on board sound with feisty. unfortunately ubuntu will not detect this chipset. does anyone have any suggestions for getting it detected. i can take it from there. thanks

This worked for me.
[Download Realtek Driver's]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false")

Download..
"Others" 4.06a 2007/6/8 4570k

Install
$ bunzip2 realtek-linux-audiopack-4.06a.tar.bz2
$ tar -xf realtek-linux-audiopack-4.06a.tar
$ cd realtek-linux-audiopack-4.06a
# ./install

---

### Post by jimerickso on 2007-09-02
thank you for your suggestion i will give it a try.

---

