---
title: "Need help with Samba and multimedia (VLC not cutting it)"
date: 2007-08-18
forum: Multimedia &amp; Video
---

### Post by deejross on 2007-08-18
First, let me apologize. This post may anger some of you out there, and that is not my intention. This post simply lets me vent my frustration, and ask for help. 

One of the biggest setbacks of moving away from Windows for me is the horrible lack of multimedia capabilities with a Ubuntu install. With every release of Ubuntu, I hope more and more that this will get fixed, or at least move in the right direction to being fixed. Truth is, we have the same multimedia capabilities now as we did in Dapper. I'm not talking about MythTV or LinuxMCE when I refer to multimedia, I'm talking about the SIMPLE things, like playing a DVD, or simply watching a movie encoded with DivX or Xvid.

I understand there are patent problems with playing these formats out of the box, and I'm not basing my opinion on that. I'm basing my opinion on the fact that I have to really go looking for libdecss2. It's not in the multiverse like the rest of the bad and ugly gstreamer codecs. Even with libdecss2, many DVD's won't play. This, to me is a HUGE set back.

Putting aside the encrypted DVD problem, I have a problem playing unencrypted DVD's as well. I back up most of my movies because I don't like fumbling around discs when I want to watch a movie. I can't do this on Ubuntu, even with K9copy, xDVDShrink, and all the other linux DVD backup programs. But again, I'm not focusing on the encryption right now.

I have all my music and movies stored on a Windows machine. All my DVD's are in folder format, as if you copied them straight from the DVD to the hard drive. Totem plays them one VOB at a time, and you can forget about seeking through the DVD. If I touch the seek bar or accidentally tap my mouse wheel, the movies stops and I have to watch it all over again to get back where I was. Totem's interface controls are terrible. Why on earth would you want to control the position of your movie with the mouse wheel? Don't you think it makes more sense to control, say, the volume with the mouse wheel instead?

VLC sucks and I've always hated it. I've never figured out why people love it so much. I have never gotten it to play a single frame of video in three years. It, along with MPlayer and Ogle are all useless to me since neither can stream over a Windows share. The only way to get either of these two players to play anything on a Windows machine is to manually edit the fstab file and mount the shares. Clicking Places, Connect To Server doesn't cut it....which brings me to another question...Why doesn't Connect To Server actually mount the shares? That seems somewhat strange to me.

The BEST media player out there, hands down is Media Player Classic. It's simple, compact, and plays everything out of the box, on the local hard drive, or over the network from a Windows share. It even handles the DVD folder format, where all I have to do is double-click on VIDEO_TS.IFO and it takes care of it all, including the menus. The only problem is, it's written for Windows and doesn't work with Wine. It amazes me that no one has created anything like that for Linux.

All I want to do is watch movies on my otherwise perfect operating system. Is that too much to ask? This is more of a cry for help than anything. I'm sorry if I offended anyone with my comments, but you have to see my side of things. Am I doing something wrong? Is there a kill-all player that everyone is now using and I just didn't get the memo, or does no one else watch movies on their computers?

Please, help me, and thank you in advance for your comments.

---

### Post by 23meg on 2007-08-18
> This post simply lets me vent my frustration, and ask for help. 

Then you should have posted to Community Cafe, which is where I'm moving your post.

> Truth is, we have the same multimedia capabilities now as we did in Dapper.

Does the easy codec installer not count? How about the ubuntu-restricted-extras metapackage? The great improvements ffmpeg has seen?

---

### Post by freeflyer57 on 2007-08-18
It takes time to get these things working. If it came out of the box, then any average joe user could use linux. I enjoyed the challenge of setting up my computer. It really lets you appreciate what you have.

---

### Post by Steveway on 2007-08-18
It works here.
There seems to be a userproblem on your side.
I use Mplayer and it handles every videofile I throw at it.
Do you have all codecs installed?
Back in my windows days I also tried the Mediaplayer-classic but I much preferred Mplayer because it was lighter on my systemressources and it played everything I had.

---

### Post by picpak on 2007-08-18
I've rarely ever found a multimedia file that Ubuntu can't handle. I don't have a DVD player, however, which may make a world's difference.

---

### Post by Freddy on 2007-08-18
So you dislike GNU/Linux and Ubuntu for not letting you perfectly stream vob files from you windows machine? Have you tried the other way around?

---

### Post by Damanther on 2007-08-18
I don't have a problem doing any of the items you have listed.

Ubuntu and most other Linux distro don't have all these things enabled "out of the box", but I was able to get most of it working with mplayer, kaffeine, k3b, etc without a lot of hassle.

There might be a distro out there that comes with all this enabled from the start, but I would imagine it would not be free. Along with some others on this thread I actually enjoy configuring the system to behave like I want. If I wanted an OS that made all my decisions for me I would install XP.

---

### Post by deejross on 2007-08-18
Freddy: First, I don't "dislike" GNU/Linux at all, in fact, I support it's movement into the desktop world and keep up with Ubuntu development. I am subscribed to the Planet Ubuntu feed, as well as the fridge feed. This is simply one of the things that is totally frustrating for me since I don't know as much about Linux as some of you do. I try to learn, but following tutorials, entering console commands only take you so far. If I don't know what those commands do and how they work, I can't learn from them.

picpak, Steveway: When you say you haven't had a problem with it, do you mean you HAVE streamed a DVD in folder format from a Windows share without problems (with menu support as well)? If so, how do I do that? I have all the gstreamer plugins (ugly and bad) installed already.

23meg: You are right about the easy codec and ffmeg advances, so I apologize for that statement, as I didn't take the time to think about multimedia as a whole, just the reoccurring problems I've had since Dapper.

With the responses I'm getting from everyone it seems like I'm doing something wrong, yet I've installed every version of Ubuntu since Dapper on multiple machines on multiple networks, and still have a problem with this. Again, I'm sorry if I angered anyone, but that was not my intent, only to get my frustration understood and get help.

---

### Post by treis on 2007-08-18
> **Damanther said:**
> I don't have a problem doing any of the items you have listed.

Me either.  I think the problem is the user, not the operating system in this case.

---

### Post by deejross on 2007-08-18
Dramanter: I agree that setting up your system is part of the fun. I enjoy setting up my desktop to look the way I want it to, but as far as the underlying system, I have no idea how to make it do what I want, which I'm sure is part of the problem.

---

### Post by deejross on 2007-08-18
treis: Again, I ask...what am I doing wrong? I have asked this question in multiple forums and multiple posts, and all I get is ,"user error".

---

### Post by GFree678 on 2007-08-18
Linux actually works BETTER for Multimedia playback than I've ever experiences with Windows. Even obscure formats which require scouting for special codecs are supplied with certain packages.

w32codecs + all the gstreamer plugins + mplayer plays EVERYTHING in existance. I'm not joking. You just have to have it set up first. Having said this, I had to learn this from a little trial and error, which a lot of new users wouldn't be able to take I think (no offence).

EDIT: DVD playback isn't hard either, but once again, you need the medibuntu repository. That could be the problem perhaps - the best multimedia repositories need to be added manually, and aren't referenced by default.

---

### Post by MetalMusicAddict on 2007-08-18
Sorry to hear. _NO_ player will play anything out of the box. I haven't hit one on windows, mac or linux. VLC comes close

The amount of work to get _everything_ to play on windows has been the same for me in linux.

---

