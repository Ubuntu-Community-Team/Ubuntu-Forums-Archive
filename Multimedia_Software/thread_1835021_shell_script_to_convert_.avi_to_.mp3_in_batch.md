---
title: "shell script to convert .avi to .mp3 in batch"
date: 2011-08-28
forum: Multimedia Software
---

### Post by qmqmqm on 2011-08-28
Hi

I have written a shell script to try to convert a bunch of avi files in a directory to mp3.

However the script stops after the first file.

I can't figure out what was wrong with the script. When I comment out the line that does the conversion, it prints the file line by line just fine.

Can anyone please advise?

Thanks in advance!

The script:
[INDENT]while read line
do
echo $line
mplayer -vo null -ao pcm:file="$line".wav "$line"
done </tmp/tmp.txt
[/INDENT]

/tmp/tmp.txt:
[INDENT]a b c.avi
d e f.avi
x y z.avi
... ...[/INDENT]

---

### Post by papibe on 2011-08-28
It just stops after the first? No errors? Is that the actual content of the list?

Regards.

---

### Post by erind on 2011-08-28
As it is, the **mplayer** reading from stdin will consume all the arguments ( $line ) at once.  Adding **< /dev/null** will redirect its reading and fix it.

```
while read line
  do
      echo $line
      mplayer -vo null -ao pcm:file="$line".wav "$line" [COLOR=Blue]< /dev/null[/COLOR]
  done < /tmp/tmp.txt
```

---

### Post by qmqmqm on 2011-09-05
> **erind said:**
> As it is, the **mplayer** reading from stdin will consume all the arguments ( $line ) at once.  Adding **< /dev/null** will redirect its reading and fix it.

```
while read line
  do
      echo $line
      mplayer -vo null -ao pcm:file="$line".wav "$line" [COLOR=Blue]< /dev/null[/COLOR]
  done < /tmp/tmp.txt
```



Thanks Erind!

$line should contain only 1 line, not the entire file, because it is inside of a while loop... I do not see how mplayer is able to read the entire file at once.

Could you (or anyone else) please explain?

Thanks in advance!

---

### Post by sisco311 on 2011-09-05
> **qmqmqm said:**
> Thanks Erind!

$line should contain only 1 line, not the entire file, because it is inside of a while loop... I do not see how mplayer is able to read the entire file at once.

Could you (or anyone else) please explain?

Thanks in advance!

By default, both the read built-in (from while read) and mplayer read from stdin (in a script running on a terminal, the Standard Input is how bash sees the characters you type on your keyboard.)

with < /tmp/tmp.txt you redirect the file to stdin, hence read will read the first line, then mplayer (it's greedier than read) will read the rest of the file.

with < /dev/null you tell to mplayer to read from /dev/null instead from stdin.

You could also tell read to read from FD6 and redirect the file to FD6:
```
while read -r -u6 line
do
    mplayer ...
done 6< /tmp/tmp.txt

```
In this case mplayer will still accept input from the keyboard, or more precisely from the Standard Input (a.k.a stdin or FD0) 

For details, check out:    [http://mywiki.wooledge.org/BashGuide/InputAndOutput](http://mywiki.wooledge.org/BashGuide/InputAndOutput)

---

### Post by qmqmqm on 2011-09-17
Thanks so much Sisco311 !

It's interesting how shell script works differently than you would think sometimes.

---

