---
title: "How to play YouTube videos and avoid all the Flash kerfuffle...."
date: 2014-02-11
forum: Multimedia Software
---

### Post by shantiq on 2014-02-11
summerized**= Basically bypass ALL browsers   ...   **and enter url into a player!


I may be stating the obvious to many of you here but 4 years into using Ubuntu it has just dawned on me that it is easy to view Youtube videos so they do not check appallingly with Flash; Pepper and other Gnash ....

with terminal     


simply

do this:


```
cvlc Your_YouTube_url
```


[B]and smooth; no checks !

[/B]will only play up to 1280x720  but that is quite good  [if anyone knows how to go higher 1920x1080 or even 4k please say]   i think youtube changed the way it delivers videos [DASH]hence limitation for terminal playback; both mpv and vlc only play the mp4 and do not "see" the DASH

```
Available formats:22    :    mp4    [720x1280]
18    :    mp4    [360x640]
43    :    webm    [360x640]
5    :    flv    [240x400]
36    :    3gp    [240x320]
17    :    3gp    [144x176]
136    :    mp4    [720p] (DASH Video)
135    :    mp4    [480p] (DASH Video)
134    :    mp4    [360p] (DASH Video)
133    :    mp4    [240p] (DASH Video)
160    :    mp4    [192p] (DASH Video)
140    :    m4a    [128k] (DASH Audio)
171    :    webm    [128k] (DASH Audio)
```


or you can use [mpv]("https://launchpad.net/~mc3man/+archive/mpv-tests")   again easy   **AND **navigation is easier faster   

```
mpv Your_YouTube_url
```


or not as  simple [that i know of]

[mplayer]("http://www.commandlinefu.com/commands/view/1405/stream-youtube-url-directly-to-mplayer.") [requires youtube-dl installed too]


```
mplayer -fs -cookies -cookies-file /tmp/cookie.txt $(youtube-dl -g --cookies /tmp/cookie.txt "Your_YouTube_url")

```


Again probably obvious to many  ...    but as i said i for one never thought of it before  ::}}
mpv cvlc mplayer  [for me here in order of smoothness]

**EDIT **  also use [Bomi]("http://bomi-player.github.io/")   smooth fast stable

---

### Post by monkeybrain20122 on 2014-02-11
A smooth and easy way that also works for many flash sites other than Youtube is [http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011) it uses mplayer, mplayer2 or totem as backend. 

