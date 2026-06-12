---
title: "Getting real player to work"
date: 2007-12-28
forum: Multimedia &amp; Video
---

### Post by revelationman on 2007-12-28
I have xbuntu  and I trying to get real player to work 
I go to bbc site  and watch bbc news etc  ,  I have tried to install the plug  in restart firefox nothing  
I have downloaded Real Player  it is a rpm  file  and I really  have no idea  how to get this sorted this is my first real crack at linux so  any suggestions will  be greatly  appreciated

---

### Post by benerivo on 2007-12-28
Downloading a deb file should help. Look [here]("http://www.debian-multimedia.org/pool/main/r/realplay/"). I think this also installs a firefox plugin as well, but I can't remember. I did it once and it played real media streams from the bbc.

---

### Post by mc4man on 2007-12-29
Here's a link to a how to 
[https://help.ubuntu.com/community/RealplayerInstallationMethods?action=show&redirect=RealPlayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods?action=show&redirect=RealPlayerInstallationMethods)

I found it to be very complicated and wasn't totally thrilled with the results. Instead I tried something a little different which is very fast and has good results with 1 limitation which is when you open a video on bbc the media player box will be blank and you have to click on 'launch in a stand alone player'. Other than that I'm pleased with result. The video will open in realplayer with no screen size limits and you get a stand alone realplayer in your sound and video menu
Warning :I'm sure this isn't an exactly proper way, and you may want to wait for someone more knowledgeable to chime in
anyway
If you have mozilla- mplayer plugin installed do a total removal 
Download RealPlayer10Gold.bin  from the realplayer for linux site to desktop
In Synaptic Package Manager do a search for helix and install helix and the mozilla-helix plugin
open up a terminal and run
```
cd Desktop
```   followed by
```
chmod a+x RealPlayer10GOLD.bin
```   followed by
```
sudo ./RealPlayer10GOLD.bin
```
after the files are extracted press enter. You'll have a prompt at directory: [blah, blah, blah]:  enter
```
/usr/local
``` then  press enter, then f.   Enter y at the prompt
The next line will say enter the prefix for symbolic links[/usr] :  I waited for the ...... to stop and typed in /usr, but i think all you need to do is press enter
It should now complete the install ,after which go to your sound and video menu and open up realplayer10, click whatever to configure plugin's, ck. for update ect. (it's automatic)
you should be able to go to bbc, click on video and the player box will load blank. click launch in stand alone player and a dialog box should open. If the default player is /usr/local/realplay (or something very similar I forget exactly) then check always open with.., if not browse to it (/usr/local/realplay and then ck. always open ....
Again there's probably better methods , anyone feel free to correct

---

### Post by revelationman on 2007-12-29
Well I have downloaded Real Player 10.1  that is done  went back to BBC nothing , sorry  I am kinda of a newbie this old machine is going to be my  learning tool  till I put  a full linux system on my laptop 

I have also  went to   preferences  
avi
asf
wwm
and all those are stating windows media player  

this is just driving me nuts i am not giving up on this  i am impressed with this os esp on a old machine  like this it is like it has given it a second life 


so any more   ideas

---

### Post by ugm6hr on 2007-12-29
> **benerivo said:**
> Downloading a deb file should help. Look [here]("http://www.debian-multimedia.org/pool/main/r/realplay/"). I think this also installs a firefox plugin as well, but I can't remember. I did it once and it played real media streams from the bbc.

This works in Gutsy.

Ref: [http://www.howtoforge.com/the_perfect_desktop_ubuntustudio_7.10_p7](http://www.howtoforge.com/the_perfect_desktop_ubuntustudio_7.10_p7)

From Terminal:
```
wget -c http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.9-0.1_i386.deb
sudo dpkg -i realplayer_10.0.9-0.1_i386.deb
```

Or download the .deb from benerivo's link and double-click.

I also use the Media Player Connectivity plugin for Firefox.

---

### Post by revelationman on 2007-12-29
well  i have installed  real player  but still does not link  with  firefox  
but i have done a back door  thing using the player within the os and installing codecs it works  but not with real player  ,
now i have installed opera  my problem is finding where the file is for the installed real  player 
this a learning curve  i know   but again  i am slowly  starting to enjoying this os  just takes loads of paitence that is all , 

so anymore tips or suggestions 


thanks 
:guitar:

---

### Post by ugm6hr on 2007-12-29
> **revelationman said:**
> well  i have installed  real player  but still does not link  with  firefox  
:

If you've installed realplayer - you may as well use it for realmedia...  Open Realplayer, go to menu **File->Open Location** and paste the following:
[http://news.bbc.co.uk/media/avdb/news/entertainment/video/141000/bb/141845_16x9_bb.ram?ad=1&ct=50](http://news.bbc.co.uk/media/avdb/news/entertainment/video/141000/bb/141845_16x9_bb.ram?ad=1&ct=50)

Does it work?

If yes - then install Media Player Connectivity (MPC) and configure it to use Realplayer for Realmedia.  This should now work in Firefox.  If no - then there is a problem with the Realplayer installation (how did you install?)

MPC: [https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

Note that Realplayer seems to have problems with buffering, so you may have to rewind the playing if it jumps at the start.

---

### Post by shadyedsan on 2007-12-30
> **revelationman said:**
> Well I have downloaded Real Player 10.1  that is done  went back to BBC nothing , sorry  I am kinda of a newbie this old machine is going to be my  learning tool  till I put  a full linux system on my laptop 

I have also  went to   preferences  
avi
asf
wwm
and all those are stating windows media player  

this is just driving me nuts i am not giving up on this  i am impressed with this os esp on a old machine  like this it is like it has given it a second life 


so any more   ideas

assuming the install was ok and realplayer is working:


when you view a video link in ubuntu for the bbc site, make sure the main settings are for realplayer and the speed of your internet connection then click lanch this player in a new window, and it will ask you to save it as a .ram file. open this file up using realplayer

hope this helps

---

