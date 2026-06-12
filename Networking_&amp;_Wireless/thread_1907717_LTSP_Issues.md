---
title: "LTSP Issues"
date: 2012-01-12
forum: Networking &amp; Wireless
---

### Post by slicknick5181 on 2012-01-12
Hello,

I have installed Edubuntu 11.10 and I currently can not get a client computer (directly connected) to boot using from the LTSP server.  I have 2 ethernet cards that I am using, 1 for internet and a seperate for thin clients, I can succesfully get online through firefox.  I did make sure during setup that I chose the correct ethernet card for the clients. When I look at the connection information I see the ip address for my internet card is correct and the ip address for the thin client card is static set.  When I plug the client in and start it the server shows connection has been made but the computer just trys to load from the server and fails.  I'm not sure what information would be helpful.  PLEASE HELP!!!!

---

### Post by CeltaWeb on 2012-06-05
Hi slicknick5181,

Did you have any luck getting this working? and can you recommend any guides on Edubuntu and thin clients.

Thanks

---

### Post by slicknick5181 on 2012-06-05
Hi [CeltaWeb]("http://ubuntuforums.org/member.php?u=1062861")

I did manage to finally get it working, my issues were in my dhcpd.conf file. But since then I have upgraded to Ubuntu 12.04 LTS (not edubuntu) and installed the ltsp server files and such, Much easier than edubuntu.

---

### Post by forkandles on 2012-12-25
CeltaWeb,

This is a very late reply to your question, but try looking here:

[http://www.linuxquestions.org/questions/blog/beachboy2-315980/ltsp-setting-up-from-scratch-35204/](http://www.linuxquestions.org/questions/blog/beachboy2-315980/ltsp-setting-up-from-scratch-35204/)

My advice would be to use Xubuntu 12.04.

---

