---
title: "WisRemote: Python script for controlling wis-streamer (go7007 driver tv tuners)"
date: 2007-11-02
forum: Multimedia &amp; Video
---

### Post by unai_goiko on 2007-11-02
Hello!

So you have a Tv tuner on your GNU/Linux computer that uses the go7007 Linux Driver and can’t watch any live TV because no GNU/Linux program really supports it? Yeah right… it is supposed to work with MythTV but it doesn’t or it’s just so hard to set it up…

Well that’s what happened to me until now that I’ve decided to make my own python script that works along with some other programs to be able to watch live TV easily on my gnome desktop.

That’s what WisRemote 1.0 is about. Basically it’s a python script that eases the use of another nice program called wis-streamer that streams your go7007’s tv video directly to your network.

After an easy configuration, in which we configure WisRemote to watch our local channels, we will be able to watch live TV right from a go7007 device connected to our local computer or to a remote computer thanks to the magic of ssh and python.

By default, WisRemote has been designed to be launched from the command line, so if you tell it to stream a certain channel, you will them have to open vlc or mplayer to watch the video stream. In order to facilitate this, I have included an extra option thanks to which it’s possible to control every single action from gnome’s tray.

More info at my website:
[http://www.goikoetxeta.com/archivos/03-11-2007/wisremote-10/]("http://www.goikoetxeta.com/archivos/03-11-2007/wisremote-10/")

---

