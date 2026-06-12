---
title: "sound working in flash movies but thats about it..."
date: 2008-05-02
forum: Multimedia Software
---

### Post by phlancelot on 2008-05-02
So my history with getting sound to work in ubuntu has been a long and tired process. I started playing with ubuntu when Feisty Fawn was around and have yet to make sound work 100% on my main desktop machine.

I'm using a creative labs audigy LS soundcard which is several years old. on windows I've never had any trouble (of course I had supported drivers) with getting sound to work in 5.1 or any other way shape or form.

I'm quite sure ubuntu recognizes this as my card as I've followed through some of the stuff on the comprehensive sound solutions guide and passed quite a few of those tests. 

The very perculiar behaviour I am now noticing in Hardy Heron is that I am able to play sounds perfectly well when they are a component of a flash video I am watching within firefox, lets say a youtube video or a myspace page of my favourite band. 

However, when I go to play sounds seemingly through any other method on my computer (mp3s with amarok, movies with VLC) no sound is present whatsoever.

In my history with other ubuntu versions I've noticed sporadic periods of the sound working. Lets say 1/10 times I would boot the system I could get sound to work in amarok or anywhere else.... 

Now it seems the sound in flash movies is here for good, it works 100%, yet I cannot produce sound in any other application....

Just wondering if anyone else has or had a similar issue to this, either using a creative audigy LS sound card or not.

it just seems like a really specific and unique kind of problem so I thought I would start a new thread about it, I've done a search and couldn't seem to locate anything like this.

thanks in advance for any help! i would be doing more of my own research on this but schoolwork calls!

---

### Post by rustutzman on 2008-05-02
In most of the sound apps in Ubuntu you can choose the output device or service. It's usually under the preferences. Have you tried different ones? Are none of them working? When you run tests using the Multimedia Systems Selector under System/Preferences do you get any output?

Russ

---

### Post by phlancelot on 2008-05-02
thanks for the speedy reply Russ

and yes I forgot to mention about my tinkerings with the sound output devices

it seems that of the various options I am given for the tests I can get sound to happen when I select the following:

I could not get a screenshot of the drop down box options so I will list them:
Autodetect
Intel ICH5 - IEC958
Intel ICH5
CA0106
[B]CA0106
CA0106
CA0106[/B]
**ALSA - Advanced Linux Sound Architecture**
ESD - Enlightened Sound Daemon
**OSS - Open Sound System**
PulseAudio Sound Server

the ones i have highlighted in bold give me a beep when i click test

the bottom three entries called "CA0106" all seem to work, the second one called "CA0106" in the list gives me a continuous beep coming from the left side of my speaker set up (I have 5.1 speakers) the next one down gives me sound coming from the right hand side, and the final one gives me sound coming from a more central locality.

the entry called "ALSA - Advanced Linux Sound Architecture" gives me a real strong loud beep

and finally the "OSS - Open Sound System" also gives me this beep but it sounds kind of like theres an extraneous clicking noise happening in the background

when I select any of the other options and hit test I do not hear any sound

I am a little confused about the bottom part of this window which lists the Default Mixer Tracks... I'm guessing that this area is more for control of the various sound channels but again I'm a bit lost as to how this applies to solving my troubles

I've also played around with some of the preferences in VLC and Amarok, attempting to change the audio outputs but I seem to have no luck so far...

[IMG][[IMG]http://img297.imageshack.us/img297/4802/screenshot2fo9.th.png[/IMG]](http://img297.imageshack.us/my.php?image=screenshot2fo9.png)[/IMG]

hope that gives you a bit more to work with for troubleshooting.

once again thanks so much for you time. its greatly appreciated

---

### Post by phlancelot on 2008-05-18
Hey so I think I've somewhat figured this out. 

Russ was very correct on suggesting exploring which output plug-ins my various programs were using. I sometimes had to do a lot of tinkering to find out how to activate ALSA as my output plug in but I've now managed to get Amarok, Songbird, Zsnes, VLC media player all working well with sound. 

Of course there are some limitations... there doesnt seem to be support for the 5.1 stereo surround that my speakers are capable of... but overall the sound quality is quite good and comparable to how it was on windows... though im not too huge of an audiophile. 

I've also noticed that on rare occasions when I boot up ubuntu my sound does not work at all... no matter what program im using and no matter what output plug-in.... for example as im writing this post... id say it happens about 10% of the time i boot ubuntu and i honestly have no clue as to what could be causing this.... it is a minor annoyance which tends to go away if i reboot (which doesnt take long for ubuntu)  still would be nice to get some final closure on why the heck its doing this....

so yea, if you are struggling with getting ubuntu sound to work and you have a creative audigy LS sound card like i do, please dont hesitate to PM me or reply here and i can try to help you more specifically using what little experience i have had tinkering with my setup to get things (mostly) working

cheers!

---

