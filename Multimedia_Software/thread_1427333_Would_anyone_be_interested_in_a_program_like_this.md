---
title: "Would anyone be interested in a program like this?"
date: 2010-03-11
forum: Multimedia Software
---

### Post by derrick81787 on 2010-03-11
Hello everyone,

I've been working a program in my spare time and just today released the second version of it.  It's a program that allows one computer to browse videos that are on another computer and then control video playback on that computer.  The way I use it is I use my netbook as basically a remote control to browse through my videos and then play the selected video on my other computer that is connected to my television.

I'm eventually wanting to get it included in the Ubuntu (or Debian) repositories, after I make some improvements and learn to package it so that it meets the requirements to get included.

The reason I'm posting this is because I was wondering if people would be interested in such a program.  Right now, I'm the only one I know of who is using it.  Launchpad lists a small number of downloads, but they may or may not have been from me (I don't remember).  I don't mean to seem like I'm advertising my own program here on the forums, I'm just hoping to help out the community with my program, and I figure this is a good place to ask for feedback.

The links to the program's homepage and Launchpad page are:
[Homepage]("http://derrickwright.info/juketv")
[Launchpad Page]("https://launchpad.net/juketv")

Thanks,
Derrick

**P.S.**
Sorry for the lack of screenshots.  I'll try and get those up there sometime soon.

---

### Post by lovinglinux on 2010-03-11
Thanks for sharing. I'm sure a lot of people will be interested.

---

### Post by 2hot6ft2 on 2010-03-11
Sounds like something my Brother and myself might be interested in. He's not really technically inclined so mythbuntu and XBMC are a little over his head. A simple interface would be good for him (like browse to file and play, pause, stop), while I like more advanced features.

Screenshots would be a plus.

Keep us posted and thanks for your efforts. I'm sure that others will be interested as well.

---

### Post by derrick81787 on 2010-03-11
> **2hot6ft2 said:**
> Sounds like something my Brother and myself might be interested in. He's not really technically inclined so mythbuntu and XBMC are a little over his head. A simple interface would be good for him (like browse to file and play, pause, stop), while I like more advanced features.

Screenshots would be a plus.

Keep us posted and thanks for your efforts. I'm sure that others will be interested as well.

I'm not at home right now, but I'll try and post screenshots tonight.  I had meant to do them earlier on, but the GUI was still changing and I didn't want to post them yet.  The look of the GUI is basically set now, but I've just been too lazy to get around to posting them, I guess.

If you or anyone else on the forum wants to give it a try or have any questions/suggestions, feel free to send me a message or post something here.

- Derrick

---

### Post by doas777 on 2010-03-11
sounds great! I do somthing similar with remote desktop, but i have to close as soon as the video starts playing, or it lags both machines trying to show hd video over a vnc session at the same time it is on the screen.

---

### Post by JAY6390 on 2010-03-11
Sounds like an excellent application. I would really like to have this (once you've gotten it to a level you're happy with) :)

---

### Post by doas777 on 2010-03-11
I have to assume you tie into a specific media player, right? or could I switch from smplayer to vlc to totem on demand?

---

### Post by derrick81787 on 2010-03-11
> **JAY6390 said:**
> Sounds like an excellent application. I would really like to have this (once you've gotten it to a level you're happy with) :)

It's pretty usable right now.  There are definitely some improvements that could be made, but nothing too major.  For instance, if you connect to the server, then put your laptop to sleep or do something that disconnects it from the network while you are watching the video, I think you might lose the connection.  I need to add some code to reconnect if something like that happens.

Other than that, my other big change that I want to make is to add a preferences dialog that edits the configuration file for you.  Right now, you have to edit it by hand, but it's pretty simple and well commented.

These two improvements would help a lot.  Other changes that I want to make are big things like make my own video player, try and integrate Hulu and YouTube, etc.

If you want to give it a try, go ahead and download version 0.2.  I think it's pretty usable, and I could definitely use some testers.  Even if it crashes or something, the client isn't doing anything other than communicating over the network, and the server is basically just listening and launching Totem, so it shouldn't cause any harm to your system or anything like that.

The only potential security issue I can think of is that the play, pause, skip, etc. commands that the server runs are specified in the configuration file and can be changed.  I need to think of something to do about that.

- Derrick

---

### Post by 2hot6ft2 on 2010-03-11
> **derrick81787 said:**
> I'm not at home right now, but I'll try and post screenshots tonight.  I had meant to do them earlier on, but the GUI was still changing and I didn't want to post them yet.  The look of the GUI is basically set now, but I've just been too lazy to get around to posting them, I guess.

