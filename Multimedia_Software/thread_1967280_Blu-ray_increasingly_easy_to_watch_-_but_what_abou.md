---
title: "Blu-ray increasingly easy to watch - but what about bd+?"
date: 2012-04-28
forum: Multimedia Software
---

### Post by ubuntukid on 2012-04-28
I just installed precise and decided to see how easy it would be to playback a blu-ray disc. I was actually surprised by just how easy it was. All I had to do was 

1) install VLC
2) download the KEYDB.cfg file from [http://vlc-bluray.whoknowsmy.name/](http://vlc-bluray.whoknowsmy.name/)
3) place the KEYDB.cfg file in ~/.config/aacs/
4) load the blu-ray in vlc, making sure to chech the no menue checkbox as VLC will most likely choke on menues
5) enjoy your blu-ray (unless it is protected by bd+).

This worked great on my computer. The only downside is that this only works with discs that only use aacs encryption. Any disc with BD+ will choke, and here comes my question. Is there anyway of watching a BD+ encrypted disc using VLC without having to rip the movie first? Is there a libbdplus library being worked on?

For those watching blu-rays in vlc, bear in mind that you need to update the KEYDB.cfg file on a regular basis for it to be compatible with your newest discs. The current KEYDB.cfg file is only about a week old, so the site seems to be up to date. I tested it on two of my discs (2001 and total recall) and both worked well.

---

### Post by ubuntukid on 2012-04-28
Well I seem to have found the answer to my question already. I thought I'd post it for others to see. On the VLC forum there is a post which basically says that the bd+ encryption problem is currently not solvable. I guess I'll just have to enjoy my bd+-free movies for the time beeing.

[http://forum.videolan.org/viewtopic.php?f=14&t=100453](http://forum.videolan.org/viewtopic.php?f=14&t=100453)

---

### Post by andrew.46 on 2012-04-28
Thanks for the notification that there was a new KEYDB.cfg file available, an important warning is that is still a somewhat grey legal area (although I have no issue with being able to play the bluray titles I have purchased on my Linux computer!). You be interested to know that makemkv can [access many bd+ blurays]("http://www.makemkv.com/svq/") and has an option to *stream *the movie for either vlc or MPlayer to pick up. Also an option to dump the movie to HDD if you wish...

---

### Post by Gernott on 2012-05-21
Hi,
i use Mythbuntu 12.04 and the way you describe for bluray dosnt work.
The folder aacs dosnt exist on my system. so i created it. but im not sure the file ist loaded.
VLC was already installed in version 2.0.1

The Errormessage in VLC is:
Blu-Ray Fehler:
Path doesn't appear to be a bluray
Ihre Eingabe konnte nicht geöffnet werden:
VLC kann die MRL "bluray:///dev/dvd #5" nicht öffnen. Sehen Sie für Details im Fehlerprotokoll nach.

My translation to English:
Blu-Ray Error:
Path doesn't appear to be a bluray
Your input could not be opened:
VLC could not open MRL "bluray:///dev/dvd #5". For Details see Errorlog.

Do you have any hint for me?
Thank you

---

