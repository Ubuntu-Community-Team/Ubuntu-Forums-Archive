---
title: "Looking for a network controlled media player to run on a headless thin client."
date: 2020-09-15
forum: Multimedia Software
---

### Post by adrian-h on 2020-09-15
Perhaps the wisdom of the group can help here, I have been playing music to my amp from the PC, not very hi-fi I know as I get the odd pop and crackle from it as the computer does something else.  But!

As I have a Ubuntu 32 bit Thin client going spare (16.04) I was wondering if there was a media player for it, most of the software I find is for a media server and that is not really what I am after, but perhaps if I say what it is I am after someone may know of, or, use a solution.

Store mp3 files locally on the HD of the device.
Play through it's stereo output socket.
Have a web page server so that from another device I can drive it, select tracks, playlist etc.
Be able to upload to it.
Adjust the volume and if possible have an equaliser?
Be able to disconnect from the server server page and it still continue to play.

Perhaps some of the media servers can already do all this, I just do not know and believe I could spend hours, probably days trying to find a solution.

So thanks in anticipation.

Adrian

---

### Post by CelticWarrior on 2020-09-15
Perhaps overkill but Kodi or Emby can do that easily.

---

### Post by TheFu on 2020-09-15
"thin client" is extremely vague.  The exact model will be needed.
There are lots of non-gui music players.  Running a web server s one of the worst interfaces to control music playback.
Just ssh into the thn client and run cmus, mpv, mplayer, clementine (there's the client/server setup), or mpd [https://www.musicpd.org/](https://www.musicpd.org/) (a server) with many compatible clients like mpc.

I'd look at audio solutions running on raspberry pis, since those almost certainly run on ubuntu too. Music players for older r-pi hardware are some of the earliest headless projects.

I just ssh into a system and tell it to play a playlist, sometimes random, using mpv player.  Posted the code link here yesterday.

---

### Post by adrian-h on 2020-09-15
The thin client I have to hand is a HP T5730 the sort of thing that at one time would be bolted to the back of a monitor in an office or shop environment. 
A brief idea of specs.

proc = AMD Sempron 2100+ @1GHz shows as i686 so a 32 bit system.
Has 1GB ram on board with 14 GB drive, most likely flash drive if memory is correct there is around 9 GB free space.

It does have all the ports for keyboard/mouse Video USB and network etc to help set it up.

I could do a lshw if it would help.

Cheers

Adrian

---

### Post by adrian-h on 2020-09-15
Just a comment on why if possible a web type interface, it was basically just for ease, when it comes to command line, I think it would be more difficult to pick multiple tracks from various albums and move into a playlist.  I am sure that if you are good at typing without mistakes it would be fine, but some form of remote GUI would help lots even if done with a remote desktop.  Actually not sure if it is just a server install or a desktop install on the box, that is something I will need to check, but sure that package manager would let me know?

Adrian

Just a quick check with attached monitor etc and no xserver, so looks like a basic command line install plus a few extra packages.

---

### Post by TheFu on 2020-09-15
gnump3 is a simple player, centralized playlist, webapp.  You'll see quickly why this is less than ideal if there are 100+ tracks.

Nobody should be typing files to be played.  Use tab completion and simple regex patterns. If you are typing more than 3 characters, then you are doing it the hard way.  I can only suggest to learn the shell better. Look up "file globbing" to get started.

A number of the options provided are light enough for the system and have controllers you might like.

---

### Post by adrian-h on 2020-09-15
I just had a quick look at gnump3 and I am confused, it says it is a server, suggesting that it serves to other computers via the network with the client running a player such as mplayer, clementine etc, am I correct in thinking that a player could also be run on the same machine as the server, hence why you probably suggested the command line option?

It's just gone midnight here so will have to retire for the night, back in the morn, thanks for the comments.

Adrian

---

### Post by TheFu on 2020-09-15
The command line stuff was a separate thought from gnump3.  I haven't used gnump3 in decades. and forgot that it is a web server that provides mp3 playlists for a client player as http URLs.  mpv can play those playlsts from a cli.

Clemetine is te normal desktop program, but with a remote controller. Probably not very useful on a 1gb 32-bit machine.

---

### Post by CatKiller on 2020-09-15
> **adrian-h said:**
> Store mp3 files locally on the HD of the device.
Play through it's stereo output socket.
Have a web page server so that from another device I can drive it, select tracks, playlist etc.
Be able to upload to it.
Adjust the volume and if possible have an equaliser?
Be able to disconnect from the server server page and it still continue to play.

Perhaps some of the media servers can already do all this, I just do not know and believe I could spend hours, probably days trying to find a solution.

The thing that's pretty much exactly what you're after is [Volumio]("https://volumio.org/"). That's what I use on one of my Raspberry Pis. Because it can all be administered from a webpage, I can start it playing something from my laptop, say, then change to something else from my phone, then change it again from my tablet. It doesn't matter what device you want to use, as long as it has a browser, and you don't need a keyboard.

Linux software tends to be like Lego; you put them together however you want. In this case, the music playback is done by mpd, it knows about the various network storage protocols (my music is stored elsewhere on a NAS), it can act as a DLNA source or sink (using miniDLNA, I think), I'm not sure what the webserver is, and you can administer it through SSH as well as through the browser if you want. I generally SSH to my machines from my phone, but that particular Pi is single-use. So you can either build up the same thing, or start with something like Volumio and change bits out, or just use it as-is.

They have an x86 image, so you can try it out, but I'd suggest seriously considering using a Raspberry Pi or similar instead. The power draw will be much lower, and they can be passively cooled.

---

### Post by Holger_Gehrke on 2020-09-15
I think the already mentioned [mpd]("https://www.musicpd.org") is probably closest to what you're looking for. The server plays music on the server's sound hardware and is controlled by clients that tell it what to play. There are multiple clients ranging from simple cli-tools through text-mode pseudo-gui programs to full GUI clients running on all major OS to mobile clients for IOS and Android. I'd use Tiny Core Linux as the server OS and build from there ...

Holger

---

### Post by adrian-h on 2020-09-16
OK thanks all for the suggestions I will have a look at them and try some out.

The Thin client has no fan so is completely silent in operation like a Rasp PI, I do have one of those but an old B+ with 512K ram, which I though would have been a bit small now.

Cheers

Adrian

---

### Post by adrian-h on 2020-09-16
I have got Volumio running, installed on a USB disk plugged it in to the Thin client which then booted up to the image.  Also plugged in another usb stick with all my mp3 files on it and turned off all web sources that I could find.  It seems to do what I want apart from the equaliser, unless that is something I have missed.

I will have a look at gnump3 and mpd later although the documentation does not suggest web based player?  Sometimes I get confused over terminology so will persist.

At least the usb sticks to boot off means the Ubuntu operating system is still there if needed at the unplugging of a stick.

Cheers

Adrian

---

### Post by adrian-h on 2020-09-16
I have struggled getting mpd woprking Ubuntu seems to install 0.19 and the docs talk of later versions, the web interface just came back with an error so I have removed that, I just do not know enough.

gnump3 seems to have stopped development in 2007.  For the time being it looks like volumio will be used.


Adrian

---

### Post by Yellow Pasque on 2020-09-17
> **adrian-h said:**
> proc = AMD Sempron 2100+ @1GHz shows as i686 so a 32 bit system.

If it's the Sempron 2100 Fanless, then it should support 64-bit.

---

### Post by adrian-h on 2020-09-17
The processor may well do but the mother board may not be capable, not really sure all I know is that when I tried to install Ubuntu on it many moons ago 64 bits would not go onto it but 32 Bit would I gradually built it up from I think version 12 to 16.

I use, or have used a few HP Thin clients for projects like vehicle tracking and a small asterisk system.  It has to be a ready done software for me unfortunately.

Anyway I waffle details on the thin client here:-
[https://www.parkytowers.me.uk/thin/hp/t5730/](https://www.parkytowers.me.uk/thin/hp/t5730/)

Adrian

---

### Post by TheFu on 2020-09-17
I installed mpd and a few clients today. The system with the speakers connected is my "server".  Edit about 3 lines in the /etc/mpd.conf, restart the daemon, install mpc on that same system, run **mpc update** and let it create a db from the music directory.
Main things to change where the 
```
music_directory
bind_to_address         "any"
...
mixer_type      "software"

```
So it would know where the  audio files were and would listen to any network clients. By default, it is set to localhost, which is useless for a networked music player.

On the systems that will control the server, i installed ncmpcpp, setup the ~/.ncmpcpp/config file like this:
```
ncmpcpp_directory =         "~/.ncmpcpp"
mpd_host =                  "istar"
mpd_port =                  "6600"
mpd_music_dir =             "/stuff/music/"
```
The music_dir here is different from that on the mpd server machine. They see music in different places, so that makes perfect sense.

start ncmpcpp and see the music being filled in.  The audio volume can't be controlled by the client, it seems.  I used alsamixer over an ssh connection.  
Update: I use **mpc vol +5** and **mpc vol -5** to control volume now.

Installed MPDroid from the f-droid appstore (mostly gnu stuff) and pointed it at the mpd server IP.  This worked for my phone, but not for a tablet. Both use my internal DNS, but that didn't work for android. The tablet never saw the mpd server machine by name or IP.  With MPDroid, there's only the server IP to setup, left the other parts as default.

---

### Post by Tadaen_Sylvermane on 2020-09-19
I had Kodi running in an LXD container on my server and outputting to a remote pulse server on my lan. The remote only needed enough muscle to run itself and the network activity. You can use a server install with pulseaudio on your remote without a gui. Got the webapp / app on phone for controlling it. Good use for a raspberry pi / thin client with little muscle. PXE boot it for good measure, then it's nothing but a dumb terminal. Here is a link to the guide to it.

[https://forum.kodi.tv/showthread.php?tid=354606&highlight=pulse](https://forum.kodi.tv/showthread.php?tid=354606&highlight=pulse)

---

### Post by Yellow Pasque on 2020-10-20
> **adrian-h said:**
> I have struggled getting mpd woprking Ubuntu seems to install 0.19 and the docs talk of later versions, the web interface just came back with an error so I have removed that, I just do not know enough.

If you (or others) are looking for an updated version: [https://launchpad.net/~dtl131/+archive/ubuntu/mpdbackport](https://launchpad.net/~dtl131/+archive/ubuntu/mpdbackport)

---

### Post by adrian-h on 2020-10-20
Thanks for the heads up.  I am sure I have missed a few notifications from the site, perhaps my email provider is  blocking some.


Adrian

---

