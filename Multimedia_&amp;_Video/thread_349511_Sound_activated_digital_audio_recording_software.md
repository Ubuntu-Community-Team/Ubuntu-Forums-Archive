---
title: "Sound activated digital audio recording software?"
date: 2007-01-30
forum: Multimedia &amp; Video
---

### Post by chadk on 2007-01-30
Does anyone know of a linux application that would allow me to set my PC to record AUDIO whenever sound above a certain level is detected?  I'd like to say, record 30 seconds every time a loud noise is detected.  

I have parrots who love to talk but I'm never in a good spot to record them when they do and I'd like to just put my pc into a recording mode so when I leave for the day or whatever, it will record them being silly.  

Here are some examples of Windows apps that seem to do what I want.  I have not tried them through WINE yet.

[http://www.yogen.com/audiomagic/](http://www.yogen.com/audiomagic/)
[http://www.sound-snooper.com/en/features.php](http://www.sound-snooper.com/en/features.php)

---

### Post by Jussi Kukkonen on 2007-01-30
There is at least one, I've used it to spy on my dog (I suspected he was barking when alone). Unfortunately I've forgotten what it was called. It was command line based and very simple to use.

I'll see if I can find it.

EDIT: no, sorry.

---

### Post by chadk on 2007-01-30
lol well thanks anyway.  So, was your dog barking?

---

### Post by chadk on 2007-01-31
I have been searching google and have found nothing.  Perhaps someone can point me towards a very simply sound recording software for linux (open source) so I can just modify it to suit my needs?

---

### Post by ksenter on 2007-02-23
I was wondering the same thing...  After some research I found manauton [http://manauton.sourceforge.net/](http://manauton.sourceforge.net/) 

It took me several hours to get it installed as well because I could find no info on how to get manauton to work in ubuntu...  So I had to muddle through it...  So hopefully the following instructions helps other people.  

Here's what I found I had to do to get it to work, if you need more specific instructions let me know:

-download the source from [http://sourceforge.net/project/showfiles.php?group_id=74593](http://sourceforge.net/project/showfiles.php?group_id=74593)

-add the following packages to ubuntu if you don't already have them: build-essentials, libasound2-dev, libncurses5-dev, libncursesw5-dev (I don't know if both of the ncurses are needed or if it's just one or the other because I added them both just in case after I got the ncurses error)

-edit the "manauton/alsa_pcm_reader.c" file to change the include statement from <sys/asoundlib.h> to <alsa/asoundlib.h> and add the following define statements 
#define ALSA_PCM_OLD_HW_PARAMS_API
#define ALSA_PCM_OLD_SW_PARAMS_API

-edit the "externalcontrols/controller.c" file to remove the extra line breaks in the string starting on line 49 (so all of the lines end with a backslash)

-in the sourcecode's directory run ./configure --with-alsa

-then run make

-then make install

-I also had to turn on my mic boost for it to work well but I imagine that depends on your microphone

-that's pretty much it, after that it was just figuring out the right command line parameters for what I was trying to do, in my case the following seems to work fairly well:  manauton --criteria=hitcount2,2 --chained --pdelay=2.0 --latency=1.0 test.wav

I know this probably isn't the most clear set of instructions (I'm tired) but I wanted to go ahead and type it up while I kind of remember what I did.

-Ken

---

### Post by DarkTUX on 2007-03-26
Nice work !

i have been looking for just such a program for a very long time, i would be very greatfull if you could send me a copy of the modified files. Or expand your previous instructions a little because i cant get it to compile without tons of errors. :( 
So i guess im doing something wrong.

/DarkTUX

---

### Post by ksenter on 2007-03-26
No problem, I'm happy to help!  Unfortuantely I'm away from the computer that I set this up on at the moment, but maybe that's a good thing as it'll give me a chance to refresh my memory as I try to set it up on this machine.  :)   First off however, can you tell me which version of ubuntu you're running (in case that matters), so that I can verify we're working in the same version.

---

### Post by DarkTUX on 2007-03-26
Wow ! quick reply !
Well,  im using 6.10 for i386 for now but will upgrade to 7.04 as soon as it is released.

Thanx ! 

DarkTUX

---

### Post by ksenter on 2007-03-26
Ok you're running the same version I'm on here.  I'm trying it now, following my own instructions, we'll see how it works.  First thing I noticed is that I said to install "build-essentials", the real name is build-essential (without the s at the end) oops.  The next thing I notice is that in the source code I said to edit "manauton/alsa_pcm_reader.c" whereas it's actually "Manauton/alsa_pcm_reader.c" (capital M) and the "externalcontrols/controller.c" is actually "ExternalControl/controller.c".  Next problem I noticed is that the files are readonly, so make sure you give yourself write access to both of these files before editing them.  I also realized the instructions for controller.c aren't very clear.  I'll try to be clearer, there's a string in that file, the definition of that string starts on line 49, but the line breaks that need to be removed are like line 64 I think, basically line 64 (I think) should look like this "smsmouse#,R,P,Q\n\" instead of:
"smsmouse#,R,P,Q

\n\"
I also noticed, and this is most likely where you're getting the errors, that I said to add:
#define ALSA_PCM_OLD_HW_PARAMS_API
#define ALSA_PCM_OLD_SW_PARAMS_API
But I didn't specify that they need to be added BEFORE the <alsa/asoundlib.h> line.

Oh, and lastly I noticed I didn't mention you'll probably want to use sudo on the make commands.

In my defense it was late night/early morning when I typed this up the first time :) .

Ok, so that seems to work for me here.  Let me know if you get an error.  Once you get it working and verify that the instructions work, I'll try to type up a revised set of instructions that make this easier, or maybe I can figure out how to write a script to do it... I'm still pretty new to this linux stuff.

---

### Post by ksenter on 2007-03-27
Any luck?

---

### Post by DarkTUX on 2007-03-28
Works perfectly..... super thanx ! !! ! 

i had misunderstod what to fix with the \n\ stuff... 




Now im off to record what my gf says in her sleep ;-) 
and since i sleep like a log this is the only option. 
Now even she will hear all the funny stuff she says........



Thanx a thousand times  !

 /DarkTUX

---

### Post by ksenter on 2007-03-28
Awesome, thanks for verifying that it works!   :) :) :) 

Now I just need to clean up the instructions...  Or maybe I should try contacting the author of Manauton and see if he'd add an ubuntu download on sourceforge.  I'm not really sure how this normally works, but I think it makes the most sense to try to contact the author/project admin and see if he's interested in making the changes.  So, that's what I'm going to try first.

---

