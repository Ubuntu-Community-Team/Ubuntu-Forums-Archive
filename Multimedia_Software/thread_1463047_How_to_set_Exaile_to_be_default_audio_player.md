---
title: "How to set Exaile to be default audio player?"
date: 2010-04-26
forum: Multimedia Software
---

### Post by BeRA on 2010-04-26
I've tried everything... first I tried with Preferences/Preferred Applications - no result... then File Type Manager from Ubuntu Tweek - nothing... I tried with a few older Exaile versions (from various repo's) - nothing... compiling 0.3.1.1 from source - still nothing :( ... with these I can set every other player to be default player (so, only Exaile refuses to obey)... hmmm to be more exact, after setting Exaile as default, double-click on any audio file associated with it results with temporary CPU usage increase and than NOTHING :S

PS. Please, just don't tell me to use VLC, Audacious, Rhythmbox, Amarok, QL or any other player... I used them all but I NEED Exaile :) (and not just because it looks beautiful enough with Ambiance to make me completely forget foobar2k... and because it's sooo stubborn :) ).

---

### Post by WinterRain on 2010-04-26
Open your home folder and go to edit>preferences>media tab and change it there.

---

### Post by BeRA on 2010-04-26
> **WinterRain said:**
> Open your home folder and go to edit>preferences>media tab and change it there.
Thanks, but I tried that one also... also results with temporary CPU usage increase and than NOTHING :S (right click- open with Exaile also doesn't work)

Hmmm maybe I wasn't clear enough... I can set it to be default player easily, but there is no effect (so it isn't default player- or it is, but only in theory :) )... Exaile stubbornly refuses to open and play the file (I have to "manually" open Exaile and then add song I want it to play)

I really don't know what could be the problem... :confused:

---

### Post by Yellow Pasque on 2010-04-26
Open nautilus in the terminal and then try to play a music file. Maybe it will give an error message when exaile doesn't start.

---

### Post by BeRA on 2010-04-26
> **Temüjin said:**
> Open nautilus in the terminal and then try to play a music file. Maybe it will give an error message when exaile doesn't start.

Good idea... this is what happens when I try to browse (It opens nautilus window, but what is this error?- apart from this error everything is OK- double-click still does nothing- no trace of it anywhere- just like I never clicked):
> berin@berin-laptop:~$ alias browse='nautilus'
berin@berin-laptop:~$ . ~/.bashrc
berin@berin-laptop:~$ browse .

(nautilus:8459): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
berin@berin-laptop:~$

But Exaile starts just as it should from terminal... This is what I get when I try to play any file from terminal (Exaile window opens normally and everything works just fine):

> berin@berin-laptop:~/Music$ exaile Toto_-_2_Hearts.mp3
INFO    : Loading Exaile 0.3.1.0...
INFO    : Loading settings...
INFO    : Setting up deferred idle manager function...
INFO    : Loading plugins...
INFO    : Loading collection...
INFO    : Loading devices...
INFO    : Loading interface...
INFO    : HAL Providers: [<cd.CDHandler object at 0x8df068c>]
INFO    : Loading main window...
INFO    : Connecting main window events...
INFO    : Loading panels...
INFO    : Connecting panel events...
INFO    : Done loading main window...
INFO    : Playing file:///home/berin/Music/Toto_-_2_Hearts.mp3
Traceback (most recent call last):
  File "/usr/lib/exaile/xl/event.py", line 451, in emit
    event.data, *cb.args, **cb.kwargs)
  File "/usr/share/exaile/plugins/minimode/__init__.py", line 38, in _enable
    MINIMODE = MiniMode(exaile)
  File "/usr/share/exaile/plugins/minimode/__init__.py", line 88, in __init__
    self.update_widgets(controls)
  File "/usr/share/exaile/plugins/minimode/__init__.py", line 244, in update_widgets
    self.box.update_widgets(ids)
  File "/usr/share/exaile/plugins/minimode/mmwidgets.py", line 139, in update_widgets
    self.add_widget(id)
  File "/usr/share/exaile/plugins/minimode/mmwidgets.py", line 108, in add_widget
    widget = type(*arguments)
  File "/usr/share/exaile/plugins/minimode/mmwidgets.py", line 575, in __init__
    self.update_track_list(self.queue.current_playlist)
  File "/usr/share/exaile/plugins/minimode/mmwidgets.py", line 630, in update_track_list
    iter = self.list.append([track, self.formatter.format(track)])
  File "/usr/share/exaile/plugins/minimode/mmwidgets.py", line 1016, in format
    substitutions[keyword] = format_callback(substitutions[keyword])
  File "/usr/share/exaile/plugins/minimode/mmwidgets.py", line 1043, in __format_length
    length = float(length)
ValueError: invalid literal for float(): Unknown
INFO    : Playing file:///home/berin/Music/music/mjuza/Red%20Hott%20Chillie%20Peppers%20-%20City%20Of%20angles.mp3
INFO    : Playing file:///home/berin/Music/new/Franz%20Ferdinand%20-%20Lucid%20Dreams.mp3



really weird :confused: (maybe it will help if I say that double-click works only and only for .ogg files (and not for .FLAC and .mp3- and almost everything I have is in .FLAC)) :confused:

---

### Post by fonsi2099 on 2010-05-12
why my Exaile do not start by 10.04? 

here the output of terminal:
---laptop:~$ exaile
INFO    : Loading Exaile 0.3.1.1...
INFO    : Loading settings...
INFO    : Setting up deferred idle manager function...
INFO    : Loading plugins...
INFO    : Loading collection...
INFO    : Loading devices...
Traceback (most recent call last):
  File "/usr/lib/exaile/exaile.py", line 52, in <module>
    main()
  File "/usr/lib/exaile/exaile.py", line 49, in main
    exaile = main.Exaile()
  File "/usr/lib/exaile/xl/main.py", line 84, in __init__
    self.__init()
  File "/usr/lib/exaile/xl/main.py", line 189, in __init
    location=os.path.join(xdg.get_data_dirs()[0], "covers"))
  File "/usr/lib/exaile/xl/cover.py", line 121, in __init__
    self.load()
  File "/usr/lib/exaile/xl/cover.py", line 330, in load
    data = pickle.load(f)
EOFError

any Idea how can I fix that
Thank you!

ubuntu 10.04 Athlon 64B

---

### Post by wmeler on 2011-04-10
I realize this post is old, but I didn't see a solution.  Moreover, I see two different problems mentioned above.  Hope one of these two helps someone out there:

PROBLEM #1)To the initial problem (less ugly):
[http://ubuntuforums.org/showthread.php?t=1726014](http://ubuntuforums.org/showthread.php?t=1726014)

PROBLEM #2)To the uglier problems listed later in this thread...
I have had a similar problem, and am hoping others in the future who stumble on this post will benefit from a post I made elsewhere:

[http://www.linuxquestions.org/questions/linux-software-2/exaile-suddenly-not-working-873425/](http://www.linuxquestions.org/questions/linux-software-2/exaile-suddenly-not-working-873425/)


***
  See the bottom where I have put links to a number of (seemingly) related bugs!

---

