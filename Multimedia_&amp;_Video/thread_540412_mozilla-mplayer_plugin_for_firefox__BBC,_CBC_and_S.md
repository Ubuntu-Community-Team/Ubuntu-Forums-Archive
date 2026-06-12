---
title: "mozilla-mplayer plugin for firefox:  BBC, CBC and Stage6 streaming videos micro-howto"
date: 2007-09-01
forum: Multimedia &amp; Video
---

### Post by ariel on 2007-09-01
**[Updated for Hardy]**

After a long time using the feature-less VLC-Plugin, and messing things up with the MediaPlayerConnectivity plugin to open lots of stand-alone VLC windows every time I wanted to watch BBC or CBC News videos, I finally got the Mplayer plugin to work fine and play all those embedded videos with no stuttering or annoyances.

[COLOR=Blue]**Hardy Heron (8.04) **[/COLOR](for previous versions, scroll to the bottom of this post)

While Stage6 does not exist anymore, the daily BBC News Videos are still a challenge for Ubuntu. Out of the box, Hardy cannot play them. Even after installing hardy's restricted codecs (which we will do below), they do not work past the BBC corporate announcement, and even that takes about half a minute to start playing back. 

We will fix the problem by reconfiguring Firefox to use the Mplayer plugin, installing the restricted codecs (to ensure windows media plays) and later installing the Real Video codecs from the Medibuntu repo. Finally, we will set the BBC News site preferences to stream Real Video. The end result will be: BBC news video play nicely and start very fast, plus all other sites to windows media or flash streaming work fine as well.


**     First part: the mplayer plugin and the basic codecs**[LIST=1]
[*]Close your Firefox
[*]Remove the plugins you will no longer be using:
```
sudo apt-get remove totem-mozilla mozilla-plugin-vlc
```
[*]Install the awesome mplayer plugin:
```
sudo apt-get install mozilla-mplayer
```
[*]Now let's install all the mp3, wm codecs, adobe flash player and some other useful stuff, all this from the official "universe" repository
(note: if you don't know what I am talking about, open your Synaptics package manager, go to Settings > Repositories, and ensure that the lines that contain "(universe)" and "(multiverse)" are checked; if have to check them, ensure that after clossing the settings window, you click on "Reload" in Synaptics main window)
```
sudo apt-get install ubuntu-restricted-extras
```[/LIST][B]
     Second part: real video codecs
[/B]     For this, we will use the medibuntu repository. We will add to the repo list, and then import their keys.[LIST=1]
[*]Edit /etc/apt/sources.list
```
sudo gedit /etc/apt/sources.list
```
[*]Append the following lines to it:
```
## Medibuntu - Ubuntu 8.04 "hardy"
deb  http://packages.medibuntu.org/ hardy free non-free
```
[*]Import medibuntu's key and update the local package list
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
[*]Now install the codec we need:
```
sudo apt-get install non-free-codecs
```[/LIST][B]
Third part: setting up BBC News site preferences[/B][LIST=1]
[*]Launch firefox and navigate to the BBC News site: [http://news.bbc.co.uk/](http://news.bbc.co.uk/)
[*]Click on one of the [watch] buttons of the daily news videos they happen to be offering
[*]In the new window that will pop up, you will notice a "Preferences" link; click on it
[*]This will show you the preferences; select "High Quality" on the left column, and "Real Media" on the right column; click OK; configuration will be stored persistently in your system
[*]The video should start playing right away![/LIST][B]
Optional[/B][B]: extra tweakings for the mplayer plugin
[/B]Some extra settings you can play with to improve the user experience[LIST]
[*]While playing an streaming video in firefox (e.g., any of the BBC ones), right click on the video, then select "Configure"; for your reference, my settings here are:[LIST]
[*]Video Output = xv
[*]Audio Output = alsa    ## also works with "pulse", if you have pulseaudio set up
[*]Minimum Cache Size = 191
[*]Percent of Media to Cache = 2
[*]All "Enable xyz" settings are checked
[*]Connect RTSP over TCP: un-checked (although I've read elsewhere that some sites may require this)[/LIST] 
[*]For more options, you can open the mozilla-mplayer plugin configuration file directly:
```
sudo gedit /etc/mplayerplug-in.conf
```Here, I set the following extra options:
showlogo=0
black-background=1[/LIST][I]
That's all, hope this helps reduce the "video streaming woes and frustration" with ubuntu.
[/I]



[COLOR=Blue]**Feisty  and Edgy ****(7.04, 7.10)**[/COLOR] (Not updated; left here for reference purposes only)

The following is for Feisty but I guess it works in other versions and distros as well.

It was (way!) simple. My original problem with mozilla-mplayer was that it simple kept "stuttering" with BBC and CBC streaming videos. 

Here's how to install it and configure it, and with the same stone, get embedded Div-X streaming videos from stage6.divx.com to work stunningly well. And also get your plugin to look good...[LIST=1]
[*]Close your Firefox
[*]Remove the plugins you will no longer be using:
```
sudo apt-get remove totem-mozilla mozilla-plugin-vlc
```
[*]Install the awesome mplayer plugin:
```
sudo apt-get install mozilla-mplayer
```
[*]Feisty (7.04) Users: Add these symlinks that enable the plugin to handle Stage6's DIVXs (7.10 users: the symlinks should already be there if you did a fresh install; if not, just add them)

```
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so /usr/lib/firefox/plugins/mplayerplug-in-dvx.so
``````
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt /usr/lib/firefox/plugins/mplayerplug-in-dvx.xpt
```
[*]Configure the plugin to with approriate Buffer / Cache size; this fixes the BBC / CBC windows media stream stuttering

Open the config file:

```
sudo gedit /etc/mplayerplug-in.conf
```Add the following lines in the file: (this works great in my system; you might have to do some tuning of the cachesize and cache-percent)

cachesize=1000
cache-percent=30
download=0
showlogo=0
black-background=1
[*]Start your browser, check your new setup in [www.cbc.ca]("http://www.cbc.ca") and Stage6
[*]Enjoy!![/LIST]Note: You might need to setup the BBC News site to stream windows media to you, instead of RealMedia; you can do this easily, after the above setup is completed:[LIST]
[*]Go to: [http://news.bbc.co.uk/](http://news.bbc.co.uk/)
[*]Open a video (for example, the 1-minute day news headlines)
[*]In the new window, you will notice a "Preferences" link; click on it
[*]This will open a window that will let you choose "Windows Media" instead of Real Media; select it, and close; configuration will be stored persistently in your system[/LIST]

---

### Post by anthortic on 2007-09-04
that mini guide worked well, thanks

---

### Post by chrome307 on 2007-09-04
The BBC site worked for me great, but had problems with playback from the Canadian site .......... not sure why .... only available to Canadian IP addresses ??

The DivX 6 playback worked great here :)

```


http://stage6.divx.com/TV-Jungle-Music-Videos/video/1110653/Blondie---Heart-of-Glass-


```

---

### Post by ariel on 2007-09-04
> **chrome307 said:**
> The BBC site worked for me great, but had problems with playback from the Canadian site .......... not sure why .... only available to Canadian IP addresses ??

The DivX 6 playback worked great here :)

```


http://stage6.divx.com/TV-Jungle-Music-Videos/video/1110653/Blondie---Heart-of-Glass-


```

Possibly! Some video content in the local BBC channels seems to be blocked as well. BBC World has always worked fine for me though

---

### Post by mithranruin on 2007-09-10
I have had real problems with BBC streaming video until finding your solution - which worked 'out of the box' - Thankyou :) 

As a newbie to Ubuntu (a refugee from the big 'M'), can anyone tell me :

- what each of the settings in the mplayerplug-in.conf file alters and which are important 
- I presume the # needs to be removed from the beginning of each line

Whilst the solution works, a couple of questions please:

1) in my display the video is 'squashed' into the top 2/3rds of the display area - and no changes to the .conf settings seems to alter this (normal/expected?)

2) the video plays well and steady but still seems a little 'blocky' (normal/expected?)

Gratefully
mithranruin

---

### Post by ariel on 2007-09-13
Hey there, 

  you can find an explanation of the plugin config options here:

[http://mplayerplug-in.sourceforge.net/config.php](http://mplayerplug-in.sourceforge.net/config.php)

You should normally leave the "#" you found in your original config file as they are. "#" means "commented out", which means that the configuration line will be taken as a comment, and not processed.

In my system, the "1/3" problem you mention only shows up when going back to normal size after maximizing to full screen

I don't seem to see any 'blockiness' with mplayer. It seem to play exactly the same as stand alone vlc.


> **mithranruin said:**
> I have had real problems with BBC streaming video until finding your solution - which worked 'out of the box' - Thankyou :) 

As a newbie to Ubuntu (a refugee from the big 'M'), can anyone tell me :

- what each of the settings in the mplayerplug-in.conf file alters and which are important 
- I presume the # needs to be removed from the beginning of each line

Whilst the solution works, a couple of questions please:

1) in my display the video is 'squashed' into the top 2/3rds of the display area - and no changes to the .conf settings seems to alter this (normal/expected?)

2) the video plays well and steady but still seems a little 'blocky' (normal/expected?)

Gratefully
mithranruin

---

### Post by stolid_agnostic on 2007-09-19
this worked absolutely perfectly!!! thanks so much!

---

### Post by andrew.46 on 2007-09-24
Hi,

 You are an absolute legend! It all worked perfectly for me and complements my brand new svn mplayer:

[http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)

 Is there much new in the newest mplayer plugin released a month or so ago?

           Thank you *very much *for this!

                       Andrew

---

### Post by ariel on 2007-09-26
@Andrew: you are welcome!

On the new release of mplayerplug-in available in sourceforge: I couldn't help but download it / compile it / install it a few weeks ago. It sort of works but had a few quirks:
   - After playing at full screen for a while, suddenly the browser window un-full-screened itself, on its own. big annoyance
   - the new version showed a speaker icon, but in my system it was not operational.
   - CBC videos behaved weirdly.

In summary: I had to roll back to Feisty's default plugin package.

---

### Post by aleksanderffs on 2007-09-27
Thanks for this :D really missed stage6

---

### Post by pakku on 2007-09-29
After I do all this both on the CBC and the BBC site when I click on a video link I get a series of  messages of the type
Playing mms:// a series of letters and numbers"
Buffering mms://a series of letters and numbers
Connecting to server series of letters and numbers
Connected

But no video.

Any thoughts?

The site works well enough on the same PC in XP (it is a dual boot) so I am loath to blame it on hardware

---

### Post by hums07 on 2007-10-06
> **pakku said:**
> After I do all this both on the CBC and the BBC site when I click on a video link I get a series of  messages of the type
Playing mms:// a series of letters and numbers"
Buffering mms://a series of letters and numbers
Connecting to server series of letters and numbers
Connected

But no video.

The site works well enough on the same PC in XP (it is a dual boot) so I am loath to blame it on hardware

I v got the same problem here. Just a series of messages and sometimes a burst of sound.

---

### Post by mindtrick on 2007-10-08
Great guide. Totem's plugins were problematic.

---

### Post by gyterpena on 2007-10-12
Hi is there any way how to use vlc plugin together with mplayer. I need vlc just for one site (IPTV from my ISP).

---

### Post by Cyfr on 2007-10-17
CBC works fine, but when I try and use BBC videos it just hangs at connecting to the server..

I use a VPN to connect to your freedom proxy but that should be fine? Every other application just works out the box and it worked fine when I used your freedom on my mac..

---

### Post by a13kurt on 2007-10-18
I've followed you're walk through, and still I've had no luck. 

I used the about:plugins command in firefox and found out that it doesn't recognize a divx plug-in. I checked the /usr/lib/firefox/plugins folder and the mplayerplug-in-dvx.so and the mplayerplug-in-dvx.xpt files are there.

I went to a web site and played a video and right clicked it to check the configuration. The box for Enable Divx Support is checked.

