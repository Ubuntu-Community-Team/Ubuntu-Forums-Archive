---
title: "Xine keymappings, up/down etc. do not work"
date: 2009-04-15
forum: Mythbuntu
---

### Post by mathog on 2009-04-15
Mythbuntu 8.10.  Lirc is fully debugged and all keys on the remote work (for instance, in irw or when mapped, in MythTV).  Xine works with the keyboard, and some keys work with Lirc, but others don't.  In particular, the up/down/left/right keys are no go.  Here for instance is the entry for the up key (which is ignored)

```
begin
    remote = RM-VL600_8201
    prog = xine
    button = up
    config = EventUp
    repeat = 0
    delay = 0
end

```
I tried changing EventUp to "Up", restarting lircd, but it made no difference.  Changed EventUp to Quit and then the up arrow caused it to quit.  The odd thing is that the keyboard "Up" arrow key works just fine, as do most of the other remote keys (Quit, Menu, Info...).
It seems that just the Event* ones are ignored. 

Does Xine expect something other than EventUp, or maybe it is not set somehow to recognize EventUp?

---

### Post by mathog on 2009-04-15
Does the lack of any answers mean nobody has this working or everybody does?  If the latter, will one of you please post the relevant part of your Xine lirc file.

Thanks.

---

### Post by nickrout on 2009-04-15
What do you want the key to do? If its to go forward/back in the video you want some lines like this: (source [http://www.flamingspork.com/junkcode/lircrc](http://www.flamingspork.com/junkcode/lircrc))

```
# set position to -60 seconds in current stream
begin
	button = xxxx
	prog   = xine
	repeat = 4
	config = SeekRelative-60
end

# set position to +60 seconds in current stream
begin
	button = xxxx
	prog   = xine
	repeat = 0
	config = SeekRelative+60
end

# set position to -30 seconds in current stream
begin
	button = xxxxx
	prog   = xine
	repeat = 0
	config = SeekRelative-30
end

# set position to +30 seconds in current stream
begin
	button = FINE_UP
	prog   = xine
	repeat = 4
	config = SeekRelative+30
end

# set position to -15 seconds in current stream
begin
	remote = xxxxx
	button = xxxxx
	prog   = xine
	repeat = 0
	config = SeekRelative-15
end

# set position to +15 seconds in current stream
begin
	remote = xxxxx
	button = xxxxx
	prog   = xine
	repeat = 0
	config = SeekRelative+15
end
```

---

### Post by mathog on 2009-04-16
> **nickrout said:**
> What do you want the key to do?
With the keyboard, **Up** increases the forward speed, **Down** increases the reverse speed.  I want the same thing to happen with the remote.

---

### Post by nickrout on 2009-04-16
> **mathog said:**
> With the keyboard, **Up** increases the forward speed, **Down** increases the reverse speed.  I want the same thing to happen with the remote.

from the look of ~/.xine/keymap you need to map up and down to SpeedFaster and SpeedSlower

---

### Post by mathog on 2009-04-16
> **nickrout said:**
> from the look of ~/.xine/keymap you need to map up and down to SpeedFaster and SpeedSlower

Perfect.  I ended up adding this:


```
begin
    remote = RM-VL600_8201
    prog = xine
    button = chan+
    config = SpeedFaster
    repeat = 0
    delay = 0
end
begin
    remote = RM-VL600_8201
    prog = xine
    button = chan-
    config = SpeedSlower
    repeat = 0
    delay = 0
end
```

because the up/down arrows were needed for navigating in the menu. 

Heads up - there was a typo in my original Xine .lirc file, which was automatically generated, so it might be on other systems too. "EvenPrior" instead of "EventPrior".

Thanks.

---

