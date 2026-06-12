---
title: "[SOLVED] SDL Mame  mythtv config...."
date: 2008-09-04
forum: Mythbuntu
---

### Post by u!mp3 on 2008-09-04
Hi, i am triying to configure sdl mame 0.127 to mythtv...

SDL mame is working in ubuntu but I'm stuck in the procces to find the right command to launch it from mythtv...

I have tried 

1.- sldmame
2.- /usr/games/sdlmame

without luck...

any help would be highly aprecciated

---

### Post by Jeeeepers on 2008-09-05
> **u!mp3 said:**
> Hi, i am triying to configure sdl mame 0.127 to mythtv...

SDL mame is working in ubuntu but I'm stuck in the procces to find the right command to launch it from mythtv...

I have tried 

1.- sldmame
2.- /usr/games/sdlmame

without luck...

any help would be highly aprecciatedgive this a try , 

```
/usr/games/sdlmame/mame %s
```

---

### Post by u!mp3 on 2008-09-11
I haven't the opportunity to test it....
I will try tonight, :guitar: let you know, thanks for your reply...

---

### Post by u!mp3 on 2008-09-14
It's not working, the screen actually load the game from 0 to 100% but then it come back to the roms select menu, sometimes just flash the black screen and comeback ....

any ideas....

thank you...

---

### Post by u!mp3 on 2008-09-14
I solve it.........made a fresh sdlmame install and in mythtv game config  use

/usr/games/sdlmame %s

---