There is also [http://linternamagica.org/](http://linternamagica.org/) Pros: works for more sites than Viewtube because it uses a different approach by dynamically detecting flash object, so even works for random sites not explicitly supported. cons: may not work for some popular Youtube channels (such as Vevo) because developer doesn't have time to keep up with google's changes (3-5 days) and some webpages may freeze  the browser because there are too many flash objects. Since LM loads automatically (viewtube starts only when user clicks 'play') such sites would have to be manually excluded.

mpv doesn't hav a gui that works with a web plugin (gecko-mediaplayer  uses gnome-mplayer which can use mplayer or mplayer2) so it won't work  with these scripts. In fact I am not sure what to make of mpv. It sounds  powerful but the absence of any web plugin and decent gui (Smplayer is  not supported) means that I am sticking to mplayer2.I know mplayer2 seems to  be dead at the moment, but it will probably work for a long while, when  it doesn't I will just switch back to mplayer unless mpv supports web  plugin and have a gui as good as Smplayer. While I can do it for debugging, I really  hate the idea of playing movies with cryptic terminal commands and having to type in or cut and paste movie file names and paths, it sounds so  1990's and it is a great and sure fire way to keep desktop Linux usage to 1-2% [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]

If you don't need to watch in the browser and only care about Youtube there are also smtube (Smplayer) and minitube, though smtube hasn't been updated for a while and the dev's automatic algorithm to keep up with google's changes seems to be broken.

I heard Vlc also has a Youtube browser addon, but I have never used it.

---

### Post by mc4man on 2014-02-11
The vlc FF addon works pretty good, usually delivers 1280x720  (the rec button is not disabled.

Always found interesting that 720p Yt generally has slightly better audio then the 1080p,  (I sometimes remux in that which cannot be mentioned...

(- for local files I only use mpv now which can be 'improved' upon by altering it's .desktop & thru .mpv/config, .mpv/plugin_osc.conf

---

### Post by shantiq on 2014-02-24
some of you may have seen this elsewhere : [pmsyt]("http://www.webupd8.org/2014/02/new-command-line-youtube-player-and.html") is one more way to listen and or view YouTube which bypasses Flash

one more reason to install [mpv]("https://launchpad.net/~mc3man/+archive/mpv-tests")


then try this maybe      Peter Hook & The Light - 'Decades' live @ Tele-Club  ::]]

---

### Post by mc4man on 2014-02-24
shantiq - 
ot for sure but thought I'd mention to you
Here I have a 1920x1080 screen but when opening smaller vids in an mpv window I like then to be centered
So just to give an ex. - 
In ~/.mpv/config this will always center an vid
```
# Write your default config options here!
geometry=50%:50%
```

Also have been fooling around a bit with Osc, I prefer it to only expose on cursor in bottom & be a bit smaller (still experimenting with that...
This is managed in ~/.mpv/plugin_osc.conf  (file needs to be created if not there..

My current - 
```
deadzonesize=1
valign=1
scalefullscreen=0.5
scalewindowed=0.75
```

Also to mention I just added a pdf version of the man pages, can be found in /usr/share/doc/mpv
(some readers require it to be extracted, others don't

---

### Post by monkeybrain20122 on 2014-02-24
You can also play all Youtube videos with html5 [https://addons.mozilla.org/en-US/firefox/addon/youtube-all-html5/](https://addons.mozilla.org/en-US/firefox/addon/youtube-all-html5/)
But you have to disable flash for it to work.

There are so many solutions for Youtube that flash or no flash is not really an issue, it is the last thing that one should fret about. But Youtube != flash,  there are other sites that use flash and especially drm enabled one, there is really no native Linux solution (hal is deprecated and only works with outdated flash if at all), as far as I know the only way that works for such use cases would be a wine hack (pipelight)

P.s Linterna magica has fixed the browser freezing issue. It is highly recommended because it works on many sites besides Youtube.[http://linternamagica.org/](http://linternamagica.org/)

---

### Post by shantiq on 2014-02-25
MB thanx for info...    personally i have had poor results with html5    worse than flash for me here  ,,,   hence really my thread here   i have tried them all  ....   all those browser routes  ... pepper gnash etc etc

that is why i favour [mpv]("https://launchpad.net/~mc3man/+archive/mpv-tests") cvlc route nowadays or even [pmsyt]("http://www.webupd8.org/2014/02/new-command-line-youtube-player-and.html") [poor man spotify you tube] [i joke you not!]

mpv is the best player i have ever had    smooth  fast  navigation even when streaming  ....    if others get joy out of browsers and video all the best to them

in 5 years i never have  ...    but now i do not longer care as the **no-browser route** is indeed [to me now]   excellent   ...    i put the info out for others who might be in the same boat


PS also thanx mc4man for fine-tuning info on mpv

---

### Post by monkeybrain20122 on 2014-02-25
Sort of related. Manage to get hardware acceleration for flash on this borrowed intel machine following the instructions at
[http://www.webupd8.org/2013/09/adobe-flash-player-hardware.html](http://www.webupd8.org/2013/09/adobe-flash-player-hardware.html) (on Nvidia machines hardware acc + flash always crashes but here it is ok)
But it seems that hardware acceleration only works on Youtube (and it works really well) but not other flash sites.

Also compiled mpv from svn because vaapi doesn't work with mplayer/mplayer2. vlc uses vaapi but not as efficient as mpv (mpv uses ~ 1/2 the cpu as vlc for the same 1920x1080 videos, both with vaapi option on).It's seeking function is also smoother than vlc's. I would prefer a gui like smplayer, but I can live with right clicking.

---

### Post by mc4man on 2014-02-25
I find the 3 (vlc, mplayer,mpv) to be quite similar in cpu use  when using accel., slight edge to mplayer, all about 15% of when not.
This is on a nvidia 660m using Intel 4000 side though the newer the hardware the less or no  need for accel for video playback.
In general I now use mpv for local vids & vlc for online as it almost never fails (404 or whatever

For mpv & vdpau on intel just created a new .desktop as such -  pared down the Mimetypes from my 'normal' mpv.desktop
```
[Desktop Entry]
Version=1.0
Type=Application
Name=mpv vdpau
GenericName=Multimedia player
Comment=hw decoding thru va_gl
Icon=/usr/share/icons/hicolor/32x32/apps/mpv.png
TryExec=/usr/bin/mpv
Exec=env VDPAU_DRIVER=va_gl mpv --really-quiet --force-window  --hwdec=vdpau --vo=vdpau  %U
Categories=AudioVideo;Video;
MimeType=video/mpeg;video/x-mpeg;video/msvideo;video/quicktime;video/x-anim;video/x-avi;video/x-ms-asf;video/x-ms-wmv;video/x-msvideo;video/x-nsv;video/x-flc;video/x-fli;video/x-flv;video/vnd.rn-realvideo;video/mp4;video/mp4v-es;video/mp2t;video/x-ogm+ogg;application/x-matroska;video/x-matroska;video/webm;application/vnd.rn-realmedia;application/x-shockwave-flash;application/x-extension-mp4;x-content/video-dvd;
```

---

### Post by andrew.46 on 2014-02-25
> **monkeybrain20122 said:**
> If you don't need to watch in the browser and only care about Youtube there are also smtube (Smplayer) and minitube, though smtube hasn't been updated for a while and the dev's automatic algorithm to keep up with google's changes seems to be broken.

Perhaps fixed now, certainly it updated itself and is working nicely today...

---

### Post by monkeybrain20122 on 2014-02-25
> **mc4man said:**
> I find the 3 (vlc, mplayer,mpv) to be quite similar in cpu use  when using accel., slight edge to mplayer, all about 15% of when not.
This is on a nvidia 660m using Intel 4000 side though the newer the hardware the less or no  need for accel for video playback.
In general I now use mpv for local vids & vlc for online as it almost never fails ..

I am able to make mplayer use vaapi through vdpau on this machine (Vga intel ironlake mobile with i915 driver) with libvdpau-va-gl. CPU usage is on par with mpv using vaapi directly and better than vlc (~15% vs ~30%) Without vaapi cpu usage for these samples would be around 80% to 90%. In general it works except for one video clip with very high frame rate where the video and audio is totally out of sync after a while and mplayer gives the warning that the machine is too slow for this (both mpv and vlc work smoothly with vaapi and smplayer with vdpau turned off) 

I think mpv is a very efficient player but lacking features for general use at the moment, for example it doesn't really have a volume control (??) and found this on their forum
> The mission of mpv is to have clean code and have faster development,  hopefully attracting new developers. It is stated in the changes. It's  not about users and actually too many users hinder the project if the  developer count stays the same. 

Not sure if this is "the mission of mpv" or just one guy's opinion. [https://github.com/mpv-player/mpv/issues/103](https://github.com/mpv-player/mpv/issues/103)

Apologies to OP, definitely going off topic here. :)

P.S. I put mpv's options in its .config file and keep the .desktop file very simple, just so that I can find it in the "open with" menu, basically same thing.

---

### Post by shantiq on 2014-02-26
> **andrew.46 said:**
> Perhaps fixed now, certainly it updated itself and is working nicely today...


Thanx MB and Andrew had never seen [Smtube]("http://handytutorial.com/install-smtube-youtube-browser-for-smplayer-in-ubuntu-using-ppa/")  before ...   one more cool way  ...  probably would personally still favour terminal way  ...   and yes nice to see smplayer is working again,   had not at first on 13.10 for me


[[IMG]http://s20.postimg.org/lebv93hg9/smtube.jpg[/IMG]]("http://postimg.org/image/lebv93hg9/")

so to install

```
[COLOR=#333333]sudo add-apt-repository ppa:rvm/smplayer[/COLOR]
```   and enter

then  ```
[COLOR=#333333]sudo apt-get update ; [/COLOR][COLOR=#333333]sudo apt-get install smplayer smtube[/COLOR]
```

---

### Post by andrew.46 on 2014-02-26
Mind you I am a little curious as to how SMTube adapts to altered youtube conditions 'on the fly'. It could not be altering the compiled code surely, there must be a configuration file that I certainly could not find...

---

### Post by mc4man on 2014-02-26
> **andrew.46 said:**
> Mind you I am a little curious as to how SMTube adapts to altered youtube conditions 'on the fly'. It could not be altering the compiled code surely, there must be a configuration file that I certainly could not find...

Maybe -  ~/.config/smplayer/ytcode.script

---

### Post by monkeybrain20122 on 2014-02-26
> **shantiq said:**
> 

```
[COLOR=#333333]sudo add-apt-repository ppa:rvm/smplayer[/COLOR]
```   and enter

then  ```
[COLOR=#333333]sudo apt-get update ; [/COLOR][COLOR=#333333]sudo apt-get install smplayer smtube[/COLOR]
```

Actually smtube in the ppa has not been updated for 29 weeks and it is broken, kind of. While it works for most videos it no longer works for 'protected' channels like vevo, for example. Thanks to Andrew.46's heads up above I found that smtube was updated two days ago in the svn channel. It will probably be uploaded to the ppa soon but I just compiled from source. This one works for all channels. There is only one small glitch. somehow, even with the prefix=/usr option it got installed in /usr/local/bin so smplayer could not find it even after running ldconfig. Making a symlink to /usr/bin fixed the problem. (to install in the chosen prefix needs to do: sudo make prefix=xxx install, but I prefer to use checkinstall but it doesn't remember the prefix from configure somehow)

---

### Post by andrew.46 on 2014-02-26
> **mc4man said:**
> Maybe -  ~/.config/smplayer/ytcode.script

As usual you are right on the ball mc4man :). I renamed this file and when prompted to 'update' for youtube changes this file was generated. A quick grep through the SMPlayer source shows the source of the downloaded file will be [here]("http://updates.smplayer.info/ytcode.script"), at least for SMPlayer 0.8.6:

```

andrew@ilium~/source/mplayer_build/smplayer/smplayer-0.8.6$ **[COLOR="#FF0000"]grep -R ytcode.script .[/COLOR]**
./src/cleanconfig.cpp:  s = config_path + "/ytcode.script";
./src/basegui.cpp:      downloader->saveAs(Paths::configPath() + "/ytcode.script");
./src/basegui.cpp:      downloader->download(QUrl("**[COLOR="#800080"]http://updates.smplayer.info/ytcode.script[/COLOR]**"));
./src/core.cpp:         YTSig::setScriptFile( Paths::configPath() + "/ytcode.script" );

```

Fascinating stuff...

---

### Post by monkeybrain20122 on 2014-03-02
Just found out that smtube can  be configured use mpv to play Youtube instead of smplayer (or totem, or vlc)  Didn't know that before. :)

---

### Post by shantiq on 2014-03-03
how do you add the mpv option MB?

---

### Post by monkeybrain20122 on 2014-03-03
The option is already there. Look at the little screw driver icon next to the search bar in the bootom. click it and there is a box where you can choose the player. It listed smplayer, vlc, mpv, gnome-mplayer and totem (I don't know how it get there. :))

I compiled smtube from source and mpv was already installed so maybe that's why it has that option? I install mpv in $Home/bin but made a symlink to /usr/bin

---

### Post by shantiq on 2014-03-03
i installed mpv [this way]("https://launchpad.net/~mc3man/+archive/mpv-tests")  and i am not too sure how to make the mpv option appear   it is situated here  > ./usr/bin/mpv    this is not too important but i am just curious :)

---

### Post by monkeybrain20122 on 2014-03-03
I installed mpv from [https://github.com/mpv-player/mpv](https://github.com/mpv-player/mpv) 
I installed it in $HOME/bin and then symlink it to /usr/bin. It created a .desktop file and I just moved it to .local/share/applications.
Then I compiled smtube from the latest tarball. That was it.

---

### Post by mc4man on 2014-03-03
> **shantiq said:**
>  not too sure how to make the mpv option appear   it is situated here      this is not too important but i am just curious :)
    You need the latest smtube source  that has mpv added to  players.cpp
    I believe there was 2 changes, you'd want the latest that works better
    The advantage there is it allows mpv to play back Vevo yt vids which I've found impossible to do straight up.
    (tried some things lately, none worked, probably some deficiency in either quvi or mpv or both though the only player I've found that can directly play Vevo is vlc

Though not sure what vid quality you'd get thru smtube/mpv if using the default opengl or xv, myself still prefer vlc for online though mpv using vdpau is ok here...

---

### Post by monkeybrain20122 on 2014-03-03
> **mc4man said:**
> You need the latest smtube source  that has mpv added to  players.cpp
    I believe there was 2 changes, you'd want the latest that works better
    The advantage there is it allows mpv to play back Vevo yt vids which I've found impossible to do straight up.
    (tried some things lately, none worked, probably some deficiency in either quvi or mpv or both though the only player I've found that can directly play Vevo is vlc

Though not sure what vid quality you'd get thru smtube/mpv if using the default opengl or xv, myself still prefer vlc for online though mpv using vdpau is ok here...


With the latest smtube everything plays vevo, even totem 

vlc and mpv both set to use vaapi, but mpv uses about half the cpu and for vlc has to switch audio to alsa or the picture may freeze leaving only audio, that goes with local files as well. mpv uses pulseaudio with no issue. Smplayer uses vaapi via vdpau with the experimental libvdpau-va-gl driver, again has to use alsa for audio, cpu usage is as good as mpv though can't play some local files smoothly while vlc and mpv both can.

Smtube used to be able to play Vevo,--I only used it with Smplayer before so not sure about other players. It used some algorithms to keep up with google's changes until may be two months ago when Google appeared to have broken smtube's automatic algorithm.

---

### Post by mc4man on 2014-03-03
> **monkeybrain20122 said:**
> With the latest smtube everything plays vevo, even totem 


In that regard I meant directly from player, thru smtube they all work, ex. of directly
```
vlc https://www.youtube.com/watch?v=C-dW7z0QBNg

```

As far as cpu use all the possible variations/players ect. there isn't really much difference here if using vaapi or vdpau, typically equal to about 6% of 1 cpu

---

### Post by shantiq on 2014-03-04
ok did all this

svn co [https://subversion.assembla.com/svn/smplayer/smplayer/trunk/](https://subversion.assembla.com/svn/smplayer/smplayer/trunk/) smplayer


software-properties-gtk    and remove earlier smplayer smtube packages


cd smplayer ; ./create_deb.sh


sudo dpkg -i smplayer_0.8.6-SVN-r6052_amd64.deb


so got latest smplayer




then

used  

**[smtube-1.8.tar.bz2]("http://downloads.sourceforge.net/smplayer/smtube-1.8.tar.bz2")  from ** [http://smplayer.sourceforge.net/en/downloads](http://smplayer.sourceforge.net/en/downloads)


and made a deb but no mpv showing  ...    what did i miss/not see/understand here?

---

### Post by monkeybrain20122 on 2014-03-04
You got the latest Smplayer but apparently an old smtube.

The tar.bz2 you downloaded is old. I got it from [https://www.assembla.com/code/smplayer/subversion/nodes/6052/smtube](https://www.assembla.com/code/smplayer/subversion/nodes/6052/smtube)
Compare the change logs. mpv was added Dec15 2013. The tar.bz2 was around Aug 2013, I think it is the same version in the rvm ppa which hasn't been updated for 30 weeks.

---

### Post by shantiq on 2014-03-04
hmmm thanx MB   what do i do with that zip ?    tags and trunks ???     do i need to create 2   debs and in which order?  and if so 1.5 in tags?        sorry   not all that familiar with svn ways

---

### Post by monkeybrain20122 on 2014-03-04
Hi,

unzip it, cd into trunk
then run 
```
./create_deb.sh
```

Or, alternatively, in trunk, run
```
./get_svn_revision.sh
make
sudo checkinstall

```

This will create a .deb and install in /usr/local

**Edited:** Never mind tags, looks like just the source codes for a bunch of old versions.

---

### Post by shantiq on 2014-03-04
Thanx MB got there :}

---

### Post by vasa1 on 2014-09-09
I installed mpv from the Software Center but found that its .desktop file had **NoDisplay=true**. I wonder why. Anyway, commented it out.

---

### Post by mc4man on 2014-09-09
> **vasa1 said:**
> I installed mpv from the Software Center but found that its .desktop file had **NoDisplay=true**. I wonder why. Anyway, commented it out.

Well there is no reason to display mpv in the Dash or an application menu as it can't run without a target file.
The 14.04 mpv package is basically worthless, 14.10 is a bit better. (but 14.10 is basically worthless...
(- i've a slower to update mpv for  14.04[ here]("https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests"), uses quvi 0.4, an often updated one [here]("https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media"), uses quvi 0.9, though note that at some point quvi is going to be of little value as dev as stopped. Both builds are far better than anything Ubuntu will/can produce

For me best option is smtube set to use mpv for playback.

---

### Post by vasa1 on 2014-09-09
> **mc4man said:**
> Well there is no reason to display mpv in the Dash or an application menu as it can't run without a target file....
For me best option is smtube set to use mpv for playback.
I see. I use Lubuntu and wanted to set mpv as my "always open with" and didn't see it under any category because of the NoDisplay=true.
I guess this is one example of the niggles non-Unity users encounter.
I'll also look at smtube. Thanks!

---

### Post by mc4man on 2014-09-09
> **vasa1 said:**
> I see. I use Lubuntu and wanted to set mpv as my "always open with" and didn't see it under any category because of the NoDisplay=true.
I guess this is one example of the niggles non-Unity users encounter.
I'll also look at smtube. Thanks!

It's more  a  Gnome/nautilus deal  where  default changes or context menu options are based on the MimeType= line & having a %<letter> at end of the Exec= in an app's .desktop

---

### Post by mc4man on 2015-02-20
> **vasa1 said:**
> I installed mpv from the Software Center but found that its .desktop file had **NoDisplay=true**. I wonder why. Anyway, commented it out.
Typically mpv needs a target file so really no use opening directly, that's why the NoDisplay=true

Recent versions now have an option --idle This will open mpv with an 'empty' window suitable for DnD. Also with --idle when a vid is done instead of closing you get the DnD window.
(small issue with that in Unity when opening a vid as big or larger than display size height wise, likely won't be fixed - [https://github.com/mpv-player/mpv/issues/1598](https://github.com/mpv-player/mpv/issues/1598)

ex. in screen
To use adjust mpv.desktop Exec= line to - 
```
Exec=mpv --no-terminal --force-window --idle -- %U
```

Haven't decided whether to add this to ppa builds, maybe  not as, at least in unity,  a launcher icon is good for DnD on supported mimetypes. If it was added then it could rightly be NoDisplay=false

(have recently  added a quicklist entry to open the  man pages in Evince, unity only. Note that official Debian/Ubuntu builds don't create a pdf of the man pages,  too bad there as it's an excellent means to view. 
Ex. added to bottom of mpv.desktop
```
Actions=Help;

[Desktop Action Help]
Name=Open Man pages in Evince
Exec=evince /usr/share/doc/mpv/mpv.pdf.gz
TargetEnvironment=Unity



```

---

