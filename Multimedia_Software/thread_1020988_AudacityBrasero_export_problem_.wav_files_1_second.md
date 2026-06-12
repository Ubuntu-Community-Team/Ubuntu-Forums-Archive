---
title: "Audacity/Brasero export problem .wav files 1 second long"
date: 2008-12-24
forum: Multimedia Software
---

### Post by PierreRussellStraddler on 2008-12-24
Hi everyone!

I am running ubuntu 8.10 and recently got Audacity and Grip for the purpose of "trimming" some audio.

Everything seems to work (more or less...) in Audacity.  With a few bumps and bugs, It seems to have successfully exported a 118.7MB .wav audio file (a 12 minute song) to the "music" folder.

When I go into brasero and add that 118.7MB .wav file, the preview shows a total track length of 0:00, and the message 

"track will be padded at it's end, the track is shorter than 6 seconds."

any ideas?

I don't even know where the problem 'lives.'  Is it an Audacity problem?  Is it a Brasero problem?

Of course, any help anyone could provide would be greatly appreciated.

Thanks in advance,

Pierre Russell Straddler

---

### Post by outcesticide on 2008-12-24
ok it could be a number of problems like the format is wrong for that so you could try converting it, it could be a size issue with whatever your burning it to, or audacity might just be bugged im not perfectly sure but ill check it out.:)

---

### Post by SuperSonic4 on 2008-12-24
It could even be a codec, do you have wavpack installed?

---

### Post by logos34 on 2008-12-24
you might consider trying wavbreaker--it's a lot lighter and you don't need to import/export the file after editing

---

### Post by Bucky Ball on 2008-12-24
When you are ready to export your finished, trimmed music file out of Audacity, are you doing:

Export as .wav
Export as MP3
Export as ogg

?

You can't just 'save as' as that will save an .au file which will not be recognised by much else (it is an Audacity project file).

I've used Audacity for a couple of years and love it.

---

### Post by mc4man on 2008-12-24
A couple of weeks ago several posters were getting the same error and in addition rhythmbox would also not play the .wav's ripped from grip and any other non gstreamer method. 

Though wav's ripped by gstreamer apps did play, enter into brasero and burn.

