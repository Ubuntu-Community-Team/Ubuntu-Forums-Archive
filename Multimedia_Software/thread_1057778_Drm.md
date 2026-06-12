---
title: "Drm?"
date: 2009-02-02
forum: Multimedia Software
---

### Post by diwas on 2009-02-02
I downloaded a movie from torrent with a wmv extension. But it won't play in any player. Mplayer says "The file has been encumbered with DRM encryption, it will not play in Mplayer!". VLC cannot play it as well. Neither can TOTEM music player. 
Is there anyway i could make this play? I have a slow internet so re-downloading the whole movie is very bad idea hehe.

---

### Post by diwas on 2009-02-02
Is it possible to play it in Windows?

---

### Post by frklin on 2009-02-02
You must install MS Media Player in Crossover/Wine. Other way, not there is...

---

### Post by diwas on 2009-02-02
Well, even in windows with WMP 11...it doesnt work. It asks to download a lisence and then install it...then if i again try to play the video, same thing happens...(asks to download lisence...)
so will installing WMP in wine help?

---

### Post by redroad55 on 2009-02-02
try this link and Post back with your results and or questions ..Best to you..
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by diwas on 2009-02-03
> **redroad55 said:**
> try this link and Post back with your results and or questions ..Best to you..
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")
I have installed all the packages and everything is fine.

---

### Post by lakersforce on 2009-02-03
DRM: Designed to only hassle the *wrong* people :)

---

### Post by diwas on 2009-02-04
Can't I play it in Windows? Anywhere please help!!!

---

### Post by redroad55 on 2009-02-04
Is it playing in 7.10 ? or have you just not got it to play at all...My wife and I live in a rural area and were limited to 2 dialup connections forever..We put together a petition, got signatures from others,and submitted to the local powers..They brought in broadband for everyone ..From what I understand by 2011 it has to by law be available .. Post back

---

### Post by diwas on 2009-02-04
> **redroad55 said:**
> Is it playing in 7.10 ? or have you just not got it to play at all...My wife and I live in a rural area and were limited to 2 dialup connections forever..We put together a petition, got signatures from others,and submitted to the local powers..They brought in broadband for everyone ..From what I understand by 2011 it has to by law be available .. Post back
7.10? Do u mean the distro or software version name?? I am sorry I didnt quite get it.

---

### Post by redroad55 on 2009-02-04
In your posts under your name you have that your running Ubuntu 7.10 Gusty Gibbon .. Just wondered if you have the movie playing in Ubuntu..Post back .. There is a VLC version for windows

---

### Post by diwas on 2009-02-04
Oh, I just edited that...hehe I am sorry.
I am using 8.10

VLC(In windows) cannot play it either. Do I have to download the latest VLC? I have a little old one..

---

