---
title: "Ubuntu Ultimate 2.7(bypassing proxy server)"
date: 2010-08-19
forum: Networking &amp; Wireless
---

### Post by Aprajita on 2010-08-19
this is my first post so sorry if i am in the wrong section and yaa i may also not be technically correct in what i wrote,but i'll try to make all things clear....

I am a student. Our Coll. provides internet facility to us,but only from 8 p.m to 12 p.m.They use proxy server for controlling the timings of net.when i used windows i cant find any way to bypass proxy and use internet for 24 hours..(later i found some softwares lyk jap etc....)

Now when i used Ubuntu Ultimate 2.7 edition and tried to access net,to my wonders i found net is still working,i dont understand how did proxy server was automatically bypassed by ubuntu ultimate???

this didn't work in previous versions of ubuntu....

Definetly i am happy to use the internet 24 hours,but the word "HOW?" is troublling me....can anyone help???

---

### Post by nbkr on 2010-08-19
Sounds like a broken network design on your college. If done correctly you won't be able to bypass a proxy. 

Just a suggestion: There is proxy and the usage of the proxy is enforced on windows by a group policy or an application running on the windows client.

By running Ubuntu the windows tools that force the browser to use the proxy don't work. This in combination with a badly configured firewall (that let's everyone connect to port 80 of any webserver instead of just the proxy) will allow you Ubuntu to access the web 24/7.

---

