---
title: "problem after unistalling envy"
date: 2008-02-08
forum: Multimedia &amp; Video
---

### Post by ilwa7esh on 2008-02-08
I installed envy and everything was working properly except i couldnt use 1680 * 1050 mode . so i decided to uninstall, i unistalled driver (i have ati x1950 pro) and restarted. What i had was a screen full of horizontal lines. I restart in recovery mode and typed envy --uninstall-all
but I still have the same problem. Can anyone please help me?

---

### Post by overdrank on 2008-02-08
> **ilwa7esh said:**
> I installed envy and everything was working properly except i couldnt use 1680 * 1050 mode . so i decided to uninstall, i unistalled driver (i have ati x1950 pro) and restarted. What i had was a screen full of horizontal lines. I restart in recovery mode and typed envy --uninstall-all
but I still have the same problem. Can anyone please help me?

HI and after uninstalling Envy along with your graphics driver you may need to reconfigure you xorg from recovery mode. ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by ilwa7esh on 2008-02-08
ok i did that, and it solved half the problem. I restarted and i was on low graphics mode so i tried and reinstalled the restricted driver but after reboot i got a blackscreen so i redid your advice again but now am stuck with low resolution. what should i do?
thank you for your help

---

### Post by ilwa7esh on 2008-02-08
ok problem solved, here is what i did though i dont know why it work.

I installed restricted driver but did not restart
I uninstalled restricted driver and restart
I unchecked all respositories and reloaded, ( read this on a post)
I rechecked them and installed the driver again and its now working

Thank you for ur help overdrank

---

### Post by The New Guy on 2008-03-01
Hey u guys I did not want to make a new post (not because Im lazy or anything like that but because I was reading yours and I hope someone help me) because I found this one. Anyways I installed envy about a week ago and start working fine but I was playing a video on youtube and when I try to make it big the video starts going slow and the computer starts freezin. And the computer acts weird solw even in the internet just by displaying a page.Then I went to ATI Catalyst Cotnrol and see what I can do from there but it show me this error
<img src=http://img141.imageshack.us/img141/9394/atiui6.png>
**[COLOR="Black"]So I was wondering what can I do to fix it? or what? Please guys some help.[/COLOR]**

This are my basics u know:
Compaq Presario
1GB Memory Ram
ATI Radeon Express 200 Series
2.2 GHz AMD Athlon 64+3500
200 GB Hard drive
Compaq Presario

---

### Post by The New Guy on 2008-03-01
Please ignore the first post ( u know the pic didn't show)

Hey u guys I did not want to make a new post (not because Im lazy or anything like that but because I was reading yours and I hope someone help me) because I found this one. Anyways I installed envy about a week ago and start working fine but I was playing a video on youtube and when I try to make it big the video starts going slow and the computer starts freezin. And the computer acts weird solw even in the internet just by displaying a page.Then I went to ATI Catalyst Cotnrol and see what I can do from there but it show me this error
[http://img141.imageshack.us/img141/9394/atiui6.png](http://img141.imageshack.us/img141/9394/atiui6.png)

So I was wondering what can I do to fix it? or what? Please guys some help



This are my basics u know:
Compaq Presario
1GB Memory Ram
ATI Radeon Express 200 Series
2.2 GHz AMD Athlon 64+3500
200 GB Hard drive
Compaq Presario

---

