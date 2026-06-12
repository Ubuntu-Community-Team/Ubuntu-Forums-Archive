---
title: "Failed to load session &quot;ubuntu&quot;"
date: 2011-04-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by osarusan on 2011-04-01
I just upgraded to the Natty  beta and I'm getting this error message every time I try to log in.

Failed to load session "ubuntu"

I have tried using every session available: Ubuntu, Classic Ubuntu, Unity-2d, and Gnome Shell. The only one that allows me to log in is Gnome Shell, but it doesn't actually load Gnome Shell; it loads a gnome panel, but compositing/compiz doesn't work.

I'm so confused, and I have no idea how to fix this or what is causing it. I would like to be able to try out Unity, but none of the sessions work except for this false Gnome Shell session.

Any ideas?

---

### Post by dino99 on 2011-04-01
check if compiz is to be blamed: uninstall all related compiz packages from synaptic, then retry after reboot

---

### Post by osarusan on 2011-04-01
No luck.

I tried uninstalling them all, and the same error came for all 3 sessions; Ubuntu, Ubuntu Classic, and Unity 2d.

---

### Post by Hakunka-Matata on 2011-04-01
[LIST]
[*]can you get to the command line?  If so I would run the updates, there are a slew of them first time after you install?
[*]did it appear to install correctly?
[*]I am running natty 11.04-amd64-Alpha3-Desktop installed about 2 weeks ago.  upon startup, I get several crashes of something tied in to Compiz, but it's able to ignore and keep going, it's getting better after each new set of updates, and there are many and often
[*]If you can't get it going, I'd reinstall, HASH check?  Check disc for defects?
[*]Good Luck, it's a killer release so far, I LOVE it.
[/LIST]

---

### Post by osarusan on 2011-04-01
The install ran fine as far as I can tell... I can access the command line, but I really don't know what to do from there to fix the sessions.

Is there a way to re-run the installation other than starting from scratch?

---

### Post by osarusan on 2011-04-01
Well, I have no idea what caused this... but it seems to have been some kind of package dependency problem. The packages were all a mess and I ended up just uninstalling and reinstalling everything and now it's working.

---

### Post by aethralis on 2011-04-03
Did you reinstall the whole natty system from live cd? I'm having namely exactly the same problem and would like to solve it without resorting to reinstalling the whole system...

I guess the gnome-shell ppa is here to blame, this namely started after I added the ppa and installed gnome-shell from there... ppa-purge won't help here, already tried it.

---

### Post by osarusan on 2011-04-03
I reinstalled the whole system from the net, but I'm sure the livecd would work as well. I actually reinstalled it package by package, rather than doing a fresh install.

What happened was when I loaded synaptic and looked at the package origins, nearly all of the packages were set to "locally installed" rather than automatic. So when I tried to install or uninstall anything that was linked to those packages, it failed. Thus I couldn't reinstall ubuntu-desktop, or any of the gnome packages, and so on.

I think I may have had the gnome-shell PPA enabled at some point before this problem occurred, but I can't remember now. I am not using now, and I don't think a will now that you've pointed it out.

Go into synaptic and check the packages that are locally installed. Try uninstalling all of them. Then reboot to a shell (since uninstalling them will probably get rid of synaptic and almost every other package on your system) and load aptitude from a shell, install ubuntu-desktop and let it finish all the dependencies. After I did that, I was able to get into gnome.

I still had a few residual "local" packages that didn't get properly uninstalled, but I manually purged them and reinstalled then after that, and everything works fine now.

---

### Post by Hakunka-Matata on 2011-04-04
Oh lah lah, well done.
and good plausible explanations, I likee

---

### Post by jbicha on 2011-04-08
The Gnome 3 PPA is not recommended yet if you are not willing for your computer to be broken.

gnome-session in the PPA does not work correctly yet. It allows me to login to Gnome Shell but not Ubuntu (Unity), Ubuntu Classic or Unity 2d. To fix that I had to

[LIST=1]
[*]Disable the PPA
[*]Remove gnome-session
[*]Re-install ubuntu-desktop and whatever else may have been autoremoved in step 2
[*]Re-enable the PPA and don't upgrade gnome-session. It's not necessary to have the gnome3 gnome-session to use Gnome Shell.
[/LIST]
I'll try to post here again when the gnome3 gnome-session is working again.

---

