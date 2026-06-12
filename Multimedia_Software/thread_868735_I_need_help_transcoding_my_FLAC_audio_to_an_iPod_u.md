---
title: "I need help transcoding my FLAC audio to an iPod using Ubuntu 8.04!"
date: 2008-07-24
forum: Multimedia Software
---

### Post by gobbles414 on 2008-07-24
Thanks in advance for your help. I'm typing this way past my bedtime, so I hope that it all makes sense.

I am trying to upload music from my Ubuntu 8.04 computer to my iPod. My computer is running 32-bit GNOME Ubuntu, I have activated medibuntu, allowed backports in Software Sources, installed restricted extras, and installed all updates. My iPod is generation 5.0, and I freshly restored it earlier today with the latest firmware using Windows XP and the newest version of iTunes. My music collection is a mixture of mp3 and FLAC audio files. Obviously, I need to transcode my FLAC files to an iPod-compatible format. But none of the programs that I've tried thus far have been satisfactory.

Rhythmbox insists on transcoding into an m4a format. None of the transcoded files will play correctly on my iPod. Is it possible to have Rhythmbox transcode FLAC => mp3 instead?

Floola seems like a potentially great iPod manager/transcoder. But the program simply gets overwhelmed by the 3000+ songs in my music library; Floola freezes when I attempt to add all of my songs to the queue.

Banshee from the repos takes a very long time to transcode -- nearly 12 hours -- and then reports that many of my FLAC files can not be transcoded. Banshee mentions an mp3-related error, with the number 508 in parentheses. I can provide the exact error message tomorrow, if any of you would find it helpful.

Following the instructions on the official Banshee website, I installed the new Banshee 1.0. Of course, I uninstalled the older version of Banshee prior to installing the newest one. Banshee 1.0 stops transcoding almost immediately, and reports that a file has failed to transcode. Again, I can provide an exact error message if it would help.

I've also tried Amarok, which sees my iPod but refuses to transcode. The transcode options in Amarok for my iPod are grayed out. 

Foobar2000, a Windows program, has worked well with my iPod in the past. In Windows, the latest versions of Foobar2000 and the iPod component are able to successfully transcode my entire collection of FLACs in a matter of minutes. But unfortunately, something about Wine is incompatible with Foobar2000's iPod component. The main Foobar2000 program works. But even with the correct iPod component installed, my iPod remains undetected.

Any ideas...? Even the most radical suggestions are welcome. Thanks again! :guitar:

---

### Post by ministoat on 2008-07-24
it's maybe not the perfect answer, but one way of doing it would be to bulk convert your flac to mp3 on your local drive using foobar, and then use whatever other program to send them to your ipod. that's assuming you have enough hard drive space :P

---

### Post by cozmicharlie on 2008-07-24
It is really fairly simple to do and you have lots of options.  From reading your post I sense you want an all in one solution.  Let me list a few options for you and you can decide which you like.

First - make sure you have all the codecs installed (the gstreamer plug ins).  Make sure and install flac from Synaptic.  You probably also want the lamemp3 codec.

Once you have them installed then you can easily convert to mp3 using Soundconverter (I believe this comes installed in Hardy but if not you can install it from Synaptic then go to applications>sound and video).  

Another option is to go back to Amarok (a very popular player for those that want an all in one player).  But, also install SoundKonverter (in Synaptic).  Don't worry that it is kde it works fine and it integrates with Amorak for file transcoding.  Again though, make sure you have the codecs installed.  Also, if you are using the gstreamer plugins then set Amorak to use the gstreamer engine (not xine).  If you use the Xine engine make sure and install all the libxine plug ins. I read somewhere Amorak works better under xine so you may try that. 

Exaile is a player similar to Amorak but for gnome.  You may want to give it a try.  

You should be able to get Rythmbox to transcode to mp3 - change the preferred codec (in the menu go to edit>preferences>music>change the preferred format to mp3).  That should work for you.

There are other options also but they are command line and I get the sense you want an integrated solution rather than a stand alone command line solution.

---

### Post by cozmicharlie on 2008-07-24
I forgot to mention - you can also run Foobar in Wine.  I am not sure how the ipod function or transcoding works through Wine though.  I use it for the live show tagger and it works great (no linux app I have found does this).  But, for all other functions I use native Linux apps.  I normally don't like Wine and Foobar is the only program I use in Wine - but, it is another option for you.

---

