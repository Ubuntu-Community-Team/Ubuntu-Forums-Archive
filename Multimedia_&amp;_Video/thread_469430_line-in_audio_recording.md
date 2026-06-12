---
title: "line-in audio recording"
date: 2007-06-09
forum: Multimedia &amp; Video
---

### Post by ahkond on 2007-06-09
Hello folks - 

I am trying (and trying and trying) to record line-in audio using anything that can be cron-scheduled (that is, a command line interface).  I have been beating my head against this wall ever since Feisty came out and I installed it on a brand-new PC.  

I have verified that my line-in is working correctly by running audacity and monitoring the input line; there is sound there.  So the sound card is OK, etc. 

However, audacity does not seem to support command-line operation that would work well with a cron job.  Therefore I can't use it as my daily tool.  

After searching on-line and seeing various forum posts and other articles, I have installed about a dozen other audio tools (lame, alsa, ecasound, aumix, pydar, Gary Burd's "fmcapture" python script, gramofile, jackd, sox, etc.) but each of them has at least one of these problems: 

a) can't install without cryptic errors that I don't know how to address
b) install, but can't run without cryptic errors that I don't know how to address
c) seem to install correctly but I have no idea where they are or how to run them
d) are so poorly documented or are so insanely complicated to use that I can't figure out how to run them at all
or 
e) run, but produce blank/empty sound files, implying that they're not hearing the line sound

If the line-in is not an option, I also have a RadioShark USB FM tuner that I can use as the audio source.  I've read various web pages and articles about using RadioShark under Linux, but see above for my results.  But I would rather just use the line-in (fewer moving parts) if possible.  This tuner is currently on my Windows box, performing the one daily job that is preventing me from turning it off and using my Ubuntu box as my main workstation (yes, I am trying to migrate).  

Does anybody have any suggestions?  Surely somebody somewhere has wanted to record audio from the "line in"??  I am comfortable programming in perl and Python so I can cope with scripts, but when the scripts start referring to mysterious entities and I have no way to figure out what they're referring to, I get stuck.  Likewise when I'm trying to read online documentation and I only get about two sentences in before the author is using terms that I not only don't recognize but I literally have no idea where to look them up.  

I realize in advance that Audio Is Difficult because of the huge variety of hardware, file standards, etc. out there so maybe there is no simple solution.  But I was hoping that audio on ubuntu would "just work".  

Thank you

-ahkond

---

### Post by reclusivemonkey on 2007-06-21
Have you tried arecord?

---

### Post by ahkond on 2007-06-21
First, thanks for the reply.  

As for arecord, no, I haven't, because I can't figure out its yelp/man page.  It describes things in terms of "PCMs" but I don't know what "PCM" stands for or, more importantly, where to find out.   The example in the yelp page says this: 

> arecord -d 10 -f cd -t wav -D copy foobar.wav
    will record foobar.wav as a 10-second, CD-quality wave file, using the
    PCM "copy" (which might be defined in the user's .asoundrc file as:

    pcm.copy {
      type plug
      slave {
        pcm hw
      }
      route_policy copy
    }


I don't understand the example because "PCM", "plug", "hw", "route_policy" and so on are mysterious to me, and I don't understand the rules governing the .asoundrc or the concepts that it manages. I tried running arecord -L to see what "PCMs" are already defined on my computer, and got several screens of more of the same, and I don't know what to change, or why.   

So, I'm still lost.  

-ahkond

---

### Post by reclusivemonkey on 2007-06-22
Well, very basically, PCM is just the sound coming out of your computer. If you feel more at home in the GUI, then just use the Gnome Mixer to set what channel you want to record (PCM should just recard all the sound you hear). Just giving it a try should show you its simple enough. What are you actually wanting to record?

---

### Post by ahkond on 2007-06-22
1. Thanks, but ... there is no Gnome Mixer in my Applications menu or System menu.  I have searched various documentations and Googled for it, and while some web pages talk about the Gnome Mixer I am unable to find out how to start it.  I get the impression that there is no such thing as "the Gnome Mixer" and instead there are several mixers and maybe people are being imprecise.  

Searching in the Synaptic package manager for "mixer" produces about a dozen matches (but not "the Gnome Mixer") and I cannot guess which one you mean.  One of them is called "alsamixer" and I have installed that; running it shows me a display that does not give me any new understanding.  

I see volume levels for PCM, Front, Surround, Center, LFE, Side and Capture.  I do not know how to "set the channel" using this (nothing in the display mentions "channels"), and this screen does not tell me anything that I can use in terms of setting up arecord or other utilities because I don't know how the terminologies connect.  In fact, I'm not sure whether you told me to use the mixer to help me edit my .asoundrc file, or to do something else with it.  Looking at the mixer does not make things more clear for me.  

Maybe this is simple if you already understand it, but I don't understand it.  There's nothing useful in the alsamixer "help" menu.  

If you have some other mixer app in mind, and not alsamixer, then I don't know what it is.  

2. I am trying to record daily broadcasts on my Sirius satellite radio receiver, using a line in/line out connection.  The radio receiver has a "line out" jack and I am connecting that to my computer's "line in" jack with a cable.  I want to record a radio show every day using a cron job that would execute a command to record the "line in" signal, for a certain amount of time, into a playable sound file that I can listen to later or put onto an iPod.  

3. By the way you're spelling [Confucius]("http://en.wikipedia.org/wiki/Confucius") incorrectly ...

---

### Post by ahkond on 2007-12-01
Six months later and I am still unable to solve this problem.  Can anybody help??

---

### Post by irlandes on 2007-12-08
I can record on one machine with Kubuntu by the following:

open one terminal konsole, and type aumix

which opens a mixer box. It is preset correctly on mine.

Then open another konsole and type, when you are ready to record:

arecord -f cd filename.wav

and on one machine it records until I hit CTRL-Z to stop it.

I don't know anything about PCM stuff.

What I just told you should record anything going through the computer.

---

### Post by Bob4242 on 2008-01-06
> **ahkond said:**
> Six months later and I am still unable to solve this problem.  Can anybody help??

Did you just want to copy satellite radio music onto your PC hard drive?  I've been doing that and then transfering it onto CDs, if you want the method for that.
-Bob

---

### Post by Lostincyberspace on 2008-01-06
You might try pulse audio I have a thread running here
[http://ubuntuforums.org/showthread.php?t=660502](http://ubuntuforums.org/showthread.php?t=660502)

---

