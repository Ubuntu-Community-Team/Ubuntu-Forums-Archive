---
title: "Evolution lost the memo feature ?"
date: 2010-09-29
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ecr959 on 2010-09-29
Hello.  I know I am going to sound like a scared newbie, might be because I am a scared newbie,  but what the hell happened to the MEMOs in Evolution ?  I have alot of memos, I really mean alot of memos, and until yesterday I had 10.04 on my netbook and everything was fine.  Yesterday I decided to upgrade to 10.10 BETA and I just noticed today that I have Evolution Mail, Calendar, but no MEMOS.  I don't see a memo link or icon or "new memo" under "File".    Did Gnome decide to drop this feature ?  

Is it a plugin or optional thing now ?  I have a backup from a few days ago, on Ubuntu One,  but that was from the older Evolution, from 10.04.

Obviously something has changed in Evolution for Maverick, can someone fill me in ?  :(

---

### Post by 23dornot23d on 2010-09-29
Have you checked the Home folder .......

Look for .......

hidden files

.evolution/memos

[IMG]http://img192.imageshack.us/img192/2278/memosl.jpg[/IMG]


You have upgraded to the development version and its still in testing .... for another 11 days.

Are all your files still there ,,,, ? 

( Might be worth backing up the folders before you do anything else ..... Need to know how they are saved ... locally or on another sever ? )

* I just installed it to test what is created ....... so someone else may know more about how the memos are saved.

---

### Post by QwUo173Hy on 2010-09-30
I just ran Evolution now to check and I see a 'Memos' button.

---

### Post by ecr959 on 2010-09-30
Jarlath,  if you see a memos button, then I need your help in understanding why I don't.  When I go to applications, I see Evolution Calendar,  and Evolution Mail,  but I don't see Evolution,  like in 10.04.  In 10.04 , I would click on Evolution and the program would have icons in it for MAIL , CALENDAR, CONTACTS, MEMOS , TASKS.  Now, I only have mail or contacts or calendar, if I click either Evolution Mail or Evolution Calendar.  I have Ubuntu Netbook Edition, is that possibly the difference ?  I went to Synaptic Package Manager and reinstalled Evolution, I did this earlier today, but it still is missing the Meemos section.  Any ideas ?

---

### Post by 23dornot23d on 2010-09-30
Here is what I see if it helps .....  [LINK]("http://img839.imageshack.us/img839/2571/nam3.jpg")

I loaded it clean from synaptic yesterday ...

> 
( Might be worth backing up the folders before you do anything else  ..... Need to know how they are saved ... locally or on another sever ? )
did you look to see if the hidden files existed and back them up before you re-installed it ?

That's why I posted the picture of the files and where they were so that you could see if they were there already .....

( I do not know enough about where evolution stores the memos ..... but I would expect them to be in the .evolution folder ..... )

If you do not see the Memo Tab .... at the bottom in yellow .... then it sounds like it did not fully load up ...... 
or maybe there is a problem between the old and the new .... with configuration files.

But it would have helped to have looked in the evolution directory first ...... and made a backup ..... before re-installing ......

But who knows ..... maybe the files are still there or on a server ...... needs someone on here that used evolution and the
memos a lot to answer it properly ......... or one of the developers .......

---

### Post by Framli on 2010-09-30
The default behavior of the netbook edition is launching Evolution with the "evolution --express" command : it's launches a netbook interface of Evolution. 

You can try to launch Evolution by typing "evolution" or "evolution -c memos" in a terminal.

---

### Post by QwUo173Hy on 2010-10-01
> **Framli said:**
> The default behavior of the netbook edition is launching Evolution with the "evolution --express" command : it's launches a netbook interface of Evolution. 

You can try to launch Evolution by typing "evolution" or "evolution -c memos" in a terminal.
Bingo, that sounds like his problem. And solution.

---

### Post by ecr959 on 2010-10-01
I want to thank Framil and Jarlath,  it looks like that was the problem.  Evolution was started as "express"  and  I just tried starting it at the CL with EVOLUTION, and now I see a memos tab where it used to be, and (I'm so happy)  I see ALL of my memos.  Thank you , guys,  I learned something new today.:)  :)  :popcorn:

---

### Post by ecr959 on 2010-10-01
Let me also thank 23dornot23d for his help, too.  I appreciate the helpful tip.  Thats why these forums are such a great way to make friends and learn from each other.  
Thanks again
:):):)

---

### Post by 23dornot23d on 2010-10-01
Your very welcome ... 
I am glad the others new the fix to get you sorted out ...... cheers ..... :):)

---

### Post by QwUo173Hy on 2010-10-01
Yes, glad you got it sorted! :)

---

