---
title: "Change Startup Screen"
date: 2008-04-14
forum: Mythbuntu
---

### Post by MARKYB0Y on 2008-04-14
Hi All, this is my first post so go easy on me, I have just installed MythBuntu and it seems to be an amazing piece of software, it is the first time I have seen Ubuntu or MythTV working.

I am using my MythBuntu machine just for a movie playback headunit and as such want to know if it is possible to get Mythbuntu to start up in the Media Library > Watch Video screen instead of having to go into these screens? I have been through the config windows etc but have not been able to find anything

thanks for your assistance in advance

---

### Post by laga on 2008-04-14
Hi,

I can think of two options.

* start "mythfrontend video" - that'll immediately load the video plugin, but I don't think you can go back to the main menu. Not sure on that one.

* Use the network control interface to jump to the video screen. It supports "jump points". You can also bind a key on your remote to a jump point.

---

### Post by MARKYB0Y on 2008-04-15
Hi Laga,

thanks for the response, can you be a little more specific please. I am not familiar with Ubuntu or MythTV

start "mythfrontend video", how would I go about doing this? do i need to amend the startup application somehow?

Jump Points sound like a good idea, however I am having issuew with my MCE RF remote at the moment so using keyboard for now

thanks

---

### Post by MARKYB0Y on 2008-04-21
start "mythfrontend video", how would I go about doing this? do i need to amend the startup application somehow?

I am from a windows background so forgive my ignorance

I have not been able to find the mythfrontend application within the file system

can anyone provide simple instructions on how to achieve this

thanks

---

### Post by MARKYB0Y on 2008-04-23
anyone?

---

### Post by superm1 on 2008-04-23
Hi,

laga's was probably meaning for you to try it first on the command line yourself.  If it functions how you want it to, then it can be moved to happen on startup..

Close mythfrontend.  Go to the applications menu and pick the Terminal.


In the Terminal type

```
mythfrontend video
```

---

