---
title: "Dial-up on 9.04...Help"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by Travis W Hillis on 2009-05-09
Well, I just got the latest Ubuntu version and love it. However, I can't seem to be able to set up a dial-up connection. I've Googled my fingers off, found several tutorials but none were written with 9.04 in mind. :( Could someone tell me how to set up a dial up connection?


BTW: If I have to download anything, I'll have to use my connection in Vista(which is also on my HD thanks to dual-booting) and save the file(s) to a shared folder. Hope this wont't  be a problem.

---

### Post by Travis W Hillis on 2009-05-09
One more thing, I was reading about some software that is suposed to make dial-up work and it said it had to be compiled. So I started to try to find out how to get a compiler...the docs said I need to be connected to get it:confused:.

---

### Post by dLeon on 2009-05-09
Do you actually want to compile a dial-up program or only want to make your dial-up connection active?

---

### Post by Travis W Hillis on 2009-05-10
Just need to make mine active. I know the username, pass, and dial-up number, I just don't know how to set it up. Thanks a lot for replying btw. I feel like a total noob lol.

---

### Post by Travis W Hillis on 2009-05-10
Bump

---

### Post by lswb on 2009-05-10
If your modem is recognized and properly working try the pppconfig program from a terminal:

sudo pppconfig

Enter the requested information, and save. Then connect by using the command "pon ISPNAME" and disconnect with "poff"

See man pppconfig for more info.

There is also a gnome-ppp gui program or kppp for KDE.

---

### Post by Travis W Hillis on 2009-05-10
Thanks! I heard about connecting with the terminal, I just didn't know it could be used with 9.04. I'll try it. :)

---

### Post by Travis W Hillis on 2009-05-11
One question, it(the pppconfig thing) asks for the dns address. I don't know the dns address. How can I find out?

---

### Post by lswb on 2009-05-11
Select the choice for dynamic DNS, the DNS address will be assigned by your ISP upon connection.

---

### Post by Travis W Hillis on 2009-05-11
Thanks! :)

---

