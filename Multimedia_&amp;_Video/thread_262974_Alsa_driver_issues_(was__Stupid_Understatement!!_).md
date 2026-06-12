---
title: "Alsa driver issues (was:  Stupid?? Understatement!! )"
date: 2006-09-22
forum: Multimedia &amp; Video
---

### Post by unlokia on 2006-09-22
Hi all - all I am trying to do is update a f*cking alsa driver and it moans blah blah about not being able to find kernel sources.

( A) why does ubuntu INSIST on calling kernel-sources something diff than suse etc

( B) and most importantly (PLEASE answer in laymans terms not geek speak!) what do I install, and WHICH version of kernel f*ck*ng sources to compile my friggin drivers...

I have Dapper Drake, and if ONLY ubuntu gave you recommended package groups that you should install, just as SUSE 10.0 does, this f*cking distro may be more user friendly - this is no way to carry on, and it is *NOT* user friendly imho!.

I love the *idea* of ubuntu, but it has a *LOT* of loose ends to tidy up, if it is anywhere NEAR as friendly as SUSE and MANDRIVA to install something simple, so I can put in this FRIGGGGGGGGGIN driver!!!


Grrrrr (pardon rant bt Im well f*cked off!!)

---

### Post by christhemonkey on 2006-09-22
First off, 
which ALSA driver are you tring to install?

Most all alsa drivers should be compiled as modules with the main ubuntu kernel.


And see here for which kernel is right for you:
[http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)

Also, such fruity language is not appreciated.
We get the idea that your annoyed...

---

### Post by wieman01 on 2006-09-22
Simple question: Why do you want to update your Alsa driver at all? What's wrong with the current version?

The sound is muted by default. Is that the trap?

_EDIT:_
And yes, the language needs improvement.

---

### Post by unlokia on 2006-09-22
I apologise profusely for my outburst. I have an ACER ASPIRE 1642zWLMi laptop which uses the ALC880/883 type chipset for audio (realtek?)

