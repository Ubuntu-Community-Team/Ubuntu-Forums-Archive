---
title: "Can't install Mplayer for Firefox"
date: 2009-07-11
forum: Multimedia Software
---

### Post by Green9090 on 2009-07-11
If I try to stream MIDI from Firefox, I get a message telling me I need additional plugins, and it offers to install Mplayer. Upon asking it to do so, I get this error message:
"Can not install 'mozilla-mplayer' (E:Unable to correct problems, you have held broken packages.)"

So then I go to the package manager and find the Mplayer-Mozilla package. Upon asking it to mark for installation it gives me a list of other things to be marked, and when I accept that it says:
"Could not mark all packages for installation or upgrade

The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.
Mozilla-mplayer:
 Depends: mplayer (>= 1.0~pre5) or
  mplayer-nogui but it is not going to be installed"

This is all completely unfamiliar territory for me; I haven't the foggiest clue what these warnings are telling me. Could anyone shed any light on this problem please?

---

### Post by Green9090 on 2009-07-11
I would really appreciate any sort of response that helps me understand the problem at all, regardless of whether you are sure how to fix it. Thanks :)

---

### Post by Green9090 on 2009-07-11
Nobody's had this before? :(

---

### Post by kerry_s on 2009-07-11
try **gecko-mediaplayer** instead. just use synaptic to install it, make sure you click reload first, so it has a fresh list of whats there.
it still uses mplayer, but it use's the new gnome-mplayer which is much better.

---

### Post by Green9090 on 2009-07-11
Got the error message 
"Gecko-mediaplayer
Depends: gnome-mplayer but it is not going to be installed"

---

### Post by kerry_s on 2009-07-11
> **Green9090 said:**
> Got the error message 
"Gecko-mediaplayer
Depends: gnome-mplayer but it is not going to be installed"

i see the problem, i missed it the first time.

> 
"Can not install 'mozilla-mplayer' (E:Unable to correct problems, you have held broken packages.)"


so you need to run this in a terminal:

**sudo apt-get -f install**

to fix the broken stuff.

---

### Post by Green9090 on 2009-07-11
The response from that command was 
"Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 22 not upgraded."

Still get the same old error messages trying to install the plugins. =\

---

### Post by kerry_s on 2009-07-11
do-> 
[B]sudo apt-get update 
sudo apt-get upgrade[/B]

that should upgrade those 22 things.
then try and installing the gecko-mediaplayer using synaptic, not the command line, use the gui, it will give you more detail on problems.

---

### Post by Green9090 on 2009-07-12
> **Green9090 said:**
> Got the error message 
"Gecko-mediaplayer
Depends: gnome-mplayer but it is not going to be installed"

