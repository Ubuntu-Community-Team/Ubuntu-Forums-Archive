---
title: "Playing shn (shorten) music files for Hardy using XMMS"
date: 2008-06-18
forum: Multimedia Software
---

### Post by cozmicharlie on 2008-06-18
I wrote this tutorial on how to play shn music files in Hardy ([http://ubuntuforums.org/showthread.php?t=739658](http://ubuntuforums.org/showthread.php?t=739658)).  It was based on using the newest ffmpeg to decode and mplayer to play since ffmpeg now supports shn.  It works fairly well.  I have found an alternative method that I like much better because it involves my favorite music player in Ubuntu, xmms.  XMMS is a lightweight player that just works (if you are looking for the itunes replacement it is not xmms).  Unfortunately, it has been removed from the repos in Hardy and the developers are concentrating on xmms2 (which I don't care for).  Luckily, thanks to Andras Barna ([http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html](http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html)), we can now install xmms on Hardy and the good news - it plays shn "like ringing a bell".  

In this tutorial I will show you how to set up xmms using the method outlined in sartek's blog (including the flac plugin) and the xmms-shn plugin.

Set up xmms in Hardy:  
To do this just follow the steps outlined in sartek's blog ([http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html](http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html)).  Alternatively, a deb is available here ([https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2)).  I used sartek's method but the deb appears to work also ([http://ubuntuforums.org/showthread.php?t=765609](http://ubuntuforums.org/showthread.php?t=765609)).

Set up from source via sartek's method -note this is all done in a terminal so the first step is always open a terminal):
[LIST=1]
[*]Get the required dependencies:
```
sudo apt-get install autotools-dev automake1.9 libtool gettext libasound2-dev libaudiofile-dev \libgl1-mesa-dev libglib1.2-dev libgtk1.2-dev libesd0-dev libice-dev libmikmod2-dev libogg-dev \
libsm-dev libvorbis-dev libxxf86vm-dev libxml-dev libssl-dev build-essential make
```
[*]Create a directory in your HOME directory:
```
# mkdir ~/build
```
[*]Change the working directory to it:
```
# cd ~/build
```
[*]Download XMMS sources:
```
# wget http://xmms.org/files/1.2.x/xmms-1.2.11.tar.gz
```
[*]Unpack it:
```
# tar xvf xmms-1.2.11.tar.gz
```
[*]Change the working directory to the source directory:
```
# cd xmms-1.2.11/

```
[*]Compiling it:
This generates the necessary files, and checks your system:
```
# ./configure --prefix=/usr
```
Then compile
```
# make

```
Install it:
```
# sudo make install
```
[*]If you do not want to install the flac or shn plugin you can delete the source directory:
```
# cd
# rm -rf ~/build
```
[/LIST]

That's it, now we can run XMMS: press ALT+F2 write xmms, hit enter and enjoy your music.

Installing the Flac Plugin
[LIST=1]
[*]We need to get the build dependencies
```
# sudo apt-get build-dep flac
```
[*]Create a ~/build directory (If you did not remove the build directory created above then skip this step):
```
# mkdir ~/build
```
[*]Change to the build directory
```
# cd ~/build
```
[*]Get flac's sources and change to the source directory
```
# apt-get source flac
# cd flac-1.2.1
```
[*]Configure and make
```
# ./configure
# make
```
**It's enough to copy the plugin, you do not need to install the whole flac stuff (that is why their is no # make install).
[*]This is good to do so an update wont break the plugin. (note - you may have to create the .home/yourname/.xmms/Plugins folder for this to work).
```
# cp src/plugin_xmms/.libs/libxmms-flac.so ~/.xmms/Plugins
```
[*]If you are not going to install the shn plugin then you can remove the directory:
```
# cd
# rm -rf ~/build

```
[/LIST]

shn Plugin
[LIST=1]
[*]Make a new ~/build directory (If you did not remove the build directory created above, then skip the first step).
```
# mkdir ~/build
```
[*]Change to the build directory
```
# cd ~/build
```
[*]Get the xmms-shn plugin
```
# wget http://www.etree.org/shnutils/xmms-shn/dist/src/xmms-shn-2.4.1.tar.gz
```
[*]untar the folder and change to the source directory
```
# tar xvf xmms-shn-2.4.1.tar.gz
# cd xmms-shn-2.4.1
```
[*]configure, make and install
```
# ./configure 
# make
# sudo make install
```
[*]After install remove the source directory
```
# cd
# rm -rf ~/build
```
[/LIST]

That's it.  Now press ALT+F2 and enjoy your shn and flac files in xmms.  

To set up a launcher in the applications menu, right click on applications>edit menu>new item>name xmms>command:/usr/bin/xmms.  You can add the xmms icon from the source file /xmms-1.2.2.11/xmms/xmms_mini.xpm.

Enjoy xmms in Hardy and again all the credit for this method goes to Andras Barna at sartek's blog - please stop by his blog and thank Andras.

Enjoy!

---

### Post by matthewbpt on 2008-07-18
this is great man, do you know how i would go about burning shn into an audio cd?

---

### Post by cozmicharlie on 2008-07-18
Glad you found this helpful.

No - not sure how you would do it.  You could convert to flac.  I will look into it and post back.

---

### Post by Samizdat on 2008-08-02
coz-man, thanks for the excellent tutorial.  Everything went without a hitch.  My only unfinished business now is to make an icon.  I don't know how to go about this, because the last time I tried to make an icon, I got a "you're not the owner of this (icons) folder" error message.  I tried to get root access to the icons folder but was unable.  What am I missing?  (Please bear in mind that I am a long-time Windows user and very rusty on the command line -- for instance, it took me a while to remember that "#" meant "commented out" and therefore was not to be copied as code.  In other words, presume that I know next to nothing about the command line).

Thanks again, just heard the late Duane Allman's excellent "The Duane Allman Hour" KPLO 1970 show, thanks to your tutorial and the flawlessly working .shn plugin.  Can't wait to try out FLAC!  Heard about xmms for years, and finally got a taste for myself!

---

### Post by cozmicharlie on 2008-08-04
great - glad to hear it worked for you and I will have to check out the Duane Allman hour.   

I assume you mean that you want to create an icon for the launcher to use.    Below are 3 options for doing this - you can choose whichever one you want.


1. You should be able to get an xmms icon from the folder you downloaded without needing to be root.  If you still have the xmms package in the ~/build folder you should be able to open it without root priveleges.  If you don't have it anymore then you could repeat steps 2-5.  Once you have the xmms untarred in ~/build then go to ~/build/xmms-1.2.2.11/xmms/xmms_mini.xpm (FYI - whenever you see "~" it means the "home" folder).  Then you should be able to access the folder without root.

2.  If you have the icon already in a folder and you cannot access it then do the following:  Open a terminal and type or copy and paste the following. 
```
sudo nautilus
```
The will open nautilus as root and you should be able to browse to the folder and select it.  To change permissions, open properties in the menu and change the permissions.  Change it from root to user (whatever your username is).  

3.  You can also do it via the command line.  
```
sudo chmod 755 "the location of the icon file" (without the quotation marks)
```
So if the icon is in /etc/bin/icons it would be 
sudo chown 755 /etc/bin/icons.

Post back if you are still having problems.

---

### Post by 666porcondissaum on 2008-11-20
Is it working in Intrepid??:confused:

---

### Post by cozmicharlie on 2008-11-21
Yes it is.  I will have to update the tutorial.  

FYI - thier are now a number of different sources for xmms (source files, debs etc).  This thread ([http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=6219325](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=6219325)), especially post # 8, contains a lot of good resources for installing xmms.  It does work in Intrepid.

---

### Post by gychang on 2008-11-21
> **cozmicharlie said:**
> Glad you found this helpful.

No - not sure how you would do it.  You could convert to flac.  I will look into it and post back.

does xmms play flac files?

gychang

---

### Post by cozmicharlie on 2008-11-21
Yes xmms plays flac.  Read through the tutorial and shows you how to set up flac.  FYI - most music players in Ubuntu will play flac.  It is in the repositories and for most all you need is to add it from the repositories.

---

### Post by gychang on 2008-11-22
> **cozmicharlie said:**
> Yes xmms plays flac.  Read through the tutorial and shows you how to set up flac.  FYI - most music players in Ubuntu will play flac.  It is in the repositories and for most all you need is to add it from the repositories.

I am into playing flac files, and will look into xmms.

gychang

---

### Post by shantiq on 2009-12-21
[COLOR=Navy][B]now and late 2009 with karmic koala does this still work ?

i am trying to play .shn which i like as a format

and i have installed xmms and xmms2  but NO SOUND out of xmms altho xmms2 works fine but does not have a shorten plugin or does anyone know of one



thanx for all help     shan


/
[/B][/COLOR]

---

### Post by shantiq on 2009-12-21
[COLOR=Blue][B]:(:(:(:(:) ok call me an idiot

[/B][/COLOR][COLOR=Blue][B] i had not realized that the audio output had to be set manually on the player


[/B][/COLOR][COLOR=Blue][B]it works beautifully well xmms plays shorten files like a dream and i still think shorten files have an amazing sound quality only wavpack gets anywhere near for me

i still think that there are no shorten plugin for xmms2   does any one know different/?

and of course none for qmmp

which is a shame really   NICE FORMAT:):)
[/B][/COLOR]

---

### Post by cozmicharlie on 2010-01-09
> **shantiq said:**
> [COLOR=Blue][B]:(:(:(:(:) ok call me an idiot

[/B][/COLOR][COLOR=Blue][B] i had not realized that the audio output had to be set manually on the player


[/B][/COLOR][COLOR=Blue][B]it works beautifully well xmms plays shorten files like a dream and i still think shorten files have an amazing sound quality only wavpack gets anywhere near for me

i still think that there are no shorten plugin for xmms2   does any one know different/?

and of course none for qmmp

which is a shame really   NICE FORMAT:):)
[/B][/COLOR]

Glad to hear it is working.  Yes - shorten does have good sound quality but so does any lossless format.  The biggest disadvantage I see is the lack of tagging in shn but for sound quality alone you can't beat it. 

I have not seen a shn plug in for xmms2 but you should check out there web site.  They may have a plug in that just is not in the repos.

Enjoy!

---

### Post by cozmicharlie on 2010-01-09
As you can read in shantiq's post, xmms is working in Karmic.  Also, this thread ([http://ubuntuforums.org/showthread.php?t=1312757&highlight=shn](http://ubuntuforums.org/showthread.php?t=1312757&highlight=shn)) has a method for installing in Karmic - see post # 11.  Make sure to install the dependencies that fix GTK 1.2 in Karmic.

Enjoy!

---

### Post by cascade9 on 2010-01-09
> **cozmicharlie said:**
> Glad to hear it is working.  Yes - shorten does have good sound quality but so does any lossless format.  The biggest disadvantage I see is the lack of tagging in shn but for sound quality alone you can't beat it. 

I have not seen a shn plug in for xmms2 but you should check out there web site.  They may have a plug in that just is not in the repos.

Enjoy!

IIRC, seeking doesnt work in shorten files either.  That may or may not be an issue, depending on the person playing the files. 

Shn was great, at the time, but its been blown away by newer lossless formats. If I still had any shn files, I would probably just use soundconverter to turn them into .flac (but I would probably also keep a copy of the original shn files).

---

### Post by shantiq on 2010-01-12
[COLOR=Blue][B];);) yes xmms works a treat in karmic koala

and so does xmms2   BOTH ARE IN THE REPOSITORY xmm2 requires a gui the best i have found so far is esperanza also in the rep

on my internet travels i have found a really good article on xmms and plugins (flac , wma ) [i share it here with you ]("http://colonos.wordpress.com/tag/xmms-in-intrepid/")


[and here too]("http://colonos.wordpress.com/2009/04/27/xmms-in-jaunty-jackalope-904-how-to-install-with-codecs/")



ALSO all the files you need to set up [XMMS including the lib...so ]("http://go2.wordpress.com/?id=725X1342&site=colonos.wordpress.com&url=http%3A%2F%2Fwww.box.net%2Fshared%2Fc1bg60gv7x")


I have also made an ed2k file of it (if you prefer)===>

[/B][/COLOR]> [COLOR=Blue]** ed2k://|file|codecs%20for%20XMMS%20and%20EAC.zip|4025814|545CE4D43D87716EF857DD27DF628672|/**[/COLOR]
[COLOR=Blue][B] 



NOTE   :  ALL of the files and codecs work up to karmic do not be put out if ir says intrepid or hardy they all still work



xmms2 is interesting as it it will play all formats including my beloved shorten

it will also play TTA True audio which some of you might like


[/B][/COLOR][B][COLOR=Navy]the file we have is[   ttaenc-3.4.1-src]("http://sourceforge.net/projects/tta/files/tta/ttaenc-src/ttaenc-3.4.1-src.tgz/download")   this came directly from aleksandr djuric who maintains true audio



[MUCH MORE ON TRUE AUDIO and xmms/qmmp]("http://ubuntuforums.org/showthread.php?p=9279278#post9279278")


it installs     with make and make install    no need for configure


OK the only thing about xmms2 is that you cannot skin [all the beautiful winamp skins ]("http://www.1001skins.com/")and that is a shame but it has medialib browser so you have access to hundreds of alternative radio stations

A programmer could probably make a really good GUI quite quickly  ( Hint hint)


Those two programs  XMMS and XMMS2 are still the most stable i have found in Ubuntu and now there is [Deadbeef]("http://deadbeef.sourceforge.net/") too


They must indeed remain alive             shan;););)
[/COLOR][/B]

---

### Post by shantiq on 2010-05-27
[B][COLOR="Blue"]got a bunch of plugins for lossless formats some of you might welcome


[CENTER][IMG]http://img227.imageshack.us/img227/791/screenshot1ov.png[/IMG][/CENTER]


I have zipped and ed2k'ed all of the plugins for lossless formats here

you need to place these into /home/yourname/.xmms/plugins


and most work straight off on reloading


```
ed2k://|file|codecs%20for%20XMMS%20and%20EAC.zip|4025814|545CE4D43D87716EF857DD27DF628672|/
```


which you can grab through Amule which is in your synaptic

if you cannot be bothered with ed2k drop me a line i shall email them to you (528KB)[/COLOR][/B]

---

### Post by moeshroom on 2010-06-19
With regard to playing Shorten files with  XMMS2, you need the avcodec plugin, which is in the Lucid repo under xmms2-plugin-avcodec .

---

### Post by shantiq on 2010-06-20
**[COLOR="Navy"]ditto for karmic. thanx moeshroom[/COLOR]**

---

### Post by shantiq on 2010-06-22
[B][COLOR="Blue"]and it works in Lucid too. Had problems at first. Track would play but NOT move on to the next one.

I changed from alsa to esound and it has fixed it.


Still the best sound around  although deadbeef is getting close[/COLOR][/B]

---

### Post by cozmicharlie on 2010-07-14
> **shantiq said:**
> [B][COLOR="Blue"]and it works in Lucid too. Had problems at first. Track would play but NOT move on to the next one.

I changed from alsa to esound and it has fixed it.


Still the best sound around  although deadbeef is getting close[/COLOR][/B]

I like Deadbeef but I have not had any luck getting it to play shn.

---

### Post by cozmicharlie on 2010-07-14
Shantiq has posted a helpful update for xmms in Lucid.

[http://ubuntuforums.org/showthread.php?t=1525072&highlight=shn](http://ubuntuforums.org/showthread.php?t=1525072&highlight=shn)

---

### Post by shantiq on 2010-07-14
> **cozmicharlie said:**
> I like Deadbeef but I have not had any luck getting it to play shn.



well cozmik one no shorten in deadbeef sadly;)

still xmms the best and audacious does it too.  xmms2 also but so ugly and so unnattractive to me but at least xmms still good:KS

---

### Post by cozmicharlie on 2010-07-14
> **shantiq said:**
> well cozmik one no shorten in deadbeef sadly;)

still xmms the best and audacious does it too.  xmms2 also but so ugly and so unnattractive to me but at least xmms still good:KS

I didn't know Audacious also plays shn - good news.  Do you find any advantage of XMMS vs Audacious?

---

### Post by shantiq on 2010-07-14
yes one difference on my system is stability


i find xmms really really stable audacious not always so although the newer versions are getting there


but deadbeef has really great sound with the foobar presets but as we have already discussed no shorten there


i am a big shorten fan and would like to see it survive. I still maintain it has a clearer sound than all the others although i have had the word placebo thrown at me by everyone and their dog


do not buy it tho:KS:KS

shorten was designed for recording speeches and lectures  great article [**here**]("ftp://svr-ftp.eng.cam.ac.uk/pub/reports/robinson_tr156.ps.Z") and for reasons which i do not understand it sounds clearer


i feel the same about xmms too that is is clearer  as you ask audacious sounds a little more muffled and qmmp too although not as much

deadbeef i hear almost as good as xmms maybe even better

well those are my observations anyway  ;)   sound heaven is a cd ripped with EAC to shn single file with cuefile and played through xmms with track info on the cuefile monitor :KS:KS:KS

---

