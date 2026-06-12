---
title: "bash history"
date: 2011-02-25
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by mc4man on 2011-02-25
If you make use of the bash history (~/.bash_history) you may want to check and see if any new entries are being added since the upgrade to bash 4.2
(none here

Edit: as it stands now, with bash 4.2+ if you wish commands entered in a terminal to be written to your bash history you must exit the terminal w/ an exit command
small explain post 7

---

### Post by Harry33 on 2011-02-25
> **mc4man said:**
> If you make use of the bash history (~/.bash_history) you may want to check and see if any new entries are being added since the upgrade to bash 4.2
(none here

Cannot do that yet.
The 64-bit build failed.

---

### Post by MacUntu on 2011-02-25
Which version? 4.2-0ubuntu1 - history working fine.

---

### Post by mc4man on 2011-02-25
> Which version? 4.2-0ubuntu1 - history working fine.
That's the version giving trouble here, guess it's time for a fresh install

(if I can get a current .iso to install properly, been having trouble lately with some recent .iso's on a nvidia laptop - if the install works then tend to get the ubuntu-unity icons and can't change icon themes

What's odd is if I revert to the last 4.1 package it works fine, going to try a new user..

---

### Post by mc4man on 2011-02-25
Well, on a fresh A2 install bash history works. Upgrading just bash and it stops dead. (history is maintained in current terminal instance, but not written to ~/.bash_history
filed a bug based on that
[https://bugs.launchpad.net/ubuntu/+source/bash/+bug/725327](https://bugs.launchpad.net/ubuntu/+source/bash/+bug/725327)

---

### Post by mc4man on 2011-03-02
Definitely see this loss of function  -  on any fresh install of the last couple days there won't even be ~/.bash_history created
A bit of a shame - will go back to 4.1 here
(find great use of a custom .inputrc here so a functioning, update-able bash_history id quite useful.

edit; though overnight 3 commands from yesterday did manage to get into bash_history somehow, so now have a total of 4 in a 2 day old install out of maybe 50 or so entered

---

### Post by mc4man on 2011-03-07
There has been a change to bash so to get commands to be wtitten to ~/.bash_history one must now use the exit command when closing a terminal

as relayed to me by chet ramey
> > One thing that has changed is that an interactive shell will no longer
> attempt to write the history file if it's killed by a signal, since that
> causes many functions to be executed that are not safe to call from a
> signal handler.  If you're in the habit of trying to exit the shell by
> closing the terminal window, which causes the shell to be killed by SIGHUP
> (I think, maybe SIGTERM), the history will not be saved.
> 
> Chet

---

### Post by Quackers on 2011-03-07
Interesting, thanks :-)

---

### Post by VMC on 2011-03-08
> **mc4man said:**
> There has been a change to bash so to get commands to be wtitten to ~/.bash_history one must now use the exit command when closing a terminal

as relayed to me by chet ramey
Will this behavior be "fixed" or do we now have to exit terminal?

---

### Post by mc4man on 2011-03-08
> Will this behavior be "fixed" or do we now have to exit terminal?
Not a clue - the long time behavior and habit for many was/is to just close a terminal out, it does have an X button sitting right there.

On the bug i filed never did get any response other than from a couple of users seeing the same. (Did post up there reason for this, will have to wait and see if anything develops.

I'd figure ubuntu would not be inclined to change the upstream code, additionally there is some indication this is a more proper way to exit a terminal anyway.

( does make clear to me now why I was getting some writes when crashing the desktop while a terminal was open...

Edit: the gnome-terminal menu's 'close window' option is the same as clicking the close button, ie. will not constitute an exit.

---

### Post by Wobblybob on 2011-03-08
Thanks mc4man for finding the answer to this problem it's been bugging me for a while. So it's a feature not a bug! I wonder if this is going to be communicated to the community on release as it's quite a change in functionatity. I agree it's probabley safer but how many of us EXIT a Terminal I wonder?

---

### Post by mechanic on 2011-03-08
I suspect most of us hit Cntrl + d as we learned long ago. That seems the equivalent of typing "exit" and hitting Return.

---

### Post by VMC on 2011-03-08
> **mc4man said:**
> Not a clue - the long time behavior and habit for many was/is to just close a terminal out, it does have an X button sitting right there.

On the bug i filed never did get any response other than from a couple of users seeing the same. (Did post up there reason for this, will have to wait and see if anything develops.

I'd figure ubuntu would not be inclined to change the upstream code, additionally there is some indication this is a more proper way to exit a terminal anyway.

( does make clear to me now why I was getting some writes when crashing the desktop while a terminal was open...

Edit: the gnome-terminal menu's 'close window' option is the same as clicking the close button, ie. will not constitute an exit.
Somehow I missed your report. I confirmed it and "me-too" also. I've always used the "x" button. Only time I have used the Ctrl+d is in an old terminal style setting.

---

### Post by mc4man on 2011-03-08
> **VMC said:**
> Somehow I missed your report. I confirmed it and "me-too" also. I've always used the "x" button. Only time I have used the Ctrl+d is in an old terminal style setting.

Want to says thanks for confirming a bug when doing a 'me too' and seeing it at 'new'  - (not done nearly enough, certainly can be frustrating to bug reporters to see me too's and new

In this case I'm ok with the change, just glad to have the history going again. (find the page_up, page_dn history search quite useful.

Actually see some advantage here, - many times i don't particularly want or need a command(s) saved, so  in those cases will now just close the window...

---

### Post by VMC on 2011-03-08
> **mc4man said:**
> ...

Actually see some advantage here, - many times i don't particularly want or need a command(s) saved, so  in those cases will now just close the window...
Yea, most of my commands are stored in alises anyhow, but its nice to have history, or maybe I relied on history too much. I find I'm constantly doing a Ctrl+r to find a recent command.

---

### Post by mc4man on 2011-03-08
> but its nice to have history, ...
What I use here alot is an .inputrc in home dir. (could be in root) w/ this, then type a few letters or word(s) and page_up/page_dn

```
"\e[5~": history-search-backward
"\e[6~": history-search-forward
```

---

### Post by mc4man on 2011-03-31
The next natty upgrade to bash should return a ~/bash_history write when using the close button 
bash (4.2-0ubuntu3)

---

### Post by VMC on 2011-03-31
> **mc4man said:**
> The next natty upgrade to bash should return a ~/bash_history write when using the close button 
bash (4.2-0ubuntu3)

Good news, thanks. I'm so use to the close button, I forget to Ctrl+d and lose my history.

---

### Post by mc4man on 2011-03-31
For whatever reason upstream decided to provide a patch to deal with this (initial response when I filed the upstream bug was to just use exit or Ctrl+d
What happens with the next version just have to wait and see
> Bash-Release:   4.2
Patch-ID:       bash42-008

Bug-Description:

Bash-4.2 does not attempt to save the shell history on receipt of a
terminating signal that is handled synchronously.  Unfortunately, the
`close' button on most X11 terminal emulators sends SIGHUP, which
kills the shell.

This is a very small patch to save the history in the case that an
interactive shell receives a SIGHUP or SIGTERM while in readline and
reading a command.

The next version of bash will do this differently.


---

