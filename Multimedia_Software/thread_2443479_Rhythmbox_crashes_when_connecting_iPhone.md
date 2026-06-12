---
title: "Rhythmbox crashes when connecting iPhone"
date: 2020-05-16
forum: Multimedia Software
---

### Post by drjdmartin on 2020-05-16
Hi,

Every time I plug my iPhone XS into my PC Rhythmbox immediately closes. I'd like to use Rhythmbox to copy music to my iPhone rather than using iTunes in my Windows 10 Virtualbox machine.

Any ideas? I am using a Dell Optiplex 7010 with Ubuntu 20.04.

Thanks

---

### Post by CelticWarrior on 2020-05-16
Welcome.

Anything related to that company's products in Ubuntu is a "best effort" kind of situation and an "hit & miss" with a lot more misses than hits.

Please try opening Rhythmbox in terminal and then do the rerst of the operations as usual. This will allow you to see, eventually, some error messages that may inform about what's going wrong.

---

### Post by drjdmartin on 2020-05-17
Thanks CelticWarrior for your sound and simple advice - I should know to do this really. I do appreciate that particular company have a tendency to make things difficult - I'm just so close to cutting the cord from Windows completely... Ultimately Virtualbox works very well.

Here is the error I get when Rhythmbox exits:

```
Rhythmbox:ERROR:rb-ipod-helpers.c:359:rb_ipod_helpers_is_ipod: assertion failed: (strlen (uri) >= 46)
Bail out! Rhythmbox:ERROR:rb-ipod-helpers.c:359:rb_ipod_helpers_is_ipod: assertion failed: (strlen (uri) >= 46)
Aborted (core dumped)
```

I'll do some googling - I've got the core dump to hand as well if that is useful.

Thanks again

---

### Post by drjdmartin on 2020-05-17
OK so the complete set of errors is actually:

```
(rhythmbox:4623): Gtk-WARNING **: 18:45:46.862: actionhelper: action app.play-repeat can't be activated due to parameter type mismatch (parameter type NULL, target type b)


(rhythmbox:4623): Gtk-WARNING **: 18:45:46.862: actionhelper: action app.play-shuffle can't be activated due to parameter type mismatch (parameter type NULL, target type b)

***

Rhythmbox:ERROR:rb-ipod-helpers.c:359:rb_ipod_helpers_is_ipod: assertion failed: (strlen (uri) >= 46)
Bail out! Rhythmbox:ERROR:rb-ipod-helpers.c:359:rb_ipod_helpers_is_ipod: assertion failed: (strlen (uri) >= 46)
Aborted (core dumped)
```

Looks like this has been reported here [https://gitlab.gnome.org/GNOME/rhythmbox/issues/1760](https://gitlab.gnome.org/GNOME/rhythmbox/issues/1760)

---

### Post by CelticWarrior on 2020-05-17
Yes, also here: [https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/1864178](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/1864178)

---

### Post by DuckHook on 2020-05-17
Please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

Re: your problem.

It looks like you will need to wait for the devs to fix this bug. If you could add your name to the bug report that you and CelticWarrior linked to, it will confirm to the devs that this effects multiple users and possibly elevate the triage level when they decide on fix order.

Good to know that you at least have a workaround for now, even if it does rely on a VM. Further to what CelticWarrior stated, it may be wise to keep your Windows VM permanently even if it is for the sole purpose of iTunes. When I owned an iPhone, the only way to get everything working was with iTunes. Even on occasions when Rhythmbox worked, it was frustratingly spotty and would break with every iOS upgrade.

---

### Post by drjdmartin on 2020-05-17
Thanks - will post the code properly next time. I've added my name to the bug list so let's hope the devs can help.

---

### Post by yancek on 2020-05-18
A method I have used to copy music to/from my iphone is explained at the link below.  Download VLC for mobile from the App Store and follow the steps listed.  The post is old but I used it recently and it worked for me on an iphone 7.  The interface on the newer versions is different but the options should be obvious. 

 [https://www.howtogeek.com/169251/how-to-add-files-to-vlc-on-your-iphone-without-itunes/](https://www.howtogeek.com/169251/how-to-add-files-to-vlc-on-your-iphone-without-itunes/)

---

### Post by drjdmartin on 2020-05-18
Thanks - that is a good sidestep and will be quite robust given you are just moving stuff about over Wifi and no wired connections are involved...

I note this is now in the Network menu in the latest VLC for iPhone - you just switch on sharing via Wifi and use the IP address of the phone in your browser. Then you drag and drop. Easy peasy.

---

