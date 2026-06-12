---
title: "Where's Grip?"
date: 2009-11-01
forum: Multimedia Software
---

### Post by Spike-X on 2009-11-01
It seems to have disappeared from the repositories. What gives?

If it's no longer supported, can anyone suggest a decent alternative?

---

### Post by bluelamp999 on 2009-11-02
I'd also like to know what gives here...

---

### Post by ikacer on 2009-11-02
a really good alternative is Rubyripper. It does probably the most accurate rips of anything available on linux.

[http://wiki.hydrogenaudio.org/index.php?title=Rubyripper]("http://wiki.hydrogenaudio.org/index.php?title=Rubyripper")

[http://code.google.com/p/rubyripper/]("http://code.google.com/p/rubyripper/")

It isn't in the reps, so you'll have to compile it yourself, but its a really easy build, I just compiled it myself on karmic a couple days ago without any difficulties. It's also on getdeb for previous Ubuntu releases, so my guess is that it will pretty soon by added there for karmic:

[http://www.getdeb.net/app/Rubyripper]("http://www.getdeb.net/app/Rubyripper")

---

### Post by benerivo on 2009-11-02
I'm suprised that grip's gone. Maybe if you download the deb from the jaunty repositories ([32bit]("http://packages.ubuntu.com/jaunty/i386/grip/download") or [64bit]("http://packages.ubuntu.com/jaunty/amd64/grip/download")) it will still install okay. I think the last update to grip was 2005, so maybe that is why it was dropped. [ripperX]("http://packages.ubuntu.com/karmic/ripperx") is a good alternative.

---

### Post by Spike-X on 2009-11-02
Thanks, I tried that, but the Jaunty package has a whole bunch of dependency issues I have neither the time nor inclination to try and resolve.

I've seen RipperX mentioned elsewhere, I'll give that a go.

---

### Post by itlarson on 2009-11-15
I'd like to cast my vote for keeping grip in the repositories-  updated or not.  Ripperx doesn't seem to allow you to set the lame command line manually.

---

### Post by orbital on 2009-11-17
I will miss Grip, great software...

I will also give RipperX a try...

---

### Post by jsiei97 on 2009-11-19
> **orbital said:**
> I will miss Grip, great software...


Me to, grip is a good program....
And then I heard that gimp is to be removed in 10.04!


Has somebody lost it??? 
This sucks! :mad:

I have used Ubuntu for 4+ years, and maybe it is time to move on...

---

### Post by coffeecat on 2009-11-19
> **jsiei97 said:**
> Me to, grip is a good program....
And then I heard that gimp is to be removed in 10.04!

Grip has been a dead project for a few years now. That's why it has been dropped - dependency problems. It relies on obsolete libraries and can no longer be supported.

So you heard that the Gimp is to be removed in 10.04? You mean, in a report [like this]("http://www.omgubuntu.co.uk/2009/11/gimp-to-be-removed-lucid.html")? Did you go beyond the headline? The Gimp is to be removed from a default installation, that's all. You can still install it from the repositories. Unlike grip, the Gimp is alive, well and likely to be around for years to come.

---

### Post by mc4man on 2009-11-19
While I use rubyripper and now that I've got neroAac support, abcde, it is possible to continue to use grip if one wished. There is only one dependency issue and due to the nature of it it's probably best to build grip on karmic rather than  install the jaunty version of the lib. 

See here for a bit more info, I did by building an i386 ubuntu .deb for karmic, oldos2er did by building the source from site.

In both cases grip works fine for ripping and encoding

[http://ubuntuforums.org/showthread.php?t=1328177](http://ubuntuforums.org/showthread.php?t=1328177)

---

### Post by optimus2861 on 2009-11-22
(Vent alert!)

The problem with ripperx is that it has no help file, tooltips, etc, to explain its options. I have a particular file name format that I want to use, and I have no idea what ripperx's options are in this regard. Piece of junk; I've got no time for software that doesn't bother to provide the most basic documentation on how it works.

Meanwhile, Audio CD Extractor doesn't want to enable mp3 as an output format no matter how I play around with its preferences; soundkonverter seems to sit at "waiting" forever (typical half-assed Ubuntu KDE implementation); ripoff tells you in the software center (which asks for my password far too often, BTW) that it doesn't have mp3 support built-in; and I forget what I didn't like about Asunder, but it only stayed on my system for about 5 minutes.

Junk, the lot of them. I would've thought a good cd ripper was a long-ago solved problem and wouldn't require this kind of running around.

(End vent.)

Off to compile grip from source, I guess!

---

### Post by coffeecat on 2009-11-22
Audio CD extractor outputs mp3 just fine on my system. In fact, I ripped a CD to mp3 for my media player just an hour or so ago. Since another app is complaining about lack of an mp3 encoder, you might want to see if you've got lame installed.

---

### Post by mc4man on 2009-11-22
> soundkonverter seems to sit at "waiting" forever

While your better off using something you're familiar with, or learning how to use abcde and or rubyripper, for sk in settings -> configure soundkonverter ->  backends the 'Cd ripper' needs to be set to cdparanoia rather than the default of Kde audio cd.....' when using in gnome

---

### Post by Spike-X on 2009-12-01
RipperX is a bit lacklustre. RubyRipper is great, though. Well worth the (minimal) time and effort needed to compile it from source.

---

### Post by optimus2861 on 2009-12-06
> **coffeecat said:**
> Audio CD extractor outputs mp3 just fine on my system. In fact, I ripped a CD to mp3 for my media player just an hour or so ago. Since another app is complaining about lack of an mp3 encoder, you might want to see if you've got lame installed.
No, lame is/was most definitely there. So I don't know what was up with CD extractor, but since I got grip running on my system I don't care anymore :P

---

### Post by nadamsieee on 2009-12-19
> **mc4man said:**
> While your better off using something you're familiar with, or learning how to use abcde and or rubyripper, for sk in settings -> configure soundkonverter ->  backends the 'Cd ripper' needs to be set to cdparanoia rather than the default of Kde audio cd.....' when using in gnome

Thanks for the tip.

With cdparanoia as the backend the "State" of the first track changes to "Ripping... State: Unknown" and... nothing. It just sits there at 0%.

But with cdda2wav as the backend there seems to be progress...

---

### Post by Zimmer on 2009-12-19
Used to use Grip, too. Still have it on Win installation.

However, I have discovered that Banshee covers most bases with its Import procedure.. (ie ripping) so I guess that is what I will be using from now on... 
Allows editing of metadata, too.

---

### Post by patek on 2010-01-08
I don't know much about this and I'm sure the developers have a logic behind removing a ripper from the distribution (unless there is one that I'm not aware off).
But I'm very disappointed there isn't a clear obvious choice, like grip was.
Might try K3B but my laptop is probably too old for that.

---

### Post by Zimmer on 2010-01-08
It has been removed because it is no longer maintained...
[http://sourceforge.net/projects/grip/](http://sourceforge.net/projects/grip/)

---

### Post by flemmingbjerke on 2010-01-17
Is there any reason to develop grip anymore?

---

### Post by will177 on 2010-01-31
I have Karmic 64-bit and grip is in my apt repository according to aptitude and according to me as I'm running it now.

$ grip --version
GNOME grip 3.3.1

$ dpkg -l grip
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  grip           3.3.1-16       GNOME-based CD-player/ripper/encoder
will@moya:~/attachments$ 


Anyway, when I tried to rip a CD is said it was doing it but nothing much happened and it finished in under 1 second.

To make it work I changed the ripper from 
grip(cdparanoia) 
to 
cdparanoia

and now it's working.

Not sure if that's what other people experience, but that's my mileage.

HTH

---

### Post by mc4man on 2010-01-31
> I have Karmic 64-bit...

Interesting... do you hapeen to have the jaunty universe repo or a ppa enabled in your sources or maybe a grip package from jaunty in your apt archives. (or it was brought forward, ect.

Cause it's nowhere to be seen in the [ubuntu packages]("http://packages.ubuntu.com/search?lang=en&searchon=names&keywords=grip") for karmic, lucid

---

### Post by shantiq on 2010-01-31
[COLOR=Blue][B];);) did not read all the replies but it is there


[http://nostatic.org/grip/](http://nostatic.org/grip/)

and apparently no longer available


but there are better software such as

[ripit ]("http://www.suwald.com/ripit/news.php")

install with   [COLOR=DarkRed]sudo apt-get install ripit[/COLOR]

[/B]**and run [COLOR=DarkRed]man ripit [/COLOR]in the terminal       to see the manual                really easy to use      **[/COLOR]
[COLOR=Blue][B]


[pacpl]("http://pacpl.sourceforge.net/")         [COLOR=DarkRed]sudo apt-get install pacpl[/COLOR]   to install

 and      [COLOR=Sienna]man pacpl[/COLOR]    for the manual



cdparanoia   is already there    again      [COLOR=DarkRed]man cdparanoia[/COLOR]   



those are a lot of fun and EASY to use

shan


[/B][/COLOR]

---

### Post by will177 on 2010-01-31
I upgraded from Jaunty - may be it got left behind on my machine then?

/etc/apt/sources.list mentions only karmic, no jaunty repos.

Anything else you'd like me to check?

---

### Post by rapido on 2010-02-01
NEW:
I created a ppa to "add" grip back into a repository as a pre-compiled module.  
Please try out this new method of fetching grip, and let me know how it works.

```

sudo add-apt-repository ppa:rapido/grip
sudo apt-get update
sudo apt-get install grip

```

OLD:
I compiled grip from sources, which seemed to work just fine.

To simplify, I have created a shell script to do the work:

```

wget http://www.shiftingheat.com/packages/ubuntu/karmic_install/grip_install.sh
sh grip_install.sh

```

For completeness, or if you would like to perform one step at a time, here is the code that he shell script contains:

```
# download grip 3.3.1 source
wget http://downloads.sourceforge.net/project/grip/grip/3.3.1/grip-3.3.1.tar.gz?use_mirror=superb-dca2

# unpack
tar -xzvf grip-3.3.1.tar.gz
cd grip-3.3.1

# get the dependencies
sudo apt-get update
sudo apt-get install libgnomeui-dev libvte-dev libcurl4-openssl-dev

# build and install
./configure
make
sudo make install

# install other useful libraries
sudo apt-get install lame flac vorbis-tools

```

Hope this helps others who wish to continue using grip.

---

### Post by shantiq on 2010-02-01
[COLOR=Blue]**;);) rapido that is impressive**

[/COLOR][COLOR=Blue]the program looks old-fashioned but is a cute way to use cdparanoia 


you obviously know your way round


i posted this on cd ripping related topic

 [http://ubuntuforums.org/showthread.php?t=1394814](http://ubuntuforums.org/showthread.php?t=1394814)

to do with a cd which does not perform through a program like grip



any pointers for myself or anyone else in the same boat/?


if you have the time


and thanx for grip      shan
[/COLOR]

---

### Post by spegru on 2010-02-10
Rapido that is great. I really wanted to keep Grip - just because I have been using it for years
However when I first tried it on my LinuxMint8 (Ubuntu9.10 based ) system, it got to 99% and hung - searching: lots of Get, Ign and Hit statements after grip-3.3.1/grip.desktop

So I followed the step by step process that you usefully included and discovered that it was hanging at apt-get update. This is no doubt because there is some kind of confict between Mint8 and Ubuntu9.10 repos.
So since mey system was already up to date, I simply skipped this step and continued, It works fine!

One thing though is I want to encode in ogg but grip complains about missing executable for that (normally called oggenc). What is the official name for that, and/or where can I get it/ what is the path to it?
I'm sure Ill be fully up and running shortly

Thanks again

Ps. I'll have to cross post in mint forums.........

---

### Post by rapido on 2010-02-10
Spegru,

You should be able to enable oggenc via the following:
$ sudo apt-get install vorbis-tools

I added this to the script above and tested it ( encoded to ogg ).  Worked for me.

As far as the hang at 99% during an apt-get update, I get that all the time.  I believe it is independent of Mint8 as it happens on vanilla karmic.  That step typically takes a couple of minutes.  Not sure exactly why and would prefer to know the "hurry-up" ( if it exists ) for the repos update.

---

### Post by spegru on 2010-02-11
Thanks Rapido.
Nice and it works for me!
spegru

---

### Post by orbital on 2010-02-11
Thanks rapido, excellent script!

---

### Post by darsu on 2010-02-16
Thanks, Rapido. Losing good and familiar software drives me up the wall.

---

### Post by dentament on 2010-04-30
Here is a ppa with pre-packaged grip
[https://launchpad.net/~futurepilot/+archive/ppa](https://launchpad.net/~futurepilot/+archive/ppa)

---

### Post by dwasifar on 2010-05-06
I am having the weirdest problem with Grip since upgrading to Lucid.  When I load a CD in Grip, the tracklist immediately highlights track 5 (or the highest track number on the disc if there are fewer than five) and won't let me change it.  If I select another track, it immediately jumps back to track 5.  This means I can't edit titles.

I have uninstalled and reinstalled Grip, both from rapido's and futurepilot's ppas, and I have built it from source too, and the problem keeps happening.  It's the strangest thing.

---

### Post by jaygo on 2010-05-24
thanks rapido!

---

### Post by Spike-X on 2010-05-25
> **dentament said:**
> Here is a ppa with pre-packaged grip
[https://launchpad.net/~futurepilot/+archive/ppa](https://launchpad.net/~futurepilot/+archive/ppa)
Excellent, thank you!

---

### Post by macalikm on 2010-10-19
this worked for me:

sudo apt-get install lame cdparanoia libgnomeui-common libgnomeui-dev libvte9 libvte-dev python-vte curl libcurl-gnutils-dev libcurl4-dev

wget [http://sourceforge.net/projects/grip/files/grip/3.3.1/grip-3.3.1.tar.gz](http://sourceforge.net/projects/grip/files/grip/3.3.1/grip-3.3.1.tar.gz)
sudo gunzip grip-3.3.1 .tar.gz
cd grip-3.3.1
./configure
make
sudo make install

each time that ./configure failed, the missing dep had to be added "sudo apt-get install"ed

cheers
MI

---

### Post by Schrute Farms on 2010-10-19
Ironic that this post just came up, because I compiled Grip just a few days ago.

I was using RipperX, and it works fine for me, but all of a sudden it crashes when it's done ripping.  All the rips are good, but files 10 and above have no ID3 tag info in them, so I have to open EasyTag and fix them.  Not a big deal, just an extra step I don't wanna do.  I tried reinstalling RipperX and LAME to no avail.
I couldn't find any other ripper in binary form that used LAME that I liked, so I decided on Ruby Ripper.  I couldn't find it in the repositories or any .debs, so I broke my compiling cherry with it.  It works great, it's just so sssllloooowwww.  My CDs are in good shape, so it doesn't have to compare the rips two times, or whatever it does.  So, I decided on Grip.  Again, couldn't find it in the repositories or any .debs, so I compiled it.  Works perfectly for me.

---

### Post by stmiller on 2011-01-02
I installed grip as well from source for Ubuntu 10.10, with:

```

sudo apt-get install lame cdparanoia libgnomeui-common libgnomeui-dev libvte9 libvte-dev python-vte curl libcurl4-gnutls-dev checkinstall build-essential

```


```

$ ./configure

$ make

$ sudo checkinstall
```

But now I'm getting the dreaded 'No Disc' that everyone seems to be getting with a sata optical drive and Grip. Anyone having any success with a sata drive in seeing the audio CD?

---

### Post by marcovermeulen on 2011-03-12
Hi all,

I've set up a PPA, along with some guides about installing Grip on my blog:
[http://mycodesnippets.com/2011/03/10/install-grip-cd-ripper-on-ubuntu-through-ppa/](http://mycodesnippets.com/2011/03/10/install-grip-cd-ripper-on-ubuntu-through-ppa/)

Compiling and installing Grip from source code, using it with FLAC encoder:
[http://mycodesnippets.com/2010/04/07/installing-grip-cd-ripper-with-flac-on-ubuntu-linux/](http://mycodesnippets.com/2010/04/07/installing-grip-cd-ripper-with-flac-on-ubuntu-linux/)

I've also included a nice guide to get Nero AAC working with Grip:
[http://mycodesnippets.com/2011/03/12/how-to-use-nero-aac-codec-with-grip-cd-ripper/](http://mycodesnippets.com/2011/03/12/how-to-use-nero-aac-codec-with-grip-cd-ripper/)

As you can see, I'm quite the Grip fan!
Please post feedback on my blog...
Cheers,
Marco.

---

### Post by oldos2er on 2011-03-12
> **marcovermeulen said:**
> As you can see, I'm quite the Grip fan!


I am too, even though I don't need it very often. Thanks for this.

---

### Post by shantiq on 2011-03-13
> **marcovermeulen said:**
> Hi all,

I've set up a PPA, along with some guides about installing Grip on my blog:
[http://mycodesnippets.com/2011/03/10/install-grip-cd-ripper-on-ubuntu-through-ppa/](http://mycodesnippets.com/2011/03/10/install-grip-cd-ripper-on-ubuntu-through-ppa/)

Compiling and installing Grip from source code, using it with FLAC encoder:
[http://mycodesnippets.com/2010/04/07/installing-grip-cd-ripper-with-flac-on-ubuntu-linux/](http://mycodesnippets.com/2010/04/07/installing-grip-cd-ripper-with-flac-on-ubuntu-linux/)

I've also included a nice guide to get Nero AAC working with Grip:
[http://mycodesnippets.com/2011/03/12/how-to-use-nero-aac-codec-with-grip-cd-ripper/](http://mycodesnippets.com/2011/03/12/how-to-use-nero-aac-codec-with-grip-cd-ripper/)

As you can see, I'm quite the Grip fan!
Please post feedback on my blog...
Cheers,
Marco.


well marco i had tried for the last 2 years to rip and encode to flac on grip and failed MISERABLY a hundred times


Could never work out those encode lines    also i too a big fan of neroAacEnc



so thaNk you for this:KS


ps if anyone wants to encode to neroAacEnc using Rubyripper you can find it [here]("http://ubuntuforums.org/showpost.php?p=9630448&postcount=26")

---

### Post by Garage Guy on 2012-07-20
Just want to say that I have exactly the same problem as dwasifar: 

"When I load a CD in Grip, the tracklist immediately highlights track 5 (or the highest track number on the disc if there are fewer than five) and won't let me change it. If I select another track, it immediately jumps back to track 5. This means I can't edit titles. I have uninstalled and reinstalled Grip, both from rapido's and futurepilot's ppas, and I have built it from source too, and the problem keeps happening."

Ubuntu 10.04 LTS 64 bit.

--GG

---

### Post by wildmanne39 on 2012-07-21
Hi, this is an old thread so it has been closed please start a new thread of your own with a descriptive title. 
Thanks

---

