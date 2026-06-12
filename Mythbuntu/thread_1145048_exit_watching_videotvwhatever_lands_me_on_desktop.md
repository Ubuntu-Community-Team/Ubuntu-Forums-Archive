---
title: "exit watching video/tv/whatever lands me on desktop"
date: 2009-05-01
forum: Mythbuntu
---

### Post by joelbradshaw on 2009-05-01
I just installed a clean install of JJ9.04.
added the ubuntu desktop through control center.
removed and readded the autologin option.

Now when I watch video of any kind, when the player exits, I go back to the desktop, mythbuntu or ubuntu, not the acutal app, mythtv...

any ideas what I might have hosed up?

thanks in advance,

joelb

---

### Post by squaregoldfish on 2009-05-01
I've been seeing something similar, although it's intermittent for me. If I run MythTV from a command line, I just get a plain "Illegal instruction" message - nothing else.

Steve.

---

### Post by jaketrunk on 2009-05-01
Has the machine been used as a frontend before?  I had something similar happen when I did a clean install on frontend-only machine...  

I was able to fix the issue by resetting the screen size in Mythbuntu (Utilities/Setup -> Setup -> Screen Setup Wizard), restarting and then re-adjusting the screen size.

---

### Post by ryanjohnston on 2009-05-06
I upgraded my machine on the weekend which had been running for over 12 months without any problems.

I now have the exact same problem - after I exit anything (live tv, recorded television or video) I am dropped back to the desktop instead of the MythTV menu.

Readjusting the screen size as mentioned did not fix the problem either.

I'm still searching the net for a possible answer :(

-ryan

---

### Post by Dewey_Oxberger on 2009-05-06
I've seen several people with this problem.

Check your logs (/var/log/mythtv/mythbackend.log) and watch for any crazy errors.

I'm curious if you are having database trouble (watch for SELECT or QUERY blah blah in the log).

If you see signs of db trouble pop over to this thread and post a note:

[http://ubuntuforums.org/showthread.php?t=1146544](http://ubuntuforums.org/showthread.php?t=1146544)

---

### Post by ryanjohnston on 2009-05-06
Thanks for the quick reply. I don't seem to have any errors in my mythbackend.log but that got me thinking that I should check my other logs. Sure enough, the error appears in /var/log/messages

May  5 21:47:46 mythtv kernel: [191445.718095] mythfrontend.re[10764]: segfault at 0 ip aa234651 sp a801a37c error 6 in Vera.ttf[aa233000+11000]

I can't seem to see anything in Google for "error 6 in Vera.ttf".

-ryan

---

### Post by SiHa on 2009-05-06
"vera.ttf" is a font. Perhaps the upgrade did something funny to this font?

Does it happen as soon as you exit, i.e. before you get the "are you sure you want to exit?" dialog?

Perhaps you could look for any instances of this font in your setup pages and change to a different one?

---

### Post by dallas8101 on 2009-05-16
I have seen the very same behavior in a new clean install of Mythbuntu 9.04.  I get the following in the logs:

mythfrontend.log
2009-05-16 21:31:17.659 TV: Attempting to change from WatchingLiveTV to None

mythbackend.log
2009-05-16 21:59:33.875 TVRec(3): Changing from WatchingLiveTV to None
2009-05-16 21:59:34.167 Finished recording Unknown: channel 3124
2009-05-16 21:59:34.172 MythSocket(9b35e70:-1): writeStringList: Error, socket went unconnected.

When I press esc to exit Watch TV or Watch Video it exits the frontend and returns to the desktop.

---

### Post by roundhay on 2009-05-28
Anyone found a solution to this probelm?

There is a simlar thread [http://ubuntuforums.org/showthread.php?t=1168993](http://ubuntuforums.org/showthread.php?t=1168993)

but no solutions so far?

I have just been chekcing the bug reports and have come across a couple fo reports that may offer a solution. It might be a conflict with pulse audio that causes this, I will investigate tonight and report back if it soves the probelm

the bugs reports are:
[https://bugs.launchpad.net/mythbuntu/+bug/366002](https://bugs.launchpad.net/mythbuntu/+bug/366002)

[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/368996](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/368996)

---

### Post by roundhay on 2009-05-28
I have just tested this and uninstalling pulse audio has solved the problem. When uninstalling pulse audio synaptic also uninstalls 'unbuntu-desktop'. I'm not sure what this so you might want to check this out before doing the uninstall?

---

### Post by Eldis on 2009-06-29
> **roundhay said:**
> I have just tested this and uninstalling pulse audio has solved the problem. When uninstalling pulse audio synaptic also uninstalls 'unbuntu-desktop'. I'm not sure what this so you might want to check this out before doing the uninstall?

I can confirm that this fixed the issue for me. thanks

---

### Post by mycroes on 2009-08-09
Works for me too. Too bad mythtv is so broken that things like this affect simple UI behaviour... Let's hope there will be a better alternative soon.
Regards,

Michael

---

