---
title: "Media Center extension for Firefox-Linux"
date: 2008-12-29
forum: Multimedia Software
---

### Post by lovinglinux on 2008-12-29
FoxMediaCenter extension is no longer under development.

---

### Post by wolfen69 on 2009-01-02
tvtime will not work for my pvr150. does it have to be tvtime, or can i use something else? btw, i use vlc for tv.

---

### Post by lovinglinux on 2009-01-02
> **wolfen69 said:**
> tvtime will not work for my pvr150. does it have to be tvtime, or can i use something else? btw, i use vlc for tv.

Unfortunately, not yet. I have plans to support other TV players but this will take some time. Maybe I could write another version for VLC, instead of implementing this option in the same code, because this would be easier and faster.

I can't capture using VLC here, so I need some information to write the code and send to you for testing. I can't promise anything, but I will try.

Could you please post your tv command so I can take a look at it?

Would also help if you specify the input source (AV, SVHS, RF) and audio/video devices you use and also how do you change channels.

Do you also use VLC for recording?

---

### Post by ugm6hr on 2009-01-06
I believe that xine is the only engine that will easily allow the use of "budget" DVB (USB) cards to record and then playback the recordings; it is certainly the only program (or Kaffeine etc) that will display TV properly for me.  VLC works, but the audio / video quality is much poorer (haven't tried recording).  Never gave MPlayer a proper go. TVtime is another one that only supports full-featured DVB cards.

This looks really nice - I'll have to give it a try if xine becomes a possiblility.

After struggling with freevo, I've decided to just use Kaffeine for TV for now.

---

### Post by lovinglinux on 2009-01-06
> **ugm6hr said:**
> I believe that xine is the only engine that will easily allow the use of "budget" DVB (USB) cards to record and then playback the recordings; it is certainly the only program (or Kaffeine etc) that will display TV properly for me.  VLC works, but the audio / video quality is much poorer (haven't tried recording).  Never gave MPlayer a proper go. TVtime is another one that only supports full-featured DVB cards.

This looks really nice - I'll have to give it a try if xine becomes a possiblility.

After struggling with freevo, I've decided to just use Kaffeine for TV for now.

Thanks for the suggestions and comments. I guess making xine the alternative engine would be the way to go. I will look into this when the extension becomes more stable. I'm currently making a lot of changes and adding new features, not related to recording/viewing TV, so there is a lot of work to do already.

---

### Post by binbash on 2009-03-07
I will check this out thanks

---

### Post by wolfen69 on 2009-04-18
simple question. how do i launch it?

edit: nevermind, i got it. but tvtime does not work for me.

for vlc i use the command
```
ivtv-tune -c25
```
to change channels.

---

### Post by lovinglinux on 2009-04-18
> **wolfen69 said:**
> simple question. how do i launch it?

edit: nevermind, i got it. but tvtime does not work for me.

for vlc i use the command
```
ivtv-tune -c25
```
to change channels.

I'm tracking down some of your messages in the forums about your card, so I can understand how it works, because I don't have a DVB card. I will try to include an option to use ivtv for changing channels in the next version.

Let me ask you a few things:

1 - which are the video and audio devices you currently use for recording?
2 - if you change the channel with the ivtv command first, then can you record with my extension?

---

### Post by wolfen69 on 2009-04-18
> **lovinglinux said:**
> I'm tracking down some of your messages in the forums about your card, so I can understand how it works, because I don't have a DVB card. I will try to include an option to use ivtv for changing channels in the next version.

Let me ask you a few things:

1 - which are the video and audio devices you currently use for recording?
2 - if you change the channel with the ivtv command first, then can you record with my extension?

i don't do alot of recording, but when i do, i just
```
cat /dev/video0 > /tmp/name_of_file.mpg
```
i believe mplayer handles that part.

actually, i found a desktop "remote control" to change channels so i don't have to use the terminal. [TV Remote]("http://sourceforge.net/projects/tvremote/")

i will try recording with your extension and see what happens.

btw, it would be really great if you had support for the hauppauge pvr x50 line of cards. they are one of the best selling tv tuners out there. otherwise i will have to install mythbuntu before football season starts. :D

---

### Post by wolfen69 on 2009-04-18
i just tried recording a channel, and when i hit record, tvtime opens and says "no video source", and does not record. it seems like a really great app, it's just too bad i can't use it. and yes, i was watching a channel on vlc when i hit record.

btw, here is my "how to" for other people that have my card.

I have a Hauppauge pvr150 card running on my box, and I get  tv by: 

```
sudo apt-get install ivtv-utils 
```

open VLC player

File -> Open Capture Device -> PVR -> OK or if you are using a newer version of VLC, do Media > Open Capture Device > PVR (from pull down menu) > OK.

then you can do (in terminal)

```
ivtv-tune -c25
``` (25 is channel number)

which changes the channel.

```
ivtv-tune -h
```

to see the options which control the card. 


for a cool desktop tv remote,(so you dont have to use terminal to change channels) go to: [http://tvremote.sourceforge.net/](http://tvremote.sourceforge.net/)

remember to have java installed first. then you can right click: open with java.

to record tv:

```
cat /dev/video0 > /tmp/name_of_file.mpg
```

it will record whatever channel you are on. then ctrl-c to stop.

---

### Post by lovinglinux on 2009-07-15
I have updated the extension to provide compatibility with Firefox 3.5.

It might take some time to appear on Mozilla web site but the version on [http://fmc.isgreat.org/](http://fmc.isgreat.org/) is already updated.

Please test it and give some feedback.

---

### Post by lovinglinux on 2009-07-28
I have released version 3.0.1 today.

FoxMediaCenter 3 series is almost a complete rewrite, focusing on usability and performance improvements. The interface and tools are more intuitive and were redesigned to make use of sidebars instead of dialog boxes.

Some features were dropped to make the extension configuration and usage simpler. Nevertheless, the basic features are more powerful than ever. I feel that now the extension is getting were I wanted when I started to develop it. Nevertheless, there are still room for improvements, so please give some feedback.

---

### Post by lovinglinux on 2009-08-14
Version 3.0.3 has been released, bringing some cool new features, like Speed Dial integration, video preview contact sheets and style chooser. It also has several code improvements, with most of the features now implemented as javascript instead of bash scripts, which allows real-time update of the data displayed.

**New Features & Changes**

[LIST]
[*]Added support for Firefox 3.6a1
[*]Introduced styles and themes tool, allowing to easily choose different color schemes for each sidebar tool and EPG.
[*]Added a Speed Dial bookmark creation tool, that automatically generates a video snapshot and add it to a Speed Dial slot.
[*]The video and pvr tabs of the Playlist Manager allows to preview the video through a contactsheet, which is created with Video Contact Sheet *NIX (vcs) if the image doesn't exist yet.
[*]Added a "deleted" column to the Watched tab in the Playlist Manager and changed the sorting based on delete status and title
[*]Alternative title is now hidden in the EPG tabs
[*]Posters and walpapers thumbnail paths were removed from preferences, so now the thumbnail images displayed in the programme info are from the wallpaper folder
[*]Changed the order and filtering of EPG tabs
[*]Improved alert and message dialogs
[*]Improved handling of file names with spaces
[*]Changed default paths for required applications
[*]Improved file and applications checking
[*]Moved several code functions from bash scripts to javascripts
[*]Several code improvements
[/LIST]

---

### Post by lovinglinux on 2009-08-17
I have released version 3.0.5. The short period release was due to some bugs that prevented some features to work in some cases, but it also brings some new features and improvements. 

**v3.0.5 (17/04)**

[list][*] Fixed Playlist malfunction due to missing current.pls file in the fmcplaylists folder
[*] Added an option to undock the EPG, opening it on a popup
[*] Improved selections and actions on the EPG, which means there is no more need to reselect a program after selecting another one in another tab, before clicking the Quick Add and Info buttons.
[*] The sidebar now re-sizes automatically to the minimum required width.
[*] The Watched tab, from Playlist manager, has been split in two, separating deleted files from the rest.[/list]


**v3.0.4 (15/04)**

[list][*] fixed issues in the Portuguese translation
[*] better video snapshot and Speed Dial thumbnail creation
[*] changed buttons spacing in the playlist tab
[*] moved several functions from bash to javascript[/list]

---

### Post by lovinglinux on 2009-08-31
Version 3.1.0 has been released. It brings new features, like a redesigned recorder which uses mencoder (does not require TVtime anymore) and a new automation system for reminders and recording schedules . This version also brings performance improvements when scanning media and updating data, which appears almost immediately on most of the interface.

**New Features & Changes**

[list][*] Firefox 3.0 no longer supported
[*] Fixed web site not opening from undocked EPG.
[*] Video Contact Sheet *NIX replaced with SlickSlice
[*] Added support for png wallpapers and posters.
[*] Added support for spaces on wallpapers and posters names.
[*] Scanning media folders does not require to reload the data anymore.
[*] Media sub-folders are not supported anymore.
[*] TVTime is not required for TV recording anymore.
[*] TV application can be changed now.
[*] Transcode was replaced with mencoder for TV recording.
[*] PVR tool functions have been moved to the PVR tab in the Playlist Manager
[*] PVR Player option has been removed, since videos are now played by Firefox
[*] Time-shifting is done through the Playlist Manager now, since the recorded video becomes available as soon as the recording starts.
[*] Reminders and PVR automatic features are now controled by Firefox instead of cron, which means Firefox must be opened to receive reminder alerts and to record programme automatically.
[*] New TV On Remind feature, that launches the TV application when a programme reminder is triggered. This can be enabled/disabled from the Reminders tab in the Scheduler sidebar.
[*] Removed script editors from the Maintenance tab.
[*] Images are opened with Firefox instead of external applications.
[*] New confirmation dialogs when launching shell commands, which copies the command to the clipboard for verification or for running it manually, but you can still run them automatically if you wish.
[*] Less obtrusive alerts when confirmation is not required
[*] Extension fully localized and translated to Portuguese, except for shell script alerts.
[*] Added a Help option to the main menu.
[*] Several performance improvements.
[*] Moved most remaining functions from bash to javascript.[/list]

---

### Post by lovinglinux on 2010-01-17
FoxMediaCenter 4 has been released and brings a new simplified interface, better usability and some cool new features, like the EPG filters, support for multiple folders in the Playlist Manager and support for DVB TV cards.

**New Features & Changes**

[list][*] this version is not compatible with previous ones and the database will be reset upon installation.
[*] new improved and simplified interface.
[*] new improved recorder with dvb cards support.
[*] integration between weekly schedules (formerly series) and programme database.
[*] added Windows compatibility.
[*] added database reset and restore features.
[*] added search and filter capabilities to the EPG and Playlist Manager.
[*] added support for bookmarks and multiple folders in the Playlist Manager.
[*] added options to choose standalone or embedded media players.
[*] xmltv import feature now supports multiple categories, directors and cast data.
[*] web site links automatically set as imdb search when importing xmltv listings.
[*] text sent to clipboard is now stripped of dots, double spaces, underlines and extensions.
[*] removed dependency on zenity, sqlite3 and xmlstarlet, which are no longer required.
[*] removed contact sheet creation feature.
[*] removed Speed Dial integration.
[*] removed TV On Remind feature.
[*] removed DVD burning feature.
[*] removed statistics feature.
[*] fixed several bugs.
[*] [/list]

---

### Post by lovinglinux on 2010-02-23
FoxMediaCenter 4.0.2 has been released and brings support for importing XML files exported by the IMDB Ripper extension and a couple of bug fixes. See [Changelog](http://foxmediacenter.lovinglinux.megabyet.net/?page_id=13) for details.

---

### Post by lovinglinux on 2010-07-14
FoxMediaCenter extension will no longer be developed, but will be replaced by a new set of extensions that will provide the same functionality, with better performance, more flexibility and more intuitive interface.

The new extensions are currently under development and will be available before the release of the final Firefox 4.

The reason for ending FoxMediaCenter is that it has some flaws in the code (not security related) that prevented it from being approved by Mozilla. This was the first Firefox extension I ever developed and although it was becoming a good extension, it would require major changes in the code to make it pass through Mozilla's approval requirements. Instead of doing that, I decided to rewrite the extension, splitting it into three new extensions. The first extension, called Mediabar, will be responsible for media management. It will allow to organize and view videos, music and games through Firefox's sidebar. The second one, called FoxPVR, will be responsible for capturing TV and the third one, called FoxEPG, will be responsible for the Electronic Program Guide.

All three extensions will be independent of each other, but will also be automatically integrated when installed together. The main reason for doing this, is that is a lot easier to maintain the extensions. FoxMediaCenter code was becoming really big and convoluted. Additionally, this will allow users to benefit from one extension, even if the other is not compatible with his OS. For now, the only extension that is not cross-platform is FoxPVR.

Most of the work on these new extensions have already been done and they are working really great. There are several new features and the interface is much more friendly.

If you want to be informed about the release of these new extensions, please subscribe to my blog [ RSS Feed]("http://feeds.feedburner.com/lovinglinuxblog") or [Twitter]("http://twitter.com/lovinglinuxblog") or [visit my blog]("http://lovinglinuxblog.blogspot.com/").

---

