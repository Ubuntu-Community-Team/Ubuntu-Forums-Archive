---
title: "Ecasound refuses to output mp3 files..help"
date: 2008-10-28
forum: Multimedia Software
---

### Post by ghanburighan on 2008-10-28
I have a problem with ecasound on 8.10. I have reinstalled Ubuntu 8.10 rc1 on my laptop. When i had 8.0.4 installed i used ecasound in conjunction with my Griffin iMic to record live audio. It worked great.
I installed ecasound and lame fresh from the ubuntu repository with synaptic (so latest stable versions).
Now when i do "ecasound -i /dev/dsp1 -o /home/somename.mp3"

i get:
(note that if i: "ecasound -i /dev/dsp1 -o /home/somename.wav" ecasound is ok and produces the wave file, no problems) 

********************************************************************************
*        ecasound v2.4.6.1 (C) 1997-2007 Kai Vehmanen and others    
********************************************************************************
- [ Session created ] ----------------------------------------------------------
- [ Chainsetup created (cmdline) ] ---------------------------------------------
- [ Connecting chainsetup ] ----------------------------------------------------
(eca-chainsetup) 'rt' buffering mode selected.
(eca-chainsetup) Audio object "/dev/dsp1", mode "read".
(audio-io) Format: s16_le, channels 2, srate 44100, interleaved.
(eca-chainsetup) Audio object "/home/todd/somefile.mp3", mode 
... "write".
(audio-io) Format: s16_le, channels 2, srate 44100, interleaved.
- [ Chainsetup connected ] -----------------------------------------------------
(eca-control-objects) Connected chainsetup: "command-line-setup".
- [ Controller/Starting batch processing ] -------------------------------------
- [ Engine init - Driver start ] -----------------------------------------------
(audioio-mp3) Starting to encode /home/todd/somefile.mp3 with lame.
(eca-engine) WARNING: An output object has raised an error! Possible causes: Out 
... of disk space, permission denied, unable to launch external applications needed in 
... processing, etc.
- [ Controller/Batch processing finished (-3) ] --------------------------------
ecasound: Warning! Errors detected during processing.
(eca-control-objects) Disconnecting chainsetup: "command-line-setup".
waitpid: No child processes
- [ Chainsetup disconnected ] ----------------------

There is plenty of disk space on my pc. I have searched the web and found only one or two people experienced this, but no answers. I'm fairly noobyish so any help would be appreciated. The -ddd option in ecasound isnt much more help. Also the iMic is recognized and can play using VLC.

Thanks

---

### Post by rubing on 2008-11-09
I am having the same problem:

> 
(audioio-mp3) Starting to encode zi.mp3 with lame.
(audioio-forked-stream) Fork child-for-write: 'lame -b 128 -s 44.10 -x -S - %f'
(eca-engine) output error - stop
(eca-engine) stopping engine operation!
(eca-engine) Signaling stop
(eca-engine) Signaling exit
(eca-engine) WARNING: An output object has raised an error! Possible causes: Out 
... of disk space, permission denied, unable to launch external applications needed in 
... processing, etc.

I don't think this happened before i upgraded....arrgh!
It looks like ecasound is having a problem launching lame

---

### Post by rubing on 2008-11-10
I tried executing the LAME command that ecasound is failing on.  It works fine, but I do receive the following strange message: 

Can't step back 277!


I looked on the lame website for exit codes and such, but couldn't find any.  :(

---

### Post by rubing on 2008-11-11
I found the following explanation of this message on transcoding.org:

> What does "Can't step back 17" (or similar) mean?

This message comes from the mp3 decoder (lame). It means that one or more previous mp3 chunks are missing. mp3 uses interdependent chunks, so if any chunks are missing the other chunks that depend on it couldn't be decoded properly. This usually happens when the file was split at some time or had its beginning cut off. There is not much you can do about it. 

So, i tried using ecasound on an mp3 with no chunks missing. However, ecasound still fails. This makes sense since the lame error is not a fatal error.

---

### Post by ghanburighan on 2008-11-16
I,ve tryed using ecasound and lame on 8.10 intrepid on two machines with the same result..fail. I don't know if it's a problem with lame or ecasound. I gave up and reinstalled hardy for now. I hope someone can figure this one out as i'd like to run intrepid but i used ecasound daily to record and can't find any alternative that records direct to mp3. oh well for now.

---

### Post by rubing on 2008-11-17
I'm in the same situation bro, but will wait another week or so before reinstalling 8.04.

I submitted a bug report here over a week ago:

[https://bugs.launchpad.net/ubuntu/+bug/296120](https://bugs.launchpad.net/ubuntu/+bug/296120)

And there is a thread on the ecasound mailing list discussing this problem here:

[http://www.nabble.com/Bug-saving-to-mp3-to20476232.html](http://www.nabble.com/Bug-saving-to-mp3-to20476232.html)

anyways this kind of sucks!!

---

### Post by trandism on 2008-12-20
This problem relates to the fact that intrepid repos give you lame 3.98 without changing the default output cmd for mp3 files that is set in ecasoundrc which sits somewhere below /usr/share but keeps the setting as it used to work with lame 3.96.1 which is on the repos of hardy..

In order to achieve smooth cooperation between ecasound and lame you need to edit the ecasoundrc file and just add a -r switch to the lame command that is set under ext-cmd-mp3-output making it like this:

ext-cmd-mp3-output = lame -r -b %B -s %S -x -S - %f

Cheers
Nick

---

### Post by ghanburighan on 2009-03-05
Tryed editing ecasoundrc with ext-cmd-mp3-output = lame -r -b %B -s %S -x -S - %f

Still wont work.

I have also tryed just Lame to stdout. Records just static. I know the iMic is working becuase i can us VLC to listen to /dev/dsp just fine.

I dont know where the bug is, Lame, ecasound or the newer kernel in Ubuntu Ibex. From ecasound error out i would guess it's lame or ubuntu.

---

### Post by trandism on 2009-03-06
Try apt-get removing lame and compile lame version 3.96.1 and use that lame binary with ecasound

---

### Post by ghanburighan on 2009-03-06
Ah. Success! Thanks so much. Yes I did as you suggested, uninstalled 3.98, downloaded the source for 3.96 compiled and all seems well again. I can record to mp3 direct from my iMic. I used 3.96 (platform independent) not 3.96.1 (i386) because i am using intrepid x86-64. Don't know if that mattered. Hope this helps others.

---

### Post by ezra_dermawan on 2009-05-27
> **trandism said:**
> This problem relates to the fact that intrepid repos give you lame 3.98 without changing the default output cmd for mp3 files that is set in ecasoundrc which sits somewhere below /usr/share but keeps the setting as it used to work with lame 3.96.1 which is on the repos of hardy..

In order to achieve smooth cooperation between ecasound and lame you need to edit the ecasoundrc file and just add a -r switch to the lame command that is set under ext-cmd-mp3-output making it like this:

ext-cmd-mp3-output = lame -r -b %B -s %S -x -S - %f

Cheers
Nick

Nick's solution is worked for me. I'm using ubuntu 9.04. Thanks Nick.

---

