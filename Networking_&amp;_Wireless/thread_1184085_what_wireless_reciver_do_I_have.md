---
title: "what wireless reciver do I have?"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by chippanfat on 2009-06-10
[SIZE=4]I'm currently looking into learning how to use "Aircrack -ng"

But I'm starting right at the beginning and I need to find out what wireless receiver i have.

where would I go in Ubuntu to to find out what hardware I have?

I have an advent 8117. If anyone has the same laptop can you please help :)

Cheers.
[/SIZE]

---

### Post by chili555 on 2009-06-10
Open a terminal (Applications -> Accessories -> Terminal, if you are running Gnome) and type:```
sudo lshw -[SIZE="4"]C[/SIZE] network
```You will be shown the details of both your ethernet and wireless cards. It ought to be apparent which card is wireless, but if you get stuck, please post back.

---

