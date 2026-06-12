---
title: "program like nero for windows"
date: 2008-02-23
forum: Multimedia Production
---

### Post by park8b156 on 2008-02-23
Ok, I've  looked and looked.  All  I find is the process in 2 steps for burning avi files.  This is the only reason i still have windows so that I can use Nero in a one step point and click/ wait an hour and its converted and burned process.  If you know of a program that does this to the T then please tell me.  And if you able to make a program like this then please do cause there alot of people who are looking for this. I can't beleave that this has not been made yet. Just for clarification i do NOT want to use 2 programs to burn one avi file.  I want to do this just like i do in windows.  So no using devede and kb3 for one move.  I only ask this because of the fact that every torrent that contains a move file is avi and this is really slowin me down.  Thanks alot. Please excuse my anger but im at wits end I love Linux and I just want to make it work for me the way it should.

---

### Post by em3raldxiii on 2008-02-23
What format are you trying to convert to?  I'm not quite 100% clear on what you are asking.  It sounds kinda like you want to take a compressed video stream (like a DivX .avi file) and burn it directly to DVD format.

Of course, we are going to assume that you are talking about legally free multimedia, right? ;)

---

### Post by edm1 on 2008-02-23
If you can't find a free solution, you could always buy [nero's native linux version.]("http://www.nero.com/eng/linux3.html")

---

### Post by uberlube on 2008-02-23
Use devede :)

---

### Post by park8b156 on 2008-02-23
Yes media is legal and i want a program that will ask for the file to convert/burn like nero does and I click ok then it converts and burns with out any futher prompts from me.  I am using pure .AVI files non divx as far as i know.  If you have ever used the windows based Nero program you should have an idea of what im talking about.   


P.S. devede the kb3 is one step to much.  I want to start the procces leave for work and put it right in the dvd player when i get home. Thanks for replying though.

---

### Post by park8b156 on 2008-02-23
Oh,yeah as far as i could see neros linux native version only burns iso files so that means i am stll using 2 programs for a one program job.

---

### Post by gsmanners on 2008-02-23
As far as I can tell, there are no programs that work the way you describe, but if you are not averse to having an all-in-one-solution using a script, there may be a way to construct a bash script for the purpose.

---

### Post by park8b156 on 2008-02-23
if i can make it have a GUI as well then ok but im not that advanced do you know of any how too's on that

---

### Post by park8b156 on 2008-02-23
or if that is already made a link to the program

---

### Post by trippinnik on 2008-02-23
I think QDVDAuthor has this functionality.  Have you tried it?  it's in the repos.

---

### Post by park8b156 on 2008-02-23
yeah i will it will have to wait till tomorrow im burning in windows right now

---

### Post by em3raldxiii on 2008-02-24
Creating your own script should be relatively simple.  I am not a pro, but I think you could probably write one to convert/burn and then put it in your Nautilus scripts folder.  Then I can see you right-clicking a file, and clicking your script entry.

If you are willing to spend a little bit of time, I am sure MANY people here would be willing to contribute.  I am willing to bet, however, that such a script already exists.  I'll see what I can find :D.

EDIT:  These links may be of some assistance:  [http://www.erikburrows.com/index.php?node=DVD+Burning+Under+Linux](http://www.erikburrows.com/index.php?node=DVD+Burning+Under+Linux) and [http://g-scripts.sourceforge.net/cat-multimedia.php#video](http://g-scripts.sourceforge.net/cat-multimedia.php#video)

---

### Post by Creative2 on 2008-02-24
if you want convert and burn..i have made fuoco...unluckly for now i have used k3b to burn..so is not so automatic...
it converts into divx then start k3b with that files ..so you must click on burn button to start burning...

mm i should use another command line xD so for example in fuoco you should replace **(NOT SURE)**

mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=192 -srate 48000  -vf scale -zoom -xy 720 -xvidencopts fixed_quant=4 -o OUTPUT ENDLOOP k3b --datadvd 'OUTDIR'

With 


mencoder INPUT -ofps 25 -ovc xvid -oac mp3lame -lameopts abr:br=192 -srate 48000  -vf scale -zoom -xy 720 -xvidencopts fixed_quant=4 -o OUTPUT ENDLOOP growisofs -Z /dev/dvd -R -J  'OUTDIR'

So it should burn your dvd data when you have finished with your divx compatible avi. if you want try you find fuoco on my signature

**Note 
as you can see before encode the files into a divx compatible formats, then after it has encoded every files  it start k3b , for the first command line, instead for the second starts to record an dvd data  but i repeat i am not sure of the results so use an re-writable dvd
link to burn cd dvd form command-line 
[http://www.yolinux.com/TUTORIALS/LinuxTutorialCDBurn.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialCDBurn.html)

---