### Post by kajillin on 2008-07-24
Im not sure if it will work on your ipod, but there is a custom firmware available that lets some ipods play flac audio. Its called rockbox, this is from the wikipedia "Rockbox on software decoding platforms (non-Archos) supports playback (depending on how you count them) of eight lossy codecs, five lossless, two uncompressed and four miscellaneous formats. This makes a conservative total of 19 supported audio formats, although a few of them do not operate in realtime on all platforms" . But it only installs on certain models, check it out [http://www.rockbox.org/](http://www.rockbox.org/) and the wiki is a little easier to get all the info you need so here [http://en.wikipedia.org/wiki/Rockbox](http://en.wikipedia.org/wiki/Rockbox)

---

### Post by cozmicharlie on 2008-07-24
> **kajillin said:**
> Im not sure if it will work on your ipod, but there is a custom firmware available that lets some ipods play flac audio. Its called rockbox, this is from the wikipedia "Rockbox on software decoding platforms (non-Archos) supports playback (depending on how you count them) of eight lossy codecs, five lossless, two uncompressed and four miscellaneous formats. This makes a conservative total of 19 supported audio formats, although a few of them do not operate in realtime on all platforms" . But it only installs on certain models, check it out [http://www.rockbox.org/](http://www.rockbox.org/) and the wiki is a little easier to get all the info you need so here [http://en.wikipedia.org/wiki/Rockbox](http://en.wikipedia.org/wiki/Rockbox)

+++++1 on Rockbox
I absolutely agree - I have Rockbox installed on my ipod and I would never go back to the native Apple crap. I simply copy my flac files from a folder on my computer to the music folder in Rockbox - so simple and its flac so the sound quality is great (you do sacrifice space though).

---

### Post by imasickboy on 2008-07-24
Coz, I've used a script called flacify in the past to tag live shows from the accompanying text file. It reads the standard text file given with live flac downloads, and tags the tracks accordingly. It works very well, and I highly recommend it. 

I don't have it currently, but it shouldn't be hard for you to search out. (Try etree.)

---

### Post by cozmicharlie on 2008-07-24
> **imasickboy said:**
> Coz, I've used a script called flacify in the past to tag live shows from the accompanying text file. It reads the standard text file given with live flac downloads, and tags the tracks accordingly. It works very well, and I highly recommend it. 

I don't have it currently, but it shouldn't be hard for you to search out. (Try etree.)

Thanks for the tip - I will check it out.

---

### Post by gobbles414 on 2008-07-26
Thank you all very much for your replies. Here are the results of your ideas -- sorry in advance for the long post:

I tried Rockbox about a year ago, as was not happy with the user interface. So unless Rockbox has really improved since then, I'm going to be switching away from the default Apple firmware. Besides, the only way that I can fit my entire music collection on my iPod is to transcode. My 5th Generation iPod is only 30 gigs.

As I mentioned in my original post, I tried running Foobar2000 in Wine but the necessary iPod component would not function correctly. I may eventually try transcoding to my hard drive using Foobar2000. But for now, I'm holding out hope that iPod/FLAC support in Ubuntu will improve.

I believe that all of the gstreamer0.10 packages which control transcoding from FLAC to mp3 are installed along with the ubuntu-restricted-extras package, which is the first package I installed on my computer after updates. I have also installed packages like *lame*, *lame-extras*, and *flac*.

In Rhythmbox, I changed *Edit => Preferences => Music* to MP3. Additionally, I also pressed the *Edit* button there, and removed the checkmark from the *Active?* box in the AAC profile. After doing this, Rhythmbox no longer transcoded to m4a files. BUT, Rhythmbox then developed a new problem. It would only transcoded some of my FLACs. Many of my FLACs were being transferred to iPod as FLACs -- without transcoding of any kind. To fix this, I attempted to alter the syntax in the *GStreamer pipeline* part of Rhythmbox's MP3 profile. None of my modifications have convinced Rhythmbox to transcode all of my FLACs.

Amarok does not function correctly with my iPod either. At least with the SQlite option, "Xine engine" is my only choice in *Settings => Configure Amarok => Engine => Sound System*; there is no GStreamer option. Per advice, I installed *libxine1-all-plugins*. But Amarok did not detect my iPod until I manually added it using *Settings => Configure Amarok => Media Devices*. I also had to manually direct Amarok to my iPod's mount point. None of my FLAC files would transcode, and all of the transcoding options in the *Configure Media Device* window were inaccessible.

Exaile did not work correctly with my iPod either. I installed the *python-gpod* package in Synaptic. Then, I installed and enabled the *Exaile iPod Plugin*. Even with the correct iPod mount point, Exaile crashed every time that I tried to access my iPod. I discovered a workaround; pressing the *refresh* button in the *Devices tab* would prevent a crash. Two iPod icons then appeared in Exaile. I discovered that the top iPod was mine. Dragging audio files from the Exaile library to my iPod copied the FLACs to my iPod without any transcoding. That is to say, the files which were sent to my iPod were FLACs.

Despite having the *podsleuh* package installed, both versions of Banshee failed. Installing packages which reference ipod-sharp did not help. In Banshee 0.13.2+dfsg-9, many of my FLACs would not transcode successfully to mp3s with bitrates higher than *constant 160*. The newer Banshee wasn't any better. First, Banshee 1.0.0-1ubuntu1~hardy3 was inconsistent when it came to displaying my iPod. Second, when I tried to transcode FLACs to constant MP3 files, I got an error message (see attached). Third, variable bitrate and average bitrate refused to create files with bitrates higher than 158 -- even at a setting of 9.

A solution that did work correctly for me in Ubuntu was converting all of my music to mp3s in Sound Converter, then using a program called Floola I added these converted files to my iPod. **Note, I do not consider this method to be an acceptable permanent solution.** I should be able to achieve what I want to do in a single program. Also, some of my FLACs do not transcode in Sound Converter successfully unless variable bitrates are used -- I think that variable 256 will work nicely.

While I am grateful to all of the developers who've made Ubuntu such a great operating system, iPod/FLAC support in Ubuntu really needs to be improved. In Microsoft Windows, Foobar2000 does a great job of transcoding my FLACs to my iPod as high-quality mp3s. Why is it proving so difficult in Ubuntu?

---

### Post by Yellow Pasque on 2008-07-26
Does your iPod support ogg/vorbis? You'd probably have better luck encoding to that (it's an "open" format) and it sounds better than mp3 anyway.

---

### Post by cozmicharlie on 2008-07-26
Actually flac is well supported in ubuntu which makes your situation even more frustrating because it should work.  The problem does not appear to be in Ubuntu since you can get Sounconverter to work(for the most part).  It is a problem in the integrated players -they just can't seem to get it right.  I have always hoped someone would come along and port Foobar to Linux but it most likely won't happen.

[LIST=1]
[*]I don't remember if Amorak is integrated with SoundKonverter in Gnome but I find it much better than Soundconverter.  You can install SoundKonverter from Synaptic. If you do then open settings>configure soundkonverter>general and you will see a dialog box that says "number of files to convert at once - make it 1.  Then try and transcode your files again.  
[*]You can use this method to permanently mount the ipod with Amarok [http://sofabedz.co.uk/linux/iPod.html#Hardy](http://sofabedz.co.uk/linux/iPod.html#Hardy)
[*]As per Xine - you have a choice to install Amarok with Xine or with multiple engine support through Synaptic.  You have installed Amarok for Xine so it is the only option in preferences.  If you install the other Amarok you have a choice of gstreamer or xine.  You might want to try the gstreamer engine also but I am not sure your results will be any better.
[*]Also, do your files have any gaps in the titles?  
[*]Also, are they tagged?  Amarok uses ID3v1 tags. most newer taggers use ID3V2 so sometimes the tags cause problems.
[/LIST]

People rave about Banshee on the forums but I have never been impressed. 

For me -I use PACPL to transcode, gtkpod to manage the ipod and xmms to play.  I personally don't like integrated solutions but to each his own.  (actually for the ipod I use Rockbox so I just add my flac files directly to the ipod without transcoding).

Other than that I am out of ideas.  They are launching Amarok 2 soon ([http://lifehacker.com/399160/an-early-look-at-amarok-2](http://lifehacker.com/399160/an-early-look-at-amarok-2)) - hopefully, it will have better support for transcoding and integrating with the ipod.

---

### Post by gobbles414 on 2008-07-26
> Does your iPod support ogg/vorbis? You'd probably have better luck encoding to that (it's an "open" format) and it sounds better than mp3 anyway. I don't think that iPods support oggs. I have one ogg file in my music library. It's a non-FLAC ogg, but it still fails to play on my iPod.

> Actually flac is well supported in ubuntu which makes your situation even more frustrating because it should work. Your point is well taken. But it seems to me that when so many music managers are failing to function correctly, the operating system might be at least partially to blame.

> I have always hoped someone would come along and port Foobar to Linux but it most likely won't happen. I feel the same way about Foobar2000 in Ubuntu as I do about Windows Live Messenger in Ubuntu. I think that the best solution, at least in the short term, is to get these programs running correctly in Wine. WLM, and its predecessor MSN Messenger, have always had a lot of problems running in Wine. But Foobar2000 works very well in Wine; it's just Foobar2000's iPod plugin that fails. I'm debating about contacting the developer of Foobar2000's iPod plugin for help.

> You can use this method to permanently mount the ipod with Amarok [http://sofabedz.co.uk/linux/iPod.html#Hardy](http://sofabedz.co.uk/linux/iPod.html#Hardy) Thanks for the link. But since Amarok won't transcode to my iPod anyway, I don't see the purpose in messing with mounting options. I'll keep this idea in reserve.

> As per Xine - you have a choice to install Amarok with Xine or with multiple engine support through Synaptic. How? When I chose the amarok package, the amarok-xine option was automatically selected. Perhaps I don't have access to all of the amarok packages, since I'm using GNOME...?

> Also, do your files have any gaps in the titles? I assume that you mean spaces versus underscores, like *This is my song* instead of *This_is_my_song*. If so, then yes... many of my songs have spaces in both their titles and filenames.

> Also, are they tagged? Amarok uses ID3v1 tags. most newer taggers use ID3V2 so sometimes the tags cause problems. They are probably all tagged in ID3v2, as I recently used EasyTag to do some advanced tag editing to my entire music library. But as you say, any program that uses GStreamer technology should react similarly to Sound Converter, and Sound Converter doesn't seem to choke on my tags. So at least one of my music managers should be transcoding correctly, right?

---

### Post by cozmicharlie on 2008-07-26
> I don't think that iPods support oggs. I have one ogg file in my music library. It's a non-FLAC ogg, but it still fails to play on my iPod.

You are correct it does not.

> I feel the same way about Foobar2000 in Ubuntu as I do about Windows Live Messenger in Ubuntu. I think that the best solution, at least in the short term, is to get these programs running correctly in Wine. WLM, and its predecessor MSN Messenger, have always had a lot of problems running in Wine. But Foobar2000 works very well in Wine; it's just Foobar2000's iPod plugin that fails. I'm debating about contacting the developer of Foobar2000's iPod plugin for help.

Maybe the ipod developer might help - I know the Foobar developer is very adamant he will not work on a linux version (doesn' have the time and I can't blame him).

>  How? When I chose the amarok package, the amarok-xine option was automatically selected. Perhaps I don't have access to all of the amarok packages, since I'm using GNOME...?

I would try Amarok again.  Do you have the medibuntu repository enabled?  If not you should.  I use gnome also and I have Amarok, Amarok Engines, and Amarok Xine in Synaptic.  Amarok and Amarok Engine give you the gstgreamer option.  Also, the Medibuntu plug ins are generally recommended over those in the other repositories (I have no idea why). You should try Amarok again with SoundKonverter (not Soundconverter).  Install SoundKonverter.  Restart your computer, open Amarok and in the menu go to tools>script manager and enable it (while in the script manager also install transceAACplus for transcoding to aac just in case you want a better sound).  Then in Amarok, you right click on the music file and you should have an option for SoundKonverter.  Use SoundKonverter to transcode and remember to set it to encode 1 file at a time.  SoundKonverter has always worked great for me. 

>  I assume that you mean spaces versus underscores, like *This is my song* instead of *This_is_my_song*. If so, then yes... many of my songs have spaces in both their titles and filenames.

Yes - spaces.  Linux file systems don't like spaces.  If the files that are not coding have spaces in the file names (not the tags), use underscores and retry.

 > They are probably all tagged in ID3v2, as I recently used EasyTag to do some advanced tag editing to my entire music library. But as you say, any program that uses GStreamer technology should react similarly to Sound Converter, and Sound Converter doesn't seem to choke on my tags. So at least one of my music managers should be transcoding correctly, right?

Yes, If that was the problem then I would expect it to be a problem in Banshee or Rythmbox so you are right that should not be causing the problem.

If I had my Ipod I would check these all out on my system but its in the shop getting a new mainboard.  Once I get it back I am going to try some of these.

---

### Post by gobbles414 on 2008-07-27
Thank you for your continued interest, comzmicharlie.

I tried installing Amarok again, this time on an Ubuntu 7.10 laptop. Installing *soundkonverter* and *amarok-engines* did not help. "Xine Engine" is still the only option that appears in Amarok's *Configure Engine* menu -- no GStreamer. I have little reason to believe that the results would be any different on my Ubuntu 8.04 computer, so I'm not going to try.

I cannot establish any pattern regarding which FLACs will successfully transcode and which ones will not. I've looked at everything from spaces & special characters in filenames, to track length, to bitrates. Yet I still cannot find any sort of pattern that explains why my FLACs will reliably transcode in Sound Converter, but not in any music managers. In fact, Banshee 1.0 will sometimes fail to transcode a given FLAC, but succeed if I attempt to transcode the same FLAC a few moments later. And as stated in one of my previous replies, some music managers don't even try to transcode.

My feeling is that the key to solving these transcoding problems is in the Banshee error message that I've attached to this thread. If we can decipher that message, then I bet the solutions to my transcoding problems will present themselves.

---

### Post by cozmicharlie on 2008-07-27
Have you tried to post on the Banshee forums?

---

### Post by gobbles414 on 2008-07-27
> **cozmicharlie said:**
> Have you tried to post on the Banshee forums? Since so many programs have failed to transcode to my iPod, I thought that these forums were the logical place to start. After I give the folks at Ubuntu Forums a few more days to generate a solution to my problem, I'll probably post at the Banshee forums. I may also post at the Foobar2000 forums and/or contact the developer of the Foobar2000 iPod plugin. Thanks again...

---

### Post by nothingspecial on 2008-07-28
This works.
[http://projects.robinbowes.com/flac2mp3/trac](http://projects.robinbowes.com/flac2mp3/trac)
It transcoded all my flacs to mp3s painlessly.

However, I haven`t managed to get all of them on my ipod using Banshee (which I like `cause of it`s podcast support).
I don`t know wether this is a problem with flac2mp3, Banshee or my ipod. I do know that I`ve got a fat juicy mp3 folder that I didn`t have before though.
Give it a shot if you like. It might work great for you.

---

### Post by gobbles414 on 2008-07-28
> **nothingspecial said:**
> This works.
[http://projects.robinbowes.com/flac2mp3/trac](http://projects.robinbowes.com/flac2mp3/trac)
It transcoded all my flacs to mp3s painlessly.

However, I haven`t managed to get all of them on my ipod using Banshee (which I like `cause of it`s podcast support).
I don`t know wether this is a problem with flac2mp3, Banshee or my ipod. I do know that I`ve got a fat juicy mp3 folder that I didn`t have before though.
Give it a shot if you like. It might work great for you. Thanks for the link. It looks like flac2mp3 is very much like the Sound Converter program that I'm already using. The "fat juicy mp3 folder" that you mention may be cache left over from when flac2mp3 transcoded all of your files; some transcoders don't delete their caches when they finish transcoding. For example, I know that in Ubuntu 8.04, the Banshee 1.0 transcoder maintains a cache in a hidden folder, which is located at */home/YOURUSERNAME/.cache/banshee-1/transcoder*.

---

### Post by gobbles414 on 2008-08-04
I've made an encouraging discovery as well as an upsetting one.

The upsetting discovery is that Sound Converter has been lying to me! I selected 256 kbps VBR MP3 in Preferences. But most of my FLACs have been converted into MP3s which both Ubuntu and Windows report as being less than 160 kbps joint stereo. This situation is clearly unacceptable.

The encouraging discovery is that Banshee 1.2 no longer crashes while transcoding to my iPod. A few moments after posting this message, I will be attempting to transcode to my iPod in Banshee 1.2 using 320 kbps CBR MP3s; transcoding to CBR seems to be working correctly in Banshee 1.2. I will report back ASAP with the results.

---

### Post by gobbles414 on 2008-08-04
Sadly, Banshee did not successfully transcode my FLACs to constant MP3 at 320 kbps. Banshee presented an error message identical to that which I attached earlier.

The next step for me is going to be re-converting all of my FLACs to MP3 using Foobar2000. I'll transcode to my hard drive and then manually transfer the transcoded files to my iPod, at least until if/when I can get the Foobar2000 iPod plugin to function in Wine. Unfortunately, I'm going on vacation in a couple of days, and I won't have time to re-convert my songs until I return home.

---

### Post by nothingspecial on 2008-08-07
If you use the flac2mp3 link I gave you, you can change the bit rate in the script to whatever you like.:)

---

### Post by gobbles414 on 2008-08-07
> **nothingspecial said:**
> If you use the flac2mp3 link I gave you, you can change the bit rate in the script to whatever you like.:) I'll try flac2mp3 as soon as I get back from my vacation.

---

### Post by gobbles414 on 2008-08-14
I was excited to try flac2mp3, but then I realized that it's a command line program. I don't have a problem understanding most command line programs. But I sort of have a personal rule: never use the command line when a GUI can do close to the same task.

So what I'm doing now is using Foobar2000 in Wine to transcode my FLACs to a folder on my hard drive. Then, I'm using Floola to add those converted tracks to my iPod. I'll live with this solution for a couple of days, and then I'll post my findings.

---

### Post by nothingspecial on 2008-08-15
> **gobbles414 said:**
> I was excited to try flac2mp3, but then I realized that it's a command line program. I don't have a problem understanding most command line programs. But I sort of have a personal rule: never use the command line when a GUI can do close to the same task.

So what I'm doing now is using Foobar2000 in Wine to transcode my FLACs to a folder on my hard drive. Then, I'm using Floola to add those converted tracks to my iPod. I'll live with this solution for a couple of days, and then I'll post my findings.

Whatever floats your boat, but I have to say -
 (and this is coming from the perspective of someone who got the ubuntu drums the 1st time I ever switched a computer on so I started with terminals and guis at the same time)
    - firing up a terminal with a keyboard shortcut and typing flac2mp3 has got to be easier than installing wine and then all that pointing and clicking.

Hope you get your mp3s sorted. :)

---

### Post by gobbles414 on 2008-08-15
> **nothingspecial said:**
> Whatever floats your boat, but I have to say -
 (and this is coming from the perspective of someone who got the ubuntu drums the 1st time I ever switched a computer on so I started with terminals and guis at the same time)
    - firing up a terminal with a keyboard shortcut and typing flac2mp3 has got to be easier than installing wine and then all that pointing and clicking.

Hope you get your mp3s sorted. :) That's what I love about Ubuntu... There's usually more than one solution to the same problem. By the way, so far my iPod hasn't had any problems playing files that I converted in Foobar2000.

---

### Post by firecat53 on 2008-08-18
Amarok with the script Trankode works great changing all my archived CD's from FLAC to mp3 for the ipods. It takes a little setup to make sure the file names, location and your mp3 settings are what you want, but then it works without a hitch as a right click option for any music in Amarok. 

If you're running Ubuntu 64-bit, I posted a [.deb for trankode and it's dependency]("http://ubuntuforums.org/showthread.php?t=790805") a while back since the one you can download through amarok only works for 32 bit. 

Scott

---

### Post by gobbles414 on 2008-08-18
> **firecat53 said:**
> Amarok with the script Trankode works great changing all my archived CD's from FLAC to mp3 for the ipods. It takes a little setup to make sure the file names, location and your mp3 settings are what you want, but then it works without a hitch as a right click option for any music in Amarok. 

If you're running Ubuntu 64-bit, I posted a [.deb for trankode and it's dependency]("http://ubuntuforums.org/showthread.php?t=790805") a while back since the one you can download through amarok only works for 32 bit. 

