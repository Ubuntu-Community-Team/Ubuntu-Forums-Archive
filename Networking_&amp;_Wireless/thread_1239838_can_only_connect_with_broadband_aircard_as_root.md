---
title: "can only connect with broadband aircard as root"
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by larynx on 2009-08-14
I have a Sierra Wireless 595U Aircard from Sprint running on Ubuntu 9.04, I downloaded the [_PDF_]("http://www6.sprint.com/downloads/linux/pdfs/Sprint_Mobile_broadband_Setup_Guide_for_Linux_1.4.pdf") file explaining how set it up in Linux. I followed it step by step but when I ran KPPP to try and connect it got stuck and in the login script debug window it said "starting pppd..." and just wouldn't continue, I tried launching it from a terminal and it displayed the error message "Couldn't find interface ppp0: No such device" in the terminal.

Finally I tried running KPPP as root and it managed to connect.

I just wanted to know if there is another way to get it to work besides running it as root as that just seems like a security problem.

---

