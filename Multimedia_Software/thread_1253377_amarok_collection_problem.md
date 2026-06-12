---
title: "amarok collection problem"
date: 2009-08-30
forum: Multimedia Software
---

### Post by whalescreams on 2009-08-30
I want amarok to only play from a specific folder on my external hard drive so.....

I go into amarok and go to setting/configure amarok/collection and check media/media(my external)/music then check off all the artist folders individually because i unchecked the option to scan folders recursively(when I didnt do that it chose every item under every subfolder) When I choose apply it scans music up to 29% then stops same happens when I choose to rescan collection it the same thing happen and there is no music in my collection.... clicking ok has no results... tried it with the check marks hilited and unhilited... 

what is causing this and how can i fix it.... 

Its been a hassle to get things working right in kubuntu (ive only been using it for a few days and see its potential but am getting close to fed up with having to figure out what is wrong with every program before i can use it)

---

### Post by whalescreams on 2009-08-30
anyone got any tips?

---

### Post by oboedad55 on 2009-08-30
> **whalescreams said:**
> anyone got any tips?

I don't have an answer for you as I use Rhythmbox, which you may want to try. Give Linux some time. It takes most people a little time to learn their way around. I think given a little time you'll enjoy the system more than what you've been using in the past.

--Jon

---

### Post by benerivo on 2009-08-30
I had the same problem once. From my memory, it was because of a single file that amarok couldn't read properly. I think it was an unusual character in the filename that was stopping it. I fixed it by a batch rename of my music directory. Sorry i can't be more specific here, but try limiting the amarok search to a single folder and see if it works.

---

### Post by whalescreams on 2009-09-01
So I think I may have solved the problem.....I had backed up all media and other files I wanted to my external and then completely restored my system with windows 7 and kubuntu.... In windows (still on my external) I had created another folder(organized music) and moved all the music I had gone through that wasnt missing tracks or anything else to it... so I had set WinMedPla to retrieve from this file as well.... when I finally went back into Windows 7 and started messing around I realized it had doubled all the files I put there.. so I started deleting some of them(but of course some of them were showing up 0 bytes) when I realized that I made sure I only deleted those..... but i would delete the file after that.. (ones that actually existed) So I used explorer and went into the file folder only to find that every single one was just empty artist/album folders.... and none of them were in the original backup folder....  skimming around I saw a new my music folder had appeared... inside that... there was a double of everything in the backup file including what was missing from the organized music file I had created... The player would still play it even though it didnt exist in the folder specified..... Windows has seriously screwed up my 180+ Gigs of music... before I switched to windows 7 doubles of stuff would be popping up all over the place... I never could get it straight.... 

Guess the newest version is no better than there other crappy operating system...

Gonna go into the folder in kubuntu and see if its all empty

Is there anything that can help me condense and organize my files through?

As soon as I get kubuntu figured out a bit more... windows is gone

is there any kind of live chat for helping with ubuntu issues?

---

