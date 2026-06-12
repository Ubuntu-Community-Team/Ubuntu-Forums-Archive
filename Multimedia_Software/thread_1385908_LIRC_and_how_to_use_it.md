---
title: "LIRC and how to use it"
date: 2010-01-20
forum: Multimedia Software
---

### Post by joeb1990 on 2010-01-20
I can't seem to grasp the way lirc works. I downloaded and installed it and have a Windows MCE RC-6 remote plugged in and the receiver is responding but I cannot navigate with it. It does not work on my desktop or any of my programs. I have researched all of lirc's homepage and cannot find a place to begin. Thank you for your help. Using 9.10 64 Bit

---

### Post by sports.car.guy on 2010-01-20
> **joeb1990 said:**
> I can't seem to grasp the way lirc works. I downloaded and installed it and have a Windows MCE RC-6 remote plugged in and the receiver is responding but I cannot navigate with it. It does not work on my desktop or any of my programs. I have researched all of lirc's homepage and cannot find a place to begin. Thank you for your help. Using 9.10 64 Bit

Where to begin, I can help there. It is to create one config file for each application you plan on using. It doesn't just work with installation of Lirc and that is that. There needs to be something, a config file to tell Lirc when an application is running that you want it to do something. The way this is accomplished is by mapping the keyboard shortcuts to it to buttons on the remote, VLC is an exception to this. It can use keyboard shorcuts, but if you change them the remote needs to have it's config file changed to reflect it. VLC developers allow for using keyboard shortcuts but also provided standard names to refer by so no need to change the config file.

Gnome and Mythbuntu Control Centre both have Lirc configuration applications that could assist you by getting the right driver loaded and a base line configuration. I believe the Gnome application lets you create the bindings to the keybard through a GUI.

Here are two samples for you to look at from my .lirc folder each named to match the application.

VLC:
```

#Play----------------------------
begin
    remote = mceusb
    prog = vlc
    button = Play
    config = key-play
    repeat = 0
    delay = 0
end
#--------------------------------

#Pause---------------------------
begin
    remote = mceusb
    prog = vlc
    button = Pause
    config = key-play-pause
    repeat = 0
    delay = 0
end
#-------------------------------

#Stop---------------------------
begin
    remote = mceusb
    prog = vlc
    button = Stop
    config = key-quit
    repeat = 0
    delay = 0
end
#------------------------------

#Record (Normal Play Speed)----
    begin
        remote = mceusb
        prog = vlc
        button = Record
        config = key-rate-normal
        repeat = 0
        delay = 0
    end
#------------------------------

#Rewind------------------------
begin
    remote = mceusb
    prog = vlc
    button = Rewind
    config = key-slower
    repeat = 0
    delay = 0
end
#-----------------------------

#Foward-----------------------
begin
    remote = mceusb
    prog = vlc
    button = Forward
    config = key-faster
    repeat = 0
    delay = 0
end
#-----------------------------

#Replay-----------------------
begin
    remote = mceusb
    prog = vlc
    button = Replay
    config = key-jump-short
    repeat = 0
    delay = 0
end
#----------------------------

#Skip------------------------
begin
    remote = mceusb
    prog = vlc
    button = Skip
    config = key-jump+short
    repeat = 0
    delay = 0
end
#----------------------------

#Left------------------------
begin
    remote = mceusb
    prog = vlc
    button = Left
    config = key-jump-medium
    repeat = 0
    delay = 0
end
#---------------------------

#Right----------------------
begin
    remote = mceusb
    prog = vlc
    button = Right
    config = key-jump+medium
    repeat = 0
    delay = 0
end
#--------------------------

#Up------------------------
begin
    remote = mceusb
    prog = vlc
    button = Up
    config = key-jump+long
    repeat = 0
    delay = 0
end
#--------------------------

#Down----------------------
begin
    remote = mceusb
    prog = vlc
    button = Down
    config = key-jump-long
    repeat = 0
    delay = 0
end
#-------------------------

#Volume Up----------------
begin
    remote = mceusb
    prog = vlc
    button = VolUp
    config = key-vol-up
    repeat = 0
    delay = 0
end
#-------------------------

#Volume Down--------------
begin
    remote = mceusb
    prog = vlc
    button = VolDown
    config = key-vol-down
    repeat = 0
    delay = 0
end
#------------------------

#Mute--------------------
begin
    remote = mceusb
    prog = vlc
    button = Mute
    config = key-vol-mute
    repeat = 0
    delay = 0
end
#------------------------

#Chan Up (Audio Sync)----
begin
    remote = mceusb
    prog = vlc
    button = ChanUp
    config = key-audiodelay-up
    repeat = 0
    delay = 0
end
#------------------------

#Chan Down (Audio Sync)--
begin
    remote = mceusb
    prog = vlc
    button = ChanDown
    config = key-audiodelay-down
    repeat = 0
    delay = 0
end
#-----------------------

#Enter (Cycle Audio)----
  begin
      remote = mceusb
      prog = vlc
      button = Enter
      config = key-audio-track
      repeat = 0
      delay = 0
  end
#-----------------------

#Enter (Cycle Audio Dev)-
  begin
      remote = mceusb
      prog = vlc
      button = Clear
      config = key-audiodevice-cycle
      repeat = 0
      delay = 0
  end
#-----------------------

#Teletext (Subtitles)---
begin
    remote = mceusb
    prog = vlc
    button = Teletext
    config = key-subtitle-track
    repeat = 0
    delay = 0
end
#----------------------

#Zoom (Aspect Ratio)---
begin
   remote = mceusb
   prog = vlc
   button = Aspect
   config = key-aspect-ratio
   repeat = 0
   delay = 0
end
#----------------------

#Windows Key-----------
begin
  remote = mceusb
  prog = vlc
  button = Home
  config = key-toggle-fullscreen
  repeat = 0
  delay = 0
end
#---------------------

#Info / More Key------
begin
    remote = mceusb
    prog = vlc
    button = More
    config = key-position
    repeat = 0
    delay = 0
end
#---------------------

#Pictures (Snapshot)--
begin
   remote = mceusb
   prog = mythtv
   button = Pictures
   config = key-snapshot
   repeat = 0
   delay = 0
end
#---------------------



begin
    remote = mceusb
    prog = vlc
    button = OK
    config = key-nav-activate
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = vlc
    button = DVD
    config = key-disc-menu
    repeat = 0
    delay = 0
end
```

