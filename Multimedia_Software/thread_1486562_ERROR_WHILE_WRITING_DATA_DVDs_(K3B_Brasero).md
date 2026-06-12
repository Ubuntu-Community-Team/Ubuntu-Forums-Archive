---
title: "ERROR WHILE WRITING DATA DVDs (K3B/ Brasero)"
date: 2010-05-18
forum: Multimedia Software
---

### Post by linuxyogi on 2010-05-18
Hi, my problem is when I try to burn a data DVD using K3B I get an error 

message saying "Could not determine size of the resulting image file" &

in case of Brasero it says "unknown error".

I am not trying to create a multisession disc.

The data I am trying to write are some .avi * mpg files (in data cd/dvd mode).

At first I thought my writer was at fault but when I tried to burn the data using the image recorder (k3b & brasero) the result was the same.

I read somewhere that file permissions must be set correctly on the source files so that K3B can determine their sizes. Read write permissions was already applied.

So then, what is causing this ?

Please help.

---

### Post by linuxyogi on 2010-05-19
No one ????:(

---

### Post by Chrisco66 on 2010-05-19
Same problem here.  Is there another burn software that will replace Brasero?  Anyone know why Brasero suddenly stopped working?  I have been using it since 7.04, and its been perfect, now it does nothing.

---

### Post by wandalalakers on 2010-05-20
I never had problems with k3b until I installed kubuntu 10.04.  I used 8.04 before that.  I reported this bug for k3b on bugs.kd3.org and the guy who created cdrecord says it's because the original cdrecord is not include with debian, ubuntu, suse, fedora, etc.
I've tried to compile his version of cdrecord and still can't get anywhere.

[http://cdrecord.berlios.de/old/private/linux-dist.html#problems](http://cdrecord.berlios.de/old/private/linux-dist.html#problems)
[http://cdrecord.berlios.de/old/private/linux-dist.html](http://cdrecord.berlios.de/old/private/linux-dist.html)

---

### Post by dE_logics on 2010-05-20
The files of your project contains special characters which the backend programs cant handle.

apt-get install krename

and after importing all the files of your project in kerename, do a find and replace in the filename tab - 

Then 'add' and in the find box paste the following code - 

[^a-zA-Z0-9\ ]

This is if your files contain only characters between a-z (case insensitive) and spaces, if not the above expression has to be modified. If it contains '-', ',' and . - 

[^a-zA-Z0-9,\ \. \-]

Then check "find is a regular expression" in the dialog, then OK, then finish. Be warned, this will rename your files and so the consequences might be bad.

---

### Post by dE_logics on 2010-05-20
> **pcdoctor said:**
> I never had problems with k3b until I installed kubuntu 10.04.  I used 8.04 before that.  I reported this bug for k3b on bugs.kd3.org and the guy who created cdrecord says it's because the original cdrecord is not include with debian, ubuntu, suse, fedora, etc.
I've tried to compile his version of cdrecord and still can't get anywhere.

[http://cdrecord.berlios.de/old/private/linux-dist.html#problems](http://cdrecord.berlios.de/old/private/linux-dist.html#problems)
[http://cdrecord.berlios.de/old/private/linux-dist.html](http://cdrecord.berlios.de/old/private/linux-dist.html)

The k3b devs cant do anything to fix problems other than the GUI/commandline ones.

Everything depends on the backend. I'll talk to the cdrkit devs about this...now they can do something.

I've reproduced the problem and reported.

---

### Post by Chrisco66 on 2010-05-20
Any hope for Brasero?  We cant be the only people having this problem..

---

### Post by linuxyogi on 2010-05-20
> **dE_logics said:**
> The files of your project contains special characters which the backend programs cant handle.

Yes, that is the problem.

Deletion of a file from the data project resolved the problem.

The burn process started & ended without any problem.

I deleted the file from my disc out of frustration !!!

As far as I can recall, the filename was very long and included combinations of upper case & lower case characters & that it was an .avi file.

But still this problem appeared after installing 10.04 & can really disrupt work for people like me. I don't have any other OS installed other than Ubuntu.

I am waiting eagerly for the next version of Ubuntu & I hope it will be less problematic than this one.

Thanks for your help.

---

### Post by dE_logics on 2010-05-20
> **linuxyogi said:**
> Yes, that is the problem.

Deletion of a file from the data project resolved the problem.

The burn process started & ended without any problem.

I deleted the file from my disc out of frustration !!!

As far as I can recall, the filename was very long and included combinations of upper case & lower case characters & that it was an .avi file.

But still this problem appeared after installing 10.04 & can really disrupt work for people like me. I don't have any other OS installed other than Ubuntu.

I am waiting eagerly for the next version of Ubuntu & I hope it will be less problematic than this one.

Thanks for your help.

The Ubuntu guys cant do anything. If something has to happen, it has to happen now. The only shot is to remove those special chars and problem will be solved.

The problem is not cause of long chars, it's cause of 'special' chars like \n (specially).

> **Chrisco66 said:**
> Any hope for Brasero?  We cant be the only people having this problem..

Yeah, I was too having this problem.

Brasero uses cdrtools or libburn. cdrtools won't help, but try installing libburn, if it's installed brasero will use it automatically.

Another burner is xfburn...is only uses libburn backend. Install that and see.

---

### Post by Chrisco66 on 2010-05-20
Ok, tried installing libburn from synaptic (libburn4).  No help, then installed libisoburn1, still no help.  I tried to completely remove cdrtools, only to find that according to Synaptic, its not installed.  It does not even come up in the list.

Do I need to restart or log off and on between changes?  

When I have more time, I will try xfburn.

---

### Post by dE_logics on 2010-05-20
> **Chrisco66 said:**
> Ok, tried installing libburn from synaptic (libburn4).  No help, then installed libisoburn1, still no help.  I tried to completely remove cdrtools, only to find that according to Synaptic, its not installed.  It does not even come up in the list.

Do I need to restart or log off and on between changes?  

When I have more time, I will try xfburn.

Xfburn is pretty easy...it's a graphical tool.

Wait, I'm opening up Ubuntu to see ...

Ok, it appears Ubuntu is using cdrkit by default. Actually in Ubuntu they have split the packages to it's components... And ironically cdrecord is missing... so you all are using cdrkit. No use restarting/logging out.


Also it's highly recommended to use krename for this, you can remove the special characters though that easily and it's a graphical tool (if you think it's not). If you're not getting something about it, ask.

---

### Post by Chrisco66 on 2010-05-21
Ok, tried xfburn.  When I click the icon, it takes at least 30 seconds before it opens.  It keeps saying "Cannot access drive (it might be in use)".  I tried a different disk, now it says "Cant unmount media, drive can not be used for burning".

I thought maybe it was the way the disk had been written in the past (DVD-RW).  I tried to blank the disk, but the Blank button was greyed out. I tried a third disk.  Now the burn image button is not greyed out.  I click Burm Image, it does nothing for about a minute, then I get a window that says "Unable to grab the drive".  

I closed all the windows, and tried again.  Now it says "Cannot access drive (it might be in use)".  

When you right click the disk icon on the desktop, most times, the only option is eject.  I just right clicked and now it shows unmount.  When I unmount the disk, click burn, it appears to be working.  When it shows complete, it ejects the disk.  It will not play on my DVD player however.  I tried the first disk again, the option to unmount is not available.  I click burn and after about 30 seconds it says "Cant grab drive".

When I used Brasero, I did not have to manually unmount the disk.  If I have to do that now, thats fine, but how do I unmount the disk first when the only option is eject?  Not to mention the fact that when I do get it to work (or appear to work) it results in a non playable disk?

I though about doing a clean install on this machine, but there is no guarantee that it will even fix the problem.  I have problems on two other machines since the upgrade to 10.04, and reinstalling didnt fix the problems.

I am not sure which way to go next.  As always, advice is appreciated..

---

### Post by dE_logics on 2010-05-21
> When I click the icon, it takes at least 30 seconds before it opens.

:lol::lol::lol:

Yeah, I know. It actually starts HAL...I guess.

> "Cannot access drive (it might be in use)". I tried a different disk, now it says "Cant unmount media, drive can not be used for burning".

This might be cause xfburn was compiled without/with hal which is not running.

> It will not play on my DVD player however. 

What did you want to make? A video DVD? If you want to play AVI files, some DVD players (new ones) support playing though though a data DVD/CD... but yours might not. There're many possibilities.

> If I have to do that now, thats fine, but how do I unmount the disk first when the only option is eject?

```
sudo umount /dev/sr0
```

Assuming you have only one device... this will most probably be it.

You can make a shell script for it - 

#! /bin/bash
gksu umount /dev/sr0

And save it to a file name (without space) and with an sh extension e.g. name.sh

Assuming it's on the desktop open terminal and run - 
> 
cd Desktop
sudo chmod u+x name.sh

Then double click on it, then click 'run in terminal', enter the pass and it should umount.

To solve problems with xfburn try running - 

sudo hald

In terminal and then start xfburn.
> 
I though about doing a clean install on this machine, but there is no guarantee that it will even fix the problem.

That's not the way to go with linux.

---

### Post by Chrisco66 on 2010-05-21
The disk I was making was an iso created with DeVeDe.  I have made many disks this way so I know the iso was good.  I did try to burn the disk with another iso, same result.  

Its not that I don't appreciate the help, but is this what I am going to have to do every time I burn a disk?  How did Brasero get broken?  Why cant it be fixed by re-installation?  I guess my real question is what is the real cause of the problem?  Is it the new kernel?  Why did it start at least a week after the upgrade to 10.04?  Did they change the backend?

Im so disappointed in the latest release.  Now I have had problems on three computers, and two are still broken.  

There is a bug report open for this item.  I hope they come up with a fix soon.

Thanks again..

---

### Post by dE_logics on 2010-05-21
> The disk I was making was an iso created with DeVeDe.

You were trying to burn an iso but k3b gave you this problem? Now THAT'S unlikely.

I never tried a the software, but cant say it's fool proof.

> Its not that I don't appreciate the help, but is this what I am going to have to do every time I burn a disk?

:lol: With xfburn, I guess you have to. But I guess that's easy, I mean, I'm attaching a script right now, just double click on it, and then, 'run in terminal'. This is the umount. Did the 'sudo hald' resolve issues with xfce? If so I'll include that too with the script.

You can try another technique. After installing cdrskin Run the following command - 

sudo mv /usr/bin/wodim /usr/bin/wodim.bak.cdrskin
sudo ln -s /usr/bin/cdrskin /usr/bin/wodim

Then try running k3b. It might also have impact on Brasero. And yes, you have to do this once.

Also you might try Sabayon. This might not fix your problem but you might like it - 

[http://sabayonlinux.org/mirrors](http://sabayonlinux.org/mirrors)

---

### Post by taecha on 2010-05-23
I have been having this problem for ages. It happened with almost every Ubuntu version since Hardy. I don't think that it has anything to do with unsupported characters since for me it does not work even if I have 'clean' file namesw. 

What I have observed is that after every kernel update DVD burning stops working creating an error during burning.

I would be more than happy if this problem could finally be solved or anyone had a solution because, quite honestly, I am getting tired of some bugs in Ubuntu which keep appearing with every release ... and I have been using Ubuntu ever since it first appeared.

---

### Post by Chrisco66 on 2010-05-23
dE_logics, no, I didnt try k3b.  The problems I reported were in Xfburn and Brasero.  I have uninstalled both for now.  

I tried k3b in the past, and that may be my next step.  I always admired the simplicity of CD/DVD creator and Brasero.  Click burn and your done.  That is the way it should be.  K3b always seemed more complicated than it needed to be.  I really dont like having to navigate through a maze of questions, selecting project names, that sort of thing (reminded me of Roxio in windows).  I know it's a more advanced, full featured application, so it will be more complex.  I just dont use many of the features that it offers.  Does K3b use the same backend as Brasero?  If so, should I even expect it to work?

I really appreciate the time you have put into this so far.  I will try the other suggestions you made when I have more time. I dont like to rush through things like this, because I might make the problem worse.  

I did try Sabayon on my "test dummy" machine.  It seemed ok, but with different hardware, there is no way to know if it will fix this problem, or maybe cause others?  I even considered going back to opensuse, but it comes with its own problems (playing certain video files require codecs that dont always work). 

Thanks again, Ill keep this updated..

---

### Post by dE_logics on 2010-05-24
K3B the most feature rich and usable burner around. KDE as a whole is a target towards the most usability, as a result it's harder.

Speaking of Roxio, we have Nero Linux too. You might like to give the trial a try, I think it's in the repos.

> Does K3b use the same backend as Brasero? 


Yeah, sorta. One of the backends is common. It officially does not use libburn which brasero can and xfburn does. But you can make it work with cdrskin (again libburn based, and IMO the best of all) through the fix as posted above - 

```
sudo mv /usr/bin/wodim /usr/bin/wodim.bak.cdrskin
sudo ln -s /usr/bin/cdrskin /usr/bin/wodim
```

> seemed ok, but with different hardware, there is no way to know if it will fix this problem, or maybe cause others?

Yeah, we have a few hardware issues with it, for e.g. on mine, the audio was not working, but on another PC, it fixed a problem. Although the graphical package manager is not as good as Synaptic (although the command like one is better than apt)

The dependency resolution is better, so is the package nomenclature as a result you get more with less no. of packages installed, furthermore, I think it's faster  (I got a feeling the Ububut devs compile with -Os instead of O2 so the installation is very small)... and all the proprietary drives, codecs etc... are also working out of box. The down side -- it takes too much space.

---

### Post by Chrisco66 on 2010-05-25
Latest update.  I tried K3b.  It looked like it was working, then it just sat there.  The elapsed time was running.  It kept saying preparing to burn, but didnt do anything after ten minutes.  

Out of desperation, I reinstalled Brasero.  Rt. clicked on the .iso, selected open with Brasero.  It asked if I wanted to blank the disk.  I clicked yes and it burned it.  Yes, it seems to be fixed.  I removed k3b, and tried again.  Still works.  I restarted, Brasero still works. 

I dont know why it just started working.  Maybe there was a missing file that was common to both Brasero and K3b that somehow was removed?  Installing K3b reinstalled that file?  I dont know. Im just glad it is working again.  

It still ejects, then pulls the tray back in, then tells me to eject manually.  That is an annoyance I can live with though.

Thanks again for all the help.  If anyone wants more details about what I did, just ask.

---

### Post by dE_logics on 2010-05-25
k3b should have installed a few backends which Brasero preferred.

Anyway, glad the problem got solved.

---

### Post by Chrisco66 on 2010-05-26
dE, thanks again for the help.  Any ideas on the eject thing?  Thats actually a separate post.  

Its annoying, not something that takes away from the functionality of the machine though.

---

### Post by dE_logics on 2010-05-27
I think your problems will be back if you apt-get autoremove. And not running that command is unhealty. The problem got solved cause of the now vacant dependencies that k3b pulled.

As of the eject problem...it might be cause of permission. Try running Brasero as root (run gksu brasero in terminal), if it ejects it's a permission problem.

Actually I get the same problems when burning in Ubuntu and never bothered to solve it.

---

### Post by Chrisco66 on 2010-05-27
Ok, now I feel stupid.  apt-get autoremove?  When was I supposed to run that?  

The forums are a humbling experience.

---

### Post by dE_logics on 2010-05-27
If you run that the problems might be back...

The reason why it got fixed was cause it installed a few new packages.

---

### Post by sdrey on 2010-10-04
BURNING AN AUDIO CD WITH UBUNTU 9.10
---------------------------------------
Ok, so for those of you who are pulling your hair out, you aren't alone.
I have been attempting to burn an audio CD from a collection of MP3's, and
here is the result so far.


Brasereo
--------
   program hangs, or crashes at various points....forget this SW.

Serpentine
----------
   seemlingly works fine...says it burns the CD even...but try the CD in any
CD player...doesn't work.

K3d
---
   BUG 1: First, will not recognize DVD as writable...
      Solution, use a 780M CD.
   BUG 2: crashes on write, bad permissions.
      Solution: run k3dsetup, and enable permissions (apparently too stupid to do this by itself).
   BUG 3: write fails, says to try lower write speed.
   BUG 4: tried lower write speed, still errors out.

   Give up on this SW....
   PS. I wasted 4 CD's during this process...apparently it will write just enough to ruin the CD...just won't finish.


BTW, I used to be able to write audio CD's just fine with Ubuntu until after several updates...clearly 
there are issues with these new releases...Hey guys, perhaps you should forget about new graphics, and 
concentrate on making SW actually work reliably...

How am I ever going to get off Windows when Ubuntu seems to be regressing....very disappointed in Ubuntu.

Solution:  Use any windows SW if you want to burn a simple Audio CD.

---

### Post by stmiller on 2010-10-17
Brasero works for me if you uncheck the box 'write directly to disk'. Both for audio and data.

---

### Post by AbdRahim on 2011-12-17
I am having the same problem with k3b -even with files that are successfully burned with Brasero

Could not determine size of image file. There is a permission problem somewhere because id works from a terminal with gksudo.

---

### Post by AbdRahim on 2011-12-17
Debugging info said that /home/xxx/.kde/share/apps/k3b/temp was an invalid node. I manually created that folder as root. Now all seems to work well. Hope this helps someone.

---

### Post by 2Pjotre on 2012-09-21
**I did not study all messages of this thread.**

 From the beginning of this thread I received some months ago the key information how to resolve some problems with unusual characters in file name. I want to pay my debt for this help, showing here a relatively general solution for some such error types (includes some inspiration from those other posts in this thread). 
[B]
How to find all files with the most typical characters with problem risks?[/B]
   
 I prefer basic system tools instead of add-on utilities. Here is a solution which can be extended to typical risks for your language (in this case: for German language)

    find /a*/ -type f -regextype posix-egrep -regex "/a./.[ä-äö-öü-üß-ß\ \,\;\?].*" -print

This would look up all files in the file trees starting with a directory name: /a... You would see all files listed which include a space character, or one of; ä ö u ß , ; ?
[B]
Then often bulk rename is required.[/B]

This could be done this way: 

Rename files/bulk = (inside CURREN(!)directory) (-n =simulat.without rename)

=== rename -v -n 's/^xb-/uxb-/' xb* ; ls -l ./ ;

Above: For start of file names. Is to adapt to the task, e.g. below for an inner character group of a file name, and now not similuation -n but really doing the rename:

=== rename -v 's/have/had/'  *have-money-*  ; ls -l ./ ;
[B]
All this could surely be improved.[/B]

But for normal needs it should do the job. [B]

I did not yet succeed to implement how trailing line feeds can be detected[/B]

(when part of the file name).
This fault might occur when saving files with the editor KATE. I had only a small case number of this error. So the debug message of K3b was sufficient to detect these files, 1 by 1 with repeating burn attempts. 

Perhaps somebody with better knowledge for this will add here how to detect in the way like above also trailing line feeds in file names? (Hence just by extending the regular expression in the command "find ...".)     

Or as far as I remember, I finally later succeeded with something like: 

ls -l ./*/filename-xxx.txt?

---

### Post by acefromspace on 2012-09-21
dE_logics, Thanks for mentioning krename... I have many issues with filenames and special characters.
linuxyogi, yes, this can be a pain in the butt, but if a simple program can fix it, we will both be happy... no need to give up on ubuntu.
By the way, I think this can be done easily in terminal, using BASH shell commands, just haven't learned enough to do it yet. Anyone have a simple way to do this?

---

### Post by acefromspace on 2012-09-21
Woops! Only read first page of thread... carry on.

---

### Post by overdrank on 2012-09-21
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