### Post by Steveway on 2007-08-18
I don't do any streaming, heck I don't even have a windowsbox here.
And I don't know what streaming video could be usefull for.
If I would want to stream a video I would use Vlc, it was created for that purpose and AFAIk does it's job very good.

---

### Post by FuturePilot on 2007-08-18
> **GFree678 said:**
> 

w32codecs + all the gstreamer plugins + mplayer plays EVERYTHING in existance. I'm not joking. You just have to have it set up first..
+1. MPlayer has been able to play everything I've thrown at it.

---

### Post by deejross on 2007-08-18
As I said in my original post, MPlayer and VLC do NOT WORK when streaming video from a Windows share UNLESS you mount the share, which can only be done by editing the fstab config file. MPlayer and VLC cannot see shares "connected" using the Connect to Server feature found in the Places menu. I have not been able to test that with local media, as copying all my media to every machine I want to watch it on is not feasible. That's why I want to stream the video.

---

### Post by Freddy on 2007-08-18
> **deejross said:**
> Freddy: First, I don't "dislike" GNU/Linux at all, in fact, I support it's movement into the desktop world and keep up with Ubuntu development. I am subscribed to the Planet Ubuntu feed, as well as the fridge feed. This is simply one of the things that is totally frustrating for me since I don't know as much about Linux as some of you do. I try to learn, but following tutorials, entering console commands only take you so far. If I don't know what those commands do and how they work, I can't learn from them.

picpak, Steveway: When you say you haven't had a problem with it, do you mean you HAVE streamed a DVD in folder format from a Windows share without problems (with menu support as well)? If so, how do I do that? I have all the gstreamer plugins (ugly and bad) installed already.

23meg: You are right about the easy codec and ffmeg advances, so I apologize for that statement, as I didn't take the time to think about multimedia as a whole, just the reoccurring problems I've had since Dapper.

With the responses I'm getting from everyone it seems like I'm doing something wrong, yet I've installed every version of Ubuntu since Dapper on multiple machines on multiple networks, and still have a problem with this. Again, I'm sorry if I angered anyone, but that was not my intent, only to get my frustration understood and get help.
I really don't understand you. You say that Gnu/Linux and Ubuntu isn't ready for multimedia, which just simply isn't true. If you buy a distro like SUSE or Linspire you will get most of these encoders you want "out of box". If you grab a copy of the gratis Ubuntu, you will simply have to install them yourself.
You say that GNU/linux isn't ready for multimedia just because you can't simply do something which in Windows you can't do at all? I might be wrong on this one, but can you stream a vob file located on a GNU/Linux machine into your Window based Multimedia player?

GNU/Linux gets bashed for many other things to but most of them is simply not true, for example many flamers say that GNU/Linux sucks because you cant play Window based game perfectly, but most of them you can at least install (even if you cant play them) I have never seen a GNU/Linux game even installed in Windows.

I have some problems with a site I used to use which demands access to "Windows Media Player", but do I blame Linux for me not be able to use that site anymore, no I blame the site and the developers of it. Just because some people ignore other os's than Windows, is not and ever will be GNU/Linux fault and sorry to say theres not much we can do about it, nor now, nor in the future.

---

### Post by deejross on 2007-08-18
Freddy: You obviously replied before reading my post. In my original post, its says > I understand there are patent problems with playing these formats out of the box, and I'm not basing my opinion on that

Let me say it again. I understand why including the codecs cannot be done by default and that you have to install them yourself. I AM NOT QUESTIONING THAT. My post is based on the fact that you can't properly stream media over a Windows share. I did not mention anything about lack of encoders being my problem.

Some question why I would do this. I already mentioned the possibility of having more than one computer wanting to play media, but in my specific case, I installed Ubuntu on a spare machine and am slowly moving away from Windows, but this is one of the major things holding me back.

Also Freddy, I think it's fair to mention that I sent Netflix a complaint for allowing Windows-only users to access their "Watch Now" feature. And I do not bash GNU/Linux at all.

---

### Post by newlinux on 2007-08-18
> **deejross said:**
> As I said in my original post, MPlayer and VLC do NOT WORK when streaming video from a Windows share UNLESS you mount the share, which can only be done by editing the fstab config file. MPlayer and VLC cannot see shares "connected" using the Connect to Server feature found in the Places menu. I have not been able to test that with local media, as copying all my media to every machine I want to watch it on is not feasible. That's why I want to stream the video.

You can mount temporarily without editing the fstab using the mount command. I stream over the network from windows or other linux machines, and VLC works best for me when looking at dvds. Never ran into one I couldn't do. Although most of the time I use Myth to do all my streaming. Do you not want to mount?

All of the things you say you have problems with I do without much problem. It did take some setup. I'd like to help, but you'd have to be more specific in what you tried and how it failed.

---

### Post by synthaxx on 2007-08-18
Above is very true.

The command you'll want is " sudo mount -t cifs (or smbfs) //[server]/[share] /[mount position] "

Or you could just use the "Network" or "Connect to server" options in the places menu.

Both work without much problems for me. And as said above, linux plays WAY more for me than windows ever did.

---

### Post by Freddy on 2007-08-18
> **deejross said:**
> Freddy: You obviously replied before reading my post. In my original post, its says 

Let me say it again. I understand why including the codecs cannot be done by default and that you have to install them yourself. I AM NOT QUESTIONING THAT. My post is based on the fact that you can't properly stream media over a Windows share. I did not mention anything about lack of encoders being my problem.

Some question why I would do this. I already mentioned the possibility of having more than one computer wanting to play media, but in my specific case, I installed Ubuntu on a spare machine and am slowly moving away from Windows, but this is one of the major things holding me back.

Also Freddy, I think it's fair to mention that I sent Netflix a complaint for allowing Windows-only users to access their "Watch Now" feature. And I do not bash GNU/Linux at all.
But even though you understand the patent issues, you also say in you first post.
> One of the biggest setbacks of moving away from Windows for me is the horrible lack of multimedia capabilities with a Ubuntu install. With every release of Ubuntu, I hope more and more that this will get fixed, or at least move in the right direction to being fixed. Truth is, we have the same multimedia capabilities now as we did in Dapper. I'm not talking about MythTV or LinuxMCE when I refer to multimedia, I'm talking about the SIMPLE things, like playing a DVD, or simply watching a movie encoded with DivX or Xvid.
I can understand why you want to do this but I simply don't know if you can (I have never even giving this a thought, but with samba almost everything is possible).

And this is not even a problem, since most people won't stream vob files from a Window based system. If they dualboot they will either use a fat32 partition or use a ext3 which they then mount from Windows with a little program called something (which I cant remember) and if they have a fileserver they will of course use the more suited GNU/Linux system for their server system.

---

### Post by deejross on 2007-08-18
newlinux: Well, the main thing is the Connect To Server feature under the Places menu. Connecting to a share with all my media SHOULD be all that I have to do in order to get everything else besides Totem to play it. Even when browsing the network share without connecting SHOULD play it. I guess my real point in all of this is, if I didn't know about mounting, and fstab, and all that, I would think Ubuntu couldn't play video and that it was broken, even after I installed all the codecs and plugins.

If someone told me I had to mount it first, I would probably try using the Connect To Server feature would lead one to believe that it mounts the share, but it does not. Again, making it seem as if Ubuntu was broken.

If someone told me I have to edit fstab to make it work (since I would want it to still be there after a reboot), I would, with Nautilus, browse to the /etc/fstab file, open it up, only to find it's read-only. Since the "
Open as Administrator" script is not installed in Nautilus by default, now I have to back up do it all again from the terminal.