MPlayer
```

begin
    remote = mceusb
    prog = mplayer
    button = Play
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mplayer
    button = Pause
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mplayer
    button = OK
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mplayer
    button = Power
    config = quit
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mplayer
    button = Mute
    config = mute
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mplayer
    button = VolDown
    config = volume -1
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mplayer
    button = Skip
    config = seek +15 0
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mplayer
    button = Enter
    config = pause
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mplayer
    button = Stop
    config = quit
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mplayer
    button = Up
    config = seek +60 0
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mplayer
    button = VolUp
    config = volume +1
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mplayer
    button = Down
    config = seek -60 0
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mplayer
    button = Replay
    config = seek -15 0
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mplayer
    button = Right
    config = seek +6 0
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mplayer
    button = Rewind
    config = seek -30 0
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mplayer
    button = Forward
    config = seek +30 0
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mplayer
    button = Home
    config = vo_fullscreen
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = mplayer
    button = Left
    config = seek -6 0
    repeat = 0
    delay = 0
end


```

I hope this helps you a little and gets you going in the right direction.

---

### Post by joeb1990 on 2010-01-20
so i sort of understood the config file but didnt know you had to make separate ones. This brings about a few more questions.
1. How do I use it to navigate the desktop
2. Where do I put all these configuration files
3. Can I find preloaded config files
4. How do I no the exact name of the buttons and program functions

---

### Post by sports.car.guy on 2010-01-20
> **joeb1990 said:**
> so i sort of understood the config file but didnt know you had to make separate ones. This brings about a few more questions.
1. How do I use it to navigate the desktop


There is no application for Gnome that I know of to do that. Windows does not do that anymore either, and it only did it with the ATI X10 RF remotes. KDE has KLirc which just got ported to KDE4 from version 3. I have never used it but it should do what you are looking for.

ADDED:

