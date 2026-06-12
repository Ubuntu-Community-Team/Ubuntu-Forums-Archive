---
title: "Configuring GStreamer &amp; ALSA"
date: 2013-01-07
forum: Multimedia Software
---

### Post by Iggy64 on 2013-01-07
I am attempting to migrate my music player from WinXP to Linux (Bodhi or Lubuntu).   Under WinXP, I typically run a player like MusicBee (BASS libraries) through ASIO to my card.  MusicBee will accept certain plugins, such as Izotope Ozone, for processing of the sound.

I am trying to comprehend the possibilities in Linux.  It looks like I will have a player, then GStreamer (in most cases), and then ALSA.  PulseAudio keeps popping up in discussions, but I just don't see where that fits in yet.  

It looks like most of the players don't have their own plugins for things like noise sharpening (for example).  I get the sense that such things must be done in GStreamer, which is starting to look like a "plugin layer" between the player and ALSA.  Then ALSA acts as the driver for the card.  Then I see that there are plugins for ALSA, too; but these seem more device oriented than audio stream oriented.

Using the example of a noise sharpener, what is the appropriate way to introduce such a capability into the player --- GStreamer --- ALSA system?  Is GStreamer the place where added audio control is applied (equalizers, filters, sharpeners, reverb)?  If so, where is a good tutorial on how to do so?  If not, what is the right path?

Many thanks for any advice.  I have read quite a bit about the various aspects of Linux audio, but I haven't discovered a good overview that ties it together, and shows me how to put it to use in playing my music.

---

### Post by aromo on 2013-01-07
Perhaps you are looking for [JACK]("http://jackaudio.org").

Have you read on [Mixxx]("http://mixxx.org")?

:guitar::guitar:

---

### Post by Iggy64 on 2013-01-07
Perhaps --- but I just don't know.  Therein lies my problem.  I'm trying to find a nice overview of the whole sequence from frontend player to soundcard input.  It seems more complex in Linux than in Windows, possibly because there are more options available.  Since I am just a user and not a computer expert), I am a bit overwhelmed in trying to grasp:

- GStreamer: what does it do, and how can it be tweaked?
- ALSA: what does it do, and how can it be tweaked?
- PulseAudio: what exactly is this, and how does it relate to the above two items?
- JACK: likewise, how does this fit into the sequence?

Even after reading until my eyes are tired, I don't have a good picture how all this fits together.  Literature I have read calls GStreamer a "framework."  Other literature calls ALSA a "framework."  Yet they both seem to be used together.  I did find one diagram that tried to relate these elements to one another, but it had arrows pointing back and forth in every which direction.  I simply could not grasp the overall idea.

It almost seems like:

In GNOME, a player requires a backend like GStreamer before it can send audio to ALSA.  In WinXP, I think I have MusicBee sending audio via ASIO to my sound card.  In Linux, I wonder if I have [Guayadeque + GStreamer] taking the place of MusicBee, and ALSA taking the place of ASIO.  Of course, even if that were true, it doesn't explain where PulseAudio fits in, or JACK.

I'm hoping to find a higher-level "Linux music playing for dummies" tutorial that shows how the pieces fit together, and what each piece is responsible for doing.  So far, I feel like I am going around in circles.  I want to learn if I can set up a decent player using a frontend + GStreamer + ALSA; or if I need other elements like PulseAudio or JACK.  I want to learn what tweaking can be done, if any, in GStreamer and ALSA.

Pity the newb.

---

### Post by Iggy64 on 2013-01-08
So, I'm still hunting for a big-picture view on how Linux audio all fits together.

I have come across one helpful discussion on TuxRadar:

[http://tuxradar.com/content/how-it-works-linux-audio-explained](http://tuxradar.com/content/how-it-works-linux-audio-explained)

This article in itself was pretty helpful for me.  However, one of the reader's responses was particularly useful.  Unfortunately titled "This article is crap," the response really simplified what the original writer had said, and allowed me to get a better idea of how everything fits together.  It suggests, as I suspected, that GStreamer is a layer that allows the insertion of codec plugins, and it confirms that PulseAudio is mainly needed if I am trying to control the mixing of multiple audio streams (which I am not).  JACK seems only needed if you are creating music (as opposed to playing it).  So, if I am interested in playing a single stream of compressed audio files, I need: a player, GStreamer, and ALSA (the hardware driver).

Perhaps this is oversimplified, but it gives me a better starting-point picture.

Now I have to figure out what configuring of GStreamer and ALSA is available.

---

### Post by Yellow Pasque on 2013-01-08
You don't need gstreamer. I use Audacious, which sends output to ALSA directly (using ALSA's libasound).

Unfortunately, there's no easy way of controlling gstreamer in a lot of apps (though some like clementine allow you to create your own pipeline). It used to be done through gconf, but I have no idea how it's done nowadays (dconf?). If it helps, I have the gstreamer noise sharpening plugin (and bauer stereophonic headphone plugin) already packaged in my PPA: [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)

