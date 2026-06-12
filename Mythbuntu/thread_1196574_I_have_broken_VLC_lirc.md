---
title: "I have broken VLC lirc"
date: 2009-06-25
forum: Mythbuntu
---

### Post by Chewiesw on 2009-06-25
Hello

I have just upgraded to 9.04 and while I was on a role, I decided to "experiment" with my VLC (my default player)lirc controls and now I have broken it completely. 

If I add the VLC config file to lircrc file the remote does not work at all and I get these messages

" not a valid number for repeat
" in /home/andrew/.mythtv/lircrc:331 ignore
" in /home/andrew/.mythtv/lircrc:332 ignore
" in /home/andrew/.mythtv/lircrc:334 ignore
" in /home/andrew/.mythtv/lircrc:340 ignore
" in /home/andrew/.mythtv/lircrc:341 ignore

mythtv. bad file format /home/andrew/.mythtv/lircrc:343
date: failed to read lirc config /home/andrew/.mythtv/lircrc for myth

However if I take the lirc config out the remote works for everything except for VLC.

I presume the numbers refer to line numbers, however when I go to these lines it does not correspond to the REPEAT= key

I would like to get my remote working again for everything

---

### Post by kadafi69 on 2009-06-25
i broke my vlc lirc too, except I reconfigured the lirc file but didnt back up the original file. oops!

---

### Post by Chewiesw on 2009-06-25
With alot of digging and scracthing I came across this

[http://ubuntuforums.org/archive/index.php/t-508017.html](http://ubuntuforums.org/archive/index.php/t-508017.html)

The problem is the line endings of all the lines, they were all DOS format. To fix it, I opened the file in nano and then made a commented-out line (didn't matter, just changing the file). I pressed Ctrl-X to exit, and when it prompted me to save, I pressed Y. At the prompt asking for the filename to save as, it said:

File Name to Write [DOS Format]: .lircrc

Hope this helps..

---