Also, in the /usr/lib/firefox/plugins folder the link for mplayerplug-in-gmp.so and mplayerplug-in-gmp.xpt files report a broken link. I'm not sure if this is relevant to my problem but I thought I'd throw that in there.

Any other ideas?

---

### Post by ariel on 2007-10-20
the first question would be, are you planning to upgrade to Gutsy soon? 

because if you do, then everything becomes much easier. If you do a fresh install, you get the Totem-plugin installed by default, but still can't play divx (hold on...)

After the fresh install, go to Applications > Add Remove, then search for "Restricted", when the search is complete, check "Ubuntu Restricted Extras", this will install all required codecs including divx and a bunch of other useful stuff (Sun Java, adobe flash player)

After that, you need to reboot the machine (not sure if a logout is enough); then you can enjoy stage6 right out of the box with no tweakings.

---

### Post by shouravv on 2007-10-21
The BBC audio used to work perfectly fine with me until updating to Gutsy, but now nothing plays ... I have followed your instructions and found that I already have mozilla mplayer set up. I enabled Ubuntu Restricted Extras and rebooted, but that doesn't help either. Any suggestion?

Audio simply won't play, clicking on video links show a bunch of messages and then says "stopped". Occasionally it plays an advertisement and then stops.

---

### Post by indrajeetak on 2007-10-21
> **chrome307 said:**
> The BBC site worked for me great, but had problems with playback from the Canadian site .......... not sure why .... only available to Canadian IP addresses ??

The DivX 6 playback worked great here :)

```


http://stage6.divx.com/TV-Jungle-Music-Videos/video/1110653/Blondie---Heart-of-Glass-


```

The BBC site worked great for me too. However, when I played the Blondie video on stage6, it plays smoothly for a few seconds and then starts buffering as shown below.
[IMG]http://img88.imageshack.us/img88/355/screenshotiw2.jpg[/IMG]
When buffering reaches 100%, the screen goes all white.

Does anyone have any idea? Thanks for your time....

---

### Post by SIGINT23 on 2007-10-24
What does your /etc/mplayerplug-in.conf look like? Just posted it here!

---

### Post by bw44 on 2007-10-24
> **ariel said:**
> After a long time using the feature-less VLC-Plugin, and messing things up with the MediaPlayerConnectivity plugin to open lots of stand-alone VLC windows every time I wanted to watch BBC or CBC News videos, I finally got the Mplayer plugin to work fine and play all those embedded videos with no stuttering or annoyances.

The following is for Feisty but I guess it works in other versions and distros as well.

