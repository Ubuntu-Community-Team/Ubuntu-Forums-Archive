---
title: "No sound at all - I tried all the possible tutorials."
date: 2010-12-18
forum: Multimedia Software
---

### Post by Nuker90 on 2010-12-18
Hello, I am Nuker90, a newbie with Ubuntu and Linux (have it for almost 2 months) and I'll try to explain my problem in the most clear way possible so you could hopefully help me.

DESCRIPTION:

Currently I am using Ubuntu 10.10 (I think - when I go at About Ubuntu, it says 11.04, but I updated it from 10.04 and the splash screen says 10.10; also, I've read about a bug on this thing... so I think it's 10.10).

Ok, so I had Ubuntu 10.04 before, running perfect; almost perfect - I had a problem with a strange beep (coming from my motherboard I think), when I restarted the system. Also, I have to say that I had a problem with my sound in the headphones: when I was plugging the headphones in, the sound from the speakers was going off but I was still not getting sound on the headphones; I figured it out in the end and it worked perfectly (updating some alsa drivers and things like these, if I remember well - also editing some cfg files).

Ok, now what is the problem: I updated, as stated, to Ubuntu 10.10, hoping to get rid of the strange beep. Everything went well, the beep went off but the alsa drivers got replaced. And the problem with the headphones appeared again.
Therefore, I tried to fix it again, by updating alsa drivers but ended up destroying everything :(. There was no more sound from the speakers and, when I went to the Sound options -> Output, there was a DUMMY OUTPUT (or SPEAKERS) option checked.

WHAT I HAVE TRIED:

I have tried to use this guide  ([http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)) to reinstall everything but I encountered an error when I was compiling the drivers (sudo module-assistant a-i   alsa-source   - in this point). Therefore, I am currently in that stage of "fixing" the problem. Also, I have to tell you that I have the   hda-intel   module for my sound card (that's what it says and what I remember from when it worked).


So, this is my problem. Hopefully someone will have the time to read everything and try to assist me in fixing it.I'd really appreciate that. 

Thank you,
Nuker90



PS: There's one more little thing that I want to ask whoever reads and is willing to help me - whenever I start Ubuntu / shut it down, I get some lines of "code" or lines of messages that prompt on my screen - is it normal for 10.10? 

Thank you again!

---

### Post by akand074 on 2010-12-18
You probably don't have 10.10, but you have 11.04. The most up to date 11.04 still says 10.10 in the boot splash. Do you have your proprietary drivers installed (System > Administration > Additional Drivers). You would be able to tell if your using 11.04 if they are installed because your using Unity instead of gnome-shell (which uses global menus and has a panel going through the left side of your screen) unless because you did an upgrade they don't activate by default.

Either way, I'd do a clean install of 10.10 if I were you. Also you can edit sound settings from System > Preferences > Sound. You can mute the alert volume to stop system beeps. Also make sure you have the correct hardware settings in the hardware tab.

---

### Post by Nuker90 on 2010-12-18
Hello akand074, thank you for the reply.

Well I know that one of the solutions is by reinstalling everything but I don't really want to do that... that's why I am posting here - also because on the stated tutorial, it was said that if I encounter an error while compiling the drivers, I should start a thread about this... So I am hoping that there is another solution to this, that does not require reinstalling the whole operating system...

Thank you again for your suggestion.

If anyone has other ideas, please help... 

Thank you,
Nuker90

---

### Post by akand074 on 2010-12-19
> **Nuker90 said:**
> Hello akand074, thank you for the reply.

Well I know that one of the solutions is by reinstalling everything but I don't really want to do that... that's why I am posting here - also because on the stated tutorial, it was said that if I encounter an error while compiling the drivers, I should start a thread about this... So I am hoping that there is another solution to this, that does not require reinstalling the whole operating system...

Thank you again for your suggestion.

If anyone has other ideas, please help... 

Thank you,
Nuker90

Well, what I was saying is if you verified that you were indeed running 11.04, then you should do a clean install of 10.10. Because 11.04 is in it's Alpha 1 stage. It's nowhere near stable so you'll find yourself with tons of issues. If you are indeed in 10.10 then yes trying to find a solution is the better choice.

---

### Post by Nuker90 on 2010-12-19
I just checked and I have 11.04... There is no way of getting to 10.10 without losing my settings / programs?

---

### Post by akand074 on 2010-12-19
> **Nuker90 said:**
> I just checked and I have 11.04... There is no way of getting to 10.10 without losing my settings / programs?

Unfortunately, there is no way of going backwards without losing your settings programs. I recommend you make a separate /home partition in the future, that way with clean installs your config files and data are untouched. [This]("http://ubuntuforums.org/showpost.php?p=8113316&postcount=3") is also something you can try, but not sure if it will cause problems seeing as it'll probably install 11.04 stuff too, but I guess for future reference. 

You could also stick with 11.04 and still try to fix your problem (I would recommend posting about it in the Natty Narwhal Testing Forums) but again, it's in the alpha 1 stage so you might run into stability issues/crashes frequently.

---

