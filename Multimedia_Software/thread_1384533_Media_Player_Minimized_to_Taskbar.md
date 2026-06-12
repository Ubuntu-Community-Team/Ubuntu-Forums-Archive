---
title: "Media Player Minimized to Taskbar?"
date: 2010-01-18
forum: Multimedia Software
---

### Post by manditajayne on 2010-01-18
Hi, I'm a recent Linux convert, mainly because a nasty virus ate up my Windows programs.  Even if I do get around to fixing Windows, I won't go back though, I'm loving Ubuntu so far :)

One thing though, I'm really picky about my music player.  Just a couple months ago, I switched to Media Monkey and loved it.  Now I'm back to square one.  As far as ones with good organizing ability, people are recommending Exaile (which is what I'm currently using), Amarok (which won't play my files for me), Rhythmbox (which didn't really impress me, no particular reason, I think it froze once and I decided once was enough), and two I haven't tried yet: Banshee and Songbird.  Does anyone know if any of these can handle one silly little feature that I really, really miss:

Being able to minimize it to the taskbar.  Windows Media Player did this, and I figured out how to do it in Media Monkey too.  Just when you minimize, it goes into super mini-mode next to the icon bar, and all you get is play/pause/stop/next/back, and it displayed the song title too.  And you could get more info when you hovered over it.  It was a nifty little feature, I really liked being able to see the song title and skip quickly without having to right click on the icon or re-open the player or whatever.  So, can anything do that in Ubuntu?

Thanks everyone!

---

### Post by jerrrys on 2010-01-18
[attach]144080[/attach]

---

### Post by manditajayne on 2010-01-19
Thanks for the idea, but does VLC have decent organizational abilities?  I've used it in windows, and wasn't impressed on that end of things, but I don't know if it's different, perhaps it can organize and do playlists better and everything with this skin you've got going on?

I tried out Banshee last night and really love it, as far as the interface and playlists and how everything works.  So if anyone has a solution for Banshee, that would be ideal :)  Maybe I'm asking too much, but Media Monkey did everything I wanted and more, so now I've been spoiled!!

---

### Post by boombox1387 on 2010-01-21
Glad you like Banshee!  I think we can make it work for you :)

There's a program called Music Applet that I can't find in the Software Center, but it's in Synaptic.  If you install that, it will give you a panel applet that allows you to control the media player of your choice.

Really, though Music Applet has been replaced by Panflute (the same programmer is behind both projects; Panflute is newer).  While Panflute isn't available in the Software Center, it might be worth the hassle to install, because it's pretty cool.

[LIST=1]
[*]Open up System > Administration > Software Sources
[*]Click the 'Other Software' tab at the top
[*]Click the 'Add' button
[*]Paste 'ppa:kuliniew/ppa' into the box (no quotes) and click 'Add Source'
[*]Click Close, it should ask you to reload the sources and you should say yes
[*]Open System > Administration > Synaptic Package Manager
[*]Search panflute and check 'panflute-applet' and 'panflute-daemon'
[*]Click 'Apply' to install, then close Synaptic
[*]Right click on your Gnome Panel, choose 'Add to Panel'
[*]Find 'Panflute Applet' and click 'Add'
[*]You should see a new panel applet.  You can right click on this applet and choose 'Preferences' to make changes (and set Banshee as the default player
[/LIST]

This will let you see playback controls, now playing information, and a lot of other stuff all in your panel.  Banshee won't exactly minimize here, but if you click the close button, Banshee will keep running in the Notification Area, so the effect is the same.

Banshee also has a Mini-Mode extension, but I haven't used it much.  You can find it in Banshee's preferences under the 'Extensions' tab.

Good luck and let me know if you run into any troubles.

---

### Post by boombox1387 on 2010-01-21
I should also explain what my instructions are telling you to do in case you aren't familiar with this process.

  The important piece is adding 'ppa:kuliniew/ppa' to your software sources.  This is a third party Personal Package Archive.  It allows developers to release and update software without using the Software Center.  If you don't have this PPA in your software sources, you won't be able to find the panflute packages in Synaptic (which manages all of the packages available for you to download and install).

---

### Post by opethfan89 on 2010-02-06
boombox1387,
Thanks SO MUCH for posting those directions! I stumbled across this thread while trying to learn how to install a tarball, and trying to install Panflute the hard way. I used to use Music Applet back in Fedora 11 and I missed it when I moved over to ubuntu 9.10. Thanks again for these instructions. I'm slowly compiling a list of all the customizations I have to do to get Ubuntu the way I like it, and this adds onto the list. Thanks!

---

### Post by boombox1387 on 2010-02-07
> **opethfan89 said:**
> boombox1387,
Thanks SO MUCH for posting those directions! I stumbled across this thread while trying to learn how to install a tarball, and trying to install Panflute the hard way. I used to use Music Applet back in Fedora 11 and I missed it when I moved over to ubuntu 9.10. Thanks again for these instructions. I'm slowly compiling a list of all the customizations I have to do to get Ubuntu the way I like it, and this adds onto the list. Thanks!

Glad it helped!  (And glad I could help you dodge installing things from tarballs!)

---

### Post by kedmond on 2010-05-05
Hey, thanks for the instructions.  I got the Panflute applet to show up in my tray with Ubuntu 10.04.  However, I cannot get it to work with Songbird.  Beyond selecting Songbird from the menu in Panflute's preferences, I'm not sure what to do.  I'm using Songbird 1.4.3.  Thanks.

Edit: By the way, typing "songbird" into the command-line doesn't launch Songbird for me.  It's located in /opt/songbird/

---

