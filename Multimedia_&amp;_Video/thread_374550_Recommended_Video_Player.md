---
title: "Recommended Video Player"
date: 2007-03-02
forum: Multimedia &amp; Video
---

### Post by NautTboy on 2007-03-02
Man, I'm really getting into this Linux Os.  The more I learn the more i want to know.

Ok I believed my DVDROM is mounted because once I put in the Audio CD it(Sound Juicer) started to play.  With a title that doesn't even associate with the music, this I can live with.

The video player that installed with Ubuntu is Movie Player.  Once insert VCD\SVCD\DVD Move Player pop-up with error message picture attached.

Anyone has a good suggestion how to correct this problem or a better player please help one newbie out.  I can't wait to go to the next step.

---

### Post by fearevilleet on 2007-03-02
I would use VLC to play media. VLC will pretty much play all media & dvds.

---

### Post by invalid on 2007-03-02
I would try using a different player, such as VLC.

---

### Post by floke on 2007-03-02
I can triple vouch for this - was searching all over for codecs etc. - but VLC has come to the rescue. If you are running beryl also then you will have problems - you need to set it to use the video output for X11 - just do a quick google for 'VLC beryl' and it will pull up the forum threads on it.

---

### Post by RomeReactor on 2007-03-02
Hi. Is Totem using Gstreamer? Try installing Totem-Xine and give it another try: Open a terminal (Applications-->Accessories-->Terminal) and type

```
sudo apt-get install totem-xine libxine1 libxine-extracodecs
```

Then try opening the disc again.

---

### Post by hppyfngy on 2007-03-02
> **RomeReactor said:**
> Hi. Is Totem using Gstreamer? Try installing Totem-Xine and give it another try: Open a terminal (Applications-->Accessories-->Terminal) and type

```
sudo apt-get install totem-xine libxine1 libxine-extracodecs
```

Then try opening the disc again.

I have a new Edgy install and using totem-xine and the lib that you suggest above but I have no sound out of my mplayer from dvd or avi.

I do still have full audio from amarok and all the "tests" in the System/Pref/Sound settings work fine...

Any suggestions?

---

### Post by RomeReactor on 2007-03-02
Hi hppyfngy. Open Mplayer, go to "Preferences-->Codecs & demuxer" and on the "Audio codec family" tab select **FFmpeg/libavcodec audio decoders**; close Mplayer, open it again and see if sound now works.

---

### Post by hppyfngy on 2007-03-02
Okay, just installed VLC package and have sound, but still opening in Totem.  How do we change file associations?

Also, I'm using my plantronics 500 headset as my audio device and the inline volume controller operates the gui's volume control, (i.e. the little volume bar shows up and moves,) but it doesn't effect the volume coming out of my headset..

Any Ideas?:confused:

---

### Post by hppyfngy on 2007-03-02
> **RomeReactor said:**
> Hi hppyfngy. Open Mplayer, go to "Preferences-->Codecs & demuxer" and on the "Audio codec family" tab select **FFmpeg/libavcodec audio decoders**; close Mplayer, open it again and see if sound now works.

When I open mplayer, my preferences has no Codec tab, just "General", "Display", and "Audio".  

We are talking about Totem, right?

---

### Post by NautTboy on 2007-03-03
> **RomeReactor said:**
> Hi. Is Totem using Gstreamer? Try installing Totem-Xine and give it another try: Open a terminal (Applications-->Accessories-->Terminal) and type
```
sudo apt-get install totem-xine libxine1 libxine-extracodecs
```
Then try opening the disc again.

Thanks for the advice but it didnt work. First pic is from VCD and the second is from DVD after it played the intro.  I'll give another try before I go with the other suggestion for VLC.

---

### Post by NautTboy on 2007-03-03
Ok, I'd also downloaded VLC universal movie player.  Other than download and install it, do i have to do anything else other than run it?  Because when I run it, it just came up without a screen.  I even went in to choose DVD, nothing.  Another capture.  Is this how it suppose to look?

---

### Post by Prometheus.172214 on 2007-03-03
Not sure if someone has posted this, but here is a suggestion for VLC and DVD CSS.

Use the following repository, with universe checked, for graphic installation: 

[ftp://ftp.videolan.org/pub/videolan/ubuntu](ftp://ftp.videolan.org/pub/videolan/ubuntu)

Search and install vlc vlc-plugin-esd mozilla-plugin-vlc and libdvdcss2 

Or add to your /etc/apt/sources.list: 

deb [ftp://ftp.videolan.org/pub/videolan/ubuntu](ftp://ftp.videolan.org/pub/videolan/ubuntu) dapper universe

And run 

 % sudo apt-get update
 % sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc libdvdcss2

From what I have seen, VLC seems to play most multimedia content and has not shown any DVD CSS error on my system. I am not sure on how to check if there is a DVD Region setting for the optical drive in Linux, however if the drive is set to the wrong DVD Region, this can happen.



The image you posted shows the VLC Media Player GUI. Try navigating to your optical drive and opening a *.vob file with VLC.  If the default player for *.vob is a different media player, navigate to the optical drive and view the contents. Then right click on a *.vob file and in the properties, set the default media player for this type of video file as VLC layer, from the list. Then try playing the*.vob file in VLC and check. I have heard some good reviews about Xine also, but I have never tried it. VLC seems to be working fine for me.

---

### Post by NautTboy on 2007-03-03
Sorry the code didn't work. Xine, i tried that too.

---

### Post by NautTboy on 2007-03-04
Ok, I'd install all the player listed under Sound and Video.  I have DVDROM and DVDRW.  I guess the DVDROM DVD lazer is going bad.

KMPlayer will play** both** miniDVD(CDR) and VCD on DVDROM only, does not recognize DVDRW.

Totem Movie Player will play **ONLY** miniDVD(CDR) and intro of DVD(not actual Move(encrypted))  

I need help on either or:

Get my Totem to Play VCD and Main Movie(encrypted)
or
Get my KMplayer to recognize, read from my DVDRW drive.

I know there's gotta be someone out there that knows very well.

---

### Post by doobydave on 2007-03-04
Pretty much everything that you could possibly want to do with ubuntu is included in this :-

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

Note there are separate pages for breezy and dapper. Windowz could learn a lot....

---

### Post by freeflyer57 on 2007-03-04
Totem requires a lot of work to get it up-and-running. Try Xine or VLC.

---

### Post by panch0 on 2007-03-05
I recommend KPlayer for playing all the different kinds of disks. It lists the available disk devices, and when you insert a disk it also autodetects that and shows the available tracks (or titles for a DVD). In the multimedia library you can also set different kinds of properties on the devices, disks, and tracks. Playback is also excellent, the aspect ratio is always detected correctly, unlike in Xine based players. KPlayer uses MPlayer behind the scenes.

---

### Post by NautTboy on 2007-03-06
Ok, it seems like different play work well for different users.  I'd just install ALL available under add/remove and nothing seems to work.  As i mention earlier, one will work with one and the other will work with the other media and player.  I'd reinstall Ubuntu and none seems to work.  i will skip this for now.

---

### Post by panch0 on 2007-03-07
KPlayer is not in Ubuntu repositories right now. Try the package listed on kde-apps.org or linked from the [KPlayer home page]("http://kplayer.sourceforge.net/"). That is the player that works best for me.

---

