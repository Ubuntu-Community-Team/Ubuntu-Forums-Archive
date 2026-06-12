---
title: "No Gnome-panel."
date: 2010-11-30
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by donniezazen on 2010-11-30
Hi,

1. I have just lost all my panels. Any solution?

2. Since, there have been a huge number of crashes and bugs in Natty, i am planning to install it in another 5 Gb root partition and share swap and home directory. Will this be compatible and not screw up Maverick for basic usage?

Thanks.

---

### Post by cariboo on 2010-11-30
> **soham_1207 said:**
> Hi,

1. I have just lost all my panels. Any solution?

I just opened a terminal nad type:

```
gnome-panel &
```

> 2. Since, there have been a huge number of crashes and bugs in Natty, i am planning to install it in another 5 Gb root partition and share swap and home directory. Will this be compatible and not screw up Maverick for basic usage?

Thanks.

Your problem may be the config files in your home directory. I just did a fresh install on my netbook, including formatting /home, and many of the problems disappeared, such as indicators not starting.

---

### Post by wilee-nilee on 2010-11-30
Where is the terminal I get no dropdown from the ubuntu icon, looks like unity, no problem just try to figure this out.

---

### Post by cariboo on 2010-11-30
You should be able to open a terminal, by pressing:

```
Ctrl-Alt-T
```

---

### Post by wilee-nilee on 2010-11-30
> **cariboo907 said:**
> You should be able to open a terminal, by pressing:

```
Ctrl-Alt-T
```


Thanks; some commands I just never use that is one of them.;)

---

### Post by karthick87 on 2010-11-30
[FONT=Verdana]Press **ALT+F2** and in the run dialog box, type [B][I]gnome-terminal

[/I][/B][/FONT]In the terminal type the following 

