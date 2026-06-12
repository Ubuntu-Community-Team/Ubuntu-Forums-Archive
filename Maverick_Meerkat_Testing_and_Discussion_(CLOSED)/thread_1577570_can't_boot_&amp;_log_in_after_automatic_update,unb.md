---
title: "can't boot &amp; log in after automatic update,unbuntu 10.10,"
date: 2010-09-19
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by reza1717s on 2010-09-19
Hi,I am a fresh Linux user,I really enjoy unbuntu performance but I have a serious problem,please forgive me if can't explain it in very technical way,I created a dual boot system ,first vista & then unbuntu 10.10,everything was fine till update center upgrade some software or upgrade unbuntu itself,then in boot time,instead of usual graphic interfaces (is that X something ?) ,i had a command line which asked for my log in name & password,but I couldn't right anything,(unresponsive keyboard),then I boot to recovery secure & I used those option but it gave me again command line,which asked for my user name & pass with the same problem,then I installed unbuntu from live cd again,it was fine till after few boot ,I have some update again which cause exact same problem again,I can't boot in normal way to log in,we live cd,I chose try option,then I check my system file & other program & its seems to me that all files are there,but I don't know how can I restore my previous setting & install,course I can install unbuntu again but it doesn't make sense because then after short time I will have the same problem again,when I was looking for a solution I realized this is a some kind of common problem after update ,& I expected with live cd most be a way to restore system but I couldn't find how,I really appreciate any guidance or suggestions but please consider as a previous windows user & newbie to Linux,I don't have any experience in working with command line of links

---

### Post by davidvandoren on 2010-09-19
most likely you installed a new kernel version and something is missing.
when your pc is booting up you'll have for 10 seconds opportunity to boot into an older kernel.
Did you try that?

---

### Post by reza1717s on 2010-09-19
> **davidvandoren said:**
> most likely you installed a new kernel version and something is missing.
when your pc is booting up you'll have for 10 seconds opportunity to boot into an older kernel.
Did you try that?
I guess maybe you are right,because my I'd I remember directly,I installed unbuntu 10.10 ,but now it is unbuntu maverick develop(er?),but how can I boot in to older version,& I'd this is the case,shall I disable automatic update option later?

---

### Post by reza1717s on 2010-09-19
P.S.,excuse me for so many  mistake in my text,I have to use my android to post, & automatic spell checking is behave sometimes very stupid :}

---

### Post by davidvandoren on 2010-09-19
when your computer boots you'll see the options listed in front of your eyes.

use the down key to a different kernel listed the first is the one you are using now.

---

### Post by Rasa1111 on 2010-09-19
i think this is the 3rd post ive read today, same issue.
Kinda glad I didnt do any of them. lol

---

### Post by reza1717s on 2010-09-19
I installed unbutu with live cd one more time,this is the third time,after 5-6 boot,i have the same problem again,after the main screen that i choose which os i want to boot,when i choose unbutu,instead of normal graphic unbuntu interface,i get a command line (unbutu maverick development branch ??)   which asking for my user name a pass,i can write my user name but when i want to write my pass,keyboard become unresponsive,then tell me that my pass is incorrect and ask me for my log in(user name) again,& same as before i am able to write it but for pass keyboard is unresponsive again!
i tried recovery option too,but it didn't help.
i log in to my system with live cd & when i check my system file,it seems to me everything is there,naturally i can install unbutu with live cd again but then i will have the same problem again.my system is a vaio vgn,with intel centrino 2 & 2.66 ghz & ati graphic card,i made two partition on my hdd,one for vista & another one for unbutu. 
any suggestion or guidance is really appreciated. 
in attachment i will put screen shots of my boot screen & files.

---

### Post by Rasa1111 on 2010-09-19
Hey, Im not sure on the rest of your problems..
But when you type in your password..
 it will act as if they keyboard is not responding, but it actually is. 
I believe it is a safety measure. 

So you just simply type in your password and hit enter. 
But none of it will actually show on screen.

> when i choose unbutu,instead of normal graphic unbuntu interface,i get a command line (unbutu maverick development branch ??

 I was getting this same screen after I borked my 10.10 install. 
But after re-installation, all is back to normal.

Sorry Im not more help.

---

### Post by CharlesA on 2010-09-19
It sounds like a problem with the X server starting.

What happens if you run startx?

*Moved to **Maverick Meerkat Testing and Discussion**.*

---

