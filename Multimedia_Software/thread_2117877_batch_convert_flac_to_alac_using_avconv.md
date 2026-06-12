---
title: "batch convert flac to alac using avconv"
date: 2013-02-19
forum: Multimedia Software
---

### Post by Guitar John on 2013-02-19
I've read about this in several around the web.  The command everyone seems to recommend is:
```
for f in *.flac; do avconv -i "$f" -c:a alac "${f%.flac}.m4a"; done
```

When I hit enter, it kicks back: 
*.flac: No such file or directory

I know that avconv works, because I've tried it with a single file using:
```
avconv -i audio.flac -acodec alac audio.m4a
```

The thing I seem to be missing is how to point the batch command to the folder where my FLAC files are located, which is:
 /media/250GB/Lossless

What am I overlooking?

---

### Post by evilsoup on 2013-02-19
```

cd /media/250GB/Lossless
for f in *.flac; do avconv -i "$f" -c:a alac "${f%.flac}.m4a"; done

## or

for f in /media/250GB/Lossless/*.flac; do avconv -i "$f" -c:a alac "${f%.flac}.m4a"; done

```

---

### Post by Guitar John on 2013-02-19
Hmmm, still kicking back No such file or directory.

There are multiple subdirectories in the main file, each with a name like:
/media/250GB/Lossless/Artist/Album

But I would think that the wildcard (*.flac) would take care of that.

---

### Post by evilsoup on 2013-02-20
Nah, for loops don't work recursively. For that, you'll need to use find.

```

cd /media/250GB/Lossless
find . -type f -name "*.flac" -exec bash -c 'avconv -i "$0" -c:a alac "${0/%flac/m4a}"' '{}' \;

## or

find /media/250GB/Lossless -type f -name "*.flac" -exec bash -c 'avconv -i "$0" -c:a alac "${0/%flac/m4a}"' '{}' \;

```Make sure you get all the quotes right.

---

### Post by Guitar John on 2013-02-20
\\:D/

Thank you, thank you.  I will mark this SOLVED.

---

### Post by billmc2 on 2013-03-09
> **evilsoup said:**
> Nah, for loops don't work recursively. For that, you'll need to use find.

```

cd /media/250GB/Lossless
find . -type f -name "*.flac" -exec bash -c 'avconv -i "$0" -c:a alac "${0/%flac/m4a}"' '{}' \;

## or

find /media/250GB/Lossless -type f -name "*.flac" -exec bash -c 'avconv -i "$0" -c:a alac "${0/%flac/m4a}"' '{}' \;

```Make sure you get all the quotes right.

evilsoup, would I be asking to much for you to explain all the little pieces in the instruction?  I've always had a problem grasping bash scripting (not enough experience I guess).  I've recently picked up an iPad, thus my reason for the conversion, but I'd like to keep things seperated.  As you've written the instruction, it writes the output file in the same directory as the input file.  My directory structure looks like ~/music/flac/artist/album ~/music/mp3/artist/album.  What I'd like to have is ~/music/m4a/artist/album.  Umfortunately, for me, I'm not sure what to change in your command to get the result I'm looking for.

Here is the way I'm reading (understanding) your command:

find is looking for a file ending with .flac  It begins its search at the level of the directory specified ( either . or /media/250GB/Lossless)

The result of the find command is being assigned to the variable $0 then executes bash

bash starts and runs the command (-c) contained in the string, defined by single quotes,  'avconv -i "$0" -c:a alac "${0/%flac/m4a}"' , so avconv starts up.

the input file for avconv is $0
-c:a indicates this will be an audio conversion and the output will be apple lossless (alac)
the output filename is "${0/%flac/m4a}".  

Between the parenthasis 0 is the path from the original file, but I don't know what %flac does.  I know it has to be a variable of some type, but I don't understand where the varable comes from, nor exactly what it designates.  Could you explain this pleae?  I'm thinking it is this variable that I would need to change to accomplish the directory structure I'd like to have. m4a designates the filename extension to use.  Where does the . (dot) come from in the filename?  I'm guessing the use of slashes are breaking up the various parts of the variable name  and somehow (I don't understand the difference between the first slash and the last slash) indicate a . needs to be placed here.