The frustrating thing is, that I *had* the driver 1.0.12rc3 compiled/installed/*WORKING!* only 2 days ago, but I simply cannot recall the fluke by which I achieved this! :(

the acer.patch is used to patch the patch_realtek.c file as documented here [http://ubuntuforums.org/showthread.php?t=202555&page=5]("http://ubuntuforums.org/showthread.php?t=202555&page=5")

As I have HAD this working and KNOW it worked, I am most annoyed for not having documented this as I did it :(.

All I know is this: when I do ./configure --with-cards=hda-intel it moans about the kernel source not being in the correct place, or installed or whatever.

This is VERY annoying - I am most proud of myself having fixed the graphics with 915resolution :D but *THIS* ... grrr... please help if you possibly can - I just would love to know WHY and WHERE the source is!.

PS: I know where the ketchup sauce is, and it tastes better than all this :D lol

I know SUSE has issues, the same as ANY distro, but it far easier to configure - I hear SUSE calling me back.. all is forgiven my friendly distro.... PLEASE.... ubuntu is WAY newer and more immature than SUSE... fact!

---

### Post by bulldog on 2006-09-22
Yes, well if it worked before,it can work again.

Did you a kernel update by any chance?

You're not very clear about why it stopped working.

If you did a kernel update,and it stopped after that you could try,

sudo aptitude install linux-headers-`uname -r` [fill in the kernel]

---

### Post by unlokia on 2006-09-22
hasn't worked from the outset - outset being a FRESH virgin 6.06 install. Going for bike ride - back in 1/2 hr!.

I havent a clue what to do, but if only ubuntu rocked like SUSE does, I'd consider using it as primary OS.

I have pentium M 735a as proc if that helps?!

havent a clue what kernel I need/use etc

PLEASE if you could assist me, in plain english, I would much appreciate that :D

Have a good time

---

### Post by bulldog on 2006-09-22
Reading your posts I can only say in plain english,

Please,please go back to your beloved SuSe and configure it the way you want and let us be.:-({|=

---

### Post by wieman01 on 2006-09-22
> **bulldog said:**
> Reading your posts I can only say in plain english,

Please,please go back to your beloved SuSe and configure it the way you want and let us be.:-({|=
Wooo... This is a tough response but not quite the answer to his question. 

Unlokia, 

Was your card not recognized in the first place? I mean during the installation of Ubuntu.

---

### Post by Brunellus on 2006-09-22
TO the OP:  This thread title has been changed to reflect the nature of the help request.  Appropriate titles help users who know how to help you know that they can help you.  Titles like the originally posted title are flamebait.  This was probably unintentional.  But we take a dim view of that sort of thing.

It would be helpful if you also described why, exactly, you're looking to compile new alsa drivers.  What problems have you been experiencing, and what guides are you following, if any, that have directed you to compile new alsa drivers?  


> **bulldog said:**
> Reading your posts I can only say in plain english,

Please,please go back to your beloved SuSe and configure it the way you want and let us be.:-({|=

Counter-flames will not be tolerated either.

Please keep discussions civil, technical, and on-topic.


PS:  I left SuSE at v. 9.1.  It was an OK distro back then, but I ended up preferring Ubuntu.

---

### Post by bulldog on 2006-09-22
I know SUSE has issues, the same as ANY distro, but it far easier to configure - I hear SUSE calling me back.. all is forgiven my friendly distro.... PLEASE.... ubuntu is WAY newer and more immature than SUSE... fact!

When I read this kind of respons,I'm done with the guy!!

If you have a problem and I can help to solve it,I'm glad to help.

But when you can't make a decent topic-start with a short discription of your problem,I'm less willing to help.

When you begin to rant and mark Ubuntu as immature,it isn't perfect I know that,I'm done,sorry.

---

### Post by bulldog on 2006-09-22
> **Brunellus said:**
> TO the OP:  This thread title has been changed to reflect the nature of the help request.  Appropriate titles help users who know how to help you know that they can help you.  Titles like the originally posted title are flamebait.  This was probably unintentional.  But we take a dim view of that sort of thing.

It would be helpful if you also described why, exactly, you're looking to compile new alsa drivers.  What problems have you been experiencing, and what guides are you following, if any, that have directed you to compile new alsa drivers?  




Counter-flames will not be tolerated either.

Please keep discussions civil, technical, and on-topic.


PS:  I left SuSE at v. 9.1.  It was an OK distro back then, but I ended up preferring Ubuntu.

I appologize for my remark,shouldn't have put it at the forum.

---

### Post by unlokia on 2006-09-22
flaming aside :D the card is recognised as far as I know, but if you read this ---> [http://ubuntuforums.org/showthread.php?t=202555&page=5]("http://ubuntuforums.org/showthread.php?t=202555&page=5")
You will see that, as I mentioned before, the compiling of the alsa driver (patched) is very easy, but I just cannot fathom out WHAT kernel sources/headers/etc I need for this. 

Im a n00b and not bothered admitting that my Linux knowledge is about 10%, but ANY help, concise and to the point help, is greatly appreciated. Please put it in clear and concise terms, remembering I am a NEWBIE :D thanks guys, I really would be stuck without your assistance! :D

---

### Post by Brunellus on 2006-09-22
> **unlokia said:**
> flaming aside :D the card is recognised as far as I know, but if you read this ---> [http://ubuntuforums.org/showthread.php?t=202555&page=5]("http://ubuntuforums.org/showthread.php?t=202555&page=5")
You will see that, as I mentioned before, the compiling of the alsa driver (patched) is very easy, but I just cannot fathom out WHAT kernel sources/headers/etc I need for this. 

Im a n00b and not bothered admitting that my Linux knowledge is about 10%, but ANY help, concise and to the point help, is greatly appreciated. Please put it in clear and concise terms, remembering I am a NEWBIE :D thanks guys, I really would be stuck without your assistance! :D
you are probably missing the build-essential package:

```

sudo aptitude install build-essential
```

then carry on compiling.

---

### Post by unlokia on 2006-09-22
Nope, done that: # sudo apt-get install build-essential

Ohh what AM I gonna dooo LOL :(

As I said before, I just pointed out that, at least with SUSE it gives you "KERNEL-SOURCES" and tells you to install them, whereas with ubuntu you get LOADS of versions of sources, and Im soo soo lostttt *cries*

---

### Post by Brunellus on 2006-09-22
> **unlokia said:**
> Nope, done that: # sudo apt-get install build-essential

Ohh what AM I gonna dooo LOL :(

As I said before, I just pointed out that, at least with SUSE it gives you "KERNEL-SOURCES" and tells you to install them, whereas with ubuntu you get LOADS of versions of sources, and Im soo soo lostttt *cries*
OK, fine.  What headers are you looking for then?

Let me just say--I know the SuSE community (especially on usenet) can be very snarky, but frankly I'm not in the mood.  I'd rather solve the problem and move on.

---

### Post by unlokia on 2006-09-22
okay (A) what are headers?
and  (B) I haven't a clue, thats why Im here asking for help :)

I have acer aspire AS1642WLMi its a centrino 735a proc :D

Ahhh headers :D [http://linux.maruhn.com/sec/kernel-headers.html]("http://linux.maruhn.com/sec/kernel-headers.html")

I have a rough idea now, but a little expansion of the concept would be useful, thanks guys.

---

### Post by crokett on 2006-09-22
> **unlokia said:**
> Hi all - all I am trying to do is update a f*cking alsa driver and it moans blah blah about not being able to find kernel sources.


Do you know how to redirect to a file?

Thusly:```
 sudo <some command to install alsa driver> | foo
```

You will find a file called 'foo' in your current directory. It should contain the errors from your failed install.  Post it here.

---

### Post by unlokia on 2006-09-22
When you say current directory do you mean "/home/matt" or root "/" what directory do you mean?!.

thanks!. :D

---

### Post by Brunellus on 2006-09-22
current directory is the directory you're in.  if you're at all confused typing

```
pwd
```

will **p**rint the **w**orking **d**irectory.

---

### Post by unlokia on 2006-09-22
Oh yeah I know! Yes I know that pwd command well. Ok well atm Im in... *brace*... windoze :( :( but about to reboot and I shall post again once I am in ok!. So you say the file is called "foo"? righty hi and thanks - seeya in a few mins dudes! :D

---

### Post by unlokia on 2006-09-22
oh dear :9 ```
./configure: line 1372: echo: write error: Broken pipe
matt@matt-laptop:~/alsa-driver-1.0.12rc3$


```

---

### Post by Brunellus on 2006-09-22
I'm moving this thread to the general support section in hopes that users there have a better understanding of what's going on.

---

### Post by unlokia on 2006-09-22
okay.. but whats all this broken pipe stuff?? Im not a plumber :P LOL!! ### would you please post the URL to which this thread has been moved.. thanks!! Cant find it :(

---

### Post by Brunellus on 2006-09-22
"pipe" is this character:  

```
 | 
```

A vertical bar.  In bash, it redirects the output of one program to the input of another.  Breaking that pipeline means that the script points to something that simply isn't there, I think.

---

### Post by unlokia on 2006-09-22
Yeah and foo wasnt there LOL. Okay this is getting ridiculous LOL. gonna create foo and then pipe to it ok

Okay that didnt work either grrr so basicall I type:

# sudo ./configure --with-cards=hda-intel | foo

yeah? well that failed miserably with the broken pipe error I mentioned before.

thanks - now what :-x grrrrrrrrrr

---

### Post by Brunellus on 2006-09-22
don't pipe it to foo, redirect it:

```

# sudo ./configure --with-cards=hda-intel > foo
```

---

### Post by unlokia on 2006-09-22
dont think thats what was said in the first instance, HOWEVER:

here we go:

```
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/matt/alsa-driver-1.0.12rc3
checking cross compile... 
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build... 
checking for kernel linux/version.h... no
The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).

```

Now, if you could recommend what I would install when I have a FRESH VIRGIN ubuntu 6.06 installation, as regards compiling etc, I shall go away, wipe this install and re-do it fresh. Then I maybe will get somewhere a little bit faster LOL!.

Thanks for your continuing help!


### EDIT ###

the result of my 'uname -r' was: 2.6.15-23-386

So, which version of the 'linux-source' and 'linux-headers' do I install, based upon my 'uname -r' result being this?!.

I think I understand - the headers are files which tell GCC how, and in what structure to compile the source code, for a particular system architechture?!

I think I am getting closer to the solution, but I just need SOME help, maybe a LOT lol :D

---

### Post by christhemonkey on 2006-09-22
You need linux-headers-2.6.15-23-386
```
sudo apt-get install linux-headers-2.6.15-23-386 
```

This will give you the relevant kernel headers for your kernel.

---

### Post by unlokia on 2006-09-22
:D :D :D :D

Ahhhh thanks guys you're wonderful!!

the sweet sound, of SOUND!!!

It's so much better watching a video, being able to HEAR it!! :D

You rock, thankyou all so so much.

Matt.

PS: Hope Edgy Eft fixes this by default!.

---

