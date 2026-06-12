---
title: "Sopcast"
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by itsmeagain on 2007-05-07
Hi 
I have just install sopcast version 0.2.8. I start the program and it opens up ok, but how do I get to view live programs?.  In Windows I have no problems, I just open sopcast select the channel I wish to view and it just works, what do I have to do to get it to work in Ubunto?

---

### Post by vcader04 on 2007-05-07
Hi 

I'm  also experiencing the same problem,  not got a clue how to  get it to view live streaming.

---

### Post by ntlam on 2007-08-25
have you installed Mplayer or xine?

---

### Post by jfreemanlc on 2007-08-25
I installed sopcast but it doesn't work with Mplayer.  Then again, that doesnt surprise me.

I have Kaffeine, but how do you switch sopcast from mplayer to kaffeine?

Also, how does one get xine?  Typing "apt-get xine" in the terminal does nothing for me.

I've read a number of threads here on this subject and none of them have been helpful for me.  There really should be a one-stop place to go that shows incompetent people like me how to get this going.

---

### Post by jfreemanlc on 2007-08-25
Alright, I actually got it to work.

Since I'm not bright enough to get xine via the terminal, I got it through the depositories or whatever they're called.

As per another thread here about sopcasts, I learned that to switch from mplayer to xine, one has to go to config and then replace mplayer by placing the folliowing on the player line:

xterm -e xine 

First channel I tried didn't work, but I'm now watching some show about boxing on chinese cctv.  Rock on.

---

### Post by ntlam on 2007-08-26
> **jfreemanlc said:**
> I installed sopcast but it doesn't work with Mplayer.  Then again, that doesnt surprise me.

I have Kaffeine, but how do you switch sopcast from mplayer to kaffeine?

Also, how does one get xine?  Typing "apt-get xine" in the terminal does nothing for me.

I've read a number of threads here on this subject and none of them have been helpful for me.  There really should be a one-stop place to go that shows incompetent people like me how to get this going.

correct command should be:
apt-get install xine

---

### Post by iheartubuntu on 2007-09-14
> **jfreemanlc said:**
> Alright, I actually got it to work.

Since I'm not bright enough to get xine via the terminal, I got it through the depositories or whatever they're called.

As per another thread here about sopcasts, I learned that to switch from mplayer to xine, one has to go to config and then replace mplayer by placing the folliowing on the player line:

xterm -e xine 

First channel I tried didn't work, but I'm now watching some show about boxing on chinese cctv.  Rock on.

i inputed "xterm -e xine" and still i get nothing.

anyone have any other tips to get sopcast running? thanks!

---

