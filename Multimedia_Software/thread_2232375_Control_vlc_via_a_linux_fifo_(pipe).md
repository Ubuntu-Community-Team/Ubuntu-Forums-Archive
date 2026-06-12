---
title: "Control vlc via a linux fifo (pipe)"
date: 2014-07-01
forum: Multimedia Software
---

### Post by macey on 2014-07-01
Ok, this is not a Ubuntu query but I know that there is a lot of knowledge on this forum and people are usually very helpful here...

Hello, I am looking for a real vlc 'expert' here..
I can easily control mplayer like this:-

```
mplayer -slave -input file=/my_fifo  myfile
```


and 'pipe' commands to the fifo with shell scripts like this:-
```
echo 'pause' >my_fifo
```

This works fine with mplayer,
How do I do this with vlc please?
I have seen posts which say use  --rc-fake-tty, I have tried various set-ups but can't get it to work..
Help PLEASE, would much prefer to use vlc over mplayer...

I only want to use shell scripts to do the control so nothing fancy..

---

### Post by ajgreeny on 2014-07-01
I'm not sure I can help specifically with your query, as I don't fully understand what you are wanting to do, but for the command line version of vlc you need to use the command **cvlc**, not **vlc**.

I don't know if this will make any difference to your attempts to use it, or if you can just replace the current mplayer command with cvlc,ie, ```
cvlc -slave -input file=/my_fifo  myfile
```

---

### Post by macey on 2014-07-02
@ajgreeny er yes, I am aware of that.. No, it doesn't help.. -slave & -input are not vlc options....at least, not in the same way as they work in mplayer.

---

### Post by macey on 2014-07-02
ok, it's easy:-

vlc -I rc --rc-host localhost:1250 {file/playlist} (-d optional to daemonise)

echo pause | nc localhost 1250


open up a port (1250 in this case) between your host & clients & have full remote
control over vlc.

At last, been messing with this for months off and on...
Very happy, managed to work this out for myself.... admittedly, doesn't use fifo (pipe) but does the job even better.

---

