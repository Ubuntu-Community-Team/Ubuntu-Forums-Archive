---
title: "Medibuntu abandoned"
date: 2013-04-13
forum: Multimedia Software
---

### Post by Fende on 2013-04-13
Hello,

I've just learned that the [Medibuntu]("http://www.medibuntu.org/") repository is no longer supported :( as it is being abandoned by its current mantainer:

[https://launchpad.net/medibuntu/+announcement/11219](https://launchpad.net/medibuntu/+announcement/11219)

Will this have any effect on media capability in Ubuntu? Are there any other repositories which provide libdvdcss2, w32codecs, w64codecs, etc?:confused:

As a non-knowledgeable end-user, I'd like to know if I will have to manually remove Medibuntu from my repositories once it stops working.

Thanks

---

### Post by lisati on 2013-04-13
There hasn't been a need to add medibuntu to your sources list to install libdvdcss2  for quite some time. Have a look here: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by monkeybrain2012 on 2013-04-13
> **lisati said:**
> There hasn't been a need to add medibuntu to your sources list to install libdvdcss2  for quite some time. Have a look here: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Well how about non-free codecs and the libav-extras packages?

---

### Post by andrew.46 on 2013-04-13
> **lisati said:**
> There hasn't been a need to add medibuntu to your sources list to install libdvdcss2  for quite some time. Have a look here: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

True but I suspect that the script mentioned on that page downloads libdvdcss from Medibuntu.

---

### Post by mc4man on 2013-04-13
Even if no one takes on maintaining,  the repos will still be there so as far a libdvdcss2, the script will retrieve or users can dl & install directly from there or Videolan
w32codecs can be directly dl'ed or gotten from mplayer site

The libav extra packages from mediabuntu are almost the same as the official repo ones, I think the only difference is libfaac support. If one needed that then they'd just have to take care of themselves, either for avconv, ffmpeg, or the current repo source for shared libs can be rebuilt to include libfaac.

As far as the other more obscure packages there, the raring builds may be good for awhile, if not the again a user would have to do for themselves.

---

### Post by andrew.46 on 2013-04-13
> **mc4man said:**
> As far as the other more obscure packages there, the raring builds may be good for awhile, if not the again a user would have to do for themselves.

And once again, with users having to build or rebuild packages, multimedia guides will flourish again on the Ubuntu Forums :)

---

### Post by monkeybrain2012 on 2013-04-13
> **andrew.46 said:**
> And once again, with users having to build or rebuild packages, multimedia guides will flourish again on the Ubuntu Forums :)

You seem to be very happy about it. :)

---

### Post by andrew.46 on 2013-04-13
> **monkeybrain2012 said:**
> You seem to be very happy about it. :)

Not happy that a great resource for Ubuntu users seems to be drifting along unmaintained, hopefully somebody will take the reins and allow Medibuntu to continue and grow. My own approach to creating media packages has always been a little more hands-on though and for a time, if MediBuntu remains quiescent, this approach will be useful on these Forums.

---

### Post by andrew.46 on 2013-04-19
Borrowing from my own work here is a method of downloading and installing the windows codecs used by MPlayer (create a download directory of course):

