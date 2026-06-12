---
title: "Internet Radio won't stream"
date: 2008-02-29
forum: Multimedia &amp; Video
---

### Post by skydiver|goose on 2008-02-29
I can't get my favorite radio station's stream to work on Ubuntu. The link to the stream player is: [http://project961.com/cc-common/ondemand/player.html?world=st](http://project961.com/cc-common/ondemand/player.html?world=st)

I used to have the link to the actual source of the stream, but I don't know where I put it and I can't find it in the page source.

---

### Post by Whiffle on 2008-02-29
That one is tough.  I have it working under konqueror with kaffeine on my other install, but I havn't played with it on this install (Fresh install of zenwalk).

But, I found this script a while ago and modified it a bit ;)  Just save it, do "chmod +x" on it, and then do

./clearchannel.sh project961

and it should play.  It uses mplayer which should already be installed.  You could even make a launcher for it if you wanted.

---

### Post by skydiver|goose on 2008-02-29
how could I make a launcher for it?

---

### Post by skydiver|goose on 2008-02-29
it's not working.. here's the terminal output:

goose@goose-laptop:~$ chmod +x
chmod: missing operand after `+x'
Try `chmod --help' for more information.
goose@goose-laptop:~$ sudo chmod +x
[sudo] password for goose:
chmod: missing operand after `+x'
Try `chmod --help' for more information.
goose@goose-laptop:~$

---

### Post by Whiffle on 2008-02-29
you have to do:

chmod +x /path/to/clearchannel.sh

with /path/to being whereever you saved it.


[http://monkeyblog.org/ubuntu/installing.html#launcher](http://monkeyblog.org/ubuntu/installing.html#launcher)

And then in the command box put

/path/to/clearchannel.sh project961


You might check the run in terminal box so it runs in a terminal.  Or, if you open up the script and where it says "mplayer", replace that with "gmplayer" and it will bring it up with a GUI.

---

### Post by skydiver|goose on 2008-02-29
goose@goose-laptop:~$ chmod +x clearchannel.sh
goose@goose-laptop:~$ clearchannel.sh project961
bash: clearchannel.sh: command not found
goose@goose-laptop:~$

I tried changing it to gmplayer too, same result. I'm in the right directory...

---

### Post by Whiffle on 2008-02-29
You need the 

./


in front of it :)

So it would look like:
goose@goose-laptop:~$ ./clearchannel.sh project961

---

### Post by skydiver|goose on 2008-02-29
thanks! I'm a linux n00b, in case you didn't pick up on that :D

---

### Post by wolfen69 on 2008-02-29
every station works for me. it's not complicated. here's how i did it. go to synaptic and search for totem. remove every instance of it. then search for mozilla-mplayer. install it. while your at it, get vlc to replace totem.(vlc is better anyway) should work.

---

### Post by xzero1 on 2008-03-03
I don't like totem much either but for my self-made x264 recordings only totem plays correctly! I get no sound with vlc or gxine and offset sound with mplayer! You might want to keep it around, just in case.

---

