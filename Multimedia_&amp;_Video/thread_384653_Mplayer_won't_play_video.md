---
title: "Mplayer won't play video"
date: 2007-03-14
forum: Multimedia &amp; Video
---

### Post by IndyBob on 2007-03-14
I have installed MPlayer and it is in the applications on the desktop.  When I check in Firefox for plugins, it says everything is to play with MPlayer, however, when I go to a site and try to play a video, all I get is the sound and nothing else that applies for Windows Media and RealPlayer Media and Quicktime Media.  It will work if the site requires Vivo Player, but nothing else.  I did delete the plugin for Totem from Firefox.  And then I thought since the associations may be bad, I tried to change that in Firefox and MPlayer only shows for FLI files.  Since I am a newbie I am at a loss of what to try next, HELP!

Also installed RealPlayer 10 and it won't work at all, but then that should be another thread.

---

### Post by mac.ryan on 2007-03-14
Are you sure you installed the codecs needed to play those videos? Ubuntu comes only with free software on it (thus, it excludes certain very common non-free codecs).

If you didn't install them, don't panic, it's very easy and straightforward: go to [www.getautomatix.com](www.getautomatix.com) and download "Automatix2", once installed, you will be accessing a self-explenatory menu for installing the codecs (and some other commonly requested non-free stuff, like google Earth or Skype...).

Hope this helps...

---

### Post by IndyBob on 2007-03-14
I will try Automatix2 when their site gets back up, it's down now.  

I thought I had gotten all the codecs by going thru the terminal and doing sudo aptitude install gstreamer0.10, etc, etc. (3 lines long) but maybe it doesn't have all of them.  I am tempted to uninstall MPlayer and try using Totem with the xine and see if that would work.  Of course I still can't get RealPlayer to work either and I think I goofed in installing RealPlayer and let it do the default install and now I can't find it to edit some of the startup script to add alsa.

Being a newbie sure is a challenge sometimes!  But with the help of all of you on the forum it's been a pleasurable learning experience.

---

