---
title: "script for music to start at set time"
date: 2008-11-25
forum: Multimedia Software
---

### Post by kadafi69 on 2008-11-25
is there a script i can run so that i can have rhythmbox to start at a particular time, or to have the start delayed by a set amount of time?

---

### Post by m_duck on 2008-11-25
I'm not sure on how to do the former, but the latter could be solved with a simple bash script. Something like ```
#!/bin/bash
sleep ##
rhythmbox &
```I think would do the trick. Where ## is the time in seconds you want delayed from executing the script. You will need to navigate to where you save the script, right click, properties, permissions tab and check the box that says "Allow executing file as program". Then you could create a launcher that runs this script, or if you want the program to run at log in (to start ## seconds after you have logged in), add an entry to System -> Preferences -> Sessions e.g.
```
Name: Rhythmbox
Command: /path/to/above/script
Comment: Delayed Rhythmbox start
```

---

### Post by kadafi69 on 2008-11-25
ive given that script a bash, ill see how i get on with it. ta

---

### Post by kadafi69 on 2008-11-26
that didnt work, just gave a propmt to go to rhythmbox, it didnt actually start the music

---

### Post by tharsan on 2008-11-26
I'm not sitting at my Linux terminal right now, but try:

```

rhythmbox --help

```

to see what the command line options are.  you should be able to provide a filename on the command line.

also, you should use a cron job instead of sleep in a batch script.
for more information on cron, check out the official Ubuntu help article on [CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by m_duck on 2008-11-26
Oh sorry, I misunderstood, I don't know how to make it start playing specifically. Also, similar to above, also check out ```
rhythmbox-client --help
```I've had a bit of a play but can't make the music start automatically.

Looking at the above, it looks like a cron job is the way to go to make it start at a specific time, but I do not really have any knowledge of using them. Even so it will still be necessary to make rhythmbox start playing so I will see what I can find...

EDIT: Cheers tharsan for the cron link. I knew it existed but have never got round to playing with it before. Procrastination awaits! :D

---

