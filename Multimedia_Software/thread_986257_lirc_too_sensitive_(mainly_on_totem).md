---
title: "lirc too sensitive (mainly on totem)"
date: 2008-11-18
forum: Multimedia Software
---

### Post by hachel on 2008-11-18
hello,
seeking and volume-adjustment is far too sensitive.
pressing the seek-forward-button forwards a whole minute, backwards only 15 seconds. Volume is similar.
How would I adjust the sensitivity? I read that the repeat-option in your lircrc could do that for you but there seemed to be no effect whatsoever, whether I set repeat to 1 or to 1000.
This is the part of my lircrc:
```
begin
	prog = totem
	button = CD_Forward
	config = seek_forward
end

begin
	prog = totem
	button = CD_Rewind
	config = seek_backward
end

begin
	prog = totem
	button = Tuner_Preset+
	config = volume_up
end


begin
	prog = totem
	button = Tuner_Preset-
	config = volume_down
```

---

### Post by ednotele on 2009-01-03
> **hachel said:**
> hello,
seeking and volume-adjustment is far too sensitive.
pressing the seek-forward-button forwards a whole minute, backwards only 15 seconds. Volume is similar.
How would I adjust the sensitivity? I read that the repeat-option in your lircrc could do that for you but there seemed to be no effect whatsoever, whether I set repeat to 1 or to 1000.
This is the part of my lircrc:
```
begin
	prog = totem
	button = CD_Forward
	config = seek_forward
end

begin
	prog = totem
	button = CD_Rewind
	config = seek_backward
end
...

```

Hello hachel,

You can try with the following:
```
begin
	prog = totem
	button = CD_Forward
	config = seek_forward:20
end

begin
	prog = totem
	button = CD_Rewind
	config = seek_backward:10
end

```

where 20 and 10 can be custom values (in seconds).

---

