---
title: "Internet problems with Ubuntu 8.10"
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by shmax44 on 2009-02-26
I had mozilla working fine on my system and all of a sudden it stopped working. I thought maybe it was just my connection, but I'm picking up the wireless networks and I even plugged directly into the router. I'm connecting, but my browser just gives me the page can't be found message... and yes, I tried more than one page.

I tried updating the system but nothing is working with getting online now. I'm running a dual system with vista so I just have to keep switching back to vista to use the internet. Is there another browser I can download from vista and run on ubuntu to get online again? Any easy way to reinstall mozilla completely? I tried unistalling it and am afraid I might have just partially uninstalled it and caused a lot of my problems. System restore would be awesome right now.

Why can't I plug directly into the router and just update the system again? Any answers, thoughts, or ideas would be awesome.

---

### Post by Crafty Kisses on 2009-02-26
First thing is first, have you tried any other web browsers? Another thing you should probably try is pinging a website so you can get a definite answer of what's going on, you should be getting replies if you ping a website. You can run the following and it will attempt to ping a website:
```
ping websitename
```
Also you may need to change your network settings in Firefox which is pretty simple to do, open up Firefox and go to **Edit->Preferences->Advanced->Network->Settings** from there you can edit your settings. I remember reading somewhere it might have something to do with DNS, but not too sure on that.

---

### Post by shmax44 on 2009-02-26
> **Codename said:**
> First thing is first, have you tried any other web browsers? Another thing you should probably try is pinging a website so you can get a definite answer of what's going on, you should be getting replies if you ping a website. You can run the following and it will attempt to ping a website:
```
ping websitename
```
Also you may need to change your network settings in Firefox which is pretty simple to do, open up Firefox and go to **Edit->Preferences->Advanced->Network->Settings** from there you can edit your settings. I remember reading somewhere it might have something to do with DNS, but not too sure on that.

I'm not getting anything back when a ping a website. It's not finding the sites, but saying it's connected. Weird. I tried editing settings too. Something is really messed up. Any other ideas of what it could be? how would I install a different browser to see if that's the problem? It's tough cause I have to download it to a jump drive and try and install it then. Still trying to get the hang of installing stuff on ubuntu too.

---

### Post by shmax44 on 2009-02-27
This seems to be a common message I'm getting when trying to update or install new things in the command prompt:

"Could not resolve 'archive.ubuntu.com'"
or
"Could not resolve 'ppa.launchpad.net' "

I'll try sudo apt-get update and it tells me:

"W: Some index files failed to download, they have been ignored, or old ones used instead. 
W: You may want to run apt-get update to correct these problems"

It's sending me in circles!

---

### Post by superprash2003 on 2009-02-27
you could try changing your dns servers to opendns - 208.67.222.222 and 208.67.220.220

for reference : [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