### Post by cecilpierce on 2011-04-08
> **jbicha said:**
> The Gnome 3 PPA is not recommended yet if you are not willing for your computer to be broken.

gnome-session in the PPA does not work correctly yet. It allows me to login to Gnome Shell but not Ubuntu (Unity), Ubuntu Classic or Unity 2d. To fix that I had to

[LIST=1]
[*]Disable the PPA
[*]Remove gnome-session
[*]Re-install ubuntu-desktop and whatever else may have been autoremoved in step 2
[*]Re-enable the PPA and don't upgrade gnome-session. It's not necessary to have the gnome3 gnome-session to use Gnome Shell.
[/LIST]
I'll try to post here again when the gnome3 gnome-session is working again.

I just upgraded one of my Natty's to Gnome3 and when I rebooted I get a black screen and a msg (failed to load session 'ubuntu') and I goto vt1 and kill gdm but it won't let me start unless I do sudo startx, then it works pretty good! Any ideas or suggestions ?
Attached Thumbnails
Click image for larger version Name: Screenshot.jpg Views: 23 Size: 21.6 KB ID: 188466   Click image for larger version Name: Screenshot-2.jpg Views: 25 Size: 34.0 KB ID: 188467  
Last edited by cecilpierce; 6 Hours Ago at 08:52 AM.. Reason: p.s. if I try to login as a user it says not authorised

---

### Post by cecilpierce on 2011-04-08
> **jbicha said:**
> The Gnome 3 PPA is not recommended yet if you are not willing for your computer to be broken.

gnome-session in the PPA does not work correctly yet. It allows me to login to Gnome Shell but not Ubuntu (Unity), Ubuntu Classic or Unity 2d. To fix that I had to

[LIST=1]
[*]Disable the PPA
[*]Remove gnome-session
[*]Re-install ubuntu-desktop and whatever else may have been autoremoved in step 2
[*]Re-enable the PPA and don't upgrade gnome-session. It's not necessary to have the gnome3 gnome-session to use Gnome Shell.
[/LIST]
I'll try to post here again when the gnome3 gnome-session is working again.

I just upgraded one of my Natty's to Gnome3 and when I rebooted I get a black screen and a msg (failed to load session 'ubuntu') and I goto vt1 and kill gdm but it won't let me start unless I do sudo startx, then it works pretty good! Any ideas or suggestions ?
Attached Thumbnails
Click image for larger version Name: Screenshot.jpg Views: 23 Size: 21.6 KB ID: 188466   Click image for larger version Name: Screenshot-2.jpg Views: 25 Size: 34.0 KB ID: 188467  
Last edited by cecilpierce; 6 Hours Ago at 08:52 AM.. Reason: p.s. if I try to login as a user it says not authorised.

This is a copy from another post yesterday.

---

### Post by emiliano12 on 2011-04-08
[B]I have the same problem, I update today (Friday April 8th) my Ubuntu 11.04 from the Update Manager, I had a lot of Updates, when they finished I restart Ubtuntu, and when Natty Start appears a message that said failed to load session "Ubuntu" so I only have a choice, start with Gnome Shell (3.0) but I want to back to Unity, and I dont know what can I do, I am new in linux, so I dont understand your indications, ppa, uninstall  gnome shell, reinstall ubuntu desktop!!

I want that someone explain me more about how to solve this problem!!! Please HeLP Me!!![/B]

---

### Post by osarusan on 2011-04-09
Not to be harsh, but if you're that new that you don't understand anything about PPA's, uninstalling and reinstalling, you probably should stay away from using the beta version. The stable releases would be better for you.

I'll try to talk you through it, but you're going to need to give more information. If you are using Gnome Shell, how did you install it? Did you use a program like Ubuntu Tweak?

---

### Post by emiliano12 on 2011-04-09
I update Ubuntu from update manager, I didnt install anything!!!

I dont know what can i do????

maybe wait for beta 2 and update from the disc!!

---

### Post by ilushechkin on 2011-04-09
Hi, you can try to remove gnome3 ppa:

```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:gnome3-team/gnome3
```

Hope it helps.

Regards,
Serge.
[http://tibcoadmin.com]("http://tibcoadmin.com")

---

### Post by Hakunka-Matata on 2011-04-11
If you need help with booting problems:

Download bootinfoscript, (find in my signature) and follow instructions.

---

### Post by danjahner on 2011-04-12
Same problem after installing Gnome 3. PPA-Purge fixed it for me.

---

