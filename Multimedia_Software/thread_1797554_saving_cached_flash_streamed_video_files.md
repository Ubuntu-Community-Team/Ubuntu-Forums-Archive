---
title: "saving cached flash streamed video files"
date: 2011-07-05
forum: Multimedia Software
---

### Post by the geek diddy on 2011-07-05
I have a toshiba satellite l505-gs5035 laptop with natty narwhal x64 installed along with linux kernel 2.6.39. I tried using clipgrab to save the video files but I can even get it to run an embedded url for a download location let alone identify video files in the browsers temp cache of files. 

ls -l /proc/$i/fd/* | grep ‘/tmp/Flash’ | grep -o “/proc/$i/fd/\\S*” | xargs cp -t ~/Videos/

I run the above script because it makes more sense to save it as it is being stored on the hard disk itself as opposed to manually selecting it from a list that might not be complete. But it always give me a cp error calling it a missing file operand, try cp --help for assistance. This line of code is directed towards mozilla and not chromium correct? I ran the pgrep -f libflashplayer.so twice and got different sets of values for the folder within the /proc director. What can the problem be?

---