This still happens :(

---

### Post by 6205 on 2009-07-12
IMO i don't use lame mplayer anymore, simply because there are much better optimized alternatives for ubuntu, like default Totem Gstreamer player with default totem-mozilla plugin. But it's also necessary to install aditional gstreamer plugins with their depecies.

gstreamer-plugins-bad
gstreamer-plugins-bad-multiverse
gstreamer-plugins-ugly
gstreamer-plugins-ugly-multiverse
gstreamer-plugins-ffmpeg

This is the most comfortable and clean solution to any streaming media in firefox.

Also i have installed VLC media player as my default player for any video files and DVD's

I strongly suggest you to unistall all mplayer related packages, clean your system with 'sudo apt-get autoremove' command from terminal and install only default totem-gstreamer + totem-mozilla plugin + all those aditional gstreamer plugins..

---

### Post by Green9090 on 2009-07-12
I'm sorry if I missed it in your post, but what then should I install in order to stream MIDI from online? I have all of the packages beginning with gstreamer in Synaptic already. 

By the way, sudo apt-get autoremove doesn't do anything, as my system is not recognizing any broken packages.

---

### Post by kerry_s on 2009-07-12
> **6205 said:**
> IMO i don't use lame mplayer anymore, simply because there are much better optimized alternatives for ubuntu, like default Totem Gstreamer player with default totem-mozilla plugin. But it's also necessary to install aditional gstreamer plugins with their depecies.

gstreamer-plugins-bad
gstreamer-plugins-bad-multiverse
gstreamer-plugins-ugly
gstreamer-plugins-ugly-multiverse
gstreamer-plugins-ffmpeg

This is the most comfortable and clean solution to any streaming media in firefox.

Also i have installed VLC media player as my default player for any video files and DVD's

I strongly suggest you to unistall all mplayer related packages, clean your system with 'sudo apt-get autoremove' command from terminal and install only default totem-gstreamer + totem-mozilla plugin + all those aditional gstreamer plugins..


totem-gstreamer sucks! totem-xine would be better, if you wanted to go with totem.

anyway's i don't think it matters, i suspect the package manager is broken.

> 
Quote:
Originally Posted by Green9090 View Post
Got the error message
"Gecko-mediaplayer
Depends: gnome-mplayer but it is not going to be installed"
This still happens 


what version of ubuntu are you using?
are you using synaptic?

---

### Post by Green9090 on 2009-07-12
Ubuntu 8.04, and yes, I'm using Synaptic. 

I also suspect the package manager is broken, how can I go about fixing that? Is it possible that just formatting and reinstalling from scratch would fix it?

---

### Post by Struki on 2009-07-12
> **6205 said:**
> IMO i don't use lame mplayer anymore, simply because there are much better optimized alternatives for ubuntu, like default Totem Gstreamer player with default totem-mozilla plugin. But it's also necessary to install aditional gstreamer plugins with their depecies.

gstreamer-plugins-bad
gstreamer-plugins-bad-multiverse
gstreamer-plugins-ugly
gstreamer-plugins-ugly-multiverse
gstreamer-plugins-ffmpeg

This is the most comfortable and clean solution to any streaming media in firefox.

Also i have installed VLC media player as my default player for any video files and DVD's

I strongly suggest you to unistall all mplayer related packages, clean your system with 'sudo apt-get autoremove' command from terminal and install only default totem-gstreamer + totem-mozilla plugin + all those aditional gstreamer plugins..

Ok I see that your post is suposed to help me, but I forgot to point out that I'm a total noob/rookie in linux, so i don't understant your help so good:

Basicly: 
What is mplayer(plugin?) and where do i find it?(to remove it I supose?)
How do I install all those plugins/packages(complete commands)
How do I use the autoremove command corectly?

Im sory if thats a list of stupid questions for you, but I got to start learning from somewhere, cause i really like linux so far, and I would like it to stick...
thnx anyway

---

### Post by kerry_s on 2009-07-12
open synaptic
click status> installed
click on the right side
start typing mplayer, it will find as you type.
right click> mark for complete removal 

here's a pic, yours won't be like mine, i'm using debian.

---

### Post by Green9090 on 2009-07-13
> **kerry_s said:**
> open synaptic
click status> installed
click on the right side
start typing mplayer, it will find as you type.
right click> mark for complete removal 

here's a pic, yours won't be like mine, i'm using debian.

There's no mplayer package installed.

---

### Post by 6205 on 2009-07-13
Ohh...crap...i'm not sure where to start :(

1./ Let's make sure that you don't have any broken depencies. If you open Synaptic package manager on the left side you have something like 'missing or broken depecies' If there's nothing broken OR synaptic doesn't start due some error, try to put into terminal 'sudo apt-get install -f' what should fix those broken/missing depencies(if any)

2./ From this point, let's asume that your system is OK and nothing is broken, so make sure that you have also enabled 'Medibuntu' repository. Click on System > Administration > Software sources and click on second tab, where you should have Medibundu listed like on picture. If you have Medibuntu, everything is OK. If not, please add it following this guide
[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories)

3./ OK :) now if you have(or had before) Medibuntu, let's try to install some gstreamer codecs through Synaptic, like on second picture. Of course, confirm also installation of all requested depencies.

4./ Check also Totem packages like on next pic..

5./ Don't tell me that it did not helped :) or give us a link to that webpage with that MIDI file..


PS: i cannot recommend totem-xine or mplayer. i have bad experiences with them and those gstreamer plugins simply work better on latest ubuntu... btw. what version of Ubuntu are you running? i asume that 9.04 - 32bit

---

### Post by Green9090 on 2009-07-13
Huh. So, I did all of that, and as a result I was for some reason able to install the Gecko mediaplayer plugin thing. Now Firefox THINKS that it is playing the midi file, but there's no sound. I am not sure if that is an improvement or not. 

This: [http://www.wholenote.com/default.asp?iTarget=http%3A//www.wholenote.com/basics/et.asp](http://www.wholenote.com/default.asp?iTarget=http%3A//www.wholenote.com/basics/et.asp) is what I am trying to do. 

Thank you for your help, that is the first thing that caused any progress.

---

### Post by Green9090 on 2009-07-14
I'm sorry, but does anyone else have any clue what the problem might be? :(

---

### Post by Green9090 on 2009-07-15
Dang, might just have to use my Windows partition for this. I was trying to keep it offline for obvious reasons :P

---