```
gconftool-2  --shutdown 
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

---

### Post by donniezazen on 2010-11-30
> **cariboo907 said:**
> I just opened a terminal nad type:

```
gnome-panel &
```



Your problem may be the config files in your home directory. I just did a fresh install on my netbook, including formatting /home, and many of the problems disappeared, such as indicators not starting.

Thanks that solved the problem.

---

### Post by andrewthomas on 2010-11-30
I think that gnome-session, gnome-session-bin, and gnome-session-common versions **2.32.1-0ubuntu3**
are causing problems, I downgraded the packages to [B]2.32.1-0ubuntu2 
[/B]and all is good.

---

### Post by garvinrick4 on 2010-11-30
#ALT/F1 gives me all the drop down menus as the Gnome Classic, run your mouse over
area after ALT/F1

#Well one install in New Natty desktop ALT/F1 gives me the Gnome Classic drop down menu's
and one install does not.  All Keyboard shortcuts work and network manager works in both.

#rick@rick-HP-G71-Notebook-PC:/$ aptitude show network-manager
Package: network-manager                 
State: installed
Automatically installed: no
Version: 0.8.3~git.20101118t223039.d60a988-0ubuntu1

---

### Post by lidex on 2010-12-01
> **soham_1207 said:**
> Hi,

1. I have just lost all my panels. Any solution?

2. Since, there have been a huge number of crashes and bugs in Natty, i am planning to install it in another 5 Gb root partition and share swap and home directory. Will this be compatible and not screw up Maverick for basic usage?

Thanks.

I had that issue today. Solved it by going into gconf-editor - desktop/gnome/session/required_components/panel and changed "" to gnome-panel. Then logout/in. Looks as if an update unset that value.

---

### Post by Harry33 on 2010-12-01
> **andrewthomas said:**
> I think that gnome-session, gnome-session-bin, and gnome-session-common versions **2.32.1-0ubuntu3**
are causing problems, I downgraded the packages to [B]2.32.1-0ubuntu2 
[/B]and all is good.

I do not have any problems with gnome-session packages (v. 2.32.1-0ubuntu3).
Then again, I do not have Unity installed, only Gnome2 (Gnome-Panel) and Gnome3 (Gnome-Shell).

---

### Post by donniezazen on 2010-12-01
> **lidex said:**
> I had that issue today. Solved it by going into gconf-editor - desktop/gnome/session/required_components/panel and changed "" to gnome-panel. Then logout/in. Looks as if an update unset that value.

Thanks this solved it permanently.

---

### Post by TNT1 on 2010-12-01
> **cariboo907 said:**
> You should be able to open a terminal, by pressing:

```
Ctrl-Alt-T
```

That's awesome. Thanks.

---

### Post by paul_in_london on 2010-12-01
> **lidex said:**
> I had that issue today. Solved it by going into gconf-editor - desktop/gnome/session/required_components/panel and changed "" to gnome-panel. Then logout/in. Looks as if an update unset that value.

+1

Before I saw this thread I discovered that safe-mode login worked. Now I can confirm that the panel key value in gconf-editor is (still) set correctly to **gnome-panel** for a safe-mode login, whereas it is unset for a normal login.

Thanks for the fix.

---

### Post by Kazade on 2010-12-01
> **lidex said:**
> I had that issue today. Solved it by going into gconf-editor - desktop/gnome/session/required_components/panel and changed "" to gnome-panel. Then logout/in. Looks as if an update unset that value.

I'm wondering if that was intentional as part of the switch to Unity...

Edit: It is!

  - add gnome gconf path and default key for not launching gnome-panel in the
    Ubuntu Desktop session (we have unity now).
    This doesn't solve case of non supported unity hw and saved session, but
    this workaround will be removed once we get the new gnome-session
    configuration system.

---

### Post by Quackers on 2010-12-01
> **lidex said:**
> I had that issue today. Solved it by going into gconf-editor - desktop/gnome/session/required_components/panel and changed "" to gnome-panel. Then logout/in. Looks as if an update unset that value.

Thanks lidex, this worked for me :-)

---

### Post by Wobblybob on 2010-12-01
> **lidex said:**
> I had that issue today. Solved it by going into gconf-editor - desktop/gnome/session/required_components/panel and changed "" to gnome-panel. Then logout/in. Looks as if an update unset that value.

Thanks mate I'm just testing the Alpha1 iso and it gives me no Gnome Panels so restored them from a Terminal

Ctrl+Alt+T

$ gconf-editor

then navigated to desktop/gnome/session/required_components/panel and changed "" to gnome-panel as you state and rebooted.

cheers

---

### Post by VMC on 2010-12-01
> **Kazade said:**
> I'm wondering if that was intentional as part of the switch to Unity...

Edit: It is!

  - add gnome gconf path and default key for not launching gnome-panel in the
    Ubuntu Desktop session (we have unity now).
    This doesn't solve case of non supported unity hw and saved session, but
    this workaround will be removed once we get the new gnome-session
    configuration system.

Yes your right. I have nvidia 6150se and needed to install the video driver before I could run unity. I used the nvidia version from their web page.

---

### Post by seeker5528 on 2010-12-02
Sounds like the disabling of Gnome panel is a temporary thing, otherwise I don't know how the fallback is supposed to work, but outside of that, from the enduser standpoint....

Wouldn't the easy solution if Unity isn't working for you be to choose the Ubuntu Classic login at the login screen?

Later, Seeker

---

### Post by cariboo on 2010-12-02
> **seeker5528 said:**
> Sounds like the disabling of Gnome panel is a temporary thing, otherwise I don't know how the fallback is supposed to work, but outside of that, from the enduser standpoint....

Wouldn't the easy solution if Unity isn't working for you be to choose the Ubuntu Classic login at the login screen?

Later, Seeker

That's way to easy. :) Ubuntu Desktop is set as the default when you log in for the first time. Hopefully there will be some sort of fall back for those of us that don't have 3D enabled until we install the proper drivers.

---

### Post by lidex on 2010-12-02
> **seeker5528 said:**
> Sounds like the disabling of Gnome panel is a temporary thing, otherwise I don't know how the fallback is supposed to work, but outside of that, from the enduser standpoint....

Wouldn't the easy solution if Unity isn't working for you be to choose the Ubuntu Classic login at the login screen?


Yeah, if you know what you're doing, which obviously I do not. I think what happened in my case was I was trying to compile unity from source following the wiki and had no clue as to the login options. My configuration must have gotten borked somewhere along the way. I think I have it cleared up now. For classic login gconf key is set to 'gnome-panel'; ccsm profile is 'default' with unity plugin disabled and gconf backend. For 'Desktop' (unity) login gconf key is (un)set to ""; ccsm profile set to 'unity' with unity plugin enabled and gconf backend.

---

### Post by Bou on 2010-12-10
> **lidex said:**
> I had that issue today. Solved it by going into gconf-editor - desktop/gnome/session/required_components/panel and changed "" to gnome-panel. Then logout/in. Looks as if an update unset that value.

I'm having the opposite problem, where a gnome-panel appears over my Unity panel all the time. Is there something I can do to banish gnome-panel from my session?

---

### Post by jerrylamos on 2010-12-18
> **karthick87 said:**
> [FONT=Verdana]Press **ALT+F2** and in the run dialog box, type [B][I]gnome-terminal

[/I][/B][/FONT]In the terminal type the following 

```
gconftool-2  --shutdown 
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