So a seemingly simple task turns into:

1. Open terminal (most Windows users start to quiver at this step alone)
2. Type sudo gedit /etc/fstab
3. Add the mount item into the list
4. Don't screw it up
5. Save and reboot

Why guide a new user through all that with the possibility of hosing the fstab file, when the Connect To Server feature SHOULD do all this for you anyways?

---

### Post by racoq on 2007-08-18
deejross, the  backend that ubuntu use (because gnome use it as default, for reproducing dvd and media files) is gstreamer.

I find gstreamer for reproducing DVD and other media files, a pile of crap.
I have faced many issues with this multimedia framework, and don't recommend it to anyone.


The totem default is based on this framework, and the package you have installed is totem-gstreamer

try to install via apt-get/aptitude or synaptic the following package:

totem-xine

It will remove the totem-gstramer, and install the totem-xine, and all the needed dependencies to render with the xine multimedia framework, that is far advanced.

Try after that to make shore that you have all the restricted codecs to play dvds, and XVid/DivX.

Unless u have a problem on your graphic card drivers, this will render all the DVD's you feed to your ubuntu box :)

Hope this helps

---

### Post by picpak on 2007-08-18
> **deejross said:**
> picpak, Steveway: When you say you haven't had a problem with it, do you mean you HAVE streamed a DVD in folder format from a Windows share without problems (with menu support as well)? If so, how do I do that? I have all the gstreamer plugins (ugly and bad) installed already.

I specifically said that I don't have a DVD player in my computer.

---

### Post by proalan on 2007-08-18
I can understand your frustrations but that is a weird setup. Streaming multimedia over a network theres bound to be buffer problems and seeking in particular. 

It seems a bit excessive and wasteful to run a windows box as a server for your multimedia files if your the only one accessing the media.

---

### Post by deejross on 2007-08-18
The Windows machine is my primary machine while I'm migrating to Ubuntu. That's why my media is on my Windows machine.

---

### Post by Epilonsama on 2007-08-18
Have you ever tried linux mint, it works flawlessly, it supports almots all of the media formats out of the box.

---

### Post by juxtaposed on 2007-08-18
> or simply watching a movie encoded with DivX or Xvid.

Works fine for me.

> I have a problem playing unencrypted DVD's as well.

Works fine for me.

> Totem plays them one VOB at a time, and you can forget about seeking through the DVD. 

Try opening up the video_ts folder with totem.

> The BEST media player out there, hands down is Media Player Classic. It's simple, compact, and plays everything out of the box, o

Then why do I always hear people complaining about not being able to play things in MPC?

> It even handles the DVD folder format, where all I have to do is double-click on VIDEO_TS.IFO and it takes care of it all, including the menus. The only problem is, it's written for Windows and doesn't work with Wine. It amazes me that no one has created anything like that for Linux.

VLC and Totem can both open video_ts DVD folders and play it perfectly.

---

### Post by muckblit on 2007-08-18
I did not know there was a package called ubuntu-restricted-extras.

There were how many brute force wrong opportunities in the universe before I would have guessed the following--

apt-get install ubuntu-restricted-extras

Or was I supposed to go into synaptic and keyword search on "extras"? How did I intuitively know that, and what kind of "extras" that would be, without context?

---

### Post by deejross on 2007-08-18
Cannot get VLC to even see the connected share
Totem gives me this error when I drag and drop the video_ts folder
> Could not determine type of stream

When opening the folder from the Open menu of Totem, it makes choose a VOB file.

