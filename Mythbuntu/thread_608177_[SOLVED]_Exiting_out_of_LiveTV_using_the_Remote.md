---
title: "[SOLVED] Exiting out of LiveTV using the Remote"
date: 2007-11-09
forum: Mythbuntu
---

### Post by bcr821 on 2007-11-09
So i finally got my remote to work but now when i'm watching LiveTV i can't get back to the menu.  When i press "esc" on the keyboard it brings me back to the previous menu and none of the buttons on the remote will do that for me.  The button on the remote labeled "Back/Exit" doesn't seem to do anything. 

I guess my question is:  Is there a way to bind the "back/exit" button on the remote to do the same thing as when i press the "esc" button on my keyboard

---

### Post by uopjohnson on 2007-11-09
Short answer. yes.  
Long answer, you can bind any recognized key on yoru remote to any key on the keyboard.  To get started open a terminal and type:
```
irw
```
then pres the Back/Exit key on your keyboard and see what it says.  Mine looks like this:
```
jon@artemis:~$ irw
000000000000179f 00 Back/Exit Hauppauge_350
```
pres cntrl-c to exit irw.
The important part of this follows the cryptic numbers 'Back/Exit'.  What does your's say?  If it says nothing then you have not configured your remote properly.  If it says anything at all we can move on.   Edit your remote button configuration file for mythtv which is at ~/.mythtv/lircrc
first search for a stanza that contains the name of the button we got from irw. eg:
```
begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Back/Exit
    config = Esc
    repeat = 0
    delay = 0
end

```
If you already have this stanza just change whatever is under config= to config = Esc and your back exit should work.  If you don't have this then add it by copying another stanza and changing the button = and the config line, but nothing else.

---

### Post by bcr821 on 2007-11-10
> **uopjohnson said:**
> Short answer. yes.  
Long answer, you can bind any recognized key on yoru remote to any key on the keyboard.  To get started open a terminal and type:
```
irw
```
then pres the Back/Exit key on your keyboard and see what it says.  Mine looks like this:
```
jon@artemis:~$ irw
000000000000179f 00 Back/Exit Hauppauge_350
```
pres cntrl-c to exit irw.
The important part of this follows the cryptic numbers 'Back/Exit'.  What does your's say?  If it says nothing then you have not configured your remote properly.  If it says anything at all we can move on.   Edit your remote button configuration file for mythtv which is at ~/.mythtv/lircrc
first search for a stanza that contains the name of the button we got from irw. eg:
```
begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Back/Exit
    config = Esc
    repeat = 0
    delay = 0
end

```
If you already have this stanza just change whatever is under config= to config = Esc and your back exit should work.  If you don't have this then add it by copying another stanza and changing the button = and the config line, but nothing else.

you sir or a badass, thank you SO much

oh and mine said:

```
begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Back/Exit
    config = D
    repeat = 0
    delay = 0
end

```

---

### Post by superm1 on 2007-11-10
> **bcr821 said:**
> you sir or a badass, thank you SO much

oh and mine said:

```
begin
    remote = hauppauge_pvr
    prog = mythtv
    button = Back/Exit
    config = D
    repeat = 0
    delay = 0
end

```
Can you please file a bug against mythbuntu-lirc-generator and notate your remote, and include these two stanzas?  Thank you.

---

### Post by uopjohnson on 2007-11-10
Filed bug [#161875]("https://bugs.launchpad.net/mythbuntu/+bug/161875/"), however I don't see how to file it against mythbuntu-lirc-generator.

---

### Post by superm1 on 2007-11-10
Thanks, i adjusted the bug properly :)

---