Not trying to be an jerk with this add. I can clearly see on Lirc's site, a means to set up and configure Lirc in the documentation, and also a tutorial off the site for setting up on Mandriva, which most would apply to Ubuntu like configuration. Both sources of information cover it all.

Actually I stand to be corrected, Linux can use Lirc as a mouse input. I found it in two seconds on the Lirc website and it is a matter of copying and pasting one snippet to your xorg.conf. You made it sound like you researched this and didn't understand it. I don't think you researched how to do this, jumped in, got over your head, don't want to read now, and are hoping that someone will bail you out. All because you just expected it to work.

I am going to point you to the information on how to do this, not just hand it to you. I am sick of coming out here and having this be the case where someone can't google and actually put some effort into getting things like Lirc, which is very well documented up and running.

All the questions below, I answered already in my first reply for the most part. You are basically asking me to do this for you. I am not tech support. I will help someone who will help themselves, but not someone who won't. My time is worth good money. I am business owner who could and should be putting my knowledge of Linux and technical expertise towards it right now.

If you paid me what I am worth for my time, I would set this all up for you, but you aren't. Make an effort to help yourself.

> 
2. Where do I put all these configuration files


As I stated in my first post these configuration files came out of .lirc in my home driectory, translation there needs to be a .lirc directory in your home one.

> 
3. Can I find preloaded config files


This is proof you don't want to read and didn't read, about Lirc, or my reply. I told you there is an application for Gnome to configure your remote, and also Mythbuntu Control Centre has a configuration screen for remotes as well.

Proof you didn't google anything about Lirc is I just googled download Lirc config files and found several you could copy off pages verbatim and have a remote working with any number of particular apps. They are for a WMC MCE remote like you have.

> 
4. How do I no the exact name of the buttons and program functions
[/QUOTE]

If you read it is well documented on the Lirc remote documentation. I also believe I stated that the Gnome configuration program will give you the button names. If not my bad, but if you tried to actually set up Lirc, you would have probably stumbled on it yourself. That is how I found out about it. It is also how I found out how to setup Lirc, and it was far from rocket science.


Here are the links to the pages that will help you get this all working.