It should be noted that in one of my replies I stated that I can play media (but not DVD's that well) in Totem. But VLC, MPlayer, (insert other media player here) WILL NOT EVEN FIND THE SHARE unless you manually mount it either by using the mount command or putting an entry into fstab.

---

### Post by racoq on 2007-08-18
deejross have you seen my post for rendering all the dvds correctly?

---

### Post by deejross on 2007-08-18
Switched to totem-xine, and right-clicking in Nautilus and opening the VIDEO_TS folder opens Totem, then closes it after about a second. Playing individual VOBs works just as it did in gstreamer, except when I open the VIDEO_TS.VOB itself, it says something about not having the correct region, though the movie is unencrypted and should not have a region attached to it.

---

### Post by sphinx on 2007-08-18
The point I think deejross is trying to make is that its not that linux, can't to this or that. Its that is doesn't do it neatly or well. I whole heartedly agree.

Its not that deejross can/can't solve his problem, that is beside the point. The point is the linux experience with multimeda is substandard to that of windows.

Yes, you can get most codecs (even if the are marked 'ugly' and 'bad' in reference to quality) with a google and following directions, however it the stuff like this that I find really annoying:
> 
... and you can forget about seeking through the DVD. If I touch the seek bar or accidentally tap my mouse wheel, the movies stops and I have to watch it all over again to get back where I was. Totem's interface controls are terrible. Why on earth would you want to control the position of your movie with the mouse wheel? Don't you think it makes more sense to control, say, the volume with the mouse wheel instead?


Here, here deejross. I agree. In windows its possible to seek properly while watching a movie. However I've found with Totem I get better luck if I pause the movie and then seek. But even then, results are far from certain.

So no, multimedia viewing on Ubuntu is still not 'ready'.

PS. slightly off-topic but points like juxtaposed's "Works fine for me" really bug me. What exactly does that mean? Is the linux comunity now going to issue the following press release?
> 
To all developers working on multimeda applications:
You now  no longer have to do anything more, you are asked to move onto other projects. It appears juxtaposed's problems are solved, obviously this means all movies will work on every other computer on the planet. So mission accomplished. You are no longer required.


Disclaimer:I realise is unfair to pick on juxtaposed alone, his example was just the closest to hand. I'll also admit to exaggeration in order to make my point. Perhaps even large amounts of it.

---

### Post by deejross on 2007-08-18
THANK YOU SPHINX!

I think your single post described it better than my 10 responses.

---

### Post by newlinux on 2007-08-18
> **deejross said:**
> newlinux: Well, the main thing is the Connect To Server feature under the Places menu. Connecting to a share with all my media SHOULD be all that I have to do in order to get everything else besides Totem to play it. Even when browsing the network share without connecting SHOULD play it. I guess my real point in all of this is, if I didn't know about mounting, and fstab, and all that, I would think Ubuntu couldn't play video and that it was broken, even after I installed all the codecs and plugins.

If someone told me I had to mount it first, I would probably try using the Connect To Server feature would lead one to believe that it mounts the share, but it does not. Again, making it seem as if Ubuntu was broken.

If someone told me I have to edit fstab to make it work (since I would want it to still be there after a reboot), I would, with Nautilus, browse to the /etc/fstab file, open it up, only to find it's read-only. Since the "
Open as Administrator" script is not installed in Nautilus by default, now I have to back up do it all again from the terminal.

So a seemingly simple task turns into:

1. Open terminal (most Windows users start to quiver at this step alone)
2. Type sudo gedit /etc/fstab
3. Add the mount item into the list
4. Don't screw it up
5. Save and reboot

Why guide a new user through all that with the possibility of hosing the fstab file, when the Connect To Server feature SHOULD do all this for you anyways?

I could say the same thing about many windows behaviors if I am used to doing them the ubuntu way. Although, I agree - connect to server should mount.

By the way, after editing fstab, there is no need to reboot.
```
sudo mount -a
``` will do just fine. And you should use gksudo instead of sudo if you are using gedit.

And I can play files through nautilus without mounting a windows share, but of course, it tries to copy the whole file over first instead of streaming it. But you know, windows doesn't play well with Linux either.

It shouldn't be a surprise that windows users struggle with linux concepts. They are two different OSs. If you used Linux all your life and then tried using windows to do things...

---

### Post by newlinux on 2007-08-18
sphinx,

I see your point. However the starting points are different for most Linux and Windows users. The typical Windows user never instalsl their own OS. If they did, they would have more headaches when it comes to multimedia. It doesn't all work out of the box on windows either. The preinstalled windows machines have had software and drivers added to make them work better.

---

### Post by Matthew Wiebelhaus on 2007-08-18
I know how you fell so since your using ubuntu still ill help you install elsia media center like windows media center but for windows also all you have to do is install the program and it has codecs preinstalled for it [http://elisa.fluendo.com/](http://elisa.fluendo.com/)

If you want multimedia and you have a good grapichs card or a crappy one it dosent matter i suggest sabayon it has support for every type of media file along with plenty of preinstalled software.

> **deejross said:**
> First, let me apologize. This post may anger some of you out there, and that is not my intention. This post simply lets me vent my frustration, and ask for help. 

One of the biggest setbacks of moving away from Windows for me is the horrible lack of multimedia capabilities with a Ubuntu install. With every release of Ubuntu, I hope more and more that this will get fixed, or at least move in the right direction to being fixed. Truth is, we have the same multimedia capabilities now as we did in Dapper. I'm not talking about MythTV or LinuxMCE when I refer to multimedia, I'm talking about the SIMPLE things, like playing a DVD, or simply watching a movie encoded with DivX or Xvid.

I understand there are patent problems with playing these formats out of the box, and I'm not basing my opinion on that. I'm basing my opinion on the fact that I have to really go looking for libdecss2. It's not in the multiverse like the rest of the bad and ugly gstreamer codecs. Even with libdecss2, many DVD's won't play. This, to me is a HUGE set back.

Putting aside the encrypted DVD problem, I have a problem playing unencrypted DVD's as well. I back up most of my movies because I don't like fumbling around discs when I want to watch a movie. I can't do this on Ubuntu, even with K9copy, xDVDShrink, and all the other linux DVD backup programs. But again, I'm not focusing on the encryption right now.

I have all my music and movies stored on a Windows machine. All my DVD's are in folder format, as if you copied them straight from the DVD to the hard drive. Totem plays them one VOB at a time, and you can forget about seeking through the DVD. If I touch the seek bar or accidentally tap my mouse wheel, the movies stops and I have to watch it all over again to get back where I was. Totem's interface controls are terrible. Why on earth would you want to control the position of your movie with the mouse wheel? Don't you think it makes more sense to control, say, the volume with the mouse wheel instead?

VLC sucks and I've always hated it. I've never figured out why people love it so much. I have never gotten it to play a single frame of video in three years. It, along with MPlayer and Ogle are all useless to me since neither can stream over a Windows share. The only way to get either of these two players to play anything on a Windows machine is to manually edit the fstab file and mount the shares. Clicking Places, Connect To Server doesn't cut it....which brings me to another question...Why doesn't Connect To Server actually mount the shares? That seems somewhat strange to me.

The BEST media player out there, hands down is Media Player Classic. It's simple, compact, and plays everything out of the box, on the local hard drive, or over the network from a Windows share. It even handles the DVD folder format, where all I have to do is double-click on VIDEO_TS.IFO and it takes care of it all, including the menus. The only problem is, it's written for Windows and doesn't work with Wine. It amazes me that no one has created anything like that for Linux.

All I want to do is watch movies on my otherwise perfect operating system. Is that too much to ask? This is more of a cry for help than anything. I'm sorry if I offended anyone with my comments, but you have to see my side of things. Am I doing something wrong? Is there a kill-all player that everyone is now using and I just didn't get the memo, or does no one else watch movies on their computers?

Please, help me, and thank you in advance for your comments.

---

### Post by deejross on 2007-08-18
But I don't want a media center (yet). I want a media PLAYER that has the ability to play DVD stored on a network share as if it was a DVD in your DVD drive. I didn't realize this was such a difficult concept.

---

### Post by Matthew Wiebelhaus on 2007-08-18
you can set it up to do that

---

### Post by racoq on 2007-08-18
deejross sorry insisting, but try this.

1- make shore libxine-extracodecs are installed through synaptic, 

2 - have u read this?
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

u must have libdvdcss2 an libdvdread3 installed for your PC architecture

If not follow these steps, these where the ones i followed to get my dvds running

---

### Post by deejross on 2007-08-18
> **newlinux said:**
> sphinx,

I see your point. However the starting points are different for most Linux and Windows users. The typical Windows user never instalsl their own OS. If they did, they would have more headaches when it comes to multimedia. It doesn't all work out of the box on windows either. The preinstalled windows machines have had software and drivers added to make them work better.

That's not what he's saying, nor what I'm saying. I know you have to install codecs on Windows to play anything besides a WMV. It's the same thing with Linux (well for a different reason). That's not the issue. The issue is that I have walk on eggshells around Totem so as to not touch my mouse wheel for fear of having to watch the video all over again just to get back to where I was, since seeking doesn't work. Other Totem-isms include not being able to play a DVD unless it's in your DVD drive. These are all Totem problems. Now, being forced to use Totem because VLC and MPlayer can't see the files unless its actually mounted is another problem.

---

### Post by Matthew Wiebelhaus on 2007-08-18
You need w32codecs also that has support for all

---

### Post by deejross on 2007-08-18
Yes, I installed the extracodecs, and yes I followed the guide, and yes DVD's work in my DVD drive, and NO that's not the issue. The issue is that If I copy a DVD to my hard drive or to another machine I cannot watch it as if it were in my DVD drive.

---

### Post by deejross on 2007-08-18
It should be noted, that thanks to racoq, switching to totem-xine from gstreamer actually lets me seek through individual VOB files. So thanks for that tip, racoq.

---

### Post by Matthew Wiebelhaus on 2007-08-18
Vlc Media Player

---

### Post by deejross on 2007-08-18
> **Matthew Wiebelhaus said:**
> Vlc Media Player

[SIZE="7"]NO[/SIZE]

How many times do I have to mention this VLC DOES NOT WORK CORRECTLY. READ MY POSTS. I'M GETTING TIRED OF REPEATING MYSELF!

Let's recap, all my posts regarding VLC, shall we?
> VLC sucks and I've always hated it
> MPlayer and VLC do NOT WORK when streaming video from a Windows share
> Cannot get VLC to even see the connected share
> VLC, MPlayer, (insert other media player here) WILL NOT EVEN FIND THE SHARE
> VLC and MPlayer can't see the files unless its actually mounted

Please READ before POSTING

---

### Post by tact on 2007-08-18
You need to give a lot more information on the exact setup and what you are doing if you want real help in sorting your problem.  Specific info from ground up.  As well as a clear statement of what you want to happen, what you tried so far, and whats going wrong.

I just did a quick skim of the few pages so far and there are more side-tracks than "stick to the facts" talk here so far - so its not that clear to me.

Example - assuming what you want is:
- play media files that sit on a WinXP box across the LAN on your ubuntu box.
(did I understand that correctly?)

There are so many places this can turn to custard that blaming ubuntu in your initial self-confessed venting is pretty short sighted.  So to the facts please.  What do you want help with?

Some detail that might help diagnose (if the above is a correct guess what you want to do):
- the WinXP box.  IP address and subnet?  LAN connection speed?  via wifi or cabled?
- the ubuntu box (as above)
- the LAN at home.  apart from the two PC's mentioned is it loaded by other machines/processes?

---

### Post by aysiu on 2007-08-18
VLC works correctly for a lot of people. Unfortunately, it doesn't work correctly **for you.**

Even back when I was using Windows, had to reinstall, and couldn't track down my InterVideo WinDVD installer disc, I used VLC for Windows, and that was the only way I could play DVDs.

If you want to make this thread about general trends, stop focusing it on your sole experiences. If you want to make this a support thread for your particular set-up, let me know and I'll retitle the thread and move it to a support area.

---

### Post by newlinux on 2007-08-18
> **deejross said:**
> That's not what he's saying, nor what I'm saying. I know you have to install codecs on Windows to play anything besides a WMV. It's the same thing with Linux (well for a different reason). That's not the issue. The issue is that I have walk on eggshells around Totem so as to not touch my mouse wheel for fear of having to watch the video all over again just to get back to where I was, since seeking doesn't work. Other Totem-isms include not being able to play a DVD unless it's in your DVD drive. These are all Totem problems. Now, being forced to use Totem because VLC and MPlayer can't see the files unless its actually mounted is another problem.

I wasn't trying to restate what he said, so I don't know how you can say what I was saying was or wasn't what you or he are saying.  I was simply making another point. He started off his point saying linux can't do this or that easily, which you have said also. My point was compared to windows from the same point, the level of difficulty for getting things to work for MOST people isn't that different. Read what I wrote more carefully. I wasn't just talking about codecs (in fact, I don't think I mentioned codecs--I was speaking more generally). My point is partially about basing what should work easily  on how windows works out of the box. For an accurate comparison you have to start at the same point. 

Believe me, I see your point, and don't entirely disagree. 

Judging by your escalating level of frustration, perhaps you should try something else. You don't seem to want to listen to any posts objectively, you just want to keep restating your frustrations. It isn't what you want. Live with it, fix it, or leave it.

---

### Post by deejross on 2007-08-18
Since there seems to be ALOT of confusion, so let me start from the beginning, to hopefully clear the air.

I have 5 drives installed on a Windows XP Professional machine, which is my main machine at the moment. I have set up shares for each drive and created the user, "linux" for security on those shares. These shares hold mostly video in Xvid/Divx format, though I have several backed up DVD's as well, which have been unencrypted.

I have another machine which I have installed Ubuntu Gusty, which I'm using right now. I have installed all the gstreamer plugins and w32codecs, libdecss2, libdvdread3. I can stream Xvid/Divx files from the XP machine with Totem without a problem. I can watch the individual VOB files in the VIDEO_TS folders of the DVD's located on the XP machine, but could not seek through the files until I switched totem to using Xine instead of gstreamer. I should also note that all the Xine plugins have been installed as well. I can now seek through the individual VOB files, but I cannot get totem to treat a DVD folder as an actual DVD (with menus). Right now, to watch a full DVD from the XP machine, I would have to create a VOB playlist in Totem.

I cannot use VLC, MPlayer, Ogle, or gXine, as they do not have the capability to browse or stream a Windows share. Using the Connect To Server feature from the Places menu has no effect on the ability of these programs to play the files. The only way to use these programs is to manually use the mount command or edit the fstab file. This is the problem. You should not have to even touch the terminal. The Connect To Server feature should do this for you, but it does not actually mount the shares, it simply provides a shortcut using the smb:// protocol.

The actual network configuration shouldn't be related to this problem, but for the sake of providing as much information as possible, I will include it:

XP machine (192.168.1.101, 255.255.255.0)
Ubuntu machine (192.168.1.102, 255.255.255.0)

Both machines have static IP addresses with the Gateway being 192.168.1.1. Everything is wired and speed is gigabit everywhere (except the modem, of course).

This should be pretty self-explanatory, but if I missed anything, or you have a question about the configuration, let me know.

---

### Post by deejross on 2007-08-18
newlinux: I apologize to you then, as I thought you were referring to codecs. I agree with you that working with Windows forever, then using Linux presents quite a few problems because now you have to learn an entirely new operating system.

And you were right about my increasing level of frustration. Which was caused by having to repeat myself over and over again because people were not reading my posts. In fact, most of them seemed to just read the subject of the post, then immediately started flaming me for saying such a thing. Those that didn't, simply replied that "It worked for me." Well, I'm glad for that person and all, but what worked? Playing a DVD in your DVD drive? Over a network? From you brain implants? What?

Then there was yourself and very few others that actually wanted to help me and took the time to actually read the post before replying. And then tact said:
> I just did a quick skim of the few pages so far and there are more side-tracks than "stick to the facts" talk here so far

This is the point at which I realized that the direction of this post has gone down the wrong road and that I was starting to actually get upset. So I did what he suggested and rewrote the post describing the exact problem along with a list of what I have tried. So from now on, I will try to respond with clear and concise messages to keep the trolls and flamers away, and keep the real helpers here.

---

### Post by sicofante on 2007-08-18
This thread is like a Marx Brothers movie. :-) Maybe Deejross is not the best writer on the planet, but most replies seem to ignore the main facts of his troubles. Sorry that I find it funny.

Deejross points out a design bug when he says Connect to Server doesn't mount the Windows share. If Nautilus sees a share EVERY piece of software in the system should see that share. It shouldn't be up the each app to know about that and it shouldn't be necessary at all to edit fstab or issue mount commands at the terminal. Since Gnome is a desktop environment, every application running in the environment must be given the same knowledge about available filesystems. Current behaviour is clearly inconsistent.

However, that has little to do with the state of the art of multimedia in Ubuntu. Maybe that exaggeration is what has led this thread to so much confusion?

---

### Post by deejross on 2007-08-19
I have to admit that when I first wrote this thread, I was frustrated and unloaded. I didn't really know what the exact problem was. The title of the thread was not very well thought out and probably had something to do with it. Now I do know what the problem is. And I think what you said about every program seeing what Nautilus sees is what I'm really trying to say in the end.

---

### Post by CarpKing on 2007-08-19
If you're looking for something like Media Player Classic, the closest on Linux is probably SMplayer (not in the repos as far as I know).  

[http://www.getdeb.net/app.php?name=SMPlayer](http://www.getdeb.net/app.php?name=SMPlayer)

---

### Post by blastus on 2007-08-19
[quote=deejross]Even with libdvdcss2, many DVD's won't play[/quote]

Which ones won't play?

---

### Post by newlinux on 2007-08-19
deejross:

no worries. I wish I could help more, but the problem you have with nautilus and not mounting really should just get fixed. I don't know what this entails, so I won't comment on why it doesn't just mount.

As for the problems with the players- I use mostly myth and vlc--which isn't working for you, which I can understand because I know others have had problems with them. With Myth you would need to mount as well, but the internal player does great with dvds.

I think the responses you got had a lot to do with the thread title - at least the "it works for me" responses, which I contributed too as well... For me it was more of comment saying I think Linux is ready for Multimedia (the it works for me comment), but certainly not without caveats. 

This is probably more effort than it is worth, but you can actually install VLC on the windows side, and set it up to stream to any client that do read rtp or http video streams over your home network (such as VLC and mplayer--in VLC's case, this solves the need to mount problem). You can set it up as a video on demand. Not sure how well dvd menus are supported this way however. I would only do this if you can't get anything else to work.

---

### Post by 3rdalbum on 2007-08-19
Since I haven't used Windows for much at all, it sounds strange to me that one would drag and drop the files and folders from a DVD straight onto the hard disk and play it that way. Whenever I want to do that sort of thing, I use Gnomebaker to make a disc image. That way, I can easily play it in VLC (which can read DVD images), burn it back to disc, mount it properly etc, and don't have to worry about accidentally losing files. If I want to, I can even encrypt the disc image.

However, I know that Windows and Windows programs would have a lot of trouble playing directly from a DVD image; so I guess this is just one of those things where it's better to do the platform-specific way. When on Linux, do as the Linuxians do.

---

### Post by tact on 2007-08-19
> **sicofante said:**
> 
Deejross points out a design bug when he says Connect to Server doesn't mount the Windows share. If Nautilus sees a share EVERY piece of software in the system should see that share. It shouldn't be up the each app to know about that and it shouldn't be necessary at all to edit fstab or issue mount commands at the terminal.

Granted that "Connect to server" does not mount a windows share.

That this is a "bug" is your opinion based on an expectation that some piece of software does not do what you think it should.   Is it not better to learn what the software was intended to do, learn, and realise that its not the tool for the job at hand here.  No need to press upon the software your notion of what you'd like it to do.

That one should not have to edit fstab or issue a mount command in terminal is again your forcing your expectation on a tool.

Not a flame.  An explanation of a thinking process.  "I want to drive in a screw.  I pick up a hammer for the job because I feel a hammer should be able to do this task.  It may get the screw in but I need to lodge a hammer-bug report because in the process of driving in the screw the hammer mashes the head of the screw.  Hammers should not mash screw heads when used to drive screws.

Next post.

---

### Post by Iarwain ben-adar on 2007-08-19
Didn't read the whole thread, so sorry if it is already said.

I play my dvd folders via Codeine. The thing you have to do is go to "Settings" and then the "Media" tab.
There you will see 2 paths (can't remember them as i am not on linux atm), change those to the dvd folder path. You have to change it every time you watch another movie, but it works.
Then just press the "Play" button, and select "from DVD".

That's how i do my stuff xD

Btw, if you can't watch encrypted dvd's (i can't either) i use Windows (dualboot) with DVDDecrypter. Rips the movie to harddrive, so i can use DVD-RIP (linux program) to encode it to a 850mB ogm file with hardcoded subs :)


Iarwain

---

### Post by tact on 2007-08-19
"Connect to server" does not MOUNT a remote SMB filesystem.  It creates a shortcut to the location basically.  Thats it.  Thats all.  

Just as when browsing windows shares using a windows machine -  does not "map network drive".  

Some linux programs written specifically with acessing SMB shares in mind MAY have the ability to use that link and when you double click on (for example a document) it may open in your wordprocessor application just fine.  When you do a "file save" perhaps you can navigate to a remote SMB share and save a file cross the LAN.

Many linux programs will not be able to do this.  They will require you to mount the folder on the local filesystem.  

SAME THING happens in windows-land.  In windows-land MANY programs NEED you to "map network drive" on a remote share before they can open files on the share, or save to the share. 

Summarising:
Some linux programs need a remote folder mounted before it can be used effectively.

Some windows programs need a remote folder to be "mapped to a local drive" before it can be used.

Some linux programs may be "aware" of SMB shares and not need remote folders mounted.

Some windows programs may be "aware" of shared folders and not need the remote folders "mapped to a drive".

Ok with that?

Next post....

---

### Post by chewearn on 2007-08-19
My 2 cents worth:

Tackling the issue of nautilus not mounting a SMB share, when it is supposed to be "mounting", I hack out a simple bash script:

```
#!/bin/bash
gnome-terminal -x sudo -p "User's password: " mount -t smbfs -o username=<foo> //<servername>/<folder> <mountpoint>

```Copy/paste this to a text file with .sh extension; make the file executable.

Replace <foo> with the login username.  If there is no login username required, just remove "-o username=<foo>" from the line.
Replace <servername> and <folder> as per your SMB shares.
Finally, replace <mountpoint> with your choice location in your ubuntu file system.  I simply use a directory in my home.

Then, its simply doubleclick on the file to launch.  You will be prompted for the User's password (for sudo), followed by the SMB password (if any).

A second script for umount:

```
#!/bin/bash
gnome-terminal -x sudo -p "User's password: " umount <mountpoint>

```Since I only have a rudimentary proficiency in bash, please excuse the "dumb" codes.  ;)

---

### Post by tact on 2007-08-19
For the sake of testing I tossed a full length movie in AVI format and a ripped DVD full length movie (in its own subfolder), and a word document - in a shared folder on a spare WinXP laptop.

The spare laptop and my laptop are both connected via wifi to a home hotspot.

My laptop is running Feisty but with the latest kernel 2.6.22-9 generic

If I use "connect to server" to access the shared folder in the XP laptop:
- I can see the shared folder.  I can see the word doc, the AVI and the folder containing the DVD.
- If I double click on the word document it opens in OO.o
- If I double click on the AVI or use "open with" to open with other video players nothing much happens.

Obviously Open office does not need the remote folder to be mounted.  The video players (all of them I have) are not so capable in this area.

If I use the mount command:
```
sudo mount -t smbfs //chrisk/Neil /media/iso
```

Then open the mounted winXP folder:
- double click on the word doc and it opens in OO.o
- double click on the AVI (or use right click and  "open with") it plays beautifully in all of my video players.
- the ONLY application I have that can open a "folder" as if it were a DVD is VLC and so in VLC if I navigate File>Open Directory> and navigate to /media/iso the DVD plays with full menus and no issue.
- if I just right click on VOB files of the DVD they play in media player or gxine but no menus etc.

So the word would seem to be....get over any emotive "should not have to mount a folder" feelings.  Learn how to do it without editing fstab is you do not want the mounts at every boot.  Learn how to do it in fstab if you want the mounts permanent.

Need more help doing things the right way?  Just ask.

---

### Post by tact on 2007-08-19
> **AstalaVista said:**
> My 2 cents worth:

Tackling the issue of nautilus not mounting a SMB share, when it is supposed to be "mounting", 

Again - is nautilus really "supposed" to be mounting a SMB share when you are browsing or using "Connect to server"?

No.   

Just like winXP does not mount remote shares when you are browsing.  You have to take further steps in WinXP to "map network drive".

No different in linux using nautilus.  You can browse shares, you can create shortcuts to shared resources (Connect to server).  But you have to take extra action to mount a share.

Lets try to NOT call things a bug that are not bugs.  Its the normal function.  

Want to mount a remote filesystem?  The tool is "mount", not "Connect to server".

---

### Post by aysiu on 2007-08-19
Since this has turned out to be more of a support thread, I've retitled it and moved it to the support forums.

---

### Post by chewearn on 2007-08-19
> **tact said:**
> Again - is nautilus really "supposed" to be mounting a SMB share when you are browsing or using "Connect to server"?

No.   

Just like winXP does not mount remote shares when you are browsing.  You have to take further steps in WinXP to "map network drive".

No different in linux using nautilus.  You can browse shares, you can create shortcuts to shared resources (Connect to server).  But you have to take extra action to mount a share.

Lets try to NOT call things a bug that are not bugs.  Its the normal function.  

Want to mount a remote filesystem?  The tool is "mount", not "Connect to server".

Did I call it a bug anywhere?  :confused:  I'm just implying that a user more familiar with Windows will assumed the "Connect to server" == "Map network drive".

In Windows, you go to "Network Neighborhood" to browser your network.  In Ubuntu, you go to Places > Network.  In Windows, you "Map network drive" to mount.  It is more intuitive then for Ubuntu "Connect to Server" to mount.  Except it doesn't.

Anyway, this is not my debate.  Next time, check the postings in the thread; I'm not the person saying Ubuntu is broken.   I'm posted that one message  to help the OP with his issue.

---

### Post by tact on 2007-08-19
> **AstalaVista said:**
> My 2 cents worth:

Tackling the issue of nautilus not mounting a SMB share, when it is supposed to be "mounting"

Lets not split hairs.  What you wrote is above.  That is what I tackled.

If nautilus is "supposed" to mount but is not - then it is a bug.  Clearly implied.  You proceeded to post your way around the implied bug. (a program not doing what its "supposed" to do is a bug).


I maintain - its not "supposed" to any such mounting.  Thus not a bug.  No need for workarounds.  The need is for the fellow with the problem of nautilus not doing as he expects - to learn what it is "supposed" to do, adjust his expectations in line with the design of the tool,  and learn which hammer is needed for driving screws.  (I use the long thin-shafted hammer with the flat or cross-shaped blade to drive screws.)

Windows users simply need to associate "mount=map network drive"  ....  not "Connect to Server" - rather than say that "nautilus does not mount when I click "connect to Server" just because I think it is "supposed to".     Unfamiliar system?  learn the system before complaining the linux hammer is no good to drive screws.

Lets not say its (Connect to Server)  "supposed to" mount (as you clearly did say).  Lets say what its supposed to do - truly - create a link only.  And point the mistaken newbie to the tool they are "supposed" to use - mount.


QED.  Lets not argue that point any longer.  Thanks.

---

### Post by sicofante on 2007-08-19
> **tact said:**
> "Connect to server" does not MOUNT a remote SMB filesystem.  It creates a shortcut to the location basically.  Thats it.  Thats all.  

Just as when browsing windows shares using a windows machine -  does not "map network drive".  

Some linux programs written specifically with acessing SMB shares in mind MAY have the ability to use that link and when you double click on (for example a document) it may open in your wordprocessor application just fine.  When you do a "file save" perhaps you can navigate to a remote SMB share and save a file cross the LAN.

Many linux programs will not be able to do this.  They will require you to mount the folder on the local filesystem.  

SAME THING happens in windows-land.  In windows-land MANY programs NEED you to "map network drive" on a remote share before they can open files on the share, or save to the share. 

Summarising:
Some linux programs need a remote folder mounted before it can be used effectively.

Some windows programs need a remote folder to be "mapped to a local drive" before it can be used.

Some linux programs may be "aware" of SMB shares and not need remote folders mounted.

Some windows programs may be "aware" of shared folders and not need the remote folders "mapped to a drive".

Ok with that?

Next post....

I sooo wish every explanation about bad design in Ubuntu didn't used Windows as a justification... :-( Linux will never be better if all we need to rest satisfied is "the same happens in Windows".

I said this is a DESIGN bug (both in Windows and Gnome, if it makes you feel better). The Gnome environment is supposed to grant same access and visibility to every piece of hardware out there to all the applications. If Nautilus (which is a central piece of software in Gnome) can see the share, then any app should see it. It's that simple.

Is this my personal opinion? God, sure! Is it just arbitrary or fanciful? You decide.

---

### Post by racoq on 2007-08-19
> **deejross said:**
> It should be noted, that thanks to racoq, switching to totem-xine from gstreamer actually lets me seek through individual VOB files. So thanks for that tip, racoq.

you are are welcome :) As i have said keep away from gstreamer, i have many issues with it and much users have also. I think that Ubuntu devs should replace gstreamer with xine, as the default multimedia framework, since its far more stable, and advanced.

[QUOTE=deejross]
Yes, I installed the extracodecs, and yes I followed the guide, and yes DVD's work in my DVD drive, and NO that's not the issue. The issue is that If I copy a DVD to my hard drive or to another machine I cannot watch it as if it were in my DVD drive.
[/QUOTE]

Ok, i think i have understood your point. You can try a quick tip (although i do not test it but i think it may work), why don't you install xine-ui, it is in the repositories and although its not as pretty as the alternatives (it supports skins so you can fix that),  it is the official multimedia player of the xine project, and it has worked me on some points where others have failed. It's a damn stable multimedia player, and reads almost anything that it supports.

You can select multiple sources for your media content, for instance browse your DVD's on Disk, and it haves an SMB button that allows you to select multimedia content on a network (Open> location > click the SMB button), and xine-ui will stream it. I don't have an DVD on my disk to test your issue, but i think xine-ui can play your dvd's on disk, as it was on your DVD drive.

---

### Post by deejross on 2007-08-19
I finally broke down and edited my fstab and added the shares using cifs. Although, I have a question. When you enter the share's location, (\\server\share) you can also add a directory in the share to mount to, BUT only one level it seems. Is this normal? In other words, if I have this as my share name, "\\server\share\dir1" it works, but if I do this, "\\server\share\dir1\dir2" I get an error saying it couldn't find the share. Is this a limitation of mount/cifs, or a bug?

By the way, mounting the shares and using VLC, I can now watch the DVD's as expected, but since so many people swear by VLC, maybe I can get some help with VLC-releated problems. One of the problems I reported two years ago seems to still be in VLC today.

In the settings window, there are options for default volume, normalizing, equalizer, etc. Why is it that after saving those settings, I still have to set them manually in the extended interface every time I open VLC?

Another VLC problem I reported two years ago, which it still has: If I set the volume up and down shortcuts to use my mouse wheel, the mouse wheel still controls the position of the video, and does not affect the volume at all.

Another problem I just found today is that if you set "Show interface with mouse", which says that when you are in fullscreen and move the mouse to the edge of the screen, it show the controls. Instead it actually shows all the open windows, including the regular VLC window (which is just a big empty box) with the video behind it all.

Again, these problems, except for the last one, have been reported over two years ago and have not been fixed. I find it hard to believe that this is the way it is designed. So does anyone have a workaround for these?

Thanks

---

### Post by tact on 2007-08-20
> **sicofante said:**
> I sooo wish every explanation about bad design in Ubuntu didn't used Windows as a justification... :-( Linux will never be better if all we need to rest satisfied is "the same happens in Windows".


Your comment above pre-supposes that there is a fault in design (of both windows and ubuntu - as you concede elsewhere).   You cannot argue from a presupposition like that.  If you don't like how something in the free operating system you use works - look for a channel you can use and make a suggestion as to how it might work better.   People will love you for that.

> **sicofante said:**
> 
I said this is a DESIGN bug (both in Windows and Gnome, if it makes you feel better). 

Your opinion.  I like how it works.   I like it that shares are NOT mounted just because I browse them.  I like having to make a deliberate decision before any share is mounted.  I like being able to browse and add "bookmark" type links to specific shared folders so I can get back therre quickly and easily - with no changes to my physical system config.  I think it works right in windows and ubuntu.   My personal opinion.   

As I also pointed out, I thought very clearly, that perhaps its at the application level that there may be fault (if indeed there is any design fault).  Because some APPLICATIONS (eg OO.o) can open documents on a share thats not mounted - some other applications cannot.   

Are you so right and expert as to be able to deem its a flaw in Gnome, not individual applications?  From a purely logical perspective, no programming knowledge needed, it would seem that if SOME applications can work with unmounted shares (OO.o) then perhaps the problem is not with Gnome at all.  Perhaps its on the other individual applications?  

Your proclaiming that its Gnome that is ***supposed*** to do such & such.... and fails to do what its ***supposed*** to do because some multimedia applications cannot play videos unless a share is deliberately mounted - begins to look shaky.   Care to back up a little?

> **sicofante said:**
> 
The Gnome environment is ***supposed to*** grant same access and visibility to every piece of hardware out there to all the applications. If Nautilus (which is a central piece of software in Gnome) can see the share, then any app*** should*** see it. It's that simple.

That term again.   Gnome is ***supposed*** to do something you think it should do.   

Whats Gnome ***supposed*** to do?  May I suggest reference to documentation?  I refer to documentation because this would be the ONLY authoritative statement of what Gnome is, or is not, ***supposed*** to do.

If its not doing what is documented, then it is not doing what it is ***supposed*** to do.  Its got a bug.  Your diligent efforts and sweat to determine this and report it appropriately will do the community so much good.  Go for it.

If it IS doing what it is ***supposed*** to do (according to documentation), and that something it does is not to your liking - then:
- we have something different to a bug.  
- we cannot say its not doing what its ***supposed*** to do
- we can suggest improvements.  You take the lead and do so and the community benefits so much for your efforts.  Thank you.

> **sicofante said:**
> 
Is this my personal opinion? God, sure! Is it just arbitrary or fanciful? You decide.

Agree with you totally - Its your personal opinion of how a piece of software should work.  Is it ***supposed*** to work your way?  No.  Its ***supposed*** to work how it was written to work.  

Is your conception of how it ***should*** work fanciful or arbitrary?  I didnt say so.  I just do not think its a clever thing for anyone to label software as "not doing what its ***supposed*** to do" unless its got a bug.  Its a very big (foolish) call to say its "not doing what its ***supposed*** to do" - just because it does not work the way YOU might like it to work.  So presumptious and pompous!

As noted above there are channels to submit suggestions for changes in software.  Look for them.  Contribute to the betterment of GNU/Linux by making intelligent suggestions rather than trying to impose your own personal opinions on a piece of work - insulting anyone involved by saying that its ***supposed*** to work in some way different to how it actually works.

Go in peace.

---

### Post by sicofante on 2007-08-20
](*,)

Just for the record: Windows allows you to see the network from every "file open dialog", which only makes sense.

When I say that Gnome is supposed to do something I'm using simple common sense. If you think Gnome should hide the network from everything but Nautilus, fine. It's nonsense to me (and I bet for anyone not thinking geek...).

As for presumptuous and pompous... Whatever. Your username is some sort of sarcasm? You might consider stop lecturing about manners and how and where to say what. I'll voice my opinions where I decide to, thanks, and will never -EVER- read a f... manual. First rule of design: don't ask your users for a manual (documentation, whatever you want to call it). For what's worth, every time some non-geek reads in a Linux forum something remotely resembling "RTFM" Linux is closer to loose yet another user.

I'm going in peace now.

---

### Post by tact on 2007-08-21
> **sicofante said:**
> ](*,)

Just for the record: Windows allows you to see the network from every "file open dialog", which only makes sense.


Incorrect.  

My sincere and tactful apologies for (again) correcting you if you find it painful.  

Many are the times, in windows XP, I had to pause what I am doing trying to save something to a network share to open another window (windows explorer) and map a network drive to some obscure drive letter yet unused, cancel the file save dialog, reopen the dialog and navigate to the recently mapped drive letter before I can save.  All because the ***application*** was NOT able to save to the net share until it was mapped.

Using your logic I should be blaming windows for hiding the network from that application.  wot rot.

> **sicofante said:**
> ](*,)

When I say that Gnome is supposed to do something I'm using simple common sense. If you think Gnome should hide the network from everything but Nautilus, fine.


You think I am a geek defending geekiness?  hehehe...  I am the furtherest from geek one can get.  I have never written a line of code in my life!   Never will.

But still again...  you REALLY believe its Gnome hiding the network from everything but nautilus?  

Did I use the invisible font when I mentioned some apps (OO.o for example) can easily open files on shares, and save files to shares, ***without mounting*** the share first on the local file system.

Why do you persist in saying its "Gnome at fault, Gnome hiding network from applications, Gnome ***should*** do something different...."    when it is patently obvious to blind freddy that if some apps can access shares without mounting them - perhaps its not Gnome (or any other system-wide design fault as you so patently insist from your high horse).

As per my point made over and again in past posts in this thread - perhaps its just the individual apps that are not able to take advantage of unmounted network shares (though some, like OO.o and nautilus evidently can).

You are very bold if in the light of this you can still keep saying Gnome (or linux or ubuntu) are doing something wrong and  "SHOULD" behave differently.  BIG gutsy call there.

Just as in windows (its true!  not all windows apps, as you proclaim, can see unmounted network shares) some linux apps also cannot access unmounted network shares.  

Please try to understand the concept.

---

### Post by newlinux on 2007-08-21
I think you guys should just agree to disagree. This seems to be getting a little chippy.

---

### Post by sicofante on 2007-08-21
I don't know what chippy means, but you're probably right. :-)

