---
title: "SLI on 8.04"
date: 2008-05-17
forum: Multimedia Software
---

### Post by wererabbit on 2008-05-17
I wiped my 7.04 installation and have installed 8.04 without any problems.  I have installed the most recent nvidia driver via Envy, and so far it all works great.

I am looking at my specs and it's showing both videocards, but I cannot tell whether it is running in SLI or not.   

Is there a way I can determine whether SLI is active, or toggle it on/off?  

Thank you in advance! :)

---

### Post by wererabbit on 2008-05-18
Bumpitybump

---

### Post by jon_herr on 2008-05-18
First:
sudo nvidia-xconfig --sli=Auto

Then restart X:
<ctrl-alt> + <backspace>

sudo nvidia-settings

Select GPU-0, look for "SLI" in description.

SLI will be enabled at that point.  There are different settings if you are interested like "AFB" - just do a  "sudo nvidia-xconfig -A" for help.

Now riddle me this - does enabling SLI make things better for you or worse?  For me, enabling SLI makes things much worse...  exactly the opposite of what should happen...

Thanks,
Jon

:confused:

---

### Post by wererabbit on 2008-05-19
I haven't had time to test this today, I will do so tomorrow after work and let you know.  Thanks for the help!

---

### Post by wererabbit on 2008-05-25
> **wererabbit said:**
> I haven't had time to test this today, I will do so tomorrow after work and let you know.  Thanks for the help!


Well, I am very late with my response, sorry!  Life caught up with me (i.e. work) and I've not had a lot of time to fiddle with this.  

I did test some today, the toggle to SLI that you suggested seems to have increased my WoW framerates by about 10-20fps. 

I'm working on installing some more games, so I'll repost when I get them tested. 

Thanks again for your help, and again, very sorry about the lack of response here on my part.

---

### Post by jon_herr on 2008-08-06
Hard evidence of something being wrong...

So I did a comparison, same machine booted in windows or linux, same game - Counterstrike Source.

Linux framerate - 20 fps

Windows framerate - 120 fps

Same hardware, same game, incredibly different results.

This used to work?  What happened to Hardy?  Help!  :confused:

Thanks,
Jon

---

