---
title: "Problems with Totem"
date: 2008-07-26
forum: Mythbuntu
---

### Post by AJ1000 on 2008-07-26
I am trying to use Totem as the front end, and I have the plugin installed. I get this error message when I try to use it:

'Totem could not play this media (Digital Television) although a plugin is present to handle it.'

Everything works fine with the Mythbuntu front end, but I was wondering why the above error message was happening with Totem. 

I am new to Linux and these forums, so forgive me if this issue is elsewhere on these forums. As a newbie, I am very impressed with Mythbuntu (the 8.04.1 version).

---

### Post by mal on 2008-07-26
AJ1000,

If you have the mythtv backend running, I think totem will not be able to get control of your TV tuner.  I've found that I have to stop the backend while viewing TV on another application.  You just have to remember to start the backend again, or it won't record any of your scheduled shows.

Hope this helps.

Mal

---

### Post by AJ1000 on 2008-07-26
As I have said before, I am a newbie. What is the best way to stop the backend?

---

### Post by mal on 2008-07-26
Try the following commands from a terminal window (Applications/Accessories/Terminal):

To stop mythbackend:

```
$ sudo invoke-rc.d mythtv-backend stop
```

and to start it:

```
$ sudo invoke-rc.d mythtv-backend start
```

Let me know if I can help further.

Mal

---

### Post by AJ1000 on 2008-07-26
Mal,

Thanks, it worked but I can not hear any sound. Do you have any ideas why?

Ajay

---

### Post by mal on 2008-07-26
The sound issue is a bit more complicated.

Do you get sound with other applications?  Do you get sound when playing mythtv recordings? 

There are a few threads in the forums discussing various fixes for sound problems with Hardy.  These might also give you some good pointers.

Mal

---

### Post by AJ1000 on 2008-07-26
Mal,

Thanks, Totem works perfectly for everything else. I have decided to stick with Mythbuntu front end as I found out how to display it as a window rather than full screen.

Ajay

---

### Post by mal on 2008-07-26
That's probably a good idea.  These plug-ins for totem seem to be still a bit buggy.

Regards,

Mal

---

### Post by AJ1000 on 2008-07-26
For anyone who wants to know the command is:

mythfrontend -w -geometry 800x600+10+100 

(where 800 is the width of window, 600 is the height of window, 10 is the X position of the window and 100 is the Y position of the window)

---

