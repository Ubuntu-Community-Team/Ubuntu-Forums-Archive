---
title: "Can not run full-screen programs (BZFLAG)"
date: 2007-12-20
forum: Multimedia &amp; Video
---

### Post by reggiedavid on 2007-12-20
Hi

I am running Ubuntu 7.10 (upgraded online from prior version - 7.02?).  Was able to run BZFLAG and others, since the upgrade I try to run the program and nothing happens.

I have tried uninstalling and then reinstalling BZFLAG, but no help.  BZFLAG is not the only program not to work.  Tremulus, Tuxcart and other full-screen apps not working.

I don't know where to look for error messages.  Thanks for any help.

---

### Post by mouseboyx on 2007-12-21
The error will come if you run bzflag or whatever you want, if you run it from a terminal.

so probably open a terminal and type bzflag.

If its not bzflag then click properties on the launcher and copy and paste the command into a terminal.

---

### Post by reggiedavid on 2007-12-26
Thanks,  will try and see what I can find....

---

### Post by big_dog1968 on 2008-03-03
I have the same issue. I ran from terminal and this is what I got:
[B][I][I]
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  136 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x5f
  Serial number of failed request:  146
  Current serial number in output stream:  148[/I][/I][/B]

---

### Post by TheguywholikesLINUX on 2008-04-21
Hi, i am new on the forum, but i am having the same problem but supertuxcart and supertux2 work fine, is there an option to start BZFlag in window mode as i think it might help?

---

### Post by TheguywholikesLINUX on 2008-04-21
W00T! :) Success!

I have been searching around, here first, when i found a solution!

go to your bzflag config file. Usually in your home dir under .bzflag or .bzf then edit your config on the line that says: set resolution "*x*    " * being the numbers to half that then try it.
It may look distorted but visible, then go into the options menu > display settings > change resolution. And  change it to your monitors resolution and see if that works.

there should be a option to put it in window mode on start up if that douse not work but i could not find it.

otherwise you will need to update your graphics card and/or drivers.

hope this helps ;-)

LikesLINUX

---

### Post by fahadsadah on 2008-04-27
TheguywholikesLinux: You just brought up a dead thread.

---

### Post by TheguywholikesLINUX on 2008-05-17
???

---

### Post by Cannaregio on 2008-05-19
> **big_dog1968 said:**
> I have the same issue. I ran from terminal and this is what I got:
[B][I][I]
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  136 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x5f
  Serial number of failed request:  146
  Current serial number in output stream:  148[/I][/I][/B]

One simple solution for the problems of your bzflag is to execute this command from a terminal:

```
bzflag -window -geometry 1280x1024+0+0
```

Of course you can change those '[COLOR="Blue"]geometry[/COLOR]' parameters accordingly to your resolution(s).

---

