---
title: "XINE (?) + MP3 problem"
date: 2006-11-01
forum: Multimedia &amp; Video
---

### Post by Rede on 2006-11-01
My roommate made the switch from Windows to Kubuntu Edgy on his laptop this weekend. (YAY!) Everything went fine... until today when MP3s seemed to have stopped working. Apparently when he went to bed yesterday everything was fine, but when he woke up Amarok wouldn't play MP3s. Amarok just popped up a message box that asked if he wanted to get MP3 support for Amarok, but clicking yes had no effect. 

Upon inspection I found that Kaffeine also failed to play MP3s, as did KMPlayer... until I switched the engine from XINE to MPLAYER. MP3s play properly with KMPlayer using the MPLAYER plugin, play as would be expected with mplayer from the command line, and XMMS also plays MP3s perfectly. The problem appears to be with XINE.

I attempted to install libxine-extracodecs, but it was already installed. So I removed it and loaded Amarok, which downloaded and reinstalled the libxine-extracodecs package... but the problem persisted after reloading Amarok. It still reports that it is unable to play MP3 files and asks if I'd like to download the codecs, but clicking yes has no effect. I tried removing the package, deleting apt's cached download, and reinstalling the libxine-extracodecs package (again) but it didn't help.


I'm pretty much at a loss here. If anyone has any idea where the problem might be, I'd appreciate the help.

---

### Post by twidget on 2006-11-01
I'm having the same problem in Dapper with pretty much the same symptoms. I've also tried uninstalling and reinstalling everything. in kaffeine when i click on details as to why the program hates me i get the following messages:
xine: couldn't find demux for >/media/sde/001 Building A Mystery.mp3<
xine: found input plugin  : file input plugin
do you get the same?

---

### Post by Rede on 2006-11-02
> **twidget said:**
> I'm having the same problem in Dapper with pretty much the same symptoms. I've also tried uninstalling and reinstalling everything. in kaffeine when i click on details as to why the program hates me i get the following messages:
xine: couldn't find demux for >/media/sde/001 Building A Mystery.mp3<
xine: found input plugin  : file input plugin
do you get the same?

Yes, thats the same error message displayed by Kaffeine here. :(

It make so little sense... ](*,)

---

### Post by twidget on 2006-11-03
bump tried whiping everything media related still doesnt work. i think adept doesnt actualy re download files if you uninstall and then re install. it skips to installation to fast for it to be downloading anything.. so to do a reinstall i think we need to find out where these files are stored and then how to remove them maybe.

---

### Post by Rede on 2006-11-06
> **twidget said:**
> bump tried whiping everything media related still doesnt work. i think adept doesnt actualy re download files if you uninstall and then re install. it skips to installation to fast for it to be downloading anything.. so to do a reinstall i think we need to find out where these files are stored and then how to remove them maybe.

I've already done this. It has no more of an effect than not removing and re-downloading them.

---

### Post by Rede on 2006-11-12
Found a solution...

I completely emptied the playlist in Amarok and closed the application. I then opened a MP3 file in Amarok from Konqueror, and MP3s now play as expected in Amarok and Kaffeine.

---

