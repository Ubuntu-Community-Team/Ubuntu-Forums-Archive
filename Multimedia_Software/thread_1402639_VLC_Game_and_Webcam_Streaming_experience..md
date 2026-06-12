---
title: "VLC Game and Webcam Streaming experience."
date: 2010-02-09
forum: Multimedia Software
---

### Post by mishaokami on 2010-02-09
PROBLEM:
My girlfriend is abroad for upwards of 6 months.  Keeping in contact is pretty important.  There are two problems however:
  
Skype has pretty good audio but its camera handling is worse than abysmal.  Of the 4 capture devices i have, (all < than 1yr old) none of them worked.  Empathy worked on 3 out of 4 of the devices but with poor echo cancellation (and no headsets) the sound quality was not the best.  So, skype it was.  But what about video?  And what about other activities?

Well, often when she was here, we would unwind with beer and games after work. Mostly she would watch and direct while i would play.

What follows is the result of 48+hrs of VLC research. For as frustrated as i was with the seemingly opaque command line interface in the beginning, in the end, i love it.  The videolan people should be praised and given donations.  While VLC is certainly tempermental at times, it is still more robust, and featureful than anything else i've found.



GOALS:
Get the webcams working in both directions.
Get a local (fast/hires) display for local gaming while i stream lower bitrate video/audio somewhere far away.  

Note: Lag kills. We play slowish games on the ps2 (Silent Hill/Canis Canem/etc).  Higher streaming resolution/fps eats upstream speed for breakfast.  Regardless, across the atlantic we have a lag of about 2-3 seconds.  Usable for us, but you will not be playing racing games with this setup.
Also, assuming a slow link, the values below for resolution, fps, bitrates represents the MINIMUM i've found to be usable.  If you have a fatter pipe then by all means crank everything to 11.
Lastly, when everything works these can all be put into scripts or gnome launcher buttons for effortless access.



SETUP:
I have a 700mhz notebook (karmic) with 380 meg ram, wifi, and a TV pccard (typhoon DBV-T Duo).  I connected the ps2 to the tv card and audio in into the Microphone jack.
Currently she attaches via http to home to get my webcam/game stream.  She starts an ssh forward on our home machine (my 8081) to her local 8080 so i can get to her webcam stream.

Optional:
I also added a larger external monitor and attached better speakers.



ASSUMPTIONS:
The webcam     = /dev/video0
The video card = /dev/video1
The sound capture device = /dev/dsp
The streaming port = 8080

You have verified independently with other programs (sound recorder, tvtime, etc) that your video / audio setup works before you start.

You port both forwarded 8080 on your home dsl/cable/air modem to 8080 on your local machine.
You have a DNS name for each host that has port forwards.  If you don't have one get one at no-ip.com or similar service.
If only one of your machines is behind an unchangable firewall, the inaccessable machine uses an ssh port forward. (see below)


QUICKIE SSH:
This can be a bit confusing at times. Unfortunately, a full explanation is beyond the scope of this howto.  This quick cheat sheet assumes a basic knowledge of ports and ssh.  If you are still having trouble there are plenty of ssh specific howtos lists and forums on the interwebs.

If one of you is behind a modem whose port forwards you can't modify (like my girlfriend) then ssh will be helpful.
Make sure you can ssh into your home machine from outside. (port forward 22 on your modem to your local machine)
From across the sea she uses this command and logs in:
ssh -f -R 8081:localhost:8080 [email]user@myhome.com[/email] sleep 1m

This connects as "user" to to myhome.com, forwards the home machines port 8081 to her machine (behind the unchangable firewall) port 8080 (where her webcam streamer is).
It then goes into the background and sleeps for 1 minute waiting for activity.
If there is no activity after one minute the forward is closed.
Otherwise if i connect to localhost:8081 on my home machine, this will get past the firewall to her machine port 8080.  If she is running her webcam streamer i will receive her video.
SSH will close the port when we disconnect.



