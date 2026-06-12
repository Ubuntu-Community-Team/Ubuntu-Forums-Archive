---
title: "online video will not play in Ubuntu -- Help Please!"
date: 2011-05-02
forum: Multimedia Software
---

### Post by nrundy on 2011-05-02
[http://www.cbsnews.com/video/watch/?id=7364554n](http://www.cbsnews.com/video/watch/?id=7364554n)

I can't get this video to play in Chromium or Firefox when using Ubuntu. I logged into Windows XP and the video plays fine. Back to Ubuntu and I can't get it to play. all are Plugins Enabled (e.g., Flash).

Any ideas on why it won't play?

---

### Post by trehanabhinav on 2011-05-02
brother, i had the same problem a few weeks ago.
try reinstalling flash plugin or look for a addon called flash aid.

---

### Post by nrundy on 2011-05-02
i'm already using flash-aid. i tried reinstalling flash but still no joy. It also doesn't work with chrome though--it has built in flash.

does the video play for you?

---

### Post by andrew.46 on 2011-05-03
Works fine here.....

---

### Post by tjones00 on 2011-05-03
I'm playing it fine including all the..........commercials.

All I did was install restricted extras no flash aid etc.

```

sudo apt-get install ubuntu-restricted-extras
```

Or install via synaptic.

One of the first things you should always do with a fresh install to ensure media compatibility.

---

### Post by nrundy on 2011-05-03
i have restricted extras installed. 

Man, I wish I could figure out what's wrong.

---

### Post by globalmac on 2011-05-04
> **nrundy said:**
> i have restricted extras installed. 

Man, I wish I could figure out what's wrong.
Don't know why but non-free flash is un-installed upon upgrade. Open a terminal and type "sudo apt-get install flashplugin-nonfree" (remember don't type the quotation marks). This worked for me, hope it works for you.

---

### Post by nrundy on 2011-05-04
[http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)

Adobe is showing its installed properly. Plus, again, I can't even view it with Chrome--it has built in flash. So i'm not sure it's a flash problem. Anybody have any ideas?

---

### Post by fremantle on 2011-05-04
try cleaning up your fash cache. 

you should install bleachbit, or do it from flash settings.

---

### Post by nrundy on 2011-05-05
I have tried four browsers:

Firefox
Chrome
Chromium
Opera

Video will not play. When I boot into Windows. The video plays fine. So something to do with an Ubuntu setting?

Anybody have anymore ideas? please?

---

### Post by SeijiSensei on 2011-05-05
Do you use AdBlock Plus?  Noscript?  Turn them off.  Many commercial video sites will not play any content unless you enable them to show the ads first. 

Another, though less likely, possibility is that the site checks to see what type of browser is being used.  Usually if the site refuses a browser, it tells you so.  You could try using the [User Agent Switcher](https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/) add-on for Firefox and masquerade as a Windows user.

---

### Post by Sikez on 2011-05-05
> **nrundy said:**
> [http://www.cbsnews.com/video/watch/?id=7364554n](http://www.cbsnews.com/video/watch/?id=7364554n)

I can't get this video to play in Chromium or Firefox when using Ubuntu. I logged into Windows XP and the video plays fine. Back to Ubuntu and I can't get it to play. all are Plugins Enabled (e.g., Flash).

Any ideas on why it won't play?

Are you running a 32bit or 64bit versions of Ubuntu & flash?

The video starts/plays for me,then it stops after 4 seconds and does not start again.
using Flash Player 10,3,162,29 on Ubuntu 10.10 64Bit
[]("http://labs.adobe.com/downloads/flashplayer10_square.html")



I also tried it on a 32 bit system Ubuntu 10.10 and it works fine using.
Adobe Flash Player 10.3 Release Candidate (32 bit I believe) April 20th 2011.
[http://labs.adobe.com/downloads/flashplayer10-3.html](http://labs.adobe.com/downloads/flashplayer10-3.html)

---

### Post by nrundy on 2011-05-05
Yes, I have totally disabled all Extensions (like Noscript and adblock).

I am using 32-bit 10.04 Ubuntu. I have Flash-Aid with 10.3 Flash for Firefox. Obviously Chrome has flash built in.

SikeZ, sounds like it won't play for you either. So maybe it's not just my box?

---

### Post by nrundy on 2011-05-06
I've narrowed it down to affecting only my user account. I created a new user account and the video plays fine when using the newly created user account. So something got messed up with my user account. I'm guessing a setting or something is causing it?

Anybody know how I might go about finding out or discovering what is preventing the video from playing in my original user account?

---