[http://www.andrews-corner.org/mplayer.html#codecs](http://www.andrews-corner.org/mplayer.html#codecs)

I am not sure how many Ubuntu media packages look at */usr/local/lib/codecs* but the path can of course easily be modified...

---

### Post by fmouse on 2013-05-17
What's happened to medibuntu.org?  This morning I can no longer resolve packages.medibuntu.org, nor [www.medibuntu.org](www.medibuntu.org), and the IP address formerly associated with packages.medibuntu.org (88.191.127.22) is no longer pingable.

---

### Post by howefield on 2013-05-17
Probably related to [http://ubuntuforums.org/showthread.php?t=2135070](http://ubuntuforums.org/showthread.php?t=2135070)

---

### Post by fmouse on 2013-05-17
As of today (or maybe yesterday or the day before), it seems that "packages.medibuntu.org" no longer resolves, and the former IP address of the server, 88.191.127.22, is no longer pingable.  It's Gone.

---

### Post by mkarr on 2013-05-17
> **fmouse said:**
> As of today (or maybe yesterday or the day before), it seems that "packages.medibuntu.org" no longer resolves, and the former IP address of the server, 88.191.127.22, is no longer pingable.  It's Gone.

So does this mean dvd playback is now broke in Ubuntu? You run the script "sudo /usr/share/doc/libdvdread4/install-css.sh" and you get the error "wget: unable to resolve host address `packages.medibuntu.org'".

---

### Post by abovett on 2013-05-17
Has anyone with better knowledge than me got advice on what to do with systems which are currently using packages from Medibuntu? We can disable the medibuntu repositories in the sources list, but presumably that leaves unmaintained packages on the system which are not being updated and could cause a security risk if vulnerabilities are found in them.

---

### Post by abovett on 2013-05-17
Has anyone with better knowledge than me got advice on what to do with systems which are currently using packages from Medibuntu? We can disable the medibuntu repositories in the sources list, but presumably that leaves unmaintained packages on the system which are not being updated and could cause a security risk if vulnerabilities are found in them.

---

### Post by oldos2er on 2013-05-17
> **mkarr said:**
> So does this mean dvd playback is now broke in Ubuntu? You run the script "sudo /usr/share/doc/libdvdread4/install-css.sh" and you get the error "wget: unable to resolve host address `packages.medibuntu.org'".

You can get libdvdcss2 from the Debian multimedia repository: [http://mirror.home-dn.net/debian-multimedia/pool/main/libd/libdvdcss/](http://mirror.home-dn.net/debian-multimedia/pool/main/libd/libdvdcss/)

---

### Post by mkarr on 2013-05-17
Well that was easy enough. Thank you!

---

### Post by oldos2er on 2013-05-17
You're welcome!

---

### Post by oldos2er on 2013-05-17
Merged threads to keep the discussion of medibuntu in one thread.

---

### Post by abovett on 2013-05-17
It seems that packages.medibuntu.org is back up again - so maybe the outage earlier today was a temporary glitch. I note the Medibuntu website is saying "Maintainer Wanted" as mentioned but for now at least the site and the repository are back up.

---

### Post by andrew.46 on 2013-05-17
> **mkarr said:**
> So does this mean dvd playback is now broke in Ubuntu? You run the script "sudo /usr/share/doc/libdvdread4/install-css.sh" and you get the error "wget: unable to resolve host address `packages.medibuntu.org'".

You can use a debian package as has been suggested or perhaps experiment with building your own:

[http://ubuntuforums.org/showthread.php?t=2146227&p=12652448#post12652448](http://ubuntuforums.org/showthread.php?t=2146227&p=12652448#post12652448)

---

### Post by MadmanRB on 2013-06-03
[https://launchpad.net/medibuntu/+announcement/11219](https://launchpad.net/medibuntu/+announcement/11219)

Surprised this went under the radar considering how critical medibuntu is.
While things like gstreamer do okay we do need things like libdvdcss for certain DVD's so I hope a new maintainer comes before 13.10 or 14.04

---

### Post by howefield on 2013-06-03
> **MadmanRB said:**
> [https://launchpad.net/medibuntu/+announcement/11219](https://launchpad.net/medibuntu/+announcement/11219)

Surprised this went under the radar considering how critical medibuntu is.

Critical isn't really the word :)

As for under the radar.. [http://ubuntuforums.org/showthread.php?t=2135070](http://ubuntuforums.org/showthread.php?t=2135070)

---

### Post by monkeybrain2012 on 2013-06-03
This has been posted in the multimedia forum over a month ago. [http://ubuntuforums.org/showthread.php?t=2135070](http://ubuntuforums.org/showthread.php?t=2135070)

I agree that this is critical for new users who expect basic multimedia support like dvd and w64 codecs from Ubuntu. On the other hand, for more experienced users this may not be a big problem. I compiled libdvdcss from the tarball downloaded from Videolan (which is more updated than medibuntu)

---

### Post by howefield on 2013-06-03
Threads merged.

---

### Post by MadmanRB on 2013-06-03
Yeah sorry, but this bothers me as not everyone can manually hand code this sort of thing.
Hope it will have a new maintainer as really compiling can be rather a hard thing.

---

### Post by andrew.46 on 2013-06-04
> **MadmanRB said:**
> Hope it will have a new maintainer as really compiling can be rather a hard thing.

The little mini-guide I put together for building libdvdcss actually only involves copying a blob of text and then pasting it in a Terminal window :)

---

### Post by hpsgty on 2013-06-04
[COLOR=#000000]True but I suspect that the script mentioned on that page downloads libdvdcss from Medibuntu.[/COLOR]

---

### Post by andrew.46 on 2013-06-04
> **hpsgty said:**
> [COLOR=#000000]True but I suspect that the script mentioned on that page downloads libdvdcss from Medibuntu.[/COLOR]

I am not sure if you are replying to my post or another but [my own offering]("http://ubuntuforums.org/showthread.php?t=2146227") downloads from videolan not Medibuntu.

---

### Post by MadmanRB on 2013-06-04
> **andrew.46 said:**
> The little mini-guide I put together for building libdvdcss actually only involves copying a blob of text and then pasting it in a Terminal window :)

Yeah but its a little intimidating using a terminal for a newer user, whom I consider every time.
I rather link to ppas or webpages they can link to a .deb from

---

### Post by Yellow Pasque on 2013-06-05
> Yeah but its a little intimidating using a terminal for a newer user
If the commands are given to copy/paste, it shouldn't be intimidating at all. I've had plenty of people that couldn't figure out how to add a PPA if I linked them (though the instructions are given on every ppa page).

---

### Post by monkeybrain2012 on 2013-06-05
Other than libdvdcss you also need the non free codecs from medibuntu. You can get them directly from mplayer's website.
Download the codecs package [http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)
Extract it

Create a codecs directory in /usr/lib

```
sudo mkdir /usr/lib/win64
```

Then move all the contents from your codecs package to this folder

```
sudo mv pathtocodecsfolder/* /usr/lib/win64
```

What else is left that we may need from medibuntu?  Probably just the libav -extras libraries. The libav-extras are tricky because if you compile ffmpeg (even as a shared library in /usr) they don't show up as seperate .debs so if you try to install say mplayer (or vlc) from synaptic it will insist on installing the repo's libav libraries as dependencies and use them. So in order to use your compiled versions you would have to compile mplayer (vlc ...) as well..

---

### Post by MadmanRB on 2013-06-05
Well again that requires a lot of work the end user should not have to do.
Now luckily gstreamer can do a lot of what these codecs can do, the only blind spot it seems to have is DVD's (and bluray, but linux isnt good for bluray anyhow)

---

### Post by FakeOutdoorsman on 2013-06-05
> **monkeybrain2012 said:**
> So in order to use your compiled versions you would have to compile mplayer (vlc ...) as well..

[list]
[*][Howto: Compile the development version of VLC under the latest Ubuntu release](http://ubuntuforums.org/showthread.php?t=2141949)
[*][Howto: Build the svn MPlayer under the latest release version of Ubuntu](http://ubuntuforums.org/showthread.php?t=2149564)
[*][How To Compile FFmpeg and x264 on Ubuntu](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)
[/list]

---

### Post by mc4man on 2013-06-05
The medibuntu versions of libav extra offer very little to the general user as compared to the repo extra versions, maybe just faac encoding
(the current in use libav just uses libvo_aacenc & maybe native, don't particularly care to see.

w64codecs are virtually worthless, w32codecs have some value though not as much as past days

gstreamer is ok, it's limited what libav offers & what version of libav is on Ubuntu/Debian & quality of gstreamer players which is so-so
(the next version, if it makes 13.10,  will finally offer wmal decoding & for libav likely fdk-aac, opus

As far as libdvdcss2, it's still on the medibuntu server & in any event Andrew's little script will download, build, & install it in a few minutes or less.
(as far as an ppa for libdvdcss2 while it would only take a few minutes to set up I wouldn't do so, not too sure LP would want it hosted

---

### Post by Yellow Pasque on 2013-06-05
[QUOTE=mc4man]as far as an ppa for libdvdcss2 while it would only take a few minutes to set up I wouldn't do so, not too sure LP would want it hosted[/QUOTE]

Yeah, I thought about it, but I don't know the legal ramifications of it, and I live in a country run by corporations who love their patent laws. The last thing I need is men in uncomfortable shoes knocking on my door.

---

### Post by andrew.46 on 2013-06-06
> **Temüjin said:**
> Yeah, I thought about it, but I don't know the legal ramifications of it, and I live in a country run by corporations who love their patent laws. The last thing I need is men in uncomfortable shoes knocking on my door.

I have sent the FBI your way...

:)

---

### Post by MadmanRB on 2013-06-06
Still all that is compiling, hopefully someone can get some binary packages compiled and make a new repo.

---

### Post by FakeOutdoorsman on 2013-06-06
That someone could be you. Think of it as an adventure and/or learning experience.

---

### Post by MadmanRB on 2013-06-06
No as I really dont want to compile unless it is necessary.
Right now this isnt necessary, once this repo goes down I guess I will have to.

Or I could cheat and use the debian multimedia repo:

[http://deb-multimedia.org/](http://deb-multimedia.org/)

Just use testing to make up for things.

---

### Post by monkeybrain2012 on 2013-06-06
> **FakeOutdoorsman said:**
> 
[LIST]
[*][Howto: Compile the development version of VLC under the latest Ubuntu release]("http://ubuntuforums.org/showthread.php?t=2141949") 
[*][Howto: Build the svn MPlayer under the latest release version of Ubuntu]("http://ubuntuforums.org/showthread.php?t=2149564") 
[*][How To Compile FFmpeg and x264 on Ubuntu]("https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide") 
[/LIST]


Hi,

I know these guides (thanks for the excellent ffmpeg guide, it is great help), but it seems that there are many duplicated ffmpeg because everything is compliled as static. 

Ideally I would like to compile ffmpeg as a shared library so that I can compile everything against one version of ffmpeg. I am able to compile the shared library after removing all the libav libraries. Using that  I  compiled vlc and mplayer2 and both work great. However, since the libav libraries are not compiled as separate .debs  so the package manager can't see them. If I install something in synaptic that uses, say libavcodecs, it will instead of using my compiled version, fetch another copy from the repository and use that instead.

 I am still trying to find an optimal solution, maybe building one copy of ffmpeg locally and compile everything against it (instead of making multiple copies of ffmpeg , one for each application I compile like in Andrew's guide) but also install the system libav files for installing packages from synaptic, but have to look up how that is done.

---

### Post by monkeybrain2012 on 2013-06-06
> **MadmanRB said:**
> No as I really dont want to compile unless it is necessary.
Right now this isnt necessary, once this repo goes down I guess I will have to.

Or I could cheat and use the debian multimedia repo:

[http://deb-multimedia.org/](http://deb-multimedia.org/)

Just use testing to make up for things.
  

Don't think it will work. I tried to use that to get ffmpeg (see my post above for my problem) debian multimedia provides the original ffmpeg rather than avconv, that was my motivation. : ) If all you need is libdvdcss2 it is easier to just type a few lines to compile it yourself. I mean, if you screw up your sources list you have to fix it with the terminal anyway. :)

---

### Post by MadmanRB on 2013-06-06
But I shouldn't have to.
No one should have to compile.
But since no one is stepping up I guess Ubuntu might as well be off my lists of distros now, multimedia playback is essential and if Ubuntu cant provide then its time to ditch a sinking ship.
Until this issue is fixed I will warn people off Ubuntu and suggest Mint, or Fedora or openSUSE as all them do have a repo for multimedia or install it by default.

---

### Post by Yellow Pasque on 2013-06-06
> **monkeybrain2012 said:**
> I am still trying to find an optimal solution, maybe building one copy of ffmpeg locally and compile everything against it (instead of making multiple copies of ffmpeg , one for each application I compile like in Andrew's guide) but also install the system libav files for installing packages from synaptic, but have to look up how that is done.

If you want something to use your local copy of ffmpeg, you'll have to compile it, and point it to the correct ffmpeg. A good example: [http://redmine.audacious-media-player.org/boards/1/topics/788](http://redmine.audacious-media-player.org/boards/1/topics/788)

---

### Post by MadmanRB on 2013-06-06
Well if you people are willing to compile then why not begin a new repo for the rest of us who either cant compile, dont know how to, or do not wish to.
I really dont wish to compile source code for something so trivial, its something that should be maintained by those more used to compiling.

---

### Post by andrew.46 on 2013-06-06
> **MadmanRB said:**
> Well if you people are willing to compile then why not begin a new repo for the rest of us who either cant compile, dont know how to, or do not wish to.
I really dont wish to compile source code for something so trivial, its something that should be maintained by those more used to compiling.

The Medibuntu repo is still in place and even has a section for saucy so the time has not come yet to factor it out of the Ubuntu world :)

---

### Post by howefield on 2013-06-06
> **MadmanRB said:**
> Well if you people are willing to compile then why not begin a new repo for the rest of us who either cant compile, dont know how to, or do not wish to.
I really dont wish to compile source code for something so trivial, its something that should be maintained by those more used to compiling.

Have you done anything to help sustain/maintain it ?

---

### Post by monkeybrain2012 on 2013-06-06
> **MadmanRB said:**
> But I shouldn't have to.
No one should have to compile.
But since no one is stepping up I guess Ubuntu might as well be off my lists of distros now, multimedia playback is essential and if Ubuntu cant provide then its time to ditch a sinking ship.
Until this issue is fixed I will warn people off Ubuntu and suggest Mint, or Fedora or openSUSE as all them do have a repo for multimedia or install it by default.

Doesn't Mint get libdvdcss also from Medibuntu?:confused: 

[http://community.linuxmint.com/software/view/libdvdcss2](http://community.linuxmint.com/software/view/libdvdcss2)

Fedora is probably not a good suggestion for those who think  compiling libdvdcss is too compilcated. I dual boot with Fedora, there are  common packages in  Ubuntu/Debian that are simply not in Fedora's repos (including  rpm-fusion) For example, mplayer2. I compile stuffs in Ubuntu often  because I just want to, but in Fedora I have to. [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]

Can't say about openSUSE, cause I have never used it.

BTW. I think creating a ppa is more complicated than just compiling  something for personal use. I confess that I don't know the ins and outs  of Debian's packaging rules.

---

### Post by Yellow Pasque on 2013-06-06
> **MadmanRB said:**
> Well if you people are willing to compile then why not begin a new repo for the rest of us who either cant compile, dont know how to, or do not wish to.
I really dont wish to compile source code for something so trivial, its something that should be maintained by those more used to compiling.

I assume you're just talking about libdvdcss, so it's all about legal reasons (which is why Medibuntu exists in the first place).

---

### Post by Yellow Pasque on 2013-06-06
> **MadmanRB said:**
> Or I could cheat and use the debian multimedia repo:
Just use testing to make up for things.

Debian and Ubuntu packages aren't guaranteed to be compatible in terms of dependencies, so it's a bad idea to mix them. For simple packages with few dependencies, you can probably get away with it, but don't be surprised if it comes back to bite you.

---

### Post by MadmanRB on 2013-06-06
> **Temüjin said:**
> I assume you're just talking about libdvdcss, so it's all about legal reasons (which is why Medibuntu exists in the first place).

Well yes there is a reason for Medibuntu, and with that reason in danger there needs to be either A: something to fill in the gap
or B: it having a developer or C: Forcing everyone to compile.
I say C is worst case scenario, ubuntu has made great strides and it will be a shame to see those codecs go, as it would make ubuntu useless for multimedia

Now if videolan has packages then fine we can be cool and not compile.
We just need to help new users figure it out.
And I always think of new users

Though it seems the most recent versions for libdvdcss are from way back.
We definitely need a more recent version, one that not everyone will have to compile.

---

### Post by MIJ-VI on 2013-10-11
"The Medibuntu repository is unmaintained and offline." 

The Medibuntu Project has come to an end
[http://www.medibuntu.org/](http://www.medibuntu.org/)

"As of October 2013, The Medibuntu Project has come to an end. The Medibuntu repository is unmaintained and offline."

Medibuntu - Wikipedia, the free encyclopedia
[https://en.wikipedia.org/wiki/Medibuntu](https://en.wikipedia.org/wiki/Medibuntu)

---

### Post by andrew.46 on 2013-10-11
A big thanks to the maintainers for their years of work!!

---

### Post by houstonbofh on 2013-10-16
So...  Of the 3 remaining things, one (/usr/share/doc/libdvdread4/install-css.sh) was fixed AFTER Medibuntu was taken down.  :)  What about the other two?  Is anyone going to host the w32codecs/w64codecs and libavcodecs-extra?  It is not like they change often...

Also, note that the mirrors are still up...

Mirror 1:

    deb [http://mirrors.ucr.ac.cr/medibuntu/](http://mirrors.ucr.ac.cr/medibuntu/) precise free non-free
    deb-src [http://mirrors.ucr.ac.cr/medibuntu/](http://mirrors.ucr.ac.cr/medibuntu/) precise free non-free



Mirror 2:

    deb [http://mirror.oscc.org.my/medibuntu/](http://mirror.oscc.org.my/medibuntu/) precise free non-free
    deb-src [http://mirror.oscc.org.my/medibuntu/](http://mirror.oscc.org.my/medibuntu/) precise free non-free



Mirror 3:

    deb [ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/](ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/) precise free non-free
    deb-src [ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/](ftp://ftp.leg.uct.ac.za/pub/linux/medibuntu/) precise free non-free

---

### Post by speartip on 2013-10-17
The libavcodec-extra package can be had, by adding the ffmpeg ppa found here:
[https://launchpad.net/~jon-severinsson/+archive/ffmpeg](https://launchpad.net/~jon-severinsson/+archive/ffmpeg)
It must pull it in as a dependency.

---

### Post by snowboarder on 2013-12-11
Use the debian-multimedia repo...that's what I use and haven't had problems. 

I use the "sid" repo so that if there's any new version for either libdvdcss2 or W64 codecs it will get pushed there. 

Desmo

---

### Post by andrew.46 on 2013-12-11
> **snowboarder said:**
> I use the "sid" repo so that if there's any new version for either libdvdcss2 or W64 codecs it will get pushed there. 

Mind you the MPlayer assembled codec pack for 64bit systems is not very useful and it is doubtful that it will ever be extended.....

---

### Post by snowboarder on 2013-12-11
> **andrew.46 said:**
> Mind you the MPlayer assembled codec pack for 64bit systems is not very useful and it is doubtful that it will ever be extended.....

You are quite right...

I should also point out that if you don't know what you are doing, a "noob" so to speak, it is asking for a borked system to mix ubuntu and debian sid repos/packages. 

If you really want libdvdcss2 and W32/64 codecs, enable the deb-multimedia repo, install said packages and then disable the deb-multimedia repo.
You'll have the packages you need and won't cause havoc with your system. 

Desmo

---

