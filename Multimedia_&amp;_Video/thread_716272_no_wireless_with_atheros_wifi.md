---
title: "no wireless with atheros wifi"
date: 2008-03-05
forum: Multimedia &amp; Video
---

### Post by iheartubuntu on 2008-03-05
I installed Ubuntu on my sisters new Toshiba Satellite Pro laptop. At first, the I could not see any wifi networks at all, until I came across the link/tutorial below which solved the problem.

[http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html](http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html)

I followed every step without a problem, and now YES, I can see the wireless networks without a problem, but I cannot make a connection to them. My other two laptops (Fujitsu & Gateway) with Ubuntu can find the wifi networks and log into them with the passphrase, but when I enter the passphrase on THIS system with the Atheros card, it just sits there trying to connect. 

I feel like Im 75% there. Any more tips I can try? I can now see the wifi networks thanks to you, but cant connect to them.

---

### Post by apureevil1 on 2008-03-05
Try WICD..thats what I ended up having to do to get my atheros card to connect (wpa2)
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by iheartubuntu on 2008-03-05
> **apureevil1 said:**
> Try WICD..thats what I ended up having to do to get my atheros card to connect (wpa2)
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

I just tried this and it didnt work. :|

---

### Post by fearevilleet on 2008-03-06
I just moved and was having issues getting my wireless working with a new router, I tried for hours. I installed WICD and bam everything started working. Thanks a lot. Cant believe I never heard of this app before.

---

### Post by akwatve on 2008-03-07
Are you using ndiswrapper ? Give it a try ... I found it very easy to use and configure.
However, I too am currently using wicd. Donno why its not working for u

---