(see author's clear how-to instructions at: [http://ubuntuforums.org/showthread.php?t=540412&highlight=totem-plugin](http://ubuntuforums.org/showthread.php?t=540412&highlight=totem-plugin))



Your post was really  instructive. I followed all your instructions and am getting much farther than I did with the totem plugin.

Thanks.

---

### Post by shouravv on 2007-10-24
> **SIGINT23 said:**
> What does your /etc/mplayerplug-in.conf look like? Just posted it here!

#vo=xv,x11
#ao=arts,esd,oss
#download=1
#dload-dir=$HOME/tmp
#keep-download=0
#noembed=0
#cachesize=512
#use-mimetypes=0
#enable-ogg=1
#enable-smil=1
#enable-helix=1
#qt-speed=med
#rtsp-use-tcp=0
#nomediacache=0
#framedrop=0
#autosync=0
#mc=1
#black-background=0
#user-agent=NSPlayer
cachesize=1000
cache-percent=30
download=0
showlogo=0

Initially only the commented out lines existed. I laster added the last 4 lines.

Thank you in advance for your help.

---

### Post by ariel on 2007-10-24
Since you are using gutsy, if I were you I'd try and remove the mplayer plugin, and install totem-gstreamer and totem-mozilla (this is the mozilla plugin), then i'd reboot.

this should leave your stage6 and cbc sites working. For the bbc, I found that the I had to set "standard quality" as opposed to "high quality" (bigger image) in the Preference section in the bbc's popup. Mplayer-plugin may work better that totem in this case; however I like the new totem-mozilla better for stage6.

cheers

---

### Post by shouravv on 2007-10-25
Problem solved:

I removed the mplayer-mozilla plugin, then added the totem-mozilla and xine-plugin packages. And it works!

I am not sure if I even need the totem-mozilla plugin at all, the xine-plugin package seems pretty independent. The totem stuff may be necessary if you want to launch video on a standalone player from within Firefox but again, I am not yet sure.

Thanks everyone!

---

### Post by indrajeetak on 2007-10-25
> **ariel said:**
> Since you are using gutsy, if I were you I'd try and remove the mplayer plugin, and install totem-gstreamer and totem-mozilla (this is the mozilla plugin), then i'd reboot.

this should leave your stage6 and cbc sites working. For the bbc, I found that the I had to set "standard quality" as opposed to "high quality" (bigger image) in the Preference section in the bbc's popup. Mplayer-plugin may work better that totem in this case; however I like the new totem-mozilla better for stage6.

cheers

I use Gutsty and had trouble with mplayer and so I followed your suggestion and took it off. I then installed the totem plugins. However, the stage6 videos are still troubling me. The first few seconds play smoothly and then the video jumps from frame to frame with no sound.

Any ideas?...

---

### Post by ariel on 2007-10-25
> **indrajeetak said:**
> I use Gutsty and had trouble with mplayer and so I followed your suggestion and took it off. I then installed the totem plugins. However, the stage6 videos are still troubling me. The first few seconds play smoothly and then the video jumps from frame to frame with no sound.

Any ideas?...


Try increasing the buffer; if you're using the mplayer plugin, increase the cache-percent, and if necessary the cachesize. It will take longer to start playing but it should tolerate more network jitter. 

You should also note that some high-def videos in divx require a *lot* of downtream BW to be able to properly stream; I have a 4mbps connection and even so I ran a few times into BW limitations with 1080p content (I think it requires 6Megs). Most of stage6 content can be streamed down a 1.5 mbps pipe just fine. But in cases where the pipe is not wide enough, you will run into the problem that only the initial buffered segment is played properly, and then the player stops, rebuffers, plays, and so on.

---

### Post by bw44 on 2007-10-25
> **shouravv said:**
> #vo=xv,x11
#ao=arts,esd,oss
#download=1
#dload-dir=$HOME/tmp
#keep-download=0
#noembed=0
#cachesize=512
#use-mimetypes=0
#enable-ogg=1
#enable-smil=1
#enable-helix=1
#qt-speed=med
#rtsp-use-tcp=0
#nomediacache=0
#framedrop=0
#autosync=0
#mc=1
#black-background=0
#user-agent=NSPlayer
cachesize=1000
cache-percent=30
download=0
showlogo=0

Initially only the commented out lines existed. I laster added the last 4 lines.

Thank you in advance for your help.

I'm no expert, but I have struggled long and hard to get the BBC (and Canadian CBC) video clips to work with Firefox under Feisty.  Below are the settings that work well for me.  They include the ones that Ariel originally recommended be added to  /etc/mplayerplug-in.conf (the last four lines in your example).

As explained on their website [http://mplayerplug-in.sourceforge.net/config.php](http://mplayerplug-in.sourceforge.net/config.php) the mplayer plug-in takes it's values from from three files: the ones from /etc/mplayerplug-in.conf are overwritten by ones in two other files.  The first is $HOME/.mozilla/mplayerplug-in.conf (which doesn't exist on my system), and the second is $HOME/.mplayer/mplayerplug-in.conf.  You can edit the latter file manually, OR, you can configure settings from the display area of the plugin while it's running:  right click on the display area and you should see something like the attached screenshot.  When you modify values and click OK they are stored in $HOME/.mplayer/mplayerplug-in.conf.  The values shown in the screenshot are the ones that work for me. (I disabled some that probably don't need to be disabled, so you should experiment, if you need RealPlayer, for example.)  

The KEY values (again, in my experience) were the "Video Output" and "Audio Output" ones.  Until I specified VO=gl and AO=esd I could not get the clips to play properly.  Now they work just as well, though a little slower, than with Windows/XP/Firefox/WMP.  

I hope this helps.  As Ariel has pointed out you may need to adjust the minimum cache size and percent to cache values.  I originally thought "more was better" and had values as high as 10000 for the minimum cache size;  256 seems to work just as well.

Good luck.

---

### Post by krt on 2007-10-25
Well, I have followed the instructions at the start of this thread, and like some others, I still cannot get anything other than bursts of noise and no video at the BBC in Feisty . . .

Also, at the National Zoo Panda Cams, part of the time I can get the live cams, yet I cannot seem to get the stored video clips to work; they appear to load, and then I get an error message and the clip never runs. Look at the site: [http://nationalzoo.si.edu/Animals/GiantPandas/](http://nationalzoo.si.edu/Animals/GiantPandas/)

krt

---

### Post by bw44 on 2007-10-26
> **krt said:**
> Well, I have followed the instructions at the start of this thread, and like some others, I still cannot get anything other than bursts of noise and no video at the BBC in Feisty . . .

Also, at the National Zoo Panda Cams, part of the time I can get the live cams, yet I cannot seem to get the stored video clips to work; they appear to load, and then I get an error message and the clip never runs. Look at the site: [http://nationalzoo.si.edu/Animals/GiantPandas/](http://nationalzoo.si.edu/Animals/GiantPandas/)

krt

Did you try configuring things as I suggested in my last post?  No guarantees (your milage may vary), but I was able to connect to the site you mention and view  both the live cams and the video clips. (Nice site!) They *are* slow to load (via my DSL link rated at 512KB), and the quality is not very good, but they do play.

Can you post the settings in your $HOME/.mplayer/mplayerplug-in.conf file ? I'm only learning, too, but maybe I can spot something that would help fix the problem.

---

### Post by krt on 2007-10-27
Well, I finally had the time to mess around with this again, and I have my mplayer set up like you said:

$ cat /etc/mplayerplug-in.conf
#debug=0
#vo=xv,x11
#ao=arts,esd,oss
#download=1
#dload-dir=$HOME/tmp
#keep-download=0
#noembed=0
#cachesize=512
#use-mimetypes=0
#enable-ogg=1
#enable-smil=1
#enable-helix=1
#qt-speed=med
#rtsp-use-tcp=0
#nomediacache=0
#framedrop=0
#autosync=0
#mc=1
#black-background=0
#user-agent=NSPlayer
cachesize=1000
cache-percent=30
download=0
showlogo=0

And I am continuing to have problems . . . Still does not work!

Thanks,

krt

---

### Post by bw44 on 2007-10-31
> **krt said:**
> Well, I finally had the time to mess around with this again, and I have my mplayer set up like you said:

$ cat /etc/mplayerplug-in.conf
#debug=0
#vo=xv,x11
#ao=arts,esd,oss
#download=1
#dload-dir=$HOME/tmp
#keep-download=0
#noembed=0
#cachesize=512
#use-mimetypes=0
#enable-ogg=1
#enable-smil=1
#enable-helix=1
#qt-speed=med
#rtsp-use-tcp=0
#nomediacache=0
#framedrop=0
#autosync=0
#mc=1
#black-background=0
#user-agent=NSPlayer
cachesize=1000
cache-percent=30
download=0
showlogo=0

And I am continuing to have problems . . . Still does not work!

Thanks,

krt

Really sorry I took so long to get back to you -- somehow I managed to turn notification off, so I didn't see your post until I checked the forum.

The list you show above has a number of (to me) important items commented out at the beginning of the lines with #.   But before you start un-commenting things, take a look at the file /home/your_user_name/.mplayer/mplayerplug-in.conf.   This file should exist and contain a  similar list to the above but without things commented out.  The values in this file will override the ones in /etc/mplayerplug-in.conf . Here is what mine shows:

vo=x11
ao=alsa
cachesize=4096
cache-percent=50
dload-dir=/home/bob
showtime=1
enable-wmp=1
enable-qt=1
enable-rm=1
enable-gmp=1
enable-dvx=1
enable-mpeg=1
enable-mp3=1
enable-ogg=1
enable-midi=0
enable-pls=1
enable-smil=1
enable-helix=1
nomediacache=0
nopauseonhide=1
rtsp-use-tcp=0
rtsp-use-http=1

These are the values that are set when you right click on the mplayer display window in your browser and select the "Configure" button. (They are shown in the screenshot attached to my earlier post).  Note, I have changed some of the values I posted before, because not everything is working well for me either. I've been trying different values.  The settings you see above make it possible for me to view the PandaCam site you mentiioned, as well as the shorter BBC and CBC video clips.  I am still having problems with long clips: but my PC is memory constrained and I only have a 512KB DSL link. After a couple of minutes of clear viewing the long video clips start to "stutter."

Try altering the values to those shown above (or cut and paste them into /home/your_user_name/.mplayer/mplayerplug-in.conf).  Of course I can't guarantee they will work for you  (No two computer systems are identical!).

Good luck and let us know what works for you!

---

### Post by lenninct on 2007-11-03
you are my hero....

---

### Post by theonhighgod on 2007-11-04
im using gusty, i did exactly as said at the beginning of the thread, it wasn't necessary to make the two links (they already existed) changed the options and all but the live feeds seem to work fine:) im really pleased,

thanks

p.s. just in case theres a difference im using amd64 version

---

### Post by stephenk on 2007-11-07
thanks, but how do I open the stream in a stand alone player - previously, there was a right click option to do this

---

### Post by emacsuser on 2007-11-07
Go to stage six and it still don't work, am I missing some codec ? Trying to play a rtsp stream in the standalone mplayer gets the same results ...

rtsp://rm-acl.bbc.co.uk/drama/robinhood/bb/ep6preview_16x9_bb.rm?BBC-UID=f4e76341cc2fccb818e3b8c2c19aec7aed9b99c66030e1e623d5

---

### Post by Voyageur on 2007-11-08
This works great for me in Stage6. However on BBC attempts, media player keeps attempting to open RealPlayer. Even though I have selected Windows Media in preferences.
Any ideas how to switch this link off?

---

### Post by indie56 on 2007-11-11
Hello
I have followed the instructions here. The mplayer goes through a series of CONNECTING and then stops.
Pl help

---

### Post by ariel on 2007-11-14
> **Voyageur said:**
> This works great for me in Stage6. However on BBC attempts, media player keeps attempting to open RealPlayer. Even though I have selected Windows Media in preferences.
Any ideas how to switch this link off?

@voyageur: you most probably have either the real player plugin or helix plugin installed, try removing it and reinstalling mozilla-mplayer (or totem mozilla plugin)

---

### Post by ariel on 2007-11-14
> **stephenk said:**
> thanks, but how do I open the stream in a stand alone player - previously, there was a right click option to do this

For stage6 in 7.10 & using totem (just the default fresh install), after you click play and the video starts, right click on it and select open in standalone player.

---

### Post by ariel on 2007-11-14
> **emacsuser said:**
> Go to stage six and it still don't work, am I missing some codec ? Trying to play a rtsp stream in the standalone mplayer gets the same results ...

rtsp://rm-acl.bbc.co.uk/drama/robinhood/bb/ep6preview_16x9_bb.rm?BBC-UID=f4e76341cc2fccb818e3b8c2c19aec7aed9b99c66030e1e623d5

In 7.10, you can ensure you have the required codecs by installing this package: "ubuntu-restricted-extras". In most cases this shouldn't break anything, but be aware it installs Sun's java a few other things you probably want anyways (ms fonts comes to mind).

---

### Post by ubuntu-freak on 2007-11-16
I posted a similar fix here [http://forums.debian.net/viewtopic.php?t=21315](http://forums.debian.net/viewtopic.php?t=21315) mainly for people using destop effects on an intel based card and having the 'black window' mplayer plugin problem while streaming. I found having no # (comments) was the only way I got it working properly.  Even if your plugin is working it will improve it's performance as autoplay is switched off. Also, if you are using the x11 driver add zoom=1 or "1" to your home/.mplayer conf file. Hope that helps. Nathan.

---

### Post by Kramxel on 2007-11-21
Thanks for the guide....

I've finally been able to put the mozilla mplayer plugin to work almost properly....

Before I had a lot of codecs all conflicting with one another.... totem mplayer realplayer

Now that's all fixed...

My problem is with Stage6... When I try to play a video it buffers fine and the sound is perfect, the only bugger is that the video plays in slow motion.... incredibly slow speed...

I've set video output to x11 and audio to alsa....

Divx playback is the only problem I've found so far...


Thanks in advance...

---

### Post by bw44 on 2007-11-21
> **ariel said:**
> Since you are using gutsy, if I were you I'd try and remove the mplayer plugin, and install totem-gstreamer and totem-mozilla (this is the mozilla plugin), then i'd reboot.

this should leave your stage6 and cbc sites working. For the bbc, I found that the I had to set "standard quality" as opposed to "high quality" (bigger image) in the Preference section in the bbc's popup. Mplayer-plugin may work better that totem in this case; however I like the new totem-mozilla better for stage6.

cheers
@Ariel,

I've been using mplayer plugin with Firefox 2.0.0.8 under Feisty and was able to view BBC clips without major problems; the Smithsonian Panda site worked well; but the CBC news site was touch and go. ([http://news.bbc.co.uk/](http://news.bbc.co.uk/)  [http://www.cbc.ca/ondemand/news/thenational.asx](http://www.cbc.ca/ondemand/news/thenational.asx)            [http://nationalzoo.si.edu/Animals/GiantPandas/default.cfm?cam=PC1](http://nationalzoo.si.edu/Animals/GiantPandas/default.cfm?cam=PC1))
           
I just upgraded to Gutsy, with the following results:  CBC video clips worked flawlessly; Panda clips were OK; but the BBC video clips weren't video any more (sound only).  I played around with the mplayer plugin settings but could not get the BBC clips to display.  

From your post I gather you feel that totem does a better job than mplayer under Gutsy (could you please comment on why?).  So I removed mplayer and its mozilla plugin and installed totem-mozilla and totem-gstreamer.  The totem plugin launches for the various video sites but never displays anything, nada (except the totem stylized screen frame).   I tried installing totem-xine (which forced the uninstall of totem-gstreamer), but this did not change anything.

Before I remove totem and re-install mplayer, could you offer any suggestions as to what I may be overlooking.  (I did not install the Ubuntu-restricted-xtras -- I'm not sure what Stage6 is and didn't think I needed it for  viewing the sites I mentioned above.) 

Also, are there totem plugin configuration settings similar to mplayer's?  If so, where do I find them?

Thanks in advance for any advice.

---

### Post by ariel on 2007-11-21
> **Kramxel said:**
> Thanks for the guide....

I've finally been able to put the mozilla mplayer plugin to work almost properly....

Before I had a lot of codecs all conflicting with one another.... totem mplayer realplayer

Now that's all fixed...

My problem is with Stage6... When I try to play a video it buffers fine and the sound is perfect, the only bugger is that the video plays in slow motion.... incredibly slow speed...

I've set video output to x11 and audio to alsa....

Divx playback is the only problem I've found so far...


Thanks in advance...

I believe that normally you would use XV as video sink, however 7.10's X has some problems in a few configurations that involve the 'intel' driver; unless you have one of those  I'd try XV and see what happens. I'd also try playing non-streamed divx and compare.

---

### Post by ariel on 2007-11-21
> **bw44 said:**
> @Ariel,

I've been using mplayer plugin with Firefox 2.0.0.8 under Feisty and was able to view BBC clips without major problems; the Smithsonian Panda site worked well; but the CBC news site was touch and go. ([http://news.bbc.co.uk/](http://news.bbc.co.uk/)  [http://www.cbc.ca/ondemand/news/thenational.asx](http://www.cbc.ca/ondemand/news/thenational.asx)            [http://nationalzoo.si.edu/Animals/GiantPandas/default.cfm?cam=PC1](http://nationalzoo.si.edu/Animals/GiantPandas/default.cfm?cam=PC1))
           
I just upgraded to Gutsy, with the following results:  CBC video clips worked flawlessly; Panda clips were OK; but the BBC video clips weren't video any more (sound only).  I played around with the mplayer plugin settings but could not get the BBC clips to display.  

From your post I gather you feel that totem does a better job than mplayer under Gutsy (could you please comment on why?).  So I removed mplayer and its mozilla plugin and installed totem-mozilla and totem-gstreamer.  The totem plugin launches for the various video sites but never displays anything, nada (except the totem stylized screen frame).   I tried installing totem-xine (which forced the uninstall of totem-gstreamer), but this did not change anything.

Before I remove totem and re-install mplayer, could you offer any suggestions as to what I may be overlooking.  (I did not install the Ubuntu-restricted-xtras -- I'm not sure what Stage6 is and didn't think I needed it for  viewing the sites I mentioned above.) 

Also, are there totem plugin configuration settings similar to mplayer's?  If so, where do I find them?

Thanks in advance for any advice.

I haven't tried the mplayer plugin under gutsy yet but I will at some point. I like the totem plugin because in full screen it has the auto-hiding time/playback bar (in mplayer the bar was either always on or always off), plus it is very easy to detach the playing video to an stand-alone totem window.

I also have the issues with  BBC videos: I had to turn BBC's streaming to windows media + Low Quality (smallish windows) to make it work; not sure if switching to mplayer would fix this or not; it used to work in feisty+mplayer though.

You can tweak totem-gstreamer stream caching parameters using gconf-editor; look for the these registry keys:

/apps/totem/network-buffer-threshold
/apps/totem/buffer-size

ps. for your no-video problem, I'd try and install the restricted-extras package; worst case it takes just one click to remove it again. I believe this package contains the windows media codecs that you need (besides the divx codecs that you don't need).

---

### Post by Kramxel on 2007-11-21
Thanks for your response ariel :)

My fullscreen problem was with all the media... not just divx...

I got it fixed by changing it to "vx" like you sugested.

I still had to do one litle tweak as I was having problem starting playback using "vx", so I used this:

noembed=1

in my  /etc/mplayerplug-in.conf

Problem solved!



To anyone interested in using "x11":

The only way I found out of working fullscreen with the "x11" option was to use:

framedrop=0

in my  /etc/mplayerplug-in.conf

But that made the fullscreen video quality very bad...

Now thanks to you I don't have to use it...


Many thanks ariel!

---

### Post by bw44 on 2007-11-22
> **ariel said:**
> I haven't tried the mplayer plugin under gutsy yet but I will at some point. I like the totem plugin because in full screen it has the auto-hiding time/playback bar (in mplayer the bar was either always on or always off), plus it is very easy to detach the playing video to an stand-alone totem window.

I also have the issues with  BBC videos: I had to turn BBC's streaming to windows media + Low Quality (smallish windows) to make it work; not sure if switching to mplayer would fix this or not; it used to work in feisty+mplayer though.

You can tweak totem-gstreamer stream caching parameters using gconf-editor; look for the these registry keys:

/apps/totem/network-buffer-threshold
/apps/totem/buffer-size

ps. for your no-video problem, I'd try and install the restricted-extras package; worst case it takes just one click to remove it again. I believe this package contains the windows media codecs that you need (besides the divx codecs that you don't need).

Thanks again for your help.  It's good to know where the totem parameters are. As it turns out the ubuntu-restricted-extras was already installed (apparently carried over from Feisty, though I don't actually remember installing it). Video clips worked well for me under Feisty with mplayer plugins for Firefox, which is why I was surprised they didn't under Gutsy.

I was also having problems with DVD movie playback and spent most of the day finding a solution to this problem.  To make a long story short it pays to read the manual: I followed the instructions on the following Ubuntu documentation page and can now play movies fine with both totem and mplayer: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu).  (see also [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats))  The key was to add the Medibuntu repository and install the libdvdcss2 and w32codecs to allow playing encrypted DVDs.