If you or anyone else on the forum wants to give it a try or have any questions/suggestions, feel free to send me a message or post something here.

- Derrick
Sounds good. I was looking thru the pages for it. I'm sure others will want to know so I'll ask. What protocol are you using on the server (security method), I guess that's the right way of asking? Since I run SSH and FreeNX I like things to be nice and secure.
Obviously this would only need to be accessed from the LAN. That can always be set with firewall rules to only allow LAN or specific IP Addresses to connect at that port.

I would like to see VLC as a player option. (food for thought, my player of choice).
Since I haven't seen the interface yet:
Just a simple control interface on the client perhaps using a firefox plugin (I'm thinking of the fox-tv plugins simplistic features) that can be found here: [http://addons.mozilla.org/en-US/firefox/addon/11200](http://addons.mozilla.org/en-US/firefox/addon/11200)
All it has in the player is a play/pause/minimize/fullscreen
When minimized it's just a small title bar. I'll post a screenshot so you can see what I mean.
Then firefox could be pointed to the server to control it and be bookmarked for later use.

None of these are must haves other than the security. I'm just throwing some ideas out there that you may or may not have considered so you have more ideas and options to play with.

I'll wait to see what you have since it's probably a lot better.

---

### Post by derrick81787 on 2010-03-11
> **doas777 said:**
> I have to assume you tie into a specific media player, right? or could I switch from smplayer to vlc to totem on demand?

Actually, right now you can specify any media player you want.  Just take a look at the configuration file, or my page that explains it [here]("http://derrickwright.info/juketv/config").  I've tested it with Totem because it's installed by default and supports all the commands I use.  It should work with anything, though.

I eventually want to make my own media player that is better integrated (but still allow custom ones) but I'm not real sure how to do that.

- Derrick

---

### Post by doas777 on 2010-03-11
> **derrick81787 said:**
> Actually, right now you can specify any media player you want.  Just take a look at the configuration file, or my page that explains it [here]("http://derrickwright.info/juketv/config").  I've tested it with Totem because it's installed by default and supports all the commands I use.  It should work with anything, though.

I eventually want to make my own media player that is better integrated (but still allow custom ones) but I'm not real sure how to do that.

- Derrick
rock on dude. I'll be watching your project closely!

---

### Post by derrick81787 on 2010-03-11
> **2hot6ft2 said:**
> I'm sure others will want to know so I'll ask. What protocol are you using on the server (security method), I guess that's the right way of asking? Since I run SSH and FreeNX I like things to be nice and secure.

Well, right now I don't really have any security for the network protocol.  I figure it's really meant to be run behind a firewall, since the person running the client has to be in the same room as the server in order to see the video playing.  The way it works is the client sends generic commands like "Play," "Pause," etc. in plain XML over the network.  The server then takes the command, say it's a "Play" command, checks the configuration file to see what the actual system command for play is, in the case of the example i linked to, the command is **totem --fullscreen *filename*** and then runs that command.

So, even though there's no security, it doesn't just take OS commands from over the network and then run them.  The worst that I would think would happen if someone connects to your server is that they could play, pause, stop, etc. your video.

> **2hot6ft2 said:**
> I would like to see VLC as a player option. (food for thought, my player of choice)

That is configurable.  The relevant section of the configuration file is this:
```
<!-- A list of commands for handling video playback and control.  Right
      now, JukeTV Server only suppors the "custom" player, but predefined
      players will hopefully be coming in future releases. -->
      <playback player='custom'>
         <commands>
            <play>totem --fullscreen '%f'</play>
            <pause>totem --pause</pause>
            <resume>totem --play</resume>
            <skip-fwd>totem --seek-fwd</skip-fwd>
            <skip-bwd>totem --seek-bwd</skip-bwd>
            <vol-up>totem --volume-up</vol-up>
            <vol-down>totem --volume-down</vol-down>
            <exit>totem --quit</exit>
         </commands>
      </playback>
```

> **2hot6ft2 said:**
> Since I haven't seen the interface yet:
Just a simple control interface on the client perhaps using a firefox plugin (I'm thinking of the fox-tv plugins simplistic features) that can be found here: [http://addons.mozilla.org/en-US/firefox/addon/11200](http://addons.mozilla.org/en-US/firefox/addon/11200)
All it has in the player is a play/pause/minimize/fullscreen
When minimized it's just a small title bar. I'll post a screenshot so you can see what I mean.

That is roughly the idea of the client interface.  It is written in GTK+.  At the top, it has play/pause, stop, skip fwd, skip bwd, volume up, and volume down.  The bottom is split into two panes.  At the left is a list of directories that contain your videos.  At the right is a listing of the files that are in the currently selected directory.  When you select one and hit play, it plays on the server, and the play button turns into a pause button.  The other buttons then control the playback.

I'll have to post screenshots tonight.  I didn't really think I'd get such a big response, but I'm glad I did.

- Derrick

---

### Post by 2hot6ft2 on 2010-03-11
I went back and looked at the script. Probably while you were typing your response and after reading the other post on the subject. It's sounding better all the time. There should be a smiley for drooling...

It's definitely something that people are interested in. If I knew how to do programming I would lend a hand but I'll have to leave that to those that are competent.
:guitar:

---

### Post by doas777 on 2010-03-11
I looked at the config file, which answers a lot of questions i would have had. 
in the libraries block, will it take an smb path for a rootdir?

---

### Post by derrick81787 on 2010-03-11
> **doas777 said:**
> I looked at the config file, which answers a lot of questions i would have had. 
in the libraries block, will it take an smb path for a rootdir?

Hummm... that's a good question.  I didn't explicitly code it to do anything like that.  To list the directory contents, it uses Python's os.listdir(dir) function.  To play the video, it just passes the path to Totem (VLC or whatever), so if those two things will work with smb paths, then this should too.

I know it will work if you mount the smb shares with CIFS or SMBFS or whatever that module is called.  I have my videos on one computer and have them mounted with NFS on a second computer that is hooked to my TV.  That second computer is the one that I use as the JukeTV Server, it works great with that setup.  As far as just passing smb://path to it goes, I really don't know.

- Derrick

*****Edit:**
We'll have to check and see if it works or not.  If it doesn't, I'll look into how to make that work in future versions.

---

### Post by derrick81787 on 2010-03-11
For those of you who want to see the client interface, I just added some screenshots to my original post.  I'll put them on the website soon, but I don't have time tonight.

- Derrick

---

### Post by 2hot6ft2 on 2010-03-11
> **derrick81787 said:**
> For those of you who want to see the client interface, I just added some screenshots to my original post.  I'll put them on the website soon, but I don't have time tonight.

- Derrick
I like it. Nice, clean and simple.

---

### Post by derrick81787 on 2010-04-08
I just figured that I would announce here that I have created Debian packages for version 0.2 to help with installation.  You can download them from either [Launchpad]("https://launchpad.net/juketv/+download"), or the [downloads page]("http://derrickwright.info/juketv/download") on my site (which links to Launchpad).

Also, I thought I would let you know that I am in the process of adding YouTube support to the server.  This means that it will be able to list the Most Viewed, Top Rated, etc. videos in YouTube as part of your video library and allow you to watch them as you would with any other video.  It will be some time off in the future, since I am busy with my last semester of school and all, but I already have a proof of concept that lists the videos from YouTube and prints their URL (and other stuff).  From there, it shouldn't be too much work to play the videos.  Look for it in version 0.3.  By then, I will hopefully set up a PPA as well.

- Derrick

*****Edit:**
There is a problem with the Debian packages.  I will fix it and then update this post.

---

### Post by derrick81787 on 2010-04-10
> **derrick81787 said:**
> I just figured that I would announce here that I have created Debian packages for version 0.2 to help with installation.  You can download them from either [Launchpad]("https://launchpad.net/juketv/+download"), or the [downloads page]("http://derrickwright.info/juketv/download") on my site (which links to Launchpad).

Also, I thought I would let you know that I am in the process of adding YouTube support to the server.  This means that it will be able to list the Most Viewed, Top Rated, etc. videos in YouTube as part of your video library and allow you to watch them as you would with any other video.  It will be some time off in the future, since I am busy with my last semester of school and all, but I already have a proof of concept that lists the videos from YouTube and prints their URL (and other stuff).  From there, it shouldn't be too much work to play the videos.  Look for it in version 0.3.  By then, I will hopefully set up a PPA as well.

- Derrick

*****Edit:**
There is a problem with the Debian packages.  I will fix it and then update this post.

So, there was a problem with the packages the first time around.  I went ahead and rebuilt the packages, so they should work fine now.  You can just remove the old ones with

```
sudo apt-get remove --purge juketv-client
```
for the client, or
```
sudo apt-get remove --purge juketv-server
```
for the server.

You can then install the new packages with
```
sudo dpkg -i <name of .deb file>
```
or by double-clicking in Nautilus and opening it in GDebi.

- Derrick

---

