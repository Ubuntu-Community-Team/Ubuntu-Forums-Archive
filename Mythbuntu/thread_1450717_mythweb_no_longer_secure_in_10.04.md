---
title: "mythweb no longer secure in 10.04"
date: 2010-04-09
forum: Mythbuntu
---

### Post by dannyboy79 on 2010-04-09
i upgraded my mythbuntu jaunty install into lucid and just happened to notice today that I can access it from work (first time using this computer so the password has never been cached) and it did NOT ask me for a password. now I am scared crapless that someone will find it and start deleting my recordings before I can get home and fix this issue. anyone know why this would've happened? i am not ssh'd into it, so I can't tell you anything about the machine but i'll be back to this post later after work. thanks so much if anyone has any insight.

---

### Post by xinix on 2010-04-09
try ```
sudo dpkg-reconfigure mythweb
``` you should be prompted to set a password.

---

### Post by novellahub on 2010-04-09
You can also set a password for Mythweb in the Mythtbuntu Control Centre.  The password gets wiped out currently during a upgrade.

---

### Post by dannyboy79 on 2010-04-09
> **novellahub said:**
> You can also set a password for Mythweb in the Mythtbuntu Control Centre.  The password gets wiped out currently during a upgrade.

WOW, why would they do that?????? does it say it in the documentation? i luckily noticed it only a few days after the upgrade. I could've been really messed up by someone and they couldn've totally borked my mythtv setup easily through mythweb. 
Luckily my girlfriend was home and I walked her though opening a terminal, and entering 
sudo service apache2 stop
all is safe temporarily. i normally have my memory stick with putty and my server key on it, but I forgot it today.
NOW I realize why I was able to watch the asx stream in vlc on my other ubuntu computer. I thought they maybe fixed the authentification issue when trying to stream from a password protected webserver.

---

### Post by tgm4883 on 2010-04-09
Is this still happening? Do you guys have auto-builds enabled?