The reason I mention this here is that following these steps also seems to have solved the problems I was having with the BBC site videos.  They work very well with mplayer now, as do the other video clips.  I wish I could say for sure what solved the problem.  I haven't tried the totem mozilla plugins yet, so I can't say whether they work.  I read somewhere that there are problems with totem-gstreamer and that totem-xine is better. I'm using the latter for DVD playback, and it works well.

---

### Post by bw44 on 2007-11-23
> **ariel said:**
> . . . I also have the issues with  BBC videos: I had to turn BBC's streaming to windows media + Low Quality (smallish windows) to make it work; not sure if switching to mplayer would fix this or not; it used to work in feisty+mplayer though. . . .

It looks like this may be and issue of network connection speed and/or congestion at the BBC site.   I  tried running at the low quality setting with totem and it does work most of the time.  But just to let BBC know there are those of us who would like to be able to access their site with Linux, I sent them the following message:

> Can you offer any suggestions about problems when using Linux-based browsers to access BBC World News video clips?

I have tried to use the Firefox video streaming plug-ins for mplayer and totem and have had no problems accessing video clips at other sites on the Internet (e.g., cbc.ca and si.edu)  Neither plugin works successfully at your site, however.  With mplayer there is a complete lack of synchronization of audio and video, and sometimes video will not play at all. With totem, clips will usually play if I select "Standard quality" rather than "High quality" network connection and "Windows Media Player."  The results of your "Test My Connection Speed" consistently result in the message: "After testing your internet connection we believe you can receive high quality media.."

Obviously, these problems may both stem from the fact that my 512Kb "high speed" Internet connection is marginal. And this would suggest that your test for connection speed is overly optimistic. But why, then, would access to other sites work? I also observed that using the same browser and network connection with the WMP plug-in under Windows XP works consistently well at the "High quality" setting.

If someone in your technical support area could review and comment on this situation, I would post their answer on the Ubuntu forum, where a number of people have described frustration with  trying to access BBC videos.

Thanks very much.

If I get a helpful reply, I'll post it.

---

### Post by boyturtle on 2007-11-24
Hi there

I did this without fault on another computer, but now it doesnt want to play

When I try to get the mplayer plugin, this is what happens

> sudo apt-get install mozilla-mplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  mozilla-mplayer: Depends: mplayer (>= 1.0~pre5) or
                            mplayer-nogui but it is not going to be installed
E: Broken packages


Any ideas whats going on here?

---

### Post by ozorba on 2007-11-24
Followed the instructions. I can hear audio but there is no video! All I can see is the hyperlink text to the audio. Any suggestions?

TIA

---

### Post by ginestre on 2007-11-24
I think I've followed all of the instructions properly; but instead of getting BBC audio and video, in the playbox I just get a list of URLs, including BBC and others, and it tells me it's playing them. Which it doesn't. Any ideas?

---

### Post by bw44 on 2007-11-24
> **ozorba said:**
> Followed the instructions. I can hear audio but there is no video! All I can see is the hyperlink text to the audio. Any suggestions?

TIA

I'm not sure which instructions you mean -- there have been quite a few posts to this thread with instructions in them.

However, if you are describing a problem accessing the BBC site, I have tried both totem and mplayer plug-ins and with mplayer I often get the same result you describe: the audio downloads and plays, but the video doesn't.  Or I should say, the video downloads and won't play until I click the play arrow in the plugin controls. Then it plays the video erratically for a few seconds and stops.  With totem it just stops.  But both mplayer and totem will play most video and audio clips at other sites.

I have repeatedly run the BBC's connection speed test and it always says I should be able to use the "High quality" setting (under Preferences).  If I manually set the connection quality setting to the"Standard" setting, mplayer will successfully play the tiny illegible videos.  

I have no problem playing the video clips on the same machine (dual-boot) with Firefox, the WMP plugin under Windows XP, and with the "High quality" setting.  Three weeks ago I was able to play the videos under Feisty using mplayer; then I upgraded to Gutsy.  So which is it: a BBC problem (they've been adding video ads before the actual video clips); an mplayer (and totem!) problem; a Firefox problem; a Gutsy problem?  Probably a combination of more than one factor. It could even be that BBC tested their streaming with WMP and they made it work with something non-standard!  This could account for why both mplayer and totem can't play the BBC videos.  As I mentioned in a previous post, I've sent the BBC a couple of "comments" describing these problems, but I'm not very optimistic about getting an answer.

It's really maddening! ](*,)  If you read through earlier post you will see that Ariel said, "I have the [same]  issues with BBC videos."

---

### Post by ozorba on 2007-11-24
> **bw44 said:**
> I'm not sure which instructions you mean -- there have been quite a few posts to this thread with instructions in them.

However, if you are describing a problem accessing the BBC site, I have tried both totem and mplayer plug-ins and with mplayer I often get the same result you describe: the audio downloads and plays, but the video doesn't.  Or I should say, the video downloads and won't play until I click the play arrow in the plugin controls. Then it plays the video erratically for a few seconds and stops.  With totem it just stops.  But both mplayer and totem will play most video and audio clips at other sites.

I have repeatedly run the BBC's connection speed test and it always says I should be able to use the "High quality" setting (under Preferences).  If I manually set the connection quality setting to the"Standard" setting, mplayer will successfully play the tiny illegible videos.  

I have no problem playing the video clips on the same machine (dual-boot) with Firefox, the WMP plugin under Windows XP, and with the "High quality" setting.  Three weeks ago I was able to play the videos under Feisty using mplayer; then I upgraded to Gutsy.  So which is it: a BBC problem (they've been adding video ads before the actual video clips); an mplayer (and totem!) problem; a Firefox problem; a Gutsy problem?  Probably a combination of more than one factor. It could even be that BBC tested their streaming with WMP and they made it work with something non-standard!  This could account for why both mplayer and totem can't play the BBC videos.  As I mentioned in a previous post, I've sent the BBC a couple of "comments" describing these problems, but I'm not very optimistic about getting an answer.

It's really maddening! ](*,)  If you read through earlier post you will see that Ariel said, "I have the [same]  issues with BBC videos."

This is exactly what I mean except I do not get any video stream. Only audio!

---

### Post by ariel on 2007-11-25
> **ozorba said:**
> This is exactly what I mean except I do not get any video stream. Only audio!

If you do get the audio, then you may want trying changing the video backend your player is using. (from XV to X11, for example).
If using Totem-gstreamer plugin: run  gstreamer-properties from a console
If using mplayer: open gmplayer then go to Preferences, Video tab, then select the backend. 

Usually you want to use XV, but I've seen broken XV's in gutsy installations with intel graphic cards (no video or distorted video, very weird).

---

### Post by bw44 on 2007-11-25
> **ariel said:**
> If you do get the audio, then you may want trying changing the video backend your player is using. (from XV to X11, for example).
If using Totem-gstreamer plugin: run  gstreamer-properties from a console
If using mplayer: open gmplayer then go to Preferences, Video tab, then select the backend. 

Usually you want to use XV, but I've seen broken XV's in gutsy installations with intel graphic cards (no video or distorted video, very weird).

Is "gmplayer" an abbreviation for "Gnome Mplayer"?  I didn't have it installed on my system, and Synaptic didn't list "gmplayer" so I guessed you meant Gnome Mplayer and installed that.  But I'm not sure because it doesn't behave quite as you describe.  Anyway,  I used it to set "Video Output" and  that seemed to add the following lines to ~/.mplayer/config:
```
[gnome-mplayer]
vo=x11
ao=alsa
```

These were in addition to the existing lines:
```
[default]
# Write your default config options here!
vo=xv
ao=alsa
```

It looks like maybe the added values apply just to gnome-mplayer, not to  the plugin.  Is that possible?

The values  in ~/.mplayer/config seem to be overridden by  those in ~/.mplayer/mplayerplug-in.conf, which can be modified using the configure option in the mplayer plug-in context menu (when you have a video stream window open). 

I have been using x11 as my video output setting in mplayerplug-in.conf and this works better than anything else.  In fact (and this really puzzles me) when I access the "One-Minute World News" BBC clip, mplayer starts and plays the 20 second advertisement fine, then stops and all I get after that is the audio of the news summary.  Either Firefox or mplayer must lose the ability to handle the video when BBC switches you from the ad clip to the news clip. (Sad to say, with Firefox and the WMP plugin under Windows, the news clip plays fine as well.)

But I also get the feeling (call it a hunch) that BBC may be working on this aspect of their service even as we discuss it here.  Like we may be trying to hit a moving target!  I'm going to give them a few days before I work on it further -- to see if anything changes at their end.

Comments? Further suggestions?

---

### Post by Eric_R on 2007-11-25
> **bw44 said:**
> Really sorry I took so long to get back to you -- somehow I managed to turn notification off, so I didn't see your post until I checked the forum.

The list you show above has a number of (to me) important items commented out at the beginning of the lines with #.   But before you start un-commenting things, take a look at the file /home/your_user_name/.mplayer/mplayerplug-in.conf.   This file should exist and contain a  similar list to the above but without things commented out.  The values in this file will override the ones in /etc/mplayerplug-in.conf . Here is what mine shows:

vo=x11
ao=alsa
cachesize=4096
cache-percent=50
dload-dir=/home/bob
showtime=1
enable-wmp=1
enable-qt=1
enable-rm=1
enable-gmp=1
enable-dvx=1
enable-mpeg=1
enable-mp3=1
enable-ogg=1
enable-midi=0
enable-pls=1
enable-smil=1
enable-helix=1
nomediacache=0
nopauseonhide=1
rtsp-use-tcp=0
rtsp-use-http=1

These are the values that are set when you right click on the mplayer display window in your browser and select the "Configure" button. (They are shown in the screenshot attached to my earlier post).  Note, I have changed some of the values I posted before, because not everything is working well for me either. I've been trying different values.  The settings you see above make it possible for me to view the PandaCam site you mentiioned, as well as the shorter BBC and CBC video clips.  I am still having problems with long clips: but my PC is memory constrained and I only have a 512KB DSL link. After a couple of minutes of clear viewing the long video clips start to "stutter."

Try altering the values to those shown above (or cut and paste them into /home/your_user_name/.mplayer/mplayerplug-in.conf).  Of course I can't guarantee they will work for you  (No two computer systems are identical!).

Good luck and let us know what works for you!

These settings worked for me using mplayer plugin with Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1) Gecko/20060601 Firefox/2.0 (Ubuntu-edgy) after nothing else did.

Thanks very much. Your post was very valuable. :)

---

### Post by bw44 on 2007-11-26
> **Eric_R said:**
> These settings worked for me using mplayer plugin with Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1) Gecko/20060601 Firefox/2.0 (Ubuntu-edgy) after nothing else did.

Thanks very much. Your post was very valuable. :)

You're most welcome!  Glad it was useful.  Now, if I could only get it working for my own system . . . 

Actually, my setup works for WMV video clips at most sites, but there is something different about the BBC. If you have a minute, and haven't done so already,  could you visit the BBC site at [http://news.bbc.co.uk/](http://news.bbc.co.uk/) and click on the link  "One Minute World News"  (It's about half-way down the page under "VIDEO AND AUDIO NEWS")?  If you'd let me know what happens (or doesn't happen) I'd be much obliged.  (I'm assuming you have a fast enough Internet connection to be able to use BBC's "High Quality" selection under their media player's "Preferences". ) The problem I have with their site is that when I access the One Minute World News link or other videos I can watch their advertisement,  but never the following news clip.  A couple of other people contributing to this thread have had the same or similar problems.

Cheers

---

### Post by bw44 on 2007-11-27
The video clip of BBC's  "Odd Box" at the following URL plays flawlessly on my system  (as of 2007-11-27) using mplayer with the setup described in previous posts:

[http://www.bbc.co.uk/mediaselector/check/player/nol/newsid_6950000/newsid_6958200?redirect=6958263.stm&news=1&bbwm=1&nbram=1&bbram=1&nbwm=1&asb=1](http://www.bbc.co.uk/mediaselector/check/player/nol/newsid_6950000/newsid_6958200?redirect=6958263.stm&news=1&bbwm=1&nbram=1&bbram=1&nbwm=1&asb=1)

I'm convinced  the problems some of us have been experiencing with BBC news clips, is a result of their technical problems introducing advertising for non-UK residents who access the  site via high-speed Internet.

I hope they get it sorted.

---

### Post by ariel on 2007-11-29
gmplayer is the default gtk frontend for mplayer and in ubuntu/debian is included in the mplayer package. You can run it from the command line.

gnome-mplayer is an alternative gtk frontend you can install via the gnome-mplayer package


> **bw44 said:**
> Is "gmplayer" an abbreviation for "Gnome Mplayer"?  I didn't have it installed on my system, and Synaptic didn't list "gmplayer" so I guessed you meant Gnome Mplayer and installed that.  But I'm not sure because it doesn't behave quite as you describe.  Anyway,  I used it to set "Video Output" and  that seemed to add the following lines to ~/.mplayer/config:
```
[gnome-mplayer]
vo=x11
ao=alsa
```These were in addition to the existing lines:
```
[default]
# Write your default config options here!
vo=xv
ao=alsa
```It looks like maybe the added values apply just to gnome-mplayer, not to  the plugin.  Is that possible?

The values  in ~/.mplayer/config seem to be overridden by  those in ~/.mplayer/mplayerplug-in.conf, which can be modified using the configure option in the mplayer plug-in context menu (when you have a video stream window open). 

I have been using x11 as my video output setting in mplayerplug-in.conf and this works better than anything else.  In fact (and this really puzzles me) when I access the "One-Minute World News" BBC clip, mplayer starts and plays the 20 second advertisement fine, then stops and all I get after that is the audio of the news summary.  Either Firefox or mplayer must lose the ability to handle the video when BBC switches you from the ad clip to the news clip. (Sad to say, with Firefox and the WMP plugin under Windows, the news clip plays fine as well.)

But I also get the feeling (call it a hunch) that BBC may be working on this aspect of their service even as we discuss it here.  Like we may be trying to hit a moving target!  I'm going to give them a few days before I work on it further -- to see if anything changes at their end.

Comments? Further suggestions?

---

### Post by bw44 on 2007-11-29
> **ariel said:**
> gmplayer is the default gtk frontend for mplayer and in ubuntu/debian is included in the mplayer package. You can run it from the command line.

gnome-mplayer is an alternative gtk frontend you can install via the gnome-mplayer package

Thanks a lot! (As a newcomer to the Linux world I'm not always sure what's a naming convention, versus an abbreviation.) Now I see the "Preferences" tab you mentioned. I've tried using gmplayer to access video clips but when I try accessing media URLs I get the message "Couldn't resolve name for AF_INET6:<domain name>. But this is off-topic so I'll go hunting elsewhere on the forums for and answer to this.

---

### Post by BigAce on 2007-12-01
Hi, 
I've read all the post. Great issues !!!
Unfortunatly, my mplayer does not want to use buffer option listening live bbc1 radio.
Each 2 minutes I have to relaunch the page to listen.
My two mplayerplug-in.conf (/etc and /home) are the same (coming from original /home one).
Here is text I have :
ao=alsa
cachesize=512
cache-percent=25
dload-dir=/home/my_computer
showtime=1
enable-wmp=1
enable-qt=1
enable-rm=1
enable-gmp=1
enable-mpeg=1
enable-mp3=1
enable-ogg=1
enable-smil=1
enable-helix=1
nomediacache=0
rtsp-use-tcp=0

I don't find solution ...
Any small idea ?

---

### Post by ariel on 2007-12-01
For radio, I prefer to use a standalone player, not the browser. For bbc's realaudio streams, I found that the latest smplayer front-end to mplayer fits the bill perfectly, and looks good. Only the very latest versions work:

[http://wesley.debianbox.be/packages/](http://wesley.debianbox.be/packages/)

After you launch it go to Open URL and paste:

[http://www.bbc.co.uk/radio1/realaudio/media/r1live.ram](http://www.bbc.co.uk/radio1/realaudio/media/r1live.ram)

Then you can listen for hours. In the past gnome-mplayer couldn't open bbc radios but maybe it works now. 

I use streamtuner to keep a list of all my "radio/media bookmarks". You can easily configure it to open your radios using smplayer.

You can google around and find the direct media link URLs to bbc2, bbcworld, virgin radio, radio france, and hundreds of other radios as well.

---

### Post by BigAce on 2007-12-02
Hi Ariel,
Thanck's a lot for your guidance.
However, I would have prefered to use mplayer stream instead of realaudio stream from BBC1.
Any solution using mplayer ?

---

### Post by rbil49 on 2007-12-05
Anyone able to get the CBC/Galaxi streaming music working with Gutsy? Man, is Gutsy broken in so many subtle ways! No problem with Edgy, but Gutsy is more and more feeling like a piece of crap.

Cheers.

---

### Post by Bakon Jarser on 2007-12-11
> **bw44 said:**
> You're most welcome!  Glad it was useful.  Now, if I could only get it working for my own system . . . 

Actually, my setup works for WMV video clips at most sites, but there is something different about the BBC. If you have a minute, and haven't done so already,  could you visit the BBC site at [http://news.bbc.co.uk/](http://news.bbc.co.uk/) and click on the link  "One Minute World News"  (It's about half-way down the page under "VIDEO AND AUDIO NEWS")?  If you'd let me know what happens (or doesn't happen) I'd be much obliged.  (I'm assuming you have a fast enough Internet connection to be able to use BBC's "High Quality" selection under their media player's "Preferences". ) The problem I have with their site is that when I access the One Minute World News link or other videos I can watch their advertisement,  but never the following news clip.  A couple of other people contributing to this thread have had the same or similar problems.

Cheers

It seems to be "working" for me in a very strange way (the one minute news).  It opens and starts playing but then it opens the link again and starts playing and does this in an infinite loop.  So what I get is it saying its connecting and then showing a couple of seconds of the video and then saying its connecting and getting an overlay of the video and audio starting again together with the video and audio where it left off when it started to download again.  I know that's a confusing explanation but it's a confusing situation.  All other videos including the oddbox bbc one that you posted work fine.  This loop problem could be the bbc's fault but it sounds to me like it might be an mplayer bug.  

BTW thanks for the great guide.

---

### Post by bw44 on 2007-12-11
> **Bakon Jarser said:**
> It seems to be "working" for me in a very strange way (the one minute news).  It opens and starts playing but then it opens the link again and starts playing and does this in an infinite loop.  So what I get is it saying its connecting and then showing a couple of seconds of the video and then saying its connecting and getting an overlay of the video and audio starting again together with the video and audio where it left off when it started to download again.  I know that's a confusing explanation but it's a confusing situation.  All other videos including the oddbox bbc one that you posted work fine.  This loop problem could be the bbc's fault but it sounds to me like it might be an mplayer bug.  

BTW thanks for the great guide.

Not sure the symptom you describe is exactly what I experience, but it' pretty close.  I just sent BBC another whine about their inability to support Linux/Firefox/mplayer.  I pointed out that a  lot of their video links look like this:

[http://news.bbc.co.uk/media/avdb/news/science_nature/video/137000/bb/137701_16x9_bb.asx?ad=1&ct=50](http://news.bbc.co.uk/media/avdb/news/science_nature/video/137000/bb/137701_16x9_bb.asx?ad=1&ct=50)

If you remove the  ?ad=1&ct=50 from the end of the URL and link to it, it plays fine. So it's not like their videos won't play.

You many be right that there's a bug in mplayer, OR is may be a combination of how the BBC has implemented their advertising with something mplayer doesn't handle correctly.  Of course, it's also possible that the BBC site is relying on something that only works for Windows sites.  I've visited another site where regular pages won't display because they choose to return a different HTTP code to Windows browsers than to Linux browsers. 

I assume your preferences for BBC are set to Windows Media Player.  When I set mine to Real Player, I was able to view the ads but they would go into a display loop and never get to the news clip.  What kind of internet connection do you have?  It may be faster than my 512KB DLS link, and this could account for why the symptoms aren't quite the same for you.

Glad my suggestions helped.

---

### Post by oniichan on 2007-12-11
Thanks. Worked perfectly after fooling around with the BBC websire for weeks.

---

### Post by bw44 on 2007-12-11
> **oniichan said:**
> Thanks. Worked perfectly after fooling around with the BBC websire for weeks.

You didn't quote anyone, so I'm not sure what worked for you.  But if it's working **perfectly,** I need **your** help!!!  As I mentioned in my last post, it only works for me if I doctor the BBC URLs,  to bypass the advertising clips.  If you're able to view the BBC videos from outside the UK including the ad clip preceding the news clip, could you post your mplayerplug-in.conf settings?

Thanks.

---

### Post by douglas.wtfo on 2007-12-11
Thanks so much for this

I am a Linux newbie.  I don't post much cuz there is so much to read.  I was disappointed that I could not listen to XM Radio online.  After running through your plugin configuration, XM Radio streaming is working great. 

THanks!!

DM.

:guitar:

---

### Post by Bakon Jarser on 2007-12-12
> **bw44 said:**
> 

I assume your preferences for BBC are set to Windows Media Player.  When I set mine to Real Player, I was able to view the ads but they would go into a display loop and never get to the news clip.  What kind of internet connection do you have?  It may be faster than my 512KB DLS link, and this could account for why the symptoms aren't quite the same for you.

Glad my suggestions helped.

Slight progress.  I can view the entire one minute news in windows media format on low quality.  It sits there and says "buffering" for about a minute and then plays.  I don't get any kind of output at all with the real player settings.  I have a 5mb download speed.  

As far as the link you posted, it went through the usual phase of trying to buffer and then said stopped after a minute.  I hit the play button and part of it played then it stopped.  I tried removing the end and it played fine, but still took a long time for buffering.  No sound at all for the video though.  Is there supposed to be?

posting my conf file just in case it helps.

vo=x11
ao=alsa
cachesize=1749
cache-percent=30
dload-dir=/home/chester
showtime=1
enable-wmp=1
enable-qt=1
enable-rm=1
enable-gmp=1
enable-dvx=1
enable-mpeg=1
enable-mp3=1
enable-ogg=1
enable-midi=0
enable-pls=1
enable-smil=1
enable-helix=1
nomediacache=0
nopauseonhide=1
rtsp-use-tcp=1
rtsp-use-http=1

download=0
showlogo=0
black-background=1
qt-speed=high

---

### Post by bw44 on 2007-12-13
> **Bakon Jarser said:**
> Slight progress.  I can view the entire one minute news in windows media format on low quality.  It sits there and says "buffering" for about a minute and then plays.  I don't get any kind of output at all with the real player settings.  I have a 5mb download speed.  

As far as the link you posted, it went through the usual phase of trying to buffer and then said stopped after a minute.  I hit the play button and part of it played then it stopped.  I tried removing the end and it played fine, but still took a long time for buffering.  No sound at all for the video though.  Is there supposed to be?

posting my conf file just in case it helps.

vo=x11
ao=alsa
cachesize=1749
cache-percent=30
dload-dir=/home/chester
showtime=1
enable-wmp=1
enable-qt=1
enable-rm=1
enable-gmp=1
enable-dvx=1
enable-mpeg=1
enable-mp3=1
enable-ogg=1
enable-midi=0
enable-pls=1
enable-smil=1
enable-helix=1
nomediacache=0
nopauseonhide=1
rtsp-use-tcp=1
rtsp-use-http=1

download=0
showlogo=0
black-background=1
qt-speed=high

Thanks a lot for trying it out.  The BBC problems for me have always been when trying to access the video clips with the high speed preference setting (which their test says should work).  At the low ("standard"?) speed setting there is not a problem, because they don't make you watch ads if you are using a low speed connection (I think they define this as below 256KB).  I can see (and hear) everything ok at low speed, but it's just too slow to load.

As for the specific video clip I mentioned, the one of the mouse with giant ears, there is no sound.  Sorry, I should have used an example with sound.  Try this one:  [http://news.bbc.co.uk/newsa/n5ctrl/summaries/world/bb/video/world_bb.asx](http://news.bbc.co.uk/newsa/n5ctrl/summaries/world/bb/video/world_bb.asx)

As for our mplayerplug-in.conf settings the only significant difference I can see is the cache size:  I'm using a much larger cache.  I had to play around with the cache and cache-percent settings, and the ones you see in the screenshot attached are the ones I've settled on.  You could try increasing the buffer size and see if it helps.  I also have autoplay=1 set, but this may be the default..

I don't know how to put an http trace on the interaction with a web site, but I  think what happens is that the video link on the BBC's page points you to a test of what browser preferences you are using.  If you're using high speed (and don't live in the UK) it then redirects you to the ad video and then somehow switches you (or is supposed to switch you) to the actual news video.  As I said in a previous post, I can usually see the ad, but after that I can only hear the sound track of the video.

I really think there is something wrong with the way the BBC videos and advertising have been implemented, AND I think they may be trying to fix it.  Unfortunately, as they test and we test, we get inconsistent results from one day to the next.  Maybe if we're patient they'll eventually get it right.  One can hope.

Cheers.

---

### Post by mtn on 2007-12-18
Thanks - worked great.

---

### Post by joshuashearer on 2007-12-21
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=540412&amp;highlight=ubuntu+divx](http://ubuntuforums.org/showthread.php?t=540412&amp;highlight=ubuntu+divx) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Ok well i have it working....the aspect ratio is a little bit off...but its working amazing otherwise....for anyone having the nightmare that i hav had ...perhaps try this config....beyon that is there any other way to change the aspect rario other than using the 

prefer-aspect=0/1 command....perhaps within the player itself or perhaps another command...forcing the origonal aspect seems far to taxing on my sytemn ...or this set up and it will not run in a functional manner if I cange it here....anyways her is my configuration,,,, thanx for all the help and info so far...


vo=xv
ao=esd
debug=2
cachesize=1000
cache-min = 20.0
cache-seek-min = 50
autostart=1
noembed=0
prefer-aspect=0
framedrop=1
cookies=0
enable-wmp=1
enable-qt=1
enable-rm=1
enable-gmp=1
enable-helix=1
enable-mpg=1
showcontrols=1
enable-mp3=1
enable-ogg=1
enable-smil=1
enable-pls=1
profile=default-joshua
blackbackground=1

thanks again

---

### Post by bw44 on 2007-12-21
> **joshuashearer said:**
> **This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=540412&amp;highlight=ubuntu+divx](http://ubuntuforums.org/showthread.php?t=540412&amp;highlight=ubuntu+divx) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Ok well i have it working....the aspect ratio is a little bit off...but its working amazing otherwise....for anyone having the nightmare that i hav had ...perhaps try this config....beyon that is there any other way to change the aspect rario other than using the 

prefer-aspect=0/1 command....perhaps within the player itself or perhaps another command...forcing the origonal aspect seems far to taxing on my sytemn ...or this set up and it will not run in a functional manner if I cange it here....anyways her is my configuration,,,, thanx for all the help and info so far...


vo=xv
ao=esd
debug=2
cachesize=1000
cache-min = 20.0
cache-seek-min = 50
autostart=1
noembed=0
prefer-aspect=0
framedrop=1
cookies=0
enable-wmp=1
enable-qt=1
enable-rm=1
enable-gmp=1
enable-helix=1
enable-mpg=1
showcontrols=1
enable-mp3=1
enable-ogg=1
enable-smil=1
enable-pls=1
profile=default-joshua
blackbackground=1

thanks again
Sorry I can't help you with the aspect ratio setting.  I have always accepted the default (whatever that is!)

I'd like to compare your settings with my own and try out some parameters which I have not used before.

Would you mind posting what version of Ubuntu you are using (or add it to your user profile) and also what version of mplayer you are running?  As you can see I am running Gutsy Gibbon(7.10).  My mplayer is version 3.4, but I think version 3.5 is available.

Glad you've pretty much got it working -- it does seem to be a bit of a struggle!

Best.

---

### Post by joshuashearer on 2007-12-21
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=540412&amp;highlight=ubuntu+divx](http://ubuntuforums.org/showthread.php?t=540412&amp;highlight=ubuntu+divx) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Ok I'm no sure what was going on before....this works too...I'm not sure if the other one did or not....10 min into a movie it kept going all weird...so more hours of work...i went back to an earlier post and even this was not working....so HA! I'm so frustrated...it was the movie....anyways I'm using this and it works well...

vo=xv 
ao=esd
debug=2
cachesize=4096
cache-percent=50
showtime=1
rtsp-use-http=1
autostart=1
noembed=0
prefer-aspect=0
framedrop=1
cookies=0
enable-wmp=1
enable-qt=1
enable-rm=1
enable-gmp=1
enable-helix=1
enable-mpg=1
showcontrols=1
enable-mp3=1
enable-ogg=1
enable-smil=1
enable-pls=1
profile=default-joshua
blackbackground=1


As for ubuntu I am using 7.10 and mplayer is 3.25-7 I think if I'm looking at the right numbers.....I think I'm still gonna toy with framedrop still and I still have another question....Is there a command line to adjust the quality of the picture.....I know that I can toy with it in mplayer properties, but I think that i was having some conflicts between /etc/config and the $home/config and the configuration files in mplayer proerties that can be changed using the graphic interface...so I have changed them all to be in sync with eachother.....I would like to do this for the picture quality as well...
on a side note I found a config file in the mplayer folder with these options but I get the idea  I could really mess things up if I toy with some of the video ones ...can anyone help with this?


#
# MPlayer configuration file
#
# Configuration files are read system-wide from /usr/local/etc/mplayer.conf
# and per user from ~/.mplayer/config, where per-user settings override
# system-wide settings, all of which are overrriden by the command line.
#
# The configuration file settings are the same as the command line
# options without the preceding '-'.
#
# See the CONFIGURATION FILES section in the man page
# for a detailed description of the syntax.


##################
# video settings #
##################

# Specify default video driver (see -vo help for a list).
vo=xv,sdl,x11

# Use SDL video with the aalib subdriver by default.
#vo = sdl:aalib

# FBdev driver:
#
# mode to use (read from fb.modes)
#fbmode = 640x480-120
#
# location of the fb.modes file
#fbmodeconfig = /etc/fb.modes

# Specify your monitor timings for the vesa and fbdev video output drivers.
# See /etc/X11/XF86Config for timings. Be careful; if you specify settings
# that exceed the capabilities of your monitor, you may damage it.
#
# horizontal frequency range (k stands for 1000)
#monitor-hfreq = 31.5k-50k,70k
#
# vertical frequency range
#monitor-vfreq = 50-90
#
# dotclock (or pixelclock) range (m stands for 1000000)
#monitor-dotclock = 30M-300M

# Start in fullscreen mode by default.
#fs=yes

# Change to a different videomode when going fullscreen.
#vm=yes

# Override the autodetected color depth, may need 'vm=yes' as well.
#bpp=0

# Enable software scaling (powerful CPU needed) for video output
# drivers that do not support hardware scaling.
#zoom=yes

# standard monitor size, with square pixels
#monitoraspect=4:3

# Use this for a widescreen monitor, non-square pixels.
#monitoraspect=16:9

# Keep the player window on top of all other windows.
#ontop=yes


##################
# audio settings #
##################

# Specify default audio driver (see -ao help for a list).
ao=alsa,oss,sdl,esd,arts

# Use SDL audio driver with the esd subdriver by default.
#ao = sdl:esd

# Specify the mixer device.
#mixer = /dev/mixer

# Resample the sound to 44100Hz with the lavcresample audio filter.
#af=lavcresample=44100


##################
# other settings #
##################

# Drop frames to preserve audio/video sync.
#framedrop = yes

# Specify your preferred skin here (skins are searched for in
# /usr/local/share/mplayer/Skin/<name> and ~/.mplayer/Skin/<name>).
#skin = Abyss

# Resample the font alphamap.
# 0     plain white fonts
# 0.75  very narrow black outline (default)
# 1     narrow black outline
# 10    bold black outline
#ffactor = 0.75

# cache settings
#
# Use 8MB input cache by default.
#cache = 8192
#
# Prefill 20% of the cache before starting playback.
#cache-min = 20.0
#
# Prefill 50% of the cache before restarting playback after the cache emptied.
#cache-seek-min = 50

# DVD: Display English subtitles if available.
#slang = en

# DVD: Play English audio tracks if available.
#alang = en


# You can also include other configuration files.
#include = /path/to/the/file/you/want/to/include


Sorry it took me so long to respond....I wanted to make sure I had an idea what was going on with this stuff and repair what may not have been working in my previous post...as i may have been incorrect before...Sorry it seemed to be working....I just watched a full movie this time and this is definately stable...
Thankyou again

Josh

---

### Post by joshuashearer on 2007-12-21
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=540412&amp;highlight=ubuntu+divx](http://ubuntuforums.org/showthread.php?t=540412&amp;highlight=ubuntu+divx) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Yesssss!!!!!!  Ok the config in the post above that I just posted works great on my computer...I have adjusted the video quality in the mplayer settings in properties....it looks beautiful....I would still love to know if there is a command line to do this...but I am soooo happy ....finally.....thanks again to all for all the tips posted on here....if nothein else is working for anyone.....try this config......I hope that it helps

vo=xv
ao=esd
debug=2
cachesize=4096
cache-percent=50
showtime=1
rtsp-use-http=1
autostart=1
noembed=0
prefer-aspect=0
framedrop=1
cookies=0
enable-wmp=1
enable-qt=1
enable-rm=1
enable-gmp=1
enable-helix=1
enable-mpg=1
showcontrols=1
enable-mp3=1
enable-ogg=1
enable-smil=1
enable-pls=1
profile=default-joshua
blackbackground=1

Also as I said before...I think I was having some conflict issues...I think...between the config files....as I had changed things at different times ...first in /etc   then in $home...and also in the graphical interface

[In ored to reach the graphical interface......Applications....then sound and video ... then MPlayer Movie player...NOT Movie Player......open MPlayer Movie Player and right click on the grey screen where the MPlayer Movieplayer controls are and select preferences....]

......since I have put them in sinc with eachother...particuarilly the buffersize under preferences then misc tab....it was totally different then what I had specified....sin ....I also turned auto sync on .....i set the value to 1.....then  I also enabled post processing  and raised the autoquality to 100  (this may not be good for all video cards).....then under the video tab....i enabled double buffering, direct rendering, frame dropping, and HARD frame dropping  (it says its dangerous) so be careful if you use this.....I have also made a habit of logging off after making changes...I don't think this is necessary...but it seems to ensure that the changes take place...I think I had a couple issues with this as well...

I don't know if this helps anyone...I hope that it does....I think I have put almost 20 hours into this.  Also if I sound like I don't know what I'm talking about ...I don't  :)  I'm brand new to this....in the end however ...it has worked.

Thankyou all again

Josh

---

### Post by arnicainthemembrane on 2007-12-21
It ain't workin!

I've downloaded and redownloaded Mplayer and the codecs multiple times and still I come back to the same problem:

BBC: audio, for radio streaming, fine. Prepared radio programs (more than a few minutes) nil. Video, nil. It connects, it loads, it buffers, then it stops and won't go. Same with Al Jazeera, same with anything which with a Windows or OS system requires Realplayer.

YouTube, fine. adverts, fine. I'm just having a hell of a time getting Mplayer to play any video or extended audio which would otherwise be played just fine on Realplayer. 

In the past I've always had my hd partitioned so i could switch to Windows for watching the news, but I'm over it and determined to figure out how to fix the problem. What am I missing here?