I've since updated and now 'non gstreamer' ripped .wav's now play in rhythmbox and enter into brasero with the exception of tracks copied  directly from a cd, (drag to folder or desktop), which still produces the same exact error in brasero and rhythmbox. 
(may be a header difference

---

### Post by Bucky Ball on 2008-12-24
I use sound juicer to rip and all seems to work fine with that also.

---

### Post by PierreRussellStraddler on 2008-12-25
outcesticide: As for the size, it is interesting to note that the .wav files exported from audacity were 118.7MB whereas other .wma files in my music folder are only about 3 to 5 MB.

supersonic4: I think I have wavepac installed...would it hurt to install it again?  do you know the command line commands to install said wavepac, or is that something I should do from synaptic package manager?

logos34: I will look into wavbreaker.  Thanks.  PS  what do you mean by "lighter?"

Bucky Ball:  In my "music" folder on my hard drive are four files:
 track_01.wav  118.7MB
 track_02.wav  148.8MB
 track_03.wav  149.2MB
 track_04.wav  189.9MB

as far as I know, they are all .wav files.  Do they need to be in the same folder as the related ".au" files? 

It appears that Audacity has turned them into actual files, and when I listen to them in Audacity, they are "trimmed" and sound fine.  The problem seems to be when I get to Brasero...it can't read them.  Maybe it's a brasero problem?

mc4man: what is a "gstreamer method?"  can I trim audio in gstreamer?  What is a header difference?  I am a little confused.  More than a little, actually...

Bucky ball: I'm not sure I'm having a problem ripping.  Or am I?  If I have a 118.8MB .wav file on my hard drive, does that mean I have a 118.8MB .wav file on my hard drive?  Why can't I burn it on to a CD?  Is that a ripping problem?  I am confused.

lastly, I used to get a notification in my e-mail when these posts got a response.  I also can't see this post in my user CP--which is an entirely different issue, and of the two, I'd really rather be able to burn CD's of .wav files I created in Audacity.

thanks to everyone and happy holidays

pierre russell straddler

---

### Post by logos34 on 2008-12-25
> **PierreRussellStraddler said:**
> 
logos34: I will look into wavbreaker.  Thanks.  PS  what do you mean by "lighter?"


uses less memory

---

### Post by SuperSonic4 on 2008-12-25
```
sudo apt-get wavpack
``` if you have it already it won't override it.

---

### Post by PierreRussellStraddler on 2008-12-25
logos34:  I just recently and easily downloaded wavbreaker, and it read the audacity file just fine.  I even used to to (easily) trim a bit of sound from a .wav file.

after that was all done, I pressed the "export to toc" button, which it seemed to do.  there are now four .toc files in my /home folder.  Sadly, brasero didn't recognize them--I got the error message that said "can't be handled by gstreamer--make sure the appropriate codec is installed"

That said, the file names don't include a .toc at the end.  Perhaps that is the problem?  I will try and let you know.  Thank you for the tip on wavbreaker, though.


supersonic4:  hiya!  thanks for the terminal code.  When I entered 

sudo apt-get wavpac

it asked me for my password, which I entered (correctly) and from there got the message:

E: Invalid operation wavpack

:(

Oh well.

Thanks everyone for your help.  I feel like we are getting closer!

warm holiday wishes,

Pierre Russell Straddler

---

### Post by SuperSonic4 on 2008-12-25
*expletives* I always make that error, it should be ```
sudo apt-get install wavpack
```

---

### Post by PierreRussellStraddler on 2008-12-25
And another thing...

I notice that the .toc files are quite small--all around 100bytes, as opposed to the .wav file, which are all around 120MB.  

Something to look into, I suppose.

Thanks

PRS

---

### Post by PierreRussellStraddler on 2008-12-25
wow.  that was fast.

installed with new code and everything seemed to work.  now to try and burn a CD

Thanks!

---

### Post by PierreRussellStraddler on 2008-12-25
Unfortunately, the install of wavpack didn't make any difference.

brasero still reads the .wav files as being less than 1 second long, and when I try and burn the .toc files from wavbreaker, I still get the message "unhandled song, can't be handled by gstreamer, make sure the appropriate codec is installed."

:(

---

### Post by logos34 on 2008-12-25
> **PierreRussellStraddler said:**
> logos34:  I just recently and easily downloaded wavbreaker, and it read the audacity file just fine.  I even used to to (easily) trim a bit of sound from a .wav file.

after that was all done, I pressed the "export to toc" button


all you need to do is >Edit>Add track break>Save button. you'll end up with two .wavs

brasero reads mine fine, but i'm on 8.04--seems you're having Intrepid-specific problems

good luck

---

### Post by mc4man on 2008-12-25
what I meant by "gstreamer method' is using a gstreamer app to rip. The problem for the most part has resolved itself except for .wavs that are copied off of a cd directly. (drag and drop, or copy and paste

While it's no guarentee that brasero will work can you play back your .wav's with rythmbox?

Here's somewhat relevant part of thread from a month ago, but as I said almost everything has been fixed. (only points out that in 8,10 brasero had a problem with normal .wavs (and still does to a limited extent


[http://ubuntuforums.org/showthread.php?p=6221137#post6221137](http://ubuntuforums.org/showthread.php?p=6221137#post6221137)


Edit :  As mentioned in last post of link,, If I take a .wav that brasero does the 'track will be padded ,shorter than ...." and run it thru sox first, brasero will then recognize it properly. (and will be slightly smaller after sox 'processing'

Ex. made a folder foo, stuck a 'problem' .wav in it. and ran sox
```

doug@doug-desktop:~/Desktop/foo$ sox foo.wav foo-1.wav
```

Pre sox (won't work in brasero) -  32716434 bytes
Post sox (will work in brasero) -   32716364 bytes  (70 bytes smaller

---

### Post by PierreRussellStraddler on 2008-12-26
Hiya!

what I meant by "gstreamer method' is using a gstreamer app to rip. The problem for the most part has resolved itself except for .wavs that are copied off of a cd directly. (drag and drop, or copy and paste


--this is awkward, as many of the .wavs I need to trim are on CD's.

While it's no guarentee that brasero will work can you play back your .wav's with rythmbox?

--no.  And when I try, it asks if I would like to download the suitable codecs.  I answer yes, down load the codec's and everything seems to go fine and then...rhythmbox fails to play the files.  When I go to look for other files in rhythmbox, I get the message that "the folder contents cannot be displayed."

doug@doug-desktop:~/Desktop/foo$ sox foo.wav foo-1.wav

--I am a little confused...my music files live in /home/pierre/Music

my track is called track_01final.wav

when I type

/home/pierre/Music/foo$ track_01final.wav track_01finalsox.wav
 
I get

bash: /home/pierre/Music/foo$: No such file or directory


when I type

/home/pierre/Music/track_01.wav sox track_01.wav track_01sox.wav

I get

/home/pierre/Music/track_01.wav:  No such file or directory


obviously I'm getting the terminal code wrong.  to help you (or someone) help me, here are the specifics:

in /home/pierre/Music are four files:

track_01final.wav (118.7MB)
track_02final.wav (149.8MB)
track_03.wav (149.4MB)
track_04afinal.wav (189.9MB)

How do I write that sox code?

Thanks again for all your help.

p.s., I did read your other post and in so doing asked myself if Kb3 might be an easier solution to this brasero problem.  I also asked myself if newer versions of Ubuntu (we are past Intreped Ibex aren't we?) might have solved the problems you outlined?  Lastly, is there a "bomb proof" software set up for Intrepid Ibex that can
a:  take tracks from a cd
b:  put them in an editing environment where they can be "trimmed"
c:  burnt on to a disc that can be played in the stereo

I am not "in love" with brasero, audacity or any of it, so if there was a functional software coctail I could download, I would be happy to do so.

anyhow, thanks again.  happy boxing day

Pierre Russell Straddler

---

### Post by mc4man on 2008-12-26
try this (more to test your .wav

First, is sox installed?, do this to ck. and install if not already
```

sudo apt-get install sox
```

Then in terminal 
```

cd /home/pierre/Music 
```

You should now be at a Music$ prompt


```
sox track_01final.wav track_01-1final.wav
```

Take the new .wav and see if it's accepted in braseo and or plays in rhythmbox.


Are your orig. .wav's (before audacity) playable or seen properly by brasero?

---

### Post by PierreRussellStraddler on 2008-12-26
YAAAAAAAAAAYYYYY!!!!!!!!!!1

the file was read by brasero and rhythm box.

THANK YOU!!!!!!!!!

I am going to try and make a cd of the four tracks, putting them through sox as directed above.  AWESOME!

What is sox?  What did it do to make the .wav work?

thank you again.  best boxing day gift ever.

pierre russell straddler

---

### Post by Bucky Ball on 2008-12-27
What I meant was, after you have edited your file in Audacity, trimmed or whatever:

File->Export

... and you are presented with a window which has 'Options' down the bottom. Click that. Choose what file type you want to export your project as (in your case, choose mp3). It may be set up to export as mp3 anyhow. You are there. The .au files I don't even save, let alone in the same folder. They are of no use to me once things are trimmed and just take up space on the hard drive. As I said, forget them, they are *Audacity Project Files* which *contain all the settings* for your project, *not just music*, and many of these settings have nothing to do with audio as such but relate to where you had your gain set, where you have put your trim and other edits and control settings.

---

