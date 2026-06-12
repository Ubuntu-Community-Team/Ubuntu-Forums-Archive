---
title: "Webcam doesn't work in skype or kopete since intrepid upgrade"
date: 2008-11-15
forum: Multimedia Software
---

### Post by Zaff on 2008-11-15
Hi all,
I have an old Creative webcam, the driver was installed using EasyCam2 and it worked fine. that is until I upgraded to intrepid.
Now if I launch cheese it works perfectly. But when I try to set it in kopete I get nothing and in skype I get weird static.
Could this be linked to the fact that kopete now runs on QT4 ? Has anyone encountered this problem ?
Any help would be greatly appreciated.

---

### Post by Zaff on 2008-11-18
This seems to be the same problem. I definitely have the same lsof output.

[http://mail.kde.org/pipermail/kopete-bugs/2008-October/002181.html](http://mail.kde.org/pipermail/kopete-bugs/2008-October/002181.html)
Any news on this ?

---

### Post by pschalkx on 2008-11-19
My Creative NX Pro webcam doesn't work either in Intrepid, I get weird static from the webcam.

I saw some threads in the forums and on the web about downloading the  spca5xx driver from:
[http://mxhaard.free.fr](http://mxhaard.free.fr)

However, I could not even compile the driver.

Anybody knows more?

Help is appreciated!

---

### Post by Ghilteras on 2008-12-15
same problem here, kopete can see my webcam if i go in the configuration tab, but if i try to invite someone to see my cam nothing happens, i cannot even see my mirror window

---

### Post by Zaff on 2008-12-16
I found a fix regarding skype here (page is in french so I'll translate):
[http://blogs.media-tips.com/bernard.opic/2008/12/11/reparer-la-video-de-skype-sous-ubuntu-810-intrepid-ibex/](http://blogs.media-tips.com/bernard.opic/2008/12/11/reparer-la-video-de-skype-sous-ubuntu-810-intrepid-ibex/)
Basically the libvl4 needs to be preloaded when launching skype so the solution is :
   1. create a file named /usr/local/bin/skype, using (sudo gedit for instance)
   2. copy the following lines in the file :
      #!/bin/sh
      LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype
   3. give the file execution permissions : 
sudo chmod a+x /usr/local/bin/skype

Still trying to figure out the problem with Kopete.

---

### Post by diskotek on 2008-12-20
thank you zaff, it absolutely worked for "skype" really nice... but i think there is a total problem: since i can not make my webcam work in "amsn".

---

### Post by Craig73 on 2009-01-01
Any updates on Kopete?  (Just installed it, same issue - it see's it in configuration but nothing - no preview, no errors, etc., - when trying to connect)

---

### Post by microlaser on 2009-02-10
> **Craig73 said:**
> Any updates on Kopete?  (Just installed it, same issue - it see's it in configuration but nothing - no preview, no errors, etc., - when trying to connect)

Try LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so kopete

Make sure you have the v4l libraries

It worked for me

---

### Post by n3had on 2009-02-27
> **microlaser said:**
> Try LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so kopete

Make sure you have the v4l libraries

It worked for me

```
1. create a file named /usr/local/bin/kopete, using (sudo gedit for instance)
2. copy the following lines in the file :
#!/bin/sh
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/kopete
3. give the file execution permissions :
sudo chmod a+x /usr/local/bin/kopete
```

Works like CHARM :)

nehad

---

### Post by rastro123 on 2009-04-23
hi, I just tried your solution for skype, and now it doesnt connect to the server, any ideas?. Im using a library for wireless connection, can I be behind a firewall for the cam? How do I undo what I just did, as before it connected ok the the skype server? thanks in advance.

---

### Post by Zaff on 2009-04-23
> **rastro123 said:**
> hi, I just tried your solution for skype, and now it doesnt connect to the server, any ideas?. Im using a library for wireless connection, can I be behind a firewall for the cam? How do I undo what I just did, as before it connected ok the the skype server? thanks in advance.
Just rename the /usr/local/bin/skype file into something else and it *should* behave like it did before, if that's where the problem comes from. (or just delete it if you're not going to use it anymore).

---

### Post by Zaff on 2009-04-23
> **n3had said:**
> ```
1. create a file named /usr/local/bin/kopete, using (sudo gedit for instance)
2. copy the following lines in the file :
#!/bin/sh
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/kopete
3. give the file execution permissions :
sudo chmod a+x /usr/local/bin/kopete
```

Works like CHARM :)

nehad

I can't believe I didn't try that before giving up...
It was so simple...
Now my webcam works on everything :)

---

### Post by PeterDW on 2009-04-24
Thank-You guys,
Your solution worked first time. Much appreciated.
Peter W.

---

### Post by tonyps on 2009-04-27
Thanks so very much!! It seems to work very well now!!

---

### Post by gshinkre on 2009-04-27
Thank you Zaff! Your solution worked perfectly well for me...That makes Jaunty complete for all I need it to do...well...almost!

---

### Post by endersgame09 on 2009-06-13
hi guys seems this is the fix ive been looking for. i can get my logitech webcam to work in cheese but not in skype. The id for the camera is - 046d:08af Logitech, Inc. QuickCam Easy/Cool. My question is could someone help a newb out and explain how to do the fix? This is my first day on Ubuntu - so i can make the text file ok - but where does it go? is that listing the actual saved file name or the directory it goes in? how do i asign that permision? once thats done is that it or do i run it once or something :( sorry for the basic questions ! any help is very apreaciated!

---

### Post by Zaff on 2009-06-13
```

1. create a file named /usr/local/bin/kopete, using (sudo gedit for instance)
2. copy the following lines in the file :
#!/bin/sh
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/kopete
3. give the file execution permissions :
sudo chmod a+x /usr/local/bin/kopete

```

> so i can make the text file ok - but where does it go? is that listing the actual saved file name or the directory it goes in? 
When you create a file named /usr/local/bin/kopete, it's actually a file named kopete in the /usr/local/bin directory. This can be confusing if you're new and I apologize for that.

> how do i asign that permision? once thats done is that it or do i run it once or something  sorry for the basic questions ! 
All you need to do is what is written, just open a terminal in Application -> Accessories -> Terminal and type the line of code in 3).
this basically does the following: 
**sudo** asks for your administration password as this is an action that requires root access
**chmod** is the command that changes permissions,** a+x** tells it to apply the X (execution) permission to All categories of users.

Hope this answers your questions, you should probably read the ubuntu and linux documentation for more information. Man pages are good too, just type :
```
man chmod
```
in a terminal to get the manual page of chmod. There is a man page for all basic linux commands.

Hope I answered your questions and you get your webcam working.

---

### Post by endersgame09 on 2009-06-13
> **Zaff said:**
> ```

1. create a file named /usr/local/bin/kopete, using (sudo gedit for instance)
2. copy the following lines in the file :
#!/bin/sh
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/kopete
3. give the file execution permissions :
sudo chmod a+x /usr/local/bin/kopete

```
When you create a file named /usr/local/bin/kopete, it's actually a file named kopete in the /usr/local/bin directory. This can be confusing if you're new and I apologize for that.


All you need to do is what is written, just open a terminal in Application -> Accessories -> Terminal and type the line of code in 3).
this basically does the following: 
**sudo** asks for your administration password as this is an action that requires root access
**chmod** is the command that changes permissions,** a+x** tells it to apply the X (execution) permission to All categories of users.

Hope this answers your questions, you should probably read the ubuntu and linux documentation for more information. Man pages are good too, just type :
```
man chmod
```in a terminal to get the manual page of chmod. There is a man page for all basic linux commands.

Hope I answered your questions and you get your webcam working.thnks allot for your help! i got the file done but i now get crazy colours and static in the skype webcam - then skype crashes! oh well ill have to keep researching. thanks again

---

### Post by califman831 on 2009-06-15
I created the kopete file as directed but was still getting a message saying something about not finding a jasper program.  I used adept to install the jasper runtime libraries.

[http://forum.soft32.com/linux/Jasper-image-converter-ftopict362856.html](http://forum.soft32.com/linux/Jasper-image-converter-ftopict362856.html)

---

### Post by peDey on 2009-06-28
> **Zaff said:**
> I found a fix regarding skype here (page is in french so I'll translate):
[http://blogs.media-tips.com/bernard.opic/2008/12/11/reparer-la-video-de-skype-sous-ubuntu-810-intrepid-ibex/](http://blogs.media-tips.com/bernard.opic/2008/12/11/reparer-la-video-de-skype-sous-ubuntu-810-intrepid-ibex/)
Basically the libvl4 needs to be preloaded when launching skype so the solution is :
   1. create a file named /usr/local/bin/skype, using (sudo gedit for instance)
   2. copy the following lines in the file :
      #!/bin/sh
      LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype
   3. give the file execution permissions : 
sudo chmod a+x /usr/local/bin/skype

Still trying to figure out the problem with Kopete.
This worked immediately for me (Jaunty + Skype 2.0).  Thanks so much!

---

### Post by dbvaio on 2009-07-02
> **n3had said:**
> ```
1. create a file named /usr/local/bin/kopete, using (sudo gedit for instance)
2. copy the following lines in the file :
#!/bin/sh
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/kopete
3. give the file execution permissions :
sudo chmod a+x /usr/local/bin/kopete
```

Works like CHARM :)

nehad


I can't believe this actually worked so easily! Thank you for such a simple solution, I've been trying to get this working for a long time. Extreme kudos to you!

Dustin

---

### Post by MohanaRao on 2009-10-17
Thank you very much this script is worked fine for me. Now my cam working for both skype and kopete Before i used to get a black image. I hope on next newer version of kopete script is embedded in software itself.

---

### Post by davezol on 2009-10-18
Zaffs solution worked a treat.
Thanks a lot.

Now all I need to do is get the mic sound sorted out.... anyone got any ideas ?  All I have is a hissing sound through my speakers when testing the mic in Preferences>Sound.

P.S. Sound capture is through ALSA and I'm running 9.04 on an Intel Pentium4.

---

### Post by tora201 on 2010-03-17
I get the following error.... 

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

Can anybody help? Cheers!

---

### Post by tora201 on 2010-03-17
Don't worry, I solved it.... plenty of other threads on this. Sorry!! It just needed to have lib32, instead of lib, since I am using 64 bit version.... I think!

---

### Post by petrasflorin on 2010-10-14
OMG THIS WORKED SO EASY! 
I can now use my WebCam on Skype !!!
Why the hell don't they integrate this into Skype or into Ubuntu itself so people won't have this problem anymore ?

I love Linux but I hate it for making easy common things being so hard. As a webcam on Skype or a DVD/ROM actually working.

---

### Post by ibrahim52 on 2011-05-01
I just want my webcam to work on yahoo which is not, tried every possible solution posted here but nothing worked i am running ubuntu 11.4

---

### Post by Lukhaz on 2011-11-15
If your camera still doesn't work after preloading **v4l1compact** it might be because yuor device use different format and you can try loading library **v4l2convert**. So the full path would be:
 
```
LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so /usr/bin/skype
```

There is also more convenient way to make this modification. Instead of making own script file use existing one ;) (provided in skype package)

[LIST=1]
[*]Edit file */usr/share/applications/skype.desktop* as super user e.g. ```
sudo nano /usr/share/applications/skype.desktop
```
[*]In file *skype.desktop* find line ```
Exec=skype
```
[*]Change value of Exec field to command above e.g. ```
Exec=LD_PRELOAD=/usr/lib32/libv4l/v4l1compact.so /usr/bin/skype
``` or if this doesn't work with your webcam ```
Exec=LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so /usr/bin/skype
```
[/LIST]

---

