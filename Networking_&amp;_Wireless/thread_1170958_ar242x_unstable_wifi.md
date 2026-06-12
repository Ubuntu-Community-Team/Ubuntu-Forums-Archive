---
title: "ar242x unstable wifi"
date: 2009-05-26
forum: Networking &amp; Wireless
---

### Post by AVeryLongNickname on 2009-05-26
My wifi used to work great after I made a clean 9.04 install, but the last couple of days it's been unstable and a real pain in the a**..

On all the other computers in the house the wifi is stable, and in winXP64 its stable on my computer as well. It used to be stable in ubuntu 9.04 out-of-the-box, but now it runs perfectly one minute, and stops completely the next..

Any one else have any similar problems..? or ideas on how to fix it..?

I'm using the integrated Atheros AR242x(rev01) chip on my asus m3a32 motherboard.

but what really bugs me out is that I've got the same wifi chip in my laptop(acer aspire one) and on that I need the "alternate madwifi driver" to get a wifi connection, but on the m3a32 the alternate doesn't work at all=s

any help would be greatly appreciated :D

---

### Post by superprash2003 on 2009-05-27
by unstable , do you mean frequent disconnections/

---

### Post by AVeryLongNickname on 2009-05-27
it doesn't disconnect from the router, but one minute i have 2MB/s, the next minute it stops.. =s

---

### Post by rothi on 2009-05-27
I have got the same Problem here, with an Acer aspire 5610 Notebook.
It starts up, WLAN works fine for about a minute than it stops working and the NetWorkmanager does not seem to realize it.

I have to reconnect manualy to get it connected for an other minute.

thx rothi

---

### Post by AVeryLongNickname on 2009-05-28
that sounds pretty much the same as my problem.. what wifi chip is in your laptop..?
you can find it by typing lspci in terminal ;)

---

### Post by rothi on 2009-05-28
hmm,
I think this should be the right line:
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)


so it is: Intel PRO/Wireless 3945ABG
doesn't tell me anything :(

---

### Post by DVANDERM on 2009-05-31
Supposedly this will work for the ar242x cards: [http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html?showComment=1243736647145#c3701962582273958571](http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html?showComment=1243736647145#c3701962582273958571) 
in the instructions change intrepid to jaunty. However it is not working for me but then again my laptop has never wanted to cooperate. 

Good luck.

---

### Post by nmaster on 2009-06-25
when the signal "drops", do you still detect the network and then just have to click to pick up the network again?  i've been having similar intermittent problems, but when the wifi drops i can't even see the networks.

---

