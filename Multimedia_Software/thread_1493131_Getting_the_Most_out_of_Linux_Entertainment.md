---
title: "Getting the Most out of Linux: Entertainment"
date: 2010-05-25
forum: Multimedia Software
---

### Post by Gelegenheit on 2010-05-25
I am almost totally green to Ubuntu. Since I got a virus I couldn't repair, I pretty much handed myself a burned cd with the Ubuntu image on it and said "Figure it out". That was about 5 days ago. Unfortunately, where do I begin? I have the adding new programs almost down, and I'm sort of plodding my way through the whole multimedia plugins deal but there are still a lot of questions I have to ask.
 
First and foremost, how have you made the most out of Ubuntu? What kinds of programs do you use for entertainment? What, specifically, do they do? Do they have a steep learning curve? Did you do any tweaking that you think has made your experience better?
 
Some general questions that are on my mind while I type this are:
 
-iPods. How are you getting the functionality of iTunes without iTunes? How do you sync your iPod? I'm currently using Floola but I'm wondering if there is a program out there that is better.
 
-Multimedia plugins. How do I get functionality out of a Windows Media Player streaming player?
 
-TV. Any of you use any programs that allow you to watch TV from your computer without any special equipment? If I want to watch a live news feed, where would I go?
 
-Games. I have a copy of Halo for the PC. Would I be able to play it? If yes, how?
 
I greatly appreciate your patience in advance for my stupid questions and lack of understanding (How do you do that stuff, with the thing? Can I do other stuff with the thing?).

---

### Post by WinterRain on 2010-05-25
> **Gelegenheit said:**
> 
 
-iPods. How are you getting the functionality of iTunes without iTunes? How do you sync your iPod? I'm currently using Floola but I'm wondering if there is a program out there that is better.
I don't use an ipod, so..... but I hear Rhythmbox has ipod support.
 
> **Gelegenheit said:**
> -Multimedia plugins. How do I get functionality out of a Windows Media Player streaming player?
If you do in terminal:
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
this will give you the medibuntu repositories for even more software choices.
then:
```
sudo apt-get install non-free-codecs gecko-mediaplayer
```
 you will then have just about every codec under the sun. And before someone chimes in with "install ubuntu restricted extras", non-free-codecs includes restricted extras plus even more.
> **Gelegenheit said:**
> -TV. Any of you use any programs that allow you to watch TV from your computer without any special equipment? If I want to watch a live news feed, where would I go?
A lot of websites have streaming feeds. Channelsurfing.net has some broadcast stations and sports.
 
> **Gelegenheit said:**
> -Games. I have a copy of Halo for the PC. Would I be able to play it? If yes, how?
I have windows on a separate drive for gaming, so I don't know if halo would work in ubuntu via wine. I'm sure others will fill in the missing pieces.
 
> **Gelegenheit said:**
> I greatly appreciate your patience in advance for my stupid questions and lack of understanding (How do you do that stuff, with the thing? Can I do other stuff with the thing?).
No such thing as a stupid question. The only stupid questions are the ones that aren't asked. Remember, we were all newbies at one time.

---

### Post by Gelegenheit on 2010-05-26
Thanks a ton for the response.  I downloaded the plugins.  While I didn't get functionality out of what I had in mind,  (I suppose it is on the other side and I have a work-around for it anyway), I am happy that I am now able to open almost anything I want to.

I haven't quite gotten Rhythmbox quite figured out yet but that is something that shouldn't be too much of a problem.  

Thanks for making my first encounter with the Ubuntu community a great one.  I look forward to my time using the OS.

---

