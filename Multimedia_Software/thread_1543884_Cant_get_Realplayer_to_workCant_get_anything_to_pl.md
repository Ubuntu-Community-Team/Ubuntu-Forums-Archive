---
title: "Cant get Realplayer to work/Cant get anything to play RA or WM lossless"
date: 2010-08-01
forum: Multimedia Software
---

### Post by typos1 on 2010-08-01
Despite trying to enable Ubuntu to play any Real media file or WM lossless, several times over the past year, I still cant get it to play them in ANY media player I ve got installed on my system. 

I m sure I followed advice (it was months ago now) and enable something in software sources (have enabled uni and multiverse) .

So I tried installing Realplayer but it wont play anything-it opens then closes again straight away. I ve played around with the settings and got it to "work" by going into tools/preferences/hardware and changing it from OSS to ALSA. I put works in inverted commas cos it plays but I get no sound. After rebooting it then did the same thing with ALSA so I changed it to OSS and it played without sound. In sound preferences under applications it doesnt mention Realplayer, just ALSA which ever way I do it. 

I ve tried changing the output in sound prefernces, but no config allows me to hear anything-sound works fine with everything else. 

I m running a 64bit system and I ve made sure I ve got libdvdccs2 and re added medibuntu after updating to Lucid. Realplayer doesnt make any sound and nothing plays WM lossless or any Realmedia stuff. Help!!

---

### Post by ron999 on 2010-08-01
Hi
Do you mean that you want to play a ra file that you've got on your hard drive?

---

### Post by typos1 on 2010-08-01
Yeah, but it would be nice to be able get Realplayer to play anything!...that I can hear

---

### Post by ron999 on 2010-08-01
Don't mess around with RealPlayer.
Use **VLC media player** instead. It will play ra files.

---

### Post by typos1 on 2010-08-01
No, GnomeMplayer wont play em, nor will Movieplayer, nor will VLC, nor will Realplayer, as I said in the first post-nothing plays em or WM lossless!

---

### Post by luigi_mb on 2010-08-01
> **typos1 said:**
> No, GnomeMplayer wont play em, nor will Movieplayer, nor will VLC, nor will Realplayer, as I said in the first post-nothing plays em or WM lossless!

Try this:

```

ffmpeg -i file.ra file.mp3

```

(replacing "file.ra" with the actual filename). Then use VLC or whatever you use to play .mp3 files. I just tried it, successfully, on an old .ra file that, as you point out, wouldn't play at all.

As you see, I did not use any switches, so the result may not be optimal. 


/luigi

---

### Post by andrew.46 on 2010-08-02
Hi typos1,

If you have a spare 20 minutes you could try  guide I have just written:

