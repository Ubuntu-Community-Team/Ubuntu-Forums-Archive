---
title: "Exaile doesn't start!!!"
date: 2010-05-17
forum: Multimedia Software
---

### Post by Malfet on 2010-05-17
Just yesterday Exaile was working fine, today it doesn't start. It shows splash screen on the start and that's all. Also, I do not see Exaile among active processes. Re-installation of Exaile from Synaptic did not help.

Here is the console outcome

INFO : Loading Exaile 0.3.1.1...
INFO : Loading settings...
INFO : Setting up deferred idle manager function...
INFO : Loading plugins...
INFO : Loading collection...
INFO : Loading devices...
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

Exaile 0.3.1.1
Ubuntu 10.04

Please, HELP!

---

### Post by addiebk on 2010-06-07
I've the same problem here.

```
INFO    : Loading Exaile 0.3.1.1...
INFO    : Loading settings...
INFO    : Setting up deferred idle manager function...
INFO    : Loading plugins...
INFO    : Attempting to connect to AudioScrobbler (http://post.audioscrobbler.com/)
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
```

---

### Post by lidex on 2010-06-07
Mine works. Here is output:
```
INFO    : Loading Exaile 0.3.1.1...
INFO    : Loading settings...
INFO    : Setting up deferred idle manager function...
INFO    : Loading plugins...
INFO    : Loading collection...
INFO    : Loading devices...
INFO    : Loading interface...
INFO    : HAL Providers: [<cd.CDHandler object at 0x366e450>]
INFO    : Loading main window...
INFO    : Connecting main window events...
INFO    : Loading panels...
INFO    : Connecting panel events...
INFO    : Done loading main window...
INFO    : Playing file:///home/lidex/Public/U2%
```

---

### Post by addiebk on 2010-06-08
After hunting around a bit, I found this:

[https://bugs.launchpad.net/exaile/+bug/469816](https://bugs.launchpad.net/exaile/+bug/469816)

Which led me to delete all of the files in ~/.local/share/exaile/ and re-install Exaile.  After this, Exaile has worked perfectly for me, though I did lose my playlists.

---

### Post by anieruddha on 2010-06-30
I had the same problem. 
1. I remove the exaile
2. Install (sudo apt-get install exaile)
3. Copied /root/.local/share/exaile to user home/.local/share/exaile
4. change permission to 777
chmod -R 777 /home/aniruddha/.local/share/exaile
5. Copied /root/.config/exaile to user home/.config/exaile
6. change permission to 777
chmod -R 777 /home/aniruddha/.config/exaile

instead of changing permission, changing ownership will do.

This solution worked for me.

---

### Post by wmeler on 2011-04-10
Here's what I did to solve this.  I'm guessing somebody already posted something similar, but I thought I'd post this just in case it helps someone else.  Not pretty, but it works:

[http://www.linuxquestions.org/questions/linux-software-2/exaile-suddenly-not-working-873425/](http://www.linuxquestions.org/questions/linux-software-2/exaile-suddenly-not-working-873425/)

As for the covers you lose...there is a Cover Manager that if you Start it, downloads away.  So no real issue there.

Also, see links at bottom to known bugs that I believe are directly related.

---

