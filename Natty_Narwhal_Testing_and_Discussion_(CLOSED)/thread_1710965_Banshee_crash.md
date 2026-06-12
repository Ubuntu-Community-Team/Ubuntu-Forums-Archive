---
title: "Banshee crash"
date: 2011-03-20
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ubuntu27 on 2011-03-20
Does any of you experience Banchsee crash after installing and enabling the **Clutter-flow** plugin?

OS: Ubuntu Natty

---

### Post by mc4man on 2011-03-20
It works fine here on a straight up tester using the natty repo packages and also on a 'using' install that has the [banshee-daily ppa ]("https://launchpad.net/~banshee-team/+archive/banshee-daily")versions

---

### Post by PaulW2U on 2011-03-20
> **ubuntu27 said:**
> Does any of you experience Banchsee crash after installing and enabling the **Clutter-flow** plugin?

Not a crash here but the sound mutes and I can't turn it on again until I disable the plug-in. Most of the entries in the Edit menu disappear too. Restarting Banshee with the plug-in enabled seems to work correctly but when trying to close Banshee the global menu entries disappeared. :confused:

I don't know how much of this is due to the plug-in though. Banshee has been one of the most troublesome applications I've come across as it has refused to run at all on Lucid or Maverick or has crashed as soon as you try to navigate the various options.

---

### Post by mc4man on 2011-03-20
> **PaulW2U said:**
> Not a crash here but the sound mutes and I can't turn it on again until I disable the plug-in.

there is a current sound mute bug, don't see anything additional there related to the plugin.
Generally this bug only affects banshee  on the first use per session
[https://bugs.launchpad.net/indicator-sound/+bug/730925](https://bugs.launchpad.net/indicator-sound/+bug/730925)

ubuntu27 - if you're using the natty repo banshee maybe try opening w/ banshee --debug and see what shows

---

### Post by PaulW2U on 2011-03-20
> **mc4man said:**
> there is a current sound mute bug, don't see anything additional there related to the plugin.
Generally this bug only affects banshee  on the first use per session
[https://bugs.launchpad.net/indicator-sound/+bug/730925](https://bugs.launchpad.net/indicator-sound/+bug/730925)
Noted. What I saw, once the plug-in had been enabled, was the sound indicator simply not not working. The menu did not drop down at all. This seems to be in addition to the volume resetting to zero as in bug #730925.

---

### Post by ubuntu27 on 2011-03-21
Hmm...No one in ubuntforums is experiencing this problem? [Someone]("http://askubuntu.com/questions/11986/banshee-with-enabled-clutterflow-plugin-crashes") at AskUbuntu has the same problem as me.

On another note, did you guys notice that the lyrics extension has become dependent on Clutter-flow plugin?


```
sudo apt-get install banshee-extension-lyrics
[sudo] password for ubuntu27: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  lib32bz2-1.0 lib32ncurses5 ia32-libs libc6-i386 lib32gcc1 lib32asound2
  lib32z1 lib32stdc++6 lib32v4l-0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  banshee-extension-clutterflow
The following NEW packages will be installed:
  banshee-extension-clutterflow banshee-extension-lyrics
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 290 kB of archives.
After this operation, 844 kB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

It used to not be like this until a few days ago.

---

### Post by mc4man on 2011-03-21
> **ubuntu27 said:**
> Hmm...No one in ubuntforums is experiencing this problem? [Someone]("http://askubuntu.com/questions/11986/banshee-with-enabled-clutterflow-plugin-crashes") at AskUbuntu has the same problem as me.

You did notice that post is 4 months ago, likely an older banshee, not on natty
Anyway the suggestion are solid - did you try?
Or to eliminate or point to your local (home dir) settings/files you can temporally create a new user, log out and in to that user and see how banshee works there

> On another note, did you guys notice that the lyrics extension has become dependent on Clutter-flow plugin?
It's an install dependency, not a 'use' dependency, you don't have to have the clutterflow plugin enabled to use the lyrics plugin

---

### Post by gnomeuser on 2011-03-21
Banshee crashed?

Please follow the instructions here to obtain a Debug log

[http://live.gnome.org/Banshee/CommonQuestions/Logs](http://live.gnome.org/Banshee/CommonQuestions/Logs)

Then go to [www.banshee.fm/file-bugs](www.banshee.fm/file-bugs) and let us know it is broken.

That being said, we only just got clutter# on Debian/Ubuntu, it has been underexposed for quite a while. Getting all the bugs worked out of the platform and the extension is likely going to take some time. Please do file bugs, let us know when it fails.

hugs and love, your friendly Banshee peeps

---

### Post by Jim_in_Omaha on 2011-03-24
> **ubuntu27 said:**
> Does any of you experience Banchsee crash after installing and enabling the **Clutter-flow** plugin?

OS: Ubuntu Natty

Same here on 10.10. Started a few days ago I believe after an update. But I usually wait for updates so I do not know. I will post back if I fix it.

---

### Post by Hairy_Palms on 2011-03-24
i get major problems with the clutterflow plugin installed too, not crashes, just major freezes on every song change.

---

