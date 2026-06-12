---
title: "Terminal won't remember last command"
date: 2011-03-28
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Sealbhach on 2011-03-28
I'm using to pressing "up arrow" to bring up the last entered command. It works as long as I keep the terminal open, but if I close it and open up a new terminal it won't remember.

Anyone else got this? I don't see any bug reports.

.

---

### Post by Atermoon on 2011-03-28
Weird. I just tried it and if I type "exit" in the terminal and press enter so it closes next time I open one it remembers everything, but if I press the X button it doesn't.
I'm not sure how it was before, I always close my terminals with "exit" - it's just the way I'm used to.

Cool avatar btw ;)

---

### Post by VinDSL on 2011-03-28
My experience has been...

Sometimes it remembers the commands -- sometimes it doesn't -- no matter what I do.

As irritating as this is, it forces me to exercise my memory, so it might be a good thing...  :D

---

### Post by rburkartjo on 2011-03-28
yes i have had the same problem for awhile. i either scroll over use the history command  and then !1888 for example to run

---

### Post by cecilpierce on 2011-03-28
Seems like Ctrl-D to exit instead of the X keeps things in memory.

---

### Post by Enigmapond on 2011-03-28
> **Sealbhach said:**
> I'm using to pressing "up arrow" to bring up the last entered command. It works as long as I keep the terminal open, but if I close it and open up a new terminal it won't remember.

Anyone else got this? I don't see any bug reports.

.

I've actually never had that problem but as rburkartjo stated, just type in "history" and that will bring up the last 500 commands typed in. Just enter "!" and the number of the command you are looking for.

Cheers!

---

### Post by cecilpierce on 2011-03-28
> **Enigmapond said:**
> I've actually never had that problem but as rburkartjo stated, just type in "history" and that will bring up the last 500 commands typed in. Just enter "!" and the number of the command you are looking for.

Cheers!

Thanks, I didn't know about that, mine went up to 775 !

---

### Post by cariboo on 2011-03-28
I always use Ctrl-d, it's just habit, and use the up-arrow to scroll through the commands I've entered previously.

---

### Post by mc4man on 2011-03-28
It's not a really a bug, the new bash will only allow writing to ~/.bash_history  when the terminal is exited (Ctrl+d or exit command

This was an upstream change in bash
( I have an old bug on this which I will not link, nothing more to be said there, actually would like it to be marked 'will not fix', which I can't do
(unless ubuntu was going to change the code which there is no indication that they will

---

### Post by PaulW2U on 2011-03-28
> **cariboo907 said:**
> I always use Ctrl-d, it's just habit, and use the up-arrow to scroll through the commands I've entered previously.
Ctrl-D is good, it eliminates the "exit" entries when scrolling though the command history.

---

### Post by ranch hand on 2011-03-28
> **PaulW2U said:**
> Ctrl-D is good, it eliminates the "exit" entries when scrolling though the command history.
Sure does.  Used to have a bunch of them.  This is much better.

---

### Post by Sealbhach on 2011-03-28
> **Enigmapond said:**
> I've actually never had that problem but as rburkartjo stated, just type in "history" and that will bring up the last 500 commands typed in. Just enter "!" and the number of the command you are looking for.

Cheers!

Thanks. I've learned that Ctrl+R is also a good way to find commands from history.

[QUOTE=mc4man]
It's not a really a bug, the new bash will only allow writing to  ~/.bash_history  when the terminal is exited (Ctrl+d or exit command
[/QUOTE]

OK, so it's been deliberately changed. I find it a little irritating to have to change my habits. Now I will exit the terminal with Ctrl+D.

.

---

### Post by VinDSL on 2011-04-01
Looks like the terminal is remembering the last command now.

I've been closing the terminal using the 'X' (close) button, in the titlebar, and it's been working fine (as of beta 1).

---

### Post by nm_geo on 2011-04-01
All methods work here for me, but I have a persistent sudo time out so I guess that might have a bearing as well.

---

### Post by mc4man on 2011-04-01
bash released a patch (008 ) the other day that returned history write when using the close button
Was included in last bash update

---

### Post by rburkartjo on 2011-04-01
seal tks for the info on ctrl-r much faster than entering history then scrolling and using !   to open a previous used command

---