Howto: Build the svn MPlayer under the latest release version of Ubuntu
[http://ubuntuforums.org/showthread.php?t=1542240](http://ubuntuforums.org/showthread.php?t=1542240)

which enables playback of both of these formats although at this stage wma lossless will play under *32 bit* ubuntu only. If it is any consolation there is a move from FFmpeg to [reverse engineer wma lossless]("http://wiki.multimedia.cx/index.php?title=FFmpeg_Summer_Of_Code_2010#WMA_lossless") as part of the Google Summer of Code 2010.

Andrew

---

### Post by typos1 on 2010-08-02
Ah, thanks Iandrew.46, ll try it. 

I ve been told in the past to that it can be done and added some "libs", but it never worked, although others said it had for them. Before I upgraded to Lucid, I did have SMplayer, but it still didnt play them and after the upgrade it disappeared. And with Karmic I had installed W32 and W64 codecs and I think it was with Jaunty that I used a 32 bit build on a  64 bit system.

luigi_mb just tried that but it says "no such file or directory".

Anyone know why I cant hear Realplayer? I does play .ra and WM lossless, just cant hear it. 

I want to convert them back to WAVs but winff wont do it-I think for the same reason that nothing will play them-ie no codec.

---

### Post by typos1 on 2010-08-02
Andrew.46-I added smplayer as per your thread...it wont play .ra s...argh!

ron999, since installing smplayer as per andrew.46's suggestion, VLC now gives a message saying it cant play .wmal files (got no message before), then bizarrely it "plays" them-but with the same prob as realplayer-ie there is no sound.

---

### Post by mc4man on 2010-08-02
Atm the only way you're getting wmal on 64 bit is with a 32 bit player with w32codecs or as you've attempted, realplayer.

Because I dumping this install (lucid), went ahead and installed realplayer.
It definitely can play wmal and ra/rm, though it's behavior is inconsistent.

Would always crash on alsa, but did work on oss here, have now gotten to work with alsa.
Also sometimes a r.click open with fails, sometimes drag and drop fails, the file menu was fairly consistent.

Try opening rp, go help - player reset, then open rp up and go thru the setup stuff. I'd set oss from the very start and see.

Maybe also try something other than wmal first to see if you get any audio 

For alsa I set the device to the hw - hw:0 here - see screen

Edit:
> VLC now gives a message saying it cant play .wmal files (got no message before), then bizarrely it "plays" them-but with the same prob as realplayer-ie there is no sound.

Not really 'the same problem' - vlc can't decode wmal unless it is a 32 bit version and is built with the config. option of --enable-loader, it's just playing the video

---

### Post by typos1 on 2010-08-02
Tried all that you say-no luck-it thinks its playing but I get no sound-tried a .wav and .wmal and.ra.

Whenever I go to sound preferences when its running it says that no app is playing sound.

I suppose I should try and install 32 bit VLC and or SMplayer to be able to play wmal or ra?

Is it jsut a case of adding the 32codecs in a terminal?

Or is there anyway of giving winFF the FFmpeg codecs so I can convert wmal and ra to wav?

---

### Post by mc4man on 2010-08-02
> Or is there anyway of giving winFF the FFmpeg codecs so I can convert wmal and ra to wav? 
.ra probably yes. wmal no (ffmpeg doesn't support

> Whenever I go to sound preferences when its running it says that no app is playing sound.
To be expected - rp only uses alsa or oss - not pulseaudio

> I suppose I should try and install 32 bit VLC and or SMplayer to be able to play wmal or ra?

Won't help - vlc would have to be built, you need a 32 bit mplayer, smplayer is just a frontend, the 64 bit version is fine.

> Is it jsut a case of adding the 32codecs in a terminal?
Not really - as mentioned you need mplayer (32bit), first - then the codecs (w32) in a place it can find.

Some options
install a 32 bit mplayer - never tried myself - maybe getlibs can help
build and install 32 bit mplayer - a little work - [basic method here]("http://ubuntuforums.org/showthread.php?p=9338517") 

Install a win version of mplayer in wine and play or use with the wine command prompt to extract to wave - works fine - window's cli is a bit different

Install some other player in wine to play and or convert.

Use a livecd (32 bit) to extract or convert with mplayer and transfer

Get realplayer going - it does work..

---

### Post by goseven on 2010-08-02
I had the same problem with Realplayer.
Don't know if you have 2 soundcards but this worked for me.

I followed the directions in this posting for blacklisting my
motherboard sound card and then Realplayer (from real.com/realplayer/linux) played audio fine.

[http://ubuntuforums.org/showthread.php?t=629391](http://ubuntuforums.org/showthread.php?t=629391)

I had this issue with Ambulant SMIL player in Ubuntu 8.04.
Audio would work in all other players except Ambulant.

Good luck,

---

### Post by Barely Here on 2011-01-28
I had a similar problem with Realplayer, in that the player would open then close stright away. It was installed in a fresh install of xubuntu 10.04 no less.

However I picked up on the tips, and changed the sound output to OSS. I'm pleased it works... short of. I'm still dealing with the shuttering problem when I'm playing radio, but it might be the streaming server's problem.

---

