---
title: "Multiple chrome processs'"
date: 2012-11-19
forum: Networking &amp; Wireless
---

### Post by dannyboy79 on 2012-11-19
I am not sure if this is normal but it's taking a lot of the limited precious RAM I have. I only have 2GB of RAM so chrome processs' taking up almost 600MB is TOO MUCH. Is this due to having so many tabs open? I am running Version 23.0.1271.64. I am not even sure where I installed it from, whether from a PPA or downloaded from their website. How can I find out where I got it from and or if I can upgrade.

Here's a picture.
[IMG]https://lh6.googleusercontent.com/-tLfPpozNxnI/UKrESQ1Wp9I/AAAAAAAAAmk/V-6qBXEw1hQ/s801/chrome%2520processs.png[/IMG]

---

### Post by wojox on 2012-11-19
> **dannyboy79 said:**
> I am not even sure where I installed it from, whether from a PPA or downloaded from their website. How can I find out where I got it from and or if I can upgrade.

Try:
```
apt-cache policy chrome
```

---

### Post by dannyboy79 on 2012-11-19
daniel@core2duo:~$ apt-cache policy chrome
W: Unable to locate package chrome

---

### Post by vasa1 on 2012-11-19
> **dannyboy79 said:**
> daniel@core2duo:~$ apt-cache policy chrome
W: Unable to locate package chrome
Not chrome but google-chrome-stable or google-chrome-beta or google-chrome-unstable

You can check the actual name on your system by searching the output of 
```
dpkg --get-selections
```
for google-chrome.

---

### Post by vasa1 on 2012-11-19
Nowadays, browsers include diagnostic tools that provide browser-specific information. For example, you could look at "former wrench" >  tools > task manager in Chrome to get a brief idea of things related to Chrome or just point your Chrome browser to chrome://memory-redirect/.

I don't worry about RAM until performance actually suffers.

Also, you may want to look at this oldish link:
[http://blog.chromium.org/2008/09/multi-process-architecture.html](http://blog.chromium.org/2008/09/multi-process-architecture.html)

---

### Post by deadflowr on 2012-11-19
>  I am not even sure where I installed it from, whether from a PPA or downloaded from their website.

You installed one of two ways.
Through the google-chrome-(stable,beta,unstable).deb file you can get when you visit google-chrome and try to download chrome.
Or, you added google-chrome(version) to your sources.list.
When you install the .deb, it automatically adds chrome to the repos(so you can get updated).


```
apt-cache policy google-chrome-stable
```

---

### Post by dannyboy79 on 2012-11-19
ok, so I figured out what version I am running, the stable one BUT is there anything I can do about the amount of RAM it takes up besides just running less tabs?

---

### Post by vasa1 on 2012-11-19
Do you have such high swap use when Chrome is totally not running?

The other thing is your up time of about three days. Was Chrome running all the while? Even though they shouldn't browsers may go crazy over time.

---

