---
title: "Hard lockups with Nvidia 8600 GT / Hardy 64 bit"
date: 2008-05-12
forum: Multimedia Software
---

### Post by Mr.Auer on 2008-05-12
Im having random lockups on my AMD X2 5000+ / Asus AM2 / Nvidia 8600 GT / Hardy Heron 64 bit version. Sometimes it happens twice in a day, sometimes I can go couple days without it happening.

Screen freezes almost totally, mouse moves very very slowly and jerkily, music still plays but stutters at times, I cant get to virtual consoles, and even Sysrequest doesnt always work. Neither does Ctrl-alt-bckspace for restarting X. This didnt happen with Gutsy 64 bit.

Heres what my syslog says when it happened:

```
May 11 02:29:19 Opossumi kernel: [11458.586892] NVRM: Xid (0002:00): 13, 0001 00000000 00005039 00000328 00000000 00000023
May 11 02:29:19 Opossumi kernel: [11458.587170] NVRM: Xid (0002:00): 13, 0001 00000000 00005039 00000328 00000000 00000023
May 11 02:29:23 Opossumi kernel: [11462.539187] NVRM: Xid (0002:00): 13, 0001 00000000 00005039 00000328 00000000 00000023
May 11 02:29:23 Opossumi kernel: [11462.539560] NVRM: Xid (0002:00): 13, 0001 00000000 00005039 00000328 00000000 00000023
May 11 02:29:27 Opossumi kernel: [11466.556117] NVRM: Xid (0002:00): 13, 0001 00000000 00005039 00000328 00000000 00000023
May 11 02:29:27 Opossumi kernel: [11466.556485] NVRM: Xid (0002:00): 13, 0001 00000000 00005039 00000328 00000000 00000023
May 11 02:29:31 Opossumi kernel: [11470.573885] NVRM: Xid (0002:00): 13, 0001 00000000 00005039 00000328 00000000 00000023
May 11 02:29:31 Opossumi kernel: [11470.574249] NVRM: Xid (0002:00): 13, 0001 00000000 00005039 00000328 00000000 00000023
May 11 02:30:50 Opossumi kernel: [11549.302414] SysRq : Keyboard mode set to system default
May 11 02:30:53 Opossumi kernel: [11552.133996] SysRq : Emergency Sync
```

This time SysRq did work...

Any ideas appreciated..Im wondering if its a bug with Nvidia 64 bit package only, or something else?

---

### Post by Mr.Auer on 2008-05-13
Forgot to mention that as far as I can remember, these lockups and corresponding syslog entries only happen when using Compiz. I dont think its happened when using regular Gnome / Metacity, even with graphics acceleration still being done by Nvidia proprietary module.

Edit:
I now installed i386 version of Hardy on the same computer. Ill see if the lockups are gone or not, and keep you posted.

---

### Post by Mr.Auer on 2008-05-13
Hmm, I have the same lockups using i386 Hardy with repository Nvidia driver and Compiz. Now Im trying running without Compiz, with Nvidia driver.

---

### Post by Mr.Auer on 2008-05-18
This seems to be Compiz-NVidia related. The hard locks only happen when running Compiz, then at some point the NVidia driver puts up and outputs those messages to syslog, then proceeds to crash real good. This has not happened once with normal Metacity with 3d enabled by Nvidia.

Ill make a bug report vs. Compiz / Nvidia.

---

### Post by malfist on 2008-05-19
Not's not compiz. I'm experencing the same thing with my 6800. The issue is with OpenGL it seems. Here's my [thread.](http://ubuntuforums.org/showthread.php?t=800267)

I'm running an i686 proccessor, 64bit so it's not limited to that. I think it is something with the nvidia driver. How long ago did this start and have you fixed it yet?

Try playing a game that uses 3D stuff like Tremulous or WoW and you should see it happen again.

---

