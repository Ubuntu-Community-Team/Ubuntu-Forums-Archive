---
title: "natty &amp; adobe flash player"
date: 2011-03-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by kuvanito on 2011-03-02
how to install,any advice? Thanks:popcorn:

---

### Post by ronacc on 2011-03-02
download the installer  from adobe and just extract it and copy libflashplayer.so to /usr/lib/mozilla/plugins . of course get the right one for your arch .

---

### Post by MadCow108 on 2011-03-02
or just install flashplayer-installer which does that for you.

---

### Post by kuvanito on 2011-03-02
to madcow:
it does not work......

---

### Post by cariboo on 2011-03-02
What doesn't work? It's pretty hard to help you with so little information. What error message are you getting? What browser are you using? Are you trying to install 32 or 64 bit?

---

### Post by kuvanito on 2011-03-02
in natty installing adobe flash player from the adobe website simply DOES NOT WORK!
running the Installer does not work so far....
but I have not tried the other way that ronacc suggested,I will try as soon as I can,30 mins

---

### Post by David D. on 2011-03-02
Have you tried using the Firefox add-on Flash-Aid?

---

### Post by kuvanito on 2011-03-02
yes david,i have tried that and it does not work either

---

### Post by dubmartian on 2011-03-02
[FONT=monospace]these have always in the repos after a fresh install and repo update.
sudo apt-get install flashplugin-installer flashplugin-nonfree

[http://packages.ubuntu.com/natty/flashplugin-nonfree](http://packages.ubuntu.com/natty/flashplugin-nonfree)
[/FONT]

---

### Post by ronacc on 2011-03-02
here is the link if you are 64bit , it works for me with Opera ,chrome ,FF and epiphany . remember just extract the installer with archive manager and copy the .so to /usr/lib/mozilla/plugins

edit : opps forgot to add the link [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz)

---

### Post by mc4man on 2011-03-02
> in natty installing adobe flash player from the adobe website simply DOES NOT WORK!
That would be correct _atm _in a default install - 
Software Center is the default installer for .debs and it will fail on downloaded .debs in one of 2 ways if the .deb is not in the apt cache.
Either SC will open and nothing will happen (likely in this case) or  it will open and you'll get an aptdaemon error

The methods described by ronaac or dubmartian will work or install gdebi, and make it the default installer for .debs
(r. click on any .deb > properties > open with and switch to gdebi, if you don;t have a ,deb handy then take an empty text file, rename to 1.deb and use that to change defaults

---

### Post by kuvanito on 2011-03-02
Thank You All.
this worked like a charm: sudo apt-get install flashplugin-installer flashplugin-nonfree
Please,closed thread now and Thanks again.:D

---

### Post by beew on 2011-03-02
Actually the best way to install flash would be to use the flashaid plugin for firefox developed by forum member lovinglinux. I wouldn't even try to install it from adobe.

---

### Post by ronacc on 2011-03-02
> **beew said:**
> Actually the best way to install flash would be to use the flashaid plugin for firefox developed by forum member lovinglinux. I wouldn't even try to install it from adobe.

that works for 32bit but if you are 64bit and want to use the 64bit flash follow the link I gave above and use the method I described . 32bit works on a 64bit sys but I prefer to run native as much as possible .

---

### Post by jerrylamos on 2011-03-03
> **kuvanito said:**
> Thank You All.
this worked like a charm: sudo apt-get install flashplugin-installer flashplugin-nonfree
Please,closed thread now and Thanks again.:D

I've just been using Synaptic from Unity 3D or classic depending on the computer.  My pc's are all 32 bit.  Famous last words, so far so good.

Jerry

---

### Post by puller on 2011-03-31
> **ronacc said:**
> here is the link if you are 64bit , it works for me with Opera ,chrome ,FF and epiphany . remember just extract the installer with archive manager and copy the .so to /usr/lib/mozilla/plugins

edit : opps forgot to add the link [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz)

Wow, this works very well!
I am using Kubuntu Natty 64 bit with chrome and downloaded the libflashplugin.
I had no clue where to copy it, I didn't know that folder worked also for chrome.
To be more complete:
cd to the folder where you have the libflashplayer.so file, then
```
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
```

Thanks again.

---

