---
title: "BBC radio listen again and streams"
date: 2008-09-09
forum: Multimedia Software
---

### Post by eeried on 2008-09-09
Hello,

I used to be able to record listen again programs with mplayer. You simply needed to get the url for the stream, and then:
```
mplayer rtsp://complete_link.rm -dumpstream -dumpfile name_of_the stream.rm
```

This doesn't seem to work on BBC7.

ON BBC radio 4 they have a new player iPlayer which doesn't seem to be doing anything, unless it just needs the realplayer codecs which I haven't installed. Mplayer had always been quite enough.

It seems too that there are restrictions for non-UK residents. I can hardly believe BBC radio 4 can't be "heard" by foreigners on the Web. Strange notion of what the Web is about.

I don't want to install realplayer as I'm sure a couple of codecs from the w32codecs and Mplayer can do the trick.

Your help will be much appreciated :)

---

### Post by ingo on 2008-11-21
You worked anything out yet? I want to record some stuff from BBC3 but have hit the same wall as you.

---

### Post by eeried on 2008-11-21
I'm afraid not, ingo.

Recording used to be such a cinch.

I can listen to the "from our own correspondent" programme, and I can't even listen to a BBC*4 Listen again programme, but I don't get an error message.

There must be a way :confused:

---

### Post by ingo on 2008-11-21
When I was still on Kubuntu 8.04 I did not even have to have realplayer installed, I think mozplugger dealt with live listening. Now on 8.10 I took the shortcut via the medibuntu repo.