### Post by cdw38 on 2008-05-19
I've been running an 8600 GT (with proprietary drivers) and Compiz with 8.04 (i386) for a few days now and no lockup problems here.  Maybe I've just been lucky?  I'll certainly report back here if it happens...

Other system specs:
Gigabyte GA-965P-DS3 (first generation, whatever version that is)
Core 2 Duo E6300
eVGA 8600 GT (with proprietary drivers as installed by Ubuntu)

---

### Post by malfist on 2008-05-19
[wrong]

---

### Post by malfist on 2008-05-19
> **Mr.Auer said:**
> 
Heres what my syslog says when it happened:

```
May 11 02:29:19 Opossumi kernel: [11458.586892] NVRM: Xid (0002:00): 13, 0001 00000000 00005039 00000328 00000000 00000023
May 11 02:29:19 Opossumi kernel: [11458.587170] NVRM: Xid (0002:00): 13, 0001 00000000 00005039 00000328 00000000 00000023
May 11 02:29:23 Opossumi kernel: [11462.539187] NVRM: Xid (0002:00): 13, 0001 00000000 00005039 00000328 00000000 00000023
May 11 02:29:23 Opossumi kernel: [11462.539560] NVRM: Xid (0002:00): 13, 0001 00000000 00005039 00000328 00000000 00000023
May 11 02:29:27 Opossumi kernel: [11466.556117] NVRM: Xid (0002:00): 13, 0001 00000000 00005039 00000328 00000000 00000023
May 11 02:29:27 Opossumi kernel: [11466.556485] NVRM: Xid (0002:00): 13, 0001 00000000 00005039 00000328 00000000 00000023
May 11 02:29:31 Opossumi kernel: [11470.573885] NVRM: Xid (0002:00): 13, 0001 00000000 00005039 00000328 00000000 00000023
May 11 02:29:31 Opossumi kernel: [11470.574249] NVRM: Xid (0002:00): 13, 0001 00000000 00005039 00000328 00000000 00000023
May 11 02:30:50 Opossumi kernel: [11549.302414] SysRq : Keyboard mode set to system default
May 11 02:30:53 Opossumi kernel: [11552.133996] SysRq : Emergency Sync
```

This time SysRq did work...

Any ideas appreciated..Im wondering if its a bug with Nvidia 64 bit package only, or something else?

This is what mine says:
```
May 19 21:44:06 jerome-desktop -- MARK --
May 19 22:03:36 jerome-desktop kernel: [ 2437.738763] NVRM: Xid (0002:00): 13, 0002 beef3097 00004097 00000204 012c0003 00000100
May 19 22:03:36 jerome-desktop kernel: [ 2441.728926] NVRM: Xid (0002:00): 6, PE001f 1818 00000000 00000000 00000000 00000000
May 19 22:03:36 jerome-desktop kernel: [ 2441.731962] NVRM: Xid (0002:00): 7, Ch 00000000 M 00000408 D 00ffffff intr 00010000
May 19 22:03:36 jerome-desktop kernel: [ 2441.734994] NVRM: Xid (0002:00): 7, Ch 00000001 M 00000000 D 00000000 intr 00010000
May 19 22:03:36 jerome-desktop kernel: [ 2441.738040] NVRM: Xid (0002:00): 4, Ch 0000001f SC 00000007 M 00000700 Data 00000000
May 19 22:03:36 jerome-desktop kernel: [ 2441.741074] NVRM: Xid (0002:00): 6, PE001f 0700 00000000 00000000 00000000 00000000
May 19 22:03:36 jerome-desktop kernel: [ 2441.750087] NVRM: Xid (0002:00): 4, Ch 0000001f SC 00000000 M 00000000 Data 00000000
May 19 22:03:36 jerome-desktop kernel: [ 2441.753182] NVRM: Xid (0002:00): 7, Ch 0000001e M 00000000 D 00000000 intr 00011000
May 19 22:03:48 jerome-desktop kernel: [ 2454.310344] SysRq : Keyboard mode set to system default
May 19 21:44:06 jerome-desktop -- MARK --
May 19 22:03:36 jerome-desktop kernel: [ 2437.738763] NVRM: Xid (0002:00): 13, 0002 beef3097 00004097 00000204 012c0003 00000100
May 19 22:03:36 jerome-desktop kernel: [ 2441.728926] NVRM: Xid (0002:00): 6, PE001f 1818 00000000 00000000 00000000 00000000
May 19 22:03:36 jerome-desktop kernel: [ 2441.731962] NVRM: Xid (0002:00): 7, Ch 00000000 M 00000408 D 00ffffff intr 00010000
May 19 22:03:36 jerome-desktop kernel: [ 2441.734994] NVRM: Xid (0002:00): 7, Ch 00000001 M 00000000 D 00000000 intr 00010000
May 19 22:03:36 jerome-desktop kernel: [ 2441.738040] NVRM: Xid (0002:00): 4, Ch 0000001f SC 00000007 M 00000700 Data 00000000
May 19 22:03:36 jerome-desktop kernel: [ 2441.741074] NVRM: Xid (0002:00): 6, PE001f 0700 00000000 00000000 00000000 00000000
May 19 22:03:36 jerome-desktop kernel: [ 2441.750087] NVRM: Xid (0002:00): 4, Ch 0000001f SC 00000000 M 00000000 Data 00000000
May 19 22:03:36 jerome-desktop kernel: [ 2441.753182] NVRM: Xid (0002:00): 7, Ch 0000001e M 00000000 D 00000000 intr 00011000
May 19 22:03:48 jerome-desktop kernel: [ 2454.310344] SysRq : Keyboard mode set to system default
```

