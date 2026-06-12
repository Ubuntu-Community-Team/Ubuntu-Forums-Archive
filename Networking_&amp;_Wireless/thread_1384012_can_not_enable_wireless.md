---
title: "can not enable wireless"
date: 2010-01-17
forum: Networking &amp; Wireless
---

### Post by erinmbates on 2010-01-17
ive been using ubuntu for about a month now and ive generally had no problems.

recently though, my wireless just stopped working.  the network manager in my panel no longer allows me to enable wireless.
the option to enable wireless is there, but it is grayed out and will not let me connect.

i reinstalled my wifi driver but it didnt change anything.

iwconfig shows that the card is working why is the network manager not?

---

### Post by iponeverything on 2010-01-17
Try booting from an earlier kernel in your grub menu.

---

### Post by erinmbates on 2010-01-17
why what does that do

---

### Post by bkratz on 2010-01-17
> **erinmbates said:**
> why what does that do

I believe he is thinking that some recent update may have broken your wireless connection and that rebooting to an older kernel might fix it. Of course if there was no update, no effect.

---

### Post by erinmbates on 2010-01-18
i did recently update actually.
sorry to ask but how exactly do i do that?
im new to ubuntu

---

### Post by Duncan7221 on 2010-01-18
i had a problem with my wireless as well. it was a proprietary drive. i finally got it working by connecting to the internet with a wire and enabling the wireless. it needed to download the driver from the internet, i guess. maybe you could give that a try if you can.

---

### Post by bkratz on 2010-01-18
> **erinmbates said:**
> i did recently update actually.
sorry to ask but how exactly do i do that?
im new to ubuntu

Well I think the post just above is probably the best direction to go; but, if you do want to try a previous kernel and you are before version 9.10 you would press esc during the grub message

In 9.10 I believe you have to use shift rather than esc. Either way you would select the older kernel (probably the second entry)

---

### Post by erinmbates on 2010-01-18
ive already been through finding the correct driver and its not like ive never used my wireless before....this has just recently stopped working.

---

