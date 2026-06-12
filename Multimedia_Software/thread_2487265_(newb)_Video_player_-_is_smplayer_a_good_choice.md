---
title: "(newb) Video player - is smplayer a good choice?"
date: 2023-05-29
forum: Multimedia Software
---

### Post by nowindows2 on 2023-05-29
I've installed Gimp for images, but need a simple, basic program that will play mp4 video clips - no editing, no dvds, and definitely no Youtube. 

The two programs most often mentioned are vlc and smplayer. I'm a Linux newb and don't want to download programs based on Internet opinions, so came here to verify smplayer is a trusted program. Is there a better choice? Thanks for your time!

---

### Post by ajgreeny on 2023-05-29
The two applications you mention, ie, VLC and smplayer are both great and personally I see no reason to look elsewhere.

I use VLC for just about all my videos but seldom for audio, when I move to using audacious, a small fast player of all the audio file-types I possess.

---

### Post by SeijiSensei on 2023-05-29
smplayer was originally designed for people like me who watch a lot of subtitled content. It's been my player of choice for a decade. 

smplayer itself is really just a front end for media players like mpv and the older mplayer. mpv's user interface is pretty limited; smplayer makes it work like it should.

```
sudo apt install smplayer mpv
```

---

### Post by Holger_Gehrke on 2023-05-29
smplayer is a frontend for mplayer or mpv. Both of these are very capable players that have almost no user interface - you just get a window with the video and control the player through the keyboard; the keys are given in the manual pages. I personally just use mpv without smplayer. The difference between mplayer and mpv is that the latter is - at least currently - the more active project and has support for hardware accelerated video playback.

Holger

---

### Post by Dennis N on 2023-05-29
You want basic, so if you are using Ubuntu, the "official" player is Videos. It's basic. It should be installed by default unless you chose minimal install option.

---

### Post by TheFu on 2023-05-29
> **Holger_Gehrke said:**
> smplayer is a frontend for mplayer or mpv. Both of these are very capable players that have almost no user interface - you just get a window with the video and control the player through the keyboard; the keys are given in the manual pages. I personally just use mpv without smplayer. The difference between mplayer and mpv is that the latter is - at least currently - the more active project and has support for hardware accelerated video playback.

Holger

I use **mpv** for almost all playback, but use **mplayer** for some things that mpv doesn't/won't do that aren't directly "playback" needs and the mpv project doesn't seem interested in providing.

Once you are used to mpv keyboard controls, a GUI just isn't needed.
I use VLC on android, since it can play pretty much anything. I find it too bloated on desktop Linux, however.  If it takes half a second to open without any media on my system, it is bloated and I want to avoid it.  Personal issue, no doubt.

---

### Post by nowindows2 on 2023-05-29
I didn't evn know there was an Mplayer - I ony saw SMplayer.

Anyway - thanks to all who answered and pointed me in the right direction. I'll start researching Mplayer, SMplayer and MPV.

Might take a while tho - here's my frst search result:


[LIST]
[*]*SMPlayer is a cross-platform graphical front-end for MPlayer and mpv[6] and forks of Mplayer using GUI widgets offered by Qt. *
[/LIST]
 
That explanation is clear - clear as mud!! :)

Thanks again!

---

### Post by mIk3_08 on 2023-05-29
For me, I find vlc enough for my desktop system. vlc can provide almost anything what I need in terms of multimedia needs. That is my opinion. 
I also use Totem sometimes its so comfortable when using it. Regards and cheers.

---

### Post by TheFu on 2023-05-30
> **nowindows2 said:**
> 
[LIST]
[*]*SMPlayer is a cross-platform graphical front-end for MPlayer and mpv[6] and forks of Mplayer using GUI widgets offered by Qt. *
[/LIST]
 
That explanation is clear - clear as mud!! :)


While it is clear to me, it isn't clear to everyone.  Think like a programmer, who probably wrote that to be concise.
GUI = Graphical User Interface.  This means a window with buttons.  Ubuntu Desktop installs are GUIs.  Gnome, KDE, XFCE, Mate ... and nearly any program you use is a GUI.
There are TUIs (Text User Interface). Aptitude is an example. There are many others, but these tend to happen less and less.  When we install Ubuntu Server, the installation is a TUI (not a GUI). and 
CLI (command line interface) methods as well.  mplayer and mpv are CLI tools.  ls, mv, cp, bash, are all CLI tools.

Let's consider text editors.  nano and vim have TUI interfaces.  Gedit, Kate, Geany have GUI interfaces.

In Unix systems it is extremely common for the CLI version of X to be created first.  That's because it is easier to automate and usually 1/10th the bloat of a GUI version.

Some more examples
[LIST]
[*]CLI: rsync   GUI: grsync
[*]CLI: ufw   GUI: gufw
[*]CLI: mpv/mplayer   GUI: smplayer
[/LIST]

Is that clearer?

One more thing ... CLI is also called "shell interface".  That's because CLI tools are run from a shell (like bash, sh, csh, tcsh, zsh, psch, .... )

It may be too soon for you and 95% of the time, you don't need to know the command line, if you don't want to, but 80% of the power with Unix systems comes from mastering the CLI/shell.  If you ever want to run a Linux server, you'll need to know some about the CLI.  Here's a no-hassle download, book, that teaches Linux from the CLI perspective.  All of it will work on your desktop, BTW.  [https://www.linuxcommand.org/tlcl.php](https://www.linuxcommand.org/tlcl.php)  You can buy the book from almost any bookseller too.  

I'd start with some free stuff first, [https://ubuntu.com/tutorials/command-line-for-beginners](https://ubuntu.com/tutorials/command-line-for-beginners) 
and 
[https://www.howtogeek.com/412055/37-important-linux-commands-you-should-know/](https://www.howtogeek.com/412055/37-important-linux-commands-you-should-know/)    Lastly, there's almost no reason to ever use **cat**.  Every tool that people show with their example using **cat** will directly read the file itself. No **cat** needed.  I disagree with the order he chose.  He uses commands BEFORE they've been introduced.  That's why the first link at linuxcommand.org is important.  Stuff is introduced in the order needed, building knowledge. Things that haven't been covered already aren't used.

Don't fear the shell. That's where all the power is.

---

