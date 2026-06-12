---
title: "why is it that creating DVD movies in linux is such a beetch"
date: 2008-08-05
forum: Multimedia Software
---

### Post by tuxulin on 2008-08-05
with linux being the greatest OS in the world
why is it that one has to be a rocket scientist to get avi and mpg
files converted to DVD such a pain.... here is my situation 

1, i have a avi file called movie.avi witch is 948Mb in size

2, i then used ffmpeg -i movie.avi -target pal-svcd movie.mpg
     the movie.mpg file size is now 1.3Gig after conversion

3, next comes the VIDEO.TS and IFO files.
     dvdauthor --title -o dvd -f movie.mpg

this is the eorrors result i always get 
WARN: Skipping sector, waiting for first VOBU…
WARN: Skipping sector, waiting for first VOBU…
WARN: Skipping sector, waiting for first VOBU…
ERR: SCR moves backwards, remultiplex input.

even after remultiplexing the input i still get the 
same errors..... 
so for the time being i had to install Virtual Box
then install WinCrap XP to get my mpeg to dvd sorted

i know creating dvd on linux is still pretty much 
difficult but is there a good guide that i can read  
with strong outcomes that creating a dvd will work.

here are some good links that i have hunted down and didnt
work for me..... however if one or more of these links work
for you then please return here and let me know what you did
thank you

