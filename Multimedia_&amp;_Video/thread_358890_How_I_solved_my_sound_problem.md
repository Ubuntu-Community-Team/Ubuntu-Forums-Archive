---
title: "How I solved my sound problem"
date: 2007-02-11
forum: Multimedia &amp; Video
---

### Post by PaulFXH on 2007-02-11
I struggled with a lost sound problem on my Dell Dimension 4550 running Edgy and WinXP for more than a week. I'm posting here so that somebody else may possibly benefit from avoiding my difficulties.

Lost sound suddenly in Ubuntu for no apparent reason although sound still played perfectly in Windows.
I went through most of the Ubuntu sound problem documentation (including:
 [http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound](http://www.ubuntuforums.org/showthread.php?t=205449&highlight=sound), 
[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems), 
[https://help.ubuntu.com/community/HowToSetupSoundCards](https://help.ubuntu.com/community/HowToSetupSoundCards) 
as well as very many posts to this forum on similar problems.
Although I learnt a lot, I didn't solve my problem.

Then, out of desperation I tried muting and unmuting all of the entries in alsamixer and only then I stumbled on the Analog/Digital Output Jack which I had switched ON (following the guideline that everything in Alsamixer should be ON and Unmuted).
Only when I switched this OFF did sound come back.

OK, that's my experience. If anybody knows anything more about why this needs to be switched off I'd be interested to hear.

---

### Post by scrooge_74 on 2007-02-11
Seems you ran into the same proplem lots of people had. I will add those links to my list of tips I have, you never know when I might need them

---

