---
title: "Video Editing, Animation, etc"
date: 2006-07-20
forum: Multimedia &amp; Video
---

### Post by dolson on 2006-07-20
A popular topic that really does have a place on UbuntuStudio.com is the topic of video editing and creation through animation.

I added a preliminary page with just some application names.

I am very unexperienced with video and animation, so feel free to improve, expand, and share.

Hopefully we can get some of the missing apps packaged for Edgy too, but I have very little time these days.

If you happen to have a workflow that works for you for video editing, please share it! It seems a bit of a sore spot for Linux, even more so than using it as an audio studio. But efforts are underway to fix it, like the Diva and PiTiVi apps.

Anyhow, yeah.

---

### Post by capsid on 2006-08-31
hi there.  I work with some folks who do animation, and we have been trying to create a professional quality workflow with linux programs for a few months now.  In windows-land, we like ToonBoom for 2d vector animation and Maya for 3d, and shake for compositing.

Luckily, Shake & maya work on linux.  Unluckily, it's not exactly free software. :biggrin:   

On the free software side, Synfig is a unique approach to 2d vector anime.  It's built around an idea that's like tweens from Flash, but on some crazy steroids.  We haven't worked that much with it, though.  

Blender is the obvious choice if you want to do 3d animation in Linux.  It is incredibly mature and well-documented.  

I just did a search trying to find a Shake replacement, and came up with Cinelerra.  Don't know anything else about it. 

As for video editors, I'm sure there are a slew of them.  Kino is the only one I can think of offf the top of my head.  I also saw a scripting language for processing video that could be a really powerful addition to someone's workflow, but the name is escaping me at the moment.  

Just trying to add to the thread;)

EDIT

