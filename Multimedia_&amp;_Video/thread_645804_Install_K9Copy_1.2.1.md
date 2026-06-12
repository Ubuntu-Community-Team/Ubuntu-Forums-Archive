---
title: "Install K9Copy 1.2.1"
date: 2007-12-20
forum: Multimedia &amp; Video
---

### Post by CHFFriday on 2007-12-20
I would like to install K9Copy 1.2.1. I have downloaded the source file but I can not get to install. I have installed autocong and automake then run some other commands in terminal but I get so far and then it stops. 

Has anyone install K9Copy 1.2.1? If you have can you please help?

I use Gusty.

CHFFriday

---

### Post by mc4man on 2007-12-20
Assuming you downloaded the .tar.gz  to your desktop extract it there, then 2 com.
doug@doug-desktop:~$_ cd Desktop; cd k9copy-1.2.1_ 
doug@doug-desktop:~/Desktop/k9copy-1.2.1$ _./configure_
obviously then make ,ect. or use checkinstall
make sure you have all the depends to compile

---

### Post by CHFFriday on 2007-12-20
mc4man,
Thanks for the get back. This is how far I got. Same as last time.
The last line there is an error.

CHFFriday

chance@IMB600x:~/Desktop/k9copy-1.2.1$ sudo ./configure
[sudo] password for chance:
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables

---

