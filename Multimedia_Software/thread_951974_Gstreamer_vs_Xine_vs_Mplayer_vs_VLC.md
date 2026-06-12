---
title: "Gstreamer vs Xine vs Mplayer vs VLC"
date: 2008-10-18
forum: Multimedia Software
---

### Post by sicofante on 2008-10-18
I'm trying to understand the differences between these four players/libraries. Any info would be great. I also would appreciate any links pointing to fair comparisons between them. I can't seem to find them myself.

So far, what I've learned is that Gstreamer and Xine are plug-in based, while Mplayer and VLC are "all-in-one" solutions. I can imagine the pros and cons of both approaches from a developer's point of view, but not so much from a user's point of view.

I'm especially concerned about picture quality and speed. For instance, I'd like to know which one has implemented the best deinterlacing filters or which one is faster at fast-forwarding (or rewinding) MPEG2/4 streams. On the other hand, I don't care very much about formats/codecs support. As long as I can play MPEG2 and MPEG4 I'm happy and that seems to be good enough on all of them, right?

I'm also interested in knowing about the best GTK+ frontends (not so much on Qt alternatives).

Thanks for any information.

(Please no "Xxx is my favourite player" posts, unless you are willing to reason why.)

---

### Post by wolfen69 on 2008-10-18
gstreamer is not a player, it provides the codecs needed to play media. as far as which one is better, is a matter of preference. i've always preferred vlc. it can handle just about anything.

---

### Post by sicofante on 2008-10-18
I've been very careful not to ask which one is better and I hope this thread doesn't turn into that at all. I'm asking about their differences. (I haven't said Gstreamer is a player either...)

---

### Post by cor2y on 2008-10-18
Ok heres my take , others will probably disagree also i have no links as such.

1) Vlc aka videolan can play ALMOST all media formats, has a webbrowser plugin it can also double as video webserver client and on the fly video encoder/stream recorder/dvd movie ripper, the only draw back is when you run into a format it cannot play such as real media files and for some people (including myself) the usage of the more expansive features (like say dumping a dvd to harddrive or recording a video stream) were not as intituative as it could have been.

2) Mplayer, simple enough media player with its own webbrowser plugin, with the w32codecs installed it can play all media formats that vlc cannot play even drm'd wmv/wma (this is provided you have the hash key to decrypt the file) and blu-ray/hd-dvd movies although not from the disc. Mplayer can also record video streams like vlc as well as dump dvd/hd-dvd/blu-ray movies to the harddrive however most of these features requires the use of the terminal/cmdline. The only thing mplayer lacks is the ability to use dvd interactive menus, you can navigate chapters etc but not navigate or use menus

3) Totem-gstreamer , once the restricted/multiverse gstreamer plugins are installed totem-gstreamer like mplayer can play all media formats however unlike mplayer it cannot play/decrypt  drm'd media or hd-dvd/blu-ray discs, if the files have already been decrypted then it can play them, also gstreamer at present doesn't have the ability to play/interact with dvd menus and its ability to navigate a dvd is somewhat lacking , i would not recommend using totem-gstreamer for dvd playback it sometimes gets what is the main movie of the disc wrong and will perhaps only play the trailers/coming attractions section of the disc. It has no recording abilities like mplayer or vlc although it can play media streams either through player or its webbrowser plugin. Neither the ability to dump a dvd disc to harddrive

4) Totem-xine, with the xine library in use, totem-xine can play all media formats with the exception of encrypted/drm'd media and blu-ray/hd-dvd. Where it out does both totem-gstreamer and mplayer is the ability like VLC to use/navigate dvd menus. It has no recording abilities like mplayer or vlc although it can play media streams either through player or its webbrowser plugin. Neither the ability to dump a dvd disc to harddrive

Picture quality for each player will depend on what drivers are in use for your video hardware as well as what libraries the player in question was compiled with, for example gstreamer-ffmpeg for 8.04 has bad/glitchy rendering for mpeg4 video artifacts/pixelation can be seen during video playback this was fixed by gstreamer after the launch of hardy so you either have the choice of compiling gstreamer-ffmpeg yourself and installing or waiting until Intrepid Ibex where it is fixed since a later/updated version of gstreamer-ffmpeg is used. In the case of VLC and Totem-xine both use native libraries to render ASF/WMV videos instead of the w32codecs that mplayer uses and on occaison there have been artifacts/pixelation when using the player slider to advance or rewind a movie in those video streams. But on the whole there is no discernable picture quality difference between each player.

Video frontends, Mplayer, VLC has a number of custom skins you can download from the official sites that you can choose for use as the player interface, interfaces that look like windows media player, cyberlink power dvd to even simpler interfaces , however since totem is an official gnome based app it doesn't share the ability to alter the interface like Mplayer and VLC can at most what you can do is change the gnome theme and see totem change to reflect this. Gnome Look is a good place to see different gnome themes [http://gnome-look.org/](http://gnome-look.org/)

---

### Post by sicofante on 2008-10-19
Nice bits of info. Thanks cor2y. Are you sure the latest libdvdnav in Mplayer doesn't allow to play DVD menus and interact with them? If I understand correctly from your post, only Xine would be able to play those?

