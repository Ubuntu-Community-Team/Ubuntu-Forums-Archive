---
title: "Synergy, &amp; 2 PC's"
date: 2009-10-17
forum: Networking &amp; Wireless
---

### Post by Gordonisnz on 2009-10-17
Hi,

I'm following an old thread 

[http://ubuntuforums.org/archive/index.php/t-297810.html](http://ubuntuforums.org/archive/index.php/t-297810.html)

and i'm wondering has anyone got a FULL code for the synergy.conf file (using IP addresses)


the examples all give bits & pieces of code, & I'm still having a hard time getting Synergy to work...


if i use 'names' instead of IP addresses - How does Synergy know where the names point to ?

---

### Post by howefield on 2009-10-17
> **Gordonisnz said:**
> if i use 'names' instead of IP addresses - How does Synergy know where the names point to ?

This synergy.conf works for me, with a laptop running XP (xxxx-xp) on the right of a desktop running Ubuntu (xxxx-desktop). Shouldn't matter whether you use IPs or names.

section: screens
        xxxx-desktop:
        xxxx-xp:
end
section: links
        xxxx-desktop:
                right = xxxx-xp
        xxxx-xp:
                left = xxxx-desktop

end

---

### Post by Gordonisnz on 2009-10-17
thanks - Testing now


Just - Are the xxx-desktop thing,  the ACTUAL name of the desktop ? 

Or a made up name..

How do I find out  in Ununtu - the Actual name of PC ?? 
(I think i know in WINXP) - just in case the answer is actual name :)

---

### Post by howefield on 2009-10-17
> **Gordonisnz said:**
> Just - Are the xxx-desktop thing,  the ACTUAL name of the desktop ?

I substituted my actual names with x's.

> How do I find out  in Ununtu - the Actual name of PC ??

You set it up during installation, it is likely to be your login name with -desktop on the end, eg, if your login name is gordonisnz, it would be gordonisnz-desktop.

Unless you changed it during setup, in which case, you would most likely know about it. What does the command prompt say when you open a terminal ?

---

### Post by Gordonisnz on 2009-10-17
> **howefield said:**
> I substituted my actual names with x's.

OK, Ive edited the file now with actual names of both PC's (also the WINXP one)

& restarted both..  - No errors, but it doesn't go...


> **howefield said:**
> 
 You set it up during installation, it is likely to be your login name with -desktop on the end, eg, if your login name is gordonisnz, it would be gordonisnz-desktop.

Unless you changed it during setup, in which case, you would most likely know about it. What does the command prompt say when you open a terminal ?

its gordon-desktop (linux PC)

Ive altered my config file on my winXP one to match...


I suspect that it is not "seeing" my other PC...

WINXP :- I went to "My Computer" >> Properties, & found the "Full Computer Name"..

Went to Linux (Ubuntu) - & ping (FULL COMPUTER NAME)

- it said "host not found"...  

How do I *know* the lunux Pc is actually able to "see" the winxP machine (& vice versa)

---

### Post by Gordonisnz on 2009-10-17
[howefield]("http://ubuntuforums.org/member.php?u=186490") - I replied to you in private messages (twice) on this forum & my sent folder says 0 messages

(I've been on the net a long time - & use forums a lot)

But it still says 0 messages sent.


???

---

### Post by howefield on 2009-10-17
> **Gordonisnz said:**
> [howefield]("http://ubuntuforums.org/member.php?u=186490") - I replied to you in private messages (twice) on this forum & my sent folder says 0 messages

Maybe you have switched off the save copy of sent messages ?

In any case, I got it and replied.

---

