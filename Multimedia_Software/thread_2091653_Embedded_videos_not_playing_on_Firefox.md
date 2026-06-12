---
title: "Embedded videos not playing on Firefox :/"
date: 2012-12-05
forum: Multimedia Software
---

### Post by Zvikatron on 2012-12-05
Hi everyone,

I've been having a strange problem ever since an update from several days ago.
Embedded videos do not play on some sites. 
Especially Youtube videos, but also others. Strangely, embedded vids on facebook do play, but on other sites they don't and I need to open the video on youtube.

I am using Ububtu 12.04 lts and Firefox for a browser. On chromium it works fine

Has anyone else encountered this problem?

---

### Post by evilsoup on 2012-12-05
You do have {l,x,k,}ubuntu-restricted-extras installed, right?

---

### Post by Zvikatron on 2012-12-05
> **evilsoup said:**
> You do have {l,x,k,}ubuntu-restricted-extras installed, right?

Not sure... (Fry meme)
How do I check this?

---

### Post by Zvikatron on 2012-12-05
> **Zvikatron said:**
> Not sure... (Fry meme)
How do I check this?

Ok, Got it.
used: 
```
dpkg --get-selections
``` and found that I have "ubuntu-restricted-addons" installed. I guess it's the same thing

---

### Post by evilsoup on 2012-12-05
That may well be the same thing, but since you're OK with the command line & to be on the safe side, try
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Zvikatron on 2012-12-06
> **evilsoup said:**
> That may well be the same thing, but since you're OK with the command line & to be on the safe side, try
```
sudo apt-get install ubuntu-restricted-extras
```

Thanks, I did that and this message appeared in the terminal (terms of use for the package): 

The thing now is that I cannot accept the terms of use. 
The <ok> won't click, ENTER doesn't work either or anything else I try, and I am afraid that the process will not complete without this.

---

### Post by Zvikatron on 2012-12-06
I closed and reopened the terminal, and got the following message when I tried to repeat the installation:

---

### Post by vasa1 on 2012-12-06
What about hitting tab?

Edit: in response to the eula post!

---

