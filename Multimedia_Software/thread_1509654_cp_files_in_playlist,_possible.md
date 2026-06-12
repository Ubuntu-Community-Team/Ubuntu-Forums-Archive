---
title: "cp files in playlist, possible?"
date: 2010-06-14
forum: Multimedia Software
---

### Post by Jay Colfer on 2010-06-14
I've got a few large, unsorted folders where I dump mp3s. I manage it all through rhythmbox and I've decided to separate the wheat from the chaff by paring down stuff I don't want and throwing all the desirable stuff into a big (~1,800 file) .PLS playlist file saved to my desktop.

My question to you is, is there a hack that'll let me cp all the file entries in this playlist from their various original directories and into one target directory? Playlist format is:

> 
[playlist]
X-GNOME-Title=Biglist
NumberOfEntries=1823
File1=file:///media/blackhole/Audio/Unsorted/file1.mp3
Title1=file 1
File2=file:///media/blackhole/Audio/Music/file2.mp3
Title2=file 2

etc.


---

### Post by Jay Colfer on 2010-06-14
With a little vim and awk voodoo (which I still don't fully understand!) I've now got a list of 1823 files, i.e.

> /media/blackhole/Audio/Music/whatever.mp3Anybody know what the best way to copy this many files to a new location might be? I'd like to leave the originals where they are for now.

I was thinking the cp command, but I'm not sure how to feed it a list of paths via a text file and I'm not sure it's a great idea to issue the command 1823 times.

Any thoughts?

---

### Post by arrange on 2010-06-14
> **Jay Colfer said:**
> I've got a few large, unsorted folders where I dump mp3s. I manage it all through rhythmbox and I've decided to separate the wheat from the chaff by paring down stuff I don't want and throwing all the desirable stuff into a big (~1,800 file) .PLS playlist file saved to my desktop.

My question to you is, is there a hack that'll let me cp all the file entries in this playlist from their various original directories and into one target directory? Playlist format is:

Do you mean something like this?```
i=1; find /media/blackhole/ -type f -iname '*.mp3' | while read F; do title=`basename "$F" .mp3`; echo -e "File${i}=file://${F}\nTitle${i}=${title}" >> /tmp/playlist; ((i++)); done
```

---

### Post by Jay Colfer on 2010-06-14
> **arrange said:**
> Do you mean something like this?```
i=1; find /media/blackhole/ -type f -iname '*.mp3' | while read F; do title=`basename "$F" .mp3`; echo -e "File${i}=file://${F}\nTitle${i}=${title}" >> /tmp/playlist; ((i++)); done
```


Thanks, I've sorted things out with help from the forums and google.

I wanted to copy the files listed in a playlist (which spanned several directories) to one folder so I could more easily manage them. I probably went about this backwards, but it got done in the end.

I used vim to search and remove the more dynamic stuff from the list (like playlist position numbers) with some wildcards, then used awk to remove every other line of text from the file because it was just ID3 track names or some such, which was garbage for my purpose.

Then a poster named sisco311 gave me a huge heads up on how to feed cp a text file:

> 

Of course, if you plan to run it multiple times, then create a script:

     ```
#!/bin/bash
while read file; do
  cp -vb "$file" /home/jay/target_directory
done < /home/jay/list_of_files.txt
```Don't forget to make it executable:

```
chmod +x ./move.sh
```

---

