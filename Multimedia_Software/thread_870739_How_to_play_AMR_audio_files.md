---
title: "How to play AMR audio files"
date: 2008-07-26
forum: Multimedia Software
---

### Post by tdn on 2008-07-26
I have a lot of AMR audio files that my mobile phone (Sony Ericsson K810i) creates. I would like to be able to play these files in Ubuntu. 

I once saw a patch for ffmpeg that enabled support for AMR, but it was rather complicated to get working properly.

Is there a better way of playing AMR audio in Ubuntu?

I would like to be able to convert the AMR files to FLAC, OGG or some other open format. Preferably a lossless one, so FLAC would be best.

---

### Post by shirilover on 2008-07-26
You might try installing libamrnb and libamrwb.
Converting these files to FLAC will just give you a lossless representation of the previous lossy audio files.

---

### Post by bpny on 2008-07-26
Realplayer for Linux will play AMR files.

---

### Post by tdn on 2008-07-27
> **shirilover said:**
> You might try installing libamrnb and libamrwb.


I do  not have those packages.
Which sources do I need to add in order to get them?

When I have these libs installed, whould mpg321, amarok and so on be able to play AMR-files?

How do you recommend that I convert them to FLAC?


> **shirilover said:**
> 
Converting these files to FLAC will just give you a lossless representation of the previous lossy audio files.

I am aware that AMR is lossy, but since the AMR files are the *original recordings*, then there does not exist any more data than there is in the AMRs. So I would like to be able to keep as much information as possible from these recordings. Hence the FLAC codec.

---