Scott Thanks for the idea, but I'm skeptical to try Amarok again -- especially since using Foobar2000 in Wine to transcode to my hard drive seems to have worked.

---

### Post by paulsdavies on 2008-08-20
Hi,

Just stumbled across this thread and thought I would put in a recomendation for Amarok. After a fair bit of fiddling, I have this working fine, and apart from never being able to mount my iPod in the same place each time (which I don't think is an Amarok issue anyway) it is ultra stable - much more than iTune ever was, does everything I need and transparently transcodes my 7,000 track flac library into mp3 onto the iPod.

I did have to hack the transkode config script to get it support flac as an input file though - if you want a copy of my config let me know (or Google for Amarok Transkode Flac to find the same page I did which gave the solution).

Regards,



Paul.

---

### Post by gobbles414 on 2008-08-21
Thanks for the idea, paulsdavies. In addition to all of the problems that I had with Amarok during testing, I really don't like KDE interfaces. So, I've decided to continue with my current method until I can successfully use Banshee in Ubuntu to transcode to my iPod.

---

### Post by Floola on 2009-05-10
Floola 5.1 beta now features FLAC transcoding with tag and embedded artwork support as well. Besides this version is focused on improving performances, so you should notice a significant speed boost.

It's a beta so backup your iPods before using: [http://www.floola.com/modules/wiwimod/index.php?page=download-beta](http://www.floola.com/modules/wiwimod/index.php?page=download-beta)

Tomas

---

