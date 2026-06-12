---
title: "&quot;Aready-running&quot; specific commands launch Totem"
date: 2008-11-25
forum: Multimedia Software
---

### Post by humble_coffee on 2008-11-25
In the man page for Totem, there is a section of command line options which it says the following about:

"The following options command an already-running instance of  Totem  to do something; they are useful for remote-control scripting:"

eg:

```
totem --play-pause
totem --play
totem --next
```

I read this as saying that these actions should only be performed if Totem is already running. However, if the player is not already-running and I run the totem command with any of these options, the player then launches. It doesn't do any of these actions then (cos there's no file loaded maybe) but the point is, shouldn't the player not load at all if it wasn't running? This makes it pretty much useless for me for a remote control button.

---

### Post by humble_coffee on 2008-12-07
This is probably one of those things that won't get fixed for ages if it ever does. So he's a workaround I came up with for anyone who runs across the same problem.

If you wanted to run this command:


```
totem --play-pause
```

Instead run this:

```
if [ `ps -C totem | wc -l` != 1 ]; then totem --play-pause; fi
```

It will only execute the command if it does not find a process called 'totem'.

---

