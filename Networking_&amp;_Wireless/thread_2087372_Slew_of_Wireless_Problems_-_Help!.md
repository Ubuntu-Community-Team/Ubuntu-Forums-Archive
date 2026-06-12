---
title: "Slew of Wireless Problems - Help!"
date: 2012-11-23
forum: Networking &amp; Wireless
---

### Post by Myst1234 on 2012-11-23
Hello everyone,

So let's get straight down to business. 

I've been using Ubuntu 12.04 for a while now, and any issues I've come across I've been able to find answers to in the forums (or our old friend Google) but I have recently come across 2 issues I cannot solve. Well, actually more of one issue that led into another.

I was having issues with my wireless internet on my HP Pavilion dv6000, nothing too major but I saw that at times my wireless would slow down drastically or even stop working intermittently. I have a netbook attached to the same network that almost never sees issues, so I assumed it was in the laptop itself.

Searching through the forum and such I found a few possible helps for it, but nothing seemed to fix it completely. I recently found one possible solution, but as soon as I executed it I lost wireless entirely. My wireless button will not turn on anymore (maybe a firmware issue?) and of course the dorpdown menu shows no networks or even the ability to enable wireless.

So, my 2 questions are -

1. How can I undo whatever it was that was done to restore the ability to wirelessly connect?

And

2. What can I do to improve the wireless on that laptop in general?

Thanks everyone in advance, this issue has been plaguing me and I'm about to pull my hair out.

**----------EDIT----------**

Ok, so after reading some other user's problems I decided to purge bcmwl-kernel-source and reboot. Afterwards I got my wireless back. I do not know if this is permanent or what. 

And I'm still experiencing odd jerks and such in wireless connection.

---

### Post by wildmanne39 on 2012-11-23
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by Myst1234 on 2012-11-23
netinfo.txt file attached, also created a wireless_script file if you need it

---

### Post by wildmanne39 on 2012-11-23
Hi, that is a good driver this is the only suggestion that I have and it fixed mine.

Set your wireless setting to much the screenshots.
Thanks

---

### Post by Myst1234 on 2012-11-23
I am unable to edit the DNS under the IPv4 Settings. It is greyed out

[B]----EDIT----

[/B]Sorry, I realized just now you also changed the drop down. I've changed it all now. I will post back soon to let you know if it has worked.

---

### Post by Myst1234 on 2012-11-24
Well it's been 24 hours or so since I did the fix and I haven't noticed any problems. Thanks again!

---

