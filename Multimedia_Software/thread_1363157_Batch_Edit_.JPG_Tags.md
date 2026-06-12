---
title: "Batch Edit .JPG Tags?"
date: 2009-12-24
forum: Multimedia Software
---

### Post by Topher88 on 2009-12-24
Alright, this is going to sound like the n00biest thing ever, but it's driving me crazy...

I want to upload some pictures I took to a hosting site, however the hosting site only recognizes the images if they have a lowercase .jpg tag, and my camera saves them with an uppercase .JPG tag...  I looked on the camera, and couldn't seem to find any way to change it there, so...  Is there a way to batch edit just the tags of the pictures to change them using the terminal?  Sure, I could manually do it, but there are a lot of pictures...  Help, please??

Thanks

---

### Post by prshah on 2009-12-24
> **Topher88 said:**
> only recognizes the images if they have a lowercase .jpg tag, and my camera saves them with an uppercase .JPG tag

Is there a way to batch edit just the tags of the pictures to change them using the terminal?

OK this is not exactly what you want, but maybe it will do till something better comes along? [implied bump]

```
Thu Dec 24 @15:21:10:~/temp$ touch file1.JPG file2.JPG
Thu Dec 24 @15:21:19:~/temp$ ls
file1.JPG  file2.JPG  temp1  test
Thu Dec 24 @15:21:21:~/temp$ [color=blue]find . -name "*.JPG" -execdir mv {} {}.jpg \;[/color]
Thu Dec 24 @15:21:26:~/temp$ ls
file1.JPG.jpg  file2.JPG.jpg  temp1  test
Thu Dec 24 @15:21:28:~/temp$ 
```

It justs adds on a lowercase ".jpg" to every uppercase ".JPG" file.

---

### Post by sanderd17 on 2009-12-24
This script will change all .JPG's to .jpg
```
 
#!/bin/bash
for i in $( ls *.JPG); do
	j=$( basename $i .JPG)'.jpg'
	mv $i $j
	echo 'moved '$i' to '$j
done

```
Save this in the file JPGtojpg in the folder with the JPG files, make it executable with
```

chmod +x JPGtojpg

```
and execute the script.

---

### Post by vanadium on 2009-12-24
It can be a bit easier than that

rename -n 's/\.JPG/\.jpg/' *.JPG

will rename all .JPG. I added the "-n" option: this just shows how the files would be renamed. Use this to check wether the result is what you want. To actually rename the files, remove the "-n" in the command.

Some background on the string 's/.../.../'
"s" means "search/replace", first "..." is what to search, second "..." is "replace with". After the last slash, options can be added such as "g" for "global replace". By default, only the first occurrence will be found and replaced. With "g", all occurences will be replaced.

---

### Post by sanderd17 on 2009-12-24
@vanadium
If I use your command, it shows the text 
```

...
file55.JPG renamed as file55.jpg                  
file56.JPG renamed as file56.jpg                  
file57.JPG renamed as file57.jpg                  
file58.JPG renamed as file58.jpg                  
file59.JPG renamed as file59.jpg                  
file5.JPG renamed as file5.jpg                    
file60.JPG renamed as file60.jpg  
... 

```
But if I ls my directory it says
```

...
file100.JPG         file179.JPG  file256.JPG  file333.JPG  file410.JPG  file489.JPG
file101.JPG         file17.JPG   file257.JPG  file334.JPG  file411.JPG  file48.JPG 
...

```
So my files aren't renamed.
I don't know why your (much shorter) command isn't working.

---

### Post by prshah on 2009-12-24
> **vanadium said:**
> 
rename -n 's/\.JPG/\.jpg/' *.JPG
**To actually rename the files, remove the "-n" in the command.**

> **sanderd17 said:**
> 
I don't know why your (much shorter) command isn't working.

Note the emphasis. Remove the "-n". The command works fine. :D

---

### Post by sanderd17 on 2009-12-24
OK, I should learn to read :P

---

### Post by emoguitarist06 on 2010-01-24
> **sanderd17 said:**
> This script will change all .JPG's to .jpg
```
 
#!/bin/bash
for i in $( ls *.JPG); do
	j=$( basename $i .JPG)'.jpg'
	mv $i $j
	echo 'moved '$i' to '$j
done

```
Save this in the file JPGtojpg in the folder with the JPG files, make it executable with
```

chmod +x JPGtojpg

```
and execute the script.

Thank You So Much! I've been having the same problem and I love this bash script. I just placed the file into my Pictures folders and once I'm down transferring all of my pics from my camera to my comp I just double click the script and they're all ready to upload!!

BTW is it an UBUNTU "bug" that copies files from my camera as JPG instead of jpg? is there is way to change that?

---

