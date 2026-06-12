---
title: "Where to &quot;Browse to&quot; to set MPlayer as default movie player?"
date: 2010-12-22
forum: Multimedia Software
---

### Post by nrundy on 2010-12-22
How do I set MPlayer as the default movie player? Totem always opens and I do not know where to browse to to select MPlayer as the program to use.

---

### Post by mc4man on 2010-12-23
Probably would be good to say what you're looking for.

Movie means local video  files or dvd video on disk?

There's at least 4 frontends - gmplayer (the ubuntu repo default), kmplayer,smplayer, gnome-mplayer, methods may vary on that.
Or for the cli mplayer, a custom mplayer .desktop(s)

---

### Post by garvinrick4 on 2010-12-23
# Take the file you want to open and have other files like it open in same program.
# Right click on file- choose open with - and other application, choose application and
   check box that says have all other files like this to also open in this application.

---

### Post by nrundy on 2010-12-23
> **garvinrick4 said:**
> # Take the file you want to open and have other files like it open in same program.
# Right click on file- choose open with - and other application, choose application and
   check box that says have all other files like this to also open in this application.

I did this (careful to make sure the check box was selected) but it doesn't work. When I double-click a file it still opens with Totem. 

Totem sucks! It can't play anything and even when it does it plays choppy, slow, and can't resize the image to something that isn't stretched out. Useless media player. Why is this the Ubuntu default???

When online, Totem is also the default player to open for watching trailers etc.  Please guys, how can one change this? In Windows I could always select a different application, check a box, and that application would always open default. Can't I do something similar in Ubuntu? How is the system recognizing Totem as the "go to" player. How do I tell the system to go to another player by default?

---

### Post by iosuna86 on 2010-12-23
I used Ubuntu Tweak to do that. 

It's pretty useful, I recommend you to install it. Then, once you open it, go to File Type Manager and you'll get all the available extensions with their correspondent default application, which you can alter by right clicking on them.

Hope that's what you were looking for.

---

### Post by nrundy on 2010-12-23
> **nrundy said:**
> How do I set MPlayer as the default movie player? Totem always opens and I do not know where to browse to to select MPlayer as the program to use.

right-click Applications > select Edit Menus > select Sound and Video (left column) > select Movie Player (middle column) > click Properties (right column) > to the right of "Command:" is a Browse... button. Where do I go to select a different player?

Is there a "Programs" directory like there is in Windows?

---

### Post by nrundy on 2010-12-23
> **iosuna86 said:**
> I used Ubuntu Tweak to do that. 

It's pretty useful, I recommend you to install it. Then, once you open it, go to File Type Manager and you'll get all the available extensions with their correspondent default application, which you can alter by right clicking on them.

Hope that's what you were looking for.

Thanks I'll try it. But I'd still like to "learn" how to change default players from within the OS.

---

### Post by iosuna86 on 2010-12-23
> **nrundy said:**
> Thanks I'll try it. But I'd still like to "learn" how to change default players from within the OS.

OK, I think I got it.

Open Nautilus, and go to the folder in which you have the file you want to open. Right click on it, choose Properties. Then, go to the Open With tab. Add the application you want and remove the application that appears as the default one.

That way you can do it within the system without the need of an application to do so.

---

### Post by nrundy on 2010-12-24
> **iosuna86 said:**
> OK, I think I got it.

Open Nautilus, and go to the folder in which you have the file you want to open. Right click on it, choose Properties. Then, go to the Open With tab. Add the application you want and remove the application that appears as the default one.

That way you can do it within the system without the need of an application to do so.
This does work for opening files I have on the computer. But the main issue is playing content online. When I attempt play online, Totem still opens as the default even after I have performed the above operation on every single kind of "video" file I have on my computer.

It seems to me there's got to be some way to change the default player for all media player uses (ie, at least I'm hoping there is). I'm heading to the bookstore today to look for Ubuntu books that might have an answer. I've already bought some Ubuntu books, but none of them have an answer that I've found from searching through them.

thank you kindly for you effort in helping though iosuna :)

---

### Post by iosuna86 on 2010-12-24
[FONT=Verdana]No worries.

I found this:

[/FONT][FONT=Verdana]> For Mozilla based applications type "about:config" in your browser, right
click go to new > string.  Name the string "
network.protocol-handler.app.rtsp" and set the value to whatever path you use for VLC (i.e. use
/usr/bin/vlc). You may also have to add a boolean
named "network.protocol-handler.external.rtsp" as true, but usually not.
[/FONT][FONT=Verdana]
Hope that helps.[/FONT]

---

### Post by nrundy on 2010-12-24
Thanks, I'll give it a try later, gotta go to work.  You don't happen to know how to get DVDs to play do you? I just posted in Multimedia forum. Dvds play fine in Windows, won't play in Ubuntu. I'm getting frustrated with Ubuntu's inability to accomplish basic stuff :(

---

### Post by iosuna86 on 2010-12-24
> **nrundy said:**
> Thanks, I'll give it a try later, gotta go to work.  You don't happen to know how to get DVDs to play do you? I just posted in Multimedia forum. Dvds play fine in Windows, won't play in Ubuntu. I'm getting frustrated with Ubuntu's inability to accomplish basic stuff :(

I'm gonna go get some lunch, but I will keep an eye on that. I have heard stuff about DVD not working well in Ubuntu and found some solutions for some people. I will check them out later and post it here. 

I have been with Ubuntu for just about a year and it was a bit frustrating at first, but now I am enjoying it a lot.

I'll see what I can find and I will let you know about it.

Have "fun" at work! ;)

---

### Post by iosuna86 on 2010-12-24
I think that you need to install ubuntu-restricted-extras to play DVDs:

```
sudo apt-get install ubuntu-restricted-extras
```

Also, you can find some helpful guidelines here:

[http://ubuntuguide.org/wiki/Ubuntu:Maverick#DVD_Playback_Capability](http://ubuntuguide.org/wiki/Ubuntu:Maverick#DVD_Playback_Capability)

And some other SOLVED threads like these:

[http://ubuntuforums.org/showthread.php?t=1623925](http://ubuntuforums.org/showthread.php?t=1623925)

[http://ubuntuforums.org/showthread.php?t=1536685](http://ubuntuforums.org/showthread.php?t=1536685)

[http://ubuntuforums.org/showthread.php?t=1623723](http://ubuntuforums.org/showthread.php?t=1623723) (Post #4)

I see that VLC has less issues than MPlayer. 

Hope that solved your problems.

---

### Post by nrundy on 2010-12-25
I figured out the DVD thing. It wasn't restricted extras, it was the CSS crap. I had all the right stuff installed, but I needed to run a command in a Terminal I guess to activate it all or something. (I found the command in a book at the bookstore). I ran it and DVDs play now -- phew.

---

### Post by karthick87 on 2010-12-25
First, install [Ubuntu Tweak]("http://ubuntu-tweak.com/").
  Then start it up, and select File Type Manager from the sidebar. Select the Video category, and then click on the first row under File Type and scroll down and Shift + click on the last row to select all the different video formats. Click the Edit button and select your preferred video player from the list.  
  
[IMG]http://imgur.com/A7hhP.png[/IMG]

---

### Post by nrundy on 2010-12-25
I get this error when trying to install: Error: Dependency is not satisfiable: gconf2 (>= 2.28.1-2)

---

### Post by karthick87 on 2010-12-25
To install ubuntu tweak,type the following in your terminal
```
sudo add-apt-repository ppa:ubuntu-tweak-testing/ppa
```
```
sudo apt-get update
``` ```
sudo apt-get install ubuntu-tweak
```

---

### Post by iosuna86 on 2010-12-25
> **nrundy said:**
> I get this error when trying to install: Error: Dependency is not satisfiable: gconf2 (>= 2.28.1-2)

I am dealing with tons of dependency issues lately too.

I guess you could:

```
sudo apt-get install gconf2
```and then run the commands you found. 

Let's see if that works out.

EDIT: what exactly are you trying to run in the Terminal?

I also found this so that you can run it pretty much all with vlc and mplayer (from [http://theindexer.wordpress.com/2010/10/02/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/):]("http://theindexer.wordpress.com/2010/10/02/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/%29:")

Common packs: 

```
sudo apt-get install libxine1-ffmpeg gxine mencoder mpeg2dec  vorbis-tools id3v2 mpg321 mpg123 libflac++6 ffmpeg libmp4v2-0  totem-mozilla icedax tagtool easytag id3tool lame  nautilus-script-audio-convert libmad0 libjpeg-progs libquicktime1 flac  faac faad sox ffmpeg2theora libmpeg2-4 uudeview flac libmpeg3-1  mpeg3-utils mpegdemux liba52-0.7.4-dev
```

Gstreammer 0.10:

 ```
sudo apt-get install gstreamer0.10-ffmpeg  gstreamer0.10-fluendo-mp3 gstreamer0.10-gnonlin gstreamer0.10-pitfdll  gstreamer0.10-sdl gstreamer0.10-plugins-bad-multiverse  gstreamer0.10-schroedinger gstreamer0.10-plugins-ugly-multiverse  totem-gstreamer
```

Enable dvd support:
 
```
sudo apt-get install libdvdread4 && sudo /usr/share/doc/libdvdread4/./install-css.sh
```
It does not need anything else to run properly, no commands in the terminal whatsoever.


I am pasting this here so that you have more info available in case you need to install something else in the future.

---

### Post by nrundy on 2010-12-25
> **iosuna86 said:**
> [FONT=Verdana]No worries.

I found this:

[/FONT][FONT=Verdana]
[/FONT][FONT=Verdana]
Hope that helps.[/FONT]

Forgot to tell you, this did not work :(  I created the string, then restarted firefox. Went online, ran for a video and Totem played it. I then created the Bolean and restarted firefox. Tried again, Totem still. I checked my /usr/bin and found vlc.exe in there. I don't know.

---

### Post by nrundy on 2010-12-25
What exactly are the ppa downloads? Aren't those unsupported?  there's got to be some way to change the default status. Tomorrow I guess I'll try uninstalling all media players except vlc. See what happens.  Thanks so much guys for helping me thus far. So thankful.

---

### Post by nrundy on 2010-12-25
This makes it sound like there already exists a way to reset default applications. Can anybody make sense of this?  [http://brainstorm.ubuntu.com/idea/21103/](http://brainstorm.ubuntu.com/idea/21103/)

---

### Post by iosuna86 on 2010-12-27
Man, I can't come up with a solution to this.

I guess you can remove Totem and the other media players you want to get rid of so that the one remaining would be the default application to play it all.

I never found myself in this situation. I just used Ubuntu Tweak (a pretty useful app btw).

You could also install UbuntuTweak, set the default apps and then remove the UbuntuTweak package if you don't want it. 

It is weird that there aren't many threads and solutions to this issue.

Hope you can get thru it.

---

### Post by nrundy on 2010-12-29
Well I uninstalled Totem. Now I can't play Trailers and videos online at all. I click the link and nothing happens. Unbelievable!

I'll try to get this Ubuntu Tweak installed next. What a headache!  I put a brainstorm to create a Program Default selection option. And the Brainstorm was blocked because "it's already been implemented." WHAT?!?! Where the heck is it? 

[http://brainstorm.ubuntu.com/idea/21103/](http://brainstorm.ubuntu.com/idea/21103/)
[http://brainstorm.ubuntu.com/idea/26794/report_duplicate/](http://brainstorm.ubuntu.com/idea/26794/report_duplicate/)
[http://brainstorm.ubuntu.com/idea/26794/](http://brainstorm.ubuntu.com/idea/26794/)

---

### Post by mc4man on 2010-12-29
> Well I uninstalled Totem. Now I can't play Trailers and videos online at all. I click the link and nothing happens. Unbelievable!

To watch video's thru a browser plugin well then you'd need one installed.
If you removed totem then you also removed totem-mozilla

The 2 best choices atm for plugins are totem-mozilla (uses totem) or gecko-mediaplayer (uses mplayer
You should only have one installed at a time
Try (w/ totem-mozilla still uninstalled

sudo apt-get install gecko-mediaplayer

---

### Post by iosuna86 on 2010-12-30
> **nrundy said:**
> Well I uninstalled Totem. Now I can't play Trailers and videos online at all. I click the link and nothing happens. Unbelievable!

I only have VLC on my system and everything runs smoothly.

Just install VLC with the following:

```
sudo apt-get install vlc vlc-plugin-pulse mozilla-plugin-vlc libavcodec-extra-52
```[FONT=Verdana]

From: [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

Ubuntu Tweak will let you manage the default apps easily. The thing, as you said, is that Ubuntu should have this by default. It sort of does, but it does not work so good.

I hope you can finally manage to get it all to work.
[/FONT]

---

### Post by nrundy on 2010-12-30
Iso, I didn't have the mozilla-vlc plugin. So I installed it. I reinstalled totem earlier today. How do I get VLC-plugin to default for internet video?  I used karthick's sudo commands and installed Ubuntu Tweak as well, but I can't find it. Where do I go to open the program?  What do you advise now for best way for setting VLC as default media player?

---

### Post by nrundy on 2010-12-30
Okay, I figured out how to open Tweak - Edit menus to show System Tools.   I set all Video stuff to VLC instead of "Movie Player." I verified I have all VLC plugins installed. But when I try to play a video online (one that plays with WMP in windows) Totem still opens. I can't get VLC to open. I uninstalled Totem, tried again. But now nothing opens when I click the link.  Tweak shows VLC as the "Associated Application" for every single Video listing present, including Window Media Video. Am I missing something?

---

### Post by iosuna86 on 2010-12-31
> **nrundy said:**
> Okay, I figured out how to open Tweak - Edit menus to show System Tools.   I set all Video stuff to VLC instead of "Movie Player." I verified I have all VLC plugins installed. But when I try to play a video online (one that plays with WMP in windows) Totem still opens. I can't get VLC to open. I uninstalled Totem, tried again. But now nothing opens when I click the link.  Tweak shows VLC as the "Associated Application" for every single Video listing present, including Window Media Video. Am I missing something?

I don't know what's wrong. Everything seems perfect. Can you give me an example of the video you want to open/play with Firefox? Just paste the link and I will see what my laptop does.

---

### Post by nrundy on 2010-12-31
mms://media1.maxmovie.com/movieinfo/image/av/Maxzhanglover_bon_trailer.wmv

mms://media1.maxmovie.com/movieinfo/image/av/Maxzhanglover_l_mv.wmv

---

### Post by iosuna86 on 2010-12-31
> **nrundy said:**
> mms://media1.maxmovie.com/movieinfo/image/av/Maxzhanglover_bon_trailer.wmv

mms://media1.maxmovie.com/movieinfo/image/av/Maxzhanglover_l_mv.wmv

I am having trouble viewing those videos too.

When I typed in that address and hit "Enter" I got a "Launch Configuration" window in which I got the option to choose the default app to open those files from now on. Somehow, the default one was Totem!!! and I don't even have it installed on my laptop!

So, I selected VLC as the default app and now VLC opens those files, BUT....

It doesn't play the file...

What the hell is wrong here???

---

### Post by mc4man on 2010-12-31
> It doesn't play the file...
No reason it shouldn't (plays fine here from location in browser.

when opening vlc thru the browser you won't get any error messages, try from a terminal and see what it says.
vlc mms://media1....

They're just wma2 w/ wmv3 video, nothing that should cause issues

---

### Post by nrundy on 2011-01-01
> **iosuna86 said:**
> 

When I typed in that address and hit "Enter" I got a "Launch Configuration" window in which I got the option to choose the default app to open those files from now on. 

What the hell is wrong here???

Iso, I do not get a "Launch Configuration" when using Ubuntu. But I do when using Windows. I want to get a "Launch Configuration" from Ubuntu so I can select VLC. I think my first step is to get a Launch Configuration from my comp. Then I'll worry about getting VLC to play.

Iso, make sure you have MMS installed on your comp from the Ubuntu Software Center. VLC won't play without this I don't think.

---

### Post by nrundy on 2011-01-01
Mc4Man, how did you get a "REPEAT" icon/button on your VLC player? I cannot find such an icon on my Ubuntu VLC. I don't understand why I don't have one. I have looked through all the icons and do not have one. But one does show up on my Windows install of VLC. How come I do not have a REPEAT icon on my Ubuntu install?!?!?

UHHH. If I could just get my comp to work like everyone else's, I'd be happy.

---

### Post by nrundy on 2011-01-01
mc4man, you got to help us man :)

You got VLC playing online videos and you got a REPEAT icon on VLC. Heaven! How'd you do it?

---

### Post by mc4man on 2011-01-01
> How'd you do it?
I use the 1.2+ dev version of vlc. While it may occasionally have a regression, it's far superior to the 1.1.X vlc.

You can build your own or if running maverick or natty then there is the videolan master ppa. (updates every day or so.
[https://launchpad.net/~videolan/+archive/master-daily/+index?field.series_filter=](https://launchpad.net/~videolan/+archive/master-daily/+index?field.series_filter=)

As far as your online video I'd think there should be no issue w/ the 1.1.X vlc either, as suggested run vlc from the command line to see what the problem is

Edit: please note that the mozilla-vlc-plugin is no longer supported in vlc-1.2, you must remove it. (actually best if switching to 1.2 to completely remove vlc first, in synaptic mark vlc-data for removal, all other vlc related will be removed

---

### Post by nrundy on 2011-01-01
how do I run from a terminal? I pasted the address, but nothing happens. Sorry, I'm a n00b.

---

### Post by nrundy on 2011-01-01
> **mc4man said:**
> 

Edit: please note that the mozilla-vlc-plugin is no longer supported in vlc-1.2, you must remove it. (actually best if switching to 1.2 to completely remove vlc first, in synaptic mark vlc-data for removal, all other vlc related will be removed

Thanks for this notice. With 1.2 you are talking about fixing the no REPEAT icon, right? You said I should still be able to get VLC 1.1 to working for online videos? Do you know why I do not get a "Launch Configuration" window (like iosuna86 does) to select which application I want use?

---

### Post by nrundy on 2011-01-01
mc4man, any help you could give me to get the "Launch Configuration" window working on my comp for online video play would be immensely appreciated. Thanks.

---

### Post by mc4man on 2011-01-01
> how do I run from a terminal
2 ways, though not sure about 1.1.X as far as second. (menu may have different name in 1.2

Open a terminal (Applications - Accessories - Terminal) and paste this in
```
vlc mms://media1.maxmovie.com/movieinfo/image/av/Maxzhanglover_bon_trailer.wmv

```

Ex.
> doug@doug-alienware:~$ vlc mms://media1.maxmovie.com/movieinfo/image/av/Maxzhanglover_bon_trailer.wmv
VLC media player 1.2.0-git Twoflower (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
Blocked: call to setlocale(6, "")
Blocked: call to strerror(2)
Blocked: call to strerror(2)
Blocked: call to strerror(2)
Blocked: call to strerror(2)
Blocked: call to strerror(2)
Warning: call to srand(1292991651)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:2252): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
QVariantMap DBusMenuExporterDBus::GetProperties(int, const QStringList&): Condition failed: action 
[0x8b0008c] access_mms access: selecting stream[0x1] audio (52 Kib/s)
[0x8b0008c] access_mms access: selecting stream[0x2] video (346 Kib/s)
[0x8b0008c] access_mms access: connection successful

Or open a terminal and just use 
vlc
Then click on media and 'Open network Stream' (or thereabouts, then enter the url in box, click on play at bottom of dialog box (see screen

---

### Post by nrundy on 2011-01-01
I ran it from Terminal and everything worked. Video started playing fine. No problems. Now, how do I get the "Launch Configuration" to appear when browsing the web so that I can select VLC as the player to use? Any ideas mc4man?  Thanks so much for telling me how to run from Terminal.

---

### Post by andrew.46 on 2011-01-01
Hi nrundy,

> **nrundy said:**
> Mc4Man, how did you get a "REPEAT" icon/button on your VLC player? I cannot find such an icon on my Ubuntu VLC. 

The 'repeat' icon is available at least in 1.1.5 as well...

Andrew

---

### Post by nrundy on 2011-01-01
> **andrew.46 said:**
> Hi nrundy,

The 'repeat' icon is available at least in 1.1.5 as well...

Andrew

 Hey andrew :)  About says I'm running 1.0.6 Goldeneye (Qt4 interface). My system is showing as fully up to date. I downloaded VLc from Ubuntu repository through synaptic. How did you get 1.1.5?

I just checked synaptic, it's only listing 1.0.6. And says it's fully up to date???

---

### Post by mc4man on 2011-01-01
> so that I can select VLC as the player to use?

Paste your mms... link into firefox's address bar, you should get a popup (screen 1
click on 'choose' and browse to 'file system' - 'usr' - 'bin' and highlight vlc, then click 'open' (screen 2

In the future you'll see screen 3, if desired enable the 'rememeber,,,' option

---

### Post by nrundy on 2011-01-01
I do NOT get a "popup." I paste the link into firefox and hit enter and Totem opens and starts playing the video.

I know the popup you are talking about because I get it when I browse to the link with Windows XP.

---

### Post by mc4man on 2011-01-01
> I do NOT get a "popup."
While I'm not big on the insides of firefox try this, (I set vlc as default thru the 'remember..' option so no popup would happen

In firefox go Edit - preferences - Applications and look for a 'mms' entry,
If there then either set vlc (use other) or set back to 'Always Ask..'

---

### Post by nrundy on 2011-01-01
Got it! THANK YOU, THANK YOU. Thank you so much! Can't thank you enough :)

---

### Post by iosuna86 on 2011-01-01
> **nrundy said:**
> Got it! THANK YOU, THANK YOU. Thank you so much! Can't thank you enough :)

I have been out for a day and I see you guys have made some valuable progress here.

I searched for "MMS" in Software Center and I got Gstreamer (something I already have) and Fluendo codecs (you gotta pay for them). Nothing else, and still, VLC doesn't play the file, neither from the terminal nor the browser.

I never play things from mms: but still, I want my system to work properly. Any "How-To's" on how should I configure VLC and my browser to get it all working?

---

### Post by andrew.46 on 2011-01-01
Hi nrundy,

> **nrundy said:**
> I just checked synaptic, it's only listing 1.0.6. And says it's fully up to date???

Up to date with the repository offerings, not up to date with the latest vlc :)

Andrew

---

### Post by iosuna86 on 2011-01-01
> **iosuna86 said:**
> I have been out for a day and I see you guys have made some valuable progress here.

I searched for "MMS" in Software Center and I got Gstreamer (something I already have) and Fluendo codecs (you gotta pay for them). Nothing else, and still, VLC doesn't play the file, neither from the terminal nor the browser.

I never play things from mms: but still, I want my system to work properly. Any "How-To's" on how should I configure VLC and my browser to get it all working?

Nevermind what I just said. I just had to check "Force all streams" under Codecs/MMS in VLC and wait for a couple of seconds for VLC to start streaming.

I am glad this problem is solved now.

Thanks for the help!

---

### Post by nrundy on 2011-01-01
> **andrew.46 said:**
> Hi nrundy,

Up to date with the repository offerings, not up to date with the latest vlc :)

Andrew

So the VLC people added the icon to the new version? That's cool. Now how do I get it? How come they didn't send this version to the Ubuntu repository?

How did you get the new version? Can I get it too?

---

### Post by andrew.46 on 2011-01-02
Hi nrundy,

> **nrundy said:**
> So the VLC people added the icon to the new version? That's cool. 

I will admit that I have not paid close enough attention to vlc to notice when that particular button appeared...

> Now how do I get it? How come they didn't send this version to the Ubuntu repository?

How did you get the new version? Can I get it too?

You have the flow the wrong way around :). The vlc developers prepare a release of the vlc source code and then it is up to the individual distros to take this source code and package it appropriately. I see that 1.1.5 appears in Natty btw. My own copy is compiled from the source code rather than taken from a repository and this is an option for you as well, although vlc can be a little difficult to compile. Have you had a look at the PPA that mc4man has suggested? This is the development version so some breakages may appear from time to time.

Andrew

---

### Post by mc4man on 2011-01-02
> Have you had a look at the PPA that mc4man has suggested? 

That would only be good for maverick and natty.
There are probably some ppa's for lucid though you'd want to be careful of ones that replace your ffmpeg libraries.

Otherwise[ Andrew's how-to will]("http://ubuntuforums.org/showthread.php?t=1398119") work quite fine for the 1.2+ and can be easily adapted for the current stable release (1.1.5 ?)
The only prerequisite for success is to read carefully and use copy and paste
(Though quite possible a minor change or 2 for using on lucid as far as build deps

---

### Post by nrundy on 2011-01-04
Is there a way to contact Ubuntu Developers and tell them they need to update VLC for 10.04? This would easily solve my problem. Because even VLC 1.1 has the REPEAT icon/button.  I thought LTS meant long-term support and that applications would be updated? VLC is way out of date in the repository.

---