---

### Post by joshuashearer on 2007-12-22
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=540412&amp;highlight=ubuntu+divx](http://ubuntuforums.org/showthread.php?t=540412&amp;highlight=ubuntu+divx) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **arnicainthemembrane said:**
> It ain't workin!

I've downloaded and redownloaded Mplayer and the codecs multiple times and still I come back to the same problem:

BBC: audio, for radio streaming, fine. Prepared radio programs (more than a few minutes) nil. Video, nil. It connects, it loads, it buffers, then it stops and won't go. Same with Al Jazeera, same with anything which with a Windows or OS system requires Realplayer.

YouTube, fine. adverts, fine. I'm just having a hell of a time getting Mplayer to play any video or extended audio which would otherwise be played just fine on Realplayer. 

In the past I've always had my hd partitioned so i could switch to Windows for watching the news, but I'm over it and determined to figure out how to fix the problem. What am I missing here?

How have you configured the mplayer plug in....could you copy and paste the config...also which version of ubuntu are you using...I will try to help if I can...

---

### Post by Blofeld on 2007-12-22
Thanks, Ariel.  This worked perfectly for me on the first try.
My sound is out of synch with the image, but I blame that on my lame CPU.

---

### Post by 5735guy on 2007-12-30
Brilliant, Many Thanks.:):)

---

### Post by 5735guy on 2008-01-05
Brilliant Thankyou. :):)

---

### Post by revelationman on 2008-01-07
> **ariel said:**
> After a long time using the feature-less VLC-Plugin, and messing things up with the MediaPlayerConnectivity plugin to open lots of stand-alone VLC windows every time I wanted to watch BBC or CBC News videos, I finally got the Mplayer plugin to work fine and play all those embedded videos with no stuttering or annoyances.

The following is for Feisty but I guess it works in other versions and distros as well.

It was (way!) simple. My original problem with mozilla-mplayer was that it simple kept "stuttering" with BBC and CBC streaming videos. 

Here's how to install it and configure it, and with the same stone, get embedded Div-X streaming videos from stage6.divx.com to work stunningly well. And also get your plugin to look good...[LIST=1]
[*]Close your Firefox
[*]Remove the plugins you will no longer be using:
```
sudo apt-get remove totem-mozilla mozilla-plugin-vlc
```
[*]Install the awesome mplayer plugin:
```
sudo apt-get install mozilla-mplayer
```
[*]Feisty (7.04) Users: Add these symlinks that enable the plugin to handle Stage6's DIVXs (7.10 users: the symlinks should already be there if you did a fresh install; if not, just add them)

```
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so /usr/lib/firefox/plugins/mplayerplug-in-dvx.so
``````
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt /usr/lib/firefox/plugins/mplayerplug-in-dvx.xpt
```
[*]Configure the plugin to with approriate Buffer / Cache size; this fixes the BBC / CBC windows media stream stuttering

Open the config file:

```
sudo gedit /etc/mplayerplug-in.conf
```Add the following lines in the file: (this works great in my system; you might have to do some tuning of the cachesize and cache-percent)

cachesize=1000
cache-percent=30
download=0
showlogo=0
black-background=1
[*]Start your browser, check your new setup in [www.cbc.ca]("http://www.cbc.ca") and Stage6
[*]Enjoy!![/LIST]Note: You might need to setup the BBC News site to stream windows media to you, instead of RealMedia; you can do this easily, after the above setup is completed:[LIST]
[*]Go to: [http://news.bbc.co.uk/](http://news.bbc.co.uk/)
[*]Open a video (for example, the 1-minute day news headlines)
[*]In the new window, you will notice a "Preferences" link; click on it
[*]This will open a window that will let you choose "Windows Media" instead of Real Media; select it, and close; configuration will be stored persistently in your system[/LIST]

Well I did all that and  BBC still will not play   this is starting to piss  me off :lolflag:

Any  other suggestions  I am running gusty 7.10 

cheers

---

### Post by revelationman on 2008-01-07
Well  to be fair I have pasted my config  in here if  you  see anything wrong 

#debug=0
#vo=xv,x11
#ao=arts,esd,oss
#download=1
#dload-dir=$HOME/tmp
#keep-download=0
#noembed=0
#cachesize=512
#use-mimetypes=0
#enable-ogg=1
#enable-smil=1
#enable-helix=1
#qt-speed=med
#rtsp-use-tcp=0
#nomediacache=0
#framedrop=0
#autosync=0
#mc=1
#black-background=0
#user-agent=NSPlayer
cachesize=1000
cache-percent=30
download=0
showlogo=0
black-background=1

---

### Post by ubuntu-freak on 2008-01-08
Looks like you are missing important "enable" options.

Try my guide here [http://ubuntuforums.org/showthread.php?t=658970&highlight=mplayer+plugin&page=3](http://ubuntuforums.org/showthread.php?t=658970&highlight=mplayer+plugin&page=3)

If it doesn't work I'll eat my laptop.

Nathan 
 
Edit: Please post in the howto thread instead of here when it works for you. Encourages people to try it and keeps the thread alive. Thanks.

---

### Post by bw44 on 2008-01-09
> **reassuringlyoffensive said:**
> Looks like you are missing important "enable" options.

Try my guide here [http://ubuntuforums.org/showthread.php?t=658970&highlight=mplayer+plugin&page=3](http://ubuntuforums.org/showthread.php?t=658970&highlight=mplayer+plugin&page=3)

If it doesn't work I'll eat my laptop.

Nathan

2 questions:

At the BBC site do you select "Windows Media Player" or "Real Media Player" in their preferences setting?

Are you able (do you have to!) view advertising before the featured video (as at the 1 minute news summary:  [http://www.bbc.co.uk/mediaselector/check/player/nol/newsid_6900000/newsid_6903100?redirect=6903113.stm&news=1&nbram=1&nbwm=1&bbwm=1&bbram=1&asb=1](http://www.bbc.co.uk/mediaselector/check/player/nol/newsid_6900000/newsid_6903100?redirect=6903113.stm&news=1&nbram=1&nbwm=1&bbwm=1&bbram=1&asb=1)
I use very simialr mplayerplug-in.conf settings to yours but am not able (without doctoring the URLs)  to view the BBC videos.

Thanks for your post.

---

### Post by ubuntu-freak on 2008-01-09
> **bw44 said:**
> 2 questions:

At the BBC site do you select "Windows Media Player" or "Real Media Player" in their preferences setting?

Are you able (do you have to!) view advertising before the featured video (as at the 1 minute news summary:  [http://www.bbc.co.uk/mediaselector/check/player/nol/newsid_6900000/newsid_6903100?redirect=6903113.stm&news=1&nbram=1&nbwm=1&bbwm=1&bbram=1&asb=1](http://www.bbc.co.uk/mediaselector/check/player/nol/newsid_6900000/newsid_6903100?redirect=6903113.stm&news=1&nbram=1&nbwm=1&bbwm=1&bbram=1&asb=1)
I use very simialr mplayerplug-in.conf settings to yours but am not able (without doctoring the URLs)  to view the BBC videos.

Thanks for your post.

Well that was odd. On other parts of the BBC site I can watch in either rm or wmv. With that link you posted though I had to select wmv and then it worked fine. Took a little while to kick in though.

Nathan

Edit: BBC is acting weird today. Tried some other videos on their site that have worked before, some play okay some don't. Must be something wrong their end.

---

### Post by bw44 on 2008-01-10
> **reassuringlyoffensive said:**
> Well that was odd. On other parts of the BBC site I can watch in either rm or wmv. With that link you posted though I had to select wmv and then it worked fine. Took a little while to kick in though.

Nathan

Edit: BBC is acting weird today. Tried some other videos on their site that have worked before, some play okay some don't. Must be something wrong their end.

You're edit says it all!  I think "BBC is acting weird" pretty well summarizes my experience with their site.  I think in the last couple of months they have been trying to implement their policy of making non-UK residents view advertising before receiving the actual videos.  Whomever they out-sourced this to has had a lot of trouble making it work, and of course, they made it work first and foremost with IE.  Firefox under Windows has worked better than Firefox under Ubuntu (Linux?).

The problem has been, and continues to be, that while we Ubuntu users try different combinations of browsers, plug-ins and settings, BBC has been changing the way their site works.  I notice, for example, that the test ads they had implemented a few weeks ago don't seem to be there at the moment.  But it's sure hard to test when what your testing is being changed at the other end!  I've just decided to let them sort it out for a while and not expect too much in the meantime.

Cheers.

---

### Post by n_murthy on 2008-01-12
i'm trying to get the mplayer plug in for my firefox webrowser. i already removed totem, but when i run 'sudo apt-get install mozilla-mplayer' the terminal spits:

# sudo apt-get install mozilla-mplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mozilla-mplayer

why is it that it cannot find the package? or where is it found in the first place?

---

### Post by ubuntu-freak on 2008-01-12
That's odd. Did you go to my how-to thread? Is the medibuntu repo enabled?
 
Nathan

---

### Post by ubuntu-freak on 2008-01-12
And remember to sudo apt-get update before installing anything

---

### Post by n_murthy on 2008-01-12
I read your how-to thread. I tried sudo apt-get update and tried installing the plug-in once again, but to no avail: same terminal response. How do I enable "medibuntu repo"?

---

### Post by ubuntu-freak on 2008-01-12
The first link on the how-to takes you to a page that tells you how to enable the medibuntu repo.
 
Once you get it all working (you will), streaming etc, post a reply in the how-to thread detailing your success. Makes other people want to try it and keeps the thread alive. 
 
Nathan

---

### Post by 5735guy on 2008-01-12
Awesome thankyou, much better than struggling with real player. GREAT STUFF !:):):):)

---

### Post by n_murthy on 2008-01-13
Now I'm having problems with my package installer: [http://ubuntuforums.org/showthread.php?p=4125909#post4125909](http://ubuntuforums.org/showthread.php?p=4125909#post4125909)

---

### Post by n_murthy on 2008-01-13
It turns out that there were some crucial packages that I removed when I used Synaptic when I tried supplanting totem for mplayer. Apparently, there were several libraries that were interdependent on some the programs in the mplayer package which subsequently were expunged when I initially tried to remove totem. 

I reinstalled those packages and followed the instructions verbatim as they appeared at the beginning of this thread. Things are working smoothly and now I can watch *Manufactured Landscapes* with satisfaction.


Much thanks for all of the support.

---

### Post by bw44 on 2008-01-15
> **reassuringlyoffensive said:**
> Well that was odd. On other parts of the BBC site I can watch in either rm or wmv. With that link you posted though I had to select wmv and then it worked fine. Took a little while to kick in though.

Nathan

Edit: BBC is acting weird today. Tried some other videos on their site that have worked before, some play okay some don't. Must be something wrong their end.

I finally got a reply from BBC, albeit it's a form letter.  Here's an excerpt:> The issue faced by the BBC is that we must add infrastructure for each type of software supported, and increasing the number of software applications means an increased cost to license fee payers. We are constantly looking to strike a balance between what our viewers and listeners would like and spending the licence fee wisely.

Having said that, we appreciate that the current situation is not ideal. Indeed, we are currently offering the content of our 'Digital Only' radio channels, and most of our News and Sport clips and streams on both Real and Windows Media Player. Regrettably, due to the considerable amount of content we offer, we currently cannot offer this across the board. 

We have ensured that versions of Real player are available as free downloads for virtually all types of hardware and operating systems (Windows, Mac, Linux and more), so that everyone can have access to our content regardless of the equipment that they choose to use.

For your information, we are currently in the process of redeveloping the way our News and Sport clip content is presented on our site. Within in the next few months we will be presenting our short clips as Flash media, embedded within text pages on the News and Sport sites. It is part of a major project to overhaul the way we present our News and Sport video and audio coverage, which will also eventually lead to changes in how we present our live and news programme content coverage.  It is also in line with how BBC programme content is currently offered within the newly launched BBC iPlayer, which you can see here if you are in the UK: [http://www.bbc.co.uk/iplayer/](http://www.bbc.co.uk/iplayer/)

So apparently not everything is supported in both rm and wmv formats, and I'm not sure how you tell which.  The letter doesn't give much detail but at least they acknowledge the wrinkles in their current offering.  And  they have a plan, so I guess we must just be patient and see how it unfolds.

---

### Post by ubuntu-freak on 2008-01-15
I'm actually not having problems now. Wmv radio takes AGES to kick in but ram is fine and sounds better anyway.
 
Nathan

---

### Post by bw44 on 2008-01-15
> **reassuringlyoffensive said:**
> I'm actually not having problems now. Wmv radio takes AGES to kick in but ram is fine and sounds better anyway.
 
Nathan
I just noticed that you are a UK resident.  I'm not sure how much difference it makes, but I believe that  if non-UK residents access the BBC site with a high-speed link that they are subject to additional advertising "trailers" which have been a major source of headaches for me.

I think I posted a very inelegant work-around in this thread earlier: basically you can click on a video link and after mplayer launches right click on its window and copy the URL (which on my system will never respond) and paste it into the address bar. Lop off the character string "ad=1&ct=50" from the end of the URL and then link to it.

I wrote to BBC and told them that I would be content to watch their ads if I could, but they won't play.  But if I make the above change to the URL, then I can watch the featured video clip.  They never replied to my fairly detailed description of the problem.

You may not be able to see and test this within the UK, but users should be aware that there is a difference in how the video clip URLs work outside the British Isles.

Cheers.

---

### Post by ubuntu-freak on 2008-01-15
Do other rm, wmv, ram streams work okay then? 
 
Nathan

---

### Post by bw44 on 2008-01-16
> **reassuringlyoffensive said:**
> Do other rm, wmv, ram streams work okay then? 
 
NathanYes, all the ones I've tried work fine (though some of the wmv audio streams are really slow, as you mentioned).

---

### Post by ubuntu-freak on 2008-01-16
Made some additions to my how-to today.
 
Faac and faad have been added to the restricted extras list. Need them for making mobile 3g2 vids and mp4.
 
DVD post is worth doing. Encrypted discs will work and you can make VLC default DVD player (great menu support). 
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
Nathan

---

### Post by Ludford on 2008-01-21
I followed this guide. But when I tried to watch a video it just displays a buffering % that slowly goes up... It goes straight from 0% to 100% in about a second on my windows boot.

Also my procceser usage shoots up to about 80% and everything lags like hell.

EDIT: NVM it just lags while buffering and then is fine during playback. Mplayer seems to do it differently than divx player. Mplayer buffers the whole thing before you can watch. Where as Divx buffers it as you watch.

---

### Post by ubuntu-freak on 2008-01-21
> **Ludford said:**
> I followed this guide. But when I tried to watch a video it just displays a buffering % that slowly goes up... It goes straight from 0% to 100% in about a second on my windows boot.

Also my procceser usage shoots up to about 80% and everything lags like hell.

EDIT: NVM it just lags while buffering and then is fine during playback. Mplayer seems to do it differently than divx player. Mplayer buffers the whole thing before you can watch. Where as Divx buffers it as you watch.

 
I noticed that buffering issue today. I'm gonna look into it weds (won't have access til then). It's not normal. Try adding 
 
download=1
 
to the top of the mplayerplug-in.conf.
 
Nathan

---

### Post by ubuntu-freak on 2008-01-21
Don't forget to 
 
rm $HOME/.mozilla/firefox/plugins/pluginreg.dat
 
Nathan

---

### Post by 5735guy on 2008-01-25
Works brilliantly on 7.04

But crashes Firefox on 7.10

Any ideas ???

Cheers.:confused:

---

### Post by ubuntu-freak on 2008-01-26
> **5735guy said:**
> Works brilliantly on 7.04

But crashes Firefox on 7.10

Any ideas ???

Cheers.:confused:

 
What worked before and now crashes? System crash or Firefox? Did you follow my how-to?
 
Nathan

---

### Post by 5735guy on 2008-01-26
Hi, 

With 7.10, Firefox greys out and stops reponding, the only way to fix this is by doing a force quit.

This only happens with 7.10, I have no problems with 7.04

Cheers:confused:

---

### Post by ubuntu-freak on 2008-01-26
> **5735guy said:**
> Hi, 

With 7.10, Firefox greys out and stops reponding, the only way to fix this is by doing a force quit.

This only happens with 7.10, I have no problems with 7.04

Cheers:confused:

 
Has it always done that in Gutsy? Or just when you tried to improve streaming? Need more info. You didn't say if you followed my how-to here
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
Nathan

---

### Post by 5735guy on 2008-01-26
Thats brilliant thankyou, have applied to both 7.10 and 7.04

HAPPY DAYS

MANY THANKS:):):):):)