### Post by redroad55 on 2009-02-04
This step is important so first go to applications > system > admin. > software sources >> third party tab .. make sure Medibuntu is present in list .. If not then go here
 [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

also

> Setting DVD Region Codes

    *

      If your DVD player regularly locks up when you try to play back a DVD, your DVD player probably does not match the DVD's Region Code. Region Codes are a form of vendor lock-in. For example, you cannot play a DVD published in Japan (Region 2) on a DVD player in the United States (Region 1) without changing the Region Code of the DVD player (unless you own a region free DVD player). You can view or modify the Region Code of your DVD drive with the regionset tool.

      IconsPage/warning.png
      The author of regionset writes: "On delivery, most DVD drives have no region code set. The drive firmware allows you to change the region code, but on nearly all drives you are limited to five (5) changes. After the fifth change, the DVD drive will stay fixed on that code -- on some drives you can upgrade the drive firmware and have then additional five changes, on other drives you won't be able to change the region code any more."
    * Most players (eg mplayer/vlc) with most DVD drives are able to ignore the value of the region setting. However, it must have been set to something; if it hasn't been initialized, even non-region-restricted DVDs won't play. Also, if it is necessary to crack the CSS key, it can sometimes take up to a few minutes to do so. 


    * To change the Region Code of your DVD player, insert a DVD from your region in the DVD player, and do the following:
          o

            Install the regionset package from the Universe repositories.
          o To launch regionset, issue the command

            regionset

          o

            See the Free Formats page for more information 


Give these things a try and Post back..Best to you

---

### Post by diwas on 2009-02-04
Thank you for the help but,
VLC in ubuntu is upto date.
And the quote above talks about DVD, not .wmv with DRM.

---

### Post by redroad55 on 2009-02-04
so you are saying that you have all needed downloads for VLC and it still does not work correct?
> Playing Non-Native Media Formats

There are a few formats such as certain Windows formats, Real, and Apple Quicktime which do not have native codecs under Linux. To work around this issue, external binary codecs are used instead to play these formats. MPlayer and xine use such external codecs and these codecs are stored in the MPlayer website in their codecs directory located at [http://www.mplayerhq.hu/MPlayer/releases/codecs/](http://www.mplayerhq.hu/MPlayer/releases/codecs/).

Medibuntu distributes a package which contains these codecs. The codecs are under the non-free component of the repository. If you followed the directions above to exclude the non-free component, follow the steps again to add the Medibuntu repository to your system's list of APT repositories and skip the step to exclude the non-free component.

Below are the instructions for installing the packages using the command line. For other methods, please refer to Installing Software.

With the entire Medibuntu repository

If you have added the entire Medibuntu repository, install the package using APT.

    *

      For i386, the package is called w32codecs:

      sudo apt-get install w32codecs

    *

      For amd64, the package is called w64codecs:

      sudo apt-get install w64codecs

    *

      For ppc, the package is called ppc-codecs:

      sudo apt-get install ppc-codecs

    *



As far as the regionset if the video is from a different region than what your DVD player in lies the conflict..Post back

---

### Post by diwas on 2009-02-05
I dont think changing the region number will do it. I am NOT having problem with the DVD. Its the wmv extension file with DRM.

I have installed w32codecs, so it won't help.

---

### Post by Kangarooo on 2010-08-17
Ok i found u can play drm wma on linux so also ubuntu with mplayer and that means also smplayer and other same player versions.
so just install mplayer and it will work
> sudo aptitude install mplayer-gui
now also i found some video files also have some protection but thats another topic.
So resume: i have all codecs tryd vlc totem restricted extras and medibuntu and only mplayer plays drm wma music files. Also it would be good if someone checks if on clean installation theese files work on mplayer heres link to one file to ckech on it [http://kangarooo.times.lv/90secondsorless1a.wma](http://kangarooo.times.lv/90secondsorless1a.wma)
and that i can open with mplayer-gui
but i cant open [http://kangarooo.times.lv/03track3.wma](http://kangarooo.times.lv/03track3.wma)
both of them have DRM protection but both act differentin vlc and in mplayer

---

### Post by endotherm on 2010-08-17
just be wary. there are several ways to install malware on a system through the automatic license download, so there are some videos available on line that will attempt to infect your system when you try to play them back. 

[http://www.theregister.co.uk/2005/01/13/drm_trojan/](http://www.theregister.co.uk/2005/01/13/drm_trojan/)

---

### Post by Kangarooo on 2010-08-18
> **endotherm said:**
> just be wary. there are several ways to install malware on a system through the automatic license download, so there are some videos available on line that will attempt to infect your system when you try to play them back. 

[http://www.theregister.co.uk/2005/01/13/drm_trojan/](http://www.theregister.co.uk/2005/01/13/drm_trojan/)

wow cool. is it really also possible in linux?
it wasnt till now u told ;)

---

### Post by endotherm on 2010-08-18
> **Kangarooo said:**
> wow cool. is it really also possible in linux?
it wasnt till now u told ;)
probably not, as long as the op does not take some of the advice above, running MS WMP  via wine. if wine is involved, there is probably a 30% chance that the software could do something harmful. 

not a likely possibility. just somthing to consider.

---

### Post by mc4man on 2010-08-18
> .....both of them have DRM protection but both act differentin vlc and in mplayer
I don't see any protection in the 90sec sample - it's simply a wmas which plays fine here in all players.

In lucid and karmic vlc won't play wmas unless re-built, gstreamer can if the plugins are updated, mplayer will in various ways.

In maverick most all players will support wmas (and wmap

The other sample is encrypted and playback isn't possible in ubuntu

---

### Post by Kangarooo on 2010-08-18
> **mc4man said:**
> I don't see any protection in the 90sec sample - it's simply a wmas which plays fine here in all players.

In lucid and karmic vlc won't play wmas unless re-built, gstreamer can if the plugins are updated, mplayer will in various ways.

In maverick most all players will support wmas (and wmap

The other sample is encrypted and playback isn't possible in ubuntu

ouh yes. now i tryd also that 90sec in 10.10 in VLC and i can also play it. maybe also ive installed some medibuntu also. but i couldnt in 9.10 but could only with mplayer-gui in 9.10
so now something has changed from then. but it has some protection couse i could play it in 9.10 so ill post tomorow results from another ubuntu witch doesnt have medibuntu installed to be sure if that now is possible without installing anything or just mplayer-gui or now with just medibuntu in any player.

the second file i got mplayer-gui from saying its DRM protected to not saying but still not playing by installing one codec tommorw ill edit this post with update..

---