[http://ubuntuforums.org/showthread.php?p=8697149#post8697149](http://ubuntuforums.org/showthread.php?p=8697149#post8697149)

[http://www.lirc.org/html/configure.html](http://www.lirc.org/html/configure.html)
(Has the snippet for using a remote as a mouse on it)

[http://www.mandrake.tips.4.free.fr/lirc.html](http://www.mandrake.tips.4.free.fr/lirc.html)

[http://www.mythtv.org/docs/mythtv-HOWTO-8.html](http://www.mythtv.org/docs/mythtv-HOWTO-8.html)

[http://www.mythtv.org/wiki/MCE_Remote](http://www.mythtv.org/wiki/MCE_Remote)

Like I said. I am not trying to be a jerk. I am sick of this type of mentality. I liked it back when people tried to set something up themselves and researched. When they couldn't get something to work at all or right, that is when they went looking for help because it was something they could not find an answer to. This is Basic Linux stuff that most Distributions configure the services on so it works, minus remote mappings.

That is all you need to make it work, and that is documented in god knows how many languages. So regardless what is your primary language that you speak, you should be able to get it up and running.

Not coming out here looking for me or another to do it for you. This is not a bug, it isn't quirky hardware, it is, as I said, basic Linux stuff, and like a lot of the newer Ubuntu and other Linux distro converts from Windows, you want someone else to do the work for you because Linux seems too scary, and it is not.

I am not saying all the Windows converts of recent are like this, but more and more are these days.

Sorry for going off on you, but come on you expected me to just hand this all to you and do the work for you. I dealt with that in college when I was in my computer science classes having intellectual leeches trying to have me do it all for them and I didn't let it fly then and not going to now.

Now if you actually give it a try and hit a snag, an actual one that isn't clearly spelled out if you had read, then I am more then willing to help, and more then a nice guy while doing it. I am not going to be taken advantage of though and do your stuff for you. I won't let people in my actual life do it why would I let someone god only knows where over the Internet?

---

### Post by joeb1990 on 2010-01-20
In actuality I believe it is you who havent been doing your reading. I already stated I had been through lirc's website and to no avail. I did forget to mention that I have the gnome remote configure program but also to no avail. Which brings us back to why this thread was created to begin with. Also, I am sick of having to deal with dickheads on forums who shouldnt start talking if they dont have the patience to finish.Maybe you shouldn't assume people have not done the research before you start getting so upset because I have been to nearly every link provided and have no success.

To anyone else who would like to help. I believe that the problem lies in the recognition of the remote. I dont know if it is a driver or hardware issue only that the gnome application takes no reading of button activity and all the tutorials I have started fall short.

---

### Post by sports.car.guy on 2010-01-20
> **joeb1990 said:**
> In actuality I believe it is you who havent been doing your reading. I already stated I had been through lirc's website and to no avail. I did forget to mention that I have the gnome remote configure program but also to no avail. Which brings us back to why this thread was created to begin with. Also, I am sick of having to deal with dickheads on forums who shouldnt start talking if they dont have the patience to finish.

To anyone else who would like to help. I believe that the problem lies in the recognition of the remote. I dont know if it is a driver or hardware issue only that the gnome application takes no reading of button activity and all the tutorials I have started fall short.


Patience to finish? Excuse me? I handed you more then enough in those links to get it up and running. I did the research for you and no you didn't read. There is documentation included with Lirc. Ever think to look at it besides the web?

Then there is the fact also in those links I sent it explains in documentation on them you can have one file with each programs buttons in it and declared and them all pointing to it. This way is messy and also you have to set each program to use it. The other way is to create a file for each program which as far as I know always the name of the program, which is the default it looks for. This is all clearly in several of the links I place here, which mind you took me 5 minutes to find, look over, and see they had what you are looking for.

If you had read the Gnome remote documentation it explains how it will help you setup the modules, etc, and let you get button info so you can create your Lirc files for each program and put the correct buttons. The Mythbuntu Control Center will create the mappings for a bunch of different media players and also help you set up Lirc to load and use the correct modules.

If you did google and read, everything, and I mean everything you are asking is documented in multiple languages.

You basically in your last post, not directly mind you, asked me to do it all for you and you have the balls to call me a dickhead because I would not. Hmmmmm who is the dickhead getting all whiny because I wouldn't set up your Lirc for you. Hand you over remote configs, even though I told you of an app that will generate the defaults for several programs for you, Mythbuntu Control Centre.

You said how you couldn't find how to use the remote with the desktop, yet on the Lirc's website in the configuration section, which I linked in my last post, Is the xorg.conf settings you need to place in it to get a remote to act as a mouse, and I am a dick? This is when I still was helping you out, but not handing you remote configs like I did in my first post. 

I then told you of a program for KDE that would allow for you to do a lot of desktop and application control, KLirc, which I put in both my posts, and I am the dickhead?

Get a reality check man!

You just don't want to admit you expected to just be able to install Lirc, have everything just work, and when you found out that wasn't the case you hoped someone would just hand everything over to you doing the leg and actual work for you.

You can try to sound like you are a victim here, but you are not. You can say that your intentions weren't to have me or someone else do YOUR Lirc config for you. You can make me the ***. I don't care.

I tried to help you and even gave you two examples in the first post. My second post after seeing how you want it handed to you all setup from me with a bow, I still referred you to pages that lay everything out in English, not like it was in an alien language.

When you saw you would have to read and do some work you went all infantile and started name calling. If you approached the forum, not looking for a hand out, and tried to help yourself, maybe I wouldn't have felt like you expect me to do your Lirc config for you which is the case, and say here is the stuff you need to know good luck.

I am a nice guy, but I am not a sucker. I am not here to do the leg work and setup something for you! I am here in my free time to try to help someone who has put an effort in, and is dealing with a legitimate issue. Not someone who don't want to try at least to help themselves and hope I will do it for them.

That is why I got out of the whole forum thing and helping people in the first place. Because I know even if I handed to you Lirc config files and everything on a silver platter there would be no gratitude from you on it. There may be a hollow thank you but that is about it. Simply why is you are the type that thinks this world and everyone in it owe you something and you expect them to deliver regardless they are a person too with their own lives and considerations in it.

If you weren't you wouldn't expect us out here to drop everything and do your Lirc config files for you!

---

### Post by jakell on 2010-02-05
Sports Car Guy, it would take you 1/4 of the time to actually help this guy, than you spent telling him why you won't. You're not only rude, you're obsessive and verbose with it.

---

### Post by epitaph on 2010-02-05
I, too, found the most easily discovered documentation on LIRC to be somewhat cryptic.

First, I would plug in a keyboard and mouse to simplify this whole experience until you get your remote working properly.

This is what I ended up doing to use my MCE remote on my HTPC.

(Most of the following is from [http://www.mythtv.org/wiki/Ubuntu_lirc_install](http://www.mythtv.org/wiki/Ubuntu_lirc_install) which is for a much older release of Ubuntu and MythTV, but don't worry)

First:

```
sudo apt-get install lirc lirc-modules-source module-assistant
sudo dpkg-reconfigure lirc-modules-source 

```

Select the Windows MCE Remote option when it prompts.

```
sudo m-a update,prepare
sudo rm /usr/src/lirc*deb
sudo m-a clean lirc
sudo m-a a-i -f lirc
sudo depmod -a

```

```
sudo modprobe lirc_mceusb2

```

This may just end up being lirc_mceusb instead of mceusb2 since I believe they were consolidated at some point. Try to see which module is listed in:

```
sudo nano /etc/lirc/hardware.conf
```

If you're new to nano, use ctrl+x to exit. The module should be listed where it says MODULES="".

After starting the module:

```
sudo /etc/init.d/lirc restart
```

You may have to use start or stop to replace restart.

At this point, test the receiver+remote:

```
irw

```

Press some buttons, it should respond. If it does, congratulations, it's "working".

Next, generate some baseline configuration files:

```
sudo apt-get install mythbuntu-lirc-generator
mythbuntu-lirc-generator

```

This will give you some pretty cut-and-dry configuration files. MPlayer should work by default, and VLC requires you to enable the IR remote module. You can find this in your home directory in a folder called ".lirc". I personally use XBMC on the media center which had no quarrels with the remote.

I have some of this stuff documented in a posting on my site [(click)](http://www.trishock.com/talky/archives/101), but it's mostly a rehash of things I have already said.

Good luck, hope this helps.

---

### Post by windmill77 on 2010-02-06
Hey epitaph, 

A BIG thanks to for the useful instructions, worked perfect 1st time.

Glad I ignored the 1st guy - as you do!

---

### Post by jakell on 2010-02-17
Having wrestled a little with LIRC, and become frustrated (namely, how to reconfigure the remote without re-installing the package, and the lack of a WinTV Nova-T module), I reinstalled Ubuntu 9.10.

 I then noticed that the remote still had some functionality, without LIRC, ie volume, jump backward/forward Power on/off.

 Looking at which packages are installed in the base install, I just saw liblircclient0 (infrared remote control support - client library) and no other LIRC packages. So I am assuming LIRC is not fully installed.

 My question is this.... If basic Ubuntu has some Remote control functionality, is it possible to build on this, without having to bother with LIRC?

---

### Post by jakell on 2010-02-24
Got it!

The remote is acting as a keyboard input in the basic Ubuntu install.

LIRC does seem fairly complex considering that all that needs doing is to remap the remote buttons, but it seems that it is the way to go.

---

### Post by samuelkarush on 2010-03-08
ya, thats what i finally figured out. volume and numbers work on my pinnacle remote even if lircd is not running.

 so i got a lircd.conf built using irrecord, and put it in /etc/lirc/    the  lircd deamon starts no prob but in syslog i get this -could not open config file ''''
 mode2 runs with no input shown on screen.

 so what needs to be done to get lircd deamon to find/open the lircd.conf file?

edit:

 so i reinstalled lirc and choose linux input layer instead of a pinnacle product and lircd starts and finds the conf file now. i didnt even have to use the lircd.conf file i had made.

fwiw my ir receiver is one that plugs right into the pinnacle card. not a usb or serial one.

 then i ran the mythtv lirc generator and everything works. took forever.

sam

---

