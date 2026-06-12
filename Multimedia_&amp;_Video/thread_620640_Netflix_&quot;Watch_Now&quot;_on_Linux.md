---
title: "Netflix &quot;Watch Now&quot; on Linux"
date: 2007-11-22
forum: Multimedia &amp; Video
---

### Post by kendalc on 2007-11-22
After a short time spent browsing the internet for possible solutions to this problem, I came across a rather absurd idea.

There are some fairly advanced Macintosh emulators out there for Linux... namely the ones on this page:
[http://www.zophar.net/unix/mac.html]("http://www.zophar.net/unix/mac.html")
My question is this: Netflix has practically promised future support for Mac on Watch Now, so could these work to watch the movies? (Firefox in Mac emulator)

Also, (a much more abstract idea), could any of those emulators run a copy of [parallels]("http://en.wikipedia.org/wiki/Parallels_Desktop_for_Mac"), which Netflix reccomends currently for watching movies on mac?

Having said all that, even if it did work, I would likely find it easier to make a 5GB partition for an old copy of Windows 98 just for Netfilx watch now...

Is there any other hope for a possible solution?

---

### Post by rbprogrammer on 2007-11-22
i'm no expert, and this is probably not the best solution depending on your resources.. but my only idea is to run a virtual machine with windows.  VirtualBox is really good i think and i use it whenever i **need** windows.  it's in the repos also..

---

### Post by rbprogrammer on 2007-11-22
just saw you had one bean which may mean you are new to linux, if you need me to explain what i just said, i will..

---

### Post by kendalc on 2007-11-22
Haha, no its in the repositories so I'm good.  I installed Ubuntu 7.1 on my computer, and I've had some luck compiling things, but apt-get & synaptic are much easier (dependencies suck).  

I checked out VirtualBox -- does it have a GUI/ can you run IE from a command line?

I have another computer running Windows -- a remote desktop might be a better idea...

---

### Post by kendalc on 2007-11-22
Oh nevermind I've got it... I'll give it a try, thanks.

---

### Post by bthoward on 2007-11-23
Have you considered giving IEs4Linux a chance?

---

### Post by johntuck on 2007-11-28
IE4Linux doesn't run Netflix Watch now movies - believe me I have tried. 
I am no expert here but is there a way to make Netflix think that you are using windows? Would be happy to read any thoughts on that.

---

### Post by BirdZerk on 2007-11-29
I was able to use "User Agent Switch" in Firefox and trick into thinking I was using IE7 and Vista, when I clicked on a movie it says that directx is required, so to watch a movie is going to require a windows environment. Dang!

---

### Post by mgroat on 2008-01-04
> **kendalc said:**
> I would likely find it easier to make a 5GB partition for an old copy of Windows 98 just for Netfilx watch now...

Before you bother with that you might want to know that "Watch Now" requires Windows XP with SP 2 or Vista.  It also requires 3GB of free hard drive space.

---

### Post by squab on 2008-01-30
I got a virtual copy of XP SP2 running on VM Ware Player that runs Netflix instant watch no problem. It seems silly to run a full virtual copy of windows just to watch internet movies but who cares. Its only 3.9g of files.

As a side note, the install has to pass windows genuine advantage in order to run Netflix's IE plugin for media player 11.

---

### Post by shinmoo on 2008-01-30
Any chance you can explain how to do that to a newbie, squab?

---

### Post by squab on 2008-01-31
I've been around Linux for a number of years but my own computer has always been windows and its only recently I've made the switch. That being said, even with my low level of experience I was able to get this working, it just will take time. Your computer can't be lacking in power either, you will be running windows and Ubuntu at the same time.

[Here's the guide I used.]("http://ubuntuforums.org/showthread.php?t=84275&highlight=vmplayer") Getting VM Player running is relatively easy but getting a image of XP with Service Pack 2 thats passed windows genuine advantage isn't as easy. Being that I legally own windows for my system, i merely installed the windows I own onto an image of a blank ide drive.

[And as proof of my success!]("http://timtom52.googlepages.com/netflixinstant.png") If you're looking at the task bar, the left box is the processor usage or my intel 2.4ghz quad core. The middle box is memory usage of my 2 gigs with the lightest color being cache (actual usage is only at ~30%). Right box is network usage which understandably is in use since its downloading video. In all, the installation of windows is at ~3gb of files on my drive.

---

### Post by shinmoo on 2008-01-31
Hm. Right now the only computer I have is one of those Everex PCs that ship with gOS installed. I'm guesing its modest 1.5GHz CPU will bottleneck me pretty badly, even with the extra gigabyte of ram I threw in. Would you recommend just doing a dual-boot?

---

### Post by misfitpierce on 2008-01-31
I think Netflix should just add support for Mac and Linux now. Linux is growing quite fast as well as mac users. They should think about it.

---

### Post by paintba||er on 2008-01-31
Does anybody else find it odd that they don't support Macs but they use them in their commercials?

---

### Post by saxuntu on 2008-01-31
what about WINE? I have no idea if it will work and haven't tried it i'm just curious.

---

### Post by squab on 2008-02-01
> **saxuntu said:**
> what about WINE? I have no idea if it will work and haven't tried it i'm just curious.

you'd never get it to work with wine. the 2 apps it needs are Internet Explorer and Windows Media Player 11, both are which are not stand alone apps are are deeply rooted in the windows OS. The only reason netflix is allowed to stream movies is because of the windows media player DRM software. Apple has no interest in letting netflix use their DRM software because they have their own movie rentals.

---

### Post by gmcalp on 2008-02-10
I actually have gotten netflix to 'sort-of' work with IEs4Linux under Gutsy.

I can get netflix to give me a video quality report (Basic) for my internet connection.. when I click on 'Play' to watch a movie/TV show, it takes me to the page where you have to download the Netflix Movie Viewer software... which I did download and installed under Wine. I was able to pass all the DRM checks that it does, but I can't figure out how to link IEs4Linux and that movie viewer software to get them to work together.

The way I got IE4Linux to work with the Netflix site is to change the User-Agent and also the Windows Version in the system.reg and the Windows setting in the user.reg (both under the ~/.ies4linux/ie6 folder).

 Here are the registry entries I put into the system.reg:

```
[SOFTWARE\\Wow6432Node\\Microsoft\\Windows\\CurrentVersion\\Internet Settings\\5.0\\User Agent]
"Version"="MSIE 7.0"
"Platform"="Windows NT 6.0"

[SOFTWARE\\Wow6432Node\\Microsoft\\Windows\\CurrentVersion\\Internet Settings\\User Agent\Post Platform]
"SV1"=hex(0):

[SOFTWARE\\Wow6432Node\\Microsoft\\Internet Explorer\\Version Vector] 
"IE"="7.0000"

[SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Internet Settings\\5.0\\User Agent]
"Version"="MSIE 7.0"
"Platform"="Windows NT 6.0"

[SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Internet Settings\\User Agent\\Post Platform]
"SV1"=hex(0):

[SOFTWARE\\Microsoft\\Internet Explorer\\Version Vector] 
"IE"="7.0000"
```

That has set it up to make it look like I am running Vista with IE7

Here is the setting I changed in the user.reg (line 2107 in my file):

```
[Software\\Wine] 1199337729
"Version"="Vista"
```

I will keep playing around and see if I can figure things out.

---

### Post by tr3wth on 2008-04-10
Events: 0x4000021F

  WmPlayerCheckBegin:          YES
  WmPlayerCreated:             YES
  WmPlayerConnected:           YES
  WmPlayerConfigured:          YES
  WmPlayerPlaybackRequested:   YES
  WmPlayerLicenseStarted:      NO
  WmPlayerLicenseStopped:      NO
  WmPlayerPlaybackStarted:     NO
  WmPlayerPlaybackStopped:     NO
  WmPlayerPlaybackReady:       YES
  WmPlayerCheckEnd:            NO
  AxPlayerCheckBegin:          NO
  AxPlayerCreated:             NO
  AxPlayerCheckEnd:            NO
  ForcedResults:               NO
  TimedOut:                    NO
  Failed:                      YES
  Crashed:                     NO

Result: 0x800300FB  
Successfully registered DLL c:\Program Files\Netflix\Netflix Movie Viewer\AxVersion.ocx
Successfully registered DLL c:\Program Files\Netflix\Netflix Movie Viewer\AxPlayer.ocx
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
fixme:seh:_abnormal_termination (void)stub
err:msi:MsiActiveScriptSite_OnScriptError script error: L"Automation server can't create object"
fixme:seh:_abnormal_termination (void)stub
err:msi:MsiActiveScriptSite_OnScriptError script error: L"'FileSystem' is null or not an object"
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled

i get this when i install the movie viewer maybe the "NO"s above are the reason it doesn't work? great job getting that far though thanks for sharing, keep us posted and good luck!

---

### Post by glacialfury on 2008-05-07
VirtualBox OSE (Opensource Edition) is available in the Ubuntu repositories, and can be installed via synaptic and probably Add/Remove Programs.

With Windows XP running in VirtualBox, I had no problems whatsoever watching Netflix videos.  Video is fine, sound is fine, and you can configure VirtualBox to use your entire screen if you install the (free) guest additions - it makes it look like you're only running Windows, when in fact Ubuntu is ticking away underneath.

Fantastic app, an easily solution, and easily setup by nontechnical users or those with little linux experience.  If you can use the Add/Remove Programs, there's not much more required.

---

### Post by StilenX on 2008-05-28
> **BirdZerk said:**
> I was able to use "User Agent Switch" in Firefox and trick into thinking I was using IE7 and Vista, when I clicked on a movie it says that directx is required, so to watch a movie is going to require a windows environment. Dang!

This sounds like a perfect solution when Mac's are eventually supported - no direct X to worry about :)

---

### Post by ccabal on 2008-07-03
Check these links out:
[http://www.desktoplinux.com/news/NS4729463290.html](http://www.desktoplinux.com/news/NS4729463290.html)
[http://linuxdevices.com/news/NS8633598605.html](http://linuxdevices.com/news/NS8633598605.html)

So there is a small linux device that Netflix is selling to download and play the movies..  SO obviously there is support for Linux for the Watch Now option,but the question is, is this some private code that is used that a normal desktop linux user doesnt have access too?  I wonder why netflix doesnt just release this for desktop users?  Anyone know?

---

### Post by Sed Levis on 2008-07-08
Hey all, 

Supernewbie here.  But I just got an update for the Mythtv frontend that handles netflix.  I don't know how to configure it and I was hoping to get some insight on how to do that as well as if it will solve the "watch now" situation.

Thanx!

---

### Post by flaggh on 2008-07-09
> **Sed Levis said:**
> Hey all, 

Supernewbie here.  But I just got an update for the Mythtv frontend that handles netflix.  I don't know how to configure it and I was hoping to get some insight on how to do that as well as if it will solve the "watch now" situation.

Thanx!

I believe the feature you are referring to is the mythflix plugin.  This only serves as a method to manage your netflix account.  It does not solve the watch now problem.

See this post for info on configuring it:
[http://ubuntuforums.org/showthread.php?p=4475204]("http://ubuntuforums.org/showthread.php?p=4475204")

---

