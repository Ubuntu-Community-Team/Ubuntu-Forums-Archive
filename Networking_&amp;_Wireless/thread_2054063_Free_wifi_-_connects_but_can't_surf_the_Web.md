---
title: "Free wifi - connects but can't surf the Web"
date: 2012-09-06
forum: Networking &amp; Wireless
---

### Post by Aquadag on 2012-09-06
System: Acer Aspire 5755-6699 dual booting Ubuntu 12.04 LTS / Windows 7. 

When I use password protected wifi at home, both Ubuntu and Windows connect automatically and either one will allow me to surf the Web. 

 === 

 When I'm at the mall using free wifi: 

+ **WINDOWS** 7 connects. When I start a browser the welcome document (the one you agree to terms of use on) comes up. After I interact with that document I can surf the Web as much as I like. 

+ **UBUNTU** 12.04. Wicd makes a connection. I found that the connection is stable enough so I can open Terminal and use Telnet or FTP to exchange data with a remote site. 

 However, I have NOT been able to use a browser and surf the Web. When the browser comes up and I try to surf I often get a network error. Sometimes an address comes up that is only the part of the one Windows' browser sees when the Welcome page comes up. But Ubuntu's browser never opens the welcome page, I can't accept the terms. I presume that I time out because the "remote site" breaks the connection. (I tried with Opera and Firefox, neither worked)
any suggestions will be appreciated

---

### Post by slimx3m on 2012-09-06
can you run this command on either machine?
```
ping google.com
```
if you get an error it might not be your machines, but rather your modem or router.  Also another testing would be connecting it to LAN to see if you can ping the world.

hope that helps.

---

### Post by AlanR8 on 2012-09-06
slimx3m....

> When I'm at the mall using free wifi: 

---

### Post by inobe on 2012-09-06
search google **ubuntu resolvconf**

[http://manpages.ubuntu.com/manpages/lucid/man8/resolvconf.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/resolvconf.8.html)

[http://www.google.com/search?q=ubuntu+network+name+server&aq=0&oq=ubuntu+network+names&sugexp=chrome,mod=12&sourceid=chrome&ie=UTF-8#hl=en&sugexp=les%3B&gs_nf=1&pq=ubuntu%20network%20name%20server&cp=14&gs_id=1m&xhr=t&q=ubuntu+resolvconf&pf=p&sclient=psy-ab&oq=ubuntu+resolvc&gs_l=&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.&fp=de59494a72cb60bd&biw=1920&bih=961](http://www.google.com/search?q=ubuntu+network+name+server&aq=0&oq=ubuntu+network+names&sugexp=chrome,mod=12&sourceid=chrome&ie=UTF-8#hl=en&sugexp=les%3B&gs_nf=1&pq=ubuntu%20network%20name%20server&cp=14&gs_id=1m&xhr=t&q=ubuntu+resolvconf&pf=p&sclient=psy-ab&oq=ubuntu+resolvc&gs_l=&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.&fp=de59494a72cb60bd&biw=1920&bih=961)

[http://www.google.com/search?q=ubuntu+network+name+server&aq=0&oq=ubuntu+network+names&sugexp=chrome,mod=12&sourceid=chrome&ie=UTF-8](http://www.google.com/search?q=ubuntu+network+name+server&aq=0&oq=ubuntu+network+names&sugexp=chrome,mod=12&sourceid=chrome&ie=UTF-8)

---

### Post by Aquadag on 2012-09-07
Demonjames' 09/06 10:10 post [on Craigslist Linux forum] suggesting <b>Auto Detect Proxy,</b> setting worked with Firefox and allowed me to log on at the mall. 

I prefer to browse with Opera, but Demonjames' 09/06 11;08 suggestion about proxy settings for Opera didn't work. I've reported the inability of Opera to autodetect proxy as a bug but who knows whether they'll fix it. 

Fortunately, I found that once I logged on with Firefox I could close Firefox and surf with Opera. 

Same computer under Windows and I can log on with Opera. Makes you wonder what Windows does that Ubuntu doesn't do, and why Ubuntu doesn't. I may report this to Ubuntu as a bug.

---

