---
title: "Classic Gnome?"
date: 2011-04-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by osarusan on 2011-04-05
When I load the classic gnome session, I get Unity, just the same as when I load the regular Ubuntu session.

In fact, the only way I can get the regular Gnome panel is by running the (No Effects) session.

Am I crazy, or isn't Classic Gnome supposed to be *not* Unity?

---

### Post by robert shearer on 2011-04-05
Yeah, somthing odd is happening.
For the last few days (since beta) whenever I try to log in to Unity or Ubuntu Classic the screen blanks and then I am returned to the log-in screen.

I have re-installed GDM but that did not help.

Currently I can run only Unity 2D or Gnome no effects.
Previously I could run all desktop options.

Hope this shakes down before Final....:(

---

### Post by Harry33 on 2011-04-05
> **robert shearer said:**
> Yeah, somthing odd is happening.
For the last few days (since beta) whenever I try to log in to Unity or Ubuntu Classic the screen blanks and then I am returned to the log-in screen.
I have re-installed GDM but that did not help.
Currently I can run only Unity 2D or Gnome no effects.
Previously I could run all desktop options.
Hope this shakes down before Final....:(

What was the update, that caused this?
Was it really gdm 2.32.0-0ubuntu15?
or
was it gnome-session 2.32.1-0ubuntu18?

---

### Post by robert shearer on 2011-04-05
> **Harry33 said:**
> What was the update, that caused this?
Was it really gdm 2.32.0-0ubuntu15?
or
was it gnome-session 2.32.1-0ubuntu18?

I don't have gdm 2.32.0-0ubuntu15, my version is gdm 2.32.0-0ubuntu14 and Synaptic lists this as the latest.

I do have gnome-session 2.32.1-0ubuntu18.
Are you suggesting this is the cause ? and if so how to fix the log-in problem ??.

---

### Post by cecilpierce on 2011-04-05
I'm having about the same thing, my default login is Classic Gnome and it always boots into Ubuntu Unity.

---

### Post by Harry33 on 2011-04-05
> **robert shearer said:**
> I don't have gdm 2.32.0-0ubuntu15, my version is gdm 2.32.0-0ubuntu14 and Synaptic lists this as the latest.

I do have gnome-session 2.32.1-0ubuntu18.
Are you suggesting this is the cause ? and if so how to fix the log-in problem ??.

Depends on did you notice the issue after that particular update.
If you did, you might want to try downgrade to the previous version:
gnome-session_2.32.1-0ubuntu17

[https://launchpad.net/ubuntu/natty/+source/gnome-session/2.32.1-0ubuntu17](https://launchpad.net/ubuntu/natty/+source/gnome-session/2.32.1-0ubuntu17)
(choose the architecture first).

---

### Post by osarusan on 2011-04-08
The problem seems to have evolved since I posted it... now I can log in to Unity, but I can't load the "Classic Gnome" session at all.

Or, rather, I can log in to it, but I get a mouse and a desktop with no panels, no launcher, and I can't use alt-f2 or anything at all. The only thing I can do is ctrl-alt-backspace back to the login screen.....

---