Yay!  Worked again.  Just updated which installed 2.6.37-10 and no panel appeared on boot.  
Ctrl-Alt-T gnome-panel &
didn't work because "there is a panel running already".  Not!

No I don't use "Unity".  It grabs an inch of the left of my screen for some silly hieroglyphs.  The Phoenicians invented the alphabet years ago...

Thanks again, Jerry

---

### Post by cariboo on 2010-12-18
As was suggested in the other thread, turn on auto hide. You probably need to install compizconfig-setting-manager to do this. Once ccsm is installed start it up and scroll all the way to the bottom. click on Unity, and another window will open allowing you to turn on auto/intellihide. Once it's enabled, all you have to do to make the panel hide is grab a window and nudge it to hide it.

---

### Post by jerrylamos on 2010-12-18
> **cariboo907 said:**
> As was suggested in the other thread, turn on auto hide. You probably need to install compizconfig-setting-manager to do this. Once ccsm is installed start it up and scroll all the way to the bottom. click on Unity, and another window will open allowing you to turn on auto/intellihide. Once it's enabled, all you have to do to make the panel hide is grab a window and nudge it to hide it.

Hmmm.  Two of my four test systems have integrated Intel video graphics.  Compiz is black listed for these.  On the other two I could run compiz but don't since I run full screen applications and all compiz eye candy would do is insert extra code slowing things down.

Oh well.  Jerry

p.s. Just installed Natty CD daily build 20101218 which finally fits on CD.  Classic desktop running O.K. on intel video graphics.  I'll try Thinkpad T40 next which does support compiz if I had it turned on.

---

### Post by cariboo on 2010-12-18
Compiz shouldn't slow things down to the point where it is noticeable, unless your system is really underpowered. I run Unity on my atom powered netbook with i945 graphics, it runs much faster than the Maverick version of Unity on top of mutter.

---

### Post by jerrylamos on 2010-12-18
> **jerrylamos said:**
> Just installed Natty CD daily build 20101218 which finally fits on CD.  Classic desktop running O.K. on intel video graphics.  I'll try Thinkpad T40 next which does support compiz if I had it turned on.

CD live ubuntu panel broken on IBM Thinkpad T40 with ati radeon graphics. Entered a bug but don't have the number.

Install which doesn't use a fancy panel worked.

