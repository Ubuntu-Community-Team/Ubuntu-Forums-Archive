---
title: "VLC pause doesnt work with lirc"
date: 2009-12-19
forum: Mythbuntu
---

### Post by newbie02 on 2009-12-19
I have vlc working with lirc however they only thing which doesn't seem to work is pause. I have tried other settings a while ago but nothing seem to work. Below is my current setting for pause on lirc. 


```
begin
    remote = mceusb
    prog = vlc
    button = Pause
    config = key-pause
    repeat = 0
    delay = 0
end
```

Any ideas how to get pause with lirc and my remote working?

Thanks 
Newbie02

---

### Post by newbie02 on 2009-12-20
I thought I had tried this .....  so i changed the following and it now works. 

```
begin
    remote = mceusb
    prog = vlc
    button = Play
    config = key-play-pause
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = vlc
    button = Pause
    config = key-play-pause
    repeat = 0
    delay = 0
end

```

---

