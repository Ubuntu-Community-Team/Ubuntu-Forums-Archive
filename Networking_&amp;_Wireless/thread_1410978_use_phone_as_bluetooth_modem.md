---
title: "use phone as bluetooth modem"
date: 2010-02-19
forum: Networking &amp; Wireless
---

### Post by Tenn lynx on 2010-02-19
Hi

I want to connect my Nokia e63 to my laptop via bluetooth, and I want to use it to access the internet.

I did this before for a friend, but he has a Nokia prism 7500, and when I paired the phone via bluetooth I was offered the option of using the phone to access the internet...

With my nokia e63 now, I'm not given the option of using my phone as a modem. I tried several other phones with the same result. It just says the pairing was successful.

Is there a package I'm missing or is the phone not fully supported maybe?

thanks
tenn

---

### Post by Tenn lynx on 2010-02-20
anyone?

---

### Post by puppywhacker on 2010-02-20
The way this works (regardless which buttons you'll have to click for it)
1. Pair your phone and the computer
2. Use the serial/rfcomm connection which is a simulated com-port
3. Your phone will have the internet profiles setup, you will dial the virtual number *99# (which dials the default profile)

you do that with for instance wvdial

---