[http://www.linux.com/feature/53702](http://www.linux.com/feature/53702)
[http://movabletripe.com/archive/merging-avis-into-a-single-dvd-on-linux/](http://movabletripe.com/archive/merging-avis-into-a-single-dvd-on-linux/)
[http://dvdauthor.sourceforge.net/doc/index.html](http://dvdauthor.sourceforge.net/doc/index.html)
[http://forums.gentoo.org/viewtopic.php?t=117709](http://forums.gentoo.org/viewtopic.php?t=117709)
[http://www.videohelp.com/dvd](http://www.videohelp.com/dvd)

---

### Post by Circus-Killer on 2008-08-05
have to agree with you there.
ive also searched high and low, but have never found anything substantial. I did find qdvdauthor, but like all the other linux dvd authoring tools, it tends to be quite a mission.

maybe im just a noob, but creating new dvds is one of the few things i haven't managed to get right.

---

### Post by kpkeerthi on 2008-08-05
I use [tovid]("http://tovid.wikia.com/wiki/Tovid_Wiki") CLI version.

---

### Post by Pauly Psychotic on 2008-08-05
You just need to find the right program. If you are converting an .avi file you will want either ToDisc [http://tovid.wikia.com/wiki/Main_Page]("http://tovid.wikia.com/wiki/Main_Page") or you can use DeVede (It's in the repositories) I use both just because I have the choice. If you are backing up DVDs I recommend K9Copy.

---

### Post by cchester on 2008-08-05
Hello,

May I suggest using ManDvd. I have been using it for a while and it works great for me. You pick which file you want to make into a dvd and you can either make menus or have it just start the movie when you insert the disc without a menu. It will convert the movie for you and then create the files needed to burn to Dvd. It then gives you the option to preview the movie before burning and if it is ok then it will burn the movie to Dvd or you can have it make an iso file so you can burn it later.

It is very fast in converting and I have never had any problems with it converting or playing Dvds made by it afterwards.

You can get ManDvd at getdeb by clicking [http://www.getdeb.net/app/ManDVD]("http://www.getdeb.net/app/ManDVD") my link to it if the link doesn't work just goto the site and search for it and pick the most recent version and use Ubuntu's built in deb installer and it will get any dependencies that you may need if any.

Hope it helps and let me know how it works out for you.

---

### Post by tuxulin on 2008-08-05
thank you for all the replies. much appreciated. :)
from the top im (as i type) currently doing a conversion
in tovids and have seen no errors yet.

first i tried it on a sample file 10Mg in size and all appeared
to go well, though i didn't burn it to disc instead i viewed it in 
a DVD player. so currently im doing the real deal.

ill be back in a few hours (after conversion is completed) to say
if it was a hit or miss.

if tovids a hit then ill stick with it if not then ill move to the 
next suggestion... wow my life runs like a bash script LOL
 

Pauly Psychotic - 
i have tested Devede and that came with errors thanks for the tip though.
:)

cchester
i have never heard of ManDVD but ill check it out 

thanks again
Tuxulin

---

### Post by tuxulin on 2008-08-06
and here i am again 
i did try the suggested software above but errors came at me from different
stages... personally i found some of the apps quite ok and where packed 
with features that are needed for users who know what they are doing with
video files. unlike them me, just a simple newbee who get lost just by 
looking at avidemux and others in that category.

i did like "Tovid" but the problem i notice with it is that it didnt build
a dvd structure for the most of my avi's and the burning facility just 
does not work at all.

however im not here to knock any of the programs they all are great and
serves great justice to those that know how to use them.

lastly before i lay this post to rest i must say that i did notice a 
common factor between most if not all these programs.

1 - to convert avi to mpg seemed very easy to do for all of them
2 - to build the DVD structure from MPG seemd a little hard for them to do
3 - for those that could build the structure had problems writing to DVD

***** when i say "DVD structure" im talking about ********* 
the DVD files AUDIO_TS, VIDEO_TS, *.bup, *.ifo and *.vob files

so back to my situation  
i solved the situation in another and what seemed like a simpler method
im not a pro and so i dont need menus and menu music. all i want to do 
is put my DVD-RW in the player and watch the movie.

this is what i done
--------------------

1 - transcode -i movie.avi -y ffmpeg --export_prof dvd-ntsc --export_asr 
-o movie -D0 -s2 -m movie.ac3 -J modfps=clonetype=3 --export_fps 29.97

****--export_asr 2 for fullscreen or --export_asr 3 for wide screen ****

2 - mplex -f 8 -o dvd_movie.mpg movie.m2v movie.ac3

3 - create a text file with the contents below (without dotted lines)

------------------------START----------------------
<dvdauthor dest="DVD">
  <vmgm />
   <titleset>
     <titles>
       <pgc>
         <vob file="dvd_movie.mpg"chapters="0,15:00,30:00,45:00,1:00:00"/>
       </pgc>
      </titles>
   </titleset>
 </dvdauthor>
------------------------END------------------------
save the new file as dvdauthor.xml in the same directory as your movie files

4 - dvdauthor -x dvdauthor.xml
******* this will create two AUDIO_TS and VIDEO_TS directories in your DVD directory and in the VIDEO_TS will create a few vob's, ifo's, bup's
files

****** in step 5 change "~/tmp/DVD/VIDEO_TS/" to your path to the DVD 
5 - make sure the DVD work by using. xine dvd:~/tmp/DVD/VIDEO_TS/


6 - get a rewiteable and use K3b to write the files to disk or 
burn the DVD contents with cdrecord or growisofs


***********************************************************************
for those on GUI
when you select create a new movie dvd in K3b you will notice
that K3b will create the AUDIO_TS and VIDEO_TS as part of the project.

what i did was to go to my ~/tmp/DVD/VIDEO_TS using nautilus and copied 
and drag the contents from the VIDEO_TS directory to the same directory
in K3b. hit burn 8 minutes later take out the CD and go watch you film.

i think ill write a bash script so the whole process can be a bit smooth in a few weeks of so.

thank you all for replying your input did help alot.

Tuxulin   :)

---

### Post by yabbies on 2008-08-06
with tovid all you have to do is open a terminal

```
tovid -in movie.avi -out movie
```
this will make a mpg
if you want widescreen add -wide and if you need pal add -pal

after conversion
you need to make xml for chapters

```
makexml movie.mpg -out movie
```
this will make an xml file

now create and burn a disc structure, pop in a blank disc and

```
makedvd -burn movie.xml
```

simple
three commmands no rocket scientistry(if that's even a word)

---

### Post by cchester on 2008-08-07
> **tuxulin said:**
> and here i am again 
i did try the suggested software above but errors came at me from different
stages... personally i found some of the apps quite ok and where packed 
with features that are needed for users who know what they are doing with
video files. unlike them me, just a simple newbee who get lost just by 
looking at avidemux and others in that category.

i did like "Tovid" but the problem i notice with it is that it didnt build
a dvd structure for the most of my avi's and the burning facility just 
does not work at all.

however im not here to knock any of the programs they all are great and
serves great justice to those that know how to use them.

lastly before i lay this post to rest i must say that i did notice a 
common factor between most if not all these programs.

1 - to convert avi to mpg seemed very easy to do for all of them
2 - to build the DVD structure from MPG seemd a little hard for them to do
3 - for those that could build the structure had problems writing to DVD

***** when i say "DVD structure" im talking about ********* 
the DVD files AUDIO_TS, VIDEO_TS, *.bup, *.ifo and *.vob files

so back to my situation  
i solved the situation in another and what seemed like a simpler method
im not a pro and so i dont need menus and menu music. all i want to do 
is put my DVD-RW in the player and watch the movie.

this is what i done
--------------------

1 - transcode -i movie.avi -y ffmpeg --export_prof dvd-ntsc --export_asr 
-o movie -D0 -s2 -m movie.ac3 -J modfps=clonetype=3 --export_fps 29.97

****--export_asr 2 for fullscreen or --export_asr 3 for wide screen ****

2 - mplex -f 8 -o dvd_movie.mpg movie.m2v movie.ac3

3 - create a text file with the contents below (without dotted lines)

------------------------START----------------------
<dvdauthor dest="DVD">
  <vmgm />
   <titleset>
     <titles>
       <pgc>
         <vob file="dvd_movie.mpg"chapters="0,15:00,30:00,45:00,1:00:00"/>
       </pgc>
      </titles>
   </titleset>
 </dvdauthor>
------------------------END------------------------
save the new file as dvdauthor.xml in the same directory as your movie files

4 - dvdauthor -x dvdauthor.xml
******* this will create two AUDIO_TS and VIDEO_TS directories in your DVD directory and in the VIDEO_TS will create a few vob's, ifo's, bup's
files

****** in step 5 change "~/tmp/DVD/VIDEO_TS/" to your path to the DVD 
5 - make sure the DVD work by using. xine dvd:~/tmp/DVD/VIDEO_TS/


6 - get a rewiteable and use K3b to write the files to disk or 
burn the DVD contents with cdrecord or growisofs


***********************************************************************
for those on GUI
when you select create a new movie dvd in K3b you will notice
that K3b will create the AUDIO_TS and VIDEO_TS as part of the project.

what i did was to go to my ~/tmp/DVD/VIDEO_TS using nautilus and copied 
and drag the contents from the VIDEO_TS directory to the same directory
in K3b. hit burn 8 minutes later take out the CD and go watch you film.

i think ill write a bash script so the whole process can be a bit smooth in a few weeks of so.

thank you all for replying your input did help alot.

Tuxulin   :)

Did you try ManDvd like I said? If so what problems did you have. Did you grab the newest version and right version for your system. Did it grab all the dependencies? Honestly I find it the easiest for making dvds and everyone I have shown it to that is new to Linux and Ubuntu have learned how to make dvds with it no problem.

Let me know matbe I can help. I am attaching a couple of files for you that I use and have given to others. They are not my creation but should help.

   How to convert DivX/XviD/MPEG to DVD with menu using manDVD  	Print	Print
I consider myself a rather old Linux user. I remember playing around with Slackware and failing to complete the installation, then getting a copy of Corel Linux (yes, it did exist!) before using Redhat, then SuSE and finally ending up with Ubuntu since version 4.10. During those years the growth of Linux desktop has been amazing. From fighting with the command line or trying for hours to play a video file, nowadays Linux is the desktop leader in features and effects with projects like Compiz that generate amazing 3D effects much better than the ones in the much advertised Windows Vista.

Of course not only Linux matured but the applications that run on the platform did as well. I remember I used to boot my Windows partition almost only to use video tools, like ConvertXToDVD or Nero as I couldn't find a working choice on Linux. However this is no longer the case. There are many great video applications for Linux, some of them even better than commercial ones for Windows, all of them not just free but open source as well! This guide is the first one in a series of guides we will add about Linux video programs. The program we will use is ManDVD, a frontend for many command line tools. Let me tell you beforehand that this program is simply amazing. The amount of the tasks it can achieve is enormous, the GUI is simple and the control you have over the DVD you are creating is almost perfect.

Tip	You can download ManDVD for various Linux distributions from here. It needs quite a few programs and depends in many KDE libs so downloading a deb or rpm is preferred over compiling the source. For your information I am running Ubuntu in the PC I used for the guide.

Step1
ManDVD01

When you open ManDVD you will see this screen. Here you should first of all set the Destination folder (1). Make sure it has at least 5GB of free space. Then you should select between PAL and NTSC and set the resolution (better use the default 720 one) (2) or open a saved project file (3). Finally click Confirm to start using the program.

Step2
ManDVD02

This is the main manDVD window. The first step is to add your files. Obviously selecting "Add a video to your project" (1) will allow you to select a file to add to the DVD. The Add file dialog is explained below. Looking at the other options (2) - "Modify title" changes the video's title for the menu and "Remove selected video" removes it from the project. The "Create a slide show" is an amazing option that lets you add a slide show in the DVD among your videos. It will be further explained in a future guide.

Then we have the editing options (3). "Cut a part of this film" is pretty obvious that allows you to cut parts that you don't want from the file, "Define chapters" sets the chapters of the video (this is where the DVD player stops when you press "Next" in your controller), and "Subtitle management" allows you to add external subtitles to your film. Finally there is the "Video effects" option which allows you to apply some interesting effects like Delogo (remove a logo from a certain area of the video - for example a TV station logo from the corner) or denoise (that could improve video quality). You can also change the brightness of your video if you find it to be bad.

In the Other (4) section you can add an introduction video that will play before the menu and "Force reencode" of MPEG videos that ManDVD may think that are already DVD ready but generate problems.

When you are done with adding all your video you can click Next. See below for an explanation of the add file dialog before moving to the next step.
ManDVD03

This is the dialog you will see after selecting which file to add. First of all you should set a title (1) for this video. This title will show within ManDVD but in the DVD menu as well. Another cool option is the ability to add a button to the menu using an image from the video. (2) To do so select "Extract an image from the video". A small media player will start playing your video. Click the camera icon you can see in the bottom right corner when you find the image you want. Then it will be saved and loaded here as the button for that video. You can also "Edit with The Gimp" - if The Gimp is installed of course - in case you need to add some effects to it or put some text in there to make your menu look better.

Finally before clicking OK and adding the video you can add some delay to the video or the audio in case they don't match (3) (usually you won't have to use that option at all).

Step3
ManDVD04

In this step you can customize the DVD menu. Your first choice is the background (1). You can either add a picture, just a color or a video for an animated background. From my experienced a nice background image makes a good menu as adding a video makes it too messy while a simple color makes it look too poor. After adding an image you can change some simple settings (2) like rotating it or changing the colors. Next stop is the font settings (3). Here you can choose which font to use, its size as well as the color of the text by default, when selected and when clicked. Finally you can add a song as a background (4) and select if it will play once or loop for ever.

When you are done with... pimping your menu click Next and go to Step 4.

Step4
ManDVD05

Next comes the button placement. First you need to double click on the video you want to add to the menu (1). Note that if you generated an image button in Step 2 that image will appear, if not just a text with the title of the video. Next you should set the size of the button using the sliders (2) as well as its place using the other two sliders on the top and left side. When you are done placing your button select "Confirm button position" (3).
Each video in your project must have a menu entry, and then you can click Next and move to the next step.

Step5
ManDVD06

You are finally able to create your video. First of all you can set the Execution priority (3). Set it to full if you plan not to use the PC or just do light tasks, lower it if you want to use the PC normally (it takes more time though). Next select the video format (4) between 4/3 and 16/9. You may also want to have a look at the Options (5) even though the defaults work fine. The options window is explained below.
Now you can encode your video by selecting "Generate DVD structure" (1). This can take from a few minutes to a few hours depending on the length of your DVD and the speed of your computer.

Tip	Keep in mind that when you have a 64bit CPU, using an AMD64 distro can give you a huge performance gain. As I have both 32bit and 64bit versions of Ubuntu installed and an AMD Athlon64 X2 4200+ I did a small benchmark, encoding the same project (about 90 minutes of XviD) in both environments. The i386 platform took one hour and 5 minutes while in AMD64 I was finished in 40 minutes. Quite a huge difference if you encode videos often don't you think?


After the DVD is created you have a few extra options (2). First of all you should "Watch the result" to make sure everything is OK. Afterwards you can burn using ManDVD, move your project to burn it with K3b (if it is installed of course) or create an ISO image to burn later. Burning right away works fine so the rest options are there just to give you a choice, for example K3b offer much more options than ManDVD itself in burning. In the screen below I am burning my DVD using ManDVD:
ManDVD08
Finally here is the options window:

ManDVD07

These are some options you can change before encoding, most importantly the video bitrate. (1). 5000kb/s is a good default setting. Change it only if you want to fit more video than 2+ hours on the DVD. Next your can select some options for the subtitles (2). Something that you may need if you are using special characters in your subtitles is to change the charset to utf8 (for example for Greek or Kyrilic letters). Finally you can select if you want to deinterlace the video (use it if you see horizontal lines in the encoded video - in 99% of the cases you shouldn't need it though) and if the DVD player will display the menu or start playing the first video when the disc is loaded.

I hope that after reading the guide you feel as excited as I was when I first tried ManDVD. In case you need any help please use our new Linux forum to ask, just remember to add your distro info as well as the console output that you can see when you click "Show/hide console" when converting. Stay tuned for more Linux guides!
 
Close Window
Close Window

---

### Post by timcredible on 2008-08-07
what?  making dvd movies in linux is super easy.  have avi files?  open devede, point to all your avi files, click next, and in a few minutes you have a dvd iso, ready to burn and play on any dvd player.  seriously, it takes no time at all and no knowledge.  devede is in synaptic

---

### Post by cariboo on 2008-08-07
Dis you try the todiscgui along with tovid?

---

### Post by TenPlus1 on 2008-08-07
I like to use DeVeDe (latest from getdeb.net)...  I just add a few .avi's, let it do the work and I'm left with an .iso file I can burn with Brasero...  How hard is that :)

---

### Post by mocha on 2008-08-07
You need to have a system.  DVD making in Linux is a biotch until you have a good system.

Firstly, let me recommend you compile your own versions of ffmpeg and mplayer/mencoder, it will save you a lot of hassle down the road if you want to do other types of conversions.  There are 2 good threads on this forum for that.

For one single video that you want to convert to DVD, I agree with the tovid method or some mencoder/ffmpeg script.  It's the easiest way.  More than one video, then use DeVeDe (from the author's site, not repository version).  Then you get the menuing as well.

DVDstyler is a nice graphical frontend to dvdauthor if you want simple menus and text buttons.  If you want snapshot or animated buttons I have not found anything in Linux to do that, so I use TMPGenc DVD Author under wine.

If you work with MPEG2-TS files, there is an essential prog called "replex" (google for it) which remultiplexes TS files into PS for using with DVDstyler/dvdauthor.

Some other tools you'll need:
WinFF (use version from author's site)
Avidemux
GOPchop
GOPdit
DVBcut
"Video Convertor Script" (search these forums)
k3b
encode2mpeg
dvdfab decrypter (under wine)

I'm not at my box right now, but I think that's the majority of the key apps you need to cover commercial cutting, encoding, and authoring.

There are a few other tricks you can pull such as when you have a video that is broken up into multiple parts.  You can use the good ol "cat" command or mencoder with direct copy options, prior to encoding.  Search for both of these methods.

There is one other gui dvdauthoring program called qdvdauthor, it supports snapshot buttons and looks really promising in general for some advanced authoring.  I was trying to help the developer get it to work with multi-core systems but was never able to get it fully working.  I don't know what the status of it is now.

---

### Post by sstusick on 2008-08-12
> **timcredible said:**
> what?  making dvd movies in linux is super easy.  have avi files?  open devede, point to all your avi files, click next, and in a few minutes you have a dvd iso, ready to burn and play on any dvd player.  seriously, it takes no time at all and no knowledge.  devede is in synapticFew minutes??? More like a few hours.

---

### Post by binbash on 2008-08-13
I use Devede for my dvd stuff.But tovid is also nice but Devede's gui is far better.

---

### Post by racgtpc on 2009-02-22
Hallelujah! For the first time since I began with Linux... and I started with RedHat6.0 and Corel Linux too... I made a DVD that worked!!! Thank you all for that "MANDVD" program. It is beautiful!

---

### Post by finite9 on 2009-02-24
I use Mencoder and ffmpeg exclusively for transcoding files... well apart from ripping DVDs which I use k9copy for as it is really easy.

I spent many man hours creating a script to do my transcoding for me, and it was a real PITA, but it only works for mpg or raw dv files so it's probably not that useful for others.  Half of the GUI tools you find just use ffmpeg or dvdauthor or mencoder on the back end anyway, so if you're having issues with GUIs, maybe you should bite the bullet and read the mencoder manual :)  It was really helpful, and it has sections for getting certain tasks done, but it is very time consuming.

One thnig to note: If you create a DVD ISO using DVD author (in intrepid), it will not play with Totem Gstreamer due to a bug in gstreamer, but VLC and Mplayer will play it fine.

---

### Post by TomB19 on 2009-03-03
> **sstusick said:**
> Few minutes??? More like a few hours.

The transcoding can take quite a bit of time if you have a slow system.  There´s nothing an authoring tool can do about that.

On my system, I can bang out a DVD in about an hour, including transcoding and burning.  That´s not bad.

By the way, I think timcredible meant that it only takes a few minutes to get it going.  He´s right about that.  DeVeDe is outstanding in that regard.  The rest of the time is spent with transcode doing it´s thing.

My only beef with DeVeDe is that it won´t launch two copies of transcode at the same time.  I have four cores but it will only nail one up and I have to wait for all of the transcoding to happen serially, even if I have multiple video files going into the DVD.  It could be way faster with a small amount of loading logic and multiple transcode launches.

Still, it´s tough to knock an application as slick as DeVeDe.  It does it´s job simply and effectively.  I give it 4.5 penguins.

---

### Post by lesmyer on 2009-04-28
> **racgtpc said:**
> Hallelujah! For the first time since I began with Linux... and I started with RedHat6.0 and Corel Linux too... I made a DVD that worked!!! Thank you all for that "MANDVD" program. It is beautiful!

Using Ubuntu Jaunty capture your DV with KINO (don't forget to run Kino as "sudo kino" in a terminal window to get firewire to work).  Then burn to DVD with MANDVD after adding image and sound and text to menu (haven't tried animations yet).  Seems to work great!  Also have had really good luck so far with Jaunty and K9COPY for backing up my new commercial DVDs.

All packages and dependencies for above software were installed on fresh install of recently released Jaunty 9.04 i386 using Synaptic Package Manager.  All updates per Update Manager have also been applied. 

LM

---

### Post by robertrej on 2009-05-07
It seems whatever software I use it converts ac3 audio to mp2 
during the process.Is there way to make ac3 audio mpg video
and retain the ac3 audio?

                         Any ideas
                         Thanks /bob

---

### Post by lesmyer on 2009-05-10
> **lesmyer said:**
> Using Ubuntu Jaunty capture your DV with KINO (don't forget to run Kino as "sudo kino" in a terminal window to get firewire to work).  Then burn to DVD with MANDVD after adding image and sound and text to menu (haven't tried animations yet).  Seems to work great!  Also have had really good luck so far with Jaunty and K9COPY for backing up my new commercial DVDs.

All packages and dependencies for above software were installed on fresh install of recently released Jaunty 9.04 i386 using Synaptic Package Manager.  All updates per Update Manager have also been applied. 

LM

Also recently had excellent results with QDVDAuthor authoring home video saved by Kino in Raw DV format.  (it was a real pain to learn how to use - not intuitive at all - but worth it for me in the end as it does not have canned limitations like MANDVD does).

LM

---

### Post by Orographic on 2009-05-12
Any tips on what you did with this approach? I've got Kino installed today and have been converting my Canon FS200 video files to various formats then trying to burn the iso made from DeVeDe to a disk. They only show up with the title page on the DVD player but nothing else.

Have just installed QDVDAuthor to play with it. I'm using a spare internal drive with a mirror of my Ubuntu setup on it, so I can totally stuff it up without any worry.

---

### Post by Orographic on 2009-05-13
Success! 

I converted the file from my Canon FS200 to a .dv file via Kino then exported from there as a DV AVI Type 1 file then used DeVeDe to burn an iso of that file.

I couldn't get the burned iso from DeVeDe to play in Movie Player but when I put the DVD into our cheap TV DVD player (about four years old) it worked great.

Not sure why that is but for basic DVDs, this approach worked. We are wanting to film some student violin performances and show them at the local school via their DVD player, so hopefully this works. Otherwise we can upload a smaller file to our website for them to view.

---

### Post by MepisReign on 2009-05-27
One word for all you guys

DeVeDe

[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

Best Regards

MepisReign

---

### Post by au6u5t on 2009-06-08
use DeVeDE event for a newbie like me, making DVD movie as simple as making a cup of coffee of course making a cup of coffee for waiting the program do his job.:popcorn:

---

### Post by alkibulan on 2009-12-17
Hi Tuxulin

This alkibulan, 
I had the same problem at to but I manage to find a program that works fine with Kermic Ubuntu 9.10 it was pretty hard at first. Because I did not know how to convert avi video file to a Dvd file. Tried, tovid, todisc,Qdvdauthor,Arista. I tried all of these dvd converters, but none of them was easy to use I kept getting errors as well. But here's one you might want to try out! ManDvd. Its, a linux program. Very easy to use and not much of a head ache like the rest them.You can find it at this link below
[http://www.softpedia.com/reviews/linux/ManDVD-Review-51807.shtml](http://www.softpedia.com/reviews/linux/ManDVD-Review-51807.shtml)

I hope you like it
alkibulan

---

### Post by alkibulan on 2009-12-17
Hi Tuxulin

This alkibulan, 

I had the same problem to but I manage to find a program that works fine with Kermic Ubuntu 9.10 it was pretty hard at first. Because I did not know how to convert avi video file to a Dvd file. I tried, tovid, todisc,Qdvdauthor,Arista. I tried all of these dvd converters, but none of them was easy to use I kept getting errors as well. But here's one you might want to try out! ManDvd. Its, a linux program. Very easy to use and not much of a head ache like the rest them.You can find it at this link below
[http://www.softpedia.com/reviews/linux/ManDVD-Review-51807.shtml](http://www.softpedia.com/reviews/linux/ManDVD-Review-51807.shtml)

I hope you like it
alkibulan

---

### Post by kelvin spratt on 2009-12-17
Devede is a clone of [ConvertXtoDVD]("http://www.afterdawn.com/software/video_software/dvd_tools/vso_divxtodvd.cfm"). in windows it does the converting and makes DVD complaint ISO. 
That you burn to a DVD that plays in all stand alone DVD players,  VLC/Linux/windows, also plays the menus.

---