---

### Post by rfurman24 on 2008-01-29
I have had mplayer working in Feisty and Gutsy with no extra work but when Gutsy broke and I decided to try Mint it would not work no matter what. I tried everything in this thread and spent many hours playing with it on my own. I finally tried Xine plugin and it works great, maybe even better than Mplayer did.

---

### Post by oedipuss on 2008-02-07
I have a very weird problem with bbc videos and mplayerplugin .. 
It will start playing just fine, and after a few seconds it seems to spawn more instances of itself playing different videos (ads?) or just repeatedly the same one, which makes the video window flicker between frames of 2 or more vids. o_O 
Sound doesn't stop when I close the firefox window, and there are many mplayer processes (6 or more, depending on how long I've let it run) running in system monitor. 
Vids from stage6 play just fine, except there's no seeking , but I guess that can't be helped. 

Totem doesn't work at all with bbc, and neither does vlc.

---

### Post by ubuntu-freak on 2008-02-07
You don't have the mozilla and vlc plugins installed also do you?  They will clash. Check out my [how-to](http://ubuntuforums.org/showthread.php?t=661833) which includes a streaming section.
 
Nathan

---

### Post by oedipuss on 2008-02-07
Both totem and vlc plugins aren't installed. The only files in my lib/mozilla/plugins dir are the libflash plugin, java and a bunch of files for the mplayerplugin, which are also linked in lib/firefox/plugins . 
I also deleted pluginreg.dat, and about: plugins in firefox reports only mplayerplugin for various mime types.

It's really weird if it doesn't happen to anyone else o_O I'm using a regular out-of-the-repo firefox and mplayer. It seems after some time mplayer will spawn another instance of itself playing the same video from the start over the same space, again and again, flickering between frames.

Here are some shots, too, though you can't see the flickering.

Again, stage6 works fine, I'm suspecting it's got something to do with the ads bbc inserts before videos.

---

### Post by ubuntu-freak on 2008-02-07
Are the vids embedded? Does it open more tabs? Have you tried only using RealPlayer for BBC streams and copying the settings from my [how-to](http://ubuntuforums.org/showthread.php?t=661833)?
 
Nathan

---

### Post by lduplantie on 2008-04-25
Thank you Ariel. Can you look into the videos at [www.radio-canada.ca](www.radio-canada.ca). I can play the videos at cbc.ca but not at radio-canada.ca under 8.04. It worked under 7.10.

Laurent

---

### Post by ariel on 2008-04-26
> **lduplantie said:**
> Thank you Ariel. Can you look into the videos at [www.radio-canada.ca]("http://www.radio-canada.ca"). I can play the videos at cbc.ca but not at radio-canada.ca under 8.04. It worked under 7.10.

Laurent

Yes I just noticed that mplayer chokes with this.

For the time being, you can watch Radio Canada's live feed with SMPlayer or VLC; this is the URL you need: 

[http://www.radio-canada.ca/util/endirect/rdidirect.asx](http://www.radio-canada.ca/util/endirect/rdidirect.asx)

I have this URL bookmarked in StreamTuner.

---

### Post by lduplantie on 2008-04-30
Hello again, 

I can't explain why but if I empty FF3b5's cache I can view the direct feed with MPlayer. I still can't view the news clips from radio-canada.ca

Other point I noticed after viewing "rdidiect.asx" FF is slower and often makes pauses (screen greys out).

I hope this will help

---

### Post by ubuntu-freak on 2008-04-30
Just to let you know, the mplayeplug-in dev has switched to developing Gecko Media Player. It still uses MPlayer, but works even better than mplayerplug-in. I highly recommend you install it:
 
**sudo apt-get remove mozilla-mplayer && sudo apt-get install gecko-mediaplayer**
 
The deb is available from [www.getdeb.com](www.getdeb.com) if you want to install it in Gutsy. Enjoy!
 
Nathan

---

### Post by ariel on 2008-05-01
> **reassuringlyoffensive said:**
> Just to let you know, the mplayeplug-in dev has switched to developing Gecko Media Player. It still uses MPlayer, but works even better than mplayerplug-in. I highly recommend you install it:
 
**sudo apt-get remove mozilla-mplayer && sudo apt-get install gecko-mediaplayer**
 
The deb is available from [www.getdeb.com]("http://www.getdeb.com") if you want to install it in Gutsy. Enjoy!
 
Nathan

Hey, thanks for tip!!

Hardy includes this in the repos. Looks cool neat so far, I will use it for a little while and see how it goes.  

It doesn't help with the radiocanada problem but again that is problably an mplayer issue.

---

### Post by ubuntu-freak on 2008-05-01
> **ariel said:**
> Hey, thanks for tip!!

Hardy includes this in the repos. Looks cool neat so far, I will use it for a little while and see how it goes.  

It doesn't help with the radiocanada problem but again that is problably an mplayer issue.

 
No problem. :-)

---

### Post by GordonZola on 2008-06-22
Thanks

---

### Post by kaivalagi on 2008-07-15
Thanks for the guide, the gecko-mplayer install works for the most part. I am running it on Hardy.

However is anyone having issues watching flash content on the bbc news website now? I think they may have changed the requirements? I sed to work for me a few weeks back, but no more.

Flash works fine on the iplayer site, but not on the bbc news site. 

When I visit [http://news.bbc.co.uk/1/hi/uk/7459669.stm](http://news.bbc.co.uk/1/hi/uk/7459669.stm) for example, it is now displaying the message "Cannot play media. You do not have the correct version of the flash player. Download the correct version"

For info, if I follow the adobe link the version of Flash offered is "9.0.124.0"

If this a common problem for everyone now or is it just me?

Any suggestions anyone?

Thanks

---

### Post by ariel on 2008-07-16
> **kaivalagi said:**
> Thanks for the guide, the gecko-mplayer install works for the most part. I am running it on Hardy.

However is anyone having issues watching flash content on the bbc news website now? I think they may have changed the requirements? I sed to work for me a few weeks back, but no more.

Flash works fine on the iplayer site, but not on the bbc news site. 

When I visit [http://news.bbc.co.uk/1/hi/uk/7459669.stm](http://news.bbc.co.uk/1/hi/uk/7459669.stm) for example, it is now displaying the message "Cannot play media. You do not have the correct version of the flash player. Download the correct version"

For info, if I follow the adobe link the version of Flash offered is "9.0.124.0"

If this a common problem for everyone now or is it just me?

Any suggestions anyone?

Thanks

I had this problem two days ago or so, right after a flash update to (I believe) flash 10 beta; the day after they reverted to 9.0.124 and bbc flash videos started to work again. Now, with 8.04 fully updated, I am not having problems.

---

### Post by kaivalagi on 2008-07-16
> **ariel said:**
> I had this problem two days ago or so, right after a flash update to (I believe) flash 10 beta; the day after they reverted to 9.0.124 and bbc flash videos started to work again. Now, with 8.04 fully updated, I am not having problems.

Problem is I am fully updated too :(

I will try removing and re-installing flash again...

Thanks
[COLOR="Blue"]
EDIT: Update just came through today and now flash is working again :) Like you said it must have been a dodgy flash update prior to todays...[/COLOR]

---

