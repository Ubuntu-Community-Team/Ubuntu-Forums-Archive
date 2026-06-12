---
title: "No Sound for Puzzle Pirates, Email, and Problems"
date: 2010-02-08
forum: Multimedia Software
---

### Post by hollyann on 2010-02-08
Hi, I'm a new Linux user and I have Ubuntu 9.10.

I play a java-based game called Yohoho Puzzle Pirates  ([www.puzzlepirates.com]("http://www.puzzlepirates.com")).  On my old computer (which had Win2k), Puzzle Pirates worked fine.  However, on my new Linux laptop...

The game itself runs fine, but there's no sound.  I've been surfing the net for the last several days to see if I could find a solution for this, but I haven't really found one yet - I've only come across situations that were similar to mine, yet still different.

There was one solution I came across, on the Puzzle Pirates wiki, where they mentioned the following:  

[I]"I thought I'd append this. On Ubuntu 9.10 neither libopenal1 nor libopenal-dev are installed by default. So you'll need to run "sudo apt-get install libopenal1 libopenal-dev" to get sound working in YPP."

[/I]So I tried that.  I heard sound on Puzzle Pirates for about 10 seconds, and then...nothing. I went to close the game and now I noticed that the game just won't close now.  I had to get my husband to show me the Linux version of Crtl-Alt-Del, because it just wouldn't close.  I started the game up again, and this time, I heard sound for about a second, and then nothing.  And then the game wouldn't close again, and I had to "kill" it in order to close it.

I'm not quite sure what to do about the situation, as I depend on the sound in the game for many things.  I'm also worried that maybe I might have done more harm by adding those two "libopenal" things, because I never had problems closing the game before I installed them.

On a related note, my Email client (Mozilla Thunderbird) also doesn't do sound.  I'm used to hearing a little chime whenever I get Email, but...there's just nothing. It's been like that ever since we got the laptop set up.   Although, this particular problem isn't as major as the one for the game, I can do without the chime, but I definitely can't do without the sound on the game.

If it helps, I have SunJava installed.  I've also posted on the Puzzle Pirates forums as well, but haven't heard back from anyone yet.

Can anyone help me please?

---

### Post by cikson on 2010-03-03
I had same problem. First I found solution in [this]("http://ubuntuforums.org/showthread.php?t=1326355&highlight=puzzle+pirates") thred and then installed libopenal1 libopenal-dev, now it works!

---

### Post by DoubleGrande on 2010-03-10
I'm not sure which one of the solutions worked for me, as I installed the two libopenal packages and the libsdl1.2debian-pulseaudio packaged mentioned in the thread cikson linked above, but after a restart I have perfect sound in pogo.com games now.

---

### Post by raffi_1970 on 2010-06-24
I had the same problem on Pogo. I installed the *libopenal1  libopenal-dev *files. it worked and now it has stopped working again. 

any ideas?

---

