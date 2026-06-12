---
title: "server playing mp3-collection to hifi-set"
date: 2008-12-25
forum: Multimedia Software
---

### Post by DoppyNL on 2008-12-25
Hi all,

I'm looking for some software that will do for me what I want, but I can't seem to find it.
I hope someone can point me to the software that will do for me what I'm looking for.

Current situation:
- Ubuntu 8.10 server (no, X-system, no monitor, no keyboard)
- network interface (duh)
- running lamp
- running samba
- has a (simple) soundcard
- CD's converted to mp3
- mp3's are stored on the server

What do I want?
Play music on the server and use it's soundcard to send it to my hifiset. A webinterface to interact with the software to allow the selection of wich tracks to play, generate playlists and maybe even manage the collection.
Optionally: also play mp3s streaming from the web interface (from remote locations) (note: this is nice to have!)

What software is out there that can do this allready?
Is there a howto somewhere that will help me on the way and install what I need?

If I posted in the wrong section I apologise, please move the topic or direct me to the right section.

tnx in advance.

in short I want this:
**I want the server to hold the files and play the files. I want to tell the server what to play via a browser (from any other device I want).**

---

### Post by namdung on 2008-12-25
Consider
[http://www.geexbox.org/en/index.html](http://www.geexbox.org/en/index.html)

---

### Post by DoppyNL on 2008-12-25
Thanks for your reply.

Geexbox looks like an excellent tool if you want a server that does everything, and nothing more.
It is however an operating system on its own, so I would need to install that instead of Ubuntu.
I don't want to drop Ubuntu, I want something that I can install/configure on Ubuntu.

I don't need any video-capability. This will probably also be to much to ask for. It's pure about my audio-collection that I want to be able to run from my allready running server.

Geexbox looks very good, it's just not what I'm looking for.

Thanx for your reply and time though!

---

### Post by namdung on 2008-12-25
Connect Ubuntu and Geexbox with ushare which is available in Synaptic Package Manager

[http://ushare.geexbox.org/](http://ushare.geexbox.org/)

---

### Post by jamesisin on 2008-12-25
I am working to build something similar.

I'm not sure you're going to find a command line version of Rhythmbox, foobar2000, or Amarok which will handle all the functions for which you are hoping.

My thinking was to have the server merely serve (probably file-serve), and run a small hi-fi computer to manage the rest (with a GUI).

An advantage to this arrangement is that I will have access to the music from all computers on my network.

Though I do have to ask, why mp3's?  Can that really qualify as hi-fi?  I plan on using waves since I'm only serving my local network (and storage is now dirt cheap).  You may want to at least consider using flac.

---

### Post by DoppyNL on 2008-12-28
> **namdung said:**
> Connect Ubuntu and Geexbox with ushare which is available in Synaptic Package Manager

[http://ushare.geexbox.org/](http://ushare.geexbox.org/)

Look into it, but this would require me to run 2 servers. One with Ubuntu and one with Geexbox. I want it solely on my Ubuntu-server. There is no need for another server. Would be costly to invest in hardware and also more costly in power usage.

Allthough this solution could be usefull for some people who also want something like a geexbox.

---

### Post by DoppyNL on 2008-12-28
> **jamesisin said:**
> I am working to build something similar.

I'm not sure you're going to find a command line version of Rhythmbox, foobar2000, or Amarok which will handle all the functions for which you are hoping.
There should be something out there that does what I want.

> **jamesisin said:**
> My thinking was to have the server merely serve (probably file-serve), and run a small hi-fi computer to manage the rest (with a GUI).

An advantage to this arrangement is that I will have access to the music from all computers on my network.
This would require 2 computers doing the work. While one should be sufficient. The one server should also be able to share the files in any other way you want. Would be a bit costly to buy hardware for both and have them both consuming power.

> **jamesisin said:**
> Though I do have to ask, why mp3's?  Can that really qualify as hi-fi?  I plan on using waves since I'm only serving my local network (and storage is now dirt cheap).  You may want to at least consider using flac.
I allready have a large number of mp3s. Converting them to wave (or any other format) would be useless unless the new format is smaller then the original. I can't add quality that way...
Using a different format wich supports better quality is allways a good idea. But I don't really need such high quality at the moment.

---

### Post by 5BallJuggler on 2008-12-28
This is the 1st time i've seen this thread, I use Firefly media server, it can be pointed to look at file locations on your PC and then stream the contents to another over the wifi network

more info from :-

[http://jamiedumbill.com/index.php?page=28](http://jamiedumbill.com/index.php?page=28)

it takes a little setting up, but once it's going it's very stable
I using a Roku Soundbridge as an interface to my HiFi system, sound quality is fantastic and speed of operation from the interface is good too

I use RythymBox to organise the music into one location

---

### Post by jamesisin on 2008-12-28
Perhaps there *should* be, but *should* and *is* can be worlds apart.

You are running Ubuntu server.  Out of the box there is no GUI.  You'll have to assemble a desktop environment if you want to use most of the fancy audio applications (like Rhythmbox or Amarok).  But in that case, perhaps you'll be better suited by installing the desktop version of Ubuntu and just giving it the functionality needed to serve the files you wish to serve?

One thought on GeexBox is perhaps you could run GeexBox inside VirtualBox and connect it back to the host machine using uShare?  I just downloaded GeexBox and will try making a VM out of it later.

Firefly looks promising and it looks like it could work on either the desktop or the server editions.

Here is their site:

[http://www.fireflymediaserver.org/](http://www.fireflymediaserver.org/)

As regards my interst in two machines (a server and a hi-fi box), I will only need to run the hi-fi box when I want to pull music to that location.  And if the server does any other work for me then this ends up being an advantage.

And finally, as regards file types, I have about 80 gigs of mp3's.  Most of my CD collection exists in that state already.  Nonetheless, if I am going to pack my CD's into boxes in the basement I want to have access to the full audio they have available.  I will be re-ripping all of my CD's (more than 600) as waves.  Otherwise I could just buy an mp3 player that would hold that entire collection and plug it into any system in the house (or beyond).

---

### Post by MartyBuntu on 2008-12-28
> **DoppyNL said:**
> I want it solely on my Ubuntu-server. There is no need for another server.

I'm not sure you understand the meaning of the word "server".

From reading your posts, it sounds like you need a capable "client" handler and Geexbox is perfect for the task you described.

---

### Post by jamesisin on 2008-12-28
MartyBuntu - What do you mean by *client handler* in this case?

---

### Post by DoppyNL on 2008-12-29
> **jamesisin said:**
> Firefly looks promising and it looks like it could work on either the desktop or the server editions.
I will look into Firefly later, first look is interesting. Got to work now, so no time to dive in it. ;).

---

### Post by DoppyNL on 2008-12-29
> **MartyBuntu said:**
> I'm not sure you understand the meaning of the word "server".

From reading your posts, it sounds like you need a capable "client" handler and Geexbox is perfect for the task you described.
From what I've read from Geexbox is that it requires it's own hardware. Wich means I need to run 2 complete computers/servers to be able to use it.
I want all of it on 1 single computer/server (ie: one fysical box) for power usage reasons and simply because another computer costs money to put in place.

I'm also interested in what you mean with "client handler".
All I know is I need someplace to store the files and manage them. And I need an interface to play them through the soundboard to my hifiset. All on one computer/server wich is running Ubuntu.

greetz

---

### Post by JoshLukas on 2008-12-29
I don't know if I understand you correctly. You want to play music localy on your server beeing output through the sound device to your connected hi-fi hardware and being able to stream to other devices in your home?
Well if that is so, you can virtualize geexbox on your server, so you don't need to buy any hardware, or you can just have a look at [ampache]("http://ampache.org/").

---

### Post by MartyBuntu on 2008-12-29
Simply put, if your server is in one room and your hi-fi is in another and you're standing in the room in front of your hi-fi, how are you going to access your server?

Okay, for example, here is my setup:

1. In my basement, I have my **server**. It is a headless Kubuntu 7.10 holding all my music and video files, configured to share with Samba.

2. In my living room, I have an XBOX hooked up to my TV running XBOX Media Center. It can access files on the server and play them through my TV and stereo receiver. This is acting as a **client**.

3.In my office, I have my wife's computer dual-booting XP/Ubuntu 8.10. It can also access the server and pull up any media file. When it does this, it is also acting as a **client**.

4. In my workshop, I have an old Pentium III generic tower PC that I mounted a 5" LCD screen on the front of. It boots Geexbox from a Compact Flash card and can also access the files on the server. When it does so, it acts as a **client**.


Short answer: Yes you need some sort of "computer" device at each
terminal you wish to access the **server**.

---

### Post by DoppyNL on 2008-12-29
I think you don't understand what completely what I want to do.

I've got a single server, wich will be located in my living room somewhere. This will be connected via UTP no my local network and internet.
This computer will ALSO be connected directly to my hifi-set using an audio-cable.
I want to use a webinterface on any other location to interact with the server and tell it to play song X or playlist Y on the server (and thus sending it to my hifiset).


It would be nice if I could also play songs streaming from any location I want, but that is not a requirement.

---

### Post by MartyBuntu on 2008-12-29
You still need a "computer" at each terminal you want to access the server from...


...unless...


...and this is only because your "server" is in the same room as your hi-fi...


...you TV-OUT or VGA-OUT a small LCD screen (2.5" - 7") that is located near your hi-fi and browse your server with a remote control. For this, you would setup Geexbox *on top of* your existing installation.

This is doable. I've done this before.

---

### Post by DoppyNL on 2008-12-29
> **MartyBuntu said:**
> You still need a "computer" at each terminal you want to access the server from...

...unless...

...and this is only because your "server" is in the same room as your hi-fi...

...you TV-OUT or VGA-OUT a small LCD screen (2.5" - 7") that is located near your hi-fi and browse your server with a remote control. For this, you would setup Geexbox *on top of* your existing installation.
Why do I need a TV-OUT or VGA-Out or a monitor or a small LCD screen if I can simply tell the server what to play via a browser?
All I need is another computer with a browser or Mobile Phone with a browser to tell the server what to do.

Yes, you need another computer to tell it what to do. But I'm completely flexible in what device that is and can switch on the fly. I could set it to play a certain playlist and then turn of the computer I used for that, or reboot it, or let it crash... The server would keep on playing that playlist!

Most of the time I will be working on my laptop, wireless, without any cables. Unable to send a signal to my hifi-set, but able to access a web interface on my server wich is able to send a signal to my hifi-set.

---

### Post by MartyBuntu on 2008-12-29
Okay, so browse your server from any device you want with Samba shares and play the files.

The management software you want should be on your laptop...Amarok will do just fine.

---

### Post by DoppyNL on 2008-12-29
> **MartyBuntu said:**
> Okay, so browse your server from any device you want with Samba shares and play the files.

The management software you want should be on your laptop...Amarok will do just fine.
As explained, I don't want to do that. 

**I want the server to hold the files and play the files. I want to tell the server what to play via a browser (from any other device I want).**

Simply because at one time I will be on my laptop, the other time my girlfriend will be on her laptop and I'm not home.
Or I am on my laptop, but without a cable to my hifiset (love to work wireless!)

But then again, I thought I said that allready :| Perhaps I wasn't clear :|

---

### Post by MartyBuntu on 2008-12-29
> **DoppyNL said:**
> 
**I want the server to hold the files and play the files. I want to tell the server what to play via a browser (from any other device I want).**


But then again, I thought I said that allready :| Perhaps I wasn't clear :|

Samba shares. Other than that, I have now idea how *you* plan to browse the server. Do you mean **web** browser?

> **DoppyNL said:**
> 
:| Perhaps I wasn't clear :|

Honestly, I have no idea what you want.

---

### Post by DoppyNL on 2008-12-29
> **MartyBuntu said:**
> Do you mean **web** browser?Yes.

> **MartyBuntu said:**
> Honestly, I have no idea what you want.Perhaps in other words it is more clear:
Running a program like amarok on my server; but instead of using a window in X on the server, the interface is a website wich I see on another computer in my webbrowser firefox.

---

### Post by MartyBuntu on 2008-12-29
> **DoppyNL said:**
> Yes.

Perhaps in other words it is more clear:
Running a program like amarok on my server; but instead of using a window in X on the server the interface is a website wich I see on another computer in my webbrowser firefox.

Accessing shares through a web browser is pointless and impractical unless you are talking about FTP'ing to your server.
This is not what you want.

Amarok *would not* be run on your server, it would be run on your *client*...(laptop...whatever)

Seriously, you need to set up Samba shares. It is **exactly** what you are looking for. Samba shares can be browsed from an Ubuntu machine, a Windows XP machine, a MacBook Pro, a toaster hacked to run Solaris...whatever...

Don't make this unnecessarily difficult.

---

### Post by DoppyNL on 2008-12-29
> **MartyBuntu said:**
> Accessing shares through a web browser is pointless and impractical unless you are talking about FTP'ing to your server.
This is not what you want.Indeed, that is not what I want; I want to play mp3's, not share files.

> **MartyBuntu said:**
> Amarok *would not* be run on your server, it would be run on your *client*...(laptop...whatever)I was refering to Amarok as an example application. I want to run an application on my server that will play mp3-files to the soundboard in my server, wich in turn sends that to my hifi-set.
I want to tell that application what to do via my web browser on another computer.

> **MartyBuntu said:**
> Seriously, you need to set up Samba shares. It is **exactly** what you are looking for. Samba shares can be browsed from an Ubuntu machine, a Windows XP machine, a MacBook Pro, a toaster hacked to run Solaris...whatever...I know what Samba can do, I allready use it. But I don't want to play the mp3's on my laptop, I don't have a wire from my laptop to my hifi-set!!


Seriously, I don't want to be offensive or anything. But please read what I'm saying! I get the idea you're not!

---

### Post by MartyBuntu on 2008-12-29
Remote Desktop to your server...pick the files to play from there.

That's all I have left. Hope it works for you.

---

### Post by d8a on 2008-12-29
Hi DoppyNL

I use a setup that seems to be similar to what you want.

My server is connected to my A/V-Receiver and running [[COLOR="Red"]_mpd_[/COLOR]]("http://mpd.wikia.com/").

On my laptop I use [[COLOR="Red"]_Sonata_[/COLOR]]("http://sonata.berlios.de/") (I know it isn't a web interface) as GUI/Client to control mpd on my server.

Anyway, I chose this setup because I didn't want to plug in the audio cable into my laptop (or any other computer on my network) for playing music anymore.

I hope that helps.

Edit: For a web interface have a look at [http://mpd.wikia.com/wiki/Clients#Web_Clients](http://mpd.wikia.com/wiki/Clients#Web_Clients) there may be something you're looking for.

---

### Post by jamesisin on 2008-12-29
If you set up your hi-fi server machine to allow terminal connections you can remote into that machine, start the music, and then sever the remote connection (leaving yourself logged in).  Ubuntu has a combination of apps (Remote Desktop Viewer and Terminal Server Client) which I believe are perfectly suited for making that connection.

I use Remote Desktop Viewer to access my terminal server (Windows SBS 2003) which serves my sites (JamesIsIn.com and SoundUnReason.com).  The server is constantly running (duh) but I am rarely signed into it.  I could--and do--sign into that server, start an application running (or a file transfer or something), and then close my RDV without logging out of my terminal session.  This leaves the app (or file transfer or whatever) running on the server--until I log in again later and close it.

This was my plan for my hi-fi computer.  No monitor, keyboard, or mouse.  Remote into it and start some music (from any location, of course--even from work).  Presto: music in my living room.  The only difference is that I plan to create both a strict server and a hi-fi client machine, while you want your server to also act as a client machine to your hi-fi.

All that being said, I was thinking of something like Ubuntu server (with an added desktop environment for ease of use) doing the serving.  Let's say it merely file serves to my local network.  Then my hi-fi computer runs something like Rhythmbox and uses the network drive as its music library.  In your case, you would have Rhythmbox (or...) on your hi-fi server so that it could play the shared directory directly.

Log in, start a playlist, set it on repeat, close RDV.  Later on, log back in, stop Rhythmbox, log out (or even shutdown) through the RDV.  (If your laptop is not Ubuntu, there are other remote desktop client applications you will be able to install.)

Or something like that...

---

### Post by jamesisin on 2008-12-29
d8a - So, he could install one of the various clients on the hi-fi server machine and thereby control the daemon, asking it to send its output signal to the local sound card?

---

### Post by d8a on 2008-12-29
> **jamesisin said:**
> d8a - So, he could install one of the various clients on the hi-fi server machine and thereby control the deamon, asking it to send its output signal to the local sound card?

Actually, no. He just needs to install mpd on the server machine. But he needs to install a client on the machine he wants to use to control the mpd on the server machine.

I'm not sure about the Web Clients ... the only thing that makes sense, is to install them on the server. Who would want to install a WEB INTERFACE on the "client" machine. That would not make sense. The advantage of using a web interface is to use a(ny) browser to control that thing and NOT install a client. BUT I didn't look into the web clients, so I can't tell you for sure.

---

### Post by jamesisin on 2008-12-29
I see.  And so you, from your laptop with Sonata, cause the daemon on your hi-fi machine to play into your hi-fi system?  This is definitely worth exploring.

Would it also be viable in the scenario I am describing?  I will build a music server and a separate hi-fi computer.  Will I be able to remotely direct the server (with the daemon) to send a stream to the hi-fi computer?

---

### Post by d8a on 2008-12-29
> **jamesisin said:**
> I see.  And so you, from your laptop with Sonata, cause the deamon on your hi-fi machine to play into your hi-fi system?  This is definitely worth exploring.

Now you got it! I've got my mp3 files on the server, the server is connected to the hi-fi and Sonata just tells the server/mpd to play this or that mp3/playlist/whatever.


> **jamesisin said:**
> Would it also be viable in the scenario I am describing?  I will build a music server and a separate hi-fi computer.  Will I be able to remotely direct the server (with the deamon) to send a stream to the hi-fi computer?

I'll read through your post again, but it sounds like what you want to do is possible with mpd.

The reason why I don't use a remote desktop connection is, that 

1. I don't want to use the xserver (and the OP doesn't want to use it either). 

2. Also IIRC I have to stay connected, as a remote desktop connection uses a separate xserver window which closes (everything) if I close the connection (this might have changed since the last time I played with that).

---

### Post by jamesisin on 2008-12-29
Actually, seeing how this works, I guess the thing to do would be access the hi-fi computer remotely and use it to trigger mpd on the server to then send the music signal back to the hi-fi computer.

Alternatively, since it looks like this daemon is command line based, you could merely ssh into the server once everything was set up correctly and run from there.

I'm not clear how the remote connections work in Ubuntu.  If I start a process through ssh, for instance, I can close my ssh client without exiting my session on the remote machine and what I have started there should continue running (just as it would continue running if there were any interuption in my connection).  I know that if I close my RDV in Ubuntu it does not send a log-off or shutdown signal to the remote machine.

---

### Post by DoppyNL on 2008-12-30
I've installed mpd on the server and Sonata on my laptop. I figured I could test it that way easily and will be looking at other available clients later.

All seems to be working at the moment. I can start playing mp3s with Sonata and it seems that mpd is playing them on the server itself.

Only problem is, I'm not hearing anything! But I think that is caused by the fact it is a server-installation, wich generally don't need any audio, so that isn't installed...
[I've opened another thread to look solve that problem, as it is not related to this question... (click here)](http://ubuntuforums.org/showthread.php?t=1025409)

---

### Post by DoppyNL on 2008-12-30
Got my sound problem fixed, see the other thread for details about that.

I've got mpd running on my server and I'm telling it what to do using an application on my laptop.
The configuration of all this was extremely simple in quickly done.

In short: it works!

I now only need to look at what client I want to use to tell the server what to play. Sonata works, but I find it a bit simple and would like some additional features. But so far it's nice :).

Tnx for the help!

---

### Post by d8a on 2008-12-30
That's great to hear! I'm glad I was able to help.

---

### Post by retrovelo on 2009-01-01
MPD sounds very cool. I'll be looking into that. 

If you're looking for something a bit simpler, try mp3act. It's a bit of an orphaned project these days, but nonetheless it will do exactly what you're looking to do, and a bit more.

Mp3act is a AJAX-driven LAMP app that you offers a 'jukebox' mode to plays tunes through the server's sound card, and a 'streaming' mode that sends m3u playlists to the browser. 

I've been using it for quite some time, and have made a few updates. For me it's proven to be a slick little system. It's served me well, but after scanning the MPD Wiki, I'll definitely be taking close look at that. 

As I recall there was one notable tweak I needed to make when installing it on Ubuntu. If you're interested I can share the details...

Mp3act source and screenshots can be found at sourceforge: [http://sourceforge.net/projects/mp3act/](http://sourceforge.net/projects/mp3act/)

---

### Post by Mykle87 on 2009-01-14
I just stumbled into this thread. Couldn't you simply use vlc media player? 

[http://wiki.videolan.org/Control_VLC_via_a_browser](http://wiki.videolan.org/Control_VLC_via_a_browser)
[http://wiki.videolan.org/Web_Interface](http://wiki.videolan.org/Web_Interface)

I just tested and it in vista and it works very well. I'm not positive if it works the same way under linux, but I think it is worth checking out. This should allow you to control vlc while on your network and also let you stream files over the internet.

---

### Post by DoppyNL on 2009-01-14
> **Mykle87 said:**
> I just stumbled into this thread. Couldn't you simply use vlc media player? 

[http://wiki.videolan.org/Control_VLC_via_a_browser](http://wiki.videolan.org/Control_VLC_via_a_browser)
[http://wiki.videolan.org/Web_Interface](http://wiki.videolan.org/Web_Interface)

I just tested and it in vista and it works very well. I'm not positive if it works the same way under linux, but I think it is worth checking out. This should allow you to control vlc while on your network and also let you stream files over the internet.
I'm not 100% sure about this. But that would require an X-system to be running on the computer running VLC.
When you are running an X-system it might be usefull.
I wanted something that would run on a system without X.

---

### Post by Mykle87 on 2009-01-14
> **DoppyNL said:**
> I'm not 100% sure about this. But that would require an X-system to be running on the computer running VLC.
When you are running an X-system it might be usefull.
I wanted something that would run on a system without X.

I don't think you do. I think you could do something like this:
```
vlc --eintf=rc
```
That should launch vlc with the remote control interface. Then you connect to it by lan.ip.address:8080 in web browser.

[This has all the command line options for VLC]("http://wiki.videolan.org/VLC_command-line_help")

---

### Post by duktape76 on 2009-02-18
Hi DoppyNL. I'm sure by now you have it all figured out. I just wanted to let you know about my setup that I have been running for about a year and am extremely pleased with. 

I'm running ubuntu server headless. The audio signal from the sound card is split and is connected to three different receivers in three different rooms. I am running MPD to play my mp3 files and phpMp2 to serve the web control. The advantage of using a web client is that I can control what is playing at my house from any browser, local or at a remote location. I can also control my music through my blackberry browser.

If you plan on using your phone as a controller, look into the mobile web clients like neoMPC. I run phpMp2 and neoMPC simultaineously from different directories. For example, from my phone I go to <mywebaddress>/neo and I am served the mobile version.

Also, Minion is a really cool firefox add-on. 

Hope this helps you, or anyone else interested in this sort of set-up.

---

### Post by anotherdike on 2009-02-22
Give the Firefox extension, Minion, a look.  It might be just what you're looking for.  It is platform independent, and configures the same as any of the other clients.

BTW, can you share your mpd.conf or .mpdconf?  I am trying to set this up on my home network, not sure of all of the config file options that need to be specified.

EDIT:

Found that my configuration is OK.  I am controlling remotely via OS X Firefox with Minion.  I also found Theremin, which works well for my needs.  

Jinzora looks sweet, but I don't have the need to set something like that up just yet.  Though, the client could be something the OP is interested in.

---

### Post by caver1 on 2009-02-22
Take a look at Jinzora.
This is what it says about itself:
"Jinzora is a Web based media streaming and management system. It is supported in various platforms and it allows you to access your music collection from any devices over the Internet."
You can set it up on your server."
[http://en.jinzora.com/](http://en.jinzora.com/)
caver1

---