[http://en.wikipedia.org/wiki/AviSynth](http://en.wikipedia.org/wiki/AviSynth) 
AviSynth is that scripting language, but it looks like it's for Windows, even tho it's GPL.  ReactOS maybe?

---

### Post by zettberlin on 2006-08-31
I got cinelerra and made some experiments with it yet i do not know that much about video-editing to judge it well.

So i asked a friend who studies filmmaking at the college of film-arts in Potsdam Babelsberg and he was quite amazed. He´s used to work with pro-apps on MacOS and told me, that cinelerra is level with those in all the really important features one needs to edit movies. On a real fast machine cinelerra allows several videotracks parallel with thumbnails and as many audiotracks as you wish. So to cut a music-video or a band-doku for the screen it seams to be absolutely sufficient.

Unfortunately cinelerra does not work with jack. It is excluslivly adapted to alsa, so one has to change the session (that is: closing all jack-apps) to cut a movie.

---

### Post by norwyn on 2006-09-03
How did you manage to install Cinelerra?

---

### Post by zettberlin on 2006-09-03
There is a small repository with cinelerra on Ubuntu, get the HOWTO here:

[http://www.kiberpipa.org/~gandalf/ubuntu/README](http://www.kiberpipa.org/~gandalf/ubuntu/README)

for latest infos you should also read:

[http://www.kiberpipa.org/~gandalf/blog/?cat=11](http://www.kiberpipa.org/~gandalf/blog/?cat=11)

---

### Post by P_Badger on 2006-10-16
I've been going through pretty much all the (linux) video editors I can get my hands on, and the best I've found is Mainactor 5.5. It costs about 200 bux, but is the best and least buggiest video editor I've found for linux.

Blender is pretty top-notch as far as free 3D animation proggies go.

Haven't tried shake, yet. Hope there's a demo out there for it.

---

### Post by capsid on 2006-10-18
The first time I posted on this thread was a couple of months ago.  Since then I've been experimenting with some linux video programs.  I'm never gonna complain about free software unless I've written it, but setting up a good workflow has been harder than I thought.  

Here are some problems I've run into:

I've only ever used Adobe Premiere for editing.  Something I liked so much about it, something similar to the audio apps I used to use like Reason and Cool Edit, was that you actually had a workspace, as in SPACE.  You drag a clip into the space, you can drag it out of the way, you can slice it into individual frames and reorder them.  A lot of linux editors seem like windows movie maker style where each clip/cut is given a thumbnail in sequence.  Looking at you workspace, you can't tell the difference between a cut that is a single frame and a clip that is an hour long.  Please tell me if there is an editor that makes it easy to do this slicing/rearranging of individual frames in a speedy and intuitive manner.  

Unrecognizeable file formats.  Since I like to mash-up any footage I can find, I'm a little dismayed that I have problems loading files into different editors.  Sometimes it's like "well this only loads the sound correctly in Lives so I guess I'll use LiVES."  Is the standard for linux video editors to outsource playback to a media player in order to get the best codec support?  If so is there a K-Lite Codec Pack equivalent for linux systems?  I had some success by running 
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse w32codecs
```
then apt-getting mplayer and having the editors use mplayer for playback, but I don't know how to configure that in all the different editors.  

LiVES seems like the most fun, but it seems to have the workspace problem I mentioned above, plus it is butt-ugly, plus it loads my avi's REALLY slowly.  

So then I spent some time looking for free editors on windows, but only found avid-free edition and zwei-stein, neither of which struck me.  I love editing and I love trying out new programs but there is just something about every video editor that makes me want to puke.  Where is the Mario Paint of video editors?

At the very least, it would be nice to have video editing capabilities in a scripting language that would forego all the ugly, cluttered attempts at GUIs.   I mentioned avisynth in my first post, but the wikipedia list I saw it on said it's windows only, and the site is down right now.

sigh....

---

### Post by MetalMusicAddict on 2006-10-18
Keep an eye out here: [http://ubuntustudio.org/](http://ubuntustudio.org/)

---

### Post by capsid on 2006-10-18
whooooooooooa, when did the site get so pimped out??? OWWW OWWW

---

### Post by MetalMusicAddict on 2006-10-18
Stay tuned. :) Thats just a splash page for now but its kinda the look we're going for with the new Ubuntu Studio (an actual distro now). Follow the link to the WIKI to see what its all about.

---

### Post by tubunu on 2006-10-21
I'd love to see a how to on cinelerra. I had it installed once or twice but could never figure out how to load a video file in it. That's why I gave up hope on it. The howto on cinelerra site is hopeless, IMO.

---

### Post by zettberlin on 2006-10-21
> **tubunu said:**
>  could never figure out how to load a video file in it. 

The standardbranch of cinelerra is very very picky about fileformats, i guess it can record from DV plus it can load its own flavour of uncompressed quicktime.
I suggest you install cinelerraCV:

[http://www.kiberpipa.org/~gandalf/ubuntu/README](http://www.kiberpipa.org/~gandalf/ubuntu/README)

it works just great on Dapper and it loads most of the common filetypes (mpeg, avi etc). Once you loeded a file into it, you get a videotrack with thumbnails plus common audiotrack/s with waveforms. Audio is blended if you have 2 files loaded parallel, video is played allways from the upmost track and switches to those below if the above track/s is/are empty.

It took me 2-3 houres to play with it until i managed to cut a little movie consisting of half a dozen clips and apply a soundtrack.
BTW: i had some trouble with the audiotracks of some avi-files. Workaround can be made with avidemux: load the file in question, choose "Vidoecodec Copy" and audio pcm plus normalize as effect....

good luck ;-)

---

### Post by tubunu on 2006-10-22
Hey, thanks! :)

---

### Post by uuwatti on 2006-12-07
Sorry to resurrect an old thread, but I just found out about UbuntuStudio. Great work. I'm shamelessly promoting my own discoveries and letting you know  that I've searched all over the internet for all sorts video, graphics and animation tools and listed them over here: [http://www.ubuntuforums.org/showthread.php?t=293798](http://www.ubuntuforums.org/showthread.php?t=293798) (I'll move the list to a proper website soon)

---