[https://bugs.edge.launchpad.net/mythbuntu/+bug/521269](https://bugs.edge.launchpad.net/mythbuntu/+bug/521269)

---

### Post by dannyboy79 on 2010-04-09
> **tgm4883 said:**
> Is this still happening? Do you guys have auto-builds enabled?

[https://bugs.edge.launchpad.net/mythbuntu/+bug/521269](https://bugs.edge.launchpad.net/mythbuntu/+bug/521269)

when i was running mythbuntu 9.10, yes, i enabled the mythbuntu-builds repo or whatever you call them. when I did a update-manager -d though, i figured it would've commented out any 3rd party repos. so i am guessing that the new mythweb upgrades came from teh main lucid repo. not sure if I have answered your question.

---

### Post by tgm4883 on 2010-04-09
> **dannyboy79 said:**
> when i was running mythbuntu 9.10, yes, i enabled the mythbuntu-builds repo or whatever you call them. when I did a update-manager -d though, i figured it would've commented out any 3rd party repos. so i am guessing that the new mythweb upgrades came from teh main lucid repo. not sure if I have answered your question.

Ok, unless you reactivated auto-builds they are disabled. Please enable your mythweb authentication then update to the latest auto-builds and let me know if that issue is resolved.

---

### Post by dannyboy79 on 2010-04-09
> **tgm4883 said:**
> Ok, unless you reactivated auto-builds they are disabled. Please enable your mythweb authentication then update to the latest auto-builds and let me know if that issue is resolved.

well, that doesn't answer my question though. is this normal when upgrading mythweb that it removes authentification of my apache2 server?

---

### Post by tgm4883 on 2010-04-09
> **dannyboy79 said:**
> well, that doesn't answer my question though. is this normal when upgrading mythweb that it removes authentification of my apache2 server?

Is it normal? Yes. Is it suppose to happen? No. Please check the bug report I posted [https://bugs.edge.launchpad.net/mythbuntu/+bug/521269](https://bugs.edge.launchpad.net/mythbuntu/+bug/521269)

---

### Post by dannyboy79 on 2010-04-09
> **tgm4883 said:**
> Is it normal? Yes. Is it suppose to happen? No. Please check the bug report I posted [https://bugs.edge.launchpad.net/mythbuntu/+bug/521269](https://bugs.edge.launchpad.net/mythbuntu/+bug/521269)

well you just got done saying that if I didn't re-enable the mythbuntu daily builds repo, there would be no way that it should have reset my password for mythweb. I upgraded from .22-fixes to .23-fixes and also upgraded to Lucid. During the lucid upgrade BUT before the myth stuff upgrade, it would've disabled the mythbuntu daily builds repo. So why does an upgrade cause the password to be reset? and please don't say because of the mythbuntu daily builds repo as we have already established that it would've been disabled.

---

### Post by tgm4883 on 2010-04-09
> **dannyboy79 said:**
> **well you just got done saying that if I didn't re-enable the mythbuntu daily builds repo, there would be no way that it should have reset my password for mythweb.** I upgraded from .22-fixes to .23-fixes and also upgraded to Lucid. During the lucid upgrade BUT before the myth stuff upgrade, it would've disabled the mythbuntu daily builds repo. So why does an upgrade cause the password to be reset? and please don't say because of the mythbuntu daily builds repo as we have already established that it would've been disabled.

Where did I say that?


Ok, let me repraise this.


> Ok, unless you reactivated auto-builds then the auto-builds are disabled. Please enable your mythweb authentication, then update to the latest auto-builds. This will let me know if I have fixed the issue or if it is still a problem

This looks to be a bug in the packaging. The issue is present in the auto-builds (for both 0.22 and 0.23) and likely in the version that was in lucid when you upgraded. I have pushed code that I believe fixes this issue, so please enabled authentication and then upgrade your packages using the autobuilds. The result should be that your authentication is still enabled.

---

### Post by tgm4883 on 2010-04-09
Ok, I was just able to test the PPA with 0.23 and the issue still exists. I think I have a fix for it really this time, but I will need some time to test it.

---

### Post by dannyboy79 on 2010-04-10
well, I secured my lucid mythweb .23-fixes install. I went to renable the auto builds using sudo dpkg-reconfigure mythbuntu-repos and check out the picture. how do I know which is from fixes and which is from development?

[IMG]http://img638.imageshack.us/img638/5433/screenshotcw.png[/IMG]

I choose the top .23 hoping for blind luck! i'd rather be running from upstream -fixes and not trunk because I don't want to deal with any breakage. i have a big family who depend on the DVR just working 
anyway, after I renabled the repos, i did an update and upgrade and noticed that it was going to upgrade a lot of mythtv stuff, I let it, then tried to get back into mythweb from another machine and sure enough, it removed my password AGAIN. no authentification required. so I had to reset the password again. what file is being overwritten?

---

### Post by tgm4883 on 2010-04-10
Did you even read the post before yours? Let me quote it for you.

> **tgm4883 said:**
> Ok, I was just able to test the PPA with 0.23 and the issue still exists. I think I have a fix for it really this time, but I will need some time to test it.

As you can see, I tested it 5 hours before you posted. Had you read my post you could have saved yourself the trouble of testing it yourself since I say it is still broken.


As for the double 0.23, there is only a single 0.23 PPA so selecting either one will give you the same one. Since 0.23 is about to be released and has already been branched upstream, trunk would be known as 0.24. Once I update the lucid auto-builds package you will see 0.23 and 0.24 in your options there.

---

### Post by nickrout on 2010-04-10
> **dannyboy79 said:**
> well, I secured my lucid mythweb .23-fixes install. I went to renable the auto builds using sudo dpkg-reconfigure mythbuntu-repos and check out the picture. how do I know which is from fixes and which is from development?


I choose the top .23 hoping for blind luck! i'd rather be running from upstream -fixes and not trunk because I don't want to deal with any breakage. i have a big family who depend on the DVR just working 
anyway, after I renabled the repos, i did an update and upgrade and noticed that it was going to upgrade a lot of mythtv stuff, I let it, then tried to get back into mythweb from another machine and sure enough, it removed my password AGAIN. no authentification required. so I had to reset the password again. what file is being overwritten?

really you should avoid exposing your mythweb to the internet. Use an ssh encrypted tunnel. From work/windows I ssh in using putty, which I have set to tunnel port 80 on my myth machine to a port on my windows box (1313 I think). I then go into my browser and go to the url localhost:1313.

It is FAR more secure than apache authentication!

---

### Post by dannyboy79 on 2010-04-12
> **nickrout said:**
> really you should avoid exposing your mythweb to the internet. Use an ssh encrypted tunnel. From work/windows I ssh in using putty, which I have set to tunnel port 80 on my myth machine to a port on my windows box (1313 I think). I then go into my browser and go to the url localhost:1313.

It is FAR more secure than apache authentication!
thanks for the revolutionary idea, you should patent it.

---

