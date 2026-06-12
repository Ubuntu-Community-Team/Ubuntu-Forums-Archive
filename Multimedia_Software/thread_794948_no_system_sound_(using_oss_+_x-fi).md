---
title: "no system sound (using oss + x-fi)"
date: 2008-05-15
forum: Multimedia Software
---

### Post by kasatka on 2008-05-15
i have problem with my sound.. so i'am using oss driver for my x-fi, and the problem is , i don't have system sound (login sound dll). but i can listen to music (amarok) or film (vlc)

i check System->preferences->sound , and there is no "default mixer track".. is that why i don't have desktop sound ? 

i also test the "system sound", i pressed the test button i don't hear anything, so can someone help me?

---

### Post by goofeyfoot on 2008-05-16
Yeah:

I am having the same problem.

I also have X Fi.

I didn't have any sound so I did what they said in the following link.[http://ubuntuforums.org/showpost.php?p=4874981&postcount=2](http://ubuntuforums.org/showpost.php?p=4874981&postcount=2)

I guess that gives you something called OSS.  Whatever that is.

Net result.  I still don't have any sound.

Can anyone tell me what to do?  I'm not a technical wizard so please keep it simple.  Can I have sound?  Or not?  If so, how do I get it.That's all I am asking.

Thanks.

Michael

---

### Post by kasatka on 2008-05-17
is your oss installation success ? test your oss driver first

go to console, do this command $osstest

if you can hear the sound than the driver is actualy working

---

### Post by goofeyfoot on 2008-05-17
kasatka:

No when I run your command I don't hear any sound.  So what do I do now?:confused:

---

### Post by goofeyfoot on 2008-05-17
One more question.

Is there a book I can just read to understand all this Ubuntu stuff?

These forums are good but it takes a month of Sundays to find anything out.  I have spent a year with a distribution with no wireless and no sound.  Won't live long enough to learn anything this way.

Is there a book or a video or something?

Thanks.  

Michael

---

### Post by goofeyfoot on 2008-05-19
Hello...anyone out there?  Hello?

---

### Post by kasatka on 2008-05-21
sorry.. this week i have a lot of homework to do , so i can't check the forums.. 

> kasatka:

No when I run your command I don't hear any sound. So what do I do now?

this mean that you don't install the oss driver correctly.. you sould hear sound when you run the osstest or maybe you don't turn on the sound yet (sudo soundon)

there is a guide about installing oss driver in the forum (i forgot the link)

---

### Post by goofeyfoot on 2008-05-22
Does anyone know how you get this oss thing working?  Is there a link like the gentleman says?  I tried something like that and thought it did something.  It looked like it did.  But I still don't get any sound.  Would appreciate a word of advice or even a link to some straightforward directions.

Thanks.

Michael

---

### Post by Yellow Pasque on 2008-05-22
[http://ubuntuforums.org/showpost.php?p=5019494&postcount=89](http://ubuntuforums.org/showpost.php?p=5019494&postcount=89)

---

