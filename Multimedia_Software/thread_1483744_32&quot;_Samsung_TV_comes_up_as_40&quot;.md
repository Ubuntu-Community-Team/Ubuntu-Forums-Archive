---
title: "32&quot; Samsung TV comes up as 40&quot;"
date: 2010-05-14
forum: Multimedia Software
---

### Post by thefish123 on 2010-05-14
Hi everyone,



Under Ubuntu 9.10 I used to hook up my 32" Samsung TV to my notebook via the external VGA/video port and use this to watch TV shows via the internet (using CastTV.com or globaltv.com).  This worked quite well.

However, since upgrading to 10.04 I haven't been able to do this.  Under 10.04 my TV comes up as a 40" Samsung (which it's not) and the screen is all jittery.  I have tried different resolutions and it is either blank or "jittery" (for lack of a better word).  

How can I get Ubuntu to correctly identify my TV at a 32 inch?


Any help would be appreciated.


Thanks,

The Fish

---

### Post by thefish123 on 2010-05-15
Just to add some more info.  The TV is a "[Samsung LN-T3232H]("http://www.samsung.com/ca/support/download/supportDown.do?group=&group_cd=&type=tv&type_cd=02010000&subtype=lcd&subtype_cd=02010100&model_nm=LN-T3232H&dType=D&mType=&model_cd=&menu=download&prd_ia_cd=02010100&disp_nm=LN-T3232H&language=")".  Under 9.10 this came up as a 32" Samsung TV in gnome-display-properties.

Under 10.04 it comes up as a 40" Samsung TV and does not have a clear display.

Thanks,
The Fish

---

### Post by thefish123 on 2010-05-18
Sorry to bump this thread but does anyone have any idea?  Essentially the TV is an external monitor.  Does anyone know what might have changed between 9.10 and 10.04 that would cause Ubuntu to now  incorrectly identify my TV?

Does anyone else have trouble connecting external displays to Ubuntu 10.04?

Thanks,
The Fish

---

### Post by thefish123 on 2010-05-21
Sorry to keep bumping my own thread but I find it hard to believe no one has any suggestions on what I might look for.  Even just a link to a website that might help with troubleshooting would be good.  I really have very little idea where to start.

PS: not being able to watch TV on the internet is a “mission critical” problem for me :-)

Regards,
The Fish

---

### Post by Manyette on 2010-05-21
Sorry that I can't help, but just FYI, my Toshiba is a 32" but always shows up as a 40" TV.  I think because they use they same set of electronics in both.  Perhaps you might forget the "inches match", and look elsewhere for the problem.  Mine works fine despite the misidentification.  Wish I could be of more help.

---

### Post by thefish123 on 2010-05-23
> **Manyette said:**
> Sorry that I can't help, but just FYI, my Toshiba is a 32" but always shows up as a 40" TV.  I think because they use they same set of electronics in both.  Perhaps you might forget the "inches match", and look elsewhere for the problem.  Mine works fine despite the misidentification.  Wish I could be of more help.Hi Manyette,

Thanks for the information.  I am not really sure where to look or how to troubleshoot this problem.  I am &#8220;comfortable&#8221; with Linux and know my way around the command line.  I am not too afraid of editing text files, etc...  but I am not an expert.

I think the main issue is that the available resolutions that come up in &#8220;gnome-display-properties&#8221; are not right for my TV.  I am pretty sure that the proper &#8220;native&#8221; resolution for my TV is 1280x720.  I know for certain the aspect ratio is 16:9 or 4:30 (this is configurable using the TV's on-screen menu).  However the only 16:9 resolution that I have available in &#8220;gnome-display-properties&#8221; is 1360x768 @ 60 Hz which results in the &#8220;jittery&#8221; display on the TV.   The other one that produces an image on the TV is 1024x768 @ 75 Hz which results in a very strange &#8220;wavy&#8221; display on the TV.

How can I override the list of available resolutions and specify one that isn't there?

Best regards,
The Fish

PS: thanks so much for taking the time to read my question and respond.  I know we all have other things to do then try to solve other people's problems :-)

---

### Post by Manyette on 2010-05-23
Hi,
To be honest, I believe you are probably more knowledgeable than I am.  I really don't understand most of gnome's resolution settings, and was lucky enough that mine came up without that kind of problem, because if it hadn't, I probably couldn't have fixed it either.  Hopefully this will bump the thread, and someone knowledgeable about Gnome's resolution setting will respond.  Mine is 1600 x 900, and was immediately recognized by the system.  Just lucky, I guess.  Hope someone else who knows more that this noob will come to your aid.  Wish you luck!

---

### Post by thefish123 on 2010-05-23
> **thefish123 said:**
> However the only 16:9 resolution that I have available in “gnome-display-properties” is 1360x768 @ 60 Hz which results in the “jittery” display on the TV.   The other one that produces an image on the TV is 1024x768 @ 75 Hz which results in a very strange “wavy” display on the TV.I just double-checked on the Samsung website and the official word from Samsung is that I should be using 60 Hz when connecting my TV to my computer.  So it would seem that the issue is just that 1360x768 @ 60 is too high.  I need to "add" the option of 1280x720.

Thanks again,
The Fish

---

### Post by thefish123 on 2010-05-27
> **thefish123 said:**
> I think the main issue is that the available resolutions that come up in “gnome-display-properties” are not right for my TV.  I am pretty sure that the proper “native” resolution for my TV is 1280x720.  I know for certain the aspect ratio is 16:9 or 4:30 (this is configurable using the TV's on-screen menu).  However the only 16:9 resolution that I have available in “gnome-display-properties” is 1360x768 @ 60 Hz which results in the “jittery” display on the TV.   The other one that produces an image on the TV is 1024x768 @ 75 Hz which results in a very strange “wavy” display on the TV. [...] How can I override the list of available resolutions and specify one that isn't there?Sorry to keep bumping my own thread but does anyone have any idea how I can add a new resolution option to gnome-display-properties?  I can’t believe I am the only one who has had this kind of a problem.

Best regards,
The Fish

---

### Post by Pumuky on 2010-12-07
Hi
Sorry for my bad english. I don't know the solution but i have the same problem. I try to conect the Toshiba Satellite PSA40E with Intel graphics to Samsung 46'' TV. When I start the computer with vga cable plugin the screen of tv "jittery". I can not conect the labtoop and TV at same time and wath two screen.
¿do you solve this problem?

---

### Post by hairy one on 2011-04-01
Going from 32" to 40" would make it Sams-Hung. Sooo, sorry could not help myself!!!!!

---

