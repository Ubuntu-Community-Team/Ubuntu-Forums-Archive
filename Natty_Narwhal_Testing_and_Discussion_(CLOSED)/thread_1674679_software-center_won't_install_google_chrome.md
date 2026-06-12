---
title: "software-center won't install google chrome"
date: 2011-01-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ronacc on 2011-01-24
I d/l'd google chrome and clicked on the .deb S-C opens and I click install and installing briefly flashes but nothing installs . dpkg from term installs it with no problem .

---

### Post by mc4man on 2011-01-24
i don't think sc will install any d/l'd .deb

---

### Post by VMC on 2011-01-24
I found that out a few days ago. I needed to install debinstaller in order to install chrome.

---

### Post by ronacc on 2011-01-24
@ mc4man it installed Opera for me ok .

@ VMC do you mean the "do everything software related" software-center needs outside helpers that aren't in its "depends" ?

---

### Post by mc4man on 2011-01-24
> it installed Opera for me ok .
I should have said 'that's not in a source' 
I use opera and it will install that, likely because opera adds  a software source. Haven't found sc able to install any .deb that isn't in the sources list(s)

Did file a bug last wk. though figured there should be one by now, though couldn't find one
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/706041](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/706041)

---

### Post by DougieFresh4U on 2011-01-24
I tried installing kernel from the ppamain and s-c would not do it, but package installer did just fine.

---

### Post by ronacc on 2011-01-24
> **mc4man said:**
> I should have said 'that's not in a source' 
I use opera and it will install that, likely because opera adds  a software source. Haven't found sc able to install any .deb that isn't in the sources list(s)

Did file a bug last wk. though figured there should be one by now, though couldn't find one
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/706041](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/706041)

yes the "source" thing could be it . I me too'd your bug and added comment .

---

### Post by mc4man on 2011-01-24
> me too'd your bug and added comment 
We'll see if anything comes of that report - though I'd think there has to be an existing one somewhere - as far as I remember this has been occuring for quite some time, at least a month or so.
(I never know whether to use a 'plain' description or pick a relevant line from a debug or error message.

(what I do find curious is I've yet to get an apport on anything in natty, the only time was when I knew something would crash (bzr), so I did it as root - that was the only time

---

### Post by cariboo on 2011-01-24
> (what I do find curious is I've yet to get an apport on anything in natty, the only time was when I knew something would crash (bzr), so I did it as root - that was the only time

I get an entry in /var/log/boot.log:

```
Stopping automatic crash report generation
```

so it looks to me that apport is crashing, on at least one of my systems.

---

### Post by mc4man on 2011-01-24
> so it looks to me that apport is crashing, on at least one of my systems.

I think so - I have an old bug on that (or similar), I'm figuring  that again maybe it's somewhere else confirmed or possibly there is no intention of using apport in natty (or one of the 1/2 dozen other reasons bugs go un-responded to...
[https://bugs.launchpad.net/ubuntu/+source/apport/+bug/696118](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/696118)

ronaac (or anyone else - 
you are allowed to change the status of a bug (if proper to do so), so if doing a 'me too' and you see a bug as 'new' it's good to change the status to 'confirmed'
Just click on the little 'new' link under Status and a pop up will happen

---

### Post by w3rt on 2011-01-24
the package chromium-browser may be what you want

---

### Post by mc4man on 2011-01-24
> I get an entry in /var/log/boot.log:  ...ect.
While i don't see that there do now on one install (5 days old), see a fail in the boot text 'start automatic crash detection' or thereabouts.

enabling apport in /etc/defaults gets rid of it, (disabled by default), seems to be a moot point - if apport does pop up it will crash itself. Going to leave off here.

---

### Post by ronacc on 2011-01-24
> **mc4man said:**
> 
ronaac (or anyone else - 
you are allowed to change the status of a bug (if proper to do so), so if doing a 'me too' and you see a bug as 'new' it's good to change the status to 'confirmed'
Just click on the little 'new' link under Status and a pop up will happen

sorry I usually do that but I was having a "senior moment "
 corrected my lapse and changed to "confirmed"

---

### Post by mc4man on 2011-01-24
> and changed to "confirmed"
I have yet and likely never will quite understand how things work in launchpad concerning bugs and whether a confirm matters or changes anything in getting a bug looked at.
I used to think it had to be confirmed first,  the one thing I now know is that's not true. 
Anyway, like you, I'll confirm a bug I'm doing me too on if it hasn't yet been, seems like the best thing to do.

---

### Post by VMC on 2011-01-24
> **mc4man said:**
> We'll see if anything comes of that report - though I'd think there has to be an existing one somewhere - as far as I remember this has been occuring for quite some time, at least a month or so.
(I never know whether to use a 'plain' description or pick a relevant line from a debug or error message.

(what I do find curious is I've yet to get an apport on anything in natty, the only time was when I knew something would crash (bzr), so I did it as root - that was the only time

Also "me-too" the report. Thanks

---

### Post by ratcheer on 2011-01-24
> **mc4man said:**
> I have yet and likely never will quite understand how things work in launchpad concerning bugs and whether a confirm matters or changes anything in getting a bug looked at.
I used to think it had to be confirmed first,  the one thing I now know is that's not true. 
Anyway, like you, I'll confirm a bug I'm doing me too on if it hasn't yet been, seems like the best thing to do.

Here you go: [https://wiki.ubuntu.com/Bugs/HowToTriage/Charts](https://wiki.ubuntu.com/Bugs/HowToTriage/Charts)

Tim

---

