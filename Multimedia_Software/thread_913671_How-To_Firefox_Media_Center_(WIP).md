---
title: "How-To: Firefox Media Center (WIP)"
date: 2008-09-08
forum: Multimedia Software
---

### Post by lovinglinux on 2008-09-08
**[COLOR="Red"]Special Note:[/COLOR]** most of the functionality of this tutorial can now be achieved with my new FoxMediaCenter extension that you can download at [http://foxmediacenter-extension.blogspot.com](http://foxmediacenter-extension.blogspot.com) so this tutorial will not be maintained anymore.

There is also a new thread

[http://ubuntuforums.org/showthread.php?t=1024400](http://ubuntuforums.org/showthread.php?t=1024400)

---

### Post by lovinglinux on 2008-09-11
The first version of the tutorial is ready. Please tell me what do you think about this idea and the tutorial itself. Also let me know if you have any suggestions on how to improve it or if you know any extensions that you think should be included. I will be glad to update the tutorial and give the proper credits for contributors.

I hope you like the "Firefox Media Center" the way I do. Have fun!

---

### Post by Jose Catre-Vandis on 2008-09-12
Looks great, can't wait to try it out. Any suggestions on how to run digital tv? Is it the same as for analog but with a different syntax? Also looking forward to TV manager accommodating UK channels.

---

### Post by lovinglinux on 2008-09-12
> **Jose Catre-Vandis said:**
> Looks great, can't wait to try it out. Any suggestions on how to run digital tv? Is it the same as for analog but with a different syntax? Also looking forward to TV manager accommodating UK channels.

Unfortunately, I'm not familiar with digital TV cards, but I guess the principles are the same. Since I use external applications to watch, record and stream TV, you just have to tweak the configurations on those applications and use my instructions to launch them trough Firefox. If an application I suggest doesn't work with digital TV, all you have to do is find one that work's and follow the same procedures to integrate them into Firefox. For example, all you need to watch recorded TV is a Firefox plugin like gecko-mediaplayer or mozilla-vlc plugin and you probably already have one. To record you might  need a different transcoder or command to start it, but the procedure to add "record" and "stop" buttons to Firefox is pretty much the same, so in the end you will have to change just a few commands and file paths.

Try it out and tell me if you find any difficulties. I will be glad to help you customize your setup. What program you currently use for watching and recording TV?

I have sent a suggestion to TV Manager designer about supporting xmltv, so users from other countries could easily adapt the extension for their local programming. He said this will be taken under consideration for future releases, but also said that they are already working on supporting other countries natively. Since UK is a major player in the entertainment industry and closely related to US studios, I bet you won't have to wait too much longer. I'm not so lucky, since in my country the best they can do is broadcast new US tv series with at least 2 months gap.

---

### Post by Jose Catre-Vandis on 2008-09-13
I use mplayer for dvb-tv. I have a channels.conf file in my ~/.mplayer directory that contains all the necessary info for selecting channels. Although I have scripts to make life easier the basic approach is:
```
 mplayer dvb:// BBC1 
``` where BBC1 is the "name/label" for the configuration info for the BBC1 channel. This command runs dvb-tv in an mplayer window

---

### Post by lovinglinux on 2008-09-13
> **Jose Catre-Vandis said:**
> I use mplayer for dvb-tv. I have a channels.conf file in my ~/.mplayer directory that contains all the necessary info for selecting channels. Although I have scripts to make life easier the basic approach is:
```
 mplayer dvb:// BBC1 
``` where BBC1 is the "name/label" for the configuration info for the BBC1 channel. This command runs dvb-tv in an mplayer window

Ok. Let's try to create a bookmark in Firefox that will open BBC1 channel

1. In the Location bar, type about:config, and press Enter.

2. Right-click anywhere in the grid, choose New, then String.

3. In the "Enter the preference name" prompt, type in "network.protocol-handler.app.dvb" and press OK.

4. In the "Enter string value" prompt, type "/usr/bin/mplayer" 

Now open the bookmark manager and create a new link using "dvb://BBC1" as url. If Firefox prompts you to select an application to open that kind of url, browse the /usr/bin/  and select mplayer, even if it is already in the available list. Then try to open this bookmark and see if mplayer opens on BBC1 channel. If it doesn't work, try using just "dvb://" as URL.

Tell me if you succeed and we will proceed to next step.

---

### Post by Jose Catre-Vandis on 2008-09-13
> **lovinglinux said:**
> Ok. Let's try to create a bookmark in Firefox that will open BBC1 channel

1. In the Location bar, type about:config, and press Enter.

2. Right-click anywhere in the grid, choose New, then String.

3. In the "Enter the preference name" prompt, type in "network.protocol-handler.app.dvb" and press OK.

4. In the "Enter string value" prompt, type "/usr/bin/mplayer" 

Now open the bookmark manager and create a new link using "dvb://BBC1" as url. If Firefox prompts you to select an application to open that kind of url, browse the /usr/bin/  and select mplayer, even if it is already in the available list. Then try to open this bookmark and see if mplayer opens on BBC1 channel. If it doesn't work, try using just "dvb://" as URL.

Tell me if you succeed and we will proceed to next step.

That worked fine! Excellent!

Still working my way through the base setup:

TV Manager was not available to me as an add-on (not doubt because I am UK based)

Have not bothered yet with the EPG or PVR as dvb recording may require a different approach to yours. or with streaming (slow broadband)

Do you know how to get music files to enqueue ( I use Audacious as my mp3 player) as opposed to just playing?

This is good stuff though

Cheers

Jose

---

### Post by lovinglinux on 2008-09-13
> **Jose Catre-Vandis said:**
> That worked fine! Excellent!

Still working my way through the base setup:

w00t

I just gave you the basic for creating a fake dvb:// association in Firefox, so when you get at this point in the tutorial you will be able to create a fancy thumbnail for each channel. You don't have to go to about:config again, just use the URL dvb:// with the channel ID you have configured for mplayer (BBC1, BBC2 or whatever) and you will be fine.

> **Jose Catre-Vandis said:**
> TV Manager was not available to me as an add-on (not doubt because I am UK based)

It is an experimental extension, not fully approved by Mozilla yet, so you need to register and login in the Mozilla extension directory to download. Just create an account there and you will be able to download it.

> **Jose Catre-Vandis said:**
> Have not bothered yet with the EPG or PVR as dvb recording may require a different approach to yours. or with streaming (slow broadband)

I'm not using streaming either, because it suck the processor power, but I included in my tutorial because some people might be interested.

DVB recording will definitively require a different approach, specially because my TV card receives a single channel frequency from the cable TV setup box, which is in other room. I can't switch channels on the PC, so a single button for recording is enough for me.

Do you currently use some software to record TV? Maybe we can figure out how to make a nice setup for you.

> **Jose Catre-Vandis said:**
> Do you know how to get music files to enqueue ( I use Audacious as my mp3 player) as opposed to just playing?

Do you mean adding to a playlist on-the-fly? I have to think about it.

---

### Post by Jose Catre-Vandis on 2008-09-13
FFMC:
The biggest problem in achieving a media center experience is when running FF in full screen with everything else loading up behind it. Anyway of getting FF to run at the "back". Fast Dial is a super extension and getting the "urls" working provides a useful interface for all sorts of things.

DVB:
As I said, I run a script to choose channels for watching and/or recording using zenity to make a gui for the choices. Have got this working from a thumbnail so I don't have to have a thumbnail for each channel.

MP3:
Yes, to enqueue to Audacious on the fly. Audacious has an option " -e or --enqueue" but it is about not setting this as a default for the whole system, simply for FFMC.

Thanks for your help

---

### Post by lovinglinux on 2008-09-13
> **Jose Catre-Vandis said:**
> FFMC:
The biggest problem in achieving a media center experience is when running FF in full screen with everything else loading up behind it. Anyway of getting FF to run at the "back". Fast Dial is a super extension and getting the "urls" working provides a useful interface for all sorts of things.Thanks for your help

You have two options. The first one is make sure all applications launched by FFMC startup as fullscreen. This is similar to MythTV behavior as far as I now.

The second option requires compiz. Open CompizConfig Settings Manager and scroll to "Window Rules" plugin. Then add "title=Mozilla Firefox" to the "Below" rule. This will make Firefox always below other windows, even when in fullscreen mode. The downside is that your regular Firefox profile window will be also below.

> **Jose Catre-Vandis said:**
> DVB:
As I said, I run a script to choose channels for watching and/or recording using zenity to make a gui for the choices. Have got this working from a thumbnail so I don't have to have a thumbnail for each channel.

In this case I recommend replacing the mplayer on your "dvb://" link handler inside FFMC (Preferences > Applications tab) to you custom GUI. So whenever you need to watch or record TV you can launch your GUI from FFMC. It will be much simpler to configure, because you just need one link to control channels and recordings. You still can create a link to the folder where you save TV recordings, so you don't have to leave the FFMC fullscreen to watch them.

> **Jose Catre-Vandis said:**
> MP3:
Yes, to enqueue to Audacious on the fly. Audacious has an option " -e or --enqueue" but it is about not setting this as a default for the whole system, simply for FFMC.

I need to test, but I guess it is possible to create a script for this. I will let you know about my findings.

---

### Post by Jose Catre-Vandis on 2008-09-13
A better fix if using Compiz for setting the Fast Dial home page at the back:

In Windows Rules>Below use "title=Fast Dial - Mozilla Firefox", this keeps the home page below but all other firefox pages with different titles not necessarily below, and does not affect your other profile. This means if you are calling out a standalaone program, and therefore not moving away from the home page, you will see your standalone application.
:)

---

### Post by lovinglinux on 2008-09-13
> **Jose Catre-Vandis said:**
> A better fix if using Compiz for setting the Fast Dial home page at the back:

In Windows Rules>Below use "title=Fast Dial - Mozilla Firefox", this keeps the home page below but all other firefox pages with different titles not necessarily below, and does not affect your other profile. This means if you are calling out a standalaone program, and therefore not moving away from the home page, you will see your standalone application.
:)