### Post by wesley_of_course on 2007-03-14
Wesley here ;

    Might try this , worked for me ;    [http://kubuntuforums.net/forums/index.php?topic=3080644.0](http://kubuntuforums.net/forums/index.php?topic=3080644.0)

---

### Post by IndyBob on 2007-03-14
Thanks, but your fix reads as though it is only for audio - I was getting audio and no video.  Of course now I have messed with it and can't even get anything to play, so back to the drawing board.  Automatix site still down for getting install, so will wait until that is back up and see if that does any good.

I still haven't figured out RealPlayer that it won't work so I am lucking out all around.

---

### Post by dmizer on 2007-03-15
i managed to fix this ... try the 5th post in this thread: [http://www.ubuntuforums.org/showthread.php?t=322085](http://www.ubuntuforums.org/showthread.php?t=322085) still a little shaky for me in some situations, but for the most part, it works.

the proper codecs are very easy to install yourself.  there's no reason to rely on automatix.

here's directions: [https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)

---

### Post by IndyBob on 2007-03-15
dmizer

Well, that partially worked, I can play RealPlayer and Quicktime movies but still not Windows Media - I am not sure how I am to look at the mplayer.conf and mplayer/mplayerplug-in conf files to see if they look like yours.  If you could give me the instructions, maybe I can see what went wrong.  Thanks!  Baby steps are better than none.

---

### Post by dmizer on 2007-03-15
sounds like you haven't installed the w32codecs yet.  you'll need to visit the second link i gave you before: [https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)

to look at the files, open up your terminal by going to: applications > accessories > terminal

then you can open the file by typing 'gksudo gedit' followed by the file path name.  for example:
```
gksudo gedit ~/.mplayer/mplayerplug-in.conf
```
and
```
gksudo gedit ~/.mplayer/config
```

---

### Post by IndyBob on 2007-03-15
dmizer,

Well I downloaded and watched the codec's load in fact it said it was replacing them.

When I tried to check mplayer plugins config per your instructions, (I copied and pasted into terminal) I get the following error:

(gedit:5035): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

When trying to check the mplayer config (again copy and pasting) I get the following:

(gedit:5164): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
bob@ubuntu:~$ 

What's causing this???

---

### Post by dmizer on 2007-03-16
no idea what would cause that unless you're using a desktop other than gnome.  you MIGHT (don't know for sure) be able to fix it by doing this:
```
sudo aptitude install gksudo
```

otherwise, i suggest trying a terminal based text editor instead ...

```
sudo nano ~/.mplayer/mplayerplug-in.conf
```

you will need to use keyboard commands in order to move around and save the file.  but the commands will be listed below the text area.  for example, ^x is the command for exiting nano (where ^ means the ctrl key like so: ctrl+x)

you can use the mouse for copy/paste, but nothing else.  the advantage to this is ... i KNOW it will work.

---

### Post by IndyBob on 2007-03-16
Well, I tried to install gksudo and got the following message:

bob@ubuntu:~$ sudo aptitude install gksudo
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No candidate version found for gksudo
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
bob@ubuntu:~$ 


I will try your other method, but this confuses me.

After downloading and installing codecs again, Mplayer comes up on Windows Media and acts like it is downloading and starts to play for just a second with sound then stops.  Should I remove Mplayer entirely and reinstall with the codecs again and try that route or try another player?

---

### Post by dmizer on 2007-03-16
no!  you're almost there.  you just have to make sure those two config files are set like mine, and it should work perfectly!

---

### Post by IndyBob on 2007-03-16
dmizer,

Well, I finally got into mplayer plugin config and added the two lines shown in yours, also finally got into mplayer.config and added the two lines there and went into preferences on gmplayer and added the changes there too and nothing worked, so I uninstalled mplayer and tried from another thread on the forum and messed that up then all heck broke loose and all sort of things started going wrong, so got totally frustrated and just reformatted and reinstalled 6.10 and will start from scratch.  I will follow your instructions on installing mplayer and see what happens this time.  I will keep you posted, I have some other things to do so it may take me a day or so to get back to this, but thank you so much for your help and I hope I don't have to post back anything except that I got it to work.

---

### Post by IndyBob on 2007-03-17
dmizer,

Well, I stuck with it last night and got things going again, but I cheated and downloaded Automatix2 for some help.  Same thing happened that I couldn't play Windows Media.  Well, I went into the two config files and nothing was showing, so I figured what the heck and copied what showed in yours and saved it and viola, it works.  There are only a couple of sites that I can't play videos that are windows media, but that 's really better than I could do before.  If I go into Firefox and look at file preferences it specifically states that WM, WVX and WAX still will be played in Windows Media Player.  I think I am done with this and will just work through my XP system if I want to watch the couple of sites that I can't get to work.  Unless you have another suggestion.  Your suggestions were very helpful and it's great for my learning curve.  I did wimp out and install Mplayer from the Synaptic Pkg Mgr and of course deleted Totem-xine through there too but I did the codec's per your instructions and through Automatix2 both.  I did not download the illegal version from Automatix2, should I have done that?  I figured that if you got yours to work from the instructions you gave me, then that should be good enough to make it work on mine.

Again thanks for your patience and all your help.

IndyBob

---

### Post by dmizer on 2007-03-18
glad to hear you got it working at least mostly to your satisfaction.  there's no shame in using synaptic.  i use it quite frequently myself.  it's certainly not cheating anyway.  what's more, even though i'm not personally fond of automatix, i can't deny it's usefulness.

sorry for the rough nature of the fix directions.  i haven't had time to make a proper howto yet, but it is in the works.

if you feel so inclined, link me to one of the sites you're unable to watch videos in, and perhaps i can come up with a solution.  no promises though ... windows media is a shifty beast ;)

---

### Post by IndyBob on 2007-03-18
dmizer,

I am just going to live with things the way they are now, as I know there is a new upgrade coming soon on mplayer, so that may help at that time.

Since I am still playing with 6.10 and trying to see if I will make the final plunge and get rid of windows xp, I will just play around for a while and then see what all happens.  I have been so frustrated at some quirks that have happened to me in windows and I have to work for weeks to get corrected that I am hoping Ubuntu and I will learn to live well with each other and I can say adios XP.

I may have to get a larger drive to put 6.10 onto as I took the easy approach and used an old 8.4 GB drive I had and booted 6.10 onto that as my slave drive as I was chicken to re-partition my main drive and I am sure I will run out of space on it soon so I will have to either backup my data and reinstall 6.10 onto a new drive and import my backup or start from scratch and go from there.  With all the good things I have heard coming down the road about Feisty, I may just wait and do a clean install when it comes out next month and set things back up then on a larger slave drive.  Time will tell on that one.

Thanks again for all your help and who knows, I may be needing assistance in the future for something else which I am sure will happen.

IndyBob

---