---

### Post by motin on 2008-06-28
I am having the same issue with GeForce 8400M GS, the nvidia-glx-new driver, Hardy 32-bit on a 64-bit system when running compiz. 

Actually, I remember having similar issues on my old laptop running Intel 915GM as well. 

After some testing, I have noticed that my crashes are not random. They incur when performing certain tasks:

1. Running Quanta
or 
2. Running Firefox with Google Spreadsheets open

... then running a compiz effect such as Fade-out, Exposé or Minimize all will result in output just like the one you posted at the top together with the same symptoms you described. 

Can you spot any pattern in when your lockups happen?

---

### Post by Mr.Auer on 2008-06-29
I have done some further investigating into this problem.
First, I updated to latest, source-compiled compiz core, as well as latest as of today, Nvidia drivers, kernel module compiled.

The lock problem still persists, but ONLY when the following conditions are met:
Im running Compiz, and using some custom theme, with default plugins on Compiz. If im running default Ubuntu theme or some of the others that come installed by default, I have no problems. But using Gelatin Gtk theme for example, Compiz, and drag-dropping (usually) or just using the machine, I get those crashes. 

Now I made a different user account with fresh Compiz and Gnome settings, and I can reproduce the crashes if I select another theme. Otherwise im fine.

So I would think that the issue has something to do with both Compiz and Nvidia driver (since the Nvidia driver outputs those errors), even the latest one, which is two versions newer than the stock Ubuntu one. I cant get the machine to crash if I only have Nvidia driver rendering, but no Compiz.

I have 32-bit Ubuntu now, on my AMD 64 X2, I had the 64-bit version before, and the same thing happened on that.

Edit: Ill try running Quake Wars now for a while, I havent played any games in a while. Lets see how that goes. Ill report back.

---

### Post by Mr.Auer on 2008-06-30
Playing Quake Wars works fine, tried running it windowed with Compiz, that works also, except in fullscreen it keeps flipping between windowed and FS.

Played several hours straight without Compiz as well, no crashes at all either way.

So it only happens when 1-3 or all of these are running: 1) Compiz, 2) NVidia and 3) modified themes and usually also 4) playing music or videos and drag and dropping files into the playlist (the most common occurrence of the crash).

My Compiz version is now 0.7.4, and Nvidia drivers are 173.14.09

---

