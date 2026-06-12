---
title: "Which app to stream audio from audio input?"
date: 2007-11-30
forum: Multimedia &amp; Video
---

### Post by jnoreiko on 2007-11-30
Can anybody suggest how to best stream audio, as mp3, from an audio input?
This is for a radio station's webstream, connecting to an icecast server.

I've installed darkice, and it has no mp3 support. Same problem with MuSE.

---

### Post by MrClearPore on 2007-11-30
I use Audacity for my Web streaming.  It works wonderfully when I stream from BBC.  I set Audacity to Capture and it will capture pretty much anything from any source.  It can save the stream in WAV or MP3 formats.  You can get Audacity from the Adept installer.

---

### Post by eye208 on 2007-11-30
> **jnoreiko said:**
> I've installed darkice, and it has no mp3 support. Same problem with MuSE.
What about IceS? [http://www.icecast.org/ices.php](http://www.icecast.org/ices.php)

---

### Post by jnoreiko on 2007-11-30
> **MrClearPore said:**
> I use Audacity for my Web streaming.  It works wonderfully when I stream from BBC.  I set Audacity to Capture and it will capture pretty much anything from any source.  It can save the stream in WAV or MP3 formats.  You can get Audacity from the Adept installer.

I know about recoding a stream with Audacity -- it's ace -- but you can use Audacity to create a stream?
I'm talking about *sending* a web stream out to the internet from the studio of a radio station.

---

### Post by jnoreiko on 2007-11-30
> **eye208 said:**
> What about IceS? [http://www.icecast.org/ices.php](http://www.icecast.org/ices.php)

I see ices2 in the ubuntu package listl but not ices0 which is the mp3 version.
I have to stream in mp3 as most people will be on Windows and won't want to bother downloading plugins or other apps.

---

### Post by eye208 on 2007-11-30
> **jnoreiko said:**
> I see ices2 in the ubuntu package listl but not ices0 which is the mp3 version.
I have to stream in mp3 as most people will be on Windows and won't want to bother downloading plugins or other apps.
It should not be too difficult to compile ices0 from source as it does not have many dependencies. You will probably need the following packages installed on your system before you begin:

build-essential
libshout3-dev
liblame-dev

Download the ices0 source package, extract it somewhere in your home folder, cd into the extracted folder and then run the following commands:

./configure
make
sudo make install

The first line will run a configuration script which checks dependencies and then writes out a makefile. The second line will execute that makefile and compile the program from its sources. **The third line is optional.** It will copy the generated executable file(s) into the system folder structure (usually /usr/local/...). **You don't have to install the program in order to use it.** It will run just fine from your home folder as well, so there is no risk to break anything if you omit the final step.

Just try it. If you run into error messages during the configure or make stages, post the output here so we can help you out.

---

### Post by jnoreiko on 2007-12-02
Thanks for the advice... compiling wasn't actually that painful :D
Though I couldn't find where the compiled program was put after 'make'. The final step gave a few weird errors, but I've got ices0 in my path and it runs.

However, I can't find any documentation on how to configure ices0 to stream from line input.

I've got MuSE working (this thread: [http://ubuntuforums.org/showthread.php?p=3877332](http://ubuntuforums.org/showthread.php?p=3877332)) and I'll see how I get on with that.

---

### Post by TekNullOG on 2007-12-04
I suggest IDJC (available in Add/Remove in Ubuntu). It is the most user friendly of them all and trust me, I do a lot of music streaming. The GUI is great and simple to configure. You might have to install the encoders though.

Tell me how you like it

No matter what you do, don't try BroadWave. It is not available threw the package manager. Once installed, it is very invasive. I am still trying to figure out how to remove it! It almost seems like a spyware or something like that...

P.L.U.R.

---

