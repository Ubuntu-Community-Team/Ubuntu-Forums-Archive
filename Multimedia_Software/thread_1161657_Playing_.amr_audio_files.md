---
title: "Playing .amr audio files"
date: 2009-05-16
forum: Multimedia Software
---

### Post by sajithkozhikode on 2009-05-16
[B][COLOR=Red]How can we play .amr audio files in Ubuntu.  [/COLOR]
[COLOR=DarkOrchid]Which player will play it?  [/COLOR]
[COLOR=Blue]Which codec requires for playing it...?  [/COLOR]
[COLOR=DarkOliveGreen]Command line to install that codec...?   
[/COLOR][/B]

[COLOR=SlateGray]***Please help me...***[/COLOR]

---

### Post by zero777zero on 2009-05-17
i suggest trying to run this prog through wine to convert it to a wav [http://www.miksoft.net/mobileAMRconverter.htm](http://www.miksoft.net/mobileAMRconverter.htm)

---

### Post by mhh91 on 2009-05-17
i was just about to ask the same question

zero777zero: isn't there any other way to do it?

---

### Post by sajithkozhikode on 2009-05-17
[SIZE=5][COLOR=Red][B]I have got a solution from another forum...
[/B][/COLOR][/SIZE]
[SIZE=4][COLOR=Blue]Link is here:[/COLOR][/SIZE]

[SIZE=3][http://www.penguin.cz/~utx/amr]("http://www.penguin.cz/%7Eutx/amr")[/SIZE]

---

### Post by mhh91 on 2009-05-17
> **sajithkozhikode said:**
> [SIZE=5][COLOR=Red][B]I have got a solution from another forum...
[/B][/COLOR][/SIZE]
[SIZE=4][COLOR=Blue]Link is here:[/COLOR][/SIZE]

[SIZE=3][http://www.penguin.cz/~utx/amr]("http://www.penguin.cz/%7Eutx/amr")[/SIZE]

i've reached this page,and i'll try installing those two over there:)

---

### Post by binbash on 2009-05-17
I play them on mplayer.But you have to compile and enable amr support yourself.

---

### Post by mhh91 on 2009-05-17
> **binbash said:**
> I play them on mplayer.But you have to compile and enable amr support yourself.

i compiled them,but i don't know how to enable them,sadly :(


i installed RealPlayer ,and it played the media hassle-free :)

---

### Post by andrew.46 on 2009-05-17
Hi sajithkozhikode,

> **sajithkozhikode said:**
> How can we play .amr audio files in Ubuntu.  Which player will play it? 

Perhaps the easiest way to play these files is to use the MPlayer that is held by the Medibuntu repository, this has been compiled against libamrwb and libamrnb which are the required libraries. Details for adding the Medibuntu repository can be [seen here]("https://help.ubuntu.com/community/Medibuntu").

All the best,

Andrew

---

