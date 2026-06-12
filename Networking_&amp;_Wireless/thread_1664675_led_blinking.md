---
title: "led blinking"
date: 2011-01-11
forum: Networking &amp; Wireless
---

### Post by nyounghoo on 2011-01-11
Hello everyone. i'm new to ubuntu and (i think) i got a major problem.
 
after using xp for a while running fine, I installed 10.10 64bit (Not dual boot. deleted xp) on my computer. i had no problems when it was formatting. But after when i updated, got my gts450 driver, and restarted my computer, the internet stopped working. the red LED keeps blinking while it is connected.
so i intalled XP again to see if ubuntu was the problem. But the xp had the same problem. it showed, the internet is connected, then not connected, connected, not connected, connected, not connected(along with the flashing LED)....
the internet works fine on my other computer with the same cable though...
 
please help. im a korean middle-schooler that got this computer less than a week ago, also with bad english.
 
i have ASUS H55 if that helps a bit....

---

### Post by PatchesTheCaveman on 2011-01-11
Please follow the instructions in this post to provide us with diagnostic information so we can look into your problem:
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

And your English is just fine by the way.  I know American adults who are far worse.  ;-)

---

### Post by mk631219 on 2011-02-23
Led blinking,
I had the same problem so what I did was I put in a ethernet card and now it works. the thing that I did (after I went through this forum) I went to **systems**, then **Preferences** then to **Network Proxy**, and in the **Network proxy** you will find two tabs goto the one that says **Ignored** **H**osts in** the Default **setting. In the **Ignored** **H**ost **list** type in **192.168.1.64** (this is the modems IP address)this may not be what it is so goto you Internet provider to see what it is. Then I put in **255.255.255.0** and then **192.168.1.254**. After you write each one in the box you will push _A_dd. When you are finished you will click on _c_lose. This should fix the problem.  
I hope that it works.
mk631219

---