### Post by mc4man on 2007-12-20
Your probably missing some packages - same spot in my configure
```
 checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
```
you could try the depends i posted earier with additions
[http://ubuntuforums.org/showthread.php?t=607991&page=2](http://ubuntuforums.org/showthread.php?t=607991&page=2)
Be advised that they are from when I had edgy and will uninstall some packages (vamps, dvdauthor, ect.). With those in place the build went fine - I did run 
```
sudo apt-get build-dep k9copy
```
for my latest compile and there were several packages I didn't have so I installed them - the compile worked without any problems - go figure

edit: you shouldn't need sudo to configure

---

### Post by CHFFriday on 2007-12-21
mc4man,
OK I just finished. This is my first compile and I think everything when't OK.

I check to see if K9Copy was in the Aplications menu but it is not there. So what is the next thing I do?

CHFFriday
 PS I got a bunch of new stuff on the Other nenu. Looks like KDE stuff.

CHFFriday

---

### Post by mc4man on 2007-12-21
I'm not sure how you installed it, in any event you can run from terminal. i never do a complete uninstall so my menu and symlink stay and for k9 i use checkinstall  to install and create a .deb. If you used make install  I'm not 100%sure this is right (worse case do make uninstall  and then checkinstall) Anyway 1st. run
```
sudo ln -s /usr/local/kde/bin/k9copy /usr/bin/k9copy
```
and then create a menu entry  - run
```
gksudo gedit /usr/share/applications/k9copy.desktop

```
and paste this in and save
```
[Desktop Entry]
Name=k9copy
Comment=DVD ripper
Exec=k9copy
Icon=/usr/local/kde/share/icons/hicolor/48x48/apps/k9copy.png
Type=Application
Categories=Application;AudioVideo;


```
Note: credit/thanks for above to kpkeerthi

---

### Post by CHFFriday on 2007-12-21
mc4man,
Well sorry nothing is working. It doesn't surprise me. I'm going to leave it until after the Holidays. Right now I'm not into it. 

I hope you can stay with me later as you have been a great help. I will send you a private message when I get back to this project in a few weeks.

CHFFriday

---

### Post by ninja_in_pajamas on 2007-12-26
I hate to sound like a total noob, but can someone tell me (in a fair amount of detail) how to install it from the tar.gz?  Tried installing the deb but when I try to install it I get 
Error: Dependency is not satisfiable. kdelibs4c2a

I have that file already installed and I even reinstalled it just to make sure.

That's why I want to try doing it from a tar.gz that I downloaded.

Can anyone help?

---

### Post by wjston on 2007-12-26
> **ninja_in_pajamas said:**
> I hate to sound like a total noob, but can someone tell me (in a fair amount of detail) how to install it from the tar.gz?  Tried installing the deb but when I try to install it I get 
Error: Dependency is not satisfiable. kdelibs4c2a

I have that file already installed and I even reinstalled it just to make sure.

That's why I want to try doing it from a tar.gz that I downloaded.

Can anyone help?

Follow this link and scroll down to post #26 ([http://ubuntuforums.org/showthread.php?t=607991&page=3&highlight=k9copy](http://ubuntuforums.org/showthread.php?t=607991&page=3&highlight=k9copy)). I think you should be able to install the latest version 1.2.1 from the tar.gz file you downloaded. Just make sure you uninstall any previous version of K9copy prior to doing the build.

---

### Post by zipperback on 2007-12-31
> **CHFFriday said:**
> mc4man,
Thanks for the get back. This is how far I got. Same as last time.
The last line there is an error.

CHFFriday

chance@IMB600x:~/Desktop/k9copy-1.2.1$ sudo ./configure
[sudo] password for chance:
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables

You need to install the required files so that you can properly build executables.

Open a terminal window and then enter the following:
sudo apt-get install build-essential

That will install all the essentials conpile the application in question

The last line of your error message says that you don;t have everything to properly compile on your system.

The above listed installation should resolve the problem for you. Once it is installed, then try compile your application again. It should work  this time.

Please let me know what happens. Thanks.

Best regards,
- zipperback
:popcorn:

---

### Post by CHFFriday on 2007-12-31
Zipperback,
Sorry for not getting back to you.
I still can not get this to work. 
If I sudo make errors pop up all over the place. Same for sudo checkinstall.

Buy the end of the week I will build a clean Gusty machine and try again. Can you give step by step instructions?

CHFFriday

---

### Post by mc4man on 2007-12-31
@CHFFriday - will get back with something for you

---

### Post by mc4man on 2008-01-01
> Buy the end of the week I will build a clean Gusty machine and try again
Had nothing much to do today so i edited out a redundant post on another thread and did a step by for installing the latest ver. (1.2.2) onto a fresh gutsy install. If you take your time and follow in order there will be no problems.
[http://ubuntuforums.org/showthread.php?t=607991&page=3&highlight=k9copy](http://ubuntuforums.org/showthread.php?t=607991&page=3&highlight=k9copy)     #27
 also will work on existing gutsy just use relevant parts.
i like this way better than previous method i was using - the symlink caused me some probs. when going from 1.2.1 to 1.2.2

---

### Post by CHFFriday on 2008-01-02
To all,
Big thanks for everyone’s help. The best thing about this months long project is I have learned allot about Linux/ Ubuntu. To us tech guys it’s more about “How do you do this? What makes it work? How can I fix it? How Can I use this now and in the future?” During this project I have install Ubuntu at least ten times using different hardware combinations etc. Changed video card and learned how to get things working after that. I could go on and on but this is not the place.  I just thank God I have the time and means to do this.

Now that I have said this, here is what I did on Tuesday. I installed K9Copy 1.2.2 using the link by wjston. I had to make some changes as they pertain to 1.2.2. I far as I know everything went will as I can start K9Copy 1.2.2. This is using Gusty! There are still problems using the program and I think it has something to do with Gusty. Here’s why. I installed K9Copy 1.1.0 on a Feisty machine! Guess what I can make a copy of the complete DVD the SAME DVD I tried on the machine that was running K9Copy 1.2.2.

I will play with this as I have time! Anyway, I again want to thank all you guys for you help and teaching expertise! 

CHFFriday

---

### Post by wjston on 2008-01-02
> **CHFFriday said:**
> 
Now that I have said this, here is what I did on Tuesday. I installed K9Copy 1.2.2 using the link by wjston. I had to make some changes as they pertain to 1.2.2. I far as I know everything went will as I can start K9Copy 1.2.2. This is using Gusty! There are still problems using the program and I think it has something to do with Gusty. Here’s why. I installed K9Copy 1.1.0 on a Feisty machine! Guess what I can make a copy of the complete DVD the SAME DVD I tried on the machine that was running K9Copy 1.2.2.

I will play with this as I have time! Anyway, I again want to thank all you guys for you help and teaching expertise! 

CHFFriday

What I would do is uninstall the build (1.2.2) on Gutsy using the package manager, and then I would follow mc4man's tutorial. I just updated my version using his howto and the only thing I had to do was put my username in wherever he specified /usr. I just backed up a DVD I bought my wife for XMas and I am playing it now (works great). As I said in my post #26, make sure you have all the dependencies necessary for K9copy to function properly. As you can see from mc4man's post, you will need to add x264 for encryption purposes. I just checked that I had everything using Synaptic Package Manger prior to proceeding with the build. Everything went well and I now have the latest version of K9copy running on Gutsy without a problem.

---

### Post by CHFFriday on 2008-01-03
Wjston or mc4man,

What is x264? This is a new one for me. I thought all de-encryption was done with libdvdcss2. I really don’t think I have it is install on the Gusty / K9Copy 1.2.2 machine. I missed it altogether! Were do I get it? And do you think other packages use this? Could this be the cause of problems that other people are having?

CHFFriday

---

### Post by mc4man on 2008-01-03
> What is x264?
[http://en.wikipedia.org/wiki/X264](http://en.wikipedia.org/wiki/X264)   - basic description and links out
> Could this be the cause of problems that other people are having?
absolutely not
I would think 90% of any problems regarding k9 are title and backup mode specific. I sense the intent and purpose of this forum would not be well served by discussing solutions for particular  titles, there are other forums which are better suited.
some general thoughts
[http://ubuntuforums.org/showthread.php?t=607991&page=2](http://ubuntuforums.org/showthread.php?t=607991&page=2)   #13

---

### Post by sakis on 2008-01-07
I believe this [http://www.getdeb.net/app.php?name=K9Copy](http://www.getdeb.net/app.php?name=K9Copy) is easier ;)

---

### Post by CHFFriday on 2008-01-08
Thanks for the responce.
Got everything working. Had to change the DVD Drive. Plexter did not work. Installed Lite-On.

CHFFriday

---

### Post by mc4man on 2008-01-08
Just a note for those with plextor drives. A lot their models by default have a dvd read setting enabled which limits the read spead to 2 -2.4x during playback and consequently ripping. While most windows rippers will override this not so much in linux. Before inserting disk hold down the eject button till the light flashes 3 times - good till reboot
@CHFFriday - not saying this was your issue - just thought I'd mention

---

### Post by CHFFriday on 2008-01-08
mc4man, Good to know.
One last thing on this. (Famous last words):)

When the Plextor is install and you go to Places there are TWO cdrom icons. This happens on any Ubuntu machine I install the Plextor on. Got any ideas. Please don't spend to much time on this.

CHFFriday

---

### Post by mc4man on 2008-01-08
I've pretty much don't pay much attention anymore to what places shows (as long as all is working)
An example why - the  setup is
2 sata hdd's on sata0 and sata1 from the mobo
A plextor 716 on primary ide as master  (mounts at /media/cdrom0 but is /dev/cdrom1)
A benq on secondary ide as master       (mounts at /media/cdrom1 but is /dev/cdrom )
so when I boot up only 1 cd/dvd device shows up in places -/dev/cdrom  (benq)
The plextor (/dev/cdrom1) is not shown after booting or even when i insert and mount media (though it plays fine and can be accessed at /media/cdrom0 ). With media in the plextor the icon in places remains with the benq.
if i now insert media into the benq then a 2nd icon shows up, the original icon switches to the plextor and the new one (with a (2) under it) becomes associated with the benq
I had replaced a plextor 712 with the 716 I believe after installing gutsy so my (uneducated) thinking is when you remove(replace ) a cd/dvd drive it may get a new /dev listing so to speak , but will retain it's mount point based on cable(s) position, ie. a drive that's in a master position will mount to /media/cdrom0
if you have only 1 drive with 2 icons I'd check the properties of each and see what drive  they  associate with. if it's the same drive then maybe insert some media and run in terminal
```
isoinfo -d -i /dev/cdrom
```   if it returns info the the drive is /dev/cdrom, if not or for the hell of it run ```
isoinfo -d -i /dev/cdrom1
```

---

