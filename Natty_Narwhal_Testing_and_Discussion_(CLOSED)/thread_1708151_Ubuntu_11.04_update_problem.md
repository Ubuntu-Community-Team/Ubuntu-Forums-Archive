---
title: "Ubuntu 11.04 update problem"
date: 2011-03-16
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by JAM3SoN on 2011-03-16
Today morning I installed all updates that were provided by update center and after restart my Ubuntu wont't boot. When I try to run current kernel or older ones, I see only black screen. Update: I booted it again, Ubuntu ran disk control and I am again on checking battery state problem, then on next row is:
^@[...] .... Read BBP 3
...] .... Write BBP 3

100000

and it hangs.

I tried to run recovery mode - when I select failsafeX I end with black screen and according to fan it is working.

My PC is Notebook HP Pavilion Dv7 with Radeon 5600 graphics and I don't remember what I installed - it was pack of ~90MB.

Is it possible to reinstall it or do something else just to make it working?

Thanks!

---

### Post by plucky on 2011-03-16
There is a sub-forum for Natty Narwhal 11.04 problems.
You shouldn't report problems on any other forums until 11.04 is released officially.

[See Here](http://ubuntuforums.org/forumdisplay.php?f=394)

See this [Thread](http://ubuntuforums.org/showthread.php?t=1707879) about your problem.


Good Luck

---

### Post by howefield on 2011-03-16
Moved to "*Natty Narwhal Testing and Discussion*"

---

### Post by Harry33 on 2011-03-16
> **howefield said:**
> Moved to "*Natty Narwhal Testing and Discussion*"

This gdm stopping issue is fixed and fix released:
gdm 2.32.0-0ubuntu11

---

### Post by Dafydd on 2011-03-20
> **Harry33 said:**
> This gdm stopping issue is fixed and fix released:
gdm 2.32.0-0ubuntu11

Thanks.

Solved my freeze at 'checking battery state' by doing:

'ALT + F2' so as to get to a command line.

Then I did:

sudo get-apt update

and then

sudo get-apt upgrade


Dafydd

---

