---
title: "Creative Sb Live 5.1 Problem In Dapper Drake"
date: 2006-09-07
forum: Multimedia &amp; Video
---

### Post by raman_tx on 2006-09-07
Hi Guys!
I love UBUNTU for so many reasons...easy 2 use/no hassels i found so far
but 1 thing is nightmare for me....so far
[COLOR="DarkRed"]SOUND..SOUND...SOUND..I CANT HEAR ON REAR /Front Speakers..(I can hear either one of them)[/COLOR]
I am using Ubuntu Dapperdrake 6.06
Sound cards..
1).SB LIVE 5.1 24BIT 
SOUND SYSTEM ....CREATIVE INSPIRE(5.1)
2).ON BOARD WHICH IS NOT 5.1

But I am a music lover so I tried many ways but nothing helped me
I was using fedora before which worked fine with sounds..I am waiting for anybody's response/suggestion otherwise I would install fedora5(I hate to leave UBUNTU but i love 2 play music while workin)
I would appreciate your help
thanks

---

### Post by linuksamiko on 2006-09-07
I had a problem like this too. My computer seamed to play music but I couldn't here anything. Then I figured out that the sound was played through my onboard soundcard. After I deactivated the Onboard-Soundcard in the BIOS, music was played through my "real" SB Live soundcard.
There is a way to set a special soundcard as the default soundcard so that you still have 2 card but since I never use my onboardsound this wasn't necessary for me.

---

### Post by assan on 2006-10-22
> **raman_tx said:**
> Hi Guys!
I love UBUNTU for so many reasons...easy 2 use/no hassels i found so far
but 1 thing is nightmare for me....so far
[COLOR="DarkRed"]SOUND..SOUND...SOUND..I CANT HEAR ON REAR /Front Speakers..(I can hear either one of them)[/COLOR]
I am using Ubuntu Dapperdrake 6.06
Sound cards..
1).SB LIVE 5.1 24BIT 
SOUND SYSTEM ....CREATIVE INSPIRE(5.1)
2).ON BOARD WHICH IS NOT 5.1

But I am a music lover so I tried many ways but nothing helped me
I was using fedora before which worked fine with sounds..I am waiting for anybody's response/suggestion otherwise I would install fedora5(I hate to leave UBUNTU but i love 2 play music while workin)
I would appreciate your help
thanks

Hi, I found solution for problems with SBLive! by searching ubuntu forum.
In console terminal run alsamixer
 write
$ alsamixer

There will be tool with some graphic. You have to navigate right through many options. There will be option swiching on rear and central speakers (I thnik by arrows up & down). 
Thats it. It works fine on my desktop.

---

