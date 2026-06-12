---
title: "Need help with extracting driver from .exe file"
date: 2009-08-07
forum: Networking &amp; Wireless
---

### Post by BigCityCat on 2009-08-07
I was doing this tutorial on how to set up my wireless by using ndiswrapper to install the firmware and driver, but I am new to linux and some of the instructions are confusing me. Specifically.....

> then install the cabextract utility and open up Konsole to navigate the correct directory. Once you have navigated to the directory storing the .exe file, type cabextract filename.exe

from the following article.

[http://www.kubuntu.org/doc/7.10/network/C/connect-wifi.html#connect-wifi-ndiswrapper](http://www.kubuntu.org/doc/7.10/network/C/connect-wifi.html#connect-wifi-ndiswrapper)

I just don't understand. Hell I don't even know if I am on the right track but I am trying. I do have cabextract installed but I don't know where the hell it is.

---

### Post by chili555 on 2009-08-07
> I don't know where the hell it is.You don't have to. What you do need to know is where the .exe is. For example, let's assume it's sitting on your desktop. Open a terminal (Applications -> Accessories -> Terminal) and do:```
cd Desktop
cabextract your_file.exe
```cabextract works on most, but not all, exe's. If you get stuck, post back.

---

### Post by BigCityCat on 2009-08-07
Ok let me try, hang with me for a sec. Thanks

---

### Post by BigCityCat on 2009-08-07
ok check it out. Thanks

Its amazing how a little syntax can screw a person up.

But I did get it extracted, and I vered off the tutorial a bit because I have ndiswrapper installed so I opened it up and I browsed found the inf file installed it, but honestly I really dont know if I need to do anymore other than blacklisting the cutter firmware. Can you give me anymore advice?

---

### Post by BigCityCat on 2009-08-07
I installed it with ndiswrapper, and it's there but it says unable to detect hardware.

All I can say is knetwork sucks ***. I had it working in ubuntu with fb cutter. I guess I will wait to see if the people from Kubuntu decide to fix it a couple months from now. Till then it's back to windows seven.

---

### Post by chili555 on 2009-08-07
Sorry it didn't work for you. Just for my curiosity, do you believe everything will work perfectly in Windows 7 without a bit of fiddling?

---

### Post by BigCityCat on 2009-08-07
I do really appreciate your time. 

I put a lot of time trying to get it to work. 

It's just that wireless is really important. If I can't get that to work then I will use win 7 cause I like it. I also like KDE 4.3. I really don't want to use any of the other Linux distributions. I will just wait and hope they come up with a solution. I am under the impression wireless is a problem for a lot of people with KDE 4.3.

---

### Post by chili555 on 2009-08-07
KDE and wireless have nothing significant to do with each other. No symptom or issue you described is KDE specific. This laptop I am answering from has both Gnome and KDE installed and wireless works equally well with either.

It actually sounds like you have added and deleted a few things without really knowing what they do that you are now lost. I'd be glad to help, however, it's getting a bit late here. Tomorrow, perhaps?

---

### Post by BigCityCat on 2009-08-07
ok I will be back tomorrow, but this is a fresh install and I haven't deleted anything.

I appreciate your help. 

It does not see any wireless right after install.

---

### Post by chili555 on 2009-08-08
Please check Private Messages.

---

### Post by BigCityCat on 2009-08-08
Thank You Mr. Chilie, no more win 7 talk.

---