### Post by vasa1 on 2012-12-06
Tab, then enter according to this:
[http://askubuntu.com/questions/16225/how-can-i-accept-the-agreement-in-a-terminal-like-for-ttf-mscorefonts-installer](http://askubuntu.com/questions/16225/how-can-i-accept-the-agreement-in-a-terminal-like-for-ttf-mscorefonts-installer)

---

### Post by Zvikatron on 2012-12-06
> **vasa1 said:**
> What about hitting tab?
Edit: in response to the eula post!

Thanks
Now I cannot do it because of that strange "unable to unlock the administration directory.." problem.

I can't go 'sudo' now

---

### Post by Zvikatron on 2012-12-06
> **vasa1 said:**
> Tab, then enter according to this:
[http://askubuntu.com/questions/16225/how-can-i-accept-the-agreement-in-a-terminal-like-for-ttf-mscorefonts-installer](http://askubuntu.com/questions/16225/how-can-i-accept-the-agreement-in-a-terminal-like-for-ttf-mscorefonts-installer)

tyvm VASA1, I will do that as soon as I'll be able to :)

---

### Post by Zvikatron on 2012-12-06
> **evilsoup said:**
> That may well be the same thing, but since you're OK with the command line & to be on the safe side, try
```
sudo apt-get install ubuntu-restricted-extras
```

I finally managed to install the restricted extras package :)

Unfortunately, it didn't solve the problem I've been having 
Anybody has other thoughts? :?

---

### Post by vasa1 on 2012-12-07
> **Zvikatron said:**
> Hi everyone,

I've been having a strange problem ever since an update from several days ago.
Embedded videos do not play on some sites. 
Especially Youtube videos, but also others. Strangely, embedded vids on facebook do play, but on other sites they don't and I need to open the video on youtube.

I am using Ububtu 12.04 lts and Firefox for a browser. On chromium it works fine

Has anyone else encountered this problem?
Which add-ons (extensions) have you installed? Perhaps, one of them is the culprit? What happens if you try with extensions disabled?

---

### Post by Zvikatron on 2012-12-07
> **vasa1 said:**
> Which add-ons (extensions) have you installed? Perhaps, one of them is the culprit? What happens if you try with extensions disabled?

That wasn't it either :)
Strangely, other types of videos work, for example: vimeo.
is there some kind of difference between the embedded vimeo and YT vids?

---

### Post by monkeybrain2012 on 2012-12-07
What do you mean by they don't work? Nothing happens or do they crash? 

Are you using a Nvidia card?

---

### Post by Zvikatron on 2012-12-07
> **monkeybrain2012 said:**
> What do you mean by they don't work? Nothing happens or do they crash? 

Are you using a Nvidia card?

I mean they don't play...
But this only happens on firefox and started only a couple of weeks ago, so I don't think thr graphics cars has anything to do with it (ATI Radeon) :-k

---

### Post by Zvikatron on 2012-12-07
It's strange that no one else seems to have the same problem... I must be doing something wrong.. :-k

---

### Post by monkeybrain2012 on 2012-12-07
I don't know if this makes any sense but it doesn't hurt to try. Go to a flash video and click it and then in the settings try changing the hardware acceleration option (disable --> enable or the other way around depending on the default) and see if it makes a difference.

---

### Post by verzx on 2012-12-07
Try this:

```
sudo apt-get update
```
```
sudo apt-get install flashplugin-installer
```
```
sudo apt-get update
```

In that order, if that doesn't work check for updates in update manager and install them and then restart. :)

---

### Post by Zvikatron on 2012-12-07
> **monkeybrain2012 said:**
> I don't know if this makes any sense but it doesn't hurt to try. Go to a flash video and click it and then in the settings try changing the hardware acceleration option (disable --> enable or the other way around depending on the default) and see if it makes a difference.
Ok, I think you are on to something here, because after going into 'settings' the setting window froze, I mean, I was not able to click on any of the options, navigate, or even close it (when I refreshed the page it disappeared).
Maybe I need to reinstall flash player..? How do I do that? :P

---

### Post by Zvikatron on 2012-12-07
> **Zvikatron said:**
> ....
Maybe I need to reinstall flash player..? How do I do that? :P

> **verzx said:**
> Try this:

```
sudo apt-get update
``````
sudo apt-get install flashplugin-installer
``````
sudo apt-get update
```In that order, if that doesn't work check for updates in update manager and install them and then restart. :)

I guess that was the answer to my question :)
Didn't work though.

I must have had something to do with a recent update, that updated browser stuff as well..

---

### Post by monkeybrain2012 on 2012-12-07
> **Zvikatron said:**
> Ok, I think you are on to something here, because after going into 'settings' the setting window froze, I mean, I was not able to click on any of the options, navigate, or even close it (when I refreshed the page it disappeared).
Maybe I need to reinstall flash player..? How do I do that? :P
Opps, they still haven't fixed this? This is an unrelated Unity bug and a work around would be to log into classic desktop or gnome-shell do it there. You can add an "affect me too" to the bug report but it doesn't look like they are doing anything about it. :(


[https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/865672](https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/865672)

---

### Post by Zvikatron on 2012-12-07
> **monkeybrain2012 said:**
> Opps, they still haven't fixed this? This is an unrelated Unity bug and a work around would be to log into classic desktop or gnome-shell do it there. You can add an "affect me too" to the bug report but it doesn't look like they are doing anything about it. :(


[https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/865672](https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/865672)

Thank you!

---

### Post by Zvikatron on 2012-12-13
Ok, something weird that I just found out: the problem does not exist when I am in "Private Browsing". 
The exact same video will play on private browsing, and not when I use the browser regularly.

:-k

---

### Post by evilsoup on 2012-12-13
Private browsing creates a temporary blank firefox profile, so... maybe try clearing your browsing history (ctrl+shift+delete). There are also add-ons to clear your flash cache, try that too.

---

### Post by Zvikatron on 2012-12-13
> **evilsoup said:**
> Private browsing creates a temporary blank firefox profile, so... maybe try clearing your browsing history (ctrl+shift+delete). There are also add-ons to clear your flash cache, try that too.

It worked!

:)

finally... (I feel kinda silly though :p)

---

