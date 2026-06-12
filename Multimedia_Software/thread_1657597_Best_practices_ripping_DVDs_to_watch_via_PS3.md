---
title: "Best practices: ripping DVDs to watch via PS3"
date: 2011-01-01
forum: Multimedia Software
---

### Post by HankB on 2011-01-01
Hi folks,
I have a collection of DVDs, some extra disk space and a PS3 hooked to an HD TV and 5.1 audio system. I'd like to rip my DVDs so I can watch them on the HD TV with sound going through the 5.1 audio system. I've been reading some posts about this and wonder what is likely to be the best approach.

I had a go with this some years ago and got some ripped DVDs viewed on the TV by using a DVI cable hookup from an extra video card. The results were less than stellar with color not being accurately reproduced. What was a smooth color on the original DVD turned into what looked dithered color when I tried to play the rip. But it's been a couple years and I'd like to have another go at this.

First question: Am I likely to be better off trying to display directly from the PC or should I serve files via DLNA to the PS3. From the standpoint of cabling and connections, I favor the latter. For that reason, most of my following questions relate to that approach.

Getting the rip workflow looks like a huge hurdle for me. There are a myriad of options for the transcode section. I'm pretty sure the settings I make here will be crucial to the success of my effort and I have no idea what the settings should be. It seems like the defaults are geared toward reducing the data to something that will fit on a CD and that is definitely not what I want to do. I want to preserve the original image quality and audio quality. I'm not trying to conserve space. I'm trying to provide the convenience of having my DVD collection at my fingertips. One aspect of transcoding is that I'd like to choose a format that the media server can just hand over to the PS3 to play. At some point I might want to run the server on an Atom based system and transcoding on the fly might be a bit much to expect for that.

The final aspect is how to serve the files to the PS3. I suppose one option is to put the files on the PS3 hard drive, but I'd rather take advantage of the storage on my PC. That leaves me with choosing a DLNA server. It seems the popular ones are mediatomb and PS3 media server (PMS.) I have also heard of fuppes. Are there advantages to either? One constraint is that I prefer a server that does not require a GUI. If I do serve from the aforementioned Atom based host, it will not have a display. But that is not a strong preference. If a server that requires a GUI or otherwise will not run in the background is much better, that would override the desire to serve in the background.

Feel free to point out anything I have overlooked or clearly don;t understand. Also feel free to point me toward any tutorials on this subject.

Thanks!

---

### Post by solar george on 2011-01-01
wrt. transcoding your dvd (I've no experience with media servers) unless you're interested in the details of working out your ideal options you'll probably find Handbrake's ([http://handbrake.fr/index.php](http://handbrake.fr/index.php)) presets work fine. Don't be put off by the fact that the last release was in 2009, the ppa is being updated regularly with new versions.

---

### Post by BicyclerBoy on 2011-01-01
IMHO

MythTV & XBMC will offer better picture quality & more flexibility than the PS box.

To achieve this you will need feature set C nvidia GPU & latest drivers.

The colour space issues can occur with PC monitor RGB v.s. video RGB.
SD & HD colour spaces are different.

DVI & HDMI can support YUV space.

Some displays screw up the colour space depending on connection type.

---

### Post by BicyclerBoy on 2011-01-02
MythTV  (& XBMC I think) will act as dlna server direct to the TV.

But most TVs do not have a very complete format support & are cpu limited & are designed with the minimum video processing hardware.

TVs with digital tuners (outside of US) will likely support h264 AVC (may be not perfectly) but transcoding to this very space efficient but is 1/2 real time on core2duo.

Any transcoding takes lots of time/CPU reduces PQ and introduces artefacts unless using high bitrates. So can be better to leave video in the original format.

---

### Post by HankB on 2011-01-02
Hi folks,
Thanks for the replies.

A new video card is out of the question at the moment, however an upgrade is possible in the future. I've started fiddling with dvd::rip as it seems to be the Swiss Army knife of ripping DVDs. I'm also doing some testing with acidrip and may have a go with handbrake.

My TV does not have a network connection or DLNA client. And a new TV is further away than a PC upgrade.

I'm using Media Tomb to serve video to the PS3. I figure since the PS3 does a pretty good job of playing DVD and Blu-Ray disks, it should be capable of handling streaming media as well.

I have discovered that with the correct configuration, Media Tomb can directly serve the .VOB files copied from the DVD. It is my understanding that these are more or less bit for bit copies of the content on the DVD platter. (If not hit me with a clue bat!) Therefore I'm surprised that viewing them directly produces horrid results. The interlace artifacts are pretty obvious. I'm guessing that streaming media does not get the same processing of the data read from the DVD. That leaves me wondering how I can duplicate that processing during the transcoding process.

This is where I feel like I'm over my head using dvd::rip. There are lots of choices on the transcode tab and I'm a bit at a loss to determine what's going to get me the best results other than by trial and error. Is there a discussion of these settings somewhere that goes beyond simply naming them?

The other thing I've discovered is that the disk seems to contain more .VOB files than I expected. For example s disk with four TV episodes (Southpark, first season, disk one) includes one .VOB that holds all four episodes and four .VOB files that each contain one episode. Is the data really duplicated that way on the disk? Also I'm puzzled that the DVD for LOTR Fellowship disk one has two 1:45 episodes that look the same to me. :confused: (Maybe I need to view both to see if they really are identical.)

thanks again,
hank

---

### Post by solar george on 2011-01-03
Its generally best not to muck around with the .VOBs directly, if you are being confused by dvd::rip options (and if you don't know what you are doing you'll likely end up with sub-par rips) you'd really be best off starting with the presets available in handbrake.

---

### Post by BicyclerBoy on 2011-01-03
The DVD file structure is intentionally obfuscated.

I am finding dvd::rip 0.98.11 to be a very unreliable with new DVDs..

Personally I don't want to rip DVDs at all..
You can extract DVD to ISO image & play them instead of VOBs..

MythTV 0.24 has excellent DVD playback & PQ possibly surpassed only by XBMC.
I think MythTV will play ISOs.
MythTV only plays DVDs (in the optical drive) in frontend box (without NFS)

A cheap nvidia Gt220 probably US$50 & will better any game box playback.

VOBs play on my PC with VLC look perfect (as far as DVDs go).

All interlaced material playback requires an appropriate deinterlacing filter like yadif etc
You should choose the highest quality that the CPU can support.
Nvidia vdpau does this in hardware. Feature set C is strongly recommended.

VLC does not use hardware video decode (vdpau purevideo) in default build.
Video acceleration is only video overlay not decode/scaling/denoise/sharpen.

---

