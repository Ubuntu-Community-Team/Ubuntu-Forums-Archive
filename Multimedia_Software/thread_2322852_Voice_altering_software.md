---
title: "Voice altering software"
date: 2016-04-30
forum: Multimedia Software
---

### Post by john547 on 2016-04-30
I searched long and wide and didnt find any software available on ubuntu that is able to change voices on the fly (like for skype sessions etc) 

So I rested my case

What I am looking now is a software that is able to change my voice if not in real time then atleast by using a prerecorded file of my voice.

I am willing to do lots of work in order to make the software work but after that the software should be kinda user friendly (= if it needs more than twisting a few graphical knobs or load some presets then I am not interested to invest time int it)

By voice altering I mean it should have setting or presets to make my voice (28 male) sound like a female, child, monster, etc I need it to use it as voiceovers for my animated cartoon characters.

I have found only one that claims to does such a thing and that should work in ubuntu called asterisk-voice changer and its an plugin for the asterisk suite... I have installed the latest asterisk + all the libraries etc successufly but when I try to make, I get error messages from the plug-in and official site seems to be offline... so. yea there is that..


If nobody can help me find out an alternative then I would leave the error message here so that maybe I could make something out of this post after all :P 

```

"myusername"@"myusername"-desktop:/usr/src/asterisk-voicechanger-master$ sudo make
[sudo] password for "mysuername": 
gcc -g -O2 -shared -fPIC -Wall -pedantic --std=gnu99 -c -o app_voicechanger.o app_voicechanger.c
app_voicechanger.c: In function &#8216;audio_callback&#8217;:
app_voicechanger.c:82:35: error: &#8216;frame->subclass.format&#8217; is a pointer; did you mean to use &#8216;->&#8217;?
     switch (frame->subclass.format.id) {
                                   ^
                                   ->
app_voicechanger.c:83:10: error: &#8216;AST_FORMAT_SLINEAR&#8217; undeclared (first use in this function)
     case AST_FORMAT_SLINEAR:
          ^~~~~~~~~~~~~~~~~~
app_voicechanger.c:83:10: note: each undeclared identifier is reported only once for each function it appears in
app_voicechanger.c:86:10: error: &#8216;AST_FORMAT_SLINEAR16&#8217; undeclared (first use in this function)
     case AST_FORMAT_SLINEAR16:
          ^~~~~~~~~~~~~~~~~~~~
Makefile:10: recipe for target 'app_voicechanger.o' failed
make: *** [app_voicechanger.o] Error 1




```

---

### Post by TheFu on 2016-05-02
"audacity different voices" - has lots of youtube videos.  Normally, I'd do more than this ... but **audacity** is THE audio tool on Linux (and Mac and Windows).

If audacity isn't enough - some more options [http://www.makeuseof.com/tag/6-awesome-alternatives-to-audacity-for-recording-and-editing-audio/](http://www.makeuseof.com/tag/6-awesome-alternatives-to-audacity-for-recording-and-editing-audio/)

Asterisk is a PBX system (voice over IP phones).  If you don't want a PBX, I wouldn't head this direction due to some added complexity.  BTW, using sudo with make like that is probably a not-so-good idea.  Only **sudo make install** would need root. Everything else related to software development shouldn't need root.

---

