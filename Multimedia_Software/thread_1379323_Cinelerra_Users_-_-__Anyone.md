---
title: "Cinelerra Users - - ? Anyone?"
date: 2010-01-12
forum: Multimedia Software
---

### Post by redwoodguy on 2010-01-12
I like the look and capability of this program. But, I can't get it to run well enough to even try it.  My questions: 1. How do you know which of the 7 versions to download? Are any of them stable?

2. I've tried ever audio driver and get no sound on any of them. (My sound works fine in other apps)

My system:
Karmic
Intel Q-8300, 4GB
Video: Intel GMA X4500

I can get the program installed and it opens. I load a small sample mpeg video and it renders. This is when the trouble starts: Hitting PLAY, causes jerky play, no sound, error lists, eventually it freezes. 

Any first hand knowledge would be great!

---

### Post by jimmers on 2010-01-12
It may or not be of some use to you, but read this, it may help, worth a try,
  	 	 	 	 	 	  **Ubuntu**

 **[Karmic Koala]("http://cinelerra.org/getting_cinelerra.php#karmic") | [Jaunty Jackalope]("http://cinelerra.org/getting_cinelerra.php#jaunty") | [Intrepid Ibex]("http://cinelerra.org/getting_cinelerra.php#intrepid") | [Hardy Heron]("http://cinelerra.org/getting_cinelerra.php#hardy") |  **

 [INDENT]Here are the Ubuntu packages repositories. Detailed instructions for installation can be found in the [Manual]("http://cvs.cinelerra.org/docs/split_manual_en/cinelerra_cv_manual_en_2.html#SEC24").[/INDENT] **9.10 Karmic Koala**

 [INDENT]for all x86 (full working on 32 and 64 bits), by Paolo Rampino:
deb [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-karmic main  [/INDENT] [INDENT] Installation notes:
- For your convenience you can install a package for detecting your version of Ubuntu, installing akirad repository and keeping it updated. 
Just double click on the link [http://akirad.cinelerra.org/pool/addakirad.deb](http://akirad.cinelerra.org/pool/addakirad.deb) and install it with GDebi Package Installer. 
Alternatively, use one of the following terminal commands:
wget -q [http://akirad.cinelerra.org/pool/addakirad.deb](http://akirad.cinelerra.org/pool/addakirad.deb) && sudo dpkg -i addakirad.deb && rm addakirad.deb && sudo apt-get update
or
echo deb [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-karmic main | sudo tee /etc/apt/sources.list.d/akirad.list && wget -q [http://akirad.cinelerra.org/dists/akirad.key](http://akirad.cinelerra.org/dists/akirad.key) -O- | sudo apt-key add - && sudo apt-get update
- 7 are the packages available in the akirad repository:[/INDENT] [INDENT] Comunity Version of Cinelerra  [/INDENT] [INDENT] *cinelerracv* (all computers)
*cinelerracv-gl* (best on computer with opengl2.0 shader)
*cinelerracv-smp* (best on multiprocessors computer, it allows also opengl2.0 shader)[/INDENT] [INDENT] Simeon Völkel merge between CinelerraCV2.1 and CinelerraHV4  [/INDENT] [INDENT] *cinelerrasv* (all computers)
*cinelerrasv-gl* (best on computer with opengl2.0 shader)
*cinelerrasv-smp* (best on multiprocessors computer, it allows also opengl2.0 shader)[/INDENT] [INDENT] Utility  [/INDENT] [INDENT] *cinelerra-swtc* (extra Shape Wipe Transitions)[/INDENT] [INDENT] - Ubuntu Karmic uses Pulse Audio as Sound driver. Since it comes with a PulseAudio ESD compatibility layer, Cinelerra can be set to work with PulseAudio. Simply open Cinelerra and go to *Settings->Preferences->Playback->Audio Driver*. Select *ESound* and set the following parameters:
Server: 
Port: 7007 
- These packages set shmmax to 0x7fffffff and add non-English language support for Cinelerra.
- Please, report any package bug to *akir4d at gmail dot com * [/INDENT] **9.04 Jaunty Jackalope**

 [INDENT]for all x86 (full working on 32 and 64 bits), by Paolo Rampino:
deb [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-jaunty main  [/INDENT] [INDENT] Installation notes:
- For your convenience you can install a package for detecting your version of Ubuntu, installing akirad repository and keeping it updated. 
Just double click on the link [http://akirad.cinelerra.org/pool/addakirad.deb](http://akirad.cinelerra.org/pool/addakirad.deb) and install it with GDebi Package Installer. 
Alternatively, use one of the following terminal commands:
wget -q [http://akirad.cinelerra.org/pool/addakirad.deb](http://akirad.cinelerra.org/pool/addakirad.deb) && sudo dpkg -i addakirad.deb && rm addakirad.deb && sudo apt-get update
or
echo deb [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-jaunty main | sudo tee /etc/apt/sources.list.d/akirad.list && wget -q [http://akirad.cinelerra.org/dists/akirad.key](http://akirad.cinelerra.org/dists/akirad.key) -O- | sudo apt-key add - && sudo apt-get update
- 7 are the packages available in the akirad repository:[/INDENT] [INDENT] Comunity Version of Cinelerra  [/INDENT] [INDENT] *cinelerracv* (all computers)
*cinelerracv-gl* (best on computer with opengl2.0 shader)
*cinelerracv-smp* (best on multiprocessors computer, it allows also opengl2.0 shader)[/INDENT] [INDENT] Simeon Völkel merge between CinelerraCV2.1 and CinelerraHV4  [/INDENT] [INDENT] *cinelerrasv* (all computers)
*cinelerrasv-gl* (best on computer with opengl2.0 shader)
*cinelerrasv-smp* (best on multiprocessors computer, it allows also opengl2.0 shader)[/INDENT] [INDENT] Utility  [/INDENT] [INDENT] *cinelerra-swtc* (extra Shape Wipe Transitions)[/INDENT] [INDENT] - Ubuntu Jaunty uses Pulse Audio as Sound driver. Since it comes with a PulseAudio ESD compatibility layer, Cinelerra can be set to work with PulseAudio. Simply open Cinelerra and go to *Settings->Preferences->Playback->Audio Driver*. Select *ESound* and set the following parameters:
Server: 
Port: 7007 
- These packages set shmmax to 0x7fffffff and add non-English language support for Cinelerra.
- Please, report any package bug to *akir4d at gmail dot com * [/INDENT] **8.10 Intrepid Ibex**

 [INDENT]for all x86 (full working on 32 and 64 bits), by Paolo Rampino:
deb [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-intrepid main  [/INDENT] [INDENT] Installation notes:
- For your convenience you can install a package for detecting your version of Ubuntu, installing akirad repository and keeping it updated. 
Just double click on the link [http://akirad.cinelerra.org/pool/addakirad.deb](http://akirad.cinelerra.org/pool/addakirad.deb) and install it with GDebi Package Installer. 
Alternatively, use one of the following terminal commands:
wget -q [http://akirad.cinelerra.org/pool/addakirad.deb](http://akirad.cinelerra.org/pool/addakirad.deb) && sudo dpkg -i addakirad.deb && rm addakirad.deb && sudo apt-get update
or
echo deb [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-intrepid main | sudo tee /etc/apt/sources.list.d/akirad.list && wget -q [http://akirad.cinelerra.org/dists/akirad.key](http://akirad.cinelerra.org/dists/akirad.key) -O- | sudo apt-key add - && sudo apt-get update
- 7 are the packages available in the akirad repository:[/INDENT] [INDENT] Comunity Version of Cinelerra  [/INDENT] [INDENT] *cinelerracv* (all computers)
*cinelerracv-gl* (best on computer with opengl2.0 shader)
*cinelerracv-smp* (best on multiprocessors computer, it allows also opengl2.0 shader)[/INDENT] [INDENT] Simeon Völkel merge between CinelerraCV2.1 and CinelerraHV4  [/INDENT] [INDENT] *cinelerrasv* (all computers)
*cinelerrasv-gl* (best on computer with opengl2.0 shader)
*cinelerrasv-smp* (best on multiprocessors computer, it allows also opengl2.0 shader)[/INDENT] [INDENT] Utility  [/INDENT] [INDENT] *cinelerra-swtc* (extra Shape Wipe Transitions)[/INDENT] [INDENT] - Ubuntu Intrepid uses Pulse Audio as Sound driver. Since it comes with a PulseAudio ESD compatibility layer, Cinelerra can be set to work with PulseAudio. Simply open Cinelerra and go to *Settings->Preferences->Playback->Audio Driver*. Select *ESound* and set the following parameters:
Server: 
Port: 7007 
- These packages set shmmax to 0x7fffffff and add non-English language support for Cinelerra.
- Please, report any package bug to *akir4d at gmail dot com*  [/INDENT] **8.04 Hardy Heron**

 [INDENT]for all x86 (full working on 32 and 64 bits), by Paolo Rampino:
deb [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-hardy main  [/INDENT] [INDENT] Installation notes:
- For your convenience you can install a package for detecting your version of Ubuntu, installing akirad repository and keeping it updated. 
Just double click on the link [http://akirad.cinelerra.org/pool/addakirad.deb](http://akirad.cinelerra.org/pool/addakirad.deb) and install it with GDebi Package Installer. 
Alternatively, use the following terminal command:
wget -c [http://akirad.cinelerra.org/pool/addakirad.deb](http://akirad.cinelerra.org/pool/addakirad.deb) && sudo dpkg -i addakirad.deb
- To update the repository information press *Reload* in Synaptic Package Manager (Adept for Kubuntu) or use the following terminal command: 
sudo apt-get update
- 7 are the packages available in the akirad repository:[/INDENT] [INDENT] Comunity Version of Cinelerra  [/INDENT] [INDENT] *cinelerracv* (all computers)
*cinelerracv-gl* (best on computer with opengl2.0 shader)
*cinelerracv-smp* (best on multiprocessors computer, it allows also opengl2.0 shader)[/INDENT] [INDENT] Simeon Völkel merge between CinelerraCV2.1 and CinelerraHV4  [/INDENT] [INDENT] *cinelerrasv* (all computers)
*cinelerrasv-gl* (best on computer with opengl2.0 shader)
*cinelerrasv-smp* (best on multiprocessors computer, it allows also opengl2.0 shader)[/INDENT] [INDENT] Utility  [/INDENT] [INDENT] *cinelerra-swtc* (extra Shape Wipe Transitions)[/INDENT] [INDENT] - Ubuntu Hardy moved to Pulse Audio Sound driver. Since it comes with a PulseAudio ESD compatibility layer, Cinelerra can be set to work with PulseAudio. Simply open Cinelerra and go to *Settings->Preferences->Playback->Audio Driver*. Select *ESound* and set the following parameters:
Server: 
Port: 7007 
- These packages set shmmax to 0x7fffffff and add non-English language support for Cinelerra.
- Please, report any package bug to *akir4d at gmail dot com*  [/INDENT] [INDENT]for i386 (not working on amd 32 bits), by Valentina Messeri:
deb [http://giss.tv/~vale/ubuntu32/hardy](http://giss.tv/~vale/ubuntu32/hardy) ./[/INDENT]

---

### Post by redwoodguy on 2010-01-12
Thanks Jimmers. I did read that before and sadly I found it pretty much uninformative. I tried several of the releases with no luck. They all did about the same thing. 

In addition to all those different releases there are mountains and mountains of configuration options after installing. So far it feels more like a programmers test bed than an application for end users.

---

### Post by wildhostile on 2010-01-13
> **redwoodguy said:**
>  . 

Hi redwoodguy,

Cinelerra doesn't read all format/codecs. You will have to test what is the best one to use with your workflow. What is the format(videocodec, audiocodec) made by your camcorder?

You can ameliorate cinelerra's behavior with some of these hints:
- In Settings -> Preferences -> Playback : uncheck "play every frame"
- In Settings -> Preferences -> Performance : choose a larger cache size (maybe 100MB)
- Try to change audio device to see if it doesn't have influence on playback.
- Try to play videos with lesser bitrate
- If your video card support opengl 2.0, I suggest you to compile the source from cinelerra.org with ./configure --enable-opengl .

You can get help:
- with the docs: [http://cinelerra.org/docs.php](http://cinelerra.org/docs.php)
- on the mailing list : [http://cinelerra.org/mailinglists.php](http://cinelerra.org/mailinglists.php)
- on irc channel on freenode.net

---

### Post by redwoodguy on 2010-01-13
Thanks wild for the info. I was just using a standard little MP4 file for testing. 

I had spend time reading their documentation and manual, which is primarily about how to compile various versions and so on. Although it looks interesting, it's not for me. I was looking for an actual end user application. Something finished, something that is already debugged and working. I don't have weeks of time to learn how to compile a big application like that and worse, I don't have any interest in "building my car from a box of parts" sort of thing. I'm just trying to make a movie. I'll keep looking.

---

### Post by redwoodguy on 2010-01-13
I solved the problem I think. 

I downloaded and installed "OpenShot" a somewhat new video editor and it is beautiful. It installs simply as you expect it should, it works perfectly when launched and it has a nice suite of transitions and effects and a very VERY easy GUI. 

I have only done a very quick tests with a few short files, but it looks rock stable, and slick as snot. For anyone wanting to do video production for YouTube or DVDs this looks like a real winner. 

[http://www.openshotvideo.com/](http://www.openshotvideo.com/)

---

### Post by a2z on 2010-02-13
> **redwoodguy said:**
> I solved the problem I think. 

I downloaded and installed "OpenShot" a somewhat new video editor and it is beautiful. It installs simply as you expect it should, it works perfectly when launched and it has a nice suite of transitions and effects and a very VERY easy GUI. 

I have only done a very quick tests with a few short files, but it looks rock stable, and slick as snot. For anyone wanting to do video production for YouTube or DVDs this looks like a real winner. 

[http://www.openshotvideo.com/](http://www.openshotvideo.com/)

I have cinelerra. Runs perfectly. If a carpenter can use it, You can too!! only mine didn't come in a box:( 
Popcorn?:popcorn:

---