I also don't understand the meaning of '{}' , I'm thinking this part of the find command.
I think, but I am unsure that \; ends the find command; if I'm wrong could you tell me what it means?

Thanks,
Bill

---

### Post by evilsoup on 2013-03-10
${0/%flac/m4a} is using bash's string substitution; in this case, it's telling bash "take the variable $0, but replace the last instance of 'flac' with 'm4a'". The '%' in front of 'flac' tells it to only replace the *last* instance of flac in the string, otherwise it would replace *all* instances of 'flac' with 'm4a'.

'{}' is a part of the find command. Find will run the command specified by '-exec' once for each file found (each '*.flac' in the specified directory, or subdirectories, in this case), and '{}' specifies the current file found by find. I hope that makes sense. '{}' becomes "$0" in the bash commandline, because it's the first positional parameter - bash sees the whole avconv string ('avconv -i "$0" -c:a alac "${0/%flac/m4a}"') as a single argument, since it is contained within the ' ' single-quotes.

\; tells find's exec where to stop, yes; find will execute everything between '-exec' and '\;', once per file found by the pattern.

---

### Post by billmc2 on 2013-03-10
> **evilsoup said:**
> ${0/%flac/m4a} is using bash's string substitution; in this case, it's telling bash "take the variable $0, but replace the last instance of 'flac' with 'm4a'". The '%' in front of 'flac' tells it to only replace the *last* instance of flac in the string, otherwise it would replace *all* instances of 'flac' with 'm4a'.

OK, that makes sense to me, whether I remember in the future, I guess, will depend on how much I use it.

> **evilsoup said:**
> '{}' is a part of the find command. Find will run the command specified by '-exec' once for each file found (each '*.flac' in the specified directory, or subdirectories, in this case), and '{}' specifies the current file found by find. I hope that makes sense. .

This too, makes sense to me.

> **evilsoup said:**
> '{}' becomes "$0" in the bash commandline, because it's the first positional parameter - bash sees the whole avconv string ('avconv -i "$0" -c:a alac "${0/%flac/m4a}"') as a single argument, since it is contained within the ' ' single-quotes..

This part here is twisting my head a bit, at least for what I want to do.  I'm OK with everything from '{}' being assigned to $0; but it seems to indicate to me I'd need another variable someplace, to change the directory tree to what I want.
Starting from the full path listing, using the directory structure I described:

$0=~/music/flac/artist/album/song.flac
'avconv -i "$0" -c:a alac "${0/%flac/m4a}"'
changes $0 to =~/music/flac/artist/album/song.m4a

Question: can I expand your variable to create another directory tree?
'avconv -i "$0" -c:a alac "${0/%flac/m4a/%flac/m4a}"'

Better yet, after rereading what you said about the % sign.  If it weren't there it would replace all instances of flac with m4a, maybe I change to this:
'avconv -i "$0" -c:a alac "${0/flac/m4a}"'
My $0 would have two instances of flac in it, the directory and the filename extension.  So based upon how I understood your answer, this should replace both flac occurances, creating another directory, yes?

> **evilsoup said:**
> \; tells find's exec where to stop, yes;
find will execute everything between '-exec' and '\;', once per file found by the
pattern.

find is sorta like a loop, it'll keep going until it finds no more; correct?

Bill

---

### Post by billmc2 on 2013-03-10
Well, neither of my ideas worked at creating new directories.  The resultant output stated "No such file or directory".

The good news is that :
"${0/%flac/m4a/%flac/m4a}" = "${0/flac/m4a}"

They both produce the same output:
~/music/m4a/artist/album/song.m4a

At this point for me, its a learning experience in how to use the shell.  I could use the command provided to create the m4a files and move them maunally; but being a basically lazy guy, I'd rather have the machine do it; I just need to learn how to coax the machine into doing it.

---

