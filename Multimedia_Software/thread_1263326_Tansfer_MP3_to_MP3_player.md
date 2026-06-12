---
title: "Tansfer MP3 to MP3 player"
date: 2009-09-10
forum: Multimedia Software
---

### Post by SergeantBort on 2009-09-10
I have a creative zen mp3 player. 

I am somewhat new to Linux, in windows I used napster to download mp3's and transfer them onto my mp3 player. But in Ubuntu I cannot seem to find a way to transfer the mp3's I have on my hard drive onto the mp3 player.

I have tried a handful of programs, and none of them seem to transfer to my mp3 player. I have tried manually copy/paste into the music folder on my mp3 player, when i disconnect my mp3 player, it says it is updating the library, but the songs do not show up.  

I dont know what else to do, I enjoy my music, but if I cannot transfer my library from my comptuer to my mp3 player what good is a library on my Ubuntu system ?  I hope to not have to use windows to much, once I get Ubuntu working to its best ability.

Programs I have tried:
Rhythmbox
Elisa Media Center
Banshee Media Player
Audacity

I think there have been more, but I cannot remeber at this time, if there is a way to do it within one of these programs, or a setting somewhere I need to change, please let me know.  I have been searching for almost a week now, for a program or a setting to be able to transfer the files to my mp3 player, any help is greatly appreciated.

---

### Post by Chronon on 2009-09-11
The first link from Google looks promising: [http://tiagoboldt.net/blog/creative-zen-linux/](http://tiagoboldt.net/blog/creative-zen-linux/)

---

### Post by SergeantBort on 2009-09-11
I appreciate that, I must not have put the right combo of search terms into google, possibly sleep deprivation, will try that tomorrow afternoon!

---

### Post by SergeantBort on 2009-09-11
Well I updated my firmware on the MP3 player like was first suggested, and because this is a newer version of Ubuntu then that page was written on, I went to see if just doing that would work, no luck. 

So I moved onto the next step in the terminal, sudo apt-get purge libmtp6 and all its telling me is it cannot find libmtp6... so I am not sure what to do from here ?

---

### Post by SergeantBort on 2009-09-11
I tried to follow it, after discovering, that libmtp6 is not longer used, it is up to libmtp8. 

I tried following it changing that.. and its not working for me.. 

not sure, either the explanation is not complete enough and I cannot follow it, or it just does not work anymore with the updates..

---

### Post by SergeantBort on 2009-09-12
After more research, and more work, i have gotten it to work.

The creative zen just does not work 100% with ubuntu.

I have been trying a lot of things, but I 'think' all you have to do is install Gnomad2, 

sudo apt-get install gnomad2


plub in your creative zen mp3 player, with gnomad2 closed.
it will show up as a drive on your desktop, unmount it (right click)
then open gnomad2, it loaded up into gnmad2 then for me and connected right up, just selected the folder where my music was, and transfered it onto my mp3 player.  

Not the easiest thing in the world, but it does work.

There is a slight possibility of a few files i downloaded before are needed for this to work, but I am not sure, as I do not think they completely installed when I tried to use them, so try to above first, if that works, great if not, ask and I will tell you the other files I had installed prior to this.

---

