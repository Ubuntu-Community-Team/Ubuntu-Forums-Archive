---
title: "YouTube videos play, but CNN videos crash Firefox"
date: 2010-05-18
forum: Multimedia Software
---

### Post by rencemc on 2010-05-18
Ever since I loaded Ubuntu 10.04, 64-bit, some website videos crash Firefox. At first it was also happening in YouTube, then I updated the Flash player and YouTube videos started working. But CNN videos crash Firefox. I tried putting about:crashes in the URL and it said that the URL doesn't exist - so I could not view any crash information. If I do about:plugins it shows Flash player 10.0 r45. All videos on sites work using the Chrome browser.

---

### Post by rencemc on 2010-05-18
I managed to view the following errors via the Firefox error console:

Warning: Unknown property 'border-radius'.  Declaration dropped.
Source File: [http://www.ubuntu.com/](http://www.ubuntu.com/)
Line: 100

Warning: Unknown property 'background-potion'.  Declaration dropped.
Source File: [http://www.ubuntu.com/](http://www.ubuntu.com/)
Line: 105

Warning: Error in parsing value for 'font-size'.  Declaration dropped.
Source File: [http://www.ubuntu.com/sites/all/themes/ubuntu09/styles/classes.css?3](http://www.ubuntu.com/sites/all/themes/ubuntu09/styles/classes.css?3)
Line: 107

Warning: Unknown property 'line-hieght'.  Declaration dropped.
Source File: [http://www.ubuntu.com/](http://www.ubuntu.com/)
Line: 400

There are more similar errors recorded.

---

### Post by WinterRain on 2010-05-18
How did you install flash?

---

### Post by rencemc on 2010-05-18
I just re-installed per those instructions and the same thing is happening.

---

### Post by lovinglinux on 2010-05-18
Check if you have libmoon installed and remove it. It is causing such problems, although it doesn't show up in your error report.

Also see [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by rencemc on 2010-05-18
lovingLinux - I checked package manager - libmoon is not installed

---

### Post by lovinglinux on 2010-05-18
> **rencemc said:**
> lovingLinux - I checked package manager - libmoon is not installed

Get Firefox 3.6.4. It should not crash, since it has plugin isolation feature.

---

### Post by den2042 on 2010-12-08
Simply try in terminal
sudo firefox

---

### Post by lovinglinux on 2010-12-08
> **den2042 said:**
> Simply try in terminal...

Please remove your suggestion. That will cause Firefox to start with root privileges, but still using the user profile, which will change the ownership of ~/.mozilla folder and cause all sorts of troubles.

Additionally, running Firefox with root privileges is a big security risk.

If you have done that already, then fix your profile ownership. To do that, see the [first item on this list]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html").

---

### Post by thatguruguy on 2010-12-08
> **den2042 said:**
> Simply try in terminal
sudo firefox

Wow.  What an incredibly bad idea.

---

