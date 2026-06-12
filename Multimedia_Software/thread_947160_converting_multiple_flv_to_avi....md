---
title: "converting multiple flv to avi..."
date: 2008-10-14
forum: Multimedia Software
---

### Post by Mia_tech on 2008-10-14
I have a folder with several flv files that I've been converting to avi using ffmpeg, to eventually put them on a dvd, but I want to be able to issue a single command that would actually convert all the files in the folder to avi, and each file in its own avi file... I thought of using something lik:

```
ffmpeg -i *.flv out.avi
```

but this will convert every flv file to a one huge avi file... could anyone tell me how could I make this process a bit more automatic

thanks

---

### Post by brandon88tube on 2008-10-22
Yeah I am looking to do similar except that I want to do flv to mp3 and keep the names exactly the same, but have a different extension. I've searched around and I have seen some scripts so that might be the way we have to go. If you find out how to do this please post it up.

Edit:
Just paste this into gedit and save as filename.sh (filename being whatever you want to call it) and place it in the same folder as the files you want to convert. Then right click the file go to properties and under permissions check the box that says make executable (there is a terminal command you can use to do this, but I don't remember off the top of my head). When this is done you can either do ./filename.sh in terminal or just double click filename.sh and choose run.

```
#!/bin/sh
for file in *.flv
do
	ffmpeg -i "$file" "${file%.flv}.avi"
done
```

---

### Post by Mia_tech on 2008-10-23
here's the one I'm using... kind of the same though
```
for if in *.flv
do
  of=`basename $if .flv`
  ffmpeg -i $if  ${of}.avi
done
```

---