### Post by shirilover on 2008-07-27
Those packages are available in the Medibuntu repos in the non-free section -> [http://www.medibuntu.org/](http://www.medibuntu.org/)

If amarok is using the xine engine, it should use libxine1-ffmpeg, libxine1-plugins and libxine1-misc-plugins which 'should' play these files.

As for converting, you could try -> [http://media-convert.com/](http://media-convert.com/)

---

### Post by tdn on 2008-07-27
> **shirilover said:**
> Those packages are available in the Medibuntu repos in the non-free section -> [http://www.medibuntu.org/](http://www.medibuntu.org/)

If amarok is using the xine engine, it should use libxine1-ffmpeg, libxine1-plugins and libxine1-misc-plugins which 'should' play these files.

As for converting, you could try -> [http://media-convert.com/](http://media-convert.com/)

Well, I have installed the lib packages you mention for Amarok. But Amarok will not play the AMR files. When I drag them to the playlist it says "some media could not be loaded(not playable)".

---

### Post by galileon on 2008-12-06
> **bpny said:**
> Realplayer for Linux will play AMR files.

thank you :)

---

### Post by tdn on 2008-12-06
I would like to be able to convert the AMR files to FLAC, OGG or some other open format.

Is this possible?
How?

---

### Post by FakeOutdoorsman on 2008-12-06
[size=5]Update: This post is now outdated[/size] because as andrew.46 notes, "FFmpeg has dropped support for the non-free amr libraries in favour of opencore-amr".  See his [opencore-amr](http://ubuntuforums.org/showpost.php?p=7584660&postcount=409) post for more info.

> **tdn said:**
> I would like to be able to convert the AMR files to FLAC, OGG or some other open format.

Is this possible?
How?
You can use ffmpeg.  If you're using Ubuntu Hardy you can use ffmpeg from the [Medibuntu repository]("http://medibuntu.org/").  I believe it has support to decode AMR.

If you're using Ubuntu Intrepid you will have to compile ffmpeg yourself:
[HOWTO: Compile the latest ffmpeg and x264 from source]("http://ubuntuforums.org/showthread.php?t=786095")

If you follow that guide, you will need some additional steps to use AMR.  First download the amr development packages from the Medibuntu repository:
```
sudo apt-get install libamrnb-dev libamrwb-dev
```
Then when you configure ffmpeg (step 5 in the guide), you will need to add additional configuration options:
```
--enable-libamr-nb --enable-libamr-wb
```
The ffmpeg command to convert to flac is relatively simple:
```
ffmpeg -i inputfile.amr outputfile.flac
```
For ogg vorbis you have several choices depending on how you configured ffmpeg:
```
ffmpeg -i inputfile.amr -acodec vorbis outputfile.ogg
```
or:
```
ffmpeg -i inputfile.amr -acodec libvorbis outputfile.ogg
```

---

### Post by wersdaluv on 2009-07-29
> **FakeOutdoorsman said:**
> [size=5]Update: This post is now outdated[/size] because as andrew.46 notes, "FFmpeg has dropped support for the non-free amr libraries in favour of opencore-amr".  See his [opencore-amr](http://ubuntuforums.org/showpost.php?p=7584660&postcount=409) post for more info.


You can use ffmpeg.  If you're using Ubuntu Hardy you can use ffmpeg from the [Medibuntu repository]("http://medibuntu.org/").  I believe it has support to decode AMR.

If you're using Ubuntu Intrepid you will have to compile ffmpeg yourself:
[HOWTO: Compile the latest ffmpeg and x264 from source]("http://ubuntuforums.org/showthread.php?t=786095")

If you follow that guide, you will need some additional steps to use AMR.  First download the amr development packages from the Medibuntu repository:
```
sudo apt-get install libamrnb-dev libamrwb-dev
```
Then when you configure ffmpeg (step 5 in the guide), you will need to add additional configuration options:
```
--enable-libamr-nb --enable-libamr-wb
```
The ffmpeg command to convert to flac is relatively simple:
```
ffmpeg -i inputfile.amr outputfile.flac
```
For ogg vorbis you have several choices depending on how you configured ffmpeg:
```
ffmpeg -i inputfile.amr -acodec vorbis outputfile.ogg
```
or:
```
ffmpeg -i inputfile.amr -acodec libvorbis outputfile.ogg
```
Thanks for the update! :)

---

### Post by Mark Rose on 2009-07-30
ffmpeg has moved to libopencore for its amr support. The command line switches have changed. You can get .debs for libopencore at [http://debian-multimedia.org/pool/main/o/opencore-amr/opencore-amr.php](http://debian-multimedia.org/pool/main/o/opencore-amr/opencore-amr.php). You need to grab all of them for your architecture.

---

### Post by andrew.46 on 2009-07-30
Hi Mark Rose,

> **Mark Rose said:**
> ffmpeg has moved to libopencore for its amr support. The command line switches have changed.

I have not tested libopencore-amr extensively but my impression so far is the commandline options themselves had not changed. Of course in FFmpeg amr encoding is now called as *-acodec libopencore_amrnb* and there is no *libopencore_amrwb* encoding. But of course I have not used libopencore-amr extensively yet and I am quite prepared to be corrected here :-).

Andrew

---

### Post by Biff Boff Kapow on 2009-08-21
Andrew... I'm lost. I would like to play some AMR files too...  Don't spend too much time on the answer... A friend put Jaunty on my computer... I think it seems like a great idea but I really don't have a clue about how to install new programs in Jaunty. Could you give me one or two basic and guiding ideas? Reading is not my forte especially having to read through so many things I know nothing about- but if you think you could give me a skeleton explanation of how to do some basic things in Linux... I would be grateful...
Thanks,
-Brian

---

### Post by andrew.46 on 2009-08-21
Hi Brian,

> **Biff Boff Kapow said:**
> Andrew... I'm lost. I would like to play some AMR files too...  

It is a pity that it is not a lot easier to do under Linux, Ubuntu is not the only distro that digs in its heels over amr... I believe the *easiest* way to get amr playback under Jaunty Jackalope is:

--------------------------

**1. Add the Medibuntu repositories.**

This is done under Jaunty by pasting the following commands into your terminal, first:

```

sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list

```

and then:

```

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

When asked if you accept a package even though it is unauthenticated type 'Yes' and this indicates that you trust Medibuntu, as I do.

**2. Install MPlayer**

Now when you install MPlayer you will be installing the Medibuntu version which has the capability of amr playback:

```
sudo apt-get install mplayer w32codecs
```

-----------------------------

The w32codec pack is not required for playback of these files but it means MPlayer will be able to play many files that use windows-only codecs. There are countless variations for this but this is the *simplest* method under Jaunty Jackalope.

I have just repeated this process on a clean install of Jaunty and tested it with the following amr file which I invite you to also download and test:

```
wget http://andrews-corner.org/samples/Rammstein_Du_Hast.3gp
```

I attach a screenshot of this file playing under Jaunty, bear in mind that amr sound is pretty bad at the best of times :-).

All the best,

Andrew

---

### Post by Biff Boff Kapow on 2009-08-21
Thanks Andrew!

Part of making linux work is supressing the excitement for having been given some instructions and then giving an accurate account of what went wrong... Okay... so it was very cool to get a response... I had your reply on my screen and when I went to fetch the terminal I covered up the first bit of code and copied the second instead. ... W32codecs is not available. I then go back and see the first code and paste it in. works. I plug the other bits in and look for Mplayer in applications and assume you mean Movie Player. Isn't able to play. Next thing I'm going to try is reloading Movie Player. I think this means that I have to go to Synaptic Package Manager and do a search for Movie Player and download it? Which... will enable the codecs you helped me with?

Thanks again for the response.
Brian

---

### Post by Biff Boff Kapow on 2009-08-21
I managed to get the files to play in the proper player... although when the connected eighth notes appear over my .amr files as I pass over them with my mouse, they don't play. too bad... it makes it a lot nicer to check the number of files I make every day collecting phone numbers and addresses. Seems the slider doesn't work either and no info on the length of the recording. I would definitely like to skip through to different parts of the file also- pretty much an essential tool for checking longer recordings of things on the radio or TV... conversations with friends etc. 

Unfortunately, I didn't manage to unmount my phone card so some of the files must have been damaged or altered- Mplayer says the stream is non-existent. 
Even when my phone has run out of batteries while recording, it still manages to save the file first so I don't think it had anything to do with my phone. I have the Sony Ericsson z710i. 
To my ears, the small speaker on the phone suits amr files though I can play them louder on the computer. Nonetheless, they sound pretty good.  

I heard that there are programs which can repair damaged amr files. I would like to find one. 

  I have put all the files on a DVD. 

A couple of questions remaining:

Why does my screen saver- the one where you fly over a plane and past some fireworks- make my system crash?  I assume it is because I only have 500 mbytes of ram?

Is there any way to make Mplayer the default player and get rid of Totem player?

Hope you had a good sleep.

Thanks

---

### Post by andrew.46 on 2009-08-21
Hi Brian,

> **Biff Boff Kapow said:**
> I managed to get the files to play in the proper player... 

Good to hear you have had some success, although I realise from the rest of your post you have a few other issues. I am no expert on phones but I believe the need or amr is slowly fading as newer phones are capable of aac playback which has a much superior sound and many are capable of utilising the mp4 container which is vastly superior to 3gp. But I guess there are still a lot of amr files floating around...

> Is there any way to make Mplayer the default player and get rid of Totem player?

The copy of MPlayer that you now have is quite capable but it is still a little old and may very well fail you in other areas. If I were you I would keep a few different players available just to be sure. And as well I am not entirely sure how to manipulate the 'default' settings for players :-).

> Hope you had a good sleep.

Indeed I slept like a log and I am now ready and prepared for my grandchildren to wreck my house all day on their visit :-).

Andrew

---

### Post by randolf_ambrose on 2009-11-27
> **andrew.46 said:**
> Hi Brian,



It is a pity that it is not a lot easier to do under Linux, Ubuntu is not the only distro that digs in its heels over amr... I believe the *easiest* way to get amr playback under Jaunty Jackalope is:

--------------------------

**1. Add the Medibuntu repositories.**

This is done under Jaunty by pasting the following commands into your terminal, first:

```

sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list

```

and then:

```

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

When asked if you accept a package even though it is unauthenticated type 'Yes' and this indicates that you trust Medibuntu, as I do.

**2. Install MPlayer**

Now when you install MPlayer you will be installing the Medibuntu version which has the capability of amr playback:

```
sudo apt-get install mplayer w32codecs
```

-----------------------------

The w32codec pack is not required for playback of these files but it means MPlayer will be able to play many files that use windows-only codecs. There are countless variations for this but this is the *simplest* method under Jaunty Jackalope.

I have just repeated this process on a clean install of Jaunty and tested it with the following amr file which I invite you to also download and test:

```
wget http://andrews-corner.org/samples/Rammstein_Du_Hast.3gp
```

I attach a screenshot of this file playing under Jaunty, bear in mind that amr sound is pretty bad at the best of times :-).

All the best,

Andrew

wow!!! ANDREW!!! man!!! this is working cool... i can play my AMR files in realplayer now...

thanks man!!!

---

### Post by andrew.46 on 2009-11-27
Hi randolf,

> **randolf_ambrose said:**
> wow!!! ANDREW!!! man!!! this is working cool... i can play my AMR files in realplayer now...

Well, I will take full credit if you mean* MPlayer*, but I suspect that RealPlayer plays amr files on its own anyway :).

All the best,

Andrew

---

### Post by karthik.velugoori on 2011-02-03
> **FakeOutdoorsman said:**
> [size=5]Update: This post is now outdated[/size] because as andrew.46 notes, "FFmpeg has dropped support for the non-free amr libraries in favour of opencore-amr".  See his [opencore-amr](http://ubuntuforums.org/showpost.php?p=7584660&postcount=409) post for more info.


You can use ffmpeg.  If you're using Ubuntu Hardy you can use ffmpeg from the [Medibuntu repository]("http://medibuntu.org/").  I believe it has support to decode AMR.

If you're using Ubuntu Intrepid you will have to compile ffmpeg yourself:
[HOWTO: Compile the latest ffmpeg and x264 from source]("http://ubuntuforums.org/showthread.php?t=786095")

If you follow that guide, you will need some additional steps to use AMR.  First download the amr development packages from the Medibuntu repository:
```
sudo apt-get install libamrnb-dev libamrwb-dev
```
Then when you configure ffmpeg (step 5 in the guide), you will need to add additional configuration options:
```
--enable-libamr-nb --enable-libamr-wb
```
The ffmpeg command to convert to flac is relatively simple:
```
ffmpeg -i inputfile.amr outputfile.flac
```
For ogg vorbis you have several choices depending on how you configured ffmpeg:
```
ffmpeg -i inputfile.amr -acodec vorbis outputfile.ogg
```
or:
```
ffmpeg -i inputfile.amr -acodec libvorbis outputfile.ogg
```

thanks FakeOutdoorsman works pretty neatly used this to install ffmpeg
it already has amr in the configure options [http://ubuntuforums.org/showpost.php?p=9114176&postcount=967](http://ubuntuforums.org/showpost.php?p=9114176&postcount=967)

---

