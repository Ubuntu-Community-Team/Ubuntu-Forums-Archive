---
title: "Bash Script to sort low bitrate from high bitrate mp3"
date: 2008-03-24
forum: Multimedia &amp; Video
---

### Post by damoek on 2008-03-24
I have a ton of mp3's that I ripped in the early days of the players, I thought 128k was good... Pshh, anyway I want to write a bash script that will scan my /media/sda2/music directory and sort everything in to two top level folders [128 or less] and [better than 128] or something similar. preserving all other folder structure. However, the problem i'm having right now is that I don't know any command that will list the bitrate of an mp3 file in bash. Can anyone point me in the correct direction here?

---

### Post by bashologist on 2008-03-24
Something like this? Just install mp3info first.
```
mp3info -r m -p %r file.mp3
```

I don't know if this'll work, it's rough and put together quickly.
```
music_location='/example'
under_location='/tmp/128 or less'
over_location='/tmp/better than 128'

mkdir "$under_location" "$over_location"

find "$music_location" -type f -name '*.mp3' -print0 | while read -d $'\0' file; do
        if [ "$(mp3info -r m -p %r "$file")" -lt 129 ]; then
                cp --parents "$file" "$under_location"
        else
                cp --parents "$file" "$over_location"
        fi
done
```

---

### Post by damoek on 2008-03-24
You are awesome! I'm going to play around with this today. Thank you so much!

---

### Post by damoek on 2008-03-24
```
#!/bin/bash
music="/media/sda2/Music"
good="/media/sda2/Music/better128"
bad="/media/sda2/Music/worse128"

mkdir "$good" "$bad"

find "$music" -type f -name '*.mp3' -print0 | while read -d $'\0' file; do
	if [ "$(mp3info -r m -p %r  "$file")" -ls 129 ]; then
		cp --parents "$file" "$bad"
	else
		cp --parents "$file" "$good"
	fi
done

```
```
daniel@daniel-desktop:~$ sh goodbad.sh 
read: 14: Illegal option -d

```

Ok... I ran into a bit of a snag. I'm not exactly sure what the pipe to while read -d $'/0'  file; do 
 is supposed to do, but its apparently causing problems. Any ideas?

---

### Post by bashologist on 2008-03-28
I've never seen this before. Google tells me it's a problem only when running from a script, so if you replace the tabs with regular spaces then copy and paste your code into a terminal it should work. Maybe try changing "read" to "builtin read" in the script. I noticed you changed "-lt" to "-ls", why is that?

---

### Post by ghostdog74 on 2008-03-28
you might as well use find's -exec option to execute mp3info.  

```

find . -name "*mp3" -exec mp3info -p "%r:%f\n" "{}" \; | while IFS=":" read -r bitrate filename
do     
   if [ "$bitrate" -le 128 ] ; then    
       # do your stuff  
   elif [ "$bitrate" -gt 128 ] ;then    
       # do your stuff 
   else 
       # do something else
   fi
done 

```
i leave the rest to you

---

### Post by damoek on 2008-04-01
Thanks Bashologist... Running the code in the command line totally worked! I spent a couple hours over at tldp.org looking at the scripting guide over there, but was never able to fully grasp where the syntax was going wrong. There were a couple of unintended outcomes that make me want to learn more about this, such as the cp --parents option used the full path instead of just the path it was in, not a hard post script fix but a good question for me to work on. Also when i tried the script that ghostdog74 supplied, i kept running into stat errors. although dangerous i'd also like this to clean up the target directories (not leave the first copy). It would be nice if Mv had a --parents like switch. Either way, thanks a whole bunch to both of you for the help on this.

---

