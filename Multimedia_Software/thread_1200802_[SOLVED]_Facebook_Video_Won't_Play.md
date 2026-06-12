---
title: "[SOLVED] Facebook Video Won't Play?"
date: 2009-06-30
forum: Multimedia Software
---

### Post by aysiu on 2009-06-30
Here's a weird one for you.

So I'm using Ubuntu 9.04 with the lpia kernel right now. I had Flash installed from the repositories, and normal Flash stuff would work (Flash websites, YouTube). But when I tried to play a video through Facebook, I got a message that I needed the latest Flash installed. I went to the Adobe website to download "the latest Flash," which actually downgraded my version, and I had to "convert" it from i386 to lpia architecture. Once that was installed, I got the same message from Facebook... but YouTube still worked fine.

If I use the regular i386 live CD and install Flash from the Adobe website, video on Facebook works just fine.

Is this an lpia thing? And, if so, why do other Flash websites work just fine and not Facebook? Anyone else experiencing this? Any proposed fixes, apart from ditching lpia altogether?

---

### Post by aysiu on 2009-06-30
Never mind. It's not an lpia thing. It's an /opt/firefox issue.

Apparently, if you install Flash directly from the Adobe website, it goes to /usr/lib/adobe-flashplugin/libflashplayer.so instead of to the traditional plugins folders (/usr/lib/mozilla/plugins or /usr/lib/xulrunner-addons/plugins).

So I just closed Firefox, copied /usr/lib/adobe-flashplugin/libflashplayer.so to /opt/firefox/plugins/ and restarted Firefox and it worked.

---

### Post by ckunzler on 2009-07-22
> **aysiu said:**
> Never mind. It's not an lpia thing. It's an /opt/firefox issue.

Apparently, if you install Flash directly from the Adobe website, it goes to /usr/lib/adobe-flashplugin/libflashplayer.so instead of to the traditional plugins folders (/usr/lib/mozilla/plugins or /usr/lib/xulrunner-addons/plugins).

So I just closed Firefox, copied /usr/lib/adobe-flashplugin/libflashplayer.so to /opt/firefox/plugins/ and restarted Firefox and it worked.

I'm having the same problem, and I'm not sure how I need to go about copying and pasting the above solution.  I hope its ok to ask such a basic question.

---

### Post by HappyFeet on 2009-07-22
I just put **libflashplayer.so** into ~/.mozilla/plugins

Never had a flash problem doing that.

---

### Post by aysiu on 2009-07-22
> **ckunzler said:**
> I'm having the same problem, and I'm not sure how I need to go about copying and pasting the above solution.  I hope its ok to ask such a basic question.
Press Alt-F2

A *Run Application* dialogue will appear

Paste in the command ```
gksudo nautilus
``` and then you can copy the plugin.

---

### Post by ckunzler on 2009-07-22
> **aysiu said:**
> Press Alt-F2

A *Run Application* dialogue will appear

Paste in the command ```
gksudo nautilus
``` and then you can copy the plugin.

That just brought up a root file browser and I didn't know where to go from there.  

I'm wondering if I could solve the problem if I just uninstall flash then reinstall it from synaptic since as you say the problem was caused by downloading flash directly from Adobe's website.
Thanks for you help.

---

### Post by wb8erj on 2009-09-05
I too had this problem, and was able to fix it with the directions on [this link.]("http://www.mikestechblog.com/joomla/operating-systems-section/operating-systems-ubuntu/87-facebook-videos-myspace-player-wont-play-ubuntu-firefox.html")

-- Mike

---

