---
title: "Mp3 encoding"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by ratbagradio on 2007-04-21
I have just upgraded from Dapper to Feisty. But before then I had no luck in installing an accessible Mp3 encoder to use with Audacity -- the audio edit prorgam I'm familair with and have installed.

After reviewing the forums, it appears tha*t libmp3lame.so* and Audacity in Dapper may not get on and other forum members  were turning to other platforms to handle their Mp3 conversion.

I downloaded and installed Jokosher without success --so I don't know where I should now proceed. I don;tw ant to create the problem I did before in trying to set up Lame on my desktop or fathom the DIY with gstreamer.

All I ask of Ubuntu is the ability to export media in an Mp3 format. And I want to install that capacity while being considerate of my limited skill with Unbuntu (as I've only been on it for just over three weeks).

So I gather that I need to first expand my software sources by adding repositories to my package list. ...

IF I can only get a walk through on this issue I can ther4eafter go solo on Ubuntu. If not I'm back editing my audio on Windows. I don;t mind if I have to edit in Audacity =and convert in another program. Just so long as I can do that AND edit my tags.

I also wonder if/when  the Ubuntu Studio "solves" these issues when it is released. (this month?)

---

### Post by jocheem67 on 2007-04-21
Well, what's your question exactly?
You wanna encode your own projects? Or cd's? Or just some songs?

Her's some possibilities:

soundjuicer is the native cd to other format converter. Has some issues though. Better is grip, uses lame and cdparanoia for ripping.
I'm using abcde : a command-line encoder, there's a thread around on the forum.

A universal converter is soundconverter, haven't used it myself.

There's a lot of possibilities in linux regarding sound. You could also try eac using wine ( eac being the best ripper available )...

But maybe I don't understand your question correctly...

---

### Post by ratbagradio on 2007-04-21
I record on either Mp3 format (on an iRiver ) or on Sony's format for Hi MD which I then can convert (but not on Linux) through Sonic Stage to a choice of a few other formats.

I'm OK with that. Thats' routine for me.

Audacity will of course handle a range of options. But when I've finished the editing and importing I cannot export to Mp3 because I cannot merge Audacity's requirements with what I can install on Dapper, Edgy (and maybe Feisty). (There seems to ba a problem with the lame file required by Audacity compared to the lame file on offer in these releases)So I'm stuck.

So IF I want to edit I'm happy to do that in Audacity and saving to Wav but ALSO  use Soundconverter or SoundKonverter(another to Mp3 transfer option) to format and create my mp3 files. But how do I install these things because everytime I try, I start mucking up my desktop. Obviously I am doing it wrong.

I can download SoundKonverter or SoundConverter from their homepage but I cannot "run" it. But I can also tweak a few files & dependencies  through package management and I can do the line entering game in Terminal. But obviously I simply do not understand the way to proceed as, to me, it is not self evident no matter how many searches I do and the reading I log. And this is proven by the fact that I haven't been able to install and make this setup work, despite my attempts.

So here's my situation:

> I'm on Feisty, fresh out of the wrapper.
Everything works fine-- including my preferred player, Amarok, and my podcast catcher, iPodder/Juice. I've downloaded and opened Lame but really who knows if it can be put to work.(I've used Lame as a standard when I ws on Windows XP so I am a little familiar with it).

I need to install a universal converter.So what do I now do, step by little step because every other attempt I've tried has ended in disaster. 

So I really don;t care what I use as long as it worksand I can in the end edit and convert on Ubuntu. 

[As for Sonic Stage -- I'll m,anulally transfer files to the  Ubuntu computer or ;later look at a system of networking. SonicStage only thsi year attained Mac useability and there seems no way to incorporate this later and more stable version on Linux although I keep cjhecking back with the mini disc community). Maybe later I should shift to Edirol or some of these other recorders (although I like the MD format)-- but for now my problem is different)

---

### Post by jocheem67 on 2007-04-22
Okay, I did a little test with "soundconverter", ripped a song to flac from a cd with soundjuicer and converted it to mp3 with soundconverter...no problems here. It uses gstreamer.

Some notes: gstreamer is a set of libraries that you need to use with a lot of gnome audio converting programs. They're not in the repositories ( not all ) that are activated by default.
Please go to this site:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Here's explained how to use the more not so legal ( at least in the states ) ways to convert audio from one format to another. With illegal I just mean patent-issues, no harm done here..

Adding repositories is quite simple:

[http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories](http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories)
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

This is a site that explains all kind of linux extensions and how to deal with them.
You can also just check behind the help-icon in ubuntu...there's also some repository stuff explained......

Don't use the binaries from the sites of the makers of the little proggies you're aiming at. Always try to use synaptic 'cause it's way more safe to do so and won't mess things up.

The lame-binary which you're trying to use is used by my favorite "abcde" , but again : you need a fully operational gstreamer-framework...check on "restricted formats"...

Hope this was your issue...otherwise let us know!

Cheers!

By the way, I don't think that liniux in general can handle the sony audio and video-formats...these are very restrictive and as such shouldn't be used at all. This company ( just like microsoft ) tries to force the computerusers into their reach by using only formats that you need their software for to work with ( crappy english )...
Mp3 is also not that open ( it's patented ) but it is the standard nowadays and as you know used by the whole world. That alone makes it more acceptable / democratic....)

---

