---
title: "Mythweb music on Android phone"
date: 2010-06-10
forum: Mythbuntu
---

### Post by larsolav on 2010-06-10
I recently got my fist smart phone running Android 2.1, so this is an Android and Mythtv question.

I have Mythweb setup with a password and can connect to it over the internet. But the phone can't play the music streams (my work computer can, so the music steaming functionality works on the Myth side). After having browsed for some music on the phone, I then click play and nothing happens. Does any one here know how to get an Android phone to play such playlists that refer to a password protected server?

I'd love to be able to access my entire music library at home!

It would also be awesome if the phone friendly web interface included a "music" button in addition to the Television & Remote icons. I wish I knew how to do cool stuff like that...

---

### Post by LowSky on 2010-06-10
I found this, maybe its worth looking into
[http://androidforums.com/android-media/35721-stream-music-your-home-computer-help-test-mecanto.html](http://androidforums.com/android-media/35721-stream-music-your-home-computer-help-test-mecanto.html)

I'm thinking it can easily be done, but maybe not with MythTv, I dont know

---

### Post by tmcgary on 2010-08-29
Had anyone had any luck with this? I have tried this with both a verizon droid and sprint htc evo 4g using froyo and had the same experience. Everything looks great with the mythweb interface but nothing happens when you click the link. Upon inspecting the directories of both phones it was evident that no file (*.m3u) was downloaded.

Is this not possible from an android device? Any alternative browsers? Do the browser settings need to be adjusted? Thanks!

---

### Post by geekyhawkes on 2010-08-30
I dont think its limited to android, I have a htc HD2 running windows mobile 6.5 and i have pretty much the same problem.  I think it must be related to the way mobile browsers pass the request to mythweb?

---

### Post by tmcgary on 2010-08-30
I know nothing of writing scripts or coding. However that being said I love to tinker:

If it is a problem with how mythweb is interpreting requests from mobile browsers, is there a way to examine if there is a string or identifying mark within the mobile browser's query for mythweb to pick up on? If so, is there a file (includes?) in mythweb that could be altered to dictate how it behaved in the presence of these requests? 

This could be applied beyond myth music and could work for the mythvideo solution proposed by jlagrlone here, [http://ubuntuforums.org/showthread.php?t=1521188](http://ubuntuforums.org/showthread.php?t=1521188)

Sorry for the vague conceptual talk, its about all I can contribute. Thanks for any help!

PS. Is there any other alternative software for this use that would play nicely along side mythbuntu that may be more effective? I have read a bit about gnump3d but that seems to not be supported anymore and I cant find much about its recent efficacy.

---

### Post by tmcgary on 2010-09-02
I downloaded google's Android SDK emulator and am fumbling around trying to use it to troubleshoot this issue.

I tried to use this workaround: [http://www.mobilecrunch.com/2010/05/24/how-to-watch-hulu-on-android-2-2/](http://www.mobilecrunch.com/2010/05/24/how-to-watch-hulu-on-android-2-2/) and it didnt work in the emulator. If someone tried it on their android device and tried to connect to their mythweb that would be super; using hulu doesnt work according to the comments below the tutorial in that link. It seems to work for some people in mythweb as detailed here: [http://flowplayer.org/forum/5/42450](http://flowplayer.org/forum/5/42450).

I was able to use the emulator to connect to my own mythweb over the internet. The emulator behaves as previously mentioned when trying to use mythmusic. When using mythvideo (altered as detailed here by jlagrone [http://ubuntuforums.org/showthread.php?t=1521188](http://ubuntuforums.org/showthread.php?t=1521188)) the emulator's browser returns the following error, "bad request your browser sent a request that this server could not understand." This would be consistent with geekyhawkes hypothesis.

Is there a way to get a debug from the server (i.e. the mythweb computer) to pinpoint the error? If so, how would I view this file? Would this be a apache debug? I don't have a ton of experience invoking the different debug logs, so please be pretty explicit in describing how to bring up the debug log.

---

### Post by tmcgary on 2010-09-02
Interesting development:

When using the WAP skin on mythweb during access by my Windows client PC, the same thing occurs in mythmusic: after pressing "play" nothing happens. So this isn't limited to android at all. 

This may not be the right terminology, but I am a layman when it comes to the behind-the-scenes heavy lifting: 

Is there a way to examine the 'coding' that dictates how mythweb hands WAP browser requests? Is there a way to remove the WAP designation all together to ensure mythweb handles all queries as if they were a non-mobile computer? Thanks!

---

### Post by tmcgary on 2010-09-10
To anyone following this thread:

I tried this solution to turn off WAP settings [http://ubuntuforums.org/showthread.php?t=915812&highlight=WAP+settings](http://ubuntuforums.org/showthread.php?t=915812&highlight=WAP+settings). However, both android on verizon droid and sprint evo did not work. When the links were clicked the page appears to try to refresh, then nothing.

Any more thoughts?

---

### Post by nickfoti on 2010-09-11
Quick thought to add, I'm not sure how all the post processing goes down - but using Fennec (firefox mobile) on the Captivate, clicking play from the mythweb music screen downloads a file called mp3act_hidden.php. 

Fennec is not able to open the file - meaning, I guess, that the m3u file is never created.

Saving it gave me this file, which - I'm guessing, is used to create the playlist

The contents of the file:

```
#EXTM3U
#EXTINF:181,Keb' Mo' - Every Morning
http://myurl.com/mythweb/music/stream?i=385
```

Don't know if that helps...

---

### Post by tmcgary on 2010-09-12
nickfoti,

that could be useful. Have you tried cutting and pasting the URL into VLC on a computer to see if its a fully functional link? If so, did it work? If that URL is good, a quick fix would be cutting and pasting the URL into an appropriate media player on one's smartphone. Does anyone know of a media player app that allows for URL input like VLC does?

Not ideal for listen to a long music playlist, but for streaming movies might be useful. Thanks for the information!

---

### Post by nickfoti on 2010-09-12
The URL works fine, I use the feature with my laptop all the time.

I came across this app, looks promising:

[http://www.streamfurious.com/](http://www.streamfurious.com/)

Apparently, the paid version allows for playing custom network urls....

---

### Post by paoleary on 2010-09-15
I've been quite happy with [Subsonic]("http://www.google.com/url?sa=t&source=web&cd=1&ved=0CBUQFjAA&url=http%3A%2F%2Fsubsonic.sourceforge.net%2F&rct=j&q=subsonic&ei=qEiQTKqHJ4T58Aayoaz-DQ&usg=AFQjCNEVxqwMRsWzJ6Pjd2inVscAGxsX2w&sig2=9RuNSpNIoppRE2rPHA6RJg&cad=rja"), which also has a separate Android app available on the Market.  (Unfortunately, unlike the server the Android client is not GPL.)  While the developer requests a donation to "unlock" the server, since source code is available this is not a problem__ in practice (w/a little digging.)

You will probably have to mess with transcode settings due to limitations in the stream types understood by Android, which as far as I know is still limited to mp3 streams for audio.  While Vorbis is the Android "native" audio format, it's inexplicably not streamable.  That's all configurable from the web interface.

The Subsonic server exposes its own Tomcat web server on a different port, so you might want to [set up a reverse proxy]("http://www.activeobjects.no/subsonic/forum/viewtopic.php?t=1569") for it in Apache, particularly if your employer requires HTTP to be on port 80.

---

### Post by tmcgary on 2010-09-16
paoleary,

have you had any luck with subsonic streaming video? I am looking for a streaming solution that could do both. Thanks!

---

### Post by paoleary on 2010-09-17
@tmcgary:  I've never tried it, and I don't believe it's supported by the mobile apps.

---

### Post by neillo on 2010-12-23
Don't know if it is relevant to this thread, but I was annoyed that vlc asked for username and password for each song, so I changed my php file like so:

```
/usr/share/mythtv/mythweb/modules/music$ diff handler.php handler.php.bak
45c45
<         return 'http://user:pass@101.102.103.104/mythweb/music/';
---
>         return root_auth_url.'music/';
```

I realize this is ugly [kludge, I believe is the term].  I probably should have traced back the url string further, but didn't want to break other portions of mythweb, and I have a static IP so it works.  Probably a security nightmare, but it beats typing a user and pass for each song.  Maybe this could help a smartphone authenticate if that is the problem?

---

### Post by newlinux on 2010-12-23
for whatever it's worth in this thread, I use ampache along with the droid app "amdroid" and can access all my music and playlists setup on ampache from pretty much anywhere using my motorola droid, droid 2, and hacked droid tablet. the web interface works well too. I love using ampache.

Good app to look into since there is already an app to interface to it on android.

---

