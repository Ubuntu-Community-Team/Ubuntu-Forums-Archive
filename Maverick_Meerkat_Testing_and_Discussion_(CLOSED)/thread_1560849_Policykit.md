---
title: "Policykit"
date: 2010-08-25
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by cecilpierce on 2010-08-25
any body having policykit not responding pop up when trying to restart or shut down ?

thanks, cecil

---

### Post by PaulW2U on 2010-08-25
Yes, it only started today - each time I've logged out or restarted.

---

### Post by sgage on 2010-08-25
Yes - I had to reboot this morning after updating the kernel, and got that error.

---

### Post by TunaCanTommy on 2010-08-25
Yep . . . started today, getting a crash report for "Ubuntu One" also.

---

### Post by cecilpierce on 2010-08-25
> **sgage said:**
> Yes - I had to reboot this morning after updating the kernel, and got that error.

it was doing that before the new kernel came out, its a pain in the you know what !

---

### Post by jou770d on 2010-08-25
> **TunaCanTommy said:**
> Yep . . . started today, getting a crash report for "Ubuntu One" also.

Same here.

I installed Maverick today and fully updated it (using aptitude safe-upgrade).

---

### Post by cariboo on 2010-08-25
Has anyone created a bug report yet?

---

### Post by Harry33 on 2010-08-25
Here is the bug report I made a few hours ago:
[https://bugs.launchpad.net/ubuntu/+source/policykit-1-gnome/+bug/623819](https://bugs.launchpad.net/ubuntu/+source/policykit-1-gnome/+bug/623819)

The problem appeared right after upgrading two packages:
- policykit-1-gnome_0.96-2ubuntu3
- libpolkit-gtk-1-0_0.96-2ubuntu3

If you want to get rid of the bug, just downgrade those packages to version 0.96-2ubuntu2.

And, by the way shut down and reboot works OK in terminal:
sudo reboot
sudo halt

---

### Post by plun on 2010-08-25
> **cariboo907 said:**
> Has anyone created a bug report yet?

This one maybe:
[https://bugs.launchpad.net/ubuntu/+source/policykit-1-gnome/+bug/623819](https://bugs.launchpad.net/ubuntu/+source/policykit-1-gnome/+bug/623819)

---

### Post by ranch hand on 2010-08-25
Added my "me too".  Am on one of my back up installs that I upgraded everything but the update mangler and policy kit stuff to check and see that that was the problem.

Sure is.  Now I can upgrade my 2 mains and be sure they work.

---

### Post by kyleabaker on 2010-08-25
Same for me (me-too'd it as well).

---

### Post by VinDSL on 2010-08-25
This cropped-up for me too...

It started yesterday, with the Linux 2.6.35-18-generic update.

The Linux 2.6.35-19-generic update, today, didn't fix the problem.

Yesterday, a dialog box popped up, saying PolicyKit Authentication Agent is still running.  

Today, the dialog box says, PolicyKit Authentication Agent is not responding.

Is this what you are seeing?!?!?

**EDIT**

I might add...

Every since I installed 10.10, certain apps require me to enter the password for my login keyring, such as Empathy and Evolution Mail.  This remains a mystery to me.

I don't know if it's related to the PolicyKit problem, but they are both auth related, sooo...

---

### Post by andrewthomas on 2010-08-25
> **VinDSL said:**
> This cropped-up for me too...

It started yesterday, with the Linux 2.6.35-18-generic update.

The Linux 2.6.35-19-generic update, today, didn't fix the problem.

Yesterday, a dialog box popped up, saying PolicyKit Authentication Agent is still running.  

Today, the dialog box says, PolicyKit Authentication Agent is not responding.

Is this what you are seeing?!?!?
It actually says both. See the screenshot.

[QUOTE=changelog]policykit-1-gnome (0.96-2ubuntu3) maverick; urgency=low

  * debian/patches/04-autorestart.patch:
    - add autorestart support (LP: #499937)

 -- Michael Vogt <michael.vogt@ubuntu.com>  Tue, 24 Aug 2010 13:08:48 +0200[/QUOTE]

---

### Post by andrewthomas on 2010-08-25
> **VinDSL said:**
> Every since I installed 10.10, certain apps require me to enter the password for my login keyring, such as Empathy and Evolution Mail.  This remains a mystery to me.

I don't know if it's related to the PolicyKit problem, but they are both auth related, sooo...
If the password for your login keyring is different from your user password then it should ask.  If they are the same, then it should already be unlocked.  I think

---

### Post by mc4man on 2010-08-25
the current little issue is from the 'autorestart' patch, would expect it to be resolved fairly quickly or at worst, the patch temporarily reverted.

---

### Post by VinDSL on 2010-08-25
> **andrewthomas said:**
> If the password for your login keyring is different from your user password then it should ask.  If they are the same, then it should already be unlocked.  I thinkEureka!

I forgot that Ubu doesn't synch the login keyring, when you change your login password.

I killed the keyring...

```
$ sudo rm ~/.gnome2/keyrings/login.keyring
```

... opened up Evolution, entered a new keyring password (used my login password) and all is good now.

Thanks!  ;)

Okay, one bug squashed.  

Now. if we can get past this PolicyKit annoyance...

---

### Post by VMC on 2010-08-25
> **plun said:**
> This one maybe:
[https://bugs.launchpad.net/ubuntu/+source/policykit-1-gnome/+bug/623819](https://bugs.launchpad.net/ubuntu/+source/policykit-1-gnome/+bug/623819)
Thanks plun. Odd, but I searched LP and came up with a ton of policykit offences, just not that one.

Here is my only knowed file on Policykit:

```
$ cat /etc/xdg/autostart/polkit-gnome-authentication-agent-1.desktop
[Desktop Entry]
Name=PolicyKit Authentication Agent
Comment=PolicyKit Authentication Agent
Exec=/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
Terminal=false
Type=Application
Categories=
NoDisplay=true
OnlyShowIn=GNOME;XFCE;
X-GNOME-AutoRestart=true
X-Ubuntu-Gettext-Domain=polkit-gnome-1

```Edit:
syslog and daemon.log contain only this entry:
Aug 25 19:04:25 vmc-desktop polkitd[1341]: started daemon version 0.96 using authority implementation `local' version `0.96'

also:

```
$ ps x -A|grep polkit
 1341 ?        S      0:00 /usr/lib/policykit-1/polkitd
 1435 ?        S      0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
```

---

### Post by florus on 2010-08-26
> Here is the bug report I made a few hours ago:
[https://bugs.launchpad.net/ubuntu/+s...me/+bug/623819](https://bugs.launchpad.net/ubuntu/+s...me/+bug/623819)

Me too. There are only 14 users who have added a me-too to the bug. Are most people reading this thread unaffected?

---

### Post by ronacc on 2010-08-26
its up to 25 me too's now .

---

### Post by florus on 2010-08-26
The bug has now been classed as medium importance and assigned to a developer.

---

### Post by recluce on 2010-08-26
Same issue here, me-too'd on launchpad. Up to 36 now.

---

### Post by DeadlyWolf on 2010-08-26
Me also, up to 40 now

---

### Post by cariboo on 2010-08-29
I see people are still adding their me too's, please stop. See [this]("https://bugs.launchpad.net/ubuntu/+source/policykit-1-gnome/+bug/623819/comments/12") post.

---

### Post by VinDSL on 2010-08-29
> **cariboo907 said:**
> I see people are still adding their me too's, please stop. See [this]("https://bugs.launchpad.net/ubuntu/+source/policykit-1-gnome/+bug/623819/comments/12") post.It's all *ranch hand's* fault, Jim!

He's the instigator of the group...  :D

---

### Post by kyleabaker on 2010-08-29
The problem is that everyone wants to post rather than click the button. They should create a status that starts asking the user if they simply want to add to the count rather than post when it reaches this point. Simple, yet effective, no?

---

### Post by dino99 on 2010-08-29
most kids makes no difference between forum,  chat and launchpad, might ask mods and devs to warn them about

---

### Post by cecilpierce on 2010-08-29
I was wondering, is there anyone not affected by the bug ?

---

### Post by ktp on 2010-08-29
> **VinDSL said:**
> It's all *ranch hand's* fault, Jim!

He's the instigator of the group...  :D

:lolflag:

---

### Post by cariboo on 2010-08-29
Back in the day it used to be called the **AOL affect** where all the AOL users added me too to a thread. :)

---

### Post by autocrosser on 2010-08-29
> **VinDSL said:**
> It's all *ranch hand's* fault, Jim!

He's the instigator of the group...  :D

:guitar::lolflag:



"me too!"

---

### Post by chrisccoulson on 2010-08-29
> **cecilpierce said:**
> I was wondering, is there anyone not affected by the bug ?

No, the bug affects everyone running the Policykit agent in their session (which should be everybody).

---

### Post by Harry33 on 2010-08-30
Well now the bug is "in progress" in Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/policykit-1-gnome/+bug/623819](https://bugs.launchpad.net/ubuntu/+source/policykit-1-gnome/+bug/623819)

---

### Post by Harry33 on 2010-08-30
The fix was released just a moment ago (v. 0.96-2ubuntu4).
I can confirm it work. Problem solved.

---

