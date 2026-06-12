---
title: "audacity"
date: 2007-06-12
forum: Multimedia &amp; Video
---

### Post by medhamsh on 2007-06-12
hi all,
i have a strange problem with audacity and xmms..
the 'File' menu bar never appears in the audacity. but if we click there some blank pop up menu comes...and so on..
similar tthe case with xmms..
one of my friend said that this is the issue with gkt compatability..
please help me in resolving the issue.. i will attach the screenshot of the audacity...

thanks in advance,
medhamsh..

---

### Post by flossgeek on 2007-06-12
I don't have a solution but that's strange, I just installed audacity on my machine on Feisty 7.04 and all was fine. However these may be of help:-

[https://bugs.launchpad.net/ubuntu/+source/gtk+1.2/+bug/62300](https://bugs.launchpad.net/ubuntu/+source/gtk+1.2/+bug/62300)

[https://launchpad.net/ubuntu/+source/gtk+1.2/+bug/65708](https://launchpad.net/ubuntu/+source/gtk+1.2/+bug/65708)

If you are new to Linux give a shout back and I'll try help you resolve the issue over instant message. 

Its possible it could have something to do with your Language Settings, probably a good place to start anyway! Go to System>Administration>Language Support and select "English(United Kingdom of Great Britain and Northern Ireland)". Then apply and close. Finally restart the x-server by simply holding **ctrl + alt + delete** which will bring you back to login prompt and try your audacity and XMMS again after logging in.

---

### Post by tgalati4 on 2007-06-12
Control-Alt-Backspace will usually reset the xserver.

---

### Post by medhamsh on 2007-06-13
hi flossgeek,
good to have your quick responce..
i could resolve it by selecting the language to uk..
great..
thanks a lot geek....:popcorn::popcorn::D:D:D:D

---

### Post by flossgeek on 2007-06-13
No problem ;)

---

### Post by rahimveron on 2007-08-01
> **flossgeek said:**
> I don't have a solution but that's strange, I just installed audacity on my machine on Feisty 7.04 and all was fine. However these may be of help:-

[https://bugs.launchpad.net/ubuntu/+source/gtk+1.2/+bug/62300](https://bugs.launchpad.net/ubuntu/+source/gtk+1.2/+bug/62300)

[https://launchpad.net/ubuntu/+source/gtk+1.2/+bug/65708](https://launchpad.net/ubuntu/+source/gtk+1.2/+bug/65708)

If you are new to Linux give a shout back and I'll try help you resolve the issue over instant message. 

Its possible it could have something to do with your Language Settings, probably a good place to start anyway! Go to System>Administration>Language Support and select "English(United Kingdom of Great Britain and Northern Ireland)". Then apply and close. Finally restart the x-server by simply holding **ctrl + alt + delete** which will bring you back to login prompt and try your audacity and XMMS again after logging in.
Thank you flossgeek. My language setting was set to English(India) & i cahanged it to Great Britain n Ireland and it works. AGain long live this amazing community. Amen

---

