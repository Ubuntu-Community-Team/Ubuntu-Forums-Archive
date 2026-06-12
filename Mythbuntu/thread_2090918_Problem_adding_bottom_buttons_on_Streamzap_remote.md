---
title: "Problem adding bottom buttons on Streamzap remote"
date: 2012-12-03
forum: Mythbuntu
---

### Post by pjbgravely on 2012-12-03
I am trying to add the red, green and yellow buttons to lirc in Mythbuntu 12.04. I added them to ~/.mythtv/lircrc as normal then restarted lirc and they won't work. I know it isn't the install because a previous install with a tuner problem did they same thing. The end to my lircrc file is:
```
begin
    remote = Streamzap_PC_Remote
    prog = mythtv
    button = KEY_FORWARD
    config = >
    repeat = 0
    delay = 0
end

#added

begin
    remote = Streamzap_PC_Remote
    prog = mythtv
    button = RED
    config = w
    repeat = 0
    delay = 0
end

begin
    remote = Streamzap_PC_Remote
    prog = mythtv
    button = GREEN
    config = O
    repeat = 0
    delay = 0
end

begin
    remote = Streamzap_PC_Remote
    prog = mythtv
    button = YELLOW
    config = C
    repeat = 0
    delay = 0
end

```

I am assuming something changed in 12.04 that makes this no longer work. I have searched everywhere for another lircrc file but have come up empty handed. Any help would be much appreciated.

---

### Post by nickrout on 2012-12-05
> **pjbgravely said:**
> I am trying to add the red, green and yellow buttons to lirc in Mythbuntu 12.04. I added them to ~/.mythtv/lircrc as normal then restarted lirc and they won't work. I know it isn't the install because a previous install with a tuner problem did they same thing. The end to my lircrc file is:
```
begin
    remote = Streamzap_PC_Remote
    prog = mythtv
    button = KEY_FORWARD
    config = >
    repeat = 0
    delay = 0
end

#added

begin
    remote = Streamzap_PC_Remote
    prog = mythtv
    button = RED
    config = w
    repeat = 0
    delay = 0
end

begin
    remote = Streamzap_PC_Remote
    prog = mythtv
    button = GREEN
    config = O
    repeat = 0
    delay = 0
end

begin
    remote = Streamzap_PC_Remote
    prog = mythtv
    button = YELLOW
    config = C
    repeat = 0
    delay = 0
end

```

I am assuming something changed in 12.04 that makes this no longer work. I have searched everywhere for another lircrc file but have come up empty handed. Any help would be much appreciated.

These days should those be KEY_GREEN (and so on)?

---

### Post by pjbgravely on 2012-12-05
Thanks, that was it. I will have to see if I can add to the mythtv wiki so others don't fall for that.

---

