---
title: "New AT&amp;T high speed Internet connection not working"
date: 2012-09-03
forum: Networking &amp; Wireless
---

### Post by AmadeusOK on 2012-09-03
Hi All,

My computer is running on Ubuntu 12.04. Last year, I got AT&T U-verse Internet connection and it worked right away without any difficulties. 

I stopped using it for a few months and then I moved to another state just a few days ago. I had to changed to a DSL connection but now I cannot access Internet. 

Does anyone has any idea of how to fix that? Does it has to do with the modem (Motorola)? Do I neeed to install any driver?

---

### Post by AmadeusOK on 2012-09-03
Some screenshots

[ATTACH]223625[/ATTACH]

[ATTACH]223626[/ATTACH]

[ATTACH]223627[/ATTACH]

---

### Post by dandnsmith on 2012-09-04
Those screenshots are very useful, and remind me of a problem I had a week ago at a small charity site which I help support.
Their internet connection failed, I tried totally resetting the modem/router, and then I got stuck in the same manner. The ISP weren't too helpful (as they don't support the particular make modem/router), but gave me general details.
After staring at things, and then doing something else for a while, I suddenly realised that I'd never checked the VCI and VPI settings - it turned out these were wrong, and all was working as soon as corrected.

I hope this helps you.

While checking on VCI/VPI I found [this note on settings](http://www.speedguide.net/articles/adsl-vpi-vci-and-encapsulation-settings-2786) which might be of interest.

---

### Post by AmadeusOK on 2012-09-04
Hey dandnsmith, 

Thanks a lot for the tip. I've just found the VPI/VCI values for AT&T. I'll try them this afternoon when I get back home. 

AmadeusOK

---

### Post by AmadeusOK on 2012-09-05
The VPI/VCI values were correct. The problem must be somewhere else. Of course I can contact Technical Support but they don't know very much about Ubuntu. I don't even know what I'm looking for.

---

### Post by dandnsmith on 2012-09-06
Another thing to look at might be what has happened to your Ubuntu installation - have you done any updates in the interim? Normally, once you have a connection to work, the only thing to go wrong is changing the conditions - there have been a number of problems associated with internet connections and system updates.
BTW how does the PC connect to the modem?

---