I then tried streamripper and kradioripper. Both are after a URL. But when I give it them (rtsp://rmv8.bbc.net.uk:554/what_have_you) they refuse to connect.

So I may not be out in the complete dry as you, but I really want to record the first four songs of this week's WorldRoutes by Lucy Duran (whatever happened to Andy Kershaw?) before it goes offline in the next few hours!!!

---

### Post by ingo on 2008-11-21
eeried - you may want to look at this site - it provides all the http URLs for rtps streams!!! [http://www.iplayerconverter.co.uk/](http://www.iplayerconverter.co.uk/)

Sadly I found it too late. The stream I was after has been taken off the server already.

Then I've found something else, haven't tried it yet, but it also seems like a good link [http://www.tomtaylor.co.uk/blog/2006/09/01/how-to-rip-bbc-radio-streams-to-mp3/](http://www.tomtaylor.co.uk/blog/2006/09/01/how-to-rip-bbc-radio-streams-to-mp3/)

---

### Post by ingo on 2008-11-21
double post...

---

### Post by eeried on 2008-11-21
quote from the iPlayer Real Converter Web site
> And now the iPlayer is taking over?

The iPlayer doesn't use RealPlayer for the audio - instead it uses encrypted MP3, and will soon use AAC (the same format as iTunes). Although this is fine for most people, it means any custom software/hardware that expects to see RealAudio won't work.
So what's the answer?

This website! Seriously, the old RealAudio is still available, so it was just a case of finding where the links are hidden and cobbling up a system to convert the new format programme IDs to RealAudio links

Nifty, eh, and clever of you to have dug out this Web site, ingo.
> encrypted MP3, and will soon use AAC (the same format as iTunes)

So is the BBC dallying with some form of DRM?

I'm sorry you missed your Andy Kershaw programme.

I don't have the chance to test the streams until Monday, but I'll have a go.

As for the mp3 converter Web site I wish it were to OGG :)

---

### Post by ingo on 2008-11-21
Quick update - I've been able to get things working with mplayer - but still no recording!!!

---

### Post by ingo on 2008-11-21
Okay, it is working!

1. enable medibuntu repo (if you haven't already done so)
2. sudo apt-get install mozilla-mplayer
3. open the show you want to record in firefox, listen to it
4. right click on the player window and select "copy URL"
5. insert the URL into the following command:

mplayer -ao pcm:file=file.wav "*insert_your_URL_here*" -dumpfile *your_programme*.wav

:guitar:
And my show was only temporarily offline - am downloading it at the mo :)

---

### Post by eeried on 2008-11-27
Hard luck for me, ingo

Could you give me an actual link that works for you?

Do you get the link from [http://www.iplayerconverter.co.uk/](http://www.iplayerconverter.co.uk/) ?

Can I convert the stream to Ogg like this?

mplayer -ao pcm:file=file.ogg "insert_your_URL_here" -dumpfile your_programme.ogg

---

### Post by ingo on 2008-11-30
Sorry eeried, been away for a couple of days.

So where exactly do you falter? You got mozilla-mplayer? Can you listen? 

Send me a pm and perhaps we can sort this quickly on skype, yahoo or icq...

---

### Post by marn on 2008-12-18
You've probably got it all sorted out by now, but for anyone else looking for a solution, as to how to record the BBC listen again streams (and they are often well worth it) I found this Howto on the Kubuntu forum useful: 

[http://kubuntuforums.net/forums/index.php?topic=3100005.0](http://kubuntuforums.net/forums/index.php?topic=3100005.0)

As far as I know, the stream can only be recorded as a wav file and then has to be converted. I personally use lame with the following command: 

```
lame -a -V2 audiofile.wav audiofile.mp3
```

The -a option converts the file to mono (fine as long as its just talking) and the -V option sets the quality of the variable bitrate (can be left out). Of course, you have to have lame installed (and also be allowed to use it...)

I also put everything into a short script (I'm no real script writer, but it works!)

```

#/bin/bash
# downloads and converts a listenagain programm from the BBC Website
# RTSP= rtsp address
# NAME= file name

echo Please enter the rtsp address of the programm you want to record
read RTSP
echo Please enter the name of the programm
read NAME
mplayer -ao pcm:file="$NAME".wav ""$RTSP"" -dumpfile "$NAME".wav
lame -a -V2 "$NAME".wav "$NAME".mp3
```

All that needs to be done ist to get the rtsp address from [http://www.iplayerconverter.co.uk/](http://www.iplayerconverter.co.uk/) and away you go

Hope this helps some of you

marn

---

### Post by ingo on 2008-12-20
Ha, it's a small world. Andy wrote that how to after some discussion here [http://kubuntuforums.net/forums/index.php?topic=11158.0](http://kubuntuforums.net/forums/index.php?topic=11158.0) - glad you found it useful, marn.

As I stated above, I don't need the iplayerconverter site 'cos I get the link straight from the iplayer itself :)

---

### Post by eeried on 2008-12-22
I don't seem to be able to listen live or again using iPlayer.

Now here's what I get, running Intrepid:

```
 mplayer -ao pcm:file=file.wav "rtsp://rmv8.bbc.net.uk:554/radio4fmcoyopa/radio_4_fm_-_friday_1530.ra?timestamp=1229702814&pid=b00fyqch&BBC-UID=3449e42f07064ed09c2fac078050458279536229501011c4046f39279df6019f_n&SSO2-UID=" -dumpfile your_programme.wav
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: mobile AMD Athlon(tm) XP-M 2200+ (Family: 6, Model: 8, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing rtsp://rmv8.bbc.net.uk:554/radio4fmcoyopa/radio_4_fm_-_friday_1530.ra?timestamp=1229702814&pid=b00fyqch&BBC-UID=3449e42f07064ed09c2fac078050458279536229501011c4046f39279df6019f_n&SSO2-UID=.
Resolving rmv8.bbc.net.uk for AF_INET6...
Couldn't resolve name for AF_INET6: rmv8.bbc.net.uk
Resolving rmv8.bbc.net.uk for AF_INET...
Connecting to server rmv8.bbc.net.uk[212.58.252.7]: 554...
librtsp: server responds: 'SOPTIONS * RTSP/1.0'
librtsp: server responds: ''
rtsp: read error.


MPlayer interrupted by signal 13 in module: open_stream
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
```

Can you try the same link?

---

### Post by ingo on 2008-12-22
Okay, I tried your command and it is working a treat. Hence your install is faulty somewhere along the line.

My gcc version:
Version: 4:4.3.1-1ubuntu2

My mplayer version:
Version: 2:1.0~rc2-0ubuntu17

---

### Post by marn on 2008-12-22
What I wondered is what the timestamp is for (I'm afraid I'm not much of an expert in these areas). It doesn't seem to be necessary, as I used the same RTSP link to download two consecutive episodes. It makes automating the download easier, as the RTSP can then be copied directly into a script, getting the script to add the date onto the wav filename, so that going to the iplayerconverter site becomes superfluous.

@eeried

your command worked fine for me as well, although I am still on hardy heron

---

### Post by DeaconBlues on 2008-12-22
Thanks for the script eeried. It worked for me on a relatively new installation of Kubuntu (just installed restricted extras today).

I also learned this from another site: Add the option "-bandwidth 9999999" to the MPlayer options string. This accelerates your download. I've just streamed a 3 hour BBC radio show to my HD in about 3 minutes. :) :) :)

---

### Post by ingo on 2008-12-22
@ eeried

If I were you I'd remove and purge mplayer and reinstall.

---

### Post by marn on 2008-12-22
Thanks DeaconBlues, that is a vast improvement. Just for the sake of completness, here is the (new) command:

```
mplayer -bandwidth 9999999 -ao pcm:file=whatever.wav "rtsp_link" -dumpfile whatever.wav
```

---

### Post by andybleaden on 2008-12-23
> **marn said:**
> Thanks DeaconBlues, that is a vast improvement. Just for the sake of completness, here is the (new) command:

```
mplayer -bandwidth 9999999 -ao pcm:file=whatever.wav "rtsp_link" -dumpfile whatever.wav
```

Glad people are getting this up and running and thanks for the positive comments for the how-to on kubuntuforums.

Please feel free to adapt as you much as you can. On one note though I read elsewhere that when you increase the bandwidth it does record faster but quality is destroyed so let us know how it sounds afterward as you may have found a way around it

---

### Post by marn on 2008-12-23
Yes, I read that as well. As far as I can tell there is no audible difference between the listen again stream and the mp3s I am creating (which means the wav file is just as good - I added a delete line to my script to save room on my HD so I can't tell). It's probably a matter of taste and the quality of the sound hardware (I've been listening to the programms on my mp3 player) but as yet I haven't noticed any drop in quality that could be termed as having been destroyed.

When using lame to convert the files it's worth playing around with the -v or -V option (man lame for more details) to get an optimal file size/quality. That is another matter of taste! I have found the -v option (default variable bitrate) to be best

btw thanks andybleaden for your howto on the kubuntu forums

---

### Post by andrew.46 on 2008-12-24
Hi marn,

> **marn said:**
> ```
mplayer -bandwidth 9999999 -ao pcm:file=whatever.wav "rtsp_link" -dumpfile whatever.wav
```

Can I suggest a slightly different syntax that has worked well for me? I omit the -bandwidth option as I am not so sure about that one:

```
mplayer -cache 2048 **[COLOR="Red"]<address>[/COLOR]** \
        -vc null -vo null -ao pcm:fast:waveheader:file=filename.wav
```

This syntax adds in a cache option which is handy for streams as it establishes a decent buffer for MPlayer to work with, adds a few options to make the conversion of the stream a little faster and tightens up the filenaming syntax considerably. Obviously you need to substitute the real address for **[COLOR="Red"]<address>[/COLOR]** in this example. Love to know if you feel this altered syntax is any better or worse?

All the best,

  Andrew

---

### Post by marn on 2008-12-24
Hallo andrew.46

thanks for your contribution. I tried your command (without the bandwidth option) and what happens is mplayer plays the file (which it hasn't been doing before). I couldn't work out why, although I must admit I haven't had much time to try - the countdown to christmas has started (in germany they celebrate on the 24th) and our kids are going into hyperdrive at the moment :) 

I will have a fiddle with the different options when I have time and report back!

---

### Post by andrew.46 on 2008-12-24
Hi marn,

> **marn said:**
> thanks for your contribution. I tried your command (without the bandwidth option) and what happens is mplayer plays the file

Oops, you have only used half of it then :-). On one line:

```
mplayer -cache 2048 **[COLOR="Red"]<address>[/COLOR]** -vc null -vo null -ao pcm:fast:waveheader:file=filename.wav
```

Happy Christmas!!!

 Andrew

---

### Post by andybleaden on 2008-12-29
I will give the different commands re bandwidth a try and if they work for me ( the idiot that idiot proof refers to !) then I will stick them into the how to over on the kubuntu forums....any other suggestions to add/amendments to make?

---

### Post by marn on 2008-12-29
Ok, back again from christmas! 

I've changed the command according to the suggestion from andrew.46 so it looks like this now:

```
mplayer -cache 2048 -bandwidth 9999999 <address> -vc null -vo null -ao pcm:fast:waveheader:file=filename.wav
```

The cache option seems sensible. I couldn't work out what waveheader does or is for, but it works :D.

I am very pleased with the quality and the speed. It takes about 5 - 7 minutes to download and convert a 45 minute program, most of which is the mp3 conversion (my computer is not very fast). 

Thanks for all your contributions

---

### Post by DeaconBlues on 2009-01-02
> **andybleaden said:**
> On one note though I read elsewhere that when you increase the bandwidth it does record faster but quality is destroyed so let us know how it sounds afterward as you may have found a way around it

I can't, at this point, say if there's a decrease in quality if you use the bandwidth option.

I've recorded the last two Adam and Joe BBC6 music shows. On last weeks I used the bandwidth 9999999 option (took a few minutes to dump the .wav file) and this weeks I recorded in actual time (3 hours). 

I copy them onto my mp3 player and listen to them in the car, so I will report back here when I've listened to them properly to see if there's a decrease in quality when using "bandwidth 9999999".

I've encoded both files to 160kbps mp3 using Audacity in Vista on the same PC, so if there's any difference in quality it will definitely be down to using the bandwith option.

---

### Post by andybleaden on 2009-01-06
Wow ...it worked and so I have updated the how to guide over on the kubuntu forums...thanks for helping out with that...saves me loads of time. I need a better way of using lame so it is in stereo and 320 k...any ideas?

---

### Post by marn on 2009-01-06
Hallo andybleaden,

I'm using this command at the moment to convert the wav files to mp3's:

```
lame -v audiofile.wav audiofile.mp3
```

which uses the standard variable bitrate setting. Stereo is default. To get best VBR quality use -V0 instead of -v. Or use -b 320 to set the constant bitrate to 320 kbits (it more than doubles the size of the file)

Just in case anybody is interested in the script I use, here it is (don't expect anything great though!) I've also left the comments I put in for someone else, as I allways found it helpful to know what the lines are doing. If you want the script to automatically delete the wave file, then remove the hash (I didn't want to post a rm line, thats for others to decide): 

```
echo Please enter the rtsp address of the programm you want to record:
read RTSP
echo Please enter the programms name:
read NAME

# mplayer will now stream the link and record it as a wav file
# using the arguments you entered above
# Because of the bandwidth option, it is streamed at maximum speed
# instead of in real time
mplayer -cache 2048 -bandwidth 9999999 "$RTSP" -vc null -vo null -ao pcm:fast:waveheader:file="$NAME".wav

# lame now recodes the wav file to mp3. The -v option makes lame use
# variable bitrate for better quality
lame -v "$NAME".wav "$NAME".mp3

# this line removes the wav file from the harddrive 
# rm "$NAME".wav	

# Well, this is self explanatory!		
echo "***"
echo your mp3 is finished and ready to listen to
```

Comments and suggestions welcome btw :D

marn

---

### Post by heyup on 2009-01-16
I cribbed marn's script and made some changes:-
```
#!/bin/bash

# rtsp = real time streaming protocol (rtsp) address of the radio programme
# filename = file name of the radio programme
# vbr = variable bitrate quality setting (0-9) 0=highest quality, default=4 

echo -n "Enter the rtsp address of the radio program > "
read rtsp
echo -n "Enter the file name of the radio program > "
read filename
echo -n "Enter the variable bitrate 0-9 > "
read vbr

mplayer -cache 2048 -bandwidth 9999999 "$rtsp" -vc null -vo null -ao pcm:fast:waveheader:file="$filename".wav

lame -V"$vbr" "$filename".wav "$filename".mp3

# 'rm -i' command option to delete the wav file after creating the mp3 file

rm -i "$filename".wav	

echo "***"
```

Then I found get_iplayer [http://linuxcentre.net/getiplayer/]("http://linuxcentre.net/getiplayer/")

Its a neat programme.

---

### Post by DeaconBlues on 2009-02-13
After listening to a few shows I don't think there's an issue with sound quality when using the "bandwidth -9999999" option.

Has anyone else noticed a decrease in quality? I haven't, but I'm only listening in my car, which has old-ish speakers anyway.

---

### Post by marn on 2009-02-20
Thanks for the tip heyup - get_iplayer does everything the script does and much, much more. I've been using the programm for a couple of weeks now and wished I had found it straight away. At least I have some idea of how its working now (at least the mplayer bit!) For everyone wanting to download/listen to the listenagain programmes it's well worth a try.

---

### Post by heyup on 2009-02-20
Glad you liked the get_iplayer. It certainly makes downloading listen again radio programmes easier to do than the script in this thread.

I've made a simple script using the get_iplayer to find comedy & entertainment programmes on BBC7 and Radio 4. You select all the programmes you want to download, and it outputs to a designated folder/directory.

The get_iplayer also has the advantage of downloading using iphone, realaudio or flash. I'm told the iphone (the default option) is better quality than realaudio.

---