HOWTO:
1) So, the webcam is the easiest type one of the following:

  with preview display:
    vlc -vvv v4l2:///dev/video0 --no-sout-audio --sout '#duplicate{dst=display,dst="transcode{width=250,height=180,fps=10.0,vcodec=mp4v,vb=130}:standard{access=http,mux=ts}"}'

  with no preview display:
    vlc -vvv v4l2:///dev/video0 --no-sout-audio --sout '#transcode{width=250,height=180,fps=10.0,vcodec=mp4v,vb=130}:standard{access=http,mux=ts}'

2) The TV will be a bit more difficult because sound is required.  I have found no source capture module for pulseaudio so i reverted to oss and use pasuspender.

To turn on mic monitor so you can hear the sound input:
amixer -c0 sset Mic 50% on (or toggle if you like)

Note: If you hear distortion on your laptop you probably have crappy speakers but make sure to also adjust input levels in the game and lower the microphone gain (Igain on my laptop).  From the command line aumix can be very useful for this.

Note: Don't forget to adjust "input" and "standard" (below) for your setup.

PAL:
pasuspender -- vlc -vvv v4l2:///dev/video0:input=3:width=640:height=480:standard=5 :input-slave=oss:///dev/dsp --sout '#duplicate{dst=display,dst="transcode{width=320,height=240,fps=16.0,vcodec=mp4v,vb=300,acodec=a52,channels=1,ab=16,deinterlace,samplerate=16000}:standard{access=http,mux=ts}"}'

NTSC:
pasuspender -- vlc -vvv v4l2:///dev/video0:input=3:width=640:height=480:standard=3 :input-slave=oss:///dev/dsp --sout '#duplicate{dst=display,dst="transcode{width=320,height=240,fps=16.0,vcodec=mp4v,vb=300,acodec=a52,channels=1,ab=16,deinterlace,samplerate=16000}:standard{access=http,mux=ts}"}'

4) On the client type:

  vlc [http://myhome.com:8080](http://myhome.com:8080) --http-caching 0 --http-reconnect --http-continuous

Note: If you use the ssh method, the person with the ssh daemon would instead run:

  vlc [http://localhost:8081](http://localhost:8081) --http-caching 0 --http-reconnect --http-continuous


Hopefully this works for you.  If not read below.



PERFORMANCE TUNING:
In the VLC command...
deinterlace didn't seem to have much effect
standard is the video standard you are using.  In my examples 3 is PAL and 5 is NTSC. A full list is available online.
input is the physical input you are using.  i.e. composite, svideo, tv, etc.
my choice of codecs, muxers, and transports is just what i found works/looks/sounds best to me.  Feel free to change them.

When something goes wrong i often got buffer related issues.  The most common were underrun or resync related.  In my experience there are 7 common variables related to this.

1) Processor power - make sure you stay below 80ish percent.

2) Video Bitrate - The more fps/stream resolution you have typically the higher bitrate you need to keep things smooth.  When frames degrade they don't fail nicely.

3) FPS - Every card has its own favorite framerate.  I've found that sometimes upping the fps can decrease cpu usage and buffer issues.

4) Capture Resolution - Same as fps.  If you capture at a weird resolution your capture card may balk. Higher resolution also means higher CPU usage.

5) Stream Resolution - If you are sending more pixels you probably need to up the video bitrate.

6) Sample Rate - Same as capture resolution but for sound.

7) Audio Bitrate - Must vary with the sample rate.  Strangely, the only thing that worked for me was keeping sample and stream bitrate the exact same.



DEBUGGING:
It's helpful is that vlc had two flags --no-sout-audio and --no-sout-video which prevents streaming of audio or video respectively.  If you have issues start with only audio or video and play with the variables before you enable the other.

If started from a gnome launcher you will not see vlc output. Prefacing the commands with "xterm -e " will output all errors to an x terminal.

I tried this on multiple machines and each had its favorite values.  Once i found them tho, performance was pretty stable.

---

### Post by guckpup on 2010-03-16
Fascinating, and thanks for sharing this. I think folks are just in awe of the fact your GF will ssh at all, and are in a state of stunned silence (hence the lack of replies).

---