Booting natty from the daily build purplish screen with cursor.  Period.
Much thrashing around with removing and installing compiz, fix broken packages, Ctrl-Alt-T gnome-panel &, multiple boots and finally got up far enough that I could log out, log in again chose ubuntu classic.  Running fine now.  Updates complain about an error with nvidea - what's that got to do with ati radeon??

Is there a boot option to choose ubuntu classic?  Sure would have saved a couple hours.

Jerry

---

### Post by cariboo on 2010-12-18
You can select the classic Desktop from the login screen, once selected it will stick until you chose something else.

---

### Post by jerrylamos on 2010-12-19
> **cariboo907 said:**
> You can select the classic Desktop from the login screen, once selected it will stick until you chose something else.

Yes, that worked.  I habitually specify automatic login on installation since there is only one account on my four test systems and I don't need extra keystrokes to login on each boot which are always the same on each login. These are multiboot with Lucid, Lubuntu, Maverick, TV-Viewer, Natty, Debian, Tiny Core.  If I'm leaving the computer for an hour I power off.

Doesn't help on CD Live though, since that's an automatic login as designed which is broken on the T40 on 20101218, launcpad bug entered. The Compaq Presario is also ati so I didn't even try.  If there's a fix on launchpad I'll try that.  So far the "Install" option on CD Live doesn't use "eye candy" desktop panels so it works

Most of the time, not always, these malfunctions are worked out during Alpha and Beta.  That's why we test.

Jerry

---

### Post by lucazade on 2010-12-20
> **jerrylamos said:**
> Doesn't help on CD Live though, since that's an automatic login as designed which is broken on the T40 on 20101218, launcpad bug entered. 

Same issue on my Thinkpad T40, livecd brings only a wallpaper and a mouse cursor.
Have you opened a bug? Which number? I'd like to confirm it and follow it.
Thanks :)

---

### Post by jerrylamos on 2010-12-20
> **lucazade said:**
> Same issue on my Thinkpad T40, livecd brings only a wallpaper and a mouse cursor.
Have you opened a bug? Which number? I'd like to confirm it and follow it.
Thanks :)

Take a look at launchpad bug #692017 to see if it matches your problem.  I just tried new daily build 20101220 which has the same problem on the T40.  My Compaq Presario with radeon Xpress 200 ran O.K.  The T40 with ati radeon mobilty 7500 does not.

Jerry

---

### Post by lucazade on 2010-12-21
> **jerrylamos said:**
> Take a look at launchpad bug #692017 to see if it matches your problem.  I just tried new daily build 20101220 which has the same problem on the T40.  My Compaq Presario with radeon Xpress 200 ran O.K.  The T40 with ati radeon mobilty 7500 does not.

Jerry

I wasn't able to find this bug through google or launchpad. Could you provide me a link? Thanks
Yes, should be related to mobility radeon 7500.

---

### Post by lucazade on 2010-12-21
> **jerrylamos said:**
> Take a look at launchpad bug #692017 to see if it matches your problem.  I just tried new daily build 20101220 which has the same problem on the T40.  My Compaq Presario with radeon Xpress 200 ran O.K.  The T40 with ati radeon mobilty 7500 does not.

Jerry

> **lucazade said:**
> I wasn't able to find this bug through google or launchpad. Could you provide me a link? Thanks
Yes, should be related to mobility radeon 7500.

[https://bugs.launchpad.net/bugs/692017](https://bugs.launchpad.net/bugs/692017)

"Not allowed here
Sorry, you don't have permission to access this page"

it is a private bug report

---

### Post by lucazade on 2010-12-22
> **lucazade said:**
> [https://bugs.launchpad.net/bugs/692017](https://bugs.launchpad.net/bugs/692017)

"Not allowed here
Sorry, you don't have permission to access this page"

it is a private bug report

created new public bug report:
[https://bugs.launchpad.net/unity/+bug/693461](https://bugs.launchpad.net/unity/+bug/693461)

---