---

### Post by Iggy64 on 2013-01-09
Thanks for the info, Temujin.

So Audacious has its own built-in plugin structure, and performs whatever processing GStreamer would do.  I've read good things about Audacious.  The only downside for me would be the lack of a music library.  I suppose I could use something like Ex Falso to organize a library and make playlists, then play them in Audacious.  It would be great if I could drag and drop tracks from Ex Falso into Audacious, but I'll bet that won't work.  I'm going to set up a separate box for experimenting, and include Audacious as one route to try.

Meanwhile, I'll keep learning what I can about how GStreamer works.  I guess some front-end apps provide ways to access the GStreamer plugins, while others don't.  Still wondering whether the GStreamer plugins can be used when not implemented in the front-end player.  I have to explore gstreamer-properties, to see what that can do.

---

### Post by Yellow Pasque on 2013-01-09
Try this:
```
sudo add-apt-repository ppa:dtl131/ppa
sudo apt-get update
sudo apt-get install gstreamer0.10-tools gstreamer0.10-delta gstreamer0.10-bs2b dconf-tools
dconf-editor
```

See the screenshot for the keys to change. You'll probably want to tweak the music-audiosink as that's what rhythmbox and other players use (though some like totem use the regular audiosink). If you wanted to use the noise sharpening plugin, you would make the key:
```
delta gain=120 ! alsasink
```
If you wanted to use the Bauer stereophonic and noise sharpening, it would be:
```
delta gain=120 ! crossfeed preset=1 ! alsasink
```
For information on the plugins and their parameters:
```
gst-inspect-0.10 <plugin>
```

---

### Post by Iggy64 on 2013-01-09
So are you saying that I can run these plugins from the Terminal, if I know the correct commands?  And then any sound that I play through GStreamer will be processed by those plugins?  That would be excellent!  Not as convenient as setting them from within the audio player itself, but that's OK.

And if I choose a player like Audacious, that doesn't use GStreamer, I can use Audacious's native plugins, right?

And most GNOME players do use GStreamer, and most don't provide direct access to the GStreamer plugins, so I will have to get at them through the Terminal?

While I could probably look up (or figure out) how to run the plugins through the Terminal, is there perhaps also a GUI for configuring GStreamer?

Many thanks for helping me learn this.  It seems a bit more complicated than my experiences in Windows.  But I really want to get switched completely over to Linux.

---

### Post by Yellow Pasque on 2013-01-10
> **Iggy64 said:**
> So are you saying that I can run these plugins from the Terminal, if I know the correct commands?  And then any sound that I play through GStreamer will be processed by those plugins? 
Yes. The commands are given above.

> And if I choose a player like Audacious, that doesn't use GStreamer, I can use Audacious's native plugins, right?
Correct.

> And most GNOME players do use GStreamer, and most don't provide direct access to the GStreamer plugins, so I will have to get at them through the Terminal?

The commands are given above. You only have to do it once.

> While I could probably look up (or figure out) how to run the plugins through the Terminal, is there perhaps also a GUI for configuring GStreamer?

dconf-editor is a GUI (albeit not very beginner-friendly).

---

### Post by Iggy64 on 2013-01-10
Many thanks to Temüjin for your continuing support.  I think I am just beginning to finally see how things fit together.  I have installed the commands you suggested and will begin experimenting.  I'm sure I'll be back with more questions, but I'll try to learn as much as I can on my own.

Again, much obliged.

---

### Post by Iggy64 on 2013-04-04
Well, I tried adding the ppa as suggested:
sudo add-apt-repository ppa:dtl131/ppa

But when I do
sudo apt-get update
I get:

E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/dtl131-ppa-precise.list
E: The list of sources could not be read.

Does this mean something is corrupted in the ppa?

---

### Post by Iggy64 on 2013-04-16
I have been successful in creating GStreamer pipelines in dconf-editor, as suggested by Temujin.  I have been working with Tom Silagyi's TAP plugins.  

I would really like to try out the delta noise-sharpening plugin Temujin created, but I am at a loss as to how to obtain/download/install it.  I added his repository (ppa:decatf/testy), but I don't know how to now acquire the plugin.  I tried 

sudo apt-get install gstreamer0.10-delta

but found there is no such package. I went into Synaptic, reloaded the repos (so that I could see if the decatf/testy source was available), and got this message from Synaptic:

