---
title: "Thunderbird problem 20.04"
date: 2020-05-24
forum: Multimedia Software
---

### Post by aughey on 2020-05-24
I went to send an email using Thunderbird. It kept asking me for my password. I tried every way I could think of to make it use my password without me having to type it in every single time but I just could not find anything that would allow me to. Google was no help at all. I got so fed up I decided to uninstall it and reinstall. I clicked on Ubuntu Sotware briefcase. The Thunderbird there told me it was not installed. I installed this version and now I have two thunderbirds on my laptop. The newer version allowed me to enter my password and I no longer have to type it in every time. Is this a bug?

---

### Post by ra7411 on 2020-05-24
I remember having that problem a few years ago. No guarantee, maybe this note I made then will solve it:

>Thunderbird password entry not showing &#8221;save pw&#8221; &#8211; close TBird, file mgr to .thunderbird, xxx.default, file  prefs.js, find the following line: user_pref("signon.rememberSignons", false); chg to true <

Good luck

---

### Post by DuckHook on 2020-05-24
You have likely installed T-bird from two different repos. The T-bird that comes up in the Software Centre is the Snap version whereas the T-Bird originally installed is the version in Ubuntu's official repo. Your confusion is understandable. This dichotomy is a side effect of Canonical's decision to promote Snaps. Unless you pay careful attention to the source, Snaps will get substituted when you assume you are dealing with the classic repo.

You have two choices:

[LIST=1]
[*]Use the Snap. It is now installed so it's a fait accompli and it works. On the other hand, it will require you to repopulate T-Bird with all of your existing e-mails and add all of your extensions/customizations. If you have a fast connection and don't mind going to the trouble, then it may be a viable solution. It is also not the "official" version so you've added complexity and attack surface to your base install.
[*]Delete the Snap and continue trying to fix the old, default T-bird. This will keep your system in its default configuration (it's always a good idea to avoid unnecessary complexity), but you will then have to continue chasing down the T-bird problem.
[/LIST]
I think you should decide on the above two options before trying to proceed with any further fix.

---

### Post by aughey on 2020-05-25
The version I had bother with was the original one installed by default when I used rthe installation ISO. The 2nd version was one I found using the orange brief case ubuntu software. I was expecting it to remove the original one and I was surprised when it behaved as if thunderbird was not installed on my system. SEE SCREENSHOT


[https://photos.app.goo.gl/MB3NUuESSKfpZWo98](https://photos.app.goo.gl/MB3NUuESSKfpZWo98)

---

### Post by DuckHook on 2020-05-27
After going back through this thread, it occurs to me that you may still be confused about your system.

You now have two TBs installed. One is a .deb pkg tied to the regular repo; the other is a snap tied to the snap store. My previous post invited you to consider your two options in light of this state of affairs. I did not get the impression from your last post that you clearly understood the current state of your system.

Please decide which of the two choices you would like to pursue.

---

### Post by walts48 on 2020-05-28
> **ra7411 said:**
> I remember having that problem a few years ago. No guarantee, maybe this note I made then will solve it:

>Thunderbird password entry not showing ”save pw” – close TBird, file mgr to .thunderbird, xxx.default, file  prefs.js, find the following line: user_pref("signon.rememberSignons", false); chg to true <

Good luck

Why do it the hard way?

In my Thunderbird 68.8.0, I can go to Preferences > Advanced, click the Config Editor button, type "signons" (without quotes) into the search bar and "signon.rememberSignons" is one of the two results. Already set to "true" because I enable "Remember password" when creating my accounts.

If set to "false" just right-click and click **Toggle**.

---

