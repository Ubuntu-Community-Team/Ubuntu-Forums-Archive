---
title: "how do I share data in ubuntu ?"
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by hondacodonbk on 2009-02-25
hey,I have a issue about sharing data between ubuntu and others ( use same ubuntu or other OS as window).how do I can share my data to them ?????
EX: if you use window and other use the same window,when you want to share your data to him.you choose property -> share,and he will go to command (run) and press \\yourPCname and he can get your data.So,if you want to do that in ubuntu,how do you do ???

---

### Post by terazen on 2009-02-25
The quickest thing I can think of would be to setup an ftp server with something like vsftp and use firefox.  You could create an account allowed to ftp and put files/links to files in the ftp folder.  Apache could do the same thing... Not aware of a quick setup to do like in windows.

---

### Post by terazen on 2009-02-25
Also, there is samba but I haven't tried it myself because it seemed more complicated to me at the time I was setting up sharing.

This video does made it look easy though so maybe worth a look! [http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)

---

### Post by superprash2003 on 2009-02-25
samba is the best way to go [http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html](http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html)

---

### Post by tlois on 2009-02-25
What about right clicking on the item and set sharing options?

---

### Post by dannyboy79 on 2009-02-25
first are we talking about in the same network or over the internet? If it's in the same network (household) then samba is the way to go for sure. Yes, I can be a little difficult to set it up using security = user but it's worth it. Otherwise just use security = share. You can find samba setup all over these forums or within goggle. Goodluck.

---

### Post by hondacodonbk on 2009-02-26
yeah,I did ^_^
I use samba and can share data with other Window PC in my room
thank for help

---

