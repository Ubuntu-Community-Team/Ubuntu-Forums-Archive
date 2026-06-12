---
title: "Apache/PHP/Samba problems after update to 9.10"
date: 2010-01-25
forum: Networking &amp; Wireless
---

### Post by Firegun on 2010-01-25
Hello guys,

I have a local server running LAMP (Ubuntu 9.10, Apache 2.2.12, PHP 5.3.0), and I´ve used to mound a share from my personal PC (running windows 7 now, but also worked on winxp) to test my sites. Well, all that worked just perfect, I was able to manipulate large sites (with huge libraries, as ZF and so on) and to test then on the linux box (witch is most near from the production env I´m use).

After updating to ubuntu 9.10 I runned into lots of troubles with samba, some of then I´ve manange to solve (related to number of opened files), but this one continue, and I was unable to findout what is the problem. I had to change the strategy, now to it work I have the files on the linux box and mount that on my personal PC, but that causes LOTs of unnecessary network traffic (I use an eclipse based IDE, so when I open it that checks for SVN cache, read all files from libraries...), and make my job slower and harder.

The problem is the follow, when I try to run the sites on the samba mounted share (files on my PC and mounted on server) if I don´t give it a full path on includes (like /home/www/site/lib/file.php) that don´t work, saying that the file can´t be found, even with the include_path of php pointing to /home/www/site/lib, when it should simply work with a direct include of the file (just saying incude 'file.php', I think most ppl using Zend Framework knows what I mean).

The same site works perfectly if I put all the files in the server. I had the very same configuration working on my office, but with ubuntu 9.04.

I can´t say where the problem rly is, I´m about to say that is in the samba, but I don´t know even how to test or debug further this problem.

I hope I was able to make my point clear, cause at this point I´m about to take my hair out of my head. Hope some1 can help me find out what had happened.

---