Failed to fetch [http://ppa.launchpad.net/decatf/testy/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/decatf/testy/ubuntu/dists/precise/main/source/Sources)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/decatf/testy/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/decatf/testy/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
Some index files failed to download. They have been ignored, or old ones used instead.

I hope someone can guide me on how to download/acquire the actual delta plugin, and where (what folder) it should be stored to be available to GStreamer.  (The TAP plugins are all in /usr/lib/ladspa.)

I'm guessing the answers are simple, but not simple enough for this noob.

Thanks, in advance, for continuing support from this forum.

---

### Post by Yellow Pasque on 2013-04-17
I did not write the plugins. I simply started packaging them in my audiohacks PPA for newer Ubuntu releases because the author (decatf) did not keep up with newer releases in his PPA. I have not yet packaged them for Ubuntu 13.04/Raring, but I will today after coffee kicks in.

---

### Post by Iggy64 on 2013-04-17
It's very kind of you to hang in there with me.  I'm still very new to Linux, to package installation, to plugins, and certainly to GStreamer.

From what I see at 
[https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)

I can use:

sudo add-apt-repository ppa:dtl131/ppa
sudo apt-get update
sudo apt-get install gstreamer0.10-delta

Is that the right method?  I am assuming that a plugin package installs the same way a regular application package installs.

Then I would have to search to see where the plugin actually ends up in the File System.

While I still have your attention (if you haven't already dozed off), I'm wondering about the Clementine package you show on your launchpad page.  It it something different from the package I would get from the Ubuntu repo?  Is it suitable only for Quantal?  (I think I'm still on Precise, although I'll have to wait till I'm home this evening to check.  It's been a while.)  I've been experimenting with my first couple of music players (Aqualung and Audacious), and was thinking about trying a GStreamer player like Clementine.  That's why I ask.

Again, I very much appreciate your making time to help me.

---

### Post by Iggy64 on 2013-04-17
Well, I've gotten a little farther -- maybe.  Or maybe I've simply gotten farther lost.  I did the 

sudo add-apt-repository ppa:dtl131/ppa
sudo apt-get update
sudo apt-get install gstreamer0.10-delta

as I suggested earlier, and found a few related log files as well as

/var/cache/apt/archives/gstreamer0.10-delta_0.1.1-2~audiohacks0_i386.deb

So I guessed (again, I have only the slighteb.st beginner knowledge of Linux) that I now needed to depackage this .deb file.  So I did

sudo dpkg -i /var/cache/apt/archives/gstreamer0.10-delta_0.1.1-2~audiohacks0_i386.deb

Although this appeared to execute OK, Catfish did not reveal any new gstreamer0.10-delta.so anywhere in my file system. So, I either failed to install the plugin, or I don't know how to find it.

Any guidance will be appreciated.

---

### Post by Yellow Pasque on 2013-04-17
```
dpkg-query -L gstreamer0.10-delta
```

---

### Post by Iggy64 on 2013-04-17
Ah, thank you once again.  Another excellent command to learn.

It showed me that that plugin was at

/usr/lib/gstreamer-0.10/libgstdelta.so


I look forward to experimenting with this plugin using dconf-editor, as you suggested.

---

### Post by JohnOShock on 2013-05-08
yes, Audacious is good, very good as far as dealing with the output, but the absence of a coherent librarian is a huge min-point for this software. Pity, otherwise I would use it. Guayadeque and Clementine are far better at this.

> **Iggy64 said:**
> Thanks for the info, Temujin.

So Audacious has its own built-in plugin structure, and performs whatever processing GStreamer would do.  I've read good things about Audacious.  The only downside for me would be the lack of a music library.  I suppose I could use something like Ex Falso to organize a library and make playlists, then play them in Audacious.  It would be great if I could drag and drop tracks from Ex Falso into Audacious, but I'll bet that won't work.  I'm going to set up a separate box for experimenting, and include Audacious as one route to try.

Meanwhile, I'll keep learning what I can about how GStreamer works.  I guess some front-end apps provide ways to access the GStreamer plugins, while others don't.  Still wondering whether the GStreamer plugins can be used when not implemented in the front-end player.  I have to explore gstreamer-properties, to see what that can do.

---

### Post by Iggy64 on 2013-07-01
Yes, JohnOShock, I have been using Audacious as my player when I don't have any exploring to do.  I can tailor the sound to each of my rooms, and do some special processing on very old recordings (40s and 50s) to brighten them up.  But Audacious lacks not only a library function, but also artist and song info -- which are things I need when I'm wading through hundreds of new tracks, trying to discover new artists.

The only app I found that does all these things well (including the sound output) was MusicBee (in Windows).  Yeah, foobar is great, and some others are great; but for my own personal needs, MusicBee was virtually perfect.  Alas, it doesn't run well at all under WINE.

Clementine is the closest thing to MusicBee under Linux.  It lacks mainly in the output configuration.  It provides no direct access to the plugin capabilities of GStreamer, which is a pity.  So I've been trying to configure GStreamer directly, using dconf-editor.  However, most of the plugins I have tried fail to actually function.  They do not show up as running processes or open files.  I've not given up yet, but I am pretty darned frustrated.  I may be missing some simple step.

---

