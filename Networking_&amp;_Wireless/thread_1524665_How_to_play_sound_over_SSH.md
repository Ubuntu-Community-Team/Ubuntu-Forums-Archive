---
title: "How to play sound over SSH"
date: 2010-07-05
forum: Networking &amp; Wireless
---

### Post by carsonrose on 2010-07-05
O[SIZE=3]kay, so here is the deal..........

I have a network of about 25 computers. All of them running either Ubuntu 10.04 or 9.10. I can ssh into each machine with no problems..... 

I want to type a terminal command and have an audio file play in the speakers of the user at the remote machine. The users have soft phones..... all sound is pushed through their headsets..... If I wanted to say.... play a cat meow in their ear or maybe a dog barking.... how would I do this?

****** I cant wait, this is going to be PRICELESS!![/SIZE]

\\:D/

---

### Post by carsonrose on 2010-07-05
No takers?

:confused:

---

### Post by toolfan2k4 on 2010-07-05
[http://ubuntu-for-humans.blogspot.com/2010/03/how-to-play-mp3s-from-terminal-on.html]("http://ubuntu-for-humans.blogspot.com/2010/03/how-to-play-mp3s-from-terminal-on.html")

You would play the sounds on their PC just as you would if you were using terminal on that machine...here is a tutorial for MP3 files...

---

### Post by carsonrose on 2010-07-14
> **toolfan2k4 said:**
> [http://ubuntu-for-humans.blogspot.com/2010/03/how-to-play-mp3s-from-terminal-on.html](http://ubuntu-for-humans.blogspot.com/2010/03/how-to-play-mp3s-from-terminal-on.html)

You would play the sounds on their PC just as you would if you were using terminal on that machine...here is a tutorial for MP3 files...


Thanks for the reply. I cant wait to try this........

---

### Post by chili555 on 2010-07-14
If you want to create your own message and have it play in that eerie, robotic voice, create a text file using vim or any terminal text editor. Use text2wave to convert it to a .wav file and then, from the terminal call:```
aplay message.wav
```

---

### Post by carsonrose on 2010-07-14
> **chili555 said:**
> If you want to create your own message and have it play in that eerie, robotic voice, create a text file using vim or any terminal text editor. Use text2wave to convert it to a .wav file and then, from the terminal call:```
aplay message.wav
```


<evil smile> this is going to be great..... !

---

### Post by carsonrose on 2010-07-15
> **carsonrose said:**
> Thanks for the reply. I cant wait to try this........


This tried to play it on my machine, not the machine I am ssh into.  How do I get the file to play on the remote machine instead of mine?

---

### Post by chili555 on 2010-07-15
ssh into the remote machine. Then do, on the terminal you have open ssh'ed into the remote machine:```
vim message.txt
```Add the text of your choice, for instance:> get back to work...lazybonesSave and quit vim.

Still on the terminal you have open ssh'ed into the remote machine:```
text2wave message.txt -o message.wav
aplay message.wav
```As long as the speakers are turned up, the remote machine will hear the message.

---

### Post by Skaperen on 2010-07-15
> **chili555 said:**
> ssh into the remote machine. Then do, on the terminal you have open ssh'ed into the remote machine:```
vim message.txt
```Add the text of your choice, for instance:Save and quit vim.

Still on the terminal you have open ssh'ed into the remote machine:```
text2wave message.txt -o message.wav
aplay message.wav
```As long as the speakers are turned up, the remote machine will hear the message.

Why not just:
```
echo 'get back to work' | ssh whoever@remote 'text2wave | aplay'
```

---

### Post by carsonrose on 2010-12-10
both of those commands work BEAUTIFULLY!! Color this thread SOLVED!! :popcorn::popcorn:;):D

---

### Post by apollothethird on 2010-12-10
> **carsonrose said:**
> both of those commands work BEAUTIFULLY!! Color this thread SOLVED!! :popcorn::popcorn:;):D

By the way you can also consider using a PulseAudio server.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