As long as applications use the guidelines from either Windows or Gnome they should be able to benefit from the services both provide. I must admit I don't know if the apps the OP uses will make proper use of the file open dialog for Gnome. If they do and still can't see the shares, that's Gnome's fault. If a Windows app uses the system file dialog, it'll be able to see the shares.

Of course, bad behaving apps are everywhere. The more a system enforces the use of standard procedures and makes it difficult to do otherwise (as it happens with the Mac, for instance), the better.

---

### Post by chewearn on 2007-08-22
deejross,
How I managed to live with VLC as the main media player in my setup (these are simply the ways I use it; might not be what you are looking for, but you did asked ;)):


> **deejross said:**
> In the settings window, there are options for default volume, normalizing, equalizer, etc. Why is it that after saving those settings, I still have to set them manually in the extended interface every time I open VLC?

In my case, I simply don't use the extended interface.  I can do this because my PC audio is connected to a small home theater system (HTS, one of those cheap all-in-one).

a) Volume control: in my PC, I fix the audio output to a "comfortable" level; then I only change the audio thru the HTS remote control.  I also mapped the VLC volume up/down to CTRL+Arrow up and CTRL+Arrow Down.  Occasionally on some media files/sources, the audio is too soft or too loud; then I adjust those thru the shortcut keys.

b) normalizing: never found a need to use this

c) equalizer: again, I use the preset sound equalizer in the HTS; but most of the time, I prefer the "flat" sound setting.


> Another VLC problem I reported two years ago, which it still has: If I set the volume up and down shortcuts to use my mouse wheel, the mouse wheel still controls the position of the video, and does not affect the volume at all.See above about my volume shortcut key mappings.  Actually, one reason I like VLC is that it allows me to customize keyboard shortcuts.  I find that there is not enough buttons on the mouse to map all the functions that I would like to have.

> Another problem I just found today is that if you set "Show interface with mouse", which says that when you are in fullscreen and move the mouse to the edge of the screen, it show the controls. Instead it actually shows all the open windows, including the regular VLC window (which is just a big empty box) with the video behind it all.i tried the same setting once (another problem I am trying to solve); find it quite irritating as well.

---

