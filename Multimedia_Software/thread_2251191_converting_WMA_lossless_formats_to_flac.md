---
title: "converting WMA lossless formats to flac"
date: 2014-11-02
forum: Multimedia Software
---

### Post by andrew_s4 on 2014-11-02
in trying to get wma files recognized by Clementine, I have learned that Clementine can not play WMA lossless files. Which is a lot of my music library. Converting these files into flac seems to be the way forward, but as a newbie to Ubuntu and command line tools especially I'm at a loss as to how to begin. 
All my music files all sit on an external harddrive, and are organized into folders related to the Artist/Album. Help with this would be appreciated!

---

### Post by mc4man on 2014-11-03
Let's try a simple test to see - 
can you write to the external drive & is a ffmpeg conversion to flac suitable to your needs. (assumes you installed ffmpeg..

So - 
browse to your external drive  & pick a folder that has wma lossless files **directly inside that folder**.
right click on that folder > Open in Terminal

Once the terminal opens copy & paste this command into terminal, press enter. It should complete without comment/error in the terminal, **leave terminal open.**
```
mkdir flacs
```

If no issue having that folder created then c&p this command into the still open terminal, press enter & we'll see
```
for f in *.wma; do ffmpeg -i  "$f"  ./flacs/"${f%.wma}.flac"; done
```

Hopefully it converts the wma's to flac & places them inside the 'flacs' folder. If not then post complete terminal output. 
If the .flac's created aren't suitable then post why, ect.

---

### Post by andrew_s4 on 2014-11-03
Man, it worked! I'm not sure exactly what happened, but it happened!! The code used is way over my understanding, but it gives me a start point, thank you very much for your time and effort. I'm impressed.

---

