---
title: "Emesene not working in 8.04"
date: 2010-05-04
forum: Multimedia Software
---

### Post by Jetro on 2010-05-04
When trying to run emesene, this message appears: 
"Error during login, please retry 
(Protocol not supported by server)"

I am running Ubuntu 8.04 Hardy Heron.

I searched for this particular error message, as well as errors regarding "emesene" in general, but it seems no-one is having problems with ut (or, perhaps no-one is using it).

I have tried the following:
[LIST][*]Installing emesene from Synaptic Package Manager
[*]Installing emesene from [this website](http://packages.ubuntu.com/hardy/emesene) (as well as from the 'Lucid' page)
[*]Installing it via terminal (sudo apt-get install emesene)
[/LIST]

The error occurs both when using a hotmail adress, as well as a non-hotmail adress.

Maybe I'm an idiot, because this programme is in fact not meant to work in Ubuntu 8.04? In that case, I wish someone told me, because I couldn't figure it out. :(

---

### Post by eotakos on 2010-05-05
Hi! I was using 8.04 for 2 years, and I upgraded to 10.04 just 2 days ago... :-) 

what I did, was use the "source" version of emesene from the original site. So, go to [http://www.emesene.org/](http://www.emesene.org/), hit download, scroll to the bottom of the page and download the source tar ball.

double click on it (the archive manager takes over), and copy the contained folder at your desktop. (actually at this point you are done - you can just go into that folder, double click on the file "emesene", choose "run in terminal", and it will do the trick. if you want something more elegant, keep reading)

open a console, navigate at your desktop, and then
```
sudo mv emesene-1.6.1 /opt
```

then from your menus go to system -> preferences -> main menu
click on the internet (from the menu on the left), and then "+new item" on your right

at the window that comes up, leave the type to "application",  at the name field put in "emesene", at the command field, put in "/opt/emesene-1.6.1/emesene" and you are done!. (you can also add an icon by clicking on the icon on the left, navigating to the folder /opt/emesene... and choose the emesene icon you'll find there.

navigate from the menus to your new emesene. that's all

I hope this does it for you... If you have any issues regarding this process post again (although I'll be "out of town" i'll try to answer as soon as possible). 

bye

---

### Post by Jetro on 2010-05-11
I was unable to copypaste the folder from the archive manager the regular way, so I just drag'n'dropped, but it seemed to work.

I get this message when I try to do the terminal stuff, however:
~$ sudo mv emesene-1.6.1 /opt
mv: cannot stat `emesene-1.6.1': No such file or directory

Even though that is the name of the folder on my desktop...

And OH MY GOD! I have no idea how, but it worked, just by running the file in terminal! ^__^ Thanks a lot! :D

---

### Post by eotakos on 2010-05-11
a couple of things (useful information for future reference -that is if you're interested):

when you open up a terminal, the directory it puts you in directly is your home directory, and not the Desktop directory (that's why I previously I mentioned navigate to your desktop). So, after you open up the console, you type 
```
cd Desktop
```
and then, the prompt before the cursor blinking, will be like
```
***@***:~/Desktop$ 
```
and now you are ready to do the "mv" command.

and a trick you can use to make sure that you typed correctly a name of a file and/or directory, is not to type the whole thing! instead, you start typing the beginning of the name, and hit "tab" and let the computer do the rest of the job. If there are more than one files/directories that start with the text that you typed,... you can hit "tab' a couple of times more, and all the possibilities available will be displayed for you.


so I guess now you can try again to complete to procedure if you want to...

I'm happy that you made it work anyhow!


p.s.: even though I upgraded to 10.04, the version of emesene at the repositories somehow generates an error for me too. So i guess I'll install the source tar I was using before in 8.04 - the one you are using now.

---

### Post by Jetro on 2010-05-12
Thanks once again! :) It worked, needless to say. 
I'm a total Linux newbie, but of course you knew that already.

---

### Post by eotakos on 2010-05-14
> **Jetro said:**
> Thanks once again! :) It worked, needless to say. 
I'm a total Linux newbie, but of course you knew that already.

Everybody using ubuntu has been in your position! don't hesitate to ask for any kind of issue regarding your new os... there is a good chance that you get an answer :) . It has been two years since I have switched to ubuntu, and there are still a whole lot to learn!

when seeking answers, besides the forum (where I always start looking at the "tutorials and tips" section), you can always check out the community support web page - [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)


(once again) I'm glad that I helped :)

---

