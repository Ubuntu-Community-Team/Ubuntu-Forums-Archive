---
title: "Youtube stopped working today..."
date: 2010-01-07
forum: Multimedia Software
---

### Post by JAYCEE1 on 2010-01-07
I running 8.04 (Hardy) on an IBM Thinkpad T41. 

I watch something on youtube every day. Today when I tried youtube, I got the "Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player" message.

I haven't made any changes to my computer at all to cause this problem. Youtube always worked fine before.

I tried installing the Flash10 deb from the adobe website.

I tried sudo apt-get install flashplugin-nonfree

And I tried sudo apt-get install flashplugin-installer (gave me an error)

Any idea how to fix this problem?

---

### Post by markbuntu on 2010-01-08
If you got the new flash10 from adobe and tried to install it it is on your system just in the wrong place. All you need to do is move the libflashplayer.so from /usr/lib/adobe-flashplugin to /usr/lib/flashplugin-nonfree and restart firefox. if you want to save the old libflashplayer.so you can move it somewhere or rename it before you move the new one.

I am also using hardy and that is what worked for me.

---

### Post by jbandlow on 2010-01-08
I'm using 9.10 and had the same problem today.  I'd like to try to figure out the cause before I try to fix it.  Automatic updates brought me Firefox 3.5.7 and a kernel update today, and I suspect this could be the source.  Anyone know anything more?

---

### Post by JAYCEE1 on 2010-01-08
> **markbuntu said:**
> If you got the new flash10 from adobe and tried to install it it is on your system just in the wrong place. All you need to do is move the libflashplayer.so from /usr/lib/adobe-flashplugin to /usr/lib/flashplugin-nonfree and restart firefox. if you want to save the old libflashplayer.so you can move it somewhere or rename it before you move the new one.

I am also using hardy and that is what worked for me.

I should have said that I use Opera 9.52. Youtube works fine in Firefox.

---

### Post by cprofitt on 2010-01-08
Do you have any script-blocking add-ons for your browser? I just ran the updates and I am not having any issues.

---

### Post by jbandlow on 2010-01-08
> **cprofitt said:**
> Do you have any script-blocking add-ons for your browser? I just ran the updates and I am not having any issues.

I've disabled all my add-ons, and I'm still having the problem.   Like JAYCEE1, I have not had problems before today.  Youtube works fine in Chrome, only Firefox has problems.  I'm on Ubuntu 9.10, Firefox 3.5.7 (32 bit), Shockwave Flash 10.0 r42.

BTW, it occurs to me that I may be inappropriately threadjacking, since JAYCEE1 seems to have a different problem. (Not sure, I'm new here.) If that's the case, let me know and I'll open a new thread.

[Update:  After re-enabling all my add-ons, YouTube works again.  Strange.  I don't understand what the problem was, but I guess I don't have it anymore.]

---

### Post by cprofitt on 2010-01-08
> **jbandlow said:**
> I've disabled all my add-ons, and I'm still having the problem.   Like JAYCEE1, I have not had problems before today.  Youtube works fine in Chrome, only Firefox has problems.  I'm on Ubuntu 9.10, Firefox 3.5.7 (32 bit), Shockwave Flash 10.0 r42.

BTW, it occurs to me that I may be inappropriately threadjacking, since JAYCEE1 seems to have a different problem. (Not sure, I'm new here.) If that's the case, let me know and I'll open a new thread.

[Update:  After re-enabling all my add-ons, YouTube works again.  Strange.  I don't understand what the problem was, but I guess I don't have it anymore.]


Glad yours was solved.

---

### Post by HappyFeet on 2010-01-08
> **JAYCEE1 said:**
> I should have said that I use Opera 9.52. Youtube works fine in Firefox.

Download the tar.gz flash file from adobe and unzip it, then put the libflashplayer.so file into /usr/lib/opera/plugins

---