BTW: these are THE four contenders, right? Or are there any others?

---

### Post by mc4man on 2008-10-19
> Are you sure the latest libdvdnav in Mplayer doesn't allow to play DVD menus and interact with them? If I understand correctly from your post, only Xine would be able to play those?

All the xine based players have dvd navigation as does vlc. Vlc defaults to starting on the main menu, that can be changed if you wish to play back as dvd would on a standalone.

Additional players - kaffeine and xine-ui (both xine based, xine-ui has large number on config. options in the gui.

Mplayer can be built to include dvdnav support, works fairly well though needs to be run from the cli (mplayer dvdnav:// <parameters>

Atm the only frontend supporting dvdnav in mplayer is gnome-mplayer which is a very 'simple' player.( navigation seems to be limited to next, previous, ff, rewind (running ver. 0.8.0

Hopefully smplayer will support dvdnav in the future 

A prebuilt mplayer w/ dvdnav can be found here (note you need the latest libdvdnav4 and libdvdread[COLOR="Red"]4[/COLOR]
also in there are links to a normal mplayer and latest smplayer

[http://ubuntuforums.org/showthread.php?t=917700](http://ubuntuforums.org/showthread.php?t=917700)

Atm I'd keep another player installed along with mplayer (dvdnav ver.) All the xine based players can co-exist the the latest dvdnav4 (4.1.3-1) as can vlc if it's built.
Haven't tried using libdvdnav4 ver. 4.1.2-3 with mplayer (dvdnav ver.) which works better with a repo version of vlc

---

### Post by crazyness003 on 2008-10-19
Yes indeed very in-depth coverage of the different players, thanks. I have totem, vlc, mplayer, and gxine installed, so if one fails to do what i want, i use another. Default is Totem, Secnond is VLC, then M player.

> **sicofante said:**
> ... Thanks cor2y...
Im sure the author would appreciate a [[IMG]http://ubuntuforums.org/images/buttons/post_thanks.gif[/IMG]]("http://ubuntuforums.org/post_thanks.php?do=post_thanks_add&p=5990482&securitytoken=1224432761-1b5de27a353a89351306cb458eb377c3dad47b28") for his/her efforts (most likely his, but we havent formally met)

Go on, click it. its right there.

---

### Post by Grams79 on 2008-10-19
Simple streaming solution:
[http://ubuntuforums.org/showthread.php?p=5997093](http://ubuntuforums.org/showthread.php?p=5997093)
:popcorn:

---

### Post by sicofante on 2008-10-22
> **crazyness003 said:**
> Im sure the author would appreciate a [[IMG]http://ubuntuforums.org/images/buttons/post_thanks.gif[/IMG]]("http://ubuntuforums.org/post_thanks.php?do=post_thanks_add&p=5990482&securitytoken=1224432761-1b5de27a353a89351306cb458eb377c3dad47b28") for his/her efforts (most likely his, but we havent formally met)

Go on, click it. its right there.
You're absolutely right. Well deserved thanks.

Now that I have some info on these four (and hoping there isn't a fifth one to look at... ;-)) I'll be trying them thoroughly and give some feedback myself.

---

### Post by xenoterracide on 2008-10-29
you might want to check out smplayer for a frontend to mplayer. It has the most intuitive UI of any of the media players I've checked out.

I personally don't understand why all of these 4 engines exist. I wish that they would all just get together under 1 project to make the perfect engine. I know that mplayer was often not included by default because of odd licensing and questionable legal distribution. But I have no idea why xine, vlc and gstreamer (esp gstreamer) all exist.

I personally though have never found a file that neither xine nor mplayer couldn't play (given proper codec installation).

I also laugh when people say linux can't handle multimedia, as I've yet to see any it can't handle (save drm-ed files and corrupted ones). The problem isn't the ability to play the media it's lack of good frontends. Amarok 1.4.x has the best ui for a music player, imho, but ui for video I find is often lacking. It's often silly things such as advancing through the video with arrow keys or mouse wheel that are unintuitive. only 2 ui's that I can think of support 'open directory' and neither are recursive (kaffeine and smplayer).

---

### Post by rvm4000 on 2008-10-29
> **xenoterracide said:**
> only 2 ui's that I can think of support 'open directory' and neither are recursive (kaffeine and smplayer).

SMPlayer can load files to the playlist from a directory recursively.

---

### Post by xenoterracide on 2008-10-29
> **rvm4000 said:**
> SMPlayer can load files to the playlist from a directory recursively.

how? I just tested smplayer 0.6.4 by going to Open > Directory and it only opens the files in the directory that I'm in, not in the directories below it.

---

### Post by rvm4000 on 2008-10-29
Click on the preferences button in the playlist and check the option "Add files in directories recursively".

---

### Post by xenoterracide on 2008-10-29
> **rvm4000 said:**
> Click on the preferences button in the playlist and check the option "Add files in directories recursively".

hey thanks... smplayer still isn't perfect but it's the best there is for video currently, imho.

---

