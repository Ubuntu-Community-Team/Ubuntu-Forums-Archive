---
title: "MythTv one channel error"
date: 2007-01-08
forum: Multimedia &amp; Video
---

### Post by mfinch on 2007-01-08
Hello, I have never posted here before and thank you for your help in advance.

I recently successfully installed MythTv. I apologize that I am not home currently to provide my technical information, but I was hoping to get a head start on the solution before I return today. I will be happy to provide more information later.

I am using the Happauge PVR 350 for recording as well as my video-out to the television. All of the channels work and record, except for channel 5. 

Channel 5 shows the video, but it is black and white, and no sound is output for live tv. This is the same way that it records, with black and white video and no sound.

I am a very new unbuntu and mythtv user, and while I am very good at following step by step instructions, I am not very technically knowledgeable. 

So far I have tried refilling the database with the channel information, and this did not change anything on this channel.

I would appreciate any ideas on where to start to work on this, or if there are any guides that help with this type of problem (I haven't found anything yet, but I have only been skimming forums and guides). Thank you!

---

### Post by majoridiot on 2007-01-08
it sounds like the frequency for that channel needs tweaked a little.  unfortunately, the only
way to do that atm is by hand- adjusting the appropriate mysql table.  you can do this by
installing phpmysql, which is a browser-based interface or by installing mythweb, which
reportedly allows for frequency tweaking, although i do not use it, so i can't verify it.

chances are you need to adjust the frequency a very small amount, as you have some
picture but no color/sound info.  i'd work it in degrees of +/- 100Hz to begin with.

---

### Post by mfinch on 2007-01-09
Great, thank you for the idea.

I have phpmyadmin installed. I'm not sure exactly what field to edit to make this change. I log in and go to the mythconverg database. There is a table called "channel" that I can access, but none of the fields there seem to be the frequency for the channel. There is one called freqid, but it just states 5 for the channel. What should I be changing?

Thank you much for the help and sorry for the simple questions!

---

### Post by majoridiot on 2007-01-09
i believe the field you are looking for is called "finetune".  i'm not at home to look at my
mythconverg, but i would start there.  frequencies in the db are generally listed in Khz.

reports are that these tweaks are easy in mythweb... you might consider installing that if
doing it by hand isn't working.  i can't verify that it is as i don't use mythweb.

EDIT:

ok... i took a look and found it.  log into phpmyadmin, and select database mythconverg from the
dropdown on the left.  in the table list that comes up in the right pane, you will see table **channel**
click on the first icon to the right of **channel** to browse it.  this brings up the channel entries...

find your channel 5 and click the pencil to edit it.  you should find "finetune" in the edit list-
it's #8 on mine.  unclick the null box and give it a value.  i suggest working increments of
+/- 100 (assumes value is Khz).  select "Save" in the dropdown at the bottom of the page,
"Go back to this page" in the dropdown next to it and then hit the "Go" button to save it.

you should tune to another channel and then back to the one you are tweaking after each
adjustment, to make sure the values are refreshed from the db.

good luck! :D

---

### Post by mfinch on 2007-01-14
Thank you much for the help! I finally found the time to sit down and give this method a try, and I was able to adjust the tuning of a couple channels that I found. Thank you again for the help, especially the step-by-step instructions through the database!

---

### Post by majoridiot on 2007-01-14
glad you got it working! :D

out of curiosity, how far were the channels off?

---

### Post by mfinch on 2007-01-15
They both worked when I entered 1500 for the finetuning, though I think channel 6 needs a bit more tweaking, as the color is a bit off but still very close.

---

### Post by majoridiot on 2007-01-15
great- thanks for the info.  hopefully it will be of use to folks having similar issues.

---

### Post by majoridiot on 2007-01-16
also, for complete info for anyone who finds this thread later-

when making the freq adjustments to the database, did you need to restart the backend and/or
frontend after each change, or could you make the change and see the result from just tuning
to a different channel and then back to the one you were adjusting?

---

### Post by bendt on 2007-01-18
It seems to be enough to just leave the channel and "LiveTV/Watch TV", and go back. That worked for me at least.

---

### Post by majoridiot on 2007-01-18
useful information... thanks again. :D

---

