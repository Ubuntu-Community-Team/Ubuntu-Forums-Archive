---
title: "Clementine and Gstreamer"
date: 2014-10-30
forum: Multimedia Software
---

### Post by andrew_s4 on 2014-10-30
Have downloaded Clementine and it is a really impressive and easy music player. Until it tries to play a WMA file, and then I get an error message from Clementine:   Your GStreamer installation is missing a plug-in.

So I installed (what I assume) all of the GStreamer extra plugins plus Ubuntu Restricted Extras package. No change. So I de-installed Clementine and reinstalled it, with no change. 

Gstreamer installation is missing a plug-in and the error message won't tell me what plug in, and all of the extra packages don't seem to change the problem. VCL works fine as does Rhythm Box, but I love how easy Clementine is to use. The other players require a lot of learning. Which brings me to my next point. I'm an absolute beginner with Ubuntu, having spent hours on a full install of 14.04 on my laptop. Would appreciate some help in getting Clementine to play my WMA files, but please don't forget to use words, rather than abbreviations!!

thanks, Andrew

---

### Post by oldos2er on 2014-10-30
According to [this]("http://askubuntu.com/questions/448967/clementine-refuses-to-play-m4a-wma-and-wav") you may need to install gstreamer0.10-ffmpeg from this PPA: [https://launchpad.net/~mc3man/+archive/trusty-media](https://launchpad.net/~mc3man/+archive/trusty-media)

---

### Post by andrew_s4 on 2014-10-31
Thanks for the reply. I downloaded the packgage gstreamer0.10-ffmpeg from the Ubuntu Software Center, but still no wma support from Clementine. Is there a difference between the software package in your suggestion from the PPA and the version from the Ubuntu software center?

---

### Post by oldos2er on 2014-10-31
Yes, it needs to be the package from the PPA; the repository package is actually avconv and not ffmpeg, despite its name.

---

### Post by mc4man on 2014-10-31
> **andrew_s4 said:**
> Thanks for the reply. I **downloaded the packgage gstreamer0.10-ffmpeg **from the Ubuntu Software Center, but still no wma support from Clementine. Is there a difference between the software package in your suggestion from the PPA and the version from the Ubuntu software center?
That would not be possible in 14.04 as the last available gstreamer0.10-ffmpeg package from Ubuntu repos is for 12.04 (precise
Are you sure you're on 14.04?

So before you go to much further what's this show?
```
apt-cache policy gstreamer0.10-ffmpeg
```

---

### Post by andrew_s4 on 2014-11-02
> **mc4man said:**
> That would not be possible in 14.04 as the last available gstreamer0.10-ffmpeg package from Ubuntu repos is for 12.04 (precise
Are you sure you're on 14.04?

So before you go to much further what's this show?
```
apt-cache policy gstreamer0.10-ffmpeg
```

I'm sure I'm on 14.04. It was a clean and fresh installation. Here's what I got from your code: 
```
gstreamer0.10-ffmpeg:
  Installed: 0.10.13-5ubuntu1~trusty2
  Candidate: 0.10.13-5ubuntu1~trusty2
  Version table:
 *** 0.10.13-5ubuntu1~trusty2 0
        500 http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status

```

It seems I did download it from the PPA link. This is a very big learning curve at the moment, so I hope you'll be patient!! However this package didn't change Clementines ability to play a wma file. It still brought up the same error message:  Your GStreamer installation is missing a plug-in.  Does this mean that because I'm using 14.04 that the gstreamer0.10-ffmpeg package doesn't/wouldn't work even if installed? 

Would really like to use Clementine, as it is so straight forward, except for this major startup glitch. The other media players Rhythmbox and VLC require more effort and hours (=$)for me to get up and going.

Advice still needed!

---

### Post by mc4man on 2014-11-02
"However this package didn't change Clementines ability to play a wma file."
Actually it does, maybe not the wma you have..
Here tested on - 
Windows Media Audio V8 (wma2) - works
Windows Media Audio 9.1  (wma2) - works
Windows Media Audio 9.1 Professional (wmapro) - works
Windows Media Audio 9 Lossless (wmal) - doesn't work, won't work

At the end of the day if clementine sticks with gstreamer it really should port to 1.0+

---

### Post by andrew_s4 on 2014-11-02
> **mc4man said:**
> "However this package didn't change Clementines ability to play a wma file."
Actually it does, maybe not the wma you have..

Sorry, I don't know how to interpret that. What do you mean by ''maybe not the wma you have''? I have a huge number of wma files assembled over the last 15 years and using windows media player they played without a hitch. Is it somehow unthinkable or unfair to hope that Clementine could do the same? I don't think so, but I'm very new to the Ubuntu/Clementine philosophy. And why can VLC and Rhythmbox do it, but not Clementine?
 I'm still hopeful there is an answer out there.

---

### Post by mc4man on 2014-11-02
> **andrew_s4 said:**
> Sorry, I don't know how to interpret that. What do you mean by ''maybe not the wma you have''? I have a huge number of wma files assembled over the last 15 years and using windows media player they played without a hitch. Is it somehow unthinkable or unfair to hope that Clementine could do the same? I don't think so, but I'm very new to the Ubuntu/Clementine philosophy. And why can VLC and Rhythmbox do it, but not Clementine?
 I'm still hopeful there is an answer out there.
Well there are several formats for .wma.
Maybe install mediainfo-gui, then open one of your files in it. Post the relevant info on type of wma. Should show in default window or once open switch to View > Text for more & ability to copy & paste from.

Or you could upload a file to here somewhat anonymously & 'll dl & ck. out
[www.datafilehost.com](www.datafilehost.com)
(you can pm a link if desired

Or - download this sample & see if it plays in Clementine
```
 wget 'http://samples.mplayerhq.hu/A-codecs/WMA9/wmapro/New%20Stories%20(Highway%20Blues)-1.wma'
```

---

### Post by andrew_s4 on 2014-11-02
Well... your code worked! Now that's confused me...I've pm you a link to a wma file that doesn't work.

---

### Post by mc4man on 2014-11-02
Your file is wma lossless which Clementine can not play back.  Unless clementine moves to gstreamer1.x it will never playback wma lossless
An option for you would be to convert your wma lossless to flac. 
If desired maybe start a new thread on that, describe the current 'setup' of your files (how organized) & whether you need tags, ect.

---

### Post by andrew_s4 on 2014-11-02
Yes, thanks I did the same check just now and came out with the same thing. Lossless... 
converting to flac seems daunting to me at my level of understanding using command line tools. I'm thinking to switch to another media player that works with all my formats till I can come up the courage and hours to figure flac out!
Thank you for your help.

---

### Post by mc4man on 2014-11-02
> **andrew_s4 said:**
> UPdate:   Ok did as you suggested. The file I pmed you, I also checked with mediainfo-gui and it is a Windows Media Audio 9 Lossless format. You wrote - "doesn't work won't work".
So I'm a little bit more ahead. I suppose my only choice now is to find another media player that plays these formats without problems. I assume that's all I can do, would that be right?
As I mentioned you can convert wma losseless to flac.  
How are your wma's organized?, maybe we can do a quick test though if you start a thread on that you should  get an abundance of methods.

---

### Post by andrew_s4 on 2014-11-02
> **mc4man said:**
> How are your wma's organized?,

hmmm, All of my music files sit on an external harddrive. They are in various formats, many if not most in wma lossless format. All sit in folders related to their Artist/Album's name. ie.../music/The Beatles/White Album and so on. 
Does this help? Or are you looking for something a bit more indepth!?

---

### Post by mc4man on 2014-11-02
I see you started new thread - good, let's see what shakes down.
If you could I'd like to see what this shows - 
```
apt-cache policy ffmpeg
```
And assuming you are running Ubuntu 14.04 (with nautilus) it would be good to install this in case a command line conversion is the way to go - 
```
sudo apt-get install nautilus-open-terminal
```
After install just do a log out/in And then you'll have a r. click option on folders "Open in Terminal" which will be useful

---

### Post by andrew_s4 on 2014-11-03
> **mc4man said:**
> I see you started new thread - good, let's see what shakes down.
If you could I'd like to see what this shows - 
```
apt-cache policy ffmpeg
```

The result:
ffmpeg:
  Installed: (none)
  Candidate: 7:2.4.2~trusty1.1
  Version table:
     7:2.4.2~trusty1.1 0
        500 [http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/](http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/) trusty/main amd64 Packages

Installed: none-does this mean it is not installed?

> And assuming you are running Ubuntu 14.04 (with nautilus) it would be good to install this in case a command line conversion is the way to go - 
```
sudo apt-get install nautilus-open-terminal
```
After install just do a log out/in And then you'll have a r. click option on folders "Open in Terminal" which will be useful

Done!

---

### Post by mc4man on 2014-11-03
/Cool, all is ok
Let's install ffmpeg & then because no response yet I'll post a simple cli to test conversion with ffmpeg in your other thread
(so we'll consider this thread finished, ie. clementine can't decode wma lossless..

```
sudo apt-get install ffmpeg
```
This is installing a static build of ffmpeg 2.4.2 
All that it is providing is the binaires - ffmpeg, ffplay, ffprobe for use to encode/decode, ect.

---