Yep, I already used that too. Problem is that I use Fast Dial everywhere :) and when you access a regular web link or leave the Fast Dial home page, FMC leaves the fullscreen mode, which is very annoying.

About the --enqueue....I don't know how to parse variables to a script. You might want to consider [URL="https://addons.mozilla.org/en-US/firefox/addon/5034"][COLOR="Red"]**AmaroK XUL remote**[/COLOR]
[/URL]. I couldn't make it work and looks like it is incompatible with FF 3.0.1 but looks promising.

---

### Post by Jose Catre-Vandis on 2008-09-13
Sourced a simple script to enqueue with audacious, although it means it applies to all mp3s (meaning I will always enqueue and have to go to the player to play:
```
#!/bin/bash
/usr/bin/audacious --enqueue "$*"
```

Name it, make executable, and point Firefox Preferences Applications MP3 Audio at it instead of gecko or simple audacious

---

### Post by lovinglinux on 2008-09-13
> **Jose Catre-Vandis said:**
> Sourced a simple script to enqueue with audacious, although it means it applies to all mp3s (meaning I will always enqueue and have to go to the player to play:
```
#!/bin/bash
/usr/bin/audacious --enqueue "$*"
```

Name it, make executable, and point Firefox Preferences Applications MP3 Audio at it instead of gecko or simple audacious

Very nice. Thank you.

I have included the Gspace extension in the top of the Extensions section, because it allows you to upload your music to GMail, listen to them anywhere and even create playlists on-the-fly that you can listen from FMC without any additional software. See example below:

[[IMG]http://img228.imageshack.us/img228/6162/screenshotgspacemozillajd8.th.png[/IMG]](http://img228.imageshack.us/img228/6162/screenshotgspacemozillajd8.png)

I knew Gspace for a few years ago, but didn't imagined that it was so well developed now and with the ability to create music playlists. One of the best extensions for FMC in my opinion. It's not a solution for what you are trying to do, but definitively worth downloading.

---

### Post by lovinglinux on 2008-09-14
I have completely replaced section 4 of the tutorial. Now instead of using FireFly for editing local files, the tutorial uses FireFTP, which is cleaner, simpler and has all necessary tools for local file management.

---

### Post by lovinglinux on 2008-09-16
I have updated section 8.2. PVR to allow multiple recordings without overwriting the avi file.

---

### Post by lovinglinux on 2008-09-16
Updated section 8.2 so when you hit the record button TVTime will be launched so you can choose channel. The recording will start only after you close TVTime window.

---

### Post by lovinglinux on 2008-09-16
Updated section 8.2 to include an option for automatically launching the recorded video after stopping the recorder and to move the file to another location before playing it (I'm starting to love this command line thing).

---

### Post by lovinglinux on 2008-09-16
Updated section 8.2 to include code that display a notification icon in the gnome panel. You can also stop the recording by clicking the notification icon. :popcorn:

---

### Post by lovinglinux on 2008-09-18
Updated section 8.2. with new transcode commands for NTSC and PAL-M and created a new section for PVR.

---

### Post by lovinglinux on 2008-09-19
Updated section 8 to include an automatic PVR script and section 4 to include an image browser/editor extension.

---

### Post by lovinglinux on 2008-09-21
Updated section 8 to include a recording time preset, so now you can easily choose for how long Transcode will record the TV and you can also override this preset at any time, interrupting the recording manually. :popcorn:

---

### Post by lovinglinux on 2008-10-09
Added a new section after Section 8, to include instructions on how to automatically generate and update media playlists based on folder content.

---

### Post by lovinglinux on 2008-10-11
NoScript 1.8.2.4 has a bug that prevents launching applications using fake protocols and Fast Dial thumbnails, among other things. So if you are experiencing this kind of issue you can temporarily install the [[COLOR="Red"]**development version**[/COLOR]]("http://noscript.net/getit") of this extension.

---

### Post by lovinglinux on 2008-10-23
Updated section 8 to include a file name option in the TV recorder.

---

### Post by mrgnash on 2008-10-24
Most awesome tutorial ever, thanks :D

---

### Post by lovinglinux on 2008-10-24
> **mrgnash said:**
> Most awesome tutorial ever, thanks :D

Thank you very much. I'm glad you like it.

---

### Post by Absinthe Minded on 2008-11-02
Hello all,

LL, this is a fantastic tutorial but I'm stuck:

> Open the Add-ons manager from the menu Tools > Add-ons. Select All-in-One Sidebar and hit Preferences button. In the AIOS Preferences window, hit "Settings" button and select "Import Settings" like this. Browse the file you have downloaded from the link above. Click OK and close the AIOS Preferences 

When I try to import, I'm only given the option to view text files, so I can't see the images to import.

Any ideas on how to fix this?

Cheers,
Nick.

---

### Post by lovinglinux on 2008-11-02
> **Absinthe Minded said:**
> Hello all,

LL, this is a fantastic tutorial but I'm stuck:



When I try to import, I'm only given the option to view text files, so I can't see the images to import.

Any ideas on how to fix this?

Cheers,
Nick.

Thank you.

You don't have to import images on this step. I guess you got confused because the icon package is in the same download page as the AIOS settings. The direct download url for AIOS settings is [http://www.mediafire.com/download.php?kd5wcdbluyk](http://www.mediafire.com/download.php?kd5wcdbluyk)

Just download that txt file and import to AIOS.

PS: I have updated the url in the tutorial with the txt url to avoid confusion

---

### Post by Absinthe Minded on 2008-11-03
Hi LL,

Thanks for such a quick response. Of course, the answer was kinda obvious in the end, but this just makes me want to thank you all the more for being so patient wth a newbie like me.

I'm working through it and all seems to be going well.

Cheers,
Nick.

edit: Another question: Can somebody give me a clue as to how I link a Fast Dial thumbnail to another drive (Windows), I'm looking to link to a file in My Documents.

---

### Post by lovinglinux on 2008-11-03
> **Absinthe Minded said:**
> Hi LL,

Thanks for such a quick response. Of course, the answer was kinda obvious in the end, but this just makes me want to thank you all the more for being so patient wth a newbie like me.

I'm working through it and all seems to be going well.

Cheers,
Nick.

edit: Another question: Can somebody give me a clue as to how I link a Fast Dial thumbnail to another drive (Windows), I'm looking to link to a file in My Documents.

You are welcome. 

Open Firefox, then go to "Menu >> File >> Open File", browse the file you want to link and open it. Then copy the resulting url from Firefox address bar and use it to create your Fast Dial link.

---

### Post by Absinthe Minded on 2008-11-04
Hi LL,

Thanks, that's easy enough but there are two problems with it.

1. I get 'Page Not Found' after a reboot, and I have to re-enter the url for it to work.

2. When the video does play, I get audio only.

Could 1. be because the url I enter contains spaces, i.e. My Documents? I read that adding the escape character '\' would fix this but it doesn't seem to work.

Another problem is that if I open Firefox via the 'mediacenter' shortcut, the next time I click on my default firefox icon, it opens mediacenter.

Thanks,
Nick.

---

### Post by lovinglinux on 2008-11-04
> **Absinthe Minded said:**
> 1. I get 'Page Not Found' after a reboot, and I have to re-enter the url for it to work.

Could 1. be because the url I enter contains spaces, i.e. My Documents? I read that adding the escape character '\' would fix this but it doesn't seem to work..

I guess yes. The method I described is just a trick so you don't have to type the entire url to create the fast dial link. Could you please post the url, so I can check what is wrong?


> **Absinthe Minded said:**
> 2. When the video does play, I get audio only.

What video? There several types of videos in the tutorial. It would help if you refer to what section of the tutorial you are talking about. Are you trying to create a fast dial link  to a video in the Windows partition? Which program you are using to display the video? Are you using a standalone player or opening the video with a Firefox plugin?

> **Absinthe Minded said:**
> Another problem is that if I open Firefox via the 'mediacenter' shortcut, the next time I click on my default firefox icon, it opens mediacenter.

Are you clicking the default Firefox icon while the "mediacenter" profile is already opened? If yes, this is normal. Firefox opens another window of the current profile, because the default Firefox icon does not have the "-no-remote" and "-P" options. What you need to do is create another icon to the regular profile with the same settings for the "mediacenter" shortcut like below:

```
firefox -no-remote -P[COLOR="Red"]** your_regular_profile_name_here**[/COLOR]
```

Or you could just add these parameters to the default Firefox icon.

---

### Post by Absinthe Minded on 2008-11-04
> **lovinglinux said:**
> I guess yes. The method I described is just a trick so you don't have to type the entire url to create the fast dial link. Could you please post the url, so I can check what is wrong?

It's a good trick, and one I'm sure I'll use it lots more in the future. The url is:

> file:///media/disk-2/Documents%20and%20Settings/Nick/My%20Documents/Azureus%20Downloads/Dark%20Star/Dark_Star.avi

All the '%20's are obviously the spaces in the url, i.e. My%20Documents, is My Documents.


> What video? There several types of videos in the tutorial. It would help if you refer to what section of the tutorial you are talking about. Are you trying to create a fast dial link  to a video in the Windows partition? Which program you are using to display the video? Are you using a standalone player or opening the video with a Firefox plugin?

It's the Dark Star video in the above url I quoted, an .avi that is on my other (Windows) disk, and yes, I'm trying to create a Fast Dial link to it.. I'm trying to launch it with a Firefox plugin (I installed geko from the 'multimedia how to' that you linked to in the tutorial). Pretty sure the install worked, I get the MPlayer logo on the top left of the screen, along with the url of the file and the audio stream, but no video.

> Are you clicking the default Firefox icon while the "mediacenter" profile is already opened? If yes, this is normal. Firefox opens another window of the current profile, because the default Firefox icon does not have the "-no-remote" and "-P" options. What you need to do is create another icon to the regular profile with the same settings for the "mediacenter" shortcut like below:

```
firefox -no-remote -P[COLOR="Red"]** your_regular_profile_name_here**[/COLOR]
```

Or you could just add these parameters to the default Firefox icon.

OK, thanks for that, I've edited the icon properties and that works perfectly now.

BTW, tell me if you get bored with sorting all this out for me - I know how time consuming and irritating it can be! I am trying to do this by looking stuff up myself, but I don't always find the answers I need.

Cheers,
Nick.

---

### Post by lovinglinux on 2008-11-04
> **Absinthe Minded said:**
> It's a good trick, and one I'm sure I'll use it lots more in the future. The url is:
All the '%20's are obviously the spaces in the url, i.e. My%20Documents, is My Documents.

Is the Windows partition mounted on boot? If it's not, then the first time you click the link it will fail, but the disk will be mounted with this action. Then when you insert the link in the address bar it will work, because the drive is now mounted. 

> **Absinthe Minded said:**
> It's the Dark Star video in the above url I quoted, an .avi that is on my other (Windows) disk, and yes, I'm trying to create a Fast Dial link to it.. I'm trying to launch it with a Firefox plugin (I installed geko from the 'multimedia how to' that you linked to in the tutorial). Pretty sure the install worked, I get the MPlayer logo on the top left of the screen, along with the url of the file and the audio stream, but no video.

Almost certain is a codec issue. Try opening the video with gnome-mplayer outside Firefox. If it is a codec issue, than you will get the same result. But if the video appears, than could be a Firefox related problem.

Have you installed Gstreamer codecs?

> **Absinthe Minded said:**
> BTW, tell me if you get bored with sorting all this out for me - I know how time consuming and irritating it can be! I am trying to do this by looking stuff up myself, but I don't always find the answers I need.

Don't worry. I can't predict or include all possible scenarios in the tutorial, so giving support to the readers is an essential part of the process. I don't get bored or irritated whatsoever. This community has been so helpful since I changed to Ubuntu two months ago, that wouldn't be fair on my part.

Since the tutorial is long and some procedures are repeated throughout the sections, just make sure you make references to which section or procedure you are dealing with when asking for a solution. This makes the process of debugging much easier for me.

---

### Post by Absinthe Minded on 2008-11-05
> **lovinglinux said:**
> Is the Windows partition mounted on boot? If it's not, then the first time you click the link it will fail, but the disk will be mounted with this action. Then when you insert the link in the address bar it will work, because the drive is now mounted.

Yes, the drive is mounted at bootup as it appears under Places>Computer as 137.4 GB Media without me having to do anything.

> Almost certain is a codec issue. Try opening the video with gnome-mplayer outside Firefox. If it is a codec issue, than you will get the same result. But if the video appears, than could be a Firefox related problem.

No video outside of Firefox - so you must be right in that it's a codec issue.

> Have you installed Gstreamer codecs?

Not as far as I'm aware, if you could point me to a guide, I'd be grateful to you. I'm using Hardy, BTW.

> Don't worry. I can't predict or include all possible scenarios in the tutorial, so giving support to the readers is an essential part of the process. I don't get bored or irritated whatsoever. This community has been so helpful since I changed to Ubuntu two months ago, that wouldn't be fair on my part.

We, that's nice of you - I'm sure it will benefit many, so good for you. I just didn't want you to think that I wasn't bothering to try and do any of it myself. Aside from all that, I can't believe how much you've learnt in two months!

> Since the tutorial is long and some procedures are repeated throughout the sections, just make sure you make references to which section or procedure you are dealing with when asking for a solution. This makes the process of debugging much easier for me.

Sure, I'll do my best to be specific in the future.

Cheers,
Nick.

---

### Post by lovinglinux on 2008-11-05
> **Absinthe Minded said:**
> Yes, the drive is mounted at bootup as it appears under Places>Computer as 137.4 GB Media without me having to do anything.

Did you tried without the special characters that replace spaces in the url?


> **Absinthe Minded said:**
> No video outside of Firefox - so you must be right in that it's a codec issue.

Not as far as I'm aware, if you could point me to a guide, I'd be grateful to you. I'm using Hardy, BTW.

The [[COLOR="Red"]**tutorial that explains how to install gecko-mediaplayer**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766683") also has instructions on how to install the codecs.

> **Absinthe Minded said:**
> We, that's nice of you - I'm sure it will benefit many, so good for you. I just didn't want you to think that I wasn't bothering to try and do any of it myself. Aside from all that, I can't believe how much you've learnt in two months!

Thanks. I'm digging a lot of stuff from these forums, but there is still a lot to learn. I never imagined myself being addicted to command-line and bash scripts :D It is awesome how we can customize Linux and automate several boring processes.

---

### Post by Absinthe Minded on 2008-11-06
> **lovinglinux said:**
> Did you tried without the special characters that replace spaces in the url?

If I paste the original url into the properties box of Fast dial (like this):

> file:///media/disk-1/Documents and Settings/Nick/My Documents/Azureus Downloads/Dark Star/Dark_Star.avi

It is converted to include the space fills (%20), like this:

> file:///media/disk-1/Documents%20and%20Settings/Nick/My%20Documents/Azureus%20Downloads/Dark%20Star/Dark_Star.avi

The [[COLOR="Red"]**tutorial that explains how to install gecko-mediaplayer**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766683") also has instructions on how to install the codecs.

Yes, that's the tutorial I used, I entered the following two lines in a terminal:

```
sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin
```

```
sudo apt-get install gnome-mplayer gecko-mediaplayer
```

When I restart Firefox and visit the link mentioned in the tutorial to test the player ([here]("http://www.apple.com/trailers/")), I get a notification where the video should be saying 'Get the latest Quicktime Player'. I must be missing something here.

> Thanks. I'm digging a lot of stuff from these forums, but there is still a lot to learn. I never imagined myself being addicted to command-line and bash scripts :D It is awesome how we can customize Linux and automate several boring processes.

Well, you're doing well - I'd love to know half what you do. Linux is addictive and I agree that the customisation options are great, and they beat Windows by a long shot. I hate having to fire up windows now but thankfully the need is becoming more and more seldom!

---

### Post by lovinglinux on 2008-11-06
> **Absinthe Minded said:**
> If I paste the original url into the properties box of Fast dial (like this):

It is converted to include the space fills (%20), like this:


Try browsing the video with the file browser (Nautilus), copy the path and add "file:///" to the beginning of it.

> **Absinthe Minded said:**
> The [[COLOR="Red"]**tutorial that explains how to install gecko-mediaplayer**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766683") also has instructions on how to install the codecs.

Yes, that's the tutorial I used, I entered the following two lines in a terminal:

```
sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin
```

```
sudo apt-get install gnome-mplayer gecko-mediaplayer
```

When I restart Firefox and visit the link mentioned in the tutorial to test the player ([here]("http://www.apple.com/trailers/")), I get a notification where the video should be saying 'Get the latest Quicktime Player'. I must be missing something here.

Yes, you missed the first part, "--PART 1/5, ESSENTIAL PACKAGES--", including "Preparation" and "Installation".


> **Absinthe Minded said:**
> Well, you're doing well - I'd love to know half what you do. Linux is addictive and I agree that the customisation options are great, and they beat Windows by a long shot. I hate having to fire up windows now but thankfully the need is becoming more and more seldom!

Yeah, I finally got rid of Windows on all machines this week, after installing Intrepid on a notebook with some BIOS issues that were preventing the installation of Hardy. It feels so good to be Windows-free :D

I have been a Windows user for about 15 years, but my satisfaction with the OS was decreasing considerably, specially after trying Vista and loosing days to get XP back on the machine.

---

### Post by Absinthe Minded on 2008-11-06
> Yes, you missed the first part, "--PART 1/5, ESSENTIAL PACKAGES--", including "Preparation" and "Installation".

Funny, I already did all that. Maybe I did something wrong - I'll go and do it again and let you know how I get on.

I agree with you on Windows, I bought a laptop a few months ago with Vista pre-installed. I doubled the RAM and it was still way too slow so it has Hardy on it now, and is ten times faster. ;)

Nick.

---

### Post by Absinthe Minded on 2008-11-08
> **lovinglinux said:**
> Try browsing the video with the file browser (Nautilus), copy the path and add "file:///" to the beginning of it.

OK, I did that and you get a url without the '%20's. When you paste it into the Fast Dial properties, the spaces are replaced with the special characters, so no change there.

> Yes, you missed the first part, "--PART 1/5, ESSENTIAL PACKAGES--", including "Preparation" and "Installation".OK, I did it all again, here's the contents of the terminal, in case that helps:

```
nick@nick-linux-desktop:~$ sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
[sudo] password for nick: 
--19:47:41--  http://www.medibuntu.org/sources.list.d/hardy.list
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving www.medibuntu.org... 87.98.242.110
Connecting to www.medibuntu.org|87.98.242.110|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 226 [text/plain]

100%[====================================>] 226           --.--K/s             

19:47:41 (14.69 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [226/226]

nick@nick-linux-desktop:~$ wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
OK
Hit http://gb.archive.ubuntu.com hardy Release.gpg
Hit http://gb.archive.ubuntu.com hardy/main Translation-en_GB
Hit http://gb.archive.ubuntu.com hardy/restricted Translation-en_GB
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_GB 
Hit http://gb.archive.ubuntu.com hardy/universe Translation-en_GB    
Hit http://gb.archive.ubuntu.com hardy/multiverse Translation-en_GB  
Hit http://gb.archive.ubuntu.com hardy-updates Release.gpg
Ign http://gb.archive.ubuntu.com hardy-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com hardy-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com hardy-updates/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com hardy-updates/multiverse Translation-en_GB
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_GB
Ign http://security.ubuntu.com hardy-security/universe Translation-en_GB
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_GB
Hit http://security.ubuntu.com hardy-security Release                
Hit http://gb.archive.ubuntu.com hardy Release                       
Get: 1 http://packages.medibuntu.org hardy Release.gpg [189B]
Hit http://gb.archive.ubuntu.com hardy-updates Release                         
Ign http://packages.medibuntu.org hardy/free Translation-en_GB                 
Ign http://packages.medibuntu.org hardy/non-free Translation-en_GB            
Hit http://security.ubuntu.com hardy-security/main Packages                    
Hit http://security.ubuntu.com hardy-security/restricted Packages              
Hit http://security.ubuntu.com hardy-security/main Sources                     
Hit http://security.ubuntu.com hardy-security/restricted Sources               
Hit http://gb.archive.ubuntu.com hardy/main Packages                           
Get: 2 http://packages.medibuntu.org hardy Release [9335B]                     
Hit http://security.ubuntu.com hardy-security/universe Packages                
Hit http://security.ubuntu.com hardy-security/universe Sources                 
Hit http://security.ubuntu.com hardy-security/multiverse Packages              
Hit http://security.ubuntu.com hardy-security/multiverse Sources               
Hit http://gb.archive.ubuntu.com hardy/restricted Packages                     
Hit http://gb.archive.ubuntu.com hardy/main Sources                      
Hit http://gb.archive.ubuntu.com hardy/restricted Sources                
Hit http://gb.archive.ubuntu.com hardy/universe Packages                 
Hit http://gb.archive.ubuntu.com hardy/universe Sources
Hit http://gb.archive.ubuntu.com hardy/multiverse Packages
Hit http://gb.archive.ubuntu.com hardy/multiverse Sources
Hit http://gb.archive.ubuntu.com hardy-updates/main Packages
Hit http://gb.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://gb.archive.ubuntu.com hardy-updates/main Sources
Hit http://gb.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://gb.archive.ubuntu.com hardy-updates/universe Packages
Hit http://gb.archive.ubuntu.com hardy-updates/universe Sources
Hit http://gb.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://gb.archive.ubuntu.com hardy-updates/multiverse Sources
Get: 3 http://packages.medibuntu.org hardy/free Packages [6322B]
Get: 4 http://packages.medibuntu.org hardy/non-free Packages [7934B]          
Fetched 23.8kB in 1s (17.8kB/s)                                               
Reading package lists... Done
nick@nick-linux-desktop:~$ sudo apt-get remove gnash gnash-common icedtea-gcjwebplugin libflash-mozplugin libflashsupport mozilla-plugin-gnash openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnash is not installed, so not removed
Package gnash-common is not installed, so not removed
Package icedtea-gcjwebplugin is not installed, so not removed
Package libflash-mozplugin is not installed, so not removed
Package libflashsupport is not installed, so not removed
Package mozilla-plugin-gnash is not installed, so not removed
Package openjdk-6-jre is not installed, so not removed
Package openjdk-6-jre-headless is not installed, so not removed
Package openjdk-6-jre-lib is not installed, so not removed
Package swfdec-mozilla is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 36 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
alsa-oss is already the newest version.
faac is already the newest version.
faad is already the newest version.
gstreamer0.10-ffmpeg is already the newest version.
gstreamer0.10-plugins-bad is already the newest version.
gstreamer0.10-plugins-bad-multiverse is already the newest version.
gstreamer0.10-plugins-ugly is already the newest version.
gstreamer0.10-plugins-ugly-multiverse is already the newest version.
gstreamer0.10-pitfdll is already the newest version.
liblame0 is already the newest version.
non-free-codecs is already the newest version.
sun-java6-fonts is already the newest version.
sun-java6-jre is already the newest version.
sun-java6-plugin is already the newest version.
unrar is already the newest version.
Suggested packages:
  konqueror-nsplugins libflashsupport ttf-xfree86-nonfree xfs
The following packages will be upgraded:
  flashplugin-nonfree
1 upgraded, 0 newly installed, 0 to remove and 35 not upgraded.
Need to get 18.8kB of archives.
After this operation, 0B of additional disk space will be used.
Get: 1 http://gb.archive.ubuntu.com hardy-backports/multiverse flashplugin-nonfree 10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2 [18.8kB]
Fetched 18.8kB in 0s (108kB/s)             
Preconfiguring packages ...
(Reading database ... 117517 files and directories currently installed.)
Preparing to replace flashplugin-nonfree 9.0.124.0ubuntu2 (using .../flashplugin-nonfree_10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2_i386.deb) ...
Unpacking replacement flashplugin-nonfree ...
Setting up flashplugin-nonfree (10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2) ...
Installing from local file /var/cache/flashplugin-nonfree/install_flash_player_9_linux.tar.gz
Flash Plugin installed.

nick@nick-linux-desktop:~$ sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kaffeine-mozilla is not installed, so not removed
Package mozilla-helix-player is not installed, so not removed
Package mozilla-plugin-vlc is not installed, so not removed
Package totem-mozilla is not installed, so not removed
Package xine-plugin is not installed, so not removed
The following packages will be REMOVED
  mozilla-mplayer
0 upgraded, 0 newly installed, 1 to remove and 34 not upgraded.
After this operation, 1839kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 117516 files and directories currently installed.)
Removing mozilla-mplayer ...
nick@nick-linux-desktop:~$ sudo apt-get install gnome-mplayer gecko-mediaplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-mplayer is already the newest version.
The following NEW packages will be installed
  gecko-mediaplayer
0 upgraded, 1 newly installed, 0 to remove and 34 not upgraded.
Need to get 0B/168kB of archives.
After this operation, 623kB of additional disk space will be used.
Selecting previously deselected package gecko-mediaplayer.
(Reading database ... 117439 files and directories currently installed.)
Unpacking gecko-mediaplayer (from .../gecko-mediaplayer_0.6.0-0ubuntu1.1_i386.deb) ...
Setting up gecko-mediaplayer (0.6.0-0ubuntu1.1) ...

nick@nick-linux-desktop:~$
```Hope this helps - Cheers,
Nick.

---

### Post by lovinglinux on 2008-11-08
> **Absinthe Minded said:**
> OK, I did that and you get a url without the '%20's. When you paste it into the Fast Dial properties, the spaces are replaced with the special characters, so no change there.

OK, I did it all again, here's the contents of the terminal, in case that helps:
Hope this helps - Cheers,
Nick.

Do you still have no video?

---

### Post by johanhartman on 2008-11-10
Hi, great HowTo...

Can I just ask how you set up fast-dial to appear like in your first screenshot (with the middle two panels removed)?

---

### Post by lovinglinux on 2008-11-10
> **johanhartman said:**
> Hi, great HowTo...

Thank you.

> **johanhartman said:**
> Can I just ask how you set up fast-dial to appear like in your first screenshot (with the middle two panels removed)?

Just leave those thumbnails empty, then right click outside the thumbs and select properties. In the general tab, disable the option "Show empty cells".

---

### Post by lovinglinux on 2008-11-12
I have added section 9.3, which explains how to create a script to select one of several playlists and select if you want to play embedded in Firefox or with a standalone player.

---

### Post by Absinthe Minded on 2008-11-12
> **lovinglinux said:**
> Do you still have no video?

Hi again, still no video - all I get is the audio with:

> **File:** /tmp/gecko/[COLOR=Red]9pCou3[/COLOR] in the top left corner. The red part changes each time you launch the video.

Thanks,
Nick.

---

### Post by lovinglinux on 2008-11-12
> **Absinthe Minded said:**
> Hi again, still no video - all I get is the audio with:

 in the top left corner. The red part changes each time you launch the video.

Thanks,
Nick.

The /tmp/gecko/[COLOR="Red"]9pCou3[/COLOR] is normal. Since you are opening the file inside Firefox, it "thinks" the video is from the web, so it caches it in the tmp directory. The name of the file is random, because it's how the Firefox plugin handles temporary files. Nothing to worry about.

Since you are not getting any video with the standalone player and the file is actually being opened with the Firefox plugin, I'm sure it's a codec issue. There is nothing wrong with the procedure related to Firefox. 

I have analyzed your terminal output and there is nothing wrong with it. It should be working, since you have all the necessary packages. You could try installing the newest gnome-mplayer version from [http://www.getdeb.net/app/GNOME+MPlayer](http://www.getdeb.net/app/GNOME+MPlayer) 

I'm not sure if it will help, but the deb version available there is the one that I'm using. If this does not solve the issue, then I guess the best thing to do is to open a new thread for support about video codecs. I'm not experienced enough to solve this kind of problem, so maybe someone else could guide you through a better troubleshooting procedure.

Anyway, if you want to proceed with my tutorial go ahead. The fact that you don't get any video will not hold you down from completing the rest of the tutorial. It wil just be annoying, because you can't see the result as expected, but once you fix the codec issue, everything will be working fine.

> **Absinthe Minded said:**
> OK, I did that and you get a url without the '%20's. When you paste it into the Fast Dial properties, the spaces are replaced with the special characters, so no change there.

Try opening a video file from the same partition/disk as the Ubuntu installation and see if it works. If yes, then it should be some issue related to the Windows partition. I don't have a NTFS partition to test, but I have tested using a file from a folder path with spaces and it does add the '%20's, but the video plays normally.

---

### Post by eber69 on 2008-11-12
> After downloading or grabbing our XMLTV source file, we need to download the [[COLOR="Red"]**EPG**[/COLOR]]("http://tvfox.bplaced.net/TvFox_0.1.6.zip") from [[COLOR="Red"]**TvFox **[/COLOR]]("http://tvfox.bplaced.net/") site. Extract the downloaded file to your home folder. You should see a new directory called "TvFox 0.1.6". 

Very clear guide and very exiting application. I'm working through the steps in your guide now. It seems the part where you should download EPG is not working. The link is not leading to an existing site or download. Is it fixable? Or is there a workaround?
Cheers

---

### Post by lovinglinux on 2008-11-12
> **eber69 said:**
> Very clear guide and very exiting application. I'm working through the steps in your guide now. It seems the part where you should download EPG is not working. The link is not leading to an existing site or download. Is it fixable? Or is there a workaround?
Cheers

Thanks for pointing that.

Unfortunately the developer of TvFox is working on something new and in the meantime the links are broken. You could try contacting him through his [[COLOR="Red"]**support thread**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=857247"). 

If you want an EPG alternative, I would recommend [[COLOR="Red"]**Freeguide**[/COLOR]]("http://www.artificialworlds.net/freeguide/Main/HomePage"). It isn't integrated to Firefox, but it is an excellent EPG application.

Nevertheless, the EPG section is kind of independent. So you can proceed without affecting the outcome of the tutorial.

---

### Post by johanhartman on 2008-11-13
Another question. I created a seperate launcher for the mediacentre on my top panel in gnome. By deafault gnome has another launcher for firefox (command: "firefox %u"). Everytime I restart on of the icons is turned into the other, i.e. the mediacentre launcher becomes an exact copy of the other icon, and somtimes the other way round.

Do you have any remedies for this?

---

### Post by lovinglinux on 2008-11-13
> **johanhartman said:**
> Another question. I created a seperate launcher for the mediacentre on my top panel in gnome. By deafault gnome has another launcher for firefox (command: "firefox %u"). Everytime I restart on of the icons is turned into the other, i.e. the mediacentre launcher becomes an exact copy of the other icon, and somtimes the other way round.

Do you have any remedies for this?

I'm not sure what are you trying to describe. Do you mean that when you reboot, the mediacenter icon command change to "firefox %u" and vice versa or do you mean that when you launch Firefox with the mediacenter icon it launches the other profile? I guess is the second situation right?

What happens is that when you launch the first profile with the -no-remote option, then you must launch other profiles with the same option, otherwise Firefox will open another window of the current profile. This does not happen if you launch the default profile with "firefox %u" first.

So, all you have to do is replace the command "firefox %u" with the one below:

```
firefox -no-remote -P [COLOR="Red"]**yourdefaultprofile**[/COLOR]
```

You could also create one icon for each profile you have using the above options and hide the default Firefox icon from the menu.

---

### Post by lovinglinux on 2008-11-13
I have included a new section 10 for Remote configuration, so we can control the Firefox Media Center from the couch. 

:popcorn:

---

### Post by eber69 on 2008-11-17
I have a TV-card not which tvtime does not support :( Could I use another player to make it work for me? My TV-card is Hauppauge PVR-150.
Cheers,
Martin

---

### Post by lovinglinux on 2008-11-17
> **eber69 said:**
> I have a TV-card not which tvtime does not support :( Could I use another player to make it work for me? My TV-card is Hauppauge PVR-150.
Cheers,
Martin

Probably yes. You will have to adapt some scripts to use the other software instead of tvtime. Do you have already used it or you still need to configure your TV card?

I don't know your TV card, but I guess it is pretty common. Try the tutorial and let me know if there is something I can help to make it work.

---

### Post by tj.milligan on 2008-11-17
Lovinglinux, thanks for the tutorial! Worked fine for me (although I don't have TV, so I'm using your guide as a media center for local and network audio/video).

My question is about streaming. Flumotion is set up and working locally, but **how would I get get my firefox media center to stream over the www (password protected access would be nice too)?** Currently, I have [ampache]("http://www.ampache.org/") installed (via intrepid repo), which, combined with apache2, acts as a streaming audio [no video] server that I access at <me>.dyndns.org/ampache. I'd like to set yours up as <me>.dyndns.org/ffmc. Thanks in advance!

---

### Post by lovinglinux on 2008-11-17
> **tj.milligan said:**
> Lovinglinux, thanks for the tutorial! Worked fine for me (although I don't have TV, so I'm using your guide as a media center for local and network audio/video).

My question is about streaming. Flumotion is set up and working locally, but **how would I get get my firefox media center to stream over the www (password protected access would be nice too)?** Currently, I have [ampache]("http://www.ampache.org/") installed (via intrepid repo), which, combined with apache2, acts as a streaming audio [no video] server that I access at <me>.dyndns.org/ampache. I'd like to set yours up as <me>.dyndns.org/ffmc. Thanks in advance!

First of all, I would like to apologize to you due to my scarce knowledge about flumotion and Internet streaming. I have tested flumotion and I wrote that part of the tutorial to provide a working streaming option to Firefox media center users, because this is an important feature of real media centers like MythTV. Nevertheless, since you don't have a TV card, this kind of setup is not really needed and I think this is not the best solution for you.

Since you already have access to your audio gallery through php/apache2/dyndns, the best solution to you would be installing a php based media gallery for videos, that you can access via http like you access ampache.

Unfortunately, I don't know any video gallery manager that has the same features like ampache, but you could try [[COLOR="Red"]**Gallery2**[/COLOR]]("http://gallery.menalto.com/"). It is an excellent photo gallery manager, that has some support for videos. Depending on the video format, you can watch it through Gallery2 like video streaming web sites, but some video formats only allow direct download. Anyway, it has lot's of security options, you can create albums with passwords or even completely hide the album url from visitors.

Gallery2 is designed for web servers, so the main page is accessible to everyone who knows your domain <me>.dyndns.org/gallery2. Nevertheless, you could create a password for it using .htaccess, so the main page would be blocked unless you enter a password. I don' know if you are already using this security approach with ampache, but since it is also written in php you can and I strongly recommend you to do it, unless you want other people to see ampache content.

Another otpion would be installing [[COLOR="Red"]**Joomla CMS**[/COLOR]]("http://www.joomla.org/"), because it has several [[COLOR="Red"]**video players**[/COLOR]]("http://extensions.joomla.org/index.php?option=com_mtree&task=listcats&cat_id=1934&Itemid=35") and [[COLOR="Red"]**streaming**[/COLOR]]("http://extensions.joomla.org/index.php?option=com_mtree&task=listcats&cat_id=1943&Itemid=35") extensions.

---

### Post by eber69 on 2008-11-18
> **lovinglinux said:**
> Probably yes. You will have to adapt some scripts to use the other software instead of tvtime. Do you have already used it or you still need to configure your TV card?

I don't know your TV card, but I guess it is pretty common. Try the tutorial and let me know if there is something I can help to make it work.

It's working fine with mplayer. That's my prefered player, I guess. I'm no script wizard I'm afraid so any help is apreciated.
Cheers,
Martin

---

### Post by lovinglinux on 2008-11-18
> **eber69 said:**
> It's working fine with mplayer. That's my prefered player, I guess. I'm no script wizard I'm afraid so any help is apreciated.
Cheers,
Martin

When you find a script that contains the word "tvtime", replace it with "mplayer" and tell me how it goes. If you find issues, please let me know the section or procedure so we can debug and find solutions for each situation.

You might also want to replace "smplayer" and "gnome-mplayer" with "mplayer" command.

---

### Post by lovinglinux on 2008-11-23
I'm glad to announce that I have expanded section 8 to include a PVR recording scheduler. 

So now you can start recording TV at any time, record and watch with time-shifting capabilities and schedule in advance any number of recordings you want, with predefined starting time and recording runtime.

:popcorn:

---

### Post by lovinglinux on 2008-11-24
I have updated the cron steps, because it wasn't really working with the previous codes.

---

### Post by lovinglinux on 2008-11-24
**[COLOR="Red"]Another important update![/COLOR]**

I have expanded section 8 to include support for scheduling TV recordings by e-mail, using a Gmail account.

So now we can tell our media center to record a TV show by simply sending an e-mail with the configuration files.

:popcorn:

Since the the method was created by me with programs not designed to do this, it isn't very elegant, but it works. I would appreciate comments about it's functionality.

---

### Post by lovinglinux on 2008-12-05
I have updated several scripts and the database from section 8, to include TvFox EPG integration with the recording scheduler.

So now we can schedule recordings manually, by e-mail or using the EPG grid.
:popcorn:

**Note:** the "scheduler.sqlite" database has now a new field for storing the program title, provided by TvFox. All scripts related to the scheduler database were also updated to include this new value and recorded files will be named after it. The modified sections were 8.4, 8.5 and the new 8.6.

---

### Post by lovinglinux on 2008-12-18
[COLOR="Red"]**Important update!**[/COLOR]

The tutorial will not be maintained anymore, because I have created a Firefox extension to do all the stuff on a single and simple interface.

Please visit the [[COLOR="Red"]**FoxMediaCenter**[/COLOR]]("http://foxmediacenter-extension.blogspot.com/") website for downloading it.

---

