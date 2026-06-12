---
title: "Firefox opens with offline mode"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by sreeyeshns on 2009-01-04
When I login to ubuntu and open firefox for the first time, it starts with offline mode and displays the message 

Offline Mode
Firefox is currently in offline mode and can't browse the Web.

Each time I login,I have to uncheck the work offline check box from the file menu. Somrone please reply.:)

---

### Post by ajgreeny on 2009-01-04
Try going to **about:config** in the FF address bar and then in the filter search for **offline**.  In my case it brings up about 8 lines one of which is:-

**browser.offline   user set   boolean    false**

I have never changed that to my knowledge, even though it says "user set", and I don't want to play around too much, but have a look in your about:config to see if it is set to "true".  If so double click to change it and try again opening FF

---

### Post by pkands on 2009-01-04
I think there is a firefox extension to force firefox to be online.

---

### Post by Sealbhach on 2009-01-04
Are you using a PPP modem in Ubuntu 8.04? That used to happen to me becaue network manager could not see that I was connecting using Gnome-PPP.  

I didn't know how to fix it.:confused:

.

---

### Post by ProgramErgoSum on 2009-01-04
I had the same observation as that of Sealbhach's. That is, when connecting thru" the PCMCIA card, the networking would appear as 'No network connection' which forces FF into Offline mode.

I uncheck the 'Work Offline' option in File menu option in FF and I am able to browse the net.

I think, Network Manager (or, whatever) needs to identify that networking is enabled.

---

### Post by sreeyeshns on 2009-01-04
I tried it. But the "Browser.offline" is set to false by default.:confused:

---

### Post by joshmuffin on 2009-01-04
Change it to true?

---

### Post by ranch hand on 2009-01-05
If you are on dial up the easiest thing to do is get used to it.  I have this problem and fought it for a month or two and there just doesn't seem to be a resolution to the problem.

It really can get on your nerves if you let it.  I do have the option of reinstalling Vista.  Thinking of that usually will cure my irritation at such a small thing as having to set FF to online every time.  I could have to use Vista every time.

---

### Post by Sealbhach on 2009-01-05
Was it not fixed in 8.10? You could perhaps install Network Manager 0.70 if you don't have it.

Also perhaps try upgrading to Firefox 3.1 or 3.2. These are available as Beta releases but are very stable and usable. Also, maybe try Opera, see if it's got the same thing?


.

---

### Post by pkands on 2009-01-05
Long Description

Tired of having to manually uncheck Work Offline when you're working on a [http://localhost](http://localhost) server? This forces Firefox to think it's online, no matter the network connection status.

[https://addons.mozilla.org/en-US/firefox/addon/8502](https://addons.mozilla.org/en-US/firefox/addon/8502)

---

### Post by ieee488 on 2009-01-05
[http://www.nabble.com/Firefox-3:-how-to-avoid-offline-mode-startup---td17058203.html](http://www.nabble.com/Firefox-3:-how-to-avoid-offline-mode-startup---td17058203.html)

scroll down to the bottom; that fixed it for me

---

### Post by ranch hand on 2009-01-05
ALL RIGHT!  That seems to have worked for me too.  Thanks a bunch for that.

I should probably turn you in to MS.  That was really the only irritation that I had with Ubuntu.  It bothered my wife more than me, but Vista bothered me more than it did her.  STook me 4 days or so to want to try something else.  Took her a month.

It is hard to give up on something that you are familiar with even if it sucks.

I think that Linux in general just makes working on the computer fun again.

---

### Post by ranch hand on 2009-01-05
Double post, too excited.

---

### Post by ProgramErgoSum on 2009-01-05
Couple of posts above in this thread, there is a reference to a FireFox addon to force FF to be in online mode when working with localhost. With the resolution related to changes in about:config, will working with localhost keep FireFox online ? (Sorry...I don't have means to test this.)

---

### Post by ranch hand on 2009-01-05
I have no idea really what working with local host means to you.  My modem is working through local host as that is the primary setting.

I do know that the about:config solution will not work if you have not installed the latest FF updates.

I have 3 installs of Hardy, one to use and 2 to play with (I mean learn on).  The one we use and one of the play ones worked fine with that solution.  The other did not have that option untill I updated it.

That 3rd install is on an external HDD and I am having a lot of fun learning about grub.

Soon I may know enough to get into real trouble.

---

### Post by Bearly Able on 2009-02-26
Thanks, ieee488 - the link worked for me, too.  I was having the same problem in Xubuntu 8.04 with a dial-up connection.

---

