---
title: "Brasero"
date: 2014-08-30
forum: Multimedia Software
---

### Post by teresa4 on 2014-08-30
I am trying to download a free version of Brasero and i keep getting an error message stating "need root password."  I'm running Kubuntu.  Kind of new at  this. Downloading software is a much different process than with Windows.  I don't recall ever setting up a root password.  I set up an administrator PW and that doesn't work.

Also another question regarding burning audio CDs created with Audacity.  Can you save to a .wav file using Linux so that the CD can be played back on a car or other CD player that can read CDRs or CDRWs?:guitar:

---

### Post by ajgreeny on 2014-08-30
> **teresa4 said:**
> I am trying to download a free version of Brasero and i keep getting an error message stating "need root password."  I'm running Kubuntu.  Kind of new at  this. Downloading software is a much different process than with Windows.  I don't recall ever setting up a root password.  I set up an administrator PW and that doesn't work.

Also another question regarding burning audio CDs created with Audacity.  Can you save to a .wav file using Linux so that the CD can be played back on a car or other CD player that can read CDRs or CDRWs?:guitar:
To install brasero (or any applications or packages from the repositories) you need to open the Kubuntu software-centre (no idea what that is in Kubuntu) search for brasero and install it.  You do not "download" the applications and install them as you do in windows; it is all done by the system's package manager.

You can also use the command line by opening a terminal, konsole in Kubuntu, and run the command ```
sudo apt-get install brasero
``` When asked, enter your admin user password exactly as you typed it at installation time, as Linux is case sensitive, and even though it will not show as you type it, just hit enter.
However, why do you want brasero? Kubuntu already has k3b which is often thought to be much better than brasero for disk burning.  I even install it in whatever version of *ubuntu I run, Xubuntu at the moment, as I prefer it to to the alternatives.

As for your query about burning an audio CD, you do not need to worry about the file type, or using audacity at all.  Audacity is an audio file editor; it does not and can not burn a CD; all it can do is change an audio file type, but there is no need to do that.  The disk burning application, whether brasero or k3b, will burn any audio file to an audio CD as long as you have all the codecs needed to decode and encode the audio files.  This allows you to burn mp3, m4a, flac, wav, or any other files to a standard playable CD.

---

### Post by speartip on 2014-09-01
You don't need Brasero. K3B is the default burning software in Kubuntu & IMO is far superior to Brasero anyway.
To burn Audio CDs just open up k3b and click "New Audio CD Project" locate the files you want to add to your compilation & click burn.
You may also want to install kubuntu-restricted-extras, cdrdao, sox & transcode. This will give you nearly all the codecs you will need.
Don't search the internet for them though, use Muon Package Manager which is already pre-installed.

---

