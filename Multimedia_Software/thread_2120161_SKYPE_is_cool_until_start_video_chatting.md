---
title: "SKYPE is cool until start video chatting"
date: 2013-02-25
forum: Multimedia Software
---

### Post by BrianBlaze on 2013-02-25
I have a problem with my Asus K53sv and Ubuntu 12.10.

I use skype to chat and it works just fine but as soon as I do voice or video chat my skype crashes. I am wondering if anyone knows where a crash file may be so I can read what happened or if they have heard of this problem and have a solution.

Thanks in advance!

---

### Post by BrianBlaze on 2013-02-25
It seems to be working now I don't like having **** unsolved so I will say this is solved but still if anyone knows where the error files are I would appreciate it

---

### Post by xc3RnbFO8P on 2013-02-26
You can start Skype from terminal
> skype 
or:

> 
Close Skype
Create directory “Logs” under your Skype data directory (~/.Skype/)
Restart Skype
Log file (skype_yyyy-mm-dd-hhmmss) will be created in ~/.Skype/Logs
To turn off logging again, delete the “Logs” directory

---

